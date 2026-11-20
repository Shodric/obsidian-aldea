---
tipo: documento
estado: borrador
area: tecnologia
proyecto: "[[Proyecto - Simulacion agentica]]"
actualizado: 2026-11-20
---

# Arquitectura técnica — Simulación agéntica

> [!info] Decisión de base
> Empezar con un **modo deterministico** que no dependa de un LLM. El modo con lenguaje se agrega como una capa reemplazable. Así se prueba el circuito, se validan las métricas y se controla el costo antes de gastar en llamadas.

## 1. Principios

- **Separar el entorno del agente**: las reglas del circuito no dependen del modelo de lenguaje.
- **Un solo contrato de acción**: todos los agentes devuelven el mismo esquema JSON.
- **Todo evento se registra**: si no está en el log, no ocurrió.
- **Reproducible por diseño**: configuración, semilla y versión del modelo guardadas.
- **Modelo agnóstico**: un adaptador traduce el proveedor elegido al contrato interno.
- **Barato por defecto**: modo mock para pruebas; LLM solo cuando aporta.

## 2. Componentes

| Componente | Responsabilidad | Entrada | Salida |
|---|---|---|---|
| Orquestador | Ejecuta la corrida y coordina el bucle | Configuración | `run_id`, estado final |
| Reloj | Avanza turnos y dispara eventos | Configuración | Turno actual |
| Entorno | Mercado, ofertas, precios, reglas | Estado + acciones | Estado actualizado |
| Runtime de agentes | Decide la acción de cada agente | Observación + memoria | Acción JSON |
| Adaptador de modelo | Llama al LLM o al mock | Prompt + configuración | Texto/JSON |
| Motor de reglas | Emisión, transferencia, vencimiento, sanción | Acción + estado | Eventos |
| Ledger | Registra lotes de crédito y transferencias | Eventos | Saldos y linaje |
| Memoria | Resume y recupera interacciones | Eventos + mensajes | Resumen por agente |
| Métricas | Calcula indicadores al cierre y por turno | Eventos | Tabla de métricas |
| Logger | Persiste eventos, prompts y errores | Todo | JSONL/SQLite |
| Generador de informe | Produce Markdown y gráficos | Métricas + eventos | Informe |
| Control de costo | Estima y limita el gasto | Uso de tokens | Corte o alerta |

## 3. Flujo de un turno

```text
para cada día en 1..D:
    para cada agente en orden aleatorio con semilla:
        observacion = entorno.observar(agente)
        memoria = memoria.resumen(agente)
        prompt = construir_prompt(agente, observacion, memoria)
        respuesta = modelo.generar(prompt)
        accion = parsear_y_validar(respuesta)
        eventos = reglas.aplicar(agente, accion, entorno)
        ledger.registrar(eventos)
        memoria.actualizar(agente, eventos)
        logger.registrar(agente, prompt, respuesta, accion, eventos)
    reglas.cerrar_dia()
    metricas.calcular_dia()
    control_costo.verificar()
```

**Reglas de orden**

- El orden de los agentes se baraja con la semilla de la corrida.
- Las acciones se aplican en orden, no en paralelo, para que el estado sea consistente.
- Si una acción es inválida, se registra el error y el agente pierde el turno.
- Si una llamada al modelo falla, se reintenta hasta N veces y luego se usa una acción de espera.

## 4. Modelo de datos

### Agente

```json
{
  "id": "a01",
  "nombre": "Marta",
  "perfil": "optimista",
  "oficio": "cocinera",
  "recursos": {"tiempo_horas": 20, "productos": ["empanadas"]},
  "necesidades": ["arreglar canilla", "comprar ropa"],
  "personalidad": {"confianza": 0.8, "riesgo": 0.3, "sociabilidad": 0.7},
  "creditos": 0,
  "memoria": [],
  "estado": "activo"
}
```

### Oferta

```json
{
  "id": "o01",
  "agente_id": "a01",
  "tipo": "producto",
  "categoria": "comida",
  "descripcion": "docena de empanadas",
  "precio_creditos": 1200,
  "stock": 10,
  "estado": "disponible"
}
```

### Lote de crédito

```json
{
  "id": "c01",
  "propietario_id": "a01",
  "monto": 5000,
  "emitido_en": "2026-11-20T10:00:00",
  "vence_en": "2026-12-20T10:00:00",
  "origen": "emision",
  "parent_id": null,
  "estado": "activo"
}
```

### Acción

```json
{
  "accion": "comprar",
  "parametros": {"oferta_id": "o01", "monto": 1200},
  "motivo": "Necesito empanadas para la semana y tengo créditos por vencer.",
  "mensaje": "¿Me vendés una docena?"
}
```

## 5. Ciclo de vida del crédito

```text
emitido → activo → transferido → activo (nuevo vencimiento)
                     ↓
                  vencido
```

- **Emitido:** se crea contra una oferta y dentro del techo.
- **Activo:** puede transferirse o dividirse.
- **Transferido:** cambia de dueño; el nuevo lote recibe un vencimiento renovado.
- **Vencido:** queda fuera de circulación y se registra.
- **Partido:** un lote se divide en dos o más lotes hijos.

**Invariantes**

- La suma de lotes activos de un agente nunca es negativa.
- Un lote vencido no se puede transferir.
- La suma de créditos emitidos es igual a la suma de activos, usados y vencidos.
- Cada lote tiene un único padre, salvo la emisión.

## 6. Modos de simulación

| Modo | Qué hace | Cuándo usarlo | Costo |
|---|---|---|---|
| Mock | Agente con reglas fijas o aleatorias | Pruebas del entorno y de las métricas | 0 |
| LLM | Agente con modelo de lenguaje | Explorar comportamiento emergente | Variable |
| Híbrido | Mock para el mercado, LLM para decisiones clave | Equilibrio costo/realismo | Medio |

**Recomendación:** construir primero el modo mock. El modo LLM se habilita por configuración, no por código duplicado.

## 7. Stack recomendado

| Capa | Opción | Motivo |
|---|---|---|
| Lenguaje | Python 3.11+ | Ecosistema de datos y prototipado rápido |
| Esquemas | Pydantic | Validación del contrato de acción |
| Persistencia | SQLite + JSONL | Simple, portable y auditable |
| Análisis | pandas | Métricas y tablas |
| Gráficos | matplotlib | Gráficos reproducibles |
| Informe | Jinja2 + Markdown | Plantillas y salida legible |
| Pruebas | pytest | Tests de reglas |
| LLM | Adaptador OpenAI-compatible | Permite cambiar de proveedor |
| Configuración | YAML + `.env` | Fácil de editar y versionar |
| Control de versiones | Git | Reproducibilidad |

**Alternativa:** TypeScript/Node si se prefiere compartir código con el MVP web. No cambia el diseño conceptual.

## 8. Reproducibilidad

Cada corrida guarda:

- `run_id`, fecha y responsable.
- Configuración completa.
- Semilla.
- Versión del código (commit).
- Versión del prompt.
- Proveedor y versión del modelo.
- Temperatura y límite de tokens.
- Costo estimado y real.
- Datos crudos.

**Prueba de reproducibilidad:** correr dos veces el modo mock con la misma configuración y semilla debe dar el mismo resultado.

## 9. Control de costos

- Estimar tokens por llamada antes de correr.
- Poner un límite duro por corrida.
- Usar caché de prompts repetidos.
- Resumir memoria para no reenviar todo el historial.
- Limitar el diálogo a N turnos.
- Usar modo mock para pruebas.
- Empezar con 10 agentes; escalar solo si hay señal.
- Registrar costo por escenario y por agente.

## 10. Observabilidad

- Logs estructurados en JSONL.
- Un `run_id` por corrida.
- Eventos con turno, agente, acción y motivo.
- Errores con stack trace y prompt asociado.
- Métricas por día y al cierre.
- Reporte de costo por corrida.

## 11. Pruebas

| Prueba | Qué verifica |
|---|---|
| Test de emisión | No se emite sin oferta ni por encima del techo |
| Test de transferencia | Los saldos cuadran y el lote cambia de dueño |
| Test de vencimiento | Un lote vencido no se transfiere |
| Test de partición | La suma de hijos es igual al padre |
| Test de sanción | La sanción se aplica y se registra |
| Test de acción inválida | El agente pierde el turno y se registra |
| Test de reproducibilidad | Misma semilla, mismo resultado |
| Test de costo | El límite detiene la corrida |

## 12. Seguridad y privacidad

- No usar datos personales reales.
- No incluir credenciales en el repositorio.
- No ejecutar código generado por agentes.
- No permitir llamadas externas desde el agente.
- Sanitizar prompts y salidas.
- Guardar los datos en una carpeta local o repositorio privado.
- Revisar los términos del proveedor de LLM.

## 13. Decisiones abiertas

1. ¿Python o TypeScript?
2. ¿SQLite o archivos JSONL?
3. ¿Un solo proceso o cola de trabajos?
4. ¿Se simula diálogo libre o mensajes plantilla?
5. ¿Se usa un modelo gratuito o DeepSeek?
6. ¿Cuántas repeticiones y semillas?
7. ¿Se corre en local o en la nube?
8. ¿El informe se genera automáticamente o se escribe a mano?

## Enlaces

- [[Proyecto - Simulacion agentica|Proyecto — Simulación agéntica]]
- [[02 - Requisitos|Requisitos]]
- [[03 - Diseno experimental|Diseño experimental]]
- [[05 - Prompts y perfiles|Prompts y perfiles]]
- [[06 - Recursos y presupuesto|Recursos y presupuesto]]
