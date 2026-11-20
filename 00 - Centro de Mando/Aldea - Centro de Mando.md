---
tipo: dashboard
area: direccion
estado: activo
actualizado: 2026-11-20
---

# Aldea — Centro de Mando

> [!summary] Estado del proyecto
> **Etapa**: diseño / pre-simulación. **Fase 0 (validación y simulación)**: en curso.
> **Documento base**: [[04 - Reuniones/2026/11-Noviembre/2026-11-20 - Llamada con Hernan - Apuntes|Apuntes de la llamada con Hernán]] · registro del 2026-11-20.
> **Idea fuerza**: créditos gratuitos que vencen mientras están quietos, respaldados por la oferta de cada participante.

## Prioridades actuales

- [ ] Recibir y archivar los documentos de Hernán: modelo original, pitches de Aldea y simulador JSX.
- [ ] Cerrar el Documento Ejecutivo y validarlo con Hernán.
- [ ] Armar el paquete de validación: agenda, checklist de las 6 decisiones y preguntas.
- [ ] Validar el encuadre legal del crédito de intercambio antes de escribir código de producción.
- [ ] Elegir el territorio del piloto y los contactos locales.
- [ ] Definir el alcance funcional del MVP y sus no-alcances.
- [ ] Dejar lista la simulación agéntica y ejecutarla cuando se acuerde (la carpeta ya está planificada).

## Próximos hitos

| Hito | Fase | Responsable | Fecha objetivo | Estado |
|---|---|---|---|---|
| Transcripción y apuntes de la llamada | 0 | Rodrigo | 2026-11-20 | Listo |
| Documento ejecutivo v0.1 | 0 | Rodrigo | 2026-11-27 | En curso |
| Archivos de Hernán recibidos y archivados | 0 | Hernán / Rodrigo | Por confirmar | Pendiente |
| Simulación agéntica v1 | 0 | Rodrigo | Por confirmar | Pospuesto |
| Dictamen legal preliminar | 1 | Rodrigo / abogada | Por confirmar | Pendiente |
| Territorio y aliados definidos | 1 | Hernán / Rodrigo | Por confirmar | Pendiente |
| MVP funcional | 2 | Rodrigo | Por confirmar | Pendiente |
| Piloto de 100–300 usuarios | 2 | Hernán / Rodrigo | Por confirmar | Pendiente |
| Evaluación y decisión sobre token de recompensa | 3 | Por confirmar | Por confirmar | Pendiente |

## Proyectos

```dataview
TABLE fase, estado, responsable, fecha_objetivo
FROM "08 - Proyectos"
WHERE tipo = "proyecto"
SORT fase ASC, estado ASC
```

## Decisiones recientes

```dataview
TABLE fecha, estado, responsable
FROM "03 - Direccion y Estrategia/Decisiones"
WHERE tipo = "decision"
SORT fecha DESC
LIMIT 10
```

## Riesgos abiertos

```dataview
TABLE severidad, probabilidad, estado
FROM "03 - Direccion y Estrategia/Riesgos"
WHERE tipo = "riesgo" AND estado != "cerrado"
SORT severidad ASC
```

## Reuniones recientes

```dataview
TABLE fecha, tipo, estado
FROM "04 - Reuniones"
WHERE tipo = "reunion" OR tipo = "acta" OR tipo = "apuntes" OR tipo = "transcripcion"
SORT fecha DESC
LIMIT 8
```

## Tareas abiertas

```tasks
not done
sort by due
```

## Accesos rápidos

- [[03 - Direccion y Estrategia/2026-11 - Documento Ejecutivo Aldea|Documento Ejecutivo Aldea]]
- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
- [[03 - Direccion y Estrategia/Roadmap - Cuatro fases|Roadmap de cuatro fases]]
- [[10 - Modelo Economico y Tokenomia/Modelo - Creditos de intercambio|Créditos de intercambio]]
- [[08 - Proyectos/Activos/Proyecto - Simulacion agentica/Proyecto - Simulacion agentica|Proyecto — Simulación agéntica]]
- [[08 - Proyectos/Activos/Proyecto - Prototipo navegable MVP|Proyecto — Prototipo navegable del MVP]]
- [[03 - Direccion y Estrategia/Riesgos/Indice - Riesgos|Registro de riesgos]]
- [[00 - Centro de Mando/Kanban - Pendientes del Vault|Kanban de pendientes]]
- [[00 - Centro de Mando/Revision y normalizacion del vault|Revisión y normalización del vault]]
- [[00 - Centro de Mando/Como usar esta estructura|Cómo usar esta estructura]]
