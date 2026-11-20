---
tipo: documento
estado: borrador
area: tecnologia
proyecto: "[[Proyecto - Simulacion agentica]]"
actualizado: 2026-11-20
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

| ID | Agentes | Perfiles (opt/neut/espec/escép) | Vencimiento | Precio | Sanción | Propósito |
|---|---|---|---|---|---|---|
| E1 | 10 | 30/40/15/15 | 30 días | Fijo | Media | Línea base |
| E2 | 30 | 25/40/20/15 | 30 días | Fijo | Media | Escalar manteniendo mezcla |
| E3 | 30 | 25/20/15/40 | 30 días | Fijo | Media | Estrés por escepticismo |
| E4 | 30 | 30/40/15/15 | 15 días | Fijo | Media | Vencimiento corto |
| E5 | 30 | 30/40/15/15 | 60 días | Fijo | Media | Vencimiento largo |
| E6 | 30 | 30/40/15/15 | 30 días | Negociado | Media | Regateo |
| E7 | 30 | 30/40/15/15 | 30 días | Fijo | Fuerte | Sanción fuerte |
| E8 | 30 | 30/40/15/15 | 30 días | Fijo | Débil | Sanción débil |

**Control:** E1 es la referencia para los escenarios de 10 agentes. Para los de 30, la referencia es E2.

## 4. Variables

| Variable | Niveles | Tipo |
|---|---|---|
| Cantidad de agentes | 10, 30, 50 | Independiente |
| Perfil optimista | 15%, 30%, 50% | Independiente |
| Perfil especulativo | 5%, 15%, 25% | Independiente |
| Perfil escéptico | 5%, 15%, 40% | Independiente |
| Vencimiento | 15, 30, 60 días | Independiente |
| Precio | Fijo, negociado | Independiente |
| Sanción | Débil, media, fuerte | Independiente |
| Confirmación de entrega | Con código, sin código | Independiente |
| Duración | 28, 56 días | Control |
| Semilla | 3 semillas por escenario | Control |

## 5. Métricas

| Métrica | Definición | Fórmula / unidad |
|---|---|---|
| Intercambios totales | Transacciones confirmadas | # |
| Intercambios por agente | Promedio de transacciones por agente activo | # |
| Créditos emitidos | Suma de créditos creados | créditos |
| Créditos usados | Suma de créditos transferidos en compras | créditos |
| Créditos vencidos | Suma de créditos que expiraron en posesión | créditos |
| Tasa de uso | Créditos usados / créditos emitidos | % |
| Tasa de vencimiento | Créditos vencidos / créditos emitidos | % |
| Tiempo promedio de circulación | Días entre emisión y última transferencia | días |
| Concentración | Gini de saldos al cierre | 0–1 |
| Tasa de incumplimiento | Ofertas no entregadas / ofertas comprometidas | % |
| Categorías activas | Categorías con al menos una oferta | # |
| Conflictos | Disputas registradas | # |
| Sanciones | Sanciones aplicadas por tipo | # |
| Satisfacción | Promedio de percepción declarada | 1–5 |
| Costo | Gasto estimado en modelos | USD |

## 6. Diseño de la corrida

- **Horizonte:** 28 días por ciclo; 56 días para observar un segundo ciclo.
- **Turnos:** 1 turno = 1 día. Cada agente actúa una vez por turno.
- **Repeticiones:** 3 semillas por escenario para la primera etapa.
- **Semillas:** fijas y registradas; no se cambian entre repeticiones del mismo escenario.
- **Modelo:** primero mock deterministico; luego LLM con temperatura baja para reducir varianza.
- **Datos:** se guardan eventos, transacciones, mensajes, configuración y resultados.
- **Costo:** se estima antes de cada corrida y se corta si supera el límite.

## 7. Plan de análisis

1. **Validación de datos:** verificar que no falten eventos, que los saldos cuadren y que no haya créditos negativos.
2. **Estadística descriptiva:** medias, medianas, desvíos y rangos por escenario.
3. **Comparación:** E2 contra E3-E8; E1 contra E2 para ver el efecto de escala.
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
| Pocas repeticiones | Ruido | 3 semillas y análisis de sensibilidad |
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
- [[10 - Modelo Economico y Tokenomia/Simulacion - Parametros y resultados|Simulación — Parámetros y resultados]]
