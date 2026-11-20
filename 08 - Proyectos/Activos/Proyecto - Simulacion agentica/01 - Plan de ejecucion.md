---
tipo: plan
estado: pendiente
area: tecnologia
proyecto: "[[Proyecto - Simulacion agentica]]"
actualizado: 2026-11-20
---

# Plan de ejecución — Simulación agéntica

## Propósito

Convertir la simulación en un proceso reproducible, barato y útil para decidir parámetros del circuito antes de construir el MVP. El plan asume que la ejecución se hará **más adelante**; por eso prioriza dejar todo listo y evitar dependencias innecesarias.

## Principios de ejecución

1. **Empezar barato**: primero un modo deterministico sin LLM; después, si aporta, agregar agentes con lenguaje.
2. **Una pregunta por corrida**: no mezclar demasiadas variables en el mismo experimento.
3. **Reproducible**: semilla, configuración, versión del modelo y datos crudos guardados.
4. **Comparable**: mismos escenarios base y mismas métricas entre corridas.
5. **Auditable**: cada acción de cada agente queda registrada con su motivo.
6. **Acotado**: el simulador no se convierte en un producto; es un laboratorio.

## Fases

### F0.1 — Preparación

**Objetivo:** cerrar el alcance y conseguir los insumos.

- Revisar el simulador JSX de Hernán y el modelo original 2016–2024.
- Confirmar las preguntas prioritarias y las hipótesis.
- Definir el presupuesto máximo y la fuente de API.
- Acordar el formato del informe final.
- Crear el repositorio o carpeta de trabajo y la estructura de datos.

**Entregable:** nota de alcance aprobada y presupuesto definido.

**Criterio de salida:** están respondidas las decisiones pendientes de la nota principal.

### F0.2 — Diseño

**Objetivo:** dejar el experimento especificado antes de programar.

- Cerrar los 4 perfiles y sus atributos.
- Definir el entorno: mercado, ciclo, vencimiento, precios y sanciones.
- Cerrar los escenarios E1-E8 y las variables.
- Definir las métricas, fórmulas y unidades.
- Escribir los prompts y el esquema `ToolCall`.
- Definir el mundo de hexágonos, el movimiento y el tablero de anuncios.
- Definir el teléfono, el grupo de la ciudad y las sesiones de chat de 10 mensajes con 1 punto por sesión.
- Definir la Fiscalía y el flujo de casos.
- Revisar la evaluación de ADK y decidir si se hace un spike aislado.
- Definir el formato de los datos de salida.

**Entregable:** [[03 - Diseno experimental|Diseño experimental]] y [[05 - Prompts y perfiles|Prompts y perfiles]] completos.

**Criterio de salida:** otra persona puede construir el arnés leyendo esos documentos.

### F0.3 — Construcción

**Objetivo:** tener un simulador que corra de punta a punta.

- Implementar el entorno, el reloj y el mundo de hexágonos.
- Implementar el registro de agentes, ofertas, créditos y transacciones.
- Implementar el motor de reglas: emisión, transferencia, vencimiento, movimiento y sanción.
- Implementar el `ActionGateway`, el toolbelt y el tablero de anuncios.
- Implementar el teléfono, las sesiones de chat, el grupo de la ciudad y las notificaciones.
- Implementar la Fiscalía y el registro de casos.
- Implementar el adaptador de modelo (mock, gratuito o pago).
- Implementar el registro de eventos y el cálculo de métricas.
- Implementar el generador de informe y gráficos.
- Escribir pruebas unitarias de las reglas críticas.

**Entregable:** arnés ejecutable con un comando y configuración por archivo.

**Criterio de salida:** una corrida de 1 agente y 7 días termina sin errores y produce métricas.

### F0.4 — Prueba

**Objetivo:** validar que el simulador no está roto antes de gastar en modelos.

- Correr con 1 agente y comportamiento fijo.
- Correr con 3 agentes y verificar transferencias y vencimientos.
- Correr con 10 agentes en modo deterministico.
- Revisar que las métricas coincidan con los eventos.
- Ajustar prompts y reglas.
- Medir consumo y costo por corrida.

**Entregable:** informe corto de validación técnica.

**Criterio de salida:** no hay errores bloqueantes y el costo por corrida está dentro del presupuesto.

### F0.5 — Corrida

**Objetivo:** ejecutar los escenarios y guardar los datos.

- Correr E1-E8 con 5 repeticiones por escenario.
- Guardar configuración, semilla, versión del modelo y datos crudos.
- Monitorear costo y tiempo.
- Detener una corrida si el costo supera el límite.
- Registrar incidentes y decisiones tomadas durante la corrida.

**Entregable:** base de datos o carpeta de resultados crudos por escenario.

**Criterio de salida:** todos los escenarios tienen datos completos o una justificación de por qué no se corrieron.

### F0.6 — Análisis y entrega

**Objetivo:** convertir los datos en decisiones.

- Calcular métricas por escenario y comparar contra la línea base.
- Hacer gráficos de circulación, vencimiento, concentración y participación.
- Identificar puntos de bloqueo y atajos.
- Escribir hallazgos y recomendaciones.
- Actualizar [[10 - Modelo Economico y Tokenomia/Simulacion - Parametros y resultados|Simulación — Parámetros y resultados]].
- Presentar el informe a Hernán y decidir próximos pasos.

**Entregable:** informe final, gráficos y recomendaciones de parámetros.

**Criterio de salida:** el informe responde las preguntas de la nota principal y propone al menos 3 cambios concretos.

## Secuencia y dependencias

```
F0.1 Preparación
   ↓
F0.2 Diseño
   ↓
F0.3 Construcción
   ↓
F0.4 Prueba
   ↓
F0.5 Corrida
   ↓
F0.6 Análisis y entrega
```

- F0.2 no empieza sin los insumos de F0.1.
- F0.3 no empieza sin los documentos de F0.2.
- F0.5 no empieza sin el criterio de salida de F0.4.
- F0.6 no empieza sin los datos crudos de F0.5.

## Roles

| Rol | Quién | Responsabilidad |
|---|---|---|
| Dirección del proyecto | Rodrigo | Alcance, presupuesto, decisiones y calidad |
| Dominio y territorio | Hernán | Reglas del circuito, supuestos y validación con la realidad |
| Construcción | Rodrigo | Arnés, datos, métricas y análisis |
| Revisión externa | Por definir | Lectura crítica de resultados y sesgos |

## Esfuerzo estimado

Estimación preliminar, sin fecha comprometida:

| Fase | Esfuerzo | Comentario |
|---|---|---|
| F0.1 Preparación | 0,5–1 día | Depende de los archivos de Hernán |
| F0.2 Diseño | 1–2 días | Se puede hacer sin código |
| F0.3 Construcción | 5–7 días | Incluye teléfono, chats, Fiscalía y LLM desde el inicio |
| F0.4 Prueba | 1–2 días | Incluye ajustes |
| F0.5 Corrida | 1–3 días | Depende de la velocidad del modelo |
| F0.6 Análisis | 2–3 días | Incluye informe y gráficos |

**Total preliminar:** 10–20 días de trabajo efectivo, distribuidos en el calendario que se acuerde. La diferencia con la estimación anterior viene del teléfono, las sesiones de chat y la Fiscalía.

## Entregables

1. Nota de alcance y presupuesto.
2. Documento de diseño experimental.
3. Arnés de simulación reproducible.
4. Datos crudos por escenario.
5. Informe de resultados con gráficos.
6. Recomendaciones de parámetros para el MVP.
7. Presentación breve para Hernán.

## Puertas de decisión

| Puerta | Pregunta | Si la respuesta es no |
|---|---|---|
| G1 | ¿Los insumos y las preguntas están claros? | No empezar el diseño |
| G2 | ¿El diseño permite responder las preguntas? | Revisar escenarios y métricas |
| G3 | ¿El arnés pasa las pruebas? | No gastar en corridas |
| G4 | ¿El costo está dentro del presupuesto? | Reducir alcance o usar modo deterministico |
| G5 | ¿Los resultados son interpretables? | Revisar datos y supuestos |
| G6 | ¿Hay recomendaciones accionables? | No presentar como conclusiones |

## Riesgos del plan

- **Dependencia de Hernán**: sin los archivos, F0.1 se bloquea. Mitigación: empezar con el diseño propio y usar el JSX como referencia.
- **Sobreingeniería**: construir un producto en lugar de un laboratorio. Mitigación: tiempo y alcance acotados.
- **Costo variable**: los precios de los modelos cambian. Mitigación: presupuesto máximo y modo deterministico.
- **Sesgo del simulador**: las reglas que escribimos determinan el resultado. Mitigación: documentar supuestos y correr variantes.
- **Falta de tiempo**: el proyecto se pospone. Mitigación: dejar todo documentado y retomable.

## Enlaces

- [[Proyecto - Simulacion agentica|Proyecto — Simulación agéntica]]
- [[02 - Requisitos|Requisitos]]
- [[03 - Diseno experimental|Diseño experimental]]
- [[07 - Checklist de ejecucion|Checklist de ejecución]]
