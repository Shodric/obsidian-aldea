---
tipo: decision
estado: propuesta
area: legal
fecha: 2026-11-20
responsable: Rodrigo / Abogada
actualizado: 2026-11-20
---

# Decisión — Encuadre legal del crédito

> [!warning] Estado: PROPUESTA
> No es una decisión tomada ni un dictamen. Es la estrategia propuesta para obtener certeza jurídica antes del MVP.

## Contexto
El crédito de intercambio es fungible y divisible, y circula como medio de pago dentro de un circuito cerrado. La hipótesis es que no es un valor negociable bajo la Ley 26.831 porque no se compra con dinero, no promete rentabilidad y solo sirve para intercambiar bienes y servicios. Pero la fungibilidad y la posibilidad de un mercado secundario podrían atraer la mirada de la CNV. Sin dictamen, construir el MVP es asumir un riesgo innecesario.

## Opciones

### A. Lanzar sin dictamen y ajustar después
- **Ventaja**: velocidad.
- **Desventaja**: riesgo de sanciones, clausura o rediseño costoso.

### B. Dictamen preliminar antes del MVP
- **Ventaja**: certeza razonable, bajo costo relativo, permite diseñar con criterio.
- **Desventaja**: demora de semanas; el dictamen no es vinculante.

### C. Consulta formal a la CNV
- **Ventaja**: mayor certeza.
- **Desventaja**: larga, costosa, puede atraer escrutinio prematuro.

## Recomendación
**Opción B**: dictamen preliminar escrito antes de escribir código de producción, con revisión de las normas de datos y lavado. Si el dictamen es ambiguo, evaluar C antes del piloto.

## Restricciones de diseño que reducen el riesgo
1. El crédito **no se compra con dinero**.
2. **No promete rentabilidad** ni se presenta como inversión.
3. **Solo sirve** para bienes y servicios del circuito.
4. **No se comercializa** fuera del sistema.
5. La emisión está **limitada por la oferta** y por techos.
6. El token de recompensa **no forma parte del MVP**.
7. La comunicación evita las palabras “moneda”, “inversión” y “criptomoneda”.

## Consecuencias
- El MVP se diseña con estas restricciones.
- La abogada revisa contratos, términos y política de datos.
- Si el dictamen es desfavorable, se ajusta el modelo antes de construir.
- El token de recompensa queda para una evaluación separada.

## Preguntas abiertas
- ¿Qué alcance tiene el dictamen?
- ¿Conviene consultar a la CNV o esperar?
- ¿Qué pasa si el crédito se usa en un mercado secundario informal?
- ¿Cómo se articula con la normativa municipal?
- ¿Qué obligaciones de lavado aplican?

## Enlaces
- [[13 - Legal y Cumplimiento/Marco regulatorio - Tokens y trueque en Argentina|Marco regulatorio]]
- [[03 - Direccion y Estrategia/Riesgos/Riesgo - Incertidumbre regulatoria|Riesgo — Incertidumbre regulatoria]]
- [[08 - Proyectos/Activos/Proyecto - Marco legal y DAO|Proyecto — Marco legal y DAO]]
