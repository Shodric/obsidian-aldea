---
tipo: documento
estado: borrador
area: estrategia
proyecto: "[[Proyecto - Simulacion agentica]]"
actualizado: 2026-11-20
---

# Idea en análisis — Bono como obligación negociable

> [!important] Estado
> **Idea en análisis, no decisión.** No forma parte del MVP ni de la primera corrida. Se registra para discutirla con Hernán y, si avanza, diseñar un experimento específico.

## 1. La idea en una frase

Cuando una persona recibe un bono, no solo obtiene un derecho a comprar: también asume una **obligación de contraprestación**. La DAO puede gestionar esa obligación como un intermediario activo, enviándole ofertas de trabajo, productos o servicios de otros participantes para que pueda cumplirla.

La analogía que surgió en la conversación es la de una **obligación negociable** del mercado de capitales. La analogía es útil para pensar el concepto, pero **no** debe usarse como definición legal o pública sin asesoramiento.

## 2. Por qué aparece

El modelo actual tiene un hueco práctico:

- El bono da derecho a comprar, pero no garantiza que el tenedor encuentre algo que necesite.
- El participante que recibió emisión inicial tiene un compromiso de venta, pero puede no saber a quién venderle.
- La DAO conoce la oferta y la demanda de la comunidad, pero hoy no tiene un rol activo de matching.
- Si el bono vence y el tenedor no encontró nada, perdió el derecho; si el participante no vendió y no tuvo demanda, no se lo sanciona. El sistema puede quedar quieto.

La idea busca convertir a la DAO en un **motor de encuentros**: no solo emite y sanciona, también acerca ofertas y demandas para que el circuito circule.

## 3. Tres lecturas posibles

La frase “al tener el bono obtiene una obligación” puede significar tres cosas distintas. Hay que elegir una antes de diseñar nada.

### Lectura A — El bono es un derecho, y la obligación es del que recibió la emisión

Es el modelo actual:

- La DAO emite créditos contra una oferta.
- El participante que los recibe se compromete a vender.
- El bono circula; la obligación de vender queda con el participante, no viaja con el bono.
- La DAO puede enviarle ofertas de trabajo o productos para ayudarlo a cumplir.

**Ventaja:** es compatible con lo que ya está diseñado. **Límite:** no convierte al bono en una obligación negociable; solo agrega un servicio de matching.

### Lectura B — El bono es una obligación que viaja con el título

El bono representa una deuda u obligación de quien lo emitió, y quien lo tiene puede exigirla. Al transferirse, la obligación cambia de manos o sigue al emisor.

- Esto se parece más a una obligación negociable o a un título de deuda.
- Requiere definir quién es el deudor, qué garantía hay y cómo se ejecuta.
- Es la lectura más riesgosa legalmente y la más difícil de explicar.

**Problema:** si la obligación viaja con el bono, el tenedor final no sabe quién le debe; si queda con el emisor, el bono es un derecho contra un emisor concreto, no una unidad fungible del circuito.

### Lectura C — El bono es un derecho, pero comprar crea una obligación de contraprestación

Cuando alguien compra un producto o servicio, no solo gasta créditos: asume el compromiso de devolver valor al circuito con trabajo, producto o servicio. La DAO le envía ofertas para que pueda cumplir.

- Es un modelo más cercano al **crédito mutuo** o a una cámara de compensación.
- El comprador queda en deuda con la comunidad, no solo con el vendedor.
- La DAO actúa como intermediaria y garante.

**Problema:** si toda compra crea una obligación, el sistema necesita un registro de deuda por participante, un mecanismo de compensación y una regla de incumplimiento. Es un cambio profundo respecto del modelo actual.

> [!question] Pregunta central
> ¿La obligación nace al **recibir la emisión inicial**, al **comprar** o al **vender**? Las tres respuestas producen economías distintas.

## 4. Cómo funcionaría, si se adopta la lectura A o C

```text
1. El participante se registra y declara qué ofrece.
2. Recibe créditos y queda registrado su compromiso.
3. La DAO conoce su oficio, skills, necesidades y disponibilidad.
4. La DAO detecta una necesidad de otro participante.
5. Le envía una oferta: “X necesita 2 horas de jardinería; paga 2 créditos”.
6. El participante acepta o rechaza.
7. Si acepta, vende, cobra y reduce su compromiso.
8. Si rechaza, queda registrado; si había demanda real, puede afectar su reputación.
9. La DAO aprende y ajusta las ofertas siguientes.
```

La DAO no obliga a aceptar cualquier trabajo. Envía **ofertas compatibles** con la oferta declarada, la ubicación y la disponibilidad. El participante mantiene el derecho a rechazar, pero el rechazo tiene consecuencias dentro del sistema.

## 5. Qué rol tendría la DAO

| Rol | Qué haría | Riesgo |
|---|---|---|
| Emisora | Crea los créditos contra una oferta | Ya existe |
| Garante | Responde por las reglas y media | Ya existe |
| **Intermediaria** | Acerca oferta y demanda, envía matches | Nuevo |
| **Empleadora** | Asigna tareas y controla su ejecución | Peligroso: cambia la naturaleza del proyecto |
| **Árbitro** | Resuelve disputas y sanciona | Ya existe, vía Fiscalía |
| **Banco de información** | Guarda perfiles, skills y disponibilidad | Privacidad y datos |

La diferencia clave es **intermediaria vs empleadora**. Si la DAO solo sugiere, el participante conserva autonomía. Si la DAO asigna, controla y sanciona el rechazo, se parece a un empleador o a una agencia de trabajo, con obligaciones laborales y regulatorias.

## 6. Argumentos a favor

- **Activa la oferta:** convierte un compromiso pasivo en una oportunidad concreta.
- **Reduce el free riding:** el que recibió créditos sabe que la DAO le va a buscar una contraprestación.
- **Mejora la circulación:** acerca al que tiene un bono con el que necesita un servicio.
- **Usa información que la DAO ya tiene:** perfiles, ofertas, necesidades y ubicación.
- **Puede reducir el vencimiento:** si el tenedor encuentra qué comprar, usa el bono antes de perderlo.
- **Da un rol útil a la DAO:** además de emitir y sancionar, ayuda a que las cosas pasen.
- **Permite medir:** aceptación de matches, tiempo de colocación, cumplimiento y satisfacción.

## 7. Riesgos y preguntas

### 7.1 Riesgo legal y de lenguaje

“Obligación negociable” es un término del mercado de capitales. En Argentina, las obligaciones negociables son valores emitidos por sociedades, sujetos a régimen de oferta pública y autorización de la CNV. Un bono de trueque **no es** una obligación negociable y no debería presentarse así.

- Usar “obligación negociable” solo como analogía interna.
- Hacia afuera: “compromiso de contraprestación”, “derecho de intercambio con compromiso” o “crédito de intercambio”.
- Antes de usar cualquier término financiero, consultar a la abogada.

### 7.2 Riesgo de trabajo forzado

Si la DAO envía ofertas y el participante no puede rechazarlas sin sanción, se parece a trabajo forzado. Hay que garantizar:

- Consentimiento.
- Derecho a rechazar sin sanción automática.
- Ofertas compatibles con la oferta declarada.
- Límites de cantidad y horario.
- Excepción por enfermedad, cuidado o falta de disponibilidad.
- Apelación.

### 7.3 Riesgo de spam y presión

Si la DAO envía muchas ofertas, el participante puede sentirse acosado. Hay que definir:

- Frecuencia máxima.
- Prioridad y relevancia.
- Canal (teléfono, notificación).
- Opción de pausar.
- Silencio o baja.

### 7.4 Riesgo de favoritismo y concentración

La DAO puede favorecer a los que mejor se llevan con el administrador o a los que tienen más reputación. Hay que definir criterios transparentes y auditables.

### 7.5 Riesgo de mercado distorsionado

Si la DAO garantiza trabajo a todos, puede desplazar la iniciativa privada o crear dependencia. Si solo garantiza a algunos, puede crear privilegios.

### 7.6 Riesgo de datos

La DAO necesitaría saber skills, disponibilidad, ubicación y necesidades. Eso es información personal y sensible. Hay que definir finalidad, retención y acceso.

### 7.7 Preguntas para Hernán

1. ¿La obligación nace al recibir la emisión, al comprar o al vender?
2. ¿La DAO puede enviar ofertas sin que el participante las pida?
3. ¿El participante puede rechazar todas sin sanción?
4. ¿Qué pasa si ninguna oferta es compatible con su oficio?
5. ¿La DAO garantiza el trabajo o solo lo sugiere?
6. ¿Quién paga el costo de matching y de administración?
7. ¿La obligación se puede transferir a otra persona?
8. ¿Qué pasa si el participante ya cumplió su compromiso?
9. ¿Cómo se mide el valor de la contraprestación?
10. ¿Qué nombre usamos hacia afuera para no caer en “valor negociable”?

## 8. Cómo lo probaríamos en el simulador

La idea se puede modelar como un **servicio de matching de la DAO**, separado del bono:

- Entidad `DaoOffer` o `MatchProposal`.
- Campos: `id`, `agentId`, `needId`, `offerId`, `credits`, `hours`, `location`, `status`, `expiresAt`.
- Herramienta o hook `dao.match`: la DAO propone; el agente acepta o rechaza.
- El agente puede rechazar sin sanción automática; el rechazo se registra.
- El hook `commitment-tracker` actualiza el compromiso cuando el agente vende.
- El experimento E9 compara “con matching” vs “sin matching”.

**Métricas:**

- Tasa de aceptación de matches.
- Tiempo hasta el primer match.
- Porcentaje de compromisos cumplidos.
- Tasa de vencimiento.
- Rechazos y motivos.
- Percepción de presión o spam.
- Costo por match.
- Distribución por agente y por rubro.

**Hipótesis H9:** el matching de la DAO aumenta la tasa de cumplimiento y reduce el vencimiento, pero puede aumentar la presión y el costo operativo. El efecto neto depende de la calidad del match y de la libertad de rechazo.

> [!warning] No en la primera corrida
> E9 es una idea para después de E1-E8. Primero hay que validar el circuito base sin matching. Si no funciona sin DAO activa, el matching puede tapar el problema en vez de resolverlo.

## 9. Decisión propuesta

| Opción | Veredicto |
|---|---|
| Incluirlo en el MVP | **No.** Agrega complejidad legal, operativa y de datos. |
| Modelarlo como experimento E9 | **Sí, más adelante.** |
| Usar “obligación negociable” hacia afuera | **No.** Usar lenguaje de intercambio y compromiso. |
| Mantener la idea en análisis | **Sí.** Registrarla y discutirla con Hernán. |

## 10. Relación con el modelo actual

| Concepto actual | Idea nueva | Diferencia |
|---|---|---|
| Bono = derecho a recibir | Bono = derecho + obligación | Cambia la naturaleza del bono |
| Compromiso del emisor inicial | Obligación de contraprestación | Puede ampliarse a cada compra |
| DAO = garante | DAO = intermediaria activa | Nuevo rol operativo |
| Sanción por rechazo con demanda | Sanción por rechazo de match | Más discrecional, más riesgo |
| Vencimiento del lote | Vencimiento del derecho | La obligación no caduca |

## 11. Enlaces

- [[00A - Concepto y modelo economico|Concepto y modelo económico]]
- [[03 - Diseno experimental|Diseño experimental]]
- [[04 - Arquitectura tecnica|Arquitectura técnica]]
- [[05 - Prompts y perfiles|Prompts y perfiles]]
- [[02 - Requisitos|Requisitos]]
- [[Proyecto - Simulacion agentica|Proyecto — Simulación agéntica]]
