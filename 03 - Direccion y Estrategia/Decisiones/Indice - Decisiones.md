---
tipo: indice
area: direccion
estado: activo
actualizado: 2026-11-20
---

# Índice — Decisiones

Registro de decisiones del proyecto. Una decisión es un compromiso explícito, con contexto, opciones, recomendación y consecuencias.

> [!warning] Propuesta ≠ decisión
> Las notas con `estado: propuesta` **no están aprobadas**. Solo pasan a `activo` cuando hay validación de las personas responsables y se registra la fecha.

## Tabla de decisiones

```dataview
TABLE fecha, estado, responsable
FROM "03 - Direccion y Estrategia/Decisiones"
WHERE tipo = "decision"
SORT fecha DESC
```

## Decisiones propuestas

- [[03 - Direccion y Estrategia/Decisiones/Decision - Encuadre del MVP sin token de recompensa|Encuadre del MVP sin token de recompensa]]
- [[03 - Direccion y Estrategia/Decisiones/Decision - Encuadre legal del credito|Encuadre legal del crédito]]
- [[03 - Direccion y Estrategia/Decisiones/Decision - Vencimiento en posesion|Vencimiento en posesión]]
- [[03 - Direccion y Estrategia/Decisiones/Decision - DAO como contraparte|DAO como contraparte]]
- [[03 - Direccion y Estrategia/Decisiones/Decision - Territorio del piloto|Territorio del piloto]]
- [[03 - Direccion y Estrategia/Decisiones/Decision - Precios ex ante y valor hora|Precios ex ante y valor hora]]

## Cómo se registra una decisión

1. Copiar [[99 - Templates/Template - Decision|Template — Decisión]].
2. Completar contexto, opciones, recomendación y consecuencias.
3. Dejar `estado: propuesta` hasta la validación.
4. Al aprobarse, cambiar a `estado: activo` y agregar fecha y responsables.
5. Enlazar desde el proyecto o área correspondiente.

## Enlaces

- [[03 - Direccion y Estrategia/Indice - Direccion y Estrategia|Dirección y Estrategia]]
