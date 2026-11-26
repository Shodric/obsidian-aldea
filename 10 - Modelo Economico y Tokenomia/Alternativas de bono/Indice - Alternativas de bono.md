---
tipo: indice
area: economia
estado: activo
actualizado: 2026-11-20
---

# Índice — Alternativas de bono

> [!info] Qué es esta carpeta
> La llamada con Hernán del **2026-11-20** puso sobre la mesa al menos **once formas distintas** de entender el bono. Muchas se mencionaron como sinónimos, pero no lo son: cambian el soporte, la regla de caducidad, quién emite, contra qué se emite y quién responde por la obligación.
>
> Esta carpeta separa esas once alternativas, las evalúa con los mismos criterios y propone una ruta. **No son decisiones tomadas**: son hipótesis de trabajo para discutir con Hernán, con legal y con la simulación.

## 1. El problema que el bono tiene que resolver

Antes de comparar alternativas, el test es siempre el mismo:

1. ¿Permite que alguien **sin dinero** acceda a bienes y servicios reales?
2. ¿Crea **demanda** para quien hoy no la tiene, sin sustituir la economía formal?
3. ¿Evita que el bono se guarde, se especule o se convierta en una moneda paralela?
4. ¿Mantiene la **obligación de entregar** aunque el bono venza?
5. ¿Se puede probar con **200–300 personas** y un presupuesto bajo?

Una alternativa que falle el punto 1 o el 4 no sirve, por más elegante que sea.

## 2. Cómo se evaluó

**Escala de factibilidad**

| Nivel | Significado |
|---|---|
| **Alta** | Se puede probar en el piloto sin habilitaciones nuevas ni dependencias externas. El equipo puede construirla y el riesgo legal se maneja con salvaguardas de diseño. |
| **Media** | Requiere una dependencia (municipio, vehículo legal, financiamiento) o una decisión regulatoria. Viable en 6–12 meses. |
| **Baja** | Requiere patrimonio, habilitación de la CNV o infraestructura que Aldea no tiene. No es viable en el horizonte del MVP. |

**Dimensiones**

| Dimensión | Pregunta |
|---|---|
| Técnica | ¿Se puede construir con el stack y el equipo actuales? |
| Legal | ¿Qué riesgo regulatorio, contractual y de datos tiene? |
| Operativa | ¿Quién la sostiene en el día a día y con cuánto esfuerzo? |
| Dependencias | ¿Qué actor externo tiene que decir que sí? |
| Costo de prueba | ¿Cuánto cuesta validarla antes de construir? |

> [!warning] Esto no es un dictamen legal
> Las valoraciones legales son **hipótesis de trabajo**. Ninguna reemplaza el dictamen de la abogada ni una consulta formal a la CNV.

## 3. Mapa de alternativas

| # | Alternativa | Eje | Factibilidad | Rol propuesto |
|---|---|---|---|---|
| 01 | [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Alt 01 - Bono fisico con vencimiento\|Bono físico con vencimiento]] | Soporte | Media | Respaldo para exclusión digital |
| 02 | [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Alt 02 - Oxidacion y demurrage\|Oxidación / demurrage]] | Caducidad | Baja | Referencia; no implementar |
| 03 | [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Alt 03 - App cerrada con ciclos\|App cerrada con ciclos]] | Soporte y emisión | Alta | Base del MVP, con ajustes |
| 04 | [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Alt 04 - UTXO con vencimiento en posesion\|UTXO con vencimiento en posesión]] | Caducidad | **Alta** | **Núcleo del MVP** |
| 05 | [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Alt 05 - NFT o bono social\|NFT / bono social]] | Naturaleza | Baja | Solo como comprobante |
| 06 | [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Alt 06 - Bono municipal\|Bono municipal]] | Emisor | Media-baja | Alianza de Fase 2/3 |
| 07 | [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Alt 07 - Plataforma privada de puntos\|Plataforma privada de puntos]] | Gobernanza | **Alta** | **Vehículo del MVP** |
| 08 | [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Alt 08 - Credito mas token de recompensa\|Crédito + token de recompensa]] | Dos unidades | Baja | Fase 3 |
| 09 | [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Alt 09 - Deuda con la DAO y obligacion negociable\|Deuda con la DAO y obligación negociable]] | Obligación | Media | Envoltorio legal del MVP |
| 10 | [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Alt 10 - Ingreso basico en bonos\|Ingreso básico en bonos]] | Emisión | Media | Semilla única, no UBI |
| 11 | [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Alt 11 - Bono respaldado en tierra o equity\|Bono respaldado en tierra o equity]] | Respaldo | Muy baja | Descartar |

## 4. Introducción a cada alternativa

### 01 — Bono físico con vencimiento
El formato original: papel con serie y fecha impresa. Es el más inclusivo y el más fácil de explicar, pero **no puede renovar el plazo al transferirse** sin un control manual. Sirve como última milla, no como núcleo.

### 02 — Oxidación / demurrage
El bono pierde valor gradualmente mientras está quieto. Resuelve la velocidad, pero exige marcar, calcular y controlar en cada operación. Hernán lo descartó por complejidad; además, es difícil de explicar y de defender ante el usuario.

### 03 — App cerrada con ciclos
Un circuito que se abre, se inscribe, circula y cierra. Es simple de construir y de auditar, pero el cierre crea el problema que Hernán identificó: **cerca del vencimiento nadie quiere recibir bonos**. El ciclo sirve como período contable, no como única regla de caducidad.

### 04 — UTXO con vencimiento en posesión
El crédito vence mientras está quieto y renueva su plazo al cambiar de manos. Es la innovación central de Aldea: resuelve la velocidad sin castigar el cierre de ciclo. **UTXO es una regla contable, no una obligación de usar blockchain**: se puede implementar en una base de datos.

### 05 — NFT / bono social
Hernán lo pensó como un NFT que representa cierta cantidad. El problema es que un NFT no es divisible ni fungible, y el circuito necesita vuelto. Su lugar útil no es la unidad, sino el **comprobante de entrega** no transferible.

### 06 — Bono municipal
El municipio emite bonos para personas sin trabajo y los comercios los aceptan a cambio de beneficios fiscales (por ejemplo, ABL). Resuelve la demanda inicial, pero depende de la voluntad política y de una ordenanza. Es una alianza, no la base del sistema.

### 07 — Plataforma privada de puntos
Cualquiera descarga la app, se registra, oferta y recibe puntos. No necesita municipio ni permiso previo. Es el vehículo de menor fricción para el MVP; su riesgo es quedarse sin masa crítica y sin ancla territorial.

### 08 — Crédito + token de recompensa
Dos unidades: el crédito que vence y un token permanente que se gana por participar. El token resuelve la retención, pero abre la puerta a la especulación, a la CNV y a un patrimonio que Aldea no tiene. Queda para Fase 3, si el circuito funciona.

### 09 — Deuda con la DAO y obligación negociable
La deuda no es con el vendedor, sino con la organización. La DAO emite, reclama y media; la obligación puede circular como un endoso. Es el puente entre el smart contract y el mundo legal, y la respuesta más sólida al «¿quién me obliga?».

### 10 — Ingreso básico en bonos
Un bono gratuito para quien no tiene nada que ofrecer. Como UBI mensual es inflacionario y difícil de fondear; como **semilla única con compromiso de oferta** puede ser la llave de entrada para los excluidos.

### 11 — Bono respaldado en tierra o equity
Una empresa con patrimonio emite un token contra el valor de la tierra. Es un valor negociable: exige CNV, propiedad, custodia y crea expectativa de rentabilidad. Contradice el principio de gratuidad. Descartar para Aldea.

## 5. Ranking y lectura

| Puesto | Alternativa | Puntaje | Por qué |
|---|---|---|---|
| 1 | **04 — UTXO con vencimiento en posesión** | 4.5/5 | Es la única que resuelve el problema central sin depender de nadie. Se implementa en base de datos. |
| 1 | **07 — Plataforma privada de puntos** | 4.5/5 | Menor fricción legal y operativa. Es el vehículo, no la regla económica. |
| 3 | **03 — App cerrada con ciclos** | 4.0/5 | Simple y auditable, pero el cierre de ciclo genera rechazo. Sirve como período contable. |
| 4 | **01 — Bono físico** | 3.0/5 | Inclusivo, pero no renueva el plazo y depende de control manual. |
| 4 | **09 — Deuda con la DAO** | 3.0/5 | Legalmente el más sólido; requiere vehículo legal y arbitraje. Versión liviana en el MVP. |
| 4 | **10 — Ingreso básico** | 3.0/5 | Útil como semilla única; inviable como UBI mensual sin fondeo. |
| 7 | **06 — Bono municipal** | 2.5/5 | Potente para la demanda, pero depende de la política y de una ordenanza. |
| 8 | **02 — Oxidación** | 2.0/5 | Compleja de operar y de explicar; el vencimiento en posesión logra lo mismo con menos fricción. |
| 8 | **05 — NFT** | 2.0/5 | No es divisible; sirve como comprobante, no como unidad. |
| 10 | **08 — Token de recompensa** | 1.5/5 | CNV, patrimonio y especulación. Fase 3 como mínimo. |
| 11 | **11 — Tierra o equity** | 1.0/5 | Es un valor negociable y contradice la gratuidad. |

### La ruta de menor riesgo

Las alternativas **no compiten entre sí**. La combinación más factible es:

| Capa | Alternativa | Qué aporta |
|---|---|---|
| Vehículo | **07 — Plataforma privada** | Baja fricción, sin dependencias políticas |
| Regla económica | **04 — UTXO con vencimiento en posesión** | Velocidad, renovación al transferir, anti-atesoramiento |
| Envoltorio legal | **09 — Deuda con la DAO** (versión liviana) | Contraparte, reclamo, mediación |
| Período contable | **03 — Ciclos** | Auditoría, reapertura, control de emisión |
| Arranque | **10 — Semilla única** | Inclusión de quien no tiene nada que ofrecer |

> [!important] La respuesta corta
> La más factible **como regla** es el **vencimiento en posesión (04)**. La más factible **como producto** es la **plataforma privada (07)**. La más factible **como contrato** es la **deuda con la DAO (09)**, en versión liviana. Ninguna alcanza sola.

## 6. Las que no son viables en el MVP

| Alternativa | Motivo | ¿Se descarta para siempre? |
|---|---|---|
| 05 — NFT | No es divisible ni fungible; el circuito necesita vuelto | No: sirve como comprobante de entrega |
| 08 — Token de recompensa | CNV, patrimonio, especulación | No: Fase 3, si el circuito funciona |
| 11 — Tierra o equity | Valor negociable; contradice la gratuidad | Sí, para Aldea |
| 02 — Oxidación | Complejidad operativa y cognitiva | No: referencia si falla el vencimiento |

## 7. Preguntas que surgen

### Las 12 que hay que responder antes de elegir

| # | Pregunta | Por qué importa |
|---|---|---|
| 1 | ¿El bono es una **unidad de cuenta** o un **comprobante de obligación**? | Si es unidad de cuenta, es fungible y hay que discutir CNV. Si es comprobante, la unidad de cuenta es otra cosa y el bono es un contrato. La llamada mezcla las dos. |
| 2 | ¿Quién emite: el participante, la DAO o el municipio? | Las tres aparecen en la llamada y son incompatibles como regla general. |
| 3 | ¿Se emite contra **oferta** (ya produje) o contra **obligación** (me comprometo)? | Cambia el riesgo, el respaldo y el marco legal. |
| 4 | ¿El vencimiento es una **regla económica** o una **sanción**? | Si es sanción, necesita debido proceso. Si es regla, es un parámetro que se comunica. |
| 5 | ¿Se puede **rechazar** un bono? ¿Quién verifica que el emisor «ya cumplió»? | Hernán dice que no mientras no cumpliste y que sí después. Falta el registro que lo pruebe. |
| 6 | ¿Qué impide la **emisión infinita** si cada uno emite contra su propia oferta? | El techo, el ciclo y la demanda. ¿Alcanzan? |
| 7 | ¿Cómo entra el que **no tiene nada que ofrecer**? | Es la objeción más fuerte de Rodrigo y la razón de ser de Aldea. |
| 8 | ¿Cómo se evita que el circuito sea **de pobres para pobres**? | Si nadie con capacidad de compra entra, la demanda es débil. |
| 9 | ¿**Blockchain** o base de datos? | La cadena solo se justifica si resuelve un problema de confianza o trazabilidad que un registro firmado no resuelve. |
| 10 | ¿Quién **fondea** la semilla y el fondo de garantía? | La DAO no tiene patrimonio. Sin fondeo, las alternativas 09 y 10 no arrancan. |
| 11 | ¿Cómo se mide la **inflación interna**? | Precios en créditos vs. pesos, canasta local, índice propio. Sin medición no hay ajuste. |
| 12 | ¿Qué **vehículo legal** tiene la DAO y quién arbitra? | Sin personalidad jurídica no hay contraparte ni reclamo. |

### Preguntas de segundo orden

1. ¿El bono se puede prestar, donar o heredar? Cada una abre un mercado secundario o una obligación que el diseño no previó.
2. ¿Qué pasa con el saldo al morir el titular o al cerrar el circuito?
3. ¿Cómo se valida una oferta sin crear un costo operativo alto?
4. ¿Qué pasa si la oferta no es deseada? Hernán dice «esperás el próximo ciclo». ¿Alcanza para retener?
5. ¿Cuál es el tamaño mínimo viable? ¿200, 500, 1.000 personas? ¿Qué densidad de oferta por categoría?
6. ¿Cómo se articula con el municipio sin capturarlo ni mezclar el rol de Hernán?
7. ¿Quién custodia las claves y qué pasa si se pierde el teléfono?
8. ¿Cómo se prueba la entrega? ¿Código tipo Mercado Libre/Minga? ¿Quién lo emite y lo valida?
9. ¿Qué datos se guardan y por cuánto tiempo? Seudónimo en el catálogo, identidad para sanciones: ¿dónde está la línea?
10. ¿Qué pasa si la DAO desaparece? ¿Quién hereda el registro y las obligaciones?
11. ¿Qué pasa si el valor de referencia en pesos se dispara? ¿Se indexa, se congela, se reemite?
12. ¿Cuál es el costo operativo por intercambio y quién lo paga?
13. ¿Cómo se cambian los parámetros (T, techo, devaluación) sin shocks ni captura?
14. ¿Qué pasa si la asamblea decide algo que viola la ley o la filosofía? ¿Hay un límite duro?

## 8. Qué probar en la simulación

| Hipótesis | Variable | Métrica | Umbral |
|---|---|---|---|
| H1: el vencimiento en posesión acelera la circulación sin vaciar el circuito | Plazo `T` | Velocidad de circulación | > 1 por ciclo |
| H2: el techo por participante evita la concentración | Techo | Gini de saldos | < 0.5 |
| H3: el circuito tolera free riders hasta cierto punto | % free riders | Intercambios por ciclo | No cae > 30% con 10% de free riders |
| H4: la semilla única incluye sin inflar | Semilla | Cobertura y precios | Cobertura > 50%, inflación < 10% |
| H5: el fondo de garantía es solvente | Tasa de default | Cobertura del fondo | Cubre default del 5–10% |
| H6: el vencimiento progresivo por saldo reduce el Gini más que el uniforme | Regla de vencimiento | Gini y velocidad | Mejora ambos |
| H7: el vale de necesidad básica mejora la retención de los más pobres | Categoría de gasto | Retención mes 2 | > 30% |
| H8: la reputación no monetaria sanciona sin expulsar | Reputación | Reincidencia | Baja sin caída de participación |

## Notas de esta carpeta

Propuestas nuevas: [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Propuestas alternativas - Bono Aldea|Propuestas alternativas — Bono Aldea]]

```dataview
TABLE alternativa, factibilidad, eje, estado
FROM "10 - Modelo Economico y Tokenomia/Alternativas de bono"
WHERE tipo = "modelo"
SORT alternativa ASC
```

## Enlaces

- [[04 - Reuniones/2026/11-Noviembre/2026-11-20 - Llamada con Hernan - Transcripcion|Transcripción de la llamada]]
- [[04 - Reuniones/2026/11-Noviembre/2026-11-20 - Llamada con Hernan - Apuntes|Apuntes de la llamada]]
- [[10 - Modelo Economico y Tokenomia/Modelo - Creditos de intercambio|Modelo — Créditos de intercambio]]
- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
- [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Propuestas alternativas - Bono Aldea|Propuestas alternativas — Bono Aldea]]
