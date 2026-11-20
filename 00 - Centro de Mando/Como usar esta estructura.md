---
tipo: indice
area: direccion
estado: activo
actualizado: 2026-11-20
---

# Cómo usar esta estructura

## Regla de orden

- **Por fecha completa**: reuniones, transcripciones, decisiones e incidentes.
- **Por año o mes**: presupuestos, reportes e hitos con fecha.
- **Sin fecha en carpeta**: proyectos, riesgos, aliados, procesos, convenios y notas vivas.

## Convención de nombres

- Reuniones: `2026-11-20 - Llamada con Hernan - Apuntes.md`
- Transcripciones: `2026-11-20 - Llamada con Hernan - Transcripcion.md`
- Decisiones: `2026-11-20 - Decision - Tema.md`
- Proyectos: `Proyecto - Nombre.md`
- Proyectos con carpeta: `Proyecto - Nombre/` con la nota principal y documentos numerados (`01 - Plan...`, `02 - Requisitos...`).
- Riesgos: `Riesgo - Nombre.md`
- Procesos: `SOP - Area - Proceso.md`
- Índices: `Indice - Area.md`
- Documentos: `AAAA-MM - Titulo.md`

## Frontmatter mínimo

```yaml
---
tipo: proyecto
estado: activo
area: proyectos
actualizado: 2026-11-20
---
```

## Flujo semanal

1. Cargar notas sueltas en `01 - Inbox`.
2. Procesar reuniones y convertirlas en decisiones y tareas.
3. Actualizar proyectos, riesgos y aliados.
4. Revisar el kanban y los indicadores.
5. Actualizar el Centro de Mando.

## Tres reglas de oro

1. **La economía real primero**: ninguna definición técnica se toma sin entender cómo afecta a quien participa del circuito.
2. **Propuesta ≠ decisión**: una idea de la llamada no es una decisión aprobada. Las decisiones van en `03 - Direccion y Estrategia/Decisiones/`.
3. **Privacidad por diseño**: no se cargan datos personales sensibles ni información de salud. El catálogo usa seudónimos; la identidad se verifica solo cuando hace falta.

## Dónde va cada cosa

| Si necesitás... | Ir a... |
|---|---|
| Ver el estado general | `00 - Centro de Mando` |
| Entender el proyecto | `03 - Direccion y Estrategia` |
| Ver gobernanza, membresía y sanciones | `02 - Gobernanza y Comunidad` |
| Ver cómo funciona el crédito | `10 - Modelo Economico y Tokenomia` |
| Ver la arquitectura y el MVP | `07 - Tecnologia y Producto` |
| Ver el piloto y sus fases | `08 - Proyectos` |
| Ver el marco legal | `13 - Legal y Cumplimiento` |
| Ver aliados y contactos | `09 - Alianzas y Ecosistema` |
| Ver evaluación y KPIs | `15 - Reportes e Indicadores` |
| Crear una nota nueva | `99 - Templates` |

## Diferencia entre los dos documentos base

- **Documento Ejecutivo**: explica Aldea para alguien de afuera (municipio, financista, aliado). No necesita entender blockchain.
- **Modelo — Circuito de créditos**: explica el mecanismo para el equipo y para quien lo va a construir. Distingue reglas económicas, técnicas y legales.

## Enlaces

- [[CLAUDE|Reglas del vault]]
- [[00 - Centro de Mando/Aldea - Centro de Mando|Centro de Mando]]
- [[00 - Centro de Mando/Kanban - Pendientes del Vault|Kanban]]
