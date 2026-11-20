# Aldea — Vault de proyecto

## Identidad

- **Proyecto**: Aldea — red de intercambio local con créditos que vencen.
- **Tipo**: proyecto web3 de infraestructura para una economía complementaria. En etapa de diseño y simulación; no es una empresa, cooperativa ni fundación constituida.
- **Alcance**: circuito de trueque con créditos gratuitos, caducos y respaldados por la oferta de productos y servicios de cada participante. Gobernanza por DAO/asociación local y capa de smart contracts.
- **Impulsor**: Hernán (Azul, Buenos Aires).
- **Tecnología y datos**: Rodrigo.
- **Ubicación**: Buenos Aires, Argentina. El primer piloto se evalúa en el conurbano; Azul queda como segundo escenario.
- **Documento base**: llamada con Hernán registrada el 2026-11-20. Fecha exacta de la llamada: por confirmar.
- **Fuente primaria**: [[04 - Reuniones/2026/11-Noviembre/2026-11-20 - Llamada con Hernan - Transcripcion|Transcripción editada]] · [[16 - Archivo/2026/transcripcion_original.txt|Transcripción automática original]].

> **Principio rector**: primero la economía real, después la tecnología. La blockchain es una capa de garantía y trazabilidad, no un fin. El MVP se prueba con créditos de intercambio, sin token de recompensa y sin dinero real de por medio.

## Qué es y qué no es

| Es | No es |
|---|---|
| Un circuito de trueque con una unidad de cuenta local | Una moneda paralela o de curso legal |
| Un crédito gratuito que vence mientras está quieto | Un activo de inversión o un token con expectativa de rentabilidad |
| Una red de personas que ofrecen bienes, servicios y oficios | Un marketplace con dinero fiduciario |
| Una DAO/asociación local que actúa como contraparte y garante | Una plataforma sin gobierno ni resolución de conflictos |
| Una herramienta para crear demanda donde no hay dinero | Un reemplazo de la economía formal |

## Estructura del vault

| Carpeta | Área | Contenido |
|---|---|---|
| `00 - Centro de Mando` | Dirección | Dashboard, prioridades, kanban del vault |
| `01 - Inbox` | Entrada | Notas sueltas para procesar |
| `02 - Gobernanza y Comunidad` | Gobernanza | DAO, asamblea, membresía, identidad, sanciones |
| `03 - Direccion y Estrategia` | Dirección | Documento ejecutivo, diagnóstico, modelo, roadmap, decisiones, riesgos |
| `04 - Reuniones` | Operación | Actas, apuntes y transcripciones |
| `05 - Finanzas y Tesoreria` | Finanzas | Presupuesto, fuentes, tesorería y fondos |
| `06 - Equipo y Roles` | Organización | Roles, responsabilidades y colaboradores |
| `07 - Tecnologia y Producto` | Tecnología | Arquitectura, MVP, simulación, seguridad, stack |
| `08 - Proyectos` | Proyectos | Simulación, MVP, piloto, marco legal, pitch |
| `09 - Alianzas y Ecosistema` | Alianzas | Mapa de aliados y pipeline de contactos |
| `10 - Modelo Economico y Tokenomia` | Economía | Créditos, vencimiento, precios, token de recompensa |
| `11 - Convenios y Contratos` | Legal | Convenios, contratos y vencimientos |
| `12 - Procesos y SOPs` | Operación | Alta de oferta, intercambio, sanciones, ciclos |
| `13 - Legal y Cumplimiento` | Legal | Marco regulatorio, datos, contratos, DAO |
| `14 - Comunicacion y Marketing` | Comunicación | Mensajes clave, FAQ, kit institucional |
| `15 - Reportes e Indicadores` | Evaluación | KPIs, marco de evaluación del piloto, reportes |
| `16 - Archivo` | Archivo | Documentos fuente y versiones históricas |
| `99 - Templates` | Sistema | Plantillas de notas |

## Reglas del vault

### Frontmatter YAML
Toda nota debe tener al menos:

```yaml
---
tipo: proyecto
estado: activo
area: proyectos
actualizado: 2026-11-20
---
```

**Tipos válidos**: `acta`, `aliado`, `apuntes`, `comunicado`, `dashboard`, `decision`, `diagnostico`, `documento`, `faq`, `indice`, `kpi_set`, `mapa`, `modelo`, `normativa`, `plan`, `politica`, `proyecto`, `reunion`, `riesgo`, `roadmap`, `sop`, `transcripcion`.

**Estados válidos**: `activo`, `en_curso`, `pendiente`, `propuesta`, `borrador`, `bloqueado`, `cerrado`, `historico`.

### Nomenclatura
- Reuniones: `2026-11-20 - Llamada con Hernan - Apuntes.md`
- Transcripciones: `2026-11-20 - Llamada con Hernan - Transcripcion.md`
- Decisiones: `2026-11-20 - Decision - Tema.md`
- Proyectos: `Proyecto - Nombre.md`
- Proyectos con documentación de soporte: carpeta `Proyecto - Nombre/` con la nota principal `Proyecto - Nombre.md` y documentos numerados (`01 - Plan...`, `02 - Requisitos...`, `03 - Diseno...`).
- Riesgos: `Riesgo - Nombre.md`
- Procesos: `SOP - Area - Proceso.md`
- Índices: `Indice - Area.md`
- Carpetas sin tildes ni ñ (evita duplicados NFD/NFC entre macOS y Linux).

### Dataview
- Las queries **no llevan prefijo del vault**. Correcto: `FROM "08 - Proyectos"`.
- Usar `tipo:` y `estado:` como filtros principales.
- Los índices se autopueblan; no editar tablas a mano.

### Integridad de la información
- No inventar datos: si falta un dato, escribir `por confirmar` y marcarlo en el kanban.
- Distinguir siempre **propuesta** de **decisión tomada**.
- No cargar datos personales sensibles ni información de salud.
- Las cifras de la llamada (20.000–100.000 ARS, 10.000 ARS de ingreso básico, USD 10–30 de simulación) son **ejemplos**, no parámetros aprobados.

## Datos clave del proyecto

- **Dos unidades**: crédito de intercambio (gratuito, caduco, fungible) y token de recompensa (permanente, fungible, **no** en el MVP).
- **Un mecanismo**: el crédito vence en posesión y renueva su plazo al transferirse (modelo UTXO).
- **Una contraparte**: la DAO/asociación local es la deudora y garante; la obligación del participante no vence con el crédito.
- **Cuatro fases**: simulación y validación → diseño legal y territorial → MVP y piloto → evaluación, token de recompensa y réplica.
- **Un principio económico**: crear demanda donde no hay dinero; complementar la economía formal, no sustituirla.
- **Un principio técnico**: empezar simple; blockchain solo cuando resuelva un problema real de confianza o trazabilidad.

## Glosario mínimo

| Término | Definición |
|---|---|
| **Crédito de intercambio** | Unidad de cuenta gratuita y caduca que representa el derecho a recibir bienes o servicios del circuito. |
| **Vencimiento en posesión** | El crédito pierde validez mientras está quieto en una wallet; al transferirse, el nuevo tenedor recibe un plazo renovado. |
| **UTXO** | Modelo de contabilidad de Bitcoin: cada crédito es una salida no gastada que se puede partir y transferir. |
| **Prosumidor** | Participante que produce y consume dentro del circuito. |
| **Ciclo** | Período de apertura, circulación y cierre del circuito (por ejemplo, 4 semanas). |
| **DAO** | Organización autónoma descentralizada; en Aldea, la capa de gobierno y la contraparte de los contratos. |
| **Token de recompensa** | Token permanente y fungible que se evalúa para fases posteriores; no forma parte del MVP. |
| **Bono municipal** | Instrumento de fomento local canjeable por descuentos o servicios; no es moneda de curso legal. |

## Regla de oro

Si el circuito no le mejora la vida a la persona que hoy no tiene dinero ni demanda para su trabajo, no se implementa. La tecnología se elige al final, debe ser reemplazable, de bajo costo y de código abierto.
