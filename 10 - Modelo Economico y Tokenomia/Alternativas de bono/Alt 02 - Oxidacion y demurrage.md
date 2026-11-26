---
tipo: modelo
estado: propuesta
area: economia
alternativa: "02"
eje: caducidad
factibilidad: baja
actualizado: 2026-11-20
---

# Alternativa 02 — Oxidación y demurrage

> [!abstract] En una línea
> El bono no vence de golpe: **pierde valor mientras está quieto**. Es la solución clásica al atesoramiento, pero exige calcular, marcar y controlar en cada operación.

## 1. Qué se planteó en la llamada

> «En Austria, en un proyecto municipal, se desarrolló un sistema de monedas o bonos sociales con un fenómeno que llamaban **oxidación**: el bono iba perdiendo valor con el tiempo. Era un formato para forzar el uso. Yo no quería complicarme con eso —vi cómo trabajaba y era complejo: el organizador tenía que recibir, marcar, controlar—, así que preferí que los bonos tuvieran vencimiento.»
> — Hernán, §1 de la transcripción

Hernán lo conoce, lo considera y lo descarta por costo operativo. La referencia teórica es el *Freigeld* de Silvio Gesell y el experimento de Wörgl (1932): el dinero que pierde valor obliga a circular.

## 2. Cómo funciona

**Versión física**
1. El bono vale 100 al emitirse.
2. Cada mes hay que pegarle un sello o perforarlo; si no, vale menos.
3. El que lo recibe descuenta el valor faltante.
4. El organizador controla que el bono esté actualizado.

**Versión digital**
1. El saldo se reduce automáticamente un porcentaje por período (por ejemplo, 1% semanal).
2. La reducción se calcula al momento de cada transferencia o de cada consulta.
3. No hay sellos: el sistema aplica la tasa.

## 3. Por qué se propuso

- **Fuerza el uso sin fecha de corte**: no hay un día en que todo vence a la vez.
- **Evita el atesoramiento**: guardar tiene un costo explícito.
- **Es gradual**: no castiga de golpe al que se olvidó.

## 4. Evaluación

| Dimensión | Valor | Fundamento |
|---|---|---|
| Técnica | Media | Digital es fácil de calcular; físico requiere sellos y control |
| Legal | Media | Un saldo que baja solo es difícil de encuadrar; puede leerse como comisión o confiscación |
| Operativa | **Baja** | Física: mucho trabajo. Digital: fácil de operar, difícil de explicar |
| Dependencias | Baja | No necesita municipio ni actor externo |
| Costo de prueba | Bajo | Se simula con una tasa y se mide la reacción |

**Factibilidad: Baja (2/5).** La complejidad no es de código: es de legitimidad y de experiencia de usuario.

## 5. El problema central

La oxidación **castiga al que menos tiene**. Quien guarda 200 créditos para comprar una heladera o pagar una reparación grande pierde poder de compra; quien tiene 20.000 y los mueve todas las semanas casi no lo siente. Es regresiva si se aplica pareja.

Además, el usuario ve que su saldo baja sin haber gastado. Eso se percibe como pérdida, no como regla, y erosiona la confianza más rápido que un vencimiento claro.

## 6. Riesgos

| Riesgo | Señal | Mitigación |
|---|---|---|
| Percepción de confiscación | Quejas, abandono | Comunicar la regla desde el inicio; mostrar el reloj |
| Regresividad | Los saldos chicos pierden más | Tasa progresiva o exención por tramo |
| Complejidad de cálculo | Disputas por saldos | Registro auditable y regla simple |
| Sin vuelta atrás | El usuario no puede planificar | Tope a la pérdida acumulada |

## 7. Rol en el MVP

**No implementar.** Su lugar es el **plan B**: si la simulación muestra que el vencimiento en posesión no alcanza para mover el circuito, probar una oxidación leve (1% semanal) como variable de ajuste.

También sirve como **argumento de comparación**: explica por qué Aldea eligió vencimiento en posesión en lugar de oxidación. Menos mecánica, misma intención.

## 8. Preguntas específicas

1. ¿La oxidación es una tasa, una multa o una regla contable?
2. ¿Se aplica al saldo o solo a la parte que excede un umbral?
3. ¿Qué pasa con el crédito oxidado: se quema o vuelve al fondo?
4. ¿Se puede compensar con un descuento por gastar rápido?

## Enlaces

- [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Indice - Alternativas de bono|Índice — Alternativas de bono]]
- [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Alt 04 - UTXO con vencimiento en posesion|Alternativa 04 — Vencimiento en posesión]]
- [[04 - Reuniones/2026/11-Noviembre/2026-11-20 - Llamada con Hernan - Transcripcion|Transcripción de la llamada]]
