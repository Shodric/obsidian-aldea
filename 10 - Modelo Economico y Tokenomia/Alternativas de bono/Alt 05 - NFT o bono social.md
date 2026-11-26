---
tipo: modelo
estado: propuesta
area: economia
alternativa: "05"
eje: naturaleza
factibilidad: baja
actualizado: 2026-11-20
---

# Alternativa 05 — NFT / bono social

> [!abstract] En una línea
> Hernán lo pensó como un NFT que representa cierta cantidad. El problema es que un NFT no es divisible ni fungible, y el circuito necesita vuelto.

## 1. Qué se planteó en la llamada

> «Yo lo pienso como un **bono social**: es un NFT que equivale a cierta cantidad, pero el valor es implícito entre las personas. Cada uno le da el valor que quiere.»
> — Hernán, §3

> «Técnicamente no es lo mismo, porque un NFT no es fungible. Pero regulatoriamente, para la CNV, estás haciendo un intercambio de un producto por un servicio. [...] La idea es que funcione como un **bono de trueque dinámico**.»
> — Rodrigo, §3

## 2. Cómo funciona

1. Cada oferta se representa como un NFT único: «10 horas de jardinería de Ana», «20 docenas de empanadas de Beto».
2. El NFT tiene metadata: oferente, descripción, valor, vencimiento.
3. Para comprar, se transfiere el NFT completo.
4. El vendedor recibe el NFT y lo puede volver a transferir.

## 3. Por qué se propuso

- **Trazabilidad**: cada bono tiene historia y dueño.
- **Identidad**: no se confunde una oferta con otra.
- **Encuadre legal**: un NFT es un objeto digital único, no una moneda.
- **Narrativa**: «bono social» suena menos a moneda que «token».

## 4. Evaluación

| Dimensión | Valor | Fundamento |
|---|---|---|
| Técnica | Media | Un NFT por oferta es fácil; el problema es el vuelto y la divisibilidad |
| Legal | **Baja** | Si se parte y se transfiere, deja de ser NFT y se vuelve fungible: cambia el encuadre |
| Operativa | Media | Requiere wallet, gas y educación; difícil para el usuario no cripto |
| Dependencias | Baja | No necesita municipio |
| Costo de prueba | Medio | Mint, wallet, red; más caro que una base de datos |

**Factibilidad: Baja (2/5).** No resiste la primera operación con vuelto.

## 5. El problema central

El circuito necesita **dividir y dar vuelto**. Si Ana tiene un NFT de 10.000 créditos y compra 8.000 en empanadas, el NFT no se puede partir: o transfiere todo y Beto le devuelve 2.000 (otro NFT), o no hay intercambio.

En el momento en que se parte, el NFT deja de ser único y se convierte en una ficha fungible. Ahí se cae el encuadre de «NFT» y vuelve el problema regulatorio que Rodrigo señaló.

Además, «cada uno le da el valor que quiere» es exactamente lo que produce un precio de mercado: el «bono blue» que Hernán quería evitar.

## 6. Riesgos

| Riesgo | Señal | Mitigación |
|---|---|---|
| No hay vuelto | Operaciones trabadas | Usar token fungible, no NFT |
| Valuación disputada | Cada uno pide un valor distinto | Precio fijo ex ante |
| Costo de red | Gas alto en operaciones chicas | Base de datos o red de bajo costo |
| UX cripto | Abandono en el alta | Wallet custodial, sin claves para el usuario |

## 7. Lo que sí sirve del NFT

No como **unidad**, pero sí como **comprobante**:

- **Recibo de entrega no transferible**: prueba que Beto entregó las empanadas y que Ana cumplió.
- **Certificado de oferta**: acredita que la oferta existió y quién la respaldó.
- **Historial reputacional**: no se transfiere, no se cotiza, no se especula.

Es una pieza útil del rompecabezas, no la unidad de cuenta.

## 8. Rol en el MVP

**Descartado como unidad.** Se puede explorar como **comprobante de entrega** en la Fase 2, cuando el circuito ya tenga volumen y haga falta prueba verificable.

## 9. Preguntas específicas

1. ¿El NFT representa la oferta o el crédito?
2. ¿Qué pasa cuando la oferta se agota o se vence?
3. ¿Se puede dividir sin perder la condición de NFT?
4. ¿Quién paga el costo de emisión?

## Enlaces

- [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Indice - Alternativas de bono|Índice — Alternativas de bono]]
- [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Alt 04 - UTXO con vencimiento en posesion|Alternativa 04 — Vencimiento en posesión]]
- [[13 - Legal y Cumplimiento/Marco regulatorio - Tokens y trueque en Argentina|Marco regulatorio — Tokens y trueque]]
