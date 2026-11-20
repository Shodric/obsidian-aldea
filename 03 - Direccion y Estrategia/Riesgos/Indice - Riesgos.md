---
tipo: indice
area: direccion
estado: activo
actualizado: 2026-11-20
---

# Índice — Riesgos

Registro de riesgos del proyecto. Cada riesgo tiene severidad, probabilidad, responsable, mitigación e indicador de alerta.

## Tabla de riesgos

```dataview
TABLE severidad, probabilidad, responsable, estado
FROM "03 - Direccion y Estrategia/Riesgos"
WHERE tipo = "riesgo"
SORT severidad ASC, probabilidad ASC
```

## Riesgos activos

- [[03 - Direccion y Estrategia/Riesgos/Riesgo - Oferta homogenea y baja densidad|Oferta homogénea y baja densidad]]
- [[03 - Direccion y Estrategia/Riesgos/Riesgo - Incumplimiento y free riders|Incumplimiento y free riders]]
- [[03 - Direccion y Estrategia/Riesgos/Riesgo - Especulacion y precios paralelos|Especulación y precios paralelos]]
- [[03 - Direccion y Estrategia/Riesgos/Riesgo - Incertidumbre regulatoria|Incertidumbre regulatoria]]
- [[03 - Direccion y Estrategia/Riesgos/Riesgo - Baja adopcion y desconfianza|Baja adopción y desconfianza]]
- [[03 - Direccion y Estrategia/Riesgos/Riesgo - Dependencia de Hernan y del territorio|Dependencia de Hernán y del territorio]]
- [[03 - Direccion y Estrategia/Riesgos/Riesgo - Sobreingenieria tecnologica|Sobreingeniería tecnológica]]
- [[03 - Direccion y Estrategia/Riesgos/Riesgo - Datos personales e identidad|Datos personales e identidad]]

## Cómo se gestiona un riesgo

1. Se identifica y se documenta con la plantilla [[99 - Templates/Template - Riesgo|Template — Riesgo]].
2. Se le asigna severidad y probabilidad.
3. Se define una mitigación con responsable y plazo.
4. Se monitorea el indicador de alerta.
5. Se actualiza el estado: `activo`, `mitigado`, `cerrado` o `materializado`.

## Enlaces

- [[03 - Direccion y Estrategia/Indice - Direccion y Estrategia|Dirección y Estrategia]]
- [[00 - Centro de Mando/Aldea - Centro de Mando|Centro de Mando]]
