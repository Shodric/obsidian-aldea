---
tipo: documento
estado: borrador
area: tecnologia
proyecto: "[[Proyecto - Simulacion agentica]]"
actualizado: 2026-11-20
---

# Evaluación — Agent Development Kit (ADK)

> [!question] Pregunta
> ¿Conviene usar el Agent Development Kit de Google (`adk.dev`) como base del simulador de Aldea?

## Qué es

ADK es un **kit de desarrollo de agentes** de Google, open source. Permite construir agentes con herramientas, sesiones, memoria, callbacks, workflows multiagente y evaluación. Tiene SDK en Python, TypeScript, Go, Java y Kotlin. TypeScript 2.0 está disponible desde agosto de 2026.

No es un motor de simulación. Es una capa para construir agentes conversacionales o de tareas y desplegarlos en producción.

## Qué resolvería

- Runtime de agente y bucle de tool calling.
- Definición de tools con esquemas.
- Sesiones y estado de conversación.
- Memoria de largo plazo.
- Callbacks antes y después de una acción.
- Workflows multiagente y grafos.
- Dev UI para inspeccionar sesiones.
- Evaluación y observabilidad.
- Adaptadores para Gemini, OpenAI, Claude, Ollama, vLLM y LiteLLM.

## Qué no resolvería

- El mundo autoritativo de Aldea: mapa, edificios, casas, locales, stock, ofertas y precios.
- El `RulesEngine` económico: emisión, lotes, FIFO, vencimiento, compromiso mínimo, escrow y sanciones.
- El `Ledger` y la reconstrucción de saldos.
- El `EventLog` y el replay determinista.
- El reloj de simulación (`run` → `día` → `turno` → `agente`).
- La UI de mapa en hexágonos y el tablero de eventos.
- El control de costos específico de Aldea.

## Pros y contras

| Pros | Contras |
|---|---|
| Ahorra escribir el bucle de agente y el tool calling | No modela el mundo, el ledger ni las reglas económicas |
| Ya trae sesiones, memoria y callbacks | Sus sesiones son conversacionales, no `día/turno/agente` |
| Tiene Dev UI y evaluación | Agrega una dependencia y una curva de aprendizaje |
| TypeScript encaja con el stack elegido | La versión 2.0 introdujo cambios incompatibles |
| Soporta varios proveedores | Está optimizado para Gemini; DeepSeek requiere adaptador |
| Sirve si el producto se vuelve una plataforma de agentes | Para 10 agentes, el loop propio es más simple y controlable |
| Podría usarse para un spike aislado | Puede ocultar el costo real de tokens y llamadas |

## Encaje con Aldea

El núcleo de Aldea no es “un agente que conversa”: es un **mundo económico con reglas duras**. Aunque ADK resolviera la conversación, el `ActionGateway`, el `RulesEngine`, el `Ledger` y el `EventLog` seguirían siendo nuestros. La parte que ADK ahorra es justamente la más simple para 10 agentes; la parte que no resuelve es la que define el proyecto.

## Opciones

| Opción | Qué implica | Veredicto |
|---|---|---|
| A — ADK como núcleo | Reemplazar el orquestador y el runtime por ADK | **No recomendado** |
| B — ADK como runtime opcional | Interfaz `AgentRuntime` con dos implementaciones: propia y ADK | **Evaluar después del MVP** |
| C — Spike aislado | Probar ADK en un cuaderno aparte, sin tocar el simulador | **Recomendado si hay curiosidad** |

## Recomendación

**No usar ADK como núcleo del MVP.** Mantener el orquestador propio, el `ActionGateway` autoritativo y el `EventLog`. Si más adelante se quiere aprovechar su Dev UI o su sistema de sesiones, se puede envolver detrás de una interfaz `AgentRuntime` y comparar, sin reescribir el motor.

La decisión se revisa cuando:

- El simulador ya funcione con 10 agentes y 5 repeticiones.
- Haya una necesidad concreta de workflows multiagente o despliegue.
- Se quiera probar otro proveedor sin tocar el contrato de tools.

## Referencias

- [ADK](https://adk.dev/)
- [Documentación de ADK](https://google.github.io/adk-docs/)
- [ADK en GitHub](https://github.com/google/adk-python)

## Enlaces

- [[04 - Arquitectura tecnica|Arquitectura técnica]]
- [[Proyecto - Simulacion agentica|Proyecto — Simulación agéntica]]
- [[02 - Requisitos|Requisitos]]
