---
tipo: documento
estado: borrador
area: tecnologia
proyecto: "[[Proyecto - Simulacion agentica]]"
actualizado: 2026-11-20
---

# Requisitos — Simulación agéntica

> [!info] Cómo leer este documento
> Los requisitos están escritos para un **laboratorio de diseño**, no para un producto. La prioridad es aprender y comparar escenarios, no cubrir todos los casos reales. Cada requisito tiene un criterio de aceptación verificable.

## 1. Requisitos funcionales

| ID | Requisito | Prioridad | Criterio de aceptación |
|---|---|---|---|
| RF-01 | Configurar una corrida desde un archivo | Must | Un `RunConfig` + `.env` define agentes, perfiles, ciclo, vencimiento, precios, sanciones, semilla y modelo |
| RF-02 | Crear agentes con perfil, recursos, necesidades, historia y personalidad | Must | Cada agente tiene los campos del esquema y un perfil asignado |
| RF-03 | Publicar ofertas con precio en créditos | Must | Un agente puede ofrecer un bien o servicio con categoría, precio y stock |
| RF-04 | Ejecutar un toolbelt cerrado | Must | El agente solo puede pedir tools permitidas; el motor valida schema, identidad y precondiciones |
| RF-05 | Emitir créditos contra una oferta | Must | La emisión queda registrada, es proporcional a la oferta y respeta el techo por agente |
| RF-06 | Transferir y dividir créditos | Must | Una transferencia puede partir un lote en dos y conservar trazabilidad y vencimiento |
| RF-07 | Aplicar vencimiento por lote | Must | Cada crédito recibido genera un lote con su propio vencimiento; el gasto usa FIFO |
| RF-08 | Aplicar compromiso mínimo y sanciones | Must | Se puede sancionar la negativa a vender con demanda; no se sanciona la falta de demanda |
| RF-09 | Confirmar entrega con código | Should | Una compra puede cerrarse con un código o confirmación explícita; las entregas diferidas usan escrow |
| RF-10 | Dialogar 1 a 1 y en grupo | Should | Los agentes pueden enviar y recibir mensajes con contexto en el mismo hexágono |
| RF-11 | Mantener memoria | Must | Cada agente tiene un resumen de interacciones y percepciones |
| RF-12 | Registrar todos los eventos | Must | Cada acción queda en un log con timestamp, agente, tool, motivo y resultado |
| RF-13 | Calcular métricas | Must | El sistema calcula las métricas del diseño experimental al cerrar la corrida |
| RF-14 | Generar informe y gráficos | Should | Se produce un Markdown con tablas y al menos 4 gráficos |
| RF-15 | Reproducir una corrida | Must | Con la misma configuración, semilla y modo mock, el resultado es idéntico |
| RF-16 | Comparar escenarios | Should | El sistema puede correr E1-E8 y generar una tabla comparativa |
| RF-17 | Detener una corrida por costo | Must | Si el gasto estimado supera el límite, la corrida se detiene y avisa |
| RF-18 | Exportar datos crudos | Must | Los eventos, transacciones y mensajes se exportan a CSV/JSONL/SQLite |
| RF-19 | Mundo de hexágonos y movimiento | Must | Cada agente tiene 20 puntos por día; moverse cuesta 1 por hexágono y se puede repetir |
| RF-20 | Tablero de anuncios | Must | Todos los agentes ven los anuncios activos; los efectos declarativos los aplica el motor o un hook |
| RF-21 | UI de configuración y observación | Should | Antes de iniciar se eligen agentes, repeticiones, días, semilla y anuncios; durante la corrida se ve el mapa y el estado |

## 2. Requisitos de datos

| ID | Entidad | Campos mínimos |
|---|---|---|
| RD-01 | Agente | `id`, `nombre`, `perfil`, `oficio`, `historia`, `recursos`, `necesidades`, `personalidad`, `memoria`, `creditos`, `efectivo`, `movimiento`, `casa_id`, `estado` |
| RD-02 | Oferta | `id`, `agente_id`, `tipo`, `categoria`, `descripcion`, `precio_creditos`, `stock`, `estado`, `creado_en` |
| RD-03 | Lote de crédito | `id`, `propietario_id`, `monto`, `emitido_en`, `vence_en`, `origen`, `estado`, `parent_id` |
| RD-04 | Transacción | `id`, `comprador_id`, `vendedor_id`, `oferta_id`, `monto`, `lotes_usados`, `estado`, `confirmada_en` |
| RD-05 | Mensaje | `id`, `de`, `para`, `canal`, `texto`, `turno`, `resumen` |
| RD-06 | Evento | `id`, `run_id`, `turno`, `agente_id`, `tipo`, `payload`, `motivo`, `timestamp` |
| RD-07 | Sanción | `id`, `agente_id`, `tipo`, `motivo`, `inicio`, `fin`, `estado` |
| RD-08 | Corrida | `run_id`, `escenario`, `config`, `semilla`, `modelo`, `inicio`, `fin`, `costo_estimado` |
| RD-09 | Resultado | `run_id`, `metrica`, `valor`, `unidad`, `desagregado_por` |
| RD-10 | Anuncio | `id`, `scope`, `category`, `title`, `body`, `startDay`, `endDay`, `effects`, `source`, `active` |
| RD-11 | Lugar | `id`, `q`, `r`, `tipo`, `nombre`, `agente_id`, `edificio_id` |

**Reglas de datos**

- Los nombres de agentes son ficticios; no se usan datos personales reales.
- Los montos se guardan como enteros para evitar errores de punto flotante.
- Cada crédito conserva su linaje: emisión, transferencias y vencimiento.
- Los logs son append-only; no se editan a mano.
- La configuración de cada corrida se guarda completa junto a los datos.

## 3. Requisitos no funcionales

| ID | Requisito | Prioridad | Criterio de aceptación |
|---|---|---|---|
| RNF-01 | Costo máximo | Must | Una corrida no supera el presupuesto definido; el sistema avisa antes de superarlo |
| RNF-02 | Duración razonable | Should | Una corrida de 10 agentes y 28 días termina en menos de 10 minutos en modo mock; las 5 repeticiones, en menos de 30 minutos |
| RNF-03 | Determinismo | Must | Modo mock con misma semilla produce el mismo resultado |
| RNF-04 | Modelo agnóstico | Must | Se puede cambiar de proveedor sin reescribir el entorno |
| RNF-05 | Observabilidad | Must | Logs, métricas y errores son consultables por corrida |
| RNF-06 | Portabilidad | Should | Corre en macOS/Linux con Node 22 + TypeScript y dependencias declaradas |
| RNF-07 | Documentación | Must | Un README explica cómo instalar, configurar y correr |
| RNF-08 | Pruebas | Must | Las reglas de emisión, transferencia y vencimiento tienen tests |
| RNF-09 | Privacidad | Must | No se cargan datos personales reales ni credenciales en el repositorio |
| RNF-10 | Seguridad | Must | El simulador no ejecuta código generado por los agentes |
| RNF-11 | Extensibilidad | Should | Se pueden agregar perfiles y escenarios sin tocar el núcleo |
| RNF-12 | Trazabilidad | Must | Cada número del informe se puede reconstruir desde los datos crudos |

## 4. Requisitos de modelo y prompts

| ID | Requisito | Prioridad | Criterio de aceptación |
|---|---|---|---|
| RM-01 | Prompts versionados | Must | Cada prompt tiene versión y se guarda con la corrida |
| RM-02 | Salida estructurada | Must | El agente responde con un JSON válido según el esquema `ToolCall` |
| RM-03 | Límite de tokens | Must | Cada llamada tiene máximo de tokens de entrada y salida |
| RM-04 | Timeout y reintentos | Must | Una llamada fallida no rompe la corrida; se reintenta o se registra |
| RM-05 | Temperatura configurable | Should | Se puede ajustar por escenario |
| RM-06 | Memoria resumida | Must | La memoria se resume para no crecer sin límite |
| RM-07 | Guardrails | Must | El agente no sale del rol, no inventa datos reales y no ejecuta acciones externas |
| RM-08 | Evaluación de adherencia | Should | Se mide cuántas respuestas son JSON válido y cuántas acciones son legales |
| RM-09 | Modo mock | Must | Se puede correr sin LLM para probar el entorno |
| RM-10 | Registro de prompts | Must | Se guarda el prompt exacto que recibió cada agente en cada turno |

## 5. Requisitos de análisis

| ID | Requisito | Prioridad | Criterio de aceptación |
|---|---|---|---|
| RA-01 | Métricas base | Must | Intercambios, emisión, uso, vencimiento, circulación, Gini, incumplimiento, categorías, conflictos y satisfacción |
| RA-02 | Comparación contra línea base | Must | Cada escenario se compara con E1 o con la corrida de control |
| RA-03 | Gráficos | Should | Al menos 4 gráficos: circulación, vencimiento, concentración y participación |
| RA-04 | Hallazgos | Must | El informe separa hechos, interpretaciones y recomendaciones |
| RA-05 | Reproducibilidad | Must | El informe incluye configuración, semilla y versión del modelo |

## 6. Fuera de alcance

- App para usuarios finales.
- Interfaz de producción.
- Integración con blockchain.
- Dinero real.
- Datos personales reales.
- Modelos de riesgo crediticio.
- Predicción de adopción.
- Token de recompensa.
- Editor avanzado de eventos en la UI (queda para una fase posterior).

## 7. Supuestos

- Los agentes pueden representar oficios y productos de la economía informal.
- El ciclo dura 28 días y el crédito vence a los 30 días, salvo que el escenario diga otra cosa.
- El precio se fija ex ante en el MVP.
- La DAO o asociación actúa como contraparte, pero en la simulación se simplifica como una regla del entorno.
- Los modelos de lenguaje pueden producir comportamiento emergente, pero no se toma como evidencia del mundo real.

## 8. Preguntas abiertas

1. ¿Cómo se definen los montos de sueldo y plan social de cada agente?
2. ¿Qué comportamiento tiene el supermercado en la etapa 2, cuando acepta bonos?
3. ¿Qué representa un día simulado en tiempo real?
4. ¿Cómo se valida el roster de 10 agentes con Hernán?
5. ¿Qué formato de informe prefiere Hernán?
6. ¿Cómo se modela la municipalidad y quién publica los anuncios?
7. ¿Se corre en local o en un VPS?
8. ¿Cómo se valida que los agentes no están actuando como el modelo espera?

## Enlaces

- [[Proyecto - Simulacion agentica|Proyecto — Simulación agéntica]]
- [[01 - Plan de ejecucion|Plan de ejecución]]
- [[03 - Diseno experimental|Diseño experimental]]
- [[04 - Arquitectura tecnica|Arquitectura técnica]]
- [[07 - Checklist de ejecucion|Checklist de ejecución]]
