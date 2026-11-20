---
tipo: decision
estado: propuesta
area: economia
fecha: 2026-11-20
responsable: Hernan / Rodrigo
actualizado: 2026-11-20
---

# Decisión — Vencimiento en posesión

> [!warning] Estado: PROPUESTA
> Es el núcleo del modelo, pero requiere validación técnica, legal y de comportamiento.

## Contexto
El crédito debe circular y no acumularse. Hernán propone que venza **mientras está en posesión**, inspirándose en los UTXO de Bitcoin: al transferirse, el nuevo tenedor recibe un plazo renovado. Esto evita el vencimiento global de todo el circuito y elimina la necesidad de sanciones masivas por rechazo.

## Opciones

### A. Vencimiento global al cierre del ciclo
- **Ventaja**: simple de implementar y explicar.
- **Desventaja**: genera una estampida al final; castiga a quien no pudo gastar; requiere sanciones por rechazo.

### B. Vencimiento en posesión con renovación al transferir
- **Ventaja**: incentiva la circulación continua; distribuye el vencimiento; reduce la presión de cierre.
- **Desventaja**: más complejo de implementar; requiere registrar el tiempo de cada UTXO.

### C. Sin vencimiento, solo incentivos reputacionales
- **Ventaja**: simple y sin riesgo de pérdida.
- **Desventaja**: no resuelve la acumulación ni la especulación.

## Recomendación
**Opción B**, con un plazo `T` inicial de 30 días (a calibrar en simulación). El vencimiento se aplica al crédito, no a la obligación.

## Consecuencias
- La billetera debe mostrar el tiempo restante de cada crédito.
- El contrato debe soportar partición y renovación.
- La comunicación debe explicar que el crédito “se duerme” si no se usa.
- El cierre de ciclo se usa para auditoría y reinscripción, no para quemar todo.

## Preguntas abiertas
- ¿`T` debe ser fijo o variable por tipo de oferta?
- ¿Qué pasa si el crédito se transfiere parcialmente varias veces?
- ¿Cómo se evita que alguien transfiera a un cómplice para renovar artificialmente?
- ¿El vencimiento se mide en tiempo real o por bloques?

## Enlaces
- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
- [[07 - Tecnologia y Producto/Arquitectura - Creditos con vencimiento|Arquitectura]]
- [[10 - Modelo Economico y Tokenomia/Modelo - Creditos de intercambio|Créditos de intercambio]]
