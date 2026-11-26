---
tipo: proyecto
estado: pendiente
fase: 0
area: proyectos
responsable: Rodrigo
inicio: 2026-11-20
fecha_objetivo: por confirmar
presupuesto_estimado: "USD 0-30"
actualizado: 2026-11-20
---

# Proyecto — Simulación agéntica

> [!info] Estado
> **Pospuesto para otro momento.** La planificación y la arquitectura están cerradas; la ejecución todavía no empezó. El modelo, el lenguaje, los agentes y las repeticiones ya están definidos. Falta la API key, el roster definitivo y la fecha de la primera corrida.

> [!info] Repositorio de desarrollo
> La copia técnica para construir el simulador está en `/Users/shodric/Documents/GitHub/aldea-simulator` (Git, solo documentación por ahora). El vault sigue siendo la fuente de gestión y de decisiones.

## Verificación técnica del 25 de noviembre de 2026

E1 de aceptación y E1–E8 se ejecutaron en modo mock, con cinco semillas compartidas. E1 registró 252 entregas confirmadas en 28 días. En el ensayo de 90 días, 30 días de vencimiento dieron 551 entregas, frente a 392 con 15 días y 623 con 60 días. La conciliación de las 45 repeticiones se verificó con SQLite.

El resultado documenta las mecánicas bajo la conducta programada. Quedan pendientes calibrar los parámetros, validar un piloto LLM y completar los casos de Fiscalía. Los resultados y comandos están en `docs/09-parametros-y-resultados.md` del repositorio `aldea-simulator`.

## Qué contiene esta carpeta

| Documento | Para qué sirve |
|---|---|
| [[00A - Concepto y modelo economico]] | Qué es Aldea, qué es un bono y qué se quiere probar |
| [[01 - Plan de ejecucion]] | Fases, actividades, entregables y puertas de decisión |
| [[02 - Requisitos]] | Qué tiene que tener el simulador para considerarse listo |
| [[03 - Diseno experimental]] | Hipótesis, escenarios E1-E8, métricas y análisis |
| [[04 - Arquitectura tecnica]] | Componentes, modelo de datos, bucle y stack |
| [[05 - Prompts y perfiles]] | Personalidades, prompts, formato de acciones y guardrails |
| [[06 - Recursos y presupuesto]] | Roles, herramientas, modelos y costos |
| [[07 - Checklist de ejecucion]] | Paso a paso para correr la simulación y entregar el informe |
| [[08 - Evaluacion ADK]] | Pros, contras y recomendación sobre Agent Development Kit |
| [[09 - Ideas en analisis - Bono como obligacion negociable]] | Idea en análisis: obligación, DAO matching y E9 |

## Objetivo

Probar el circuito de Aldea con agentes de IA que tengan personalidad, memoria y capacidad de diálogo, antes de construir el MVP. El objetivo no es predecir el futuro, sino **encontrar los puntos de bloqueo, los atajos y las condiciones de sostenibilidad** del modelo.

## Preguntas que debe responder

1. ¿El circuito arranca y se sostiene con 10 agentes?
2. ¿Qué proporción de créditos queda sin usar o vence?
3. ¿Los especuladores acaparan o estabilizan el mercado?
4. ¿Qué pasa cuando sube el porcentaje de escépticos?
5. ¿El vencimiento de 15, 30 o 60 días cambia la circulación?
6. ¿El precio fijo evita el regateo o lo desplaza a otro canal?
7. ¿Qué sanciones sostienen la confianza sin expulsar a la gente?
8. ¿Qué atajos inventan los agentes para romper el sistema?

## Alcance

- Diseñar 4 perfiles de agente: optimista, neutro, especulativo y escéptico.
- Modelar **10 agentes** elegidos por el usuario, con oferta, demanda, créditos y vencimiento.
- Incluir diálogo libre, memoria, movimiento y capacidad de cambiar de opinión.
- Incluir teléfono, grupo de la ciudad, anuncios por notificación y sesiones de chat de 10 mensajes con costo de 1 punto.
- Incluir Fiscalía para denuncias, mediación y casos.
- Ejecutar **5 repeticiones** por escenario.
- Medir intercambios, circulación, vencimientos, concentración y conflictos.
- Producir un informe con recomendaciones de parámetros.

## Fuera de alcance

- Construir la app real.
- Usar dinero real.
- Simular el territorio completo.
- Predecir la adopción con precisión.
- Token de recompensa.
- Validar legalmente el modelo.

## Fases

| Fase | Nombre | Entregable | Estado |
|---|---|---|---|
| F0.1 | Preparación | Insumos, preguntas y presupuesto aprobados | Pendiente |
| F0.2 | Diseño | Perfiles, escenarios, métricas y prompts cerrados | Pendiente |
| F0.3 | Construcción | Arnés reproducible con modo deterministico y modo LLM | Pendiente |
| F0.4 | Prueba | Corrida con 1, 3 y 10 agentes; ajustes | Pendiente |
| F0.5 | Corrida | E1-E8 ejecutados y datos crudos guardados | Pendiente |
| F0.6 | Análisis | Informe, gráficos y recomendaciones | Pendiente |

El detalle de cada fase está en [[01 - Plan de ejecucion|Plan de ejecución]].

## Hitos

| Hito | Fecha objetivo | Estado |
|---|---|---|
| Insumos de Hernán recibidos | 2026-11-20 | Listo (falta el JSX) |
| Perfiles y métricas definidos | Por confirmar | Pendiente |
| Roster de 10 agentes elegido | Por confirmar | Pendiente |
| Arnés de simulación funcionando | Por confirmar | Pendiente |
| Primera corrida con 10 agentes | Por confirmar | Pendiente |
| Cinco repeticiones completas | Por confirmar | Pendiente |
| Informe de resultados | Por confirmar | Pendiente |

## Requisitos mínimos para ejecutar

Antes de escribir la primera línea del simulador tienen que estar definidos:

- [ ] Las preguntas y las hipótesis prioritarias.
- [ ] Los 4 perfiles de agente y sus reglas de decisión.
- [ ] Los escenarios E1-E8 y sus variables.
- [ ] Las métricas y la forma de calcularlas.
- [ ] El modelo de lenguaje, el presupuesto y el límite de llamadas.
- [ ] Los puntos de conversación por día, el límite de 10 mensajes por sesión y el costo de 1 punto por sesión.
- [ ] El formato de datos y el mecanismo de reproducibilidad.
- [ ] El criterio de éxito y el formato del informe.

El detalle está en [[02 - Requisitos|Requisitos]] y [[07 - Checklist de ejecucion|Checklist de ejecución]].

## Dependencias

- Archivos de Hernán: modelo original y pitches recibidos; falta el simulador JSX.
- Definición de parámetros del circuito: vencimiento, precios, techos y sanciones.
- Modelo DeepSeek v4.1 Flash configurado en `.env` y API key disponible.
- Presupuesto de modelos: USD 0–30 para la primera etapa.
- Una persona con tiempo para construir y analizar el arnés.
- Un lugar donde guardar datos crudos y resultados.

## Riesgos

- **Abstracción excesiva**: los agentes no representan el comportamiento real.
- **Sesgo de cooperación**: los LLM tienden a colaborar y a olvidar el conflicto.
- **Costo**: las llamadas a modelos superan el presupuesto.
- **Complejidad**: el arnés se vuelve más costoso que el MVP.
- **Sobreinterpretación**: los resultados se leen como profecías.
- **Datos inventados**: los agentes producen información que parece real.

Mitigaciones en [[06 - Recursos y presupuesto|Recursos y presupuesto]] y [[03 - Diseno experimental|Diseño experimental]].

## Criterio de éxito

- Se identifican al menos 3 puntos de bloqueo del circuito.
- Se comparan al menos 3 escenarios de participación.
- Se producen recomendaciones concretas de parámetros.
- El costo total no supera los USD 30.
- Los datos crudos y el código permiten repetir la corrida.

## Decisiones pendientes antes de correr

| Decisión | Elección | Responsable | Estado |
|---|---|---|---|
| Lenguaje | TypeScript + Node 22 | Rodrigo | Definido |
| Persistencia | SQLite + JSONL | Rodrigo | Definido |
| Modelo de lenguaje | DeepSeek v4.1 Flash vía `.env` | Rodrigo | Definido |
| Modo de simulación | Híbrido (mock + LLM) | Rodrigo | Definido |
| Agentes | 10, elegidos por el usuario en la UI | Rodrigo / Hernán | Definido |
| Repeticiones | 5 por escenario | Rodrigo | Definido |
| Movimiento | 20 puntos por día; 1 punto por hexágono | Rodrigo | Definido |
| Conversación | 10 mensajes por agente por sesión; 1 punto por sesión nueva | Rodrigo | Definido |
| Puntos de conversación | 2 por día (1 para la primera corrida) | Rodrigo | Recomendado |
| Teléfono | Perfil, anuncios, grupo de la ciudad, mensajes, billetera y memorias | Rodrigo | Definido |
| Fiscalía | Denuncias, mediación, investigación y sanción | Rodrigo | Definido |
| ADK | No como núcleo; spike opcional | Rodrigo | Definido |
| Horizonte | 28 días (56 para segundo ciclo) | Rodrigo | Recomendado |
| Formato del informe | Markdown + gráficos; PDF/slides después | Rodrigo / Hernán | Recomendado |
| Presupuesto máximo | USD 0–30 para la primera etapa | Rodrigo / Hernán | Pendiente |

## Enlaces

- [[07 - Tecnologia y Producto/Simulacion - Agentes IA|Simulación — Agentes IA]]
- [[10 - Modelo Economico y Tokenomia/Simulacion - Parametros y resultados|Simulación — Parámetros y resultados]]
- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
- [[08 - Proyectos/Indice - Proyectos|Índice de proyectos]]
