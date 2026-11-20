---
tipo: sop
estado: pendiente
area: tecnologia
proyecto: "[[Proyecto - Simulacion agentica]]"
actualizado: 2026-11-20
---

# Checklist de ejecución — Simulación agéntica

> [!info] Uso
> Esta lista se recorre de arriba hacia abajo. No se pasa a la siguiente sección si queda un ítem crítico sin resolver. Los ítems no críticos se pueden dejar para después, pero se registran.

## 1. Pre-flight

- [ ] Confirmar que la simulación se va a ejecutar ahora (no está pospuesta).
- [ ] Designar responsable de la corrida.
- [ ] Acordar presupuesto máximo.
- [ ] Revisar y aprobar el concepto y el modelo económico en [[00A - Concepto y modelo economico|00A]].
- [ ] Definir la pregunta principal de la primera corrida.
- [ ] Recibir y revisar el simulador JSX de Hernán.
- [x] Recibir el modelo original 2016–2024.
- [x] Recibir los dos pitches de Aldea.
- [x] Recibir la aproximación técnica v6 (con y sin token de recompensa).
- [ ] Confirmar los parámetros base del circuito.
- [ ] Elegir el roster de 10 agentes y sus fichas.
- [ ] Elegir modo: mock, DeepSeek V4.1 Flash o híbrido.
- [ ] Crear cuenta y API key si se usa LLM.
- [ ] Completar `LLM_API_KEY` en `.env`.
- [ ] Configurar límite de gasto y alertas.
- [x] Crear repositorio o carpeta de trabajo.
- [x] Crear `.env.example` y `.gitignore` para secretos.
- [ ] Crear estructura de datos y resultados.
- [ ] Verificar que no haya datos personales reales.
- [ ] Confirmar 10 agentes, 5 repeticiones, 28 días y 20 puntos de movimiento.
- [ ] Confirmar puntos de conversación por día, 10 mensajes por sesión y costo de 1 punto por sesión.
- [ ] Revisar la evaluación de ADK y decidir si se usa como spike opcional, no como núcleo.

## 2. Diseño

- [ ] Cerrar los 4 perfiles y sus porcentajes.
- [ ] Definir el roster y las fichas de los 10 agentes.
- [ ] Definir atributos, historias, motivaciones y reglas de decisión.
- [ ] Cerrar el entorno: mapa de hexágonos, edificios, casas, mercado, ciclo, vencimiento, precios y sanciones.
- [ ] Cerrar los escenarios E1-E8 con 10 agentes.
- [ ] Definir variables y niveles.
- [ ] Definir 5 repeticiones por escenario y semillas.
- [ ] Definir métricas, fórmulas y unidades.
- [ ] Escribir los prompts y el esquema `ToolCall`.
- [ ] Definir el tablero de anuncios y sus efectos.
- [ ] Definir el teléfono, sus pestañas y qué información es pública o privada.
- [ ] Definir sesiones de chat, límite de 10 mensajes y costo de 1 punto.
- [ ] Definir el grupo de la ciudad y sus reglas de moderación.
- [ ] Definir la Fiscalía: denuncia, mediación, investigación, sanción y apelación.
- [ ] Definir el formato de logs y resultados.
- [ ] Definir el criterio de éxito.
- [ ] Revisar el diseño con Hernán.

## 3. Construcción

- [ ] Implementar configuración por archivo (`RunConfig` + `.env`).
- [ ] Implementar mundo de hexágonos, edificios, casas y locations.
- [ ] Implementar agentes, perfiles, roster y memoria privada.
- [ ] Implementar `ActionGateway` con validación Zod e identidad de sesión.
- [ ] Implementar `RulesEngine`, `Ledger` y `EventLog`.
- [ ] Implementar mercado y ofertas.
- [ ] Implementar ledger de créditos por lotes.
- [ ] Implementar emisión, transferencia, partición, FIFO y vencimiento.
- [ ] Implementar compromiso mínimo y sanciones.
- [ ] Implementar confirmación de entrega y escrow.
- [ ] Implementar movimiento con 20 puntos por día.
- [ ] Implementar diálogo y memoria.
- [ ] Implementar teléfono: perfil, anuncios, grupo de la ciudad, mensajes, billetera, memorias y contactos.
- [ ] Implementar sesiones de chat con 10 mensajes y 1 punto por sesión.
- [ ] Implementar grupo de la ciudad y notificaciones.
- [ ] Implementar Fiscalía y casos.
- [ ] Implementar tablero de anuncios y efectos declarativos.
- [ ] Implementar hooks y sandbox.
- [ ] Implementar adaptador mock.
- [ ] Implementar adaptador LLM (DeepSeek V4.1 Flash).
- [ ] Implementar UI de configuración y mapa en tiempo real.
- [ ] Implementar logs y métricas.
- [ ] Implementar control de costo.
- [ ] Implementar generador de informe.
- [ ] Escribir README de uso.

## 4. Pruebas

- [ ] Test de emisión sin oferta.
- [ ] Test de techo de emisión.
- [ ] Test de transferencia.
- [ ] Test de partición.
- [ ] Test de vencimiento.
- [ ] Test de sanción.
- [ ] Test de acción inválida.
- [ ] Test de identidad y tool no permitida.
- [ ] Test de movimiento y límite de 20 puntos.
- [ ] Test de anuncios y efectos.
- [ ] Test de chat: 10 mensajes por sesión y 1 punto por sesión nueva.
- [ ] Test de teléfono: solo el dueño lee perfil privado, memorias y billetera.
- [ ] Test de grupo de la ciudad y notificaciones.
- [ ] Test de Fiscalía y casos.
- [ ] Test de hook sin permiso.
- [ ] Test de prompt injection.
- [ ] Test de reproducibilidad.
- [ ] Test de límite de costo.
- [ ] Corrida de 1 agente y 7 días.
- [ ] Corrida de 3 agentes y 14 días.
- [ ] Corrida de 10 agentes en modo mock.
- [ ] Revisar que los saldos cuadren.
- [ ] Revisar que las métricas coincidan con los eventos.

## 5. Corrida

- [ ] Congelar configuración y versión del código.
- [ ] Registrar 5 semillas por escenario.
- [ ] Correr E1 con 5 repeticiones.
- [ ] Revisar resultados y costo de E1.
- [ ] Correr E2-E8 con 5 repeticiones cada uno.
- [ ] Monitorear costo y tiempo.
- [ ] Detener si se supera el límite.
- [ ] Guardar datos crudos por escenario.
- [ ] Guardar logs de prompts y respuestas.
- [ ] Registrar incidentes y decisiones.

## 6. Análisis

- [ ] Validar integridad de datos.
- [ ] Calcular métricas por escenario.
- [ ] Comparar contra línea base.
- [ ] Hacer gráficos de circulación.
- [ ] Hacer gráficos de vencimiento.
- [ ] Hacer gráficos de concentración.
- [ ] Hacer gráficos de participación.
- [ ] Analizar mensajes y conflictos.
- [ ] Analizar sesiones, mensajes, puntos de conversación y costo por agente.
- [ ] Identificar puntos de bloqueo.
- [ ] Identificar atajos y conductas inesperadas.
- [ ] Separar hechos, interpretaciones y recomendaciones.

## 7. Entrega

- [ ] Escribir informe ejecutivo.
- [ ] Escribir anexo metodológico.
- [ ] Incluir configuración, semilla y versión del modelo.
- [ ] Incluir limitaciones.
- [ ] Actualizar [[10 - Modelo Economico y Tokenomia/Simulacion - Parametros y resultados|Simulación — Parámetros y resultados]].
- [ ] Preparar presentación de 10 minutos.
- [ ] Presentar a Hernán.
- [ ] Registrar decisiones tomadas.
- [ ] Archivar datos y código.

## 8. Definition of done

La simulación se considera terminada cuando:

- [ ] Todos los escenarios planificados se corrieron o se justificó su omisión.
- [ ] Los 10 agentes elegidos y las 5 repeticiones se ejecutaron.
- [ ] La UI permitió configurar roster, días, semilla, anuncios y presupuesto de conversación antes de iniciar.
- [ ] El teléfono, el grupo de la ciudad y la Fiscalía funcionaron con las reglas definidas.
- [ ] Los datos crudos están archivados y son reproducibles.
- [ ] El informe responde las preguntas de la nota principal.
- [ ] Hay al menos 3 recomendaciones concretas de parámetros.
- [ ] El costo real está dentro del presupuesto.
- [ ] Hernán revisó los resultados.
- [ ] Las decisiones quedaron registradas en el vault.

## Enlaces

- [[Proyecto - Simulacion agentica|Proyecto — Simulación agéntica]]
- [[01 - Plan de ejecucion|Plan de ejecución]]
- [[02 - Requisitos|Requisitos]]
- [[03 - Diseno experimental|Diseño experimental]]
- [[04 - Arquitectura tecnica|Arquitectura técnica]]
- [[06 - Recursos y presupuesto|Recursos y presupuesto]]
