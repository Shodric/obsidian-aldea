---
tipo: decision
estado: propuesta
area: economia
fecha: 2026-11-20
responsable: Hernan / Rodrigo
actualizado: 2026-11-20
---

# Decisión — Precios ex ante y valor hora

> [!warning] Estado: PROPUESTA
> El mecanismo es parte del núcleo, pero los parámetros están sin definir.

## Contexto
Hernán propone que los precios se fijen **antes** del intercambio y no se negocien. El sistema asigna un valor en créditos a partir del precio declarado en pesos y una ecuación de valor hora. Rodrigo advierte que la gente igual le dará un valor propio al crédito (“bono blue”) y que la inflación puede distorsionar los precios.

## Opciones

### A. Valor hora único
- **Ventaja**: simple, igualitario, fácil de explicar.
- **Desventaja**: no reconoce especialización; puede expulsar oficios calificados.

### B. Escala por oficio
- **Ventaja**: más justo con la especialización.
- **Desventaja**: complejo, discrecional, requiere datos y puede generar conflictos.

### C. Precio declarado + conversión
- **Ventaja**: flexible, usa el conocimiento local.
- **Desventaja**: riesgo de inflación de precios y comparabilidad difícil.

## Recomendación
**Opción A** para el MVP (valor hora único), con una tabla de conversión para productos y una revisión por ciclo. Evaluar **B** en la Fase 2 con datos del piloto.

## Reglas propuestas
- El precio se publica antes del intercambio y no se negocia.
- El valor de referencia se actualiza por ciclo, no durante el ciclo.
- El sistema puede rechazar precios fuera de rango.
- Hay un piso y un techo por operación y por participante.

## Consecuencias
- La app debe mostrar el precio en créditos y el equivalente en pesos.
- La comunicación debe explicar por qué no se regatea.
- Se necesita una fuente de datos para el valor hora.

## Preguntas abiertas
- ¿Cuál es el valor hora de referencia?
- ¿Cómo se actualiza sin generar inflación?
- ¿Qué pasa si un oficio no acepta el valor hora?
- ¿Cómo se manejan los productos con precios muy variables?

## Enlaces
- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
- [[10 - Modelo Economico y Tokenomia/Mecanismo - Precios y valor hora|Precios y valor hora]]
- [[03 - Direccion y Estrategia/Riesgos/Riesgo - Especulacion y precios paralelos|Riesgo — Especulación]]
