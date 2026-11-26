---
tipo: documento
estado: propuesta
area: economia
version: 0.1
actualizado: 2026-11-20
---

# Propuestas alternativas — Bono Aldea

> [!info] Qué es este documento
> Ocho propuestas que **no aparecieron en la llamada** y que intentan resolver los puntos débiles de las once alternativas originales sin salirse de la filosofía de Aldea. Son hipótesis de diseño para la simulación y para discutir con Hernán. **No son decisiones tomadas.**

## El filtro: los cinco tests de Aldea

Cada propuesta se evalúa contra estos cinco criterios. Si falla uno, se descarta o se rediseña.

| # | Test | Pregunta |
|---|---|---|
| 1 | **Persona** | ¿Le mejora la vida a quien hoy no tiene dinero ni demanda para su trabajo? |
| 2 | **Economía real** | ¿Pone primero los bienes, servicios y oficios, y después la tecnología? |
| 3 | **Naturaleza del crédito** | ¿Sigue siendo gratuito, caduco y no convertible a pesos? |
| 4 | **Obligación** | ¿La obligación de entregar sobrevive al crédito y la comunidad es la contraparte? |
| 5 | **Simplicidad** | ¿Se puede probar sin dinero real, sin token de recompensa y sin blockchain? |

## Mapa de propuestas

| # | Propuesta | Resuelve | Factibilidad | Fase |
|---|---|---|---|---|
| P1 | Crédito semilla con compromiso de oferta | Inclusión sin inflación | Alta | Simulación / MVP |
| P2 | Vencimiento progresivo por saldo | Concentración | Alta | Simulación / MVP |
| P3 | Vale de necesidad básica | Gasto en comida | Media | Fase 2 |
| P4 | Fondo mutuo de garantía | Incumplimiento | Alta | Simulación / MVP |
| P5 | Reputación no monetaria con cupos | Sanción sin «Veraz» | Alta | Simulación / MVP |
| P6 | Banco de horas de cuidado | Trabajo invisible | Media | Fase 2 |
| P7 | Crédito de capital de trabajo en especie | Falta de insumos | Media | Fase 2 |
| P8 | Federación de circuitos | Escala sin moneda global | Baja | Largo plazo |

---

## P1 — Crédito semilla con compromiso de oferta

**Problema que resuelve**: el ingreso básico mensual inflaciona y es insostenible; pero sin algo, el que no tiene nada no puede entrar.

**Cómo funciona**

1. El nuevo participante recibe una **semilla única** (ejemplo: 5.000–10.000 ARS equivalentes) al registrarse.
2. Firma un **compromiso de oferta diferido**: se compromete a publicar X horas de algo dentro de N días.
3. La semilla vence con el plazo normal `T`.
4. Si cumple el compromiso, queda habilitado para emitir contra su oferta.
5. Si no cumple, no renueva la semilla y su techo de emisión baja.

**Por qué sigue la filosofía**

| Test | Cumple | Cómo |
|---|---|---|
| 1. Persona | Sí | Incluye al que no tiene nada que ofrecer hoy |
| 2. Economía real | Sí | La semilla se gasta en bienes y servicios del circuito |
| 3. Crédito | Sí | Es gratuito, caduco y no convertible |
| 4. Obligación | Sí | El compromiso de oferta sobrevive a la semilla |
| 5. Simplicidad | Sí | No necesita blockchain ni token |

**Riesgo principal**: el que no puede ofrecer nada (mayores, discapacidad) queda afuera. **Mitigación**: una **tranche solidaria** fondeada por el fondo de garantía, un sponsor o el municipio, sin compromiso de oferta.

**Qué probar**: porcentaje de semillas que se convierten en ofertas reales; gasto en necesidades básicas; default.

---

## P2 — Vencimiento progresivo por saldo

**Problema que resuelve**: el vencimiento parejo castiga al que guarda poco para una compra grande y no presiona al que acumula mucho.

**Cómo funciona**

1. Hasta un umbral (ejemplo: 20.000 ARS eq.), el crédito vence en **30 días**.
2. Por encima del umbral, el excedente vence en **7 días**.
3. El reloj corre por tramo; el usuario ve un solo saldo y un solo semáforo.
4. La regla se comunica como «el que acumula, corre más rápido».

**Por qué sigue la filosofía**

| Test | Cumple | Cómo |
|---|---|---|
| 1. Persona | Sí | Protege al que tiene poco |
| 2. Economía real | Sí | Empuja a circular, no a atesorar |
| 3. Crédito | Sí | Sigue siendo caduco y gratuito |
| 4. Obligación | Sí | No toca la obligación |
| 5. Simplicidad | Parcial | Es más complejo de explicar que un plazo único |

**Riesgo principal**: gaming con múltiples cuentas para evitar el tramo alto. **Mitigación**: identidad verificada para el techo, límite por persona.

**Qué probar**: Gini de saldos; velocidad por quintil; percepción de justicia.

---

## P3 — Vale de necesidad básica

**Problema que resuelve**: la objeción de Rodrigo. Si no tenés dinero, no vas a gastar tu tiempo en cosas que no te alimentan. Un crédito libre puede terminar en bijouterie mientras falta comida.

**Cómo funciona**

1. Una parte de la emisión (ejemplo: 30%) se entrega como **vale de necesidad básica**.
2. El vale se canjea solo en categorías esenciales: alimentos, salud, arreglos, útiles, higiene.
3. El resto de los créditos es de uso libre.
4. Variante suave: si gastás en categorías esenciales, el plazo se renueva 15 días.

**Por qué sigue la filosofía**

| Test | Cumple | Cómo |
|---|---|---|
| 1. Persona | Sí | Prioriza comida y salud |
| 2. Economía real | Sí | Ancla el circuito en necesidades concretas |
| 3. Crédito | Sí | No es convertible; sigue venciendo |
| 4. Obligación | Sí | No cambia la obligación |
| 5. Simplicidad | Parcial | Fragmenta la liquidez y requiere categorías |

**Riesgo principal**: menos liquidez para el productor que quiere comprar insumos no esenciales. **Mitigación**: porcentaje acotado y canje progresivo.

**Qué probar**: proporción de gasto esencial; retención de los más pobres; liquidez del circuito.

---

## P4 — Fondo mutuo de garantía

**Problema que resuelve**: si alguien no entrega, la DAO puede expulsarlo, pero la víctima pierde. Sin resarcimiento, la confianza se cae.

**Cómo funciona**

1. Un porcentaje de cada intercambio (ejemplo: 2–3%) se aporta en créditos a un **fondo mutuo**.
2. El fondo compensa al damnificado por incumplimiento verificado, hasta un tope.
3. También financia la mediación y el arbitraje.
4. La asamblea publica el balance y decide el uso del excedente.

**Por qué sigue la filosofía**

| Test | Cumple | Cómo |
|---|---|---|
| 1. Persona | Sí | Protege al que entrega y no cobra |
| 2. Economía real | Sí | Es un seguro mutual, no un producto financiero |
| 3. Crédito | Sí | El fondo está en créditos, no en pesos |
| 4. Obligación | Sí | Refuerza el cumplimiento |
| 5. Simplicidad | Sí | Se implementa con una cuenta y una regla |

**Riesgo principal**: colusión para vaciar el fondo. **Mitigación**: verificación, topes, auditoría y reputación.

**Qué probar**: solvencia con default del 5–10%; fraude; costo de verificación.

---

## P5 — Reputación no monetaria con cupos

**Problema que resuelve**: la única sanción disponible es excluir, y eso se parece demasiado a un «Veraz». Además, un token de recompensa traería especulación.

**Cómo funciona**

1. La reputación es **no transferible y no monetizable**: historial, insignias, niveles.
2. La reputación no cambia el saldo: cambia los **cupos**.
3. Más reputación = más techo de emisión, prioridad en el catálogo, acceso al fondo de garantía.
4. Sanción = menos cupo, no menos créditos.

**Por qué sigue la filosofía**

| Test | Cumple | Cómo |
|---|---|---|
| 1. Persona | Sí | No le quita el pan al que se equivocó |
| 2. Economía real | Sí | Premia cumplir, no especular |
| 3. Crédito | Sí | No crea una segunda moneda |
| 4. Obligación | Sí | Refuerza el cumplimiento |
| 5. Simplicidad | Sí | Es un contador y una regla de cupos |

**Riesgo principal**: subjetividad y datos personales. **Mitigación**: criterios públicos, derecho a reparación, datos mínimos.

**Qué probar**: correlación entre cupo y cumplimiento; reincidencia; percepción de justicia.

---

## P6 — Banco de horas de cuidado

**Problema que resuelve**: el circuito valora solo lo que el mercado ya valora. El cuidado de niños, mayores y tareas comunitarias no tiene demanda y suele recaer en mujeres.

**Cómo funciona**

1. Un subcircuito de **banco de horas**: 1 hora = 1 crédito, sin importar la tarea.
2. Se ofrecen horas de cuidado, acompañamiento, trámites, apoyo escolar, tareas comunitarias.
3. Un **pool de cuidado** fondeado por el fondo de garantía o la semilla paga las primeras horas.
4. Los proveedores de comida aceptan esos créditos porque también necesitan cuidado.

**Por qué sigue la filosofía**

| Test | Cumple | Cómo |
|---|---|---|
| 1. Persona | Sí | Incluye a quien no tiene oficio «de mercado» |
| 2. Economía real | Sí | Valoriza trabajo real e invisible |
| 3. Crédito | Sí | Misma unidad, mismo vencimiento |
| 4. Obligación | Sí | La hora se debe igual que un producto |
| 5. Simplicidad | Parcial | Requiere un pool y una categoría nueva |

**Riesgo principal**: el cuidado no produce comida; el circuito se desbalancea. **Mitigación**: mezclar con ofertas productivas y fondear el pool.

**Qué probar**: oferta y demanda de cuidado; participación de mujeres y mayores; retención.

---

## P7 — Crédito de capital de trabajo en especie

**Problema que resuelve**: un productor no puede ofrecer si le faltan insumos (harina, tela, herramientas). El circuito le da demanda, pero no insumos.

**Cómo funciona**

1. La DAO o un **pool de productores** adelanta créditos para comprar insumos **dentro del circuito**.
2. El productor se compromete a entregar el producto terminado.
3. La devolución es en producto, no en créditos.
4. El pool rota el capital y cobra un pequeño recargo en créditos para sostener el fondo.

**Por qué sigue la filosofía**

| Test | Cumple | Cómo |
|---|---|---|
| 1. Persona | Sí | Permite producir a quien no tiene capital |
| 2. Economía real | Sí | Fortalece cadenas productivas locales |
| 3. Crédito | Sí | No hay dinero; el capital es en créditos |
| 4. Obligación | Sí | El compromiso es entregar producto |
| 5. Simplicidad | Parcial | Requiere un pool y gestión de riesgo |

**Riesgo principal**: default del productor y concentración del pool. **Mitigación**: topes, garantía, diversificación.

**Qué probar**: aumento de ofertas productivas; default; efecto multiplicador en la cadena.

---

## P8 — Federación de circuitos con cámara de compensación

**Problema que resuelve**: escalar un solo circuito diluye la confianza. Hernán dice «no escalar, cubrir demanda». La respuesta no es una moneda global, sino varios circuitos que se reconocen.

**Cómo funciona**

1. Cada barrio o ciudad tiene su **propia DAO y su propio crédito**.
2. Los créditos **no viajan** entre circuitos.
3. Las **obligaciones** sí: una cámara de compensación registra quién debe qué a quién entre circuitos.
4. El tipo de cambio se calcula con un índice de precios local, no con especulación.

**Por qué sigue la filosofía**

| Test | Cumple | Cómo |
|---|---|---|
| 1. Persona | Sí | Cada circuito responde a su territorio |
| 2. Economía real | Sí | No hay moneda global ni activo especulativo |
| 3. Crédito | Sí | Cada crédito es local y caduco |
| 4. Obligación | Sí | La obligación es lo que circula |
| 5. Simplicidad | No | Es un diseño de largo plazo |

**Riesgo principal**: gobernanza compleja y disputas de tipo de cambio. **Mitigación**: no implementar hasta que un circuito funcione solo.

**Qué probar**: simulación de dos circuitos con precios distintos; costo de compensación; conflictos.

---

## Matriz de prioridad

| Prioridad | Propuestas | Por qué |
|---|---|---|
| **Probar en la simulación ahora** | P1, P2, P4, P5 | Se modelan con variables y no requieren infraestructura |
| **Diseñar para Fase 2** | P3, P6, P7 | Requieren categorías, pool o acuerdos con productores |
| **Norte de largo plazo** | P8 | Depende de que un circuito funcione solo |

## Qué probar primero

| # | Hipótesis | Variable | Métrica |
|---|---|---|---|
| 1 | La semilla única incluye sin inflar | Monto y compromiso | Conversión a oferta; inflación |
| 2 | El vencimiento progresivo reduce la concentración | Umbral y plazos | Gini; velocidad |
| 3 | El fondo de garantía sostiene la confianza | Aporte y tope | Solvencia; default |
| 4 | La reputación con cupos sanciona sin expulsar | Criterios | Reincidencia; retención |

## Relación con las alternativas originales

| Propuesta | Reemplaza o mejora | Alternativa original |
|---|---|---|
| P1 | Reemplaza el UBI mensual | Alt 10 — Ingreso básico |
| P2 | Mejora la regla de caducidad | Alt 04 — Vencimiento en posesión |
| P3 | Complementa el crédito | Alt 04 / Alt 07 |
| P4 | Complementa la contraparte | Alt 09 — Deuda con la DAO |
| P5 | Reemplaza el token de recompensa | Alt 08 — Token de recompensa |
| P6 | Amplía el catálogo | Alt 07 — Plataforma privada |
| P7 | Complementa la producción | Alt 03 / Alt 06 |
| P8 | Extiende el modelo | Alt 07 — Plataforma privada |

## Preguntas abiertas

1. ¿Cuál de las ocho propuestas tiene más chances de sobrevivir a la simulación?
2. ¿P1 y P10 (semilla) se financian con el mismo fondo que P4 (garantía) o con fondos separados?
3. ¿P2 es explicable en una frase? Si no, ¿vale la complejidad?
4. ¿P3 fragmenta demasiado la liquidez para un piloto de 200 personas?
5. ¿P5 crea un «Veraz» con otro nombre?
6. ¿P6 y P7 requieren un pool que la DAO todavía no puede administrar?
7. ¿P8 es una distracción antes de validar un solo circuito?

## Enlaces

- [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Indice - Alternativas de bono|Índice — Alternativas de bono]]
- [[10 - Modelo Economico y Tokenomia/Modelo - Creditos de intercambio|Modelo — Créditos de intercambio]]
- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
- [[08 - Proyectos/Activos/Proyecto - Simulacion agentica/Proyecto - Simulacion agentica|Proyecto — Simulación agéntica]]
- [[04 - Reuniones/2026/11-Noviembre/2026-11-20 - Llamada con Hernan - Transcripcion|Transcripción de la llamada]]
