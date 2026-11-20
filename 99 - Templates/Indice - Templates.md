---
tipo: indice
area: sistema
estado: activo
actualizado: 2026-11-20
---

# Índice — Templates

Plantillas para crear notas consistentes. Usar con el plugin core **Templates** de Obsidian.

## Plantillas

| Plantilla | Uso |
|---|---|
| [[99 - Templates/Template - Proyecto|Proyecto]] | Proyectos con fase, hitos y tareas |
| [[99 - Templates/Template - Reunion|Reunión]] | Reuniones con agenda y tareas |
| [[99 - Templates/Template - Apuntes|Apuntes]] | Notas de reunión o lectura |
| [[99 - Templates/Template - Decision|Decisión]] | Registro de decisiones |
| [[99 - Templates/Template - Riesgo|Riesgo]] | Registro de riesgos |
| [[99 - Templates/Template - Indice|Índice]] | Índice de carpeta con Dataview |
| [[99 - Templates/Template - Documento|Documento]] | Documento genérico |
| [[99 - Templates/Template - SOP|SOP]] | Procedimiento operativo |
| [[99 - Templates/Template - Aliado|Aliado]] | Ficha de aliado |
| [[99 - Templates/Template - Acta|Acta]] | Acta de asamblea o comité |
| [[99 - Templates/Template - Transcripcion|Transcripción]] | Transcripción editada |
| [[99 - Templates/Template - KPI|KPIs]] | Conjunto de indicadores |

## Configuración

1. Instalar el plugin core **Templates**.
2. Configurar la carpeta de plantillas: `99 - Templates`.
3. Usar `{{date:YYYY-MM-DD}}` y `{{time:HH:mm}}` para fechas.
4. Reemplazar `{{title}}` por el título de la nota.

## Convenciones

- Frontmatter mínimo: `tipo`, `estado`, `area`, `actualizado`.
- Nombres de archivo según `CLAUDE.md`.
- Enlaces internos con `[[...]]`.
- No dejar placeholders sin completar en notas activas.
