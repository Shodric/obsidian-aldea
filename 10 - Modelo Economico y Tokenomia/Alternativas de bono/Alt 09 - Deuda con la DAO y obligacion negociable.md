---
tipo: modelo
estado: propuesta
area: economia
alternativa: "09"
eje: obligacion
factibilidad: media
actualizado: 2026-11-20
---

# Alternativa 09 — Deuda con la DAO y obligación negociable

> [!abstract] En una línea
> La deuda no es con el vendedor, sino con la organización. La DAO emite, reclama y media; la obligación puede circular como un endoso. Es el puente entre el smart contract y el mundo legal.

## 1. Qué se planteó en la llamada

> «Nosotros lo que estamos haciendo es establecer un contrato entre esa persona y nuestra sociedad, entre la organización DAO. [...] Esa persona no está en deuda con el vendedor, está en deuda con nosotros. Nosotros seríamos quienes le reclamamos a esa persona.»
> — Rodrigo, §8

> «Yo contraté a alguien obteniendo su deuda; compro su deuda, compro su milanesa, y tendría que entregar esa deuda a otra persona que la requiere. Y se hace circular.»
> — Hernán, §8

> «Eso tendría que ser una **obligación negociable**. Ese es el mejor ejemplo del mercado.»
> — Hernán, §10

## 2. Cómo funciona

**Capa 1 — La DAO como contraparte**
1. El participante se registra y acepta los términos.
2. La DAO emite el crédito **al vendedor** contra la promesa del comprador.
3. El comprador queda en deuda con la **DAO**, no con el vendedor.
4. La DAO registra la obligación con estado: `pendiente`, `en curso`, `cumplido`, `incumplido`, `en disputa`.
5. Si hay incumplimiento, la DAO reclama, media o sanciona.

**Capa 2 — La obligación negociable**
1. La obligación puede transferirse a otro participante (endoso).
2. El nuevo tenedor puede exigirla o volver a transferirla.
3. El valor de la obligación se descuenta según riesgo y plazo.
4. La DAO mantiene el registro de quién debe qué a quién.

## 3. Por qué se propuso

- **Resuelve el «¿quién me obliga?»**: hay una contraparte con nombre y reglas.
- **Centraliza la mediación**: un solo árbitro, no mil disputas bilaterales.
- **Separa crédito de obligación**: el crédito vence, la obligación no.
- **Permite circular la deuda**: el que necesita un servicio puede comprar la deuda de otro.
- **Da fuerza legal**: un contrato con una entidad es más exigible que un acuerdo entre pares.

## 4. Evaluación

| Dimensión | Valor | Fundamento |
|---|---|---|
| Técnica | Media | Registro de obligaciones, estados y endosos |
| Legal | **Alta** | Es un contrato; requiere vehículo legal, términos y arbitraje |
| Operativa | Media | Comité, mediación, registro y auditoría |
| Dependencias | **Alta** | Personalidad jurídica de la DAO o de la asociación |
| Costo de prueba | Medio | Redacción legal, registro y un piloto acotado |

**Factibilidad: Media (3/5).** La capa 1 es viable en el MVP; la capa 2 es Fase 2/3.

## 5. El problema central

La DAO como contraparte es sólida, pero **la DAO no existe legalmente todavía**. Sin personalidad jurídica:

- no puede firmar;
- no puede reclamar;
- no puede ser demandada;
- no puede recibir un fondo de garantía.

La obligación negociable agrega otro problema: si se crea un mercado de deudas, aparece un **precio del riesgo** y, con él, un «Veraz» informal. El que no puede pagar queda marcado y excluido, que es exactamente lo que Aldea quiere evitar.

## 6. Riesgos

| Riesgo | Señal | Mitigación |
|---|---|---|
| DAO sin personalidad | No puede contratar | Constituir asociación o cooperativa antes del piloto |
| Mercado de deuda especulativo | Se compran deudas para cobrar | Límites, prohibición de cesión a terceros |
| Exclusión tipo Veraz | Listas negras | Reputación con derecho a reparación |
| Disputas sin árbitro | Conflictos escalan | Mediación y reglamento |
| Privacidad | Datos de deudores expuestos | Datos mínimos, acceso restringido |

## 7. Rol en el MVP

**Versión liviana, sí.** No hace falta una DAO on-chain ni un mercado de obligaciones. Alcanza con:

- una **asociación civil o cooperativa** que firme los términos;
- un **registro de obligaciones** con estados;
- un **reglamento de mediación**;
- la DAO como contraparte y garante.

La obligación negociable se evalúa después, con datos de cumplimiento y un marco legal claro.

## 8. Preguntas específicas

1. ¿Qué vehículo legal se usa: asociación, cooperativa, fundación o SAS?
2. ¿Quién arbitra y quién paga el arbitraje?
3. ¿La obligación se transfiere con el crédito o queda en el emisor original?
4. ¿Qué pasa con la deuda si el deudor muere o se va del territorio?
5. ¿Se puede ceder la deuda a un tercero ajeno al circuito?

## Enlaces

- [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Indice - Alternativas de bono|Índice — Alternativas de bono]]
- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
- [[02 - Gobernanza y Comunidad/Reglas de membresia y sanciones|Reglas de membresía y sanciones]]
- [[13 - Legal y Cumplimiento/Indice - Legal y Cumplimiento|Índice — Legal y cumplimiento]]
