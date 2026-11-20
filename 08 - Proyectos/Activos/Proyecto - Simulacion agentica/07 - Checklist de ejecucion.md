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
- [ ] Definir la pregunta principal de la primera corrida.
- [ ] Recibir y revisar el simulador JSX de Hernán.
- [ ] Recibir el modelo original 2016–2024.
- [ ] Recibir los dos pitches de Aldea.
- [ ] Confirmar los parámetros base del circuito.
- [ ] Elegir modo: mock, gratuito, DeepSeek o híbrido.
- [ ] Crear cuenta y API key si se usa LLM.
- [ ] Configurar límite de gasto y alertas.
- [ ] Crear repositorio o carpeta de trabajo.
- [ ] Crear estructura de datos y resultados.
- [ ] Verificar que no haya datos personales reales.

## 2. Diseño

- [ ] Cerrar los 4 perfiles y sus porcentajes.
- [ ] Definir atributos, motivaciones y reglas de decisión.
- [ ] Cerrar el entorno: mercado, ciclo, vencimiento, precios y sanciones.
- [ ] Cerrar los escenarios E1-E8.
- [ ] Definir variables y niveles.
- [ ] Definir métricas, fórmulas y unidades.
- [ ] Escribir los prompts y el esquema de acción.
- [ ] Definir el formato de logs y resultados.
- [ ] Definir el criterio de éxito.
- [ ] Revisar el diseño con Hernán.

## 3. Construcción

- [ ] Implementar configuración por archivo.
- [ ] Implementar agentes y perfiles.
- [ ] Implementar mercado y ofertas.
- [ ] Implementar ledger de créditos.
- [ ] Implementar emisión, transferencia, partición y vencimiento.
- [ ] Implementar sanciones.
- [ ] Implementar confirmación de entrega.
- [ ] Implementar diálogo y memoria.
- [ ] Implementar adaptador mock.
- [ ] Implementar adaptador LLM.
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
- [ ] Test de reproducibilidad.
- [ ] Test de límite de costo.
- [ ] Corrida de 1 agente y 7 días.
- [ ] Corrida de 3 agentes y 14 días.
- [ ] Corrida de 10 agentes en modo mock.
- [ ] Revisar que los saldos cuadren.
- [ ] Revisar que las métricas coincidan con los eventos.

## 5. Corrida

- [ ] Congelar configuración y versión del código.
- [ ] Registrar semilla por escenario.
- [ ] Correr E1 con 3 semillas.
- [ ] Revisar resultados y costo de E1.
- [ ] Correr E2-E8.
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
