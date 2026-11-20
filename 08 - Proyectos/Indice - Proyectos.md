---
tipo: indice
area: proyectos
estado: activo
actualizado: 2026-11-20
---

# Índice — Proyectos

## Proyectos

| Proyecto | Fase | Estado | Responsable | Fecha objetivo |
|---|---|---|---|---|
| [[08 - Proyectos/Activos/Proyecto - Simulacion agentica/Proyecto - Simulacion agentica|Simulación agéntica]] | 0 | Pendiente (pospuesto) | Rodrigo | Por confirmar |
| [[08 - Proyectos/Activos/Proyecto - Documento y pitch|Documento y pitch]] | 0 | En curso | Rodrigo | 2026-11-27 |
| [[08 - Proyectos/Activos/Proyecto - Marco legal y DAO|Marco legal y DAO]] | 1 | Pendiente | Rodrigo / Abogada | Por confirmar |
| [[08 - Proyectos/Activos/Proyecto - Prototipo navegable MVP|Prototipo navegable del MVP]] | 2 | Pendiente (no iniciado) | Rodrigo | Por confirmar |
| [[08 - Proyectos/Activos/Proyecto - MVP de trueque|MVP de trueque]] | 2 | Pendiente | Rodrigo | Por confirmar |
| [[08 - Proyectos/Activos/Proyecto - Piloto territorial|Piloto territorial]] | 2 | Pendiente | Hernán / Rodrigo | Por confirmar |

> [!info] Proyectos con carpeta
> Cuando un proyecto necesita planos, requisitos, arquitectura o checklist de ejecución, se crea una carpeta con el nombre del proyecto y la nota principal adentro. Ejemplo: `08 - Proyectos/Activos/Proyecto - Simulacion agentica/`.

## Vista Dataview

```dataview
TABLE fase, estado, responsable, fecha_objetivo
FROM "08 - Proyectos"
WHERE tipo = "proyecto"
SORT fase ASC, estado ASC
```

## Cómo se crea un proyecto

1. Copiar [[99 - Templates/Template - Proyecto|Template — Proyecto]].
2. Completar objetivo, alcance, fuera de alcance, actividades e hitos.
3. Asignar responsable, fase y fecha objetivo.
4. Registrar dependencias y riesgos.
5. Definir el criterio de éxito.
6. Si el proyecto necesita documentación de ejecución, crear una carpeta `Proyecto - Nombre/` y adentro la nota principal `Proyecto - Nombre.md` más los documentos numerados (`01 - Plan...`, `02 - Requisitos...`).
7. Actualizar el estado semanalmente.

## Enlaces

- [[03 - Direccion y Estrategia/Roadmap - Cuatro fases|Roadmap]]
- [[00 - Centro de Mando/Aldea - Centro de Mando|Centro de Mando]]
