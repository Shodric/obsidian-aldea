---
tipo: modelo
estado: propuesta
area: economia
alternativa: "04"
eje: caducidad
factibilidad: alta
actualizado: 2026-11-20
---

# Alternativa 04 — UTXO con vencimiento en posesión

> [!abstract] En una línea
> El crédito vence **mientras está quieto** y renueva su plazo al cambiar de manos. Es la innovación central de Aldea: resuelve la velocidad sin castigar el cierre de ciclo.

## 1. Qué se planteó en la llamada

> «Quizás lo mejor es que el bono tenga caducidad **mientras está quieto**. Vos cobrás, se parte el UTXO que tenías y te queda uno más chiquito; ese UTXO se vence si no lo gastás. Una vez que lo gastás y lo pasás a otro, se genera un UTXO nuevo, y ese se va a vencer cuando esté en posesión de otra persona.»
> — Hernán, §3

> «El bono se vence **en posesión**, no se vence todo el circuito de golpe.»
> — Hernán, §3

## 2. Cómo funciona

Cada crédito es una **salida no gastada** (UTXO) con tres datos: monto, dueño y fecha de vencimiento.

1. Ana ofrece 10 horas de jardinería y recibe **10.000 créditos**; cada uno nace con plazo `T`.
2. Ana compra 8.000 en empanadas. El UTXO se parte: 8.000 van a Beto y 2.000 vuelven a Ana como vuelto.
3. Beto recibe 8.000 **con plazo renovado**. Ana conserva 2.000 **con su reloj original**.
4. Si Ana no gasta sus 2.000 antes de `T`, se queman.
5. La obligación de Ana —entregar las 10 horas— **no se quema**. Queda registrada.

```
[Oferta] → [Emisión con reloj T] → [Posesión: el reloj corre]
                                        ↓
                              [Transferencia: se parte]
                                        ↓
                         [Nuevo UTXO con reloj renovado]
```

## 3. Por qué se propuso

- **Justicia**: no hay un día en que todos pierden a la vez.
- **Velocidad**: el que tiene créditos sabe que si los duerme, los pierde.
- **Anti-atesoramiento**: guardar no tiene sentido; mover sí.
- **Continuidad**: el circuito no depende de una apertura y un cierre.
- **Trazabilidad**: cada crédito tiene historia y dueño.

## 4. Evaluación

| Dimensión | Valor | Fundamento |
|---|---|---|
| Técnica | **Alta** | UTXO es una regla contable; se implementa en PostgreSQL sin blockchain |
| Legal | Media | Es fungible y divisible: hay que dictaminar si es valor negociable; sin dinero ni rentabilidad, el riesgo es manejable |
| Operativa | **Alta** | Es automático; no hay sellos ni control manual |
| Dependencias | Baja | No necesita municipio ni permiso previo |
| Costo de prueba | Bajo | Se simula con una tabla de saldos y fechas |

**Factibilidad: Alta (4.5/5).** Es la alternativa que mejor resuelve el problema central con el menor costo operativo.

> [!important] UTXO no es blockchain
> El modelo UTXO viene de Bitcoin, pero es una **forma de llevar la cuenta**: cada crédito es una ficha con dueño y vencimiento. Se puede implementar en una base de datos común. Blockchain solo se justifica si varias organizaciones necesitan verificar sin confiar en el operador.

## 5. El problema central que resuelve

El acantilado de cierre (Alternativa 03). Con vencimiento en posesión:

- No hay una semana en que todos quieran gastar a la vez.
- El que recibe un crédito sabe que tiene un plazo completo por delante.
- El que quiere guardar para una compra grande puede hacerlo, pero pagando el costo de que el reloj corra.

## 6. Variante — Devaluación por rechazo

Rodrigo propuso, como sanción, «ir devaluando el precio de su bono. Rechazaste cinco ofertas: tu bono vale 5% menos» (§9).

| A favor | En contra |
|---|---|
| Fácil de implementar | Castiga al que tiene saldo, no al que rechaza |
| Señal clara | Puede afectar a quien no puede cumplir por razones justificadas |
| No requiere exclusión | Se presta a fraude: aceptar y no entregar |

**Recomendación**: no aplicarla al saldo en el MVP. Si se usa, aplicarla al **techo de emisión** o a la **reputación**, no a los créditos que la persona ya tiene. La sanción debe caer sobre la capacidad de seguir participando, no sobre el ahorro.

## 7. Riesgos

| Riesgo | Señal | Mitigación |
|---|---|---|
| Complejidad para el usuario | «¿Por qué mi saldo se partió?» | Mostrar un solo saldo y un reloj por tramo |
| Pérdida de wallet | El usuario pierde el teléfono | Recuperación por identidad verificada |
| Disputa por el reloj | «Me venció antes» | Registro auditable y notificaciones previas |
| Percepción de pérdida | Abandono tras un vencimiento | Avisos a 7, 3 y 1 día; recordatorio de uso |
| Fungibilidad | Riesgo CNV | Sin conversión a pesos, sin mercado secundario, sin rendimiento |

## 8. Rol en el MVP

**Es el núcleo.** Todo lo demás —plataforma, DAO, ciclos— se construye alrededor de esta regla. La primera versión puede ser una base de datos con:

- tabla de UTXO (monto, dueño, vence el);
- tabla de obligaciones (deudor, acreedor, estado);
- job diario que quema lo vencido y notifica.

## 9. Preguntas específicas

1. ¿El plazo `T` es igual para todos o depende del tipo de oferta?
2. ¿El vuelto renueva el plazo o conserva el original? (La propuesta de Hernán: ambos renuevan.)
3. ¿Qué pasa si el crédito vence mientras hay una disputa abierta?
4. ¿Se puede congelar un crédito durante una mediación?
5. ¿La obligación se transfiere con el crédito o queda en el emisor original?

## Enlaces

- [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Indice - Alternativas de bono|Índice — Alternativas de bono]]
- [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Alt 03 - App cerrada con ciclos|Alternativa 03 — App cerrada con ciclos]]
- [[03 - Direccion y Estrategia/Decisiones/Decision - Vencimiento en posesion|Decisión — Vencimiento en posesión]]
- [[07 - Tecnologia y Producto/Arquitectura - Creditos con vencimiento|Arquitectura — Créditos con vencimiento]]
