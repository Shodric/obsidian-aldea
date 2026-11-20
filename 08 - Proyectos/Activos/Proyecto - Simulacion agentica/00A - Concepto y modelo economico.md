---
tipo: documento
estado: borrador
area: estrategia
proyecto: "[[Proyecto - Simulacion agentica]]"
actualizado: 2026-11-20
---

# Concepto y modelo económico — Simulación

> [!important] Para qué sirve este documento
> Los documentos 01 a 09 explican **cómo** construir el simulador. Este documento explica **qué** estamos simulando y **por qué** esas reglas tienen sentido. Sin esta capa, el simulador puede ejecutarse bien y producir resultados que no significan nada.

## 1. Qué es Aldea

**Definición corta:** Aldea es una red local de intercambio que usa un crédito gratuito, caduco y no convertible para crear demanda donde falta dinero, sin reemplazar la economía formal.

| Es | No es |
|---|---|
| Una economía complementaria y local | Una moneda paralela o de curso legal |
| Un crédito que circula y vence | Un activo de inversión o un token con rentabilidad |
| Una red de personas que ofrecen bienes, servicios y oficios | Un marketplace con dinero fiduciario |
| Una comunidad con reglas, garantía y arbitraje | Una app sin gobierno ni resolución de conflictos |
| Una herramienta para activar capacidad ociosa | Un reemplazo del sueldo, la vivienda o los servicios básicos |

**Propósito:** que una persona con capacidad de producir o de prestar un servicio pueda conseguir otros bienes y servicios aunque no tenga pesos suficientes en ese momento. El circuito no crea dinero: crea **demanda recíproca** y la organiza.

**Público:** trabajadores informales, feriantes, artesanos, oficios de baja escala y microemprendedores. No es para vivienda, servicios complejos ni grandes compras. La economía formal sigue existiendo: el sueldo paga la vivienda y los servicios; el circuito cubre otros intercambios.

**Territorio:** el piloto se evalúa en el conurbano por densidad y economía social; Azul queda como segundo escenario. La unidad es el barrio o la zona, no la provincia.

**Gobernanza:** una DAO o asociación local actúa como contraparte y garante; una asamblea define las reglas; la Fiscalía media y sanciona; el municipio puede acompañar, pero no es dueño del circuito.

**Tecnología:** una app simple primero; blockchain solo cuando resuelva un problema real de confianza o trazabilidad. El MVP no necesita token de recompensa ni dinero real.

## 2. Qué es un bono

### 2.1 Definición de trabajo

> [!important] Definición propuesta para el simulador
> Un **bono** —también llamado **crédito de intercambio**— es un derecho nominal, gratuito, fungible y divisible a recibir bienes o servicios dentro del circuito. Está denominado en horas de trabajo, no se convierte a pesos ni a cripto, y vence mientras está en posesión de quien lo tiene. Su respaldo último es la capacidad de producción de la comunidad y la garantía de la DAO/asociación.

Esta definición es una **propuesta de trabajo**, no una decisión cerrada con Hernán. Si cambia la naturaleza del bono, cambian las reglas y las métricas.

### 2.2 Tres capas y tres nombres

| Capa | Nombre canónico | Qué es |
|---|---|---|
| Usuario | **Bono** | Lo que la persona ve y usa para pagar |
| Contabilidad | **Crédito de intercambio** | La unidad de cuenta y el lote que se transfiere |
| Técnica | **Token de intercambio** | La representación digital del crédito; no es una criptomoneda |

Evitar decir “moneda” salvo para aclarar que **no** lo es. Evitar “inversión”, “rendimiento” y “cotización”.

### 2.3 Quién debe qué

| Actor | Derecho | Obligación |
|---|---|---|
| Tenedor del bono | Usarlo antes de que venza | Aceptarlo como pago si participa del circuito y la operación cumple las reglas |
| Participante que recibe emisión inicial | Recibir créditos | Entregar la oferta que declaró; el compromiso no caduca con el bono |
| Vendedor | Cobrar en créditos | Entregar el bien o servicio y confirmar la operación |
| DAO / asociación | Emitir y gobernar el circuito | Garantizar las reglas, mediar y sostener la confianza; no reembolsar en pesos |
| Fiscalía | Recibir denuncias y resolver | Aplicar debido proceso, evidencia y apelación |

**La distinción clave:** el bono **no es la deuda**. Es el instrumento que da derecho a exigir producción del circuito. La obligación de vender del participante se registra aparte, en el compromiso. Cuando el bono vence, se extingue el instrumento, pero **no** se extingue automáticamente el compromiso de quien lo recibió.

### 2.4 Qué respalda al bono

No hay respaldo en pesos, en cripto ni en una reserva fraccionaria. El respaldo es:

1. **Oferta real**: hay bienes y servicios publicados y disponibles.
2. **Compromiso**: quien recibió créditos se comprometió a vender.
3. **Garantía**: la DAO/asociación hace cumplir las reglas y media.
4. **Confianza**: los participantes creen que podrán usar el bono antes de que venza.

Si falla la oferta, el bono pierde valor aunque el sistema funcione técnicamente. Si falla la confianza, la gente deja de aceptarlo. Si falla la garantía, aparecen los free riders y los conflictos.

### 2.5 Qué pasa cuando vence

- Vence **el lote**, no todo el saldo del agente.
- El tenedor pierde el derecho; no hay reembolso en pesos ni en cripto.
- Contablemente, se extingue el pasivo del circuito; **no** se registra como ingreso ni como ganancia.
- El compromiso de venta del participante que recibió la emisión inicial **sigue vigente** hasta que lo cumpla o sea sancionado.
- No hay reemisión automática del mismo lote. Un nuevo ciclo puede emitir créditos nuevos según las reglas.
- La app muestra el saldo por fecha de vencimiento y avisa antes.

> [!question] Decisión abierta
> ¿La emisión inicial se repone en cada ciclo o solo al ingresar? Para la primera simulación se propone **una emisión inicial por corrida, sin reemisión automática**, para observar el efecto puro del vencimiento.

### 2.6 Qué lo diferencia de otros instrumentos

| Instrumento | Se parece en | Se diferencia en |
|---|---|---|
| Moneda | Sirve para pagar | No es de curso legal, no se convierte, vence y no tiene política monetaria |
| Vale o gift card | Representa un derecho a consumir | No está atado a un solo comercio y circula entre participantes |
| Crédito mutuo | Crea obligaciones recíprocas | La DAO es la contraparte y el vencimiento es individual |
| Banco de tiempo | Usa horas como unidad | Incluye productos, precios e inputs, no solo servicios |
| NFT | Es digital y trazable | Es fungible y divisible; no representa un activo único |
| Valor negociable | Puede circular | No promete rentabilidad ni convertibilidad; no se comercializa |

## 3. El circuito en una página

```text
1. La persona se registra y declara qué ofrece.
2. Recibe créditos iniciales proporcionales a su oferta, dentro de un mínimo y un máximo.
3. Esos créditos fijan su compromiso mínimo de venta.
4. Publica su oferta en el catálogo y la ve en el teléfono.
5. Otro participante compra con créditos.
6. El comprador gasta primero los lotes que vencen antes (FIFO).
7. El vendedor recibe un lote nuevo, con su propio plazo.
8. La entrega se confirma; si es diferida, queda en escrow.
9. Si un lote no se gasta, vence y sale de circulación.
10. Al cerrar el ciclo se evalúa el compromiso, se sanciona el rechazo y se revisan los resultados.
```

**Regla fundamental:** una venta **no crea créditos nuevos**. Solo transfiere créditos existentes. La única creación es la emisión inicial contra una oferta (y, si se define, la emisión de un nuevo ciclo).

### 3.1 Un ejemplo numérico

- Marta declara que puede ofrecer 10 docenas de empanadas por semana; el sistema le asigna 10 créditos iniciales (1 crédito = 1 hora; el ejemplo es ilustrativo).
- Jorge necesita empanadas y tiene 4 créditos. Compra 2 docenas por 2 créditos.
- Marta recibe 2 créditos nuevos, con vencimiento a 30 días; su compromiso baja de 10 a 8.
- Jorge gastó primero el lote que vencía antes.
- Si Marta no vende nada en 30 días y rechaza una compra con demanda, puede ser sancionada. Si no recibió ninguna compra, no se la sanciona.
- Si Jorge no gasta sus créditos, vencen. Perdió el derecho, pero su compromiso de vender (si recibió emisión) sigue.

## 4. Reglas económicas del simulador

| Parámetro | Definición | Valor inicial propuesto | Estado |
|---|---|---|---|
| Unidad de cuenta | 1 crédito = X horas de trabajo | 1 crédito = 1 hora | Propuesto |
| Emisión inicial | Créditos contra oferta declarada | Proporcional a la oferta, con mínimo y máximo | Propuesto |
| Compromiso mínimo | Ventas que el participante debe aceptar | Igual a la emisión inicial | Propuesto |
| Vencimiento | Plazo de cada lote en posesión | 15 / 30 / 60 días según escenario | Propuesto |
| Gasto | Orden de consumo de lotes | FIFO: primero el que vence antes | Definido |
| Precio | Precio en créditos | Fijo ex ante, sin regateo en el MVP | Definido |
| Sanción | Consecuencia por rechazar venta con demanda | Suspensión del ciclo siguiente + reputación | Propuesto |
| Sin demanda | Caso sin solicitudes de compra | No se sanciona | Definido |
| Token de recompensa | Token permanente por superar el compromiso | Fuera del MVP | Definido |
| Efectivo | Sueldo, plan social o ingreso mixto | Variable por agente; no se imprime | Propuesto |
| Supermercado | Venta en efectivo en etapa 1 | Solo efectivo; etapa 2 evalúa bonos | Definido |
| Ciclo | Marco de inscripción y evaluación | 28 días | Definido |
| Agentes | Cantidad de la primera corrida | 10 | Definido |
| Repeticiones | Corridas por escenario | 5 | Definido |

> [!warning] Cifras
> Los valores son **parámetros de simulación**, no valores aprobados del mundo real. Las cifras en ARS que aparecen en la llamada son ejemplos. Para el simulador conviene usar unidades abstractas y no pretender precisión en pesos.

## 5. Por qué alguien aceptaría un bono

Un agente acepta un bono si el beneficio esperado de usarlo supera el costo de aceptarlo. Los motivos que el simulador debe representar:

1. **Necesidad presente:** quiere un bien o servicio ahora y no tiene pesos suficientes.
2. **Compromiso:** recibió emisión inicial y debe vender para cumplir.
3. **Confianza:** cree que otros van a aceptar el bono y que la DAO garantiza las reglas.
4. **Vencimiento:** sabe que si no lo usa, lo pierde; eso lo empuja a circular.
5. **Complemento:** no reemplaza su sueldo; le permite acceder a cosas que no podría comprar con pesos.
6. **Reputación:** quiere mantener su lugar en la comunidad y evitar sanciones.
7. **Alternativa:** no tiene una mejor opción de venta en efectivo.

Si ninguno de estos motivos alcanza, el circuito no arranca aunque la app funcione. La simulación tiene que medir **aceptación**, no solo transacciones.

## 6. Modelo de decisión del agente

### 6.1 Estado mínimo

Cada agente tiene:

- **Necesidades** (bienes y servicios que quiere).
- **Capacidad de producción** (qué sabe hacer y cuánto puede ofrecer).
- **Efectivo** y **créditos** por lote.
- **Tiempo** y **energía**.
- **Confianza** en el circuito y **reputación**.
- **Perfil**: optimista, neutro, especulativo o escéptico.
- **Memoria** de experiencias y rumores.
- **Teléfono** y red de contactos.

### 6.2 Heurística mínima

Para el modo mock, cada agente evalúa sus acciones con una regla simple:

```text
valor_esperado(acción) =
  satisfacción_de_necesidad
  + ingreso_esperado
  + reputación
  + confianza
  - riesgo_de_incumplimiento
  - esfuerzo
  - riesgo_de_vencimiento
```

No hace falta una función de utilidad perfecta. Hace falta que las decisiones sean **explicables** y que el modo mock sea reproducible. El LLM puede usarse para el diálogo y para justificar la decisión, pero no para inventar reglas económicas.

### 6.3 Perfiles y sesgos

| Perfil | Sesgo principal | Qué debería hacer |
|---|---|---|
| Optimista | Confía, prueba, coopera | Acepta bonos, compra y vende, invita a otros |
| Neutro | Calcula costo/beneficio | Participa si le conviene; cambia según la experiencia |
| Especulativo | Busca arbitraje y reserva | Acapara si puede, prueba precios paralelos, explota vencimientos |
| Escéptico | Desconfía del sistema | Acepta solo si conoce al vendedor o si la DAO le da garantía |

El perfil no debe ser una etiqueta decorativa: tiene que cambiar la probabilidad de aceptar, el uso del teléfono y la reacción a una sanción.

### 6.4 Qué se espera observar

- Si los agentes con menos efectivo usan más el circuito.
- Si los especuladores estabilizan o desestabilizan.
- Si el teléfono y el grupo de la ciudad ayudan a coordinar o amplifican rumores.
- Si las sanciones disuaden el free riding sin expulsar a los que no tienen demanda.
- Si el vencimiento acelera la circulación o genera rechazo.

## 7. Qué queremos probar

### 7.1 Preguntas de decisión

El simulador no está para “ver qué pasa”. Está para responder decisiones concretas:

1. ¿Con cuántos agentes y qué diversidad de oferta el circuito se sostiene?
2. ¿Qué plazo de vencimiento equilibra circulación y confianza?
3. ¿El compromiso mínimo reduce el free riding sin excluir a quien no tiene demanda?
4. ¿La DAO como contraparte mejora la aceptación?
5. ¿El teléfono y el grupo de la ciudad mejoran la coordinación?
6. ¿Qué sanción es suficientemente fuerte sin ser expulsiva?
7. ¿El precio fijo evita la especulación o crea escasez?
8. ¿La diversidad de oferta es la variable más importante?

### 7.2 Hipótesis y señales

| Hipótesis | Variable | Métrica | Señal de sostén | Señal de falla |
|---|---|---|---|---|
| H1: el circuito arranca y se sostiene | 10 agentes, 28 días | Agentes que compran y venden | ≥60% con al menos una operación | <30% con operaciones |
| H2: el vencimiento acelera la circulación | T = 15/30/60 | Velocidad y tasa de vencimiento | Más intercambios con T corto y vencimiento <20% | Vencimiento >40% o caída de intercambios |
| H3: el compromiso reduce el free riding | Con/sin compromiso | Rechazos con demanda | Rechazos <20% y participación ≥60% | Rechazos >40% o participación <30% |
| H4: la DAO mejora la aceptación | Garantía DAO vs bilateral | Tasa de aceptación | Aceptación mayor con DAO | Aceptación igual o menor |
| H5: el teléfono mejora la coordinación | Con/sin teléfono | Intercambios y confianza | Más intercambios y confianza ≥3,5/5 | Más conflictos o confianza <2,5/5 |
| H6: la sanción sostiene la cooperación | Débil/media/fuerte | Free riding y participación | Free riding <20% sin caída de participación | Participación <30% |
| H7: el precio fijo limita la especulación | Fijo/negociado | Dispersión y stock | Menos dispersión y menos faltantes | Precios paralelos o desabastecimiento |
| H8: la diversidad de oferta es condición | Homogénea/diversa | Categorías activas | ≥5 categorías y más intercambios | <3 categorías y estancamiento |

> [!warning] Umbrales
> Estos umbrales son **hipótesis operativas** para la primera corrida, no verdades. Se ajustan después de ver los datos y de validarlos con Hernán.

### 7.3 Qué NO prueba el simulador

- No prueba adopción real ni demanda real.
- No prueba viabilidad legal ni tributaria.
- No predice el comportamiento de una comunidad concreta.
- No prueba efectos de red con 10 agentes.
- No reemplaza un piloto territorial.
- No convierte a los agentes LLM en personas.

**Con 10 agentes se prueba un mecanismo, no un mercado.** Es un túnel de viento: sirve para detectar contradicciones y ajustar parámetros antes de gastar en el piloto.

## 8. Calibración y datos de partida

| Dato | De dónde sale | Estado |
|---|---|---|
| Precio de la hora | Documento de Hernán y valores locales | Por confirmar |
| Precios por rubro | Relevamiento local o valores de referencia | Por confirmar |
| Sueldo/plan social | Distribución de ingresos del territorio | Por confirmar |
| Oferta por agente | Fichas del roster | Por confirmar |
| Necesidades | Entrevistas o hipótesis del equipo | Por confirmar |
| Diversidad de rubros | Composición real de ferias y oficios | Por confirmar |
| Plazo de vencimiento | Escenarios E1-E8 | Definido como variable |
| Sanción | Reglamento de membresía | Propuesto |
| Confianza inicial | Supuesto de la simulación | Propuesto |

**Recomendación:** empezar con **unidades abstractas** (1 crédito = 1 hora; efectivo en unidades normalizadas) y no con pesos exactos. Así se evita la falsa precisión y se puede comparar escenarios. La calibración en pesos se hace después, con datos del territorio.

## 9. Glosario canónico

| Término | Definición |
|---|---|
| **Bono** | Nombre para el usuario del crédito de intercambio. |
| **Crédito de intercambio** | Unidad de cuenta gratuita, fungible y caduca que da derecho a recibir bienes o servicios del circuito. |
| **Token de intercambio** | Representación técnica del crédito; no es una criptomoneda. |
| **Lote** | Cantidad de crédito con una fecha de vencimiento propia. |
| **Vencimiento en posesión** | El lote vence si queda quieto; al transferirse, el receptor recibe un lote nuevo. |
| **FIFO** | Se gastan primero los lotes que vencen antes. |
| **Compromiso mínimo** | Ventas que el participante debe aceptar por haber recibido emisión inicial. |
| **Free rider** | Quien recibe créditos y se niega a vender cuando tiene demanda. |
| **DAO** | Organización autónoma descentralizada; en Aldea, la capa de gobierno y la contraparte. |
| **Fiscalía** | Servicio de denuncias, mediación, investigación y sanción. |
| **Ciclo** | Período de inscripción, circulación y evaluación (28 días en la simulación). |
| **Token de recompensa** | Token permanente por superar el compromiso; fuera del MVP. |

## 10. Decisiones abiertas

| Decisión | Opciones | Recomendación | Responsable |
|---|---|---|---|
| Naturaleza del bono | Vale, deuda de la DAO, crédito mutuo, unidad interna | Derecho sobre la producción del circuito con garantía de la DAO | Hernán / Rodrigo |
| Qué pasa al vencer | Se extingue el derecho; el compromiso sigue | Mantener esa separación | Hernán / Rodrigo |
| Reemisión | Una por corrida o por ciclo | Una por corrida en la primera simulación | Rodrigo |
| Fórmula de emisión | Proporcional a la oferta, con mínimo y máximo | Definir fórmula exacta antes de la corrida | Rodrigo |
| Unidad de cuenta | Pesos, horas o abstracta | 1 crédito = 1 hora; efectivo abstracto | Rodrigo |
| Modelo de agente | Heurístico, LLM o híbrido | Heurístico para mock; LLM para diálogo | Rodrigo |
| Umbrales de éxito | Ver sección 7 | Validar con Hernán antes de correr | Hernán / Rodrigo |
| Calibración | Datos reales o supuestos | Supuestos explícitos en la primera corrida | Hernán / Rodrigo |

## 11. Cómo se usa este documento

- Leerlo **antes** de [[01 - Plan de ejecucion|Plan de ejecución]] y [[02 - Requisitos|Requisitos]].
- Si cambia la definición del bono, actualizar [[04 - Arquitectura tecnica|Arquitectura técnica]] y [[02 - Requisitos|Requisitos]].
- Si cambia lo que queremos probar, actualizar [[03 - Diseno experimental|Diseño experimental]].
- Si cambia el modelo de agente, actualizar [[05 - Prompts y perfiles|Prompts y perfiles]].
- Registrar las decisiones en el vault y en el repositorio `aldea-simulator`.

## Enlaces

- [[Proyecto - Simulacion agentica|Proyecto — Simulación agéntica]]
- [[01 - Plan de ejecucion|Plan de ejecución]]
- [[02 - Requisitos|Requisitos]]
- [[03 - Diseno experimental|Diseño experimental]]
- [[04 - Arquitectura tecnica|Arquitectura técnica]]
- [[05 - Prompts y perfiles|Prompts y perfiles]]
- [[06 - Recursos y presupuesto|Recursos y presupuesto]]
- [[07 - Checklist de ejecucion|Checklist de ejecución]]
- [[08 - Evaluacion ADK|Evaluación ADK]]
- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
- [[10 - Modelo Economico y Tokenomia/Mecanismo - Precios y valor hora|Mecanismo — Precios y valor hora]]
