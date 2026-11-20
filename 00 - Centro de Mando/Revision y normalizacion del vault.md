---
tipo: documento
estado: pendiente
area: direccion
actualizado: 2026-11-20
---

# Revisión y normalización del vault

> [!info] Qué es
> Es una revisión de **calidad y consistencia** de la estructura, no del contenido del proyecto. Busca que las notas se puedan encontrar, enlazar y filtrar sin errores. No cambia decisiones ni reescribe documentos.

## Qué revisa

| Área | Qué se verifica | Ejemplo de problema |
|---|---|---|
| Frontmatter | Que todas las notas tengan `tipo`, `estado`, `area` y `actualizado`; que usen tipos y estados válidos | Una nota con `tipo: proyecto` y `estado: en curso` (con espacio) |
| Enlaces internos | Que todos los enlaces apunten a una nota existente | Un enlace a una nota que se renombró |
| Índices | Que cada carpeta tenga su índice y que las tablas no estén desactualizadas | Un proyecto nuevo que no aparece en el índice |
| Nombres | Que sigan la nomenclatura definida | `reunion hernan.md` en lugar de `2026-11-20 - ...` |
| Duplicados | Que no haya dos notas para el mismo tema | Dos versiones del documento ejecutivo |
| Notas huérfanas | Que no haya notas sin enlaces entrantes | Un riesgo que no está en el índice |
| Consultas Dataview | Que las carpetas referenciadas existan y que los campos estén escritos igual | `FROM "08 - Proyectos"` cuando la carpeta cambió de nombre |
| Etiquetas | Que las etiquetas sean consistentes | `#legal` y `#Legal` usadas para lo mismo |
| Archivos sueltos | Que no queden archivos en la raíz o en `01 - Inbox` sin procesar | Un PDF suelto en la raíz |

## Qué no hace

- No decide si una propuesta es buena o mala.
- No aprueba decisiones.
- No borra notas sin confirmación.
- No cambia el contenido de los documentos.
- No corrige datos de la llamada.
- No valida el marco legal.

## Cómo se hace

1. **Inventario**: listar todas las notas y carpetas.
2. **Frontmatter**: revisar campos obligatorios y valores válidos.
3. **Enlaces**: resolver cada enlace interno y marcar los rotos.
4. **Índices**: comparar el contenido real de la carpeta con su índice.
5. **Nombres**: detectar nombres fuera de convención.
6. **Duplicados**: buscar títulos y temas repetidos.
7. **Dataview**: verificar que las consultas apunten a carpetas existentes.
8. **Corrección**: arreglar lo mecánico y listar lo que requiere decisión.
9. **Registro**: dejar un resumen de cambios y pendientes.

## Checklist

- [ ] Inventario de notas y carpetas.
- [ ] Frontmatter obligatorio en todas las notas.
- [ ] Tipos y estados válidos.
- [ ] Enlaces internos resueltos.
- [ ] Índices actualizados.
- [ ] Nombres según convención.
- [ ] Duplicados detectados.
- [ ] Notas huérfanas detectadas.
- [ ] Consultas Dataview verificadas.
- [ ] Etiquetas consistentes.
- [ ] Archivos sueltos procesados.
- [ ] Resumen de cambios.

## Resultado esperado

- Un listado de problemas encontrados.
- Correcciones mecánicas aplicadas.
- Una lista corta de decisiones que necesita Rodrigo o Hernán.
- Un vault más fácil de navegar, sin cambiar el contenido del proyecto.

## Cuándo hacerlo

- Antes de compartir el vault con Hernán.
- Después de una tanda grande de notas nuevas.
- Al cerrar una fase del proyecto.
- Cuando una búsqueda no encuentra algo que debería estar.

## Enlaces

- [[00 - Centro de Mando/Kanban - Pendientes del Vault|Kanban de pendientes]]
- [[00 - Centro de Mando/Como usar esta estructura|Cómo usar esta estructura]]
- [[CLAUDE|Reglas del vault]]
