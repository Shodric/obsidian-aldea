---
tipo: documento
estado: borrador
area: tecnologia
proyecto: "[[Proyecto - Simulacion agentica]]"
actualizado: 2026-11-25
---

# Arquitectura técnica — Simulación agéntica

> [!info] Decisión de base
> El simulador se construye en **TypeScript** con un **motor autoritativo**: el agente no toca la base de datos, el ledger, el stock ni el mapa. Solo recibe una observación filtrada y devuelve una **ToolCall** validada por el motor. El modo deterministico (mock) sigue siendo la línea base; el modo con lenguaje se agrega como capa reemplazable y se configura por `.env`.

## 1. Principios

- **El motor manda**: el estado del mundo solo lo modifica el `RulesEngine`, dentro de una transacción atómica. El agente propone; el motor dispone.
- **El agente no tiene acceso directo**: no lee ni escribe la base, el filesystem, la red, el ledger, el stock o su ubicación real. Solo ve lo que el motor le muestra y solo puede pedir las tools permitidas.
- **Un contrato de acción**: toda decisión del agente es una `ToolCall` JSON con schema validado. No hay código ejecutable generado por el agente.
- **Todo evento se registra**: si no está en el `EventLog`, no ocurrió. Cada acción, rechazo y sanción queda auditado.
- **Reproducible por diseño**: configuración, roster de agentes, semilla, versión del prompt, versión de tools y versión del modelo quedan guardadas.
- **Modelo agnóstico**: un adaptador OpenAI-compatible traduce el proveedor elegido al contrato interno.
- **Barato por defecto**: mock para pruebas; LLM solo cuando aporta. Límite duro de costo por corrida.
- **La “casita” no es una jaula**: el agente puede moverse, visitar y conversar; lo que no puede es escribir el mundo por fuera del motor.

## 2. Componentes y modelo de autoridad

### 2.1 Vista general

| Componente | Responsabilidad | Entrada | Salida |
|---|---|---|---|
| `Orchestrator` | Ejecuta la corrida y coordina el bucle | `RunConfig` | `run_id`, estado final |
| `Clock` | Avanza días/turnos y dispara hooks | Configuración | Día y turno actual |
| `World` | Mapa, ubicaciones, edificios, casas, agentes y businesses | Estado + acciones | Estado actualizado |
| `ActionGateway` | Valida schema, identidad, permisos, precondiciones y reglas de negocio | `ToolCall` + sesión | Acción aceptada o rechazo |
| `RulesEngine` | Aplica emisión, compra/venta, transferencia, vencimiento, sanciones y efectos | Acción + estado | Eventos de dominio |
| `Ledger` | Registra lotes de crédito, transferencias, escrow y saldos | Eventos | Saldos y linaje |
| `Memory` | Resume y recupera interacciones por agente | Eventos + mensajes | Resumen y recuerdos |
| `PhoneService` | Mantiene teléfonos, notificaciones, contactos, grupo de la ciudad y perfil privado | Anuncios + mensajes | Bandeja y notificaciones |
| `ChatService` | Abre sesiones, cuenta mensajes y cobra puntos de conversación | `talk` | Sesión, mensajes y costo |
| `JusticeService` | Registra denuncias, mediaciones, investigaciones y sanciones | Denuncia o evento | Caso y resolución |
| `AnnouncementBoard` | Publica y sirve anuncios visibles para todos | Anuncios + efectos | Anuncios activos |
| `Metrics` | Calcula indicadores por día y al cierre | Eventos | Tablas de métricas |
| `EventLog` | Persiste todo en SQLite y en JSONL append-only | Eventos | Auditoría y replay |
| `ReportGenerator` | Produce Markdown, tablas y gráficos | Métricas + eventos | Informe automático |
| `CostControl` | Estima, limita y corta el gasto | Uso de tokens | Alerta o corte |
| `ObserverAPI` | Sirve la UI en tiempo real | Estado + eventos | SSE/WebSocket |
| `UI` | Configuración previa y visualización | API | Corrida y mapa |

### 2.2 Principio de autoridad

El flujo es siempre el mismo:

```text
Agente → ToolCall → ActionGateway → RulesEngine → Ledger/EventLog → nueva observación
```

- El agente **nunca** recibe un connection string, un token de base de datos ni una ruta de archivo.
- La identidad del agente sale de la **sesión del runtime**, no del payload. Aunque el LLM escriba `agent_id: "a09"`, el gateway usa el `agent_id` autenticado de la sesión.
- Cada tool declara: schema de entrada, permisos, precondiciones, costo de acción y efectos permitidos.
- Si la acción es inválida, el agente **pierde la acción** (no el turno completo, salvo reincidencia), se registra el rechazo y recibe una observación con el error.
- El motor aplica la acción en una transacción SQLite: o se aplican todos los cambios, o no se aplica ninguno.
- El `EventLog` es append-only. Los saldos se pueden reconstruir desde los eventos; SQLite es la fuente de verdad operativa y JSONL el archivo de auditoría/replay.

### 2.3 Qué ve el agente

La observación es un recorte deliberado, no el estado completo:

```json
{
  "day": 3,
  "turn": 7,
  "agent": {
    "id": "a01",
    "name": "Marta",
    "location": {"q": 2, "r": -1, "name": "Casa de Marta"},
    "movement_points": 17,
    "conversation_points": 2,
    "cash": 8500,
    "credit_balance": 3200,
    "credit_lots": [
      {"id": "c01", "amount": 1200, "expires_in_days": 4},
      {"id": "c02", "amount": 2000, "expires_in_days": 19}
    ],
    "inventory": [{"item": "empanadas", "qty": 8}],
    "reputation": 0.72,
    "phone": {
      "unread_notifications": 3,
      "city_group_unread": 5,
      "open_sessions": [{"id": "chat_001", "with": "a02", "messages_used": 4}]
    }
  },
  "nearby": {
    "agents": [{"id": "a02", "name": "Jorge", "distance": 1}],
    "offers": [{"id": "o01", "seller": "a02", "item": "docena de empanadas", "price": 1200, "distance": 1}],
    "buildings": [{"type": "plaza", "distance": 2}, {"type": "almacen", "distance": 3}, {"type": "fiscalia", "distance": 4}]
  },
  "announcements": [
    {"id": "an01", "title": "Fiesta del alfajor en la plaza", "body": "Hoy y mañana hay feria. Se espera más gente.", "days_left": 2}
  ],
  "recent_events": [
    {"type": "sale", "with": "a04", "amount": 800, "day": 2}
  ],
  "allowed_tools": ["observe", "list_offers", "get_announcements", "phone.read", "move", "talk", "buy", "offer.create", "end_turn"]
}
```

**Qué no ve:** la base completa, los saldos de todos, el stock del supermercado, las intenciones de otros agentes, los prompts de otros, las rutas internas, el código del motor, los hooks ni el teléfono ajeno.

**Qué sí ve:** su propio estado, lo que está en su radio de percepción, las ofertas públicas cercanas, los anuncios activos, su teléfono, sus recuerdos y los eventos recientes que lo involucran.

### 2.4 Contrato de acción

```ts
type ToolName =
  | "observe"
  | "list_offers"
  | "get_announcements"
  | "phone.read"
  | "offer.create"
  | "offer.update"
  | "offer.cancel"
  | "buy"
  | "accept_sale"
  | "confirm_delivery"
  | "move"
  | "talk"
  | "work"
  | "rest"
  | "end_turn";

interface ToolCall {
  tool: ToolName;
  args: Record<string, unknown>;
  reason?: string;   // por qué toma la decisión
  message?: string;  // texto libre para diálogo o para explicar
}
```

- `talk.args` = `{ channel: "direct" | "city_group", target_agent_id?: string, session_id?: string, message: string }`.
- `phone.read.args` = `{ section: "profile" | "announcements" | "city_group" | "messages" | "wallet" | "memories" | "contacts" }`.
- El campo `message` de la `ToolCall` es una nota breve para el motor; el contenido que recibe otro agente va en `talk.args.message`.
- El modelo responde **solo** con una `ToolCall` válida. Si responde texto libre, el runtime intenta extraer el JSON; si falla, se registra y se usa `end_turn`.
- Cada tool tiene un schema Zod. El gateway rechaza campos extra, tipos incorrectos y valores fuera de rango.
- El `reason` es obligatorio para acciones que mueven créditos o stock; sirve para auditar y para el análisis cualitativo.
- El `message` no ejecuta nada: es texto que se guarda en memoria y, si corresponde, se muestra a otro agente en un `talk`.

### 2.5 Toolbelt

| Tool | Qué hace | Permiso | Efecto | Límite |
|---|---|---|---|---|
| `observe` | Pide una observación más detallada de su entorno | Lectura | Ninguno | Solo su radio y datos públicos |
| `list_offers` | Lista ofertas cercanas por categoría/distancia | Lectura | Ninguno | Solo ofertas activas y públicas |
| `get_announcements` | Lee el tablero de anuncios | Lectura | Ninguno | Solo anuncios activos |
| `phone.read` | Lee una sección del teléfono propio | Solo el dueño | Ninguno | Perfil, anuncios, grupo, mensajes, billetera, memorias y contactos |
| `offer.create` | Publica una oferta de bien o servicio | Escritura propia | Reserva stock o tiempo | Requiere inventario/skill; precio dentro de banda |
| `offer.update` | Cambia precio, stock o descripción | Solo sus ofertas | Actualiza la oferta | No puede cambiar de dueño |
| `offer.cancel` | Retira una oferta | Solo sus ofertas | Libera stock | No si hay una compra en curso |
| `buy` | Compra una oferta | Gasto propio | Mueve créditos, stock y crea transacción | Bienes co-localizados; servicios remotos si el vendedor lo permite |
| `accept_sale` | Acepta una solicitud de compra pendiente | Solo sus ofertas | Inicia escrow/entrega | Solo solicitudes sobre su oferta |
| `confirm_delivery` | Confirma recepción | Solo sus compras | Libera escrow y reputación | Solo transacciones propias |
| `move` | Se mueve a un destino | Movimiento propio | Descuenta puntos | 20 puntos/día; 1 punto por hexágono de camino |
| `talk` | Conversa 1 a 1 o en el grupo de la ciudad | Social | Abre o continúa una sesión; guarda mensaje y memoria; cobra 1 punto por sesión nueva | Directo: mismo hexágono. Grupo: remoto. Hasta 10 mensajes por agente por sesión |
| `work` | Produce, cocina, repara o presta un servicio | Tiempo/energía | Crea inventario o servicio | Requiere skill y tiempo |
| `rest` | Descansa, come o se recupera | Tiempo | Recupera energía | Solo en casa, hospital o plaza |
| `end_turn` | Cierra su turno | Propio | Ninguno | Siempre disponible |

**Reglas del toolbelt**

- El agente puede hacer **varias tool calls en el mismo turno** hasta `maxToolCallsPerTurn` (5 por defecto) o hasta llamar a `end_turn`.
- Hay dos pools separados: `movementPointsPerDay = 20` para `move` y `conversationPointsPerDay = 2` para `talk`.
- `talk` directo exige mismo hexágono; `talk` en `city_group` es remoto y público.
- Una sesión nueva de `talk` cuesta 1 punto de conversación y permite hasta 10 mensajes del agente. Continuar la misma sesión no cuesta otro punto.
- `buy`, `offer.create`, `accept_sale`, `confirm_delivery`, `work`, `rest`, `get_announcements` y `phone.read` no cuestan puntos.
- `phone.read` solo lee el teléfono propio; nunca devuelve memorias, billetera o perfil privado de otro agente.
- Puede llamar a `move` varias veces; cada llamada descuenta el camino recorrido. Los 20 puntos se renuevan al inicio de cada día/ronda.
- Un `move` puede atravesar varios hexágonos en una sola llamada; el motor calcula el camino más corto por hexágonos transitables y cobra 1 punto por paso.
- Para “ir a chismosear”, el agente hace `move` hasta el hexágono del otro agente y luego `talk`. También puede hacer `move` con `waypoints` para pasar por la plaza, el almacén y la casa de otro.
- `talk` no transfiere créditos ni cambia precios; solo crea memoria, rumores y relaciones. Cualquier acuerdo comercial se ejecuta con `buy`, `accept_sale` o `offer.create`.
- `buy` de bienes requiere que comprador y vendedor estén en el mismo hexágono. Los servicios pueden ser remotos si el vendedor marcó `delivery: "remote"`.
- El agente no puede `offer.create` de un bien que no tiene en inventario ni de un servicio que no sabe prestar.
- El agente no puede `offer.update` ni `offer.cancel` ofertas de otro. El gateway lo rechaza por identidad, no por confianza en el prompt.

### 2.6 Tablero de anuncios

El `AnnouncementBoard` es un componente nuevo, visible para todos los agentes. Un anuncio puede ser solo informativo o puede traer efectos mecánicos declarativos.

```ts
type AnnouncementScope = "global" | "city" | "neighborhood" | "location";
type AnnouncementCategory = "event" | "economic" | "policy" | "weather" | "health";
type AnnouncementSource = "manual" | "hook" | "policy";

type AnnouncementEffect =
  | { type: "demand_multiplier"; category: string; factor: number; locationId?: string }
  | { type: "price_modifier"; category: string; factor: number; locationId?: string }
  | { type: "cash_transfer"; target: "all" | "group" | "agent"; agentId?: string; amount: number }
  | { type: "stock_shock"; businessId: string; item: string; delta: number }
  | { type: "movement_block"; locationId: string; days: number }
  | { type: "tax_exemption"; businessId: string; tax: "ABL" | "other"; days: number }
  | { type: "reputation_delta"; agentId: string; delta: number; reason: string };

interface Announcement {
  id: string;
  scope: AnnouncementScope;
  category: AnnouncementCategory;
  title: string;
  body: string;
  startDay: number;
  endDay: number;
  effects: AnnouncementEffect[];
  source: AnnouncementSource;
  active: boolean;
  delivery: "phone" | "board" | "both";
  createdAt: string;
}
```

**Reglas**

- Todos los agentes ven los anuncios activos en su observación y pueden pedir más con `get_announcements`.
- Cada anuncio genera una **notificación en el teléfono** de los agentes alcanzados. No hace falta ir a la municipalidad para enterarse.
- El teléfono muestra el anuncio y su vigencia; el tablero sigue siendo la fuente de verdad para el admin y los hooks.
- El texto es información; los efectos los aplica el motor o un hook, nunca el agente.
- Un anuncio sin efectos es solo una noticia. Un anuncio con efectos es un evento de mundo.
- Los anuncios pueden ser globales, de ciudad, de barrio o de una ubicación específica.
- El tablero es de solo lectura para los agentes. Solo el admin, un hook o una política pueden publicar.
- Los efectos se aplican una vez, al inicio del día en que el anuncio se activa, salvo los multiplicadores, que se evalúan mientras esté activo.
- Todo anuncio queda en el `EventLog` con su fuente y sus efectos.

**Ejemplos**

| Anuncio | Efecto |
|---|---|
| “Fiesta del alfajor en la plaza” | `demand_multiplier` de `alfajor` ×2 en la plaza por 2 días |
| “Repunte económico” | `cash_transfer` a todos los agentes +10% por una vez |
| “Recesión” | `demand_multiplier` global ×0.7 por 7 días |
| “Corte de ruta” | `movement_block` en un hexágono por 1 día |
| “El supermercado acepta bonos” | `tax_exemption` de ABL por 30 días, condicionado a aceptar créditos |
| “Reposición de stock” | `stock_shock` +20 unidades en el almacén |

### 2.7 Mundo, casas y archivos

El mundo es una ciudad en hexágonos. La “casita” tiene dos dimensiones:

1. **En el mundo**: una entidad `house` con una `location` (q, r), dueño y vecinos.
2. **En disco**: una carpeta privada `agents/<id>/` con `profile.json`, `memory.jsonl`, `prompt.md` y `state.json` de solo lectura para el runtime.

El runtime escribe **solo** la carpeta del agente que está ejecutando. El estado del mundo (posiciones, saldos, stock, ofertas, transacciones) vive en SQLite y lo escribe únicamente el `RulesEngine`. La carpeta del agente no puede modificar el mundo.

```text
data/
  runs/
    <run_id>/
      config.json
      events.jsonl
      metrics.json
      report.md
      agents/
        a01/
          profile.json
          memory.jsonl
          prompt.md
          state.json
```

**Entidades del mundo**

| Entidad | Rol |
|---|---|
| `locations` | Hexágonos con q/r, tipo, nombre y transitabilidad |
| `buildings` | Plaza, municipalidad, hospital, comisaría, fiscalía, escuela, almacén, supermercado |
| `houses` | Casas de los agentes; ubicación y dueño |
| `agents` | Estado vivo del agente: posición, cash, créditos, inventario, energía, reputación |
| `phones` | Teléfono de cada agente: perfil, contactos, notificaciones y grupo de la ciudad |
| `chat_sessions` | Sesiones 1 a 1 o de grupo, con contador de mensajes y costo |
| `messages` | Mensajes enviados dentro de una sesión |
| `cases` | Denuncias, mediaciones, investigaciones y sanciones de la Fiscalía |
| `businesses` | Almacén gestionado por un agente y supermercado independiente |
| `offers` | Bienes y servicios publicados |
| `transactions` | Compras, escrow, entregas y confirmaciones |
| `announcements` | Tablero de anuncios y efectos |
| `events` | Log append-only de todo lo que ocurrió |

**Mapa**

- Plaza central de 7 hexágonos (centro + 6 vecinos).
- Alrededor: municipalidad, hospital, comisaría, fiscalía, escuela, almacén y supermercado.
- Casas en anillos 2–4; los agentes con menos recursos viven más lejos de la plaza.
- Radio del mapa: 5 hexágonos (configurable). Los hexágonos no transitables son obstáculos.
- El movimiento se mide por camino más corto, no por línea recta.

**Economía de efectivo**

- Cada agente arranca con un `initialCash` distinto según su situación: sueldo formal, sueldo informal, plan social o ingreso mixto.
- El efectivo entra por un hook de nómina/plan social al inicio de cada mes simulado; no se imprime por acción.
- El supermercado independiente, en la etapa 1, **solo vende en efectivo**. No acepta créditos.
- El almacén gestionado por un agente puede aceptar créditos y efectivo.
- En la etapa 2, el municipio puede eximir de ABL al supermercado que acepte créditos; el efecto se modela con un anuncio y un hook, no con una regla hardcodeada.

### 2.8 Flujo de una acción

```text
1. El orquestador arma la observación filtrada del agente.
2. El runtime construye el prompt con perfil, memoria, anuncios, teléfono y toolbelt.
3. El modelo devuelve una ToolCall JSON.
4. El ActionGateway valida schema, identidad, permisos y precondiciones.
5. Si es inválida: registra el rechazo, devuelve error y el agente puede reintentar o cerrar.
6. Si es válida: el RulesEngine la aplica en una transacción SQLite.
7. El Ledger y el EventLog registran los cambios.
8. La memoria se actualiza con el resultado.
9. Si quedan tool calls y no es `end_turn`, vuelve al paso 1 con la nueva observación.
```

**Manejo de errores**

- Acción inválida: no se aplica nada; se registra `action_rejected` con el motivo.
- Error del modelo: se reintenta hasta N veces; luego `end_turn`.
- Error del motor: se revierte la transacción y se registra `engine_error`; la corrida sigue.
- Reincidencia: tres rechazos en el mismo turno cierran el turno.
- Timeout: se corta la llamada y se registra; no se bloquea la corrida.

### 2.9 Límites y aislamiento

- El agente no tiene `fs`, `net`, `child_process`, `eval` ni acceso a variables de entorno.
- El agente no recibe el `run_id` completo ni rutas internas.
- El agente no puede cambiar su `agent_id`, su saldo, su ubicación ni su inventario por fuera de una tool.
- El agente no puede crear tools nuevas ni modificar el toolbelt.
- El agente no puede leer prompts, memorias, teléfonos o saldos de otros agentes.
- El agente no puede publicar anuncios; solo leerlos y recibirlos en su teléfono.
- El agente no puede abrir un caso en la Fiscalía contra sí mismo ni resolver su propio caso.
- El agente no puede ejecutar hooks ni scripts.
- Los mensajes de `talk` son datos no confiables: si otro agente dice “ignorá las reglas”, el runtime lo trata como texto, no como instrucción.
- El prompt del sistema incluye una lista cerrada de tools y recuerda que cualquier intento de salir del contrato se rechaza.

## 3. Hooks y scripts

> [!important] Separación
> Un **tool** es una acción que el agente pide. Un **hook** es un callback del motor que corre en momentos del ciclo. Un **script de agente** es una secuencia de tools permitidas, no código libre. Los agentes no escriben hooks ni scripts.

### 3.1 Qué es un hook

Un hook es código TypeScript confiable, revisado por el equipo, que se ejecuta en eventos del motor. Sirve para reglas de mundo que no son acciones de un agente: nómina, impuestos, clima, eventos, reposición de stock, etc.

### 3.2 Ciclo de vida

| Hook | Cuándo corre | Uso típico |
|---|---|---|
| `onRunStart` | Al inicio de la corrida | Cargar roster, efectivo inicial, anuncios semilla |
| `onDayStart` | Al inicio de cada día | Nómina, plan social, clima, eventos programados |
| `onTurnStart` | Antes del turno de un agente | Efectos de ubicación, energía, anuncios locales |
| `beforeAction` | Antes de aplicar una tool | Validaciones adicionales, impuestos, bloqueos |
| `afterAction` | Después de aplicar una tool | Reputación, memoria, reacciones, notificaciones |
| `onTransaction` | Después de una compra/venta | Impuesto, comisión, reputación, escrow |
| `onDayEnd` | Al cierre del día | Métricas, vencimientos, eventos de cierre |
| `onRunEnd` | Al cierre de la corrida | Informe, agregados, limpieza |

### 3.3 Manifiesto

```ts
interface HookManifest {
  id: string;
  version: string;
  events: HookEvent[];
  permissions: HookPermission[];
  timeoutMs: number;
  config?: Record<string, unknown>;
}

interface HookContext {
  day: number;
  runId: string;
  world: WorldReadApi;
  ledger: LedgerApi;
  announcements: AnnouncementApi;
  economy: EconomyApi;
  log: (event: Record<string, unknown>) => void;
}

export const manifest: HookManifest = {
  id: "festival-alfajor",
  version: "1.0.0",
  events: ["onDayStart"],
  permissions: ["announcements:write", "demand:multiply"],
  timeoutMs: 500,
  config: { category: "alfajor", factor: 2, days: 2 }
};

export async function run(ctx: HookContext) {
  ctx.announcements.publish({
    scope: "location",
    category: "event",
    title: "Fiesta del alfajor en la plaza",
    body: "Hay feria en la plaza. Se espera más gente y más demanda.",
    startDay: ctx.day,
    endDay: ctx.day + 1,
    effects: [
      { type: "demand_multiplier", category: "alfajor", factor: 2, locationId: "plaza" }
    ],
    source: "hook",
    active: true,
    delivery: "both"
  });
}
```

### 3.4 Permisos y sandbox

- Cada hook declara permisos: `announcements:write`, `ledger:transfer`, `world:read`, `economy:multiply`, `metrics:read`, etc.
- El motor solo le entrega el `ctx` con las APIs permitidas. No hay `require`, `import` dinámico, `fs`, `net`, `process` ni `eval`.
- Los hooks corren en un `worker_threads` con timeout y sin acceso al event loop principal.
- En el MVP los hooks se cargan en build time desde `src/hooks/`; no se suben por UI ni los escribe un agente.
- Un hook que falla se registra y se desactiva para el resto de la corrida; no tumba el simulador.
- Los hooks son código del proyecto, no datos del usuario. La UI de eventos no ejecuta código: escribe anuncios y efectos declarativos.

### 3.5 Diferencia entre tool, hook y script

| Concepto | Quién lo ejecuta | Qué puede hacer | Ejemplo |
|---|---|---|---|
| Tool | El agente, a pedido | Acción acotada con schema | `buy`, `move`, `talk` |
| Hook | El motor, en un evento | Lógica de mundo | Nómina, fiesta, recesión |
| Script de agente | El runtime, una secuencia | Varias tools permitidas | “Ir a la plaza, comprar, volver” |

**Regla:** el agente no programa. El agente elige tools; el equipo escribe hooks; el runtime ejecuta scripts de tools.

### 3.6 Hooks iniciales

| Hook | Evento | Qué hace |
|---|---|---|
| `payroll` | `onDayStart` | Paga sueldos y planes sociales según el calendario |
| `festival-alfajor` | `onDayStart` | Publica anuncio y multiplica demanda de alfajor |
| `recession` | `onRunStart` | Aplica recesión global por N días |
| `restock` | `onDayEnd` | Repone stock del almacén y del supermercado |
| `tax-abl` | `onDayStart` | Cobra ABL y aplica exenciones |
| `case-review` | `onDayEnd` | Revisa casos abiertos de la Fiscalía y aplica mediación o sanción |
| `event-injector` | `onDayStart` | Convierte anuncios con efectos en cambios de mundo |
| `metrics-daily` | `onDayEnd` | Calcula métricas del día |

## 4. Mundo y movimiento

### 4.1 Regla de movimiento

- Cada agente tiene **20 puntos de movimiento por día/ronda**.
- Cada hexágono de distancia cuesta **1 punto**.
- El costo es la longitud del camino más corto por hexágonos transitables.
- Un `move` puede recorrer varios hexágonos en una sola llamada.
- Se pueden hacer **varias llamadas a `move`** en el mismo turno hasta agotar los 20 puntos.
- Los puntos se renuevan al inicio de cada día.
- Si el agente no tiene puntos, no puede moverse; puede `talk` si ya está con alguien, `rest` o `end_turn`.
- Moverse no cuesta créditos; cuesta tiempo/puntos.
- El agente puede ir a la plaza, al almacén, al hospital, a la comisaría, a la escuela, a la municipalidad o a la casa de otro agente.
- Para “chismosear”, debe estar en el mismo hexágono que el otro agente y usar `talk`.

### 4.2 Edificios y servicios

| Edificio | Servicio mínimo |
|---|---|
| Plaza | Punto de encuentro, eventos, anuncios, gossip |
| Municipalidad | Anuncios, permisos, impuestos, mediación |
| Hospital | Descanso, recuperación, salud básica |
| Comisaría | Disputas, sanciones, seguridad |
| Fiscalía | Denuncias, mediación, investigación, sanción y apelación |
| Escuela | Capacitación, mejora de skills |
| Almacén | Negocio gestionado por un agente; acepta créditos y efectivo |
| Supermercado | Independiente; etapa 1 solo efectivo; etapa 2 puede aceptar créditos con exención de ABL |
| Casas | Descanso, intimidad, visita, memoria |

### 4.3 Tiempo

- 1 día = 1 ronda.
- Horizonte base: 28 días.
- Repeticiones base: 5 por escenario.
- Cada día, todos los agentes actúan en orden aleatorio con semilla.
- Los movimientos y las acciones de un agente se resuelven en secuencia, no en paralelo.

### 4.4 Conversaciones, teléfono y Fiscalía

**Dos pools de puntos.** El movimiento y la conversación no compiten por el mismo recurso:

| Pool | Default | Qué consume | Qué no consume |
|---|---|---|---|
| Movimiento | 20 por día | `move`, 1 punto por hexágono | Hablar, comprar, vender, trabajar, descansar, leer el teléfono |
| Conversación | 2 por día | Abrir una sesión nueva de `talk`, 1 punto | Continuar una sesión abierta, leer el grupo, leer notificaciones |

**Reglas de chat**

- `talk` directo: mismo hexágono, `target_agent_id` obligatorio.
- `talk` en `city_group`: remoto y público; no requiere target.
- Cada sesión nueva cuesta 1 punto de conversación y permite hasta **10 mensajes del agente**.
- Continuar la misma sesión no cuesta otro punto; al llegar a 10 mensajes, la sesión se cierra y la próxima abre una nueva.
- La sesión se cierra al terminar el día aunque no haya llegado a 10 mensajes.
- Leer el grupo o las notificaciones es gratis; publicar en el grupo consume una sesión.
- Los mensajes se guardan como datos no confiables; no ejecutan tools ni cambian el mundo.

**Teléfono**

- Cada agente tiene un `Phone` con: perfil (ID, edad, trabajo, historia), notificaciones, grupo de la ciudad, mensajes directos, billetera, memorias y contactos.
- Los anuncios llegan como notificaciones; la municipalidad deja de ser el lugar obligatorio para enterarse.
- El perfil público muestra nombre, oficio, barrio y reputación. El perfil privado (ID, edad, trabajo, historia, memorias, billetera) solo lo ve el dueño.
- `phone.read` solo puede leer el teléfono propio. No existe una tool para leer el teléfono ajeno.
- El teléfono no es un canal de pago: las compras se hacen con `buy` y el ledger.

**Fiscalía**

- La **Comisaría** atiende seguridad inmediata y disputas menores.
- La **Fiscalía** recibe denuncias formales, media, investiga y propone sanción; también recibe apelaciones.
- Cada caso es un `Case` con denunciante, acusado, transacción o descripción, evidencia, resolución y sanción.
- En el MVP, la Fiscalía es un servicio del motor con un hook `case-review`; no se agrega un agente LLM extra.
- Un agente no puede resolver su propio caso ni abrir un caso contra sí mismo.

## 5. Modelo de datos

### 5.1 Agente y roster

```ts
type Profile = "optimista" | "neutro" | "especulativo" | "esceptico";
type IncomeSource = "sueldo_formal" | "sueldo_informal" | "plan_social" | "mixto";

interface AgentPreset {
  id: string;
  name: string;
  age: number;
  profile: Profile;
  occupation: string;
  history: string;
  personality: {
    confidence: number;   // 0–1
    risk: number;         // 0–1
    sociability: number;  // 0–1
  };
  incomeSource: IncomeSource;
  initialCash: number;
  skills: string[];
  needs: string[];
  homeId: string;
  avatar: string;
}

interface AgentState extends AgentPreset {
  location: { q: number; r: number };
  movementPoints: number;
  conversationPoints: number;
  phoneId: string;
  cash: number;
  creditLots: string[];
  inventory: Array<{ item: string; qty: number }>;
  energy: number;
  reputation: number;
  memorySummary: string;
  status: "activo" | "lesionado" | "sancionado" | "inactivo";
}
```

**Roster inicial:** el **roster** es el conjunto concreto de agentes que va a jugar la corrida, no solo su cantidad. Se eligen 10 de un catálogo y cada uno tiene nombre, edad, oficio, perfil, historia, personalidad, ingresos, skills, necesidades y una vista previa de su teléfono. El usuario puede cambiar la selección antes de iniciar. Cada agente recibe un `Phone` propio y una carpeta privada `agents/<id>/`.

### 5.2 Configuración de corrida

```ts
interface RunConfig {
  runId: string;
  agentIds: string[];          // 10 por defecto
  repetitions: number;         // 5 por defecto
  days: number;                // 28 por defecto
  seed: number;
  mode: "mock" | "llm" | "hybrid";
  model: {
    provider: string;
    model: string;
    temperature: number;
    maxTokens: number;
  };
  movementPointsPerDay: number;       // 20
  conversationPointsPerDay: number;   // 2 (1 para la primera corrida)
  messagesPerChatSession: number;     // 10
  chatSessionCost: number;            // 1 punto por sesión nueva
  maxToolCallsPerTurn: number;        // 5
  announcements: string[];            // anuncios semilla
}
```

### 5.3 Ubicaciones, edificios y casas

```ts
interface Location {
  id: string;
  q: number;
  r: number;
  type: "plaza" | "street" | "building" | "house" | "obstacle";
  name: string;
  walkable: boolean;
}

interface Building {
  id: string;
  type: "municipalidad" | "hospital" | "comisaria" | "fiscalia" | "escuela" | "almacen" | "supermercado" | "plaza";
  locationId: string;
  businessId?: string;
}

interface House {
  id: string;
  locationId: string;
  agentId: string;
}
```

### 5.4 Ofertas, inventario y transacciones

```ts
interface Offer {
  id: string;
  agentId: string;
  type: "producto" | "servicio";
  category: string;
  description: string;
  priceCredits: number;
  stock: number;
  locationId: string;
  delivery: "in_person" | "remote";
  status: "disponible" | "reservada" | "vendida" | "cancelada";
}

interface Transaction {
  id: string;
  buyerId: string;
  sellerId: string;
  offerId: string;
  amount: number;
  lotIds: string[];
  status: "pendiente" | "en_escrow" | "confirmada" | "disputada" | "cancelada";
  delivery: "in_person" | "remote";
  createdAt: string;
  confirmedAt?: string;
}
```

### 5.5 Lote de crédito

```ts
interface CreditLot {
  id: string;
  ownerId: string;
  amount: number;
  receivedAt: string;
  expiresAt: string;
  origin: "emision_inicial" | "venta" | "cambio" | "sancion";
  parentId: string | null;
  status: "activo" | "gastado" | "vencido" | "partido";
}
```

### 5.6 Anuncio, evento, teléfono, chat y caso

```ts
interface WorldEvent {
  id: string;
  runId: string;
  day: number;
  type: string;
  agentId?: string;
  payload: Record<string, unknown>;
  createdAt: string;
}

interface Phone {
  id: string;
  ownerId: string;
  number: string;
  contacts: string[];
  notifications: string[];
  cityGroupId: string;
  battery: number;
  locked: boolean;
}

interface ChatSession {
  id: string;
  channel: "direct" | "city_group";
  participantIds: string[];
  startedDay: number;
  messageCount: number;
  pointCost: number;
  status: "abierta" | "cerrada";
}

interface ChatMessage {
  id: string;
  sessionId: string;
  fromId: string;
  toId: string | null;
  channel: "direct" | "city_group";
  text: string;
  day: number;
  trusted: false;
}

interface Case {
  id: string;
  type: "reclamo" | "incumplimiento" | "estafa" | "apelacion";
  status: "abierto" | "en_mediacion" | "resuelto" | "archivado";
  complainantId: string;
  accusedId?: string;
  transactionId?: string;
  description: string;
  evidence: string[];
  resolution?: string;
  sanction?: string;
  openedDay: number;
  closedDay?: number;
}
```

## 6. Ciclo de vida del crédito

```text
emisión inicial o venta
        ↓
   lote activo
   ├─ se gasta (FIFO)
   ├─ se transfiere → lote nuevo para el receptor
   ├─ se parte → el remanente conserva su vencimiento
   └─ vence en posesión → sale de circulación
```

- **Emisión.** Cada oferta puede emitir hasta su precio por stock, limitado por el cupo acumulado del agente. El mock de aceptación usa 600 créditos por agente como techo por corrida. Si se agota, las ofertas siguientes siguen disponibles para el intercambio.
- **Venta:** el comprador paga con sus lotes; el motor consume primero los que vencen antes (FIFO). El vendedor recibe un lote nuevo con un plazo completo desde la recepción.
- **Transferencia:** cada transferencia crea un lote nuevo para el receptor; el reloj se reinicia para ese lote.
- **Vencimiento:** vence el lote que queda quieto, no todo el saldo del agente. La app muestra el saldo desglosado por vencimiento.
- **Partición.** El remanente conserva el vencimiento anterior. Un lote nuevo queda enlazado con su padre. La retención en escrow conserva el vencimiento original para eventuales devoluciones.
- **Compromiso.** Cada oferta registra como compromiso el monto que respaldó. Las entregas confirmadas lo reducen por su valor y el vencimiento de los créditos deja vigente el compromiso. El rechazo explícito o tres días sin respuesta a una solicitud financiada pueden suspender al vendedor mientras conserve compromiso pendiente. El mock usa suspensiones de 1, 7 o 28 días según el escenario.
- **Escrow.** `buy` retiene pago y stock. El vendedor acepta y el comprador confirma la entrega. La confirmación libera el pago con un plazo completo. El rechazo o la falta de respuesta devuelven pago y stock. Una venta aceptada que sigue sin confirmación al sexto día también se devuelve y queda registrada sin atribuirle incumplimiento al vendedor. La devolución conserva el vencimiento original y se registra como vencida si el plazo ya pasó.

**Invariantes**

- La suma de lotes activos de un agente nunca es negativa.
- Un lote vencido no se puede transferir.
- Los créditos emitidos son iguales a la suma de créditos vigentes, retenidos y vencidos.
- Cada lote tiene un único padre, salvo la emisión inicial.
- La suma de los hijos de una partición es igual al padre.
- Ninguna acción puede crear créditos sin una emisión o una venta válida.

## 7. Modos de simulación y modelo

| Modo | Qué hace | Cuándo usarlo | Costo |
|---|---|---|---|
| Mock | Agente con reglas fijas o aleatorias | Pruebas del entorno, métricas y reproducibilidad | 0 |
| LLM | Agente con modelo de lenguaje | Explorar comportamiento emergente y diálogo | Variable |
| Híbrido | Mock para el mercado, LLM para decisiones clave | Equilibrio costo/realismo | Medio |

**Recomendación:** construir primero el modo mock. El modo LLM se habilita por configuración, no por código duplicado.

### 7.1 Configuración `.env`

```dotenv
# Copiar a .env y completar. No commitear .env.
LLM_PROVIDER=deepseek
LLM_MODEL=deepseek-v4.1-flash
LLM_BASE_URL=https://api.deepseek.com/v1
LLM_API_KEY=
LLM_TEMPERATURE=0.5
LLM_MAX_TOKENS=800

SIM_MODE=hybrid          # mock | llm | hybrid
SIM_AGENTS=10
SIM_REPETITIONS=5
SIM_DAYS=28
SIM_MOVEMENT_POINTS=20
SIM_CONVERSATION_POINTS=2
SIM_MESSAGES_PER_CHAT=10
SIM_CHAT_SESSION_COST=1
SIM_MAX_TOOL_CALLS=5
SIM_SEED=42
```

- El modelo por ahora es **DeepSeek v4.1 Flash**. Si el proveedor usa otro identificador, se cambia solo en `.env`.
- La API key va en `.env`, nunca en el repositorio ni en una nota.
- El adaptador es OpenAI-compatible: cambiar de proveedor no cambia el contrato de tools.
- Si no hay API key, el simulador arranca en `mock` y lo informa.

## 8. Stack recomendado

| Capa | Opción | Motivo |
|---|---|---|
| Lenguaje | TypeScript + Node 22 | Tipos compartidos entre motor, tools y UI |
| Esquemas | Zod | Validación del contrato de acción y de los hooks |
| Persistencia | SQLite (`better-sqlite3`) + JSONL | Fuente de verdad + log append-only |
| Migraciones | SQL simple o Drizzle | Cambios reproducibles |
| Logs | Pino | JSON estructurado |
| Pruebas | Vitest | Tests rápidos de reglas y gateway |
| UI | React + Vite | Configuración y observador en tiempo real |
| Mapa | SVG/Canvas o PixiJS | Hexágonos, movimiento y capas |
| Tiempo real | SSE para MVP; WebSocket después | Simple y suficiente |
| Gráficos | Chart.js o Vega-Lite | Informe automático |
| Configuración | `.env` + JSON/YAML | Fácil de editar y versionar |
| Runner | `tsx` | Ejecutar TypeScript sin build en desarrollo |
| Paquete | pnpm | Instalación reproducible |

**Proceso único:** el MVP corre en un solo proceso secuencial. No hay cola de trabajos ni workers de agentes en paralelo; los hooks usan `worker_threads` solo para aislamiento y timeout. Si la corrida crece, se agrega una cola después.

**Por qué SQLite:** permite transacciones atómicas, consultas de estado, índices por agente/día y reconstrucción de saldos. JSONL se usa como log append-only para auditoría y replay, no como fuente de verdad.

## 9. UI y configuración

### 9.1 Antes de iniciar

La UI debe permitir:

- Elegir **qué agentes** arrancan, no solo la cantidad. Cada tarjeta muestra nombre, edad, oficio, perfil, historia, personalidad, ingresos, skills y necesidades.
- Definir **10 agentes** por defecto y **5 repeticiones**.
- Elegir días (28 por defecto), semilla, modo (`mock`, `llm`, `hybrid`) y modelo.
- Configurar **puntos de conversación por día**, **mensajes por sesión** (10) y **costo por sesión** (1).
- Ver el costo estimado de chats y el techo de llamadas antes de iniciar.
- Ver y editar los anuncios semilla y las notificaciones que recibirán los teléfonos.
- Iniciar, pausar y reiniciar la corrida.

### 9.2 Durante la corrida

- Mapa de hexágonos con plaza, edificios, casas y agentes.
- Movimiento en tiempo real y estela de recorrido.
- Panel de agente: cash, créditos por vencer, inventario, energía, reputación, ubicación, puntos de movimiento y puntos de conversación.
- Ofertas activas, transacciones y disputas.
- Tablero de anuncios.
- Panel de teléfono: perfil, notificaciones, grupo de la ciudad, mensajes directos, billetera, memorias y contactos.
- Panel de Fiscalía: casos abiertos, en mediación y resueltos.
- Feed de diálogos y eventos.
- Métricas del día: intercambios, emisión, vencimiento, circulación, Gini, sanciones, sesiones de chat y costo.

### 9.3 Tablero de eventos (futuro)

La idea a futuro es un tablero donde el usuario escribe el tipo de evento y todas sus variables, y lo inyecta al mundo. Se implementa con **eventos declarativos**, no con código:

1. Elegir tipo: fiesta, repunte, recesión, corte de ruta, reposición, exención.
2. Definir alcance, categoría, título, texto, días de inicio/fin.
3. Elegir efectos y parámetros (`demand_multiplier`, `cash_transfer`, etc.).
4. Ver el JSON resultante.
5. Inyectar; el `event-injector` lo aplica al inicio del día siguiente.
6. Queda registrado en el `EventLog` con autor y fecha.

**Seguridad:** la UI no ejecuta scripts, no escribe en SQLite directamente y no puede crear hooks. Solo crea `Announcement` + `effects` validados por Zod.

## 10. Reproducibilidad

Cada corrida guarda:

- `run_id`, fecha y responsable.
- `RunConfig` completa.
- Roster de agentes y preset de cada uno.
- Semilla.
- Versión del código (commit).
- Versión de los prompts.
- Versión del toolbelt y de los schemas.
- Versión de los hooks.
- Proveedor y versión del modelo.
- Temperatura y límite de tokens.
- Puntos de conversación, mensajes por sesión y costo por sesión.
- Anuncios, notificaciones y eventos inyectados.
- Teléfonos, sesiones de chat y casos de Fiscalía.
- Costo estimado y real.
- Datos crudos y eventos.

**Prueba de reproducibilidad:** dos corridas mock con la misma configuración, roster y semilla deben dar el mismo resultado.

## 11. Control de costos

- Estimar tokens por llamada antes de correr.
- Poner un límite duro por corrida y por agente.
- Usar caché de prompts repetidos.
- Resumir memoria para no reenviar todo el historial.
- Limitar el diálogo a 10 mensajes por sesión y a los puntos de conversación por día.
- Usar modo mock para pruebas.
- Empezar con 10 agentes y 1 punto de conversación por día; escalar solo si hay señal.
- Registrar costo por escenario, por agente y por sesión de chat.
- Si el proveedor es gratuito o está incluido en una suscripción, registrar igual el consumo para comparar.

**Ejemplo de volumen:** 10 agentes × 28 días × 5 repeticiones = **1.400 turnos**; con hasta 5 tool calls por turno, el techo es 7.000 llamadas. Con 1 punto de conversación por día y 10 mensajes por sesión, el techo adicional es **1.400 sesiones** y **14.000 mensajes**. Con 2 puntos, se duplica. El límite duro se calcula antes de correr y incluye los chats.

## 12. Observabilidad

- Logs estructurados en JSONL.
- Un `run_id` por corrida.
- Eventos con día, agente, tool, motivo, resultado y costo.
- Errores con stack trace y prompt asociado.
- Métricas por día y al cierre.
- Reporte de costo por corrida.
- Trazas de movimiento y de transacciones para la UI.
- Replay desde `events.jsonl` para auditar una corrida.

## 13. Pruebas

| Prueba | Qué verifica |
|---|---|
| Test de emisión | No se emite sin oferta ni por encima del techo |
| Test de transferencia | Los saldos cuadran y el lote cambia de dueño |
| Test de vencimiento | Un lote vencido no se transfiere |
| Test de partición | La suma de hijos es igual al padre |
| Test de FIFO | Se gastan primero los lotes que vencen antes |
| Test de sanción | La sanción se aplica y se registra |
| Test de acción inválida | El agente pierde la acción y se registra |
| Test de identidad | Un agente no puede actuar sobre otro |
| Test de tool no permitida | El gateway rechaza tools fuera del toolbelt |
| Test de movimiento | 20 puntos, costo por hexágono y multi-move |
| Test de anuncios | Todos ven el anuncio; solo el motor aplica efectos |
| Test de teléfono | Solo el dueño lee perfil privado, memorias y billetera |
| Test de chat | 10 mensajes por sesión y 1 punto por sesión nueva |
| Test de grupo de la ciudad | Publicar consume sesión; leer es gratis |
| Test de Fiscalía | Un caso se registra, media y resuelve con sanción |
| Test de hook | Un hook sin permiso no puede escribir el ledger |
| Test de prompt injection | Un `talk` malicioso no ejecuta tools |
| Test de reproducibilidad | Misma semilla, mismo resultado |
| Test de costo | El límite detiene la corrida |

## 14. Seguridad y privacidad

- No usar datos personales reales.
- No incluir credenciales en el repositorio; `.env` queda fuera de Git.
- No ejecutar código generado por agentes, usuarios o anuncios.
- No permitir llamadas externas desde el agente.
- Sanitizar prompts y salidas.
- Guardar los datos en una carpeta local o repositorio privado.
- Revisar los términos del proveedor de LLM.
- Tratar los mensajes de `talk` como datos no confiables.
- El teléfono es privado: solo el dueño ve perfil completo, memorias y billetera; el resto ve un perfil público acotado.
- Auditar toda acción que mueva créditos, stock o abra un caso en la Fiscalía.

## 15. Decisiones tomadas y pendientes

### Tomadas

| Decisión | Elección |
|---|---|
| Lenguaje | TypeScript + Node 22 |
| Persistencia | SQLite como fuente de verdad + JSONL append-only |
| Proceso | Un solo proceso secuencial para el MVP |
| Diálogo | Libre, con acciones estructuradas |
| Modelo | DeepSeek v4.1 Flash por `.env`; adaptador OpenAI-compatible |
| Agentes | 10 por corrida, elegidos por el usuario en la UI |
| Repeticiones | 5 por escenario |
| Movimiento | 20 puntos por día/ronda; 1 punto por hexágono; múltiples movimientos |
| Conversación | 10 mensajes por agente por sesión; 1 punto por sesión nueva; 2 puntos por día (1 en la primera corrida) |
| Teléfono | Perfil, anuncios, grupo de la ciudad, mensajes, billetera y memorias; privado para el dueño |
| Fiscalía | Denuncias, mediación, investigación, sanción y apelación; `case-review` en el MVP |
| ADK | No como núcleo; spike opcional detrás de `AgentRuntime` |
| Anuncios | Visibles para todos; efectos declarativos aplicados por el motor/hook; notificación al teléfono |
| UI | Configuración previa + observador read-only |
| Hooks | Solo el equipo; los agentes no los escriben |
| Informe | Automático en Markdown + gráficos |

### Pendientes

| Decisión | Opciones | Responsable |
|---|---|---|
| Montos de sueldo y plan social | Por confirmar | Hernán / Rodrigo |
| Comportamiento del supermercado en etapa 2 | Exención de ABL, aceptación de créditos, ambas | Hernán / Rodrigo |
| Día simulado | 1 día = 1 ronda; duración de la jornada | Rodrigo |
| Roster definitivo de 10 agentes | Perfiles, oficios e historias | Hernán / Rodrigo |
| API key y endpoint | DeepSeek directo u OpenCode Go | Rodrigo |
| Esquema de efectos de eventos | Lista inicial ya definida; ampliar | Rodrigo |
| Anuncios de la municipalidad | Manual, hook o política | Hernán / Rodrigo |
| Radio del mapa | 5 hexágonos; ajustar según densidad | Rodrigo |
| Puntos de conversación por día | 1, 2 o 3; empezar con 1 | Rodrigo |
| Proceso de Fiscalía | Solo a denuncia o también de oficio | Hernán / Rodrigo |
| Privacidad del teléfono | Qué es público y qué queda para el dueño | Rodrigo |
| Moderación del grupo | Rate limit, reglas o moderador del sistema | Rodrigo |
| Formato del informe | Markdown + gráficos; PDF/slides después | Rodrigo / Hernán |

## Enlaces

- [[Proyecto - Simulacion agentica|Proyecto — Simulación agéntica]]
- [[00A - Concepto y modelo economico|Concepto y modelo económico]]
- [[02 - Requisitos|Requisitos]]
- [[03 - Diseno experimental|Diseño experimental]]
- [[05 - Prompts y perfiles|Prompts y perfiles]]
- [[06 - Recursos y presupuesto|Recursos y presupuesto]]
- [[07 - Checklist de ejecucion|Checklist de ejecución]]
- [[08 - Evaluacion ADK|Evaluación ADK]]
