---
tipo: documento
estado: borrador
area: tecnologia
proyecto: "[[Proyecto - Simulacion agentica]]"
actualizado: 2026-11-25
---

# Diseño experimental — Simulación agéntica

> [!info] Principio
> La simulación no busca predecir el futuro. Busca **poner a prueba supuestos del circuito** y encontrar dónde se traba. Cada escenario cambia una variable principal y mantiene el resto constante.

## 1. Preguntas de investigación

1. ¿Qué condiciones mínimas hacen que el circuito arranque y se sostenga?
2. ¿Qué proporción de créditos se usa, queda quieta o vence?
3. ¿Los especuladores acaparan, estabilizan o quiebran el mercado?
4. ¿Qué pasa cuando aumenta el porcentaje de escépticos?
5. ¿El plazo de vencimiento cambia la velocidad de circulación?
6. ¿El precio fijo evita el regateo o lo desplaza a otro canal?
7. ¿Qué sanción sostiene la confianza sin expulsar a la gente?
8. ¿Qué atajos inventan los agentes para romper el sistema?

## 2. Hipótesis

| ID | Hipótesis | Variable | Resultado esperado |
|---|---|---|---|
| H1 | Un circuito con 10 agentes y perfiles balanceados arranca y produce intercambios | Cantidad de agentes | Al menos 20 intercambios en 28 días |
| H2 | Los especuladores acaparan créditos y reducen la circulación | % especuladores | Gini más alto y más vencimientos |
| H3 | Un exceso de escépticos reduce la participación y la confianza | % escépticos | Menos intercambios y más abandono |
| H4 | Un vencimiento más corto acelera la circulación | Plazo | Más intercambios por crédito y menos saldo ocioso |
| H5 | El precio negociado aumenta la dispersión y el regateo | Precio fijo vs. negociado | Mayor varianza de precios y más conflictos |
| H6 | Una sanción fuerte mejora el cumplimiento pero aumenta la exclusión | Sanción | Menos incumplimiento y más bajas |
| H7 | La confirmación de entrega reduce las disputas | Confirmación | Menos conflictos por transacción |

## 3. Escenarios

| ID | Agentes | Agentes por perfil (opt/neut/espec/escép) | Vencimiento | Precio | Sanción | Propósito |
|---|---|---|---|---|---|---|
| E1 | 10 | 3/4/2/1 | 30 días | Fijo | Media | Línea base |
| E2 | 10 | 3/2/2/3 | 30 días | Fijo | Media | Estrés por escepticismo |
| E3 | 10 | 3/3/3/1 | 30 días | Fijo | Media | Estrés por especulación |
| E4 | 10 | 3/4/2/1 | 15 días | Fijo | Media | Vencimiento corto |
| E5 | 10 | 3/4/2/1 | 60 días | Fijo | Media | Vencimiento largo |
| E6 | 10 | 3/4/2/1 | 30 días | Negociado | Media | Regateo |
| E7 | 10 | 3/4/2/1 | 30 días | Fijo | Fuerte | Sanción fuerte |
| E8 | 10 | 3/4/2/1 | 30 días | Fijo | Débil | Sanción débil |

**Control:** E1 es la referencia. Cada escenario cambia una variable principal respecto de E1. Las cantidades son enteras. En E2, dos neutros pasan a escépticos. En E3, un neutro pasa a especulativo. Se conservan los ciudadanos, oficios y recursos. La escala a 30 agentes queda para una fase posterior.

### 3.1 E9 propuesto — matching de la DAO

No forma parte de la primera corrida. Se propone para después de E1-E8:

| ID | Agentes | Vencimiento | Precio | Sanción | DAO matching | Propósito |
|---|---|---|---|---|---|---|
| E9 | 10 | 30 días | Fijo | Media | Sí | Medir si la DAO encuentra contraprestaciones y mejora el cumplimiento |

Comparación: E9 contra E1. La DAO envía ofertas de trabajo/productos a los agentes que tienen un compromiso; el agente puede aceptar o rechazar. Se miden aceptación, cumplimiento, vencimiento, presión y costo. Ver [[09 - Ideas en analisis - Bono como obligacion negociable|Bono como obligación negociable]].

## 4. Variables

| Variable | Niveles | Tipo |
|---|---|---|
| Cantidad de agentes | 10 en fase 1; 30 en fase 2 opcional | Control |
| Perfil optimista | 20%, 30%, 40% | Independiente |
| Perfil especulativo | 15%, 25%, 30% | Independiente |
| Perfil escéptico | 15%, 25%, 35% | Independiente |
| Vencimiento | 15, 30, 60 días | Independiente |
| Precio | Fijo, negociado | Independiente |
| Sanción | Débil, media, fuerte | Independiente |
| Matching de la DAO | Sin, con | Independiente (E9) |
| Confirmación de entrega | Con código, sin código | Independiente |
| Duración | 28, 56 días | Control |
| Repeticiones | 5 por escenario | Control |
| Puntos de conversación | 1, 2, 3 por día | Independiente |

## 5. Métricas

| Métrica | Definición | Fórmula / unidad |
|---|---|---|
| Intercambios totales | Transacciones confirmadas | # |
| Intercambios por agente | Promedio de transacciones por agente activo | # |
| Créditos emitidos | Suma de créditos creados | créditos |
| Créditos usados | Suma de créditos transferidos en compras | créditos |
| Créditos vencidos | Suma de créditos que expiraron en posesión | créditos |
| Circulación acumulada | Créditos transferidos en entregas confirmadas / créditos emitidos. La misma unidad puede circular varias veces. | veces |
| Tasa de vencimiento | Créditos vencidos / créditos emitidos | % |
| Tiempo promedio de circulación | Días entre emisión y última transferencia | días |
| Concentración | Gini de saldos al cierre | 0–1 |
| Tasa de incumplimiento | Solicitudes con rechazo del vendedor o sin respuesta / (entregas confirmadas + solicitudes incumplidas). Informar aparte solicitudes pendientes y aceptadas sin confirmación. | % |
| Categorías activas | Categorías con al menos una oferta | # |
| Conflictos | Disputas registradas | # |
| Sanciones | Sanciones aplicadas por tipo | # |
| Sesiones de chat | Sesiones abiertas por agente y día | # |
| Mensajes | Mensajes enviados por agente, canal y día | # |
| Uso de puntos de conversación | Puntos consumidos / disponibles | % |
| Casos de Fiscalía | Casos abiertos, mediados y resueltos | # |
| Matches de la DAO | Ofertas de contraprestación enviadas | # |
| Aceptación de matches | Matches aceptados / enviados | % |
| Tiempo hasta el match | Días entre obligación y primer match aceptado | días |
| Presión percibida | Rechazos por incompatibilidad o exceso de ofertas | 1–5 |
| Satisfacción | Promedio de percepción declarada | 1–5 |
| Costo | Gasto estimado en modelos, separando turnos y chat | USD |

## 6. Diseño de la corrida

- **Horizonte.** El E1 de aceptación dura 28 días. La comparación E1–E8 usa 90 días para que los lotes iniciales de 15, 30 y 60 días tengan tiempo de vencer. Los saldos vigentes y retenidos al cierre se registran por separado.
- **Turnos:** 1 turno = 1 día. Cada agente actúa una vez por turno, con hasta 5 tool calls, 20 puntos de movimiento y 2 puntos de conversación (1 en la primera corrida).
- **Repeticiones:** 5 por escenario, con semillas fijas y registradas.
- **Semillas.** Usar cinco semillas distintas, registradas y en el mismo orden para todos los escenarios. La primera batería usa 42, 43, 44, 45 y 46. Comparar primero por pares de igual semilla.
- **Modelo:** primero mock deterministico; luego LLM con temperatura 0,5 para reducir varianza.
- **Datos:** se guardan eventos, transacciones, mensajes, configuración y resultados.
- **Costo:** se estima antes de cada corrida y se corta si supera el límite. 10 agentes × 28 días × 5 repeticiones = 1.400 turnos; hasta 7.000 tool calls si se usan 5 por turno.

## 7. Plan de análisis

1. **Validación de datos:** verificar que no falten eventos, que los saldos cuadren y que no haya créditos negativos.
2. **Estadística descriptiva:** medias, medianas, desvíos y rangos por escenario.
3. **Comparación:** E2-E8 contra E1, cada uno con una variable principal distinta. No se compara escala en la fase 1.
4. **Series temporales:** circulación, emisión y vencimiento por día.
5. **Concentración:** Gini al cierre y evolución.
6. **Análisis cualitativo:** mensajes, conflictos y atajos detectados.
7. **Síntesis:** hallazgos, interpretación y recomendaciones.
8. **Limitaciones:** sesgos del simulador y validez externa.

## 8. Amenazas a la validez

| Amenaza | Efecto | Mitigación |
|---|---|---|
| Sesgo de cooperación de los LLM | Resultados demasiado optimistas | Forzar conflicto, usar perfiles escépticos y especulativos |
| Prompts que inducen la respuesta | Los agentes “actúan” el guion | Prompts neutrales y pruebas de adherencia |
| Abstracción del territorio | No representa un barrio real | Validar supuestos con Hernán y datos de campo |
| Pocas repeticiones | Ruido | 5 repeticiones y análisis de sensibilidad |
| Costo | Menos corridas | Modo mock y modelos baratos |
| Sobreinterpretación | Decisiones basadas en ficción | Informe separa evidencia, interpretación y recomendación |

## 9. Salidas

- Tabla comparativa por escenario.
- Gráficos de circulación, vencimiento, concentración y participación.
- Lista de puntos de bloqueo.
- Lista de atajos y conductas inesperadas.
- Recomendaciones de parámetros.
- Registro de supuestos y limitaciones.

## 10. Criterios de éxito del diseño

- Cada escenario responde una pregunta.
- Cada métrica tiene definición y fórmula.
- Los datos permiten reconstruir el resultado.
- El costo está acotado.
- El informe distingue lo observado de lo interpretado.

## Enlaces

- [[Proyecto - Simulacion agentica|Proyecto — Simulación agéntica]]
- [[02 - Requisitos|Requisitos]]
- [[04 - Arquitectura tecnica|Arquitectura técnica]]
- [[05 - Prompts y perfiles|Prompts y perfiles]]
- [[09 - Ideas en analisis - Bono como obligacion negociable|Bono como obligación negociable]]
- [[10 - Modelo Economico y Tokenomia/Simulacion - Parametros y resultados|Simulación — Parámetros y resultados]]
