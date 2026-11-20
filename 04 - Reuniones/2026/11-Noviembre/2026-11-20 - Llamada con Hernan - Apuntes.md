---
tipo: apuntes
estado: activo
fecha: 2026-11-20
fecha_llamada: por confirmar
area: direccion
participantes: Hernan; Rodrigo
reunion: "[[04 - Reuniones/2026/11-Noviembre/2026-11-20 - Llamada con Hernan - Transcripcion]]"
actualizado: 2026-11-20
---

# Apuntes — Llamada con Hernán

> [!summary] En una frase
> **Aldea** es una red de intercambio local donde cada persona emite créditos contra lo que ofrece (productos, servicios, oficios, cosas usadas) y esos créditos **vencen mientras están quietos**, para que circulen. La tecnología (blockchain + smart contracts) es una capa de garantía y trazabilidad, no el fin.

## Ficha de la reunión

| Campo | Dato |
|---|---|
| Fecha de la llamada | Por confirmar |
| Registro | 2026-11-20 |
| Participantes | Hernán (impulsor), Rodrigo (tecnología y datos) |
| Duración | Por confirmar |
| Modalidad | Llamada / videollamada |
| Transcripción | [[04 - Reuniones/2026/11-Noviembre/2026-11-20 - Llamada con Hernan - Transcripcion|Transcripción editada]] |
| Fuente cruda | [[16 - Archivo/2026/transcripcion_original.txt|Transcripción automática]] |

## Qué es Aldea

Aldea es un **circuito de trueque con créditos locales** para personas que tienen capacidad ociosa y les falta dinero, pero no encuentran demanda para su trabajo. No es una moneda paralela ni una criptomoneda: es un **bono de trueque dinámico**, gratuito en su emisión y caduco mientras está en posesión.

El objetivo no es reemplazar la economía formal sino **complementarla**: la persona mantiene su sueldo o changa formal para vivienda y servicios, y resuelve otras necesidades (comida, arreglos, clases, ropa, muebles) con el circuito de intercambio.

## Cómo funciona — versión de trabajo

1. **Alta**: la persona se registra con un seudónimo y un contacto. Para el MVP no se pide DNI; la identidad verificada se reserva para sanciones y contratos.
2. **Oferta**: publica qué ofrece (horas de un oficio, productos, clases, cosas usadas) y el sistema le asigna un valor en créditos según una escala de valor hora y/o una cotización de referencia.
3. **Emisión**: recibe créditos **contra esa oferta**. No puede emitir si no ofrece algo. Hay un piso y un techo por participante.
4. **Catálogo**: ve las ofertas de la zona y compra con créditos. Los precios están puestos de antemano y no se regatean.
5. **Intercambio**: al comprar, los créditos pasan al vendedor. El crédito que estaba quieto empieza a vencer; al cambiar de manos, **se renueva el plazo** para el nuevo tenedor.
6. **Cumplimiento**: el vendedor queda obligado a entregar lo que ofreció. La obligación **no vence** aunque el crédito venza. La DAO (o la asociación local) actúa como contraparte y garante.
7. **Cierre de ciclo**: cada ciclo (por ejemplo, 4 semanas) abre, circula y cierra. Para seguir participando hay que volver a inscribirse y ofertar.

## Los cinco hallazgos de la llamada

### 1. El problema no es la falta de dinero: es la falta de demanda
Hernán lo dice explícitamente: el sistema está pensado “exclusivamente para quien no tiene fuerza de trabajo y no está encontrando demanda”. No hay dinero, entonces no hay demanda de trabajo. Aldea **crea demanda** donde el mercado formal no la genera.

### 2. El vencimiento es el motor, no un castigo
El crédito vence **en posesión**, no de golpe al final del ciclo. Eso resuelve tres cosas:
- acelera la circulación (“lo voy a querer usar cuanto antes”);
- evita la especulación y el atesoramiento;
- elimina la necesidad de sanciones masivas por rechazo, porque el incentivo ya está en gastar.

Hernán lo compara con los **UTXO de Bitcoin**: al partir un crédito de 10 en 5 + 5, cada UTXO nuevo renueva su plazo. No es un NFT: es **fungible y divisible**, y por eso el encuadre legal cambia.

### 3. La obligación no caduca; el crédito sí
El compromiso de entregar el producto o servicio **sobrevive** al vencimiento del crédito. La deuda circula: quien compra asume la obligación, y puede transferirla a otro. Hernán lo acepta como evolución del modelo (“me gusta”), aunque no lo había pensado así.

### 4. La DAO como contraparte resuelve el “¿quién me obliga?”
En el modelo original, el participante quedaba en deuda con otro participante. Rodrigo propone que la deuda sea **con la organización/DAO**: la DAO emite el crédito al vendedor, el comprador queda en deuda con la DAO, y la DAO puede reclamar, sancionar o mediar. Es el puente entre el smart contract y el mundo legal.

### 5. El MVP debe ser solo el crédito de intercambio
El **token de recompensa** (permanente, fungible, potencialmente negociable) queda para una fase posterior: requiere CNV, patrimonio, habilitaciones y un diseño de emisión que todavía no existe. El MVP se concentra en el crédito de intercambio, que no cruza dinero y es más fácil de encuadrar.

## Propuestas vs. decisiones

> [!warning] Regla del vault
> En esta llamada **no se tomó ninguna decisión formal**. Todo lo que sigue es **propuesta** o **hipótesis de trabajo**, a validar con Hernán, con legal y con el piloto.

| # | Propuesta | Estado | Nota |
|---|---|---|---|
| 1 | Lanzar el MVP solo con crédito de intercambio, sin token de recompensa | Propuesta | Hernán lo sugiere; falta validación legal |
| 2 | Crédito con vencimiento en posesión y renovación al transferir | Propuesta | Núcleo del modelo; requiere diseño técnico |
| 3 | La DAO/asociación local como contraparte de la obligación | Propuesta | Idea de Rodrigo; Hernán la acepta como evolución |
| 4 | Precios fijos ex ante, sin regateo | Propuesta | Para evitar “bono blue” y especulación |
| 5 | Piso y techo de emisión por participante (ej. 20.000–100.000 ARS) | Propuesta | Cifras de ejemplo; a estudiar |
| 6 | Sanciones: devaluación del crédito, exclusión y reentrada pagando | Propuesta | A validar con legal |
| 7 | Piloto de 100–300 usuarios en una zona densa (conurbano) antes que Azul | Propuesta | Hernán ve Azul como mercado deprimido y homogéneo |
| 8 | Simulación con agentes de IA antes del MVP | Propuesta | Presupuesto inicial USD 10–30 |
| 9 | Ingreso básico mínimo en créditos (ej. 10.000 ARS/mes) | Propuesta | Para incluir a quienes no tienen nada que ofrecer |
| 10 | Token de recompensa respaldado en tierra/equity | Idea exploratoria | Muy preliminar; alto riesgo regulatorio |

## Tareas detectadas

| # | Tarea | Responsable | Fecha objetivo | Estado |
|---|---|---|---|---|
| 1 | Enviar a Rodrigo los archivos: modelo original de moneda social (2016–2024), pitches de Aldea (con y sin token de recompensa) y simulador JSX | Hernán | Por confirmar | Pendiente |
| 2 | Cargar y ordenar los archivos recibidos en `16 - Archivo/2026/` | Rodrigo | Por confirmar | Pendiente |
| 3 | Revisar el simulador JSX y verificar que sea seguro ejecutarlo | Rodrigo | Por confirmar | Pendiente |
| 4 | Diseñar la simulación agéntica: perfiles, parámetros, métricas y costo | Rodrigo | Por confirmar | Pendiente |
| 5 | Correr una primera simulación con 10 agentes y documentar resultados | Rodrigo | Por confirmar | Pendiente |
| 6 | Definir el territorio del piloto y los contactos locales | Hernán + Rodrigo | Por confirmar | Pendiente |
| 7 | Validar el encuadre legal del crédito de intercambio (CNV, datos, contratos) | Rodrigo + abogada | Por confirmar | Pendiente |
| 8 | Escribir el documento ejecutivo de Aldea a partir de la transcripción y los archivos | Rodrigo | 2026-11-27 | En curso |
| 9 | Armar el mapa de aliados: municipio, ferias, cooperativas, universidades, web3 | Rodrigo | Por confirmar | Pendiente |
| 10 | Definir el alcance funcional del MVP y sus no-alcances | Rodrigo + Hernán | Por confirmar | Pendiente |

## Preguntas abiertas

1. **¿Cuál es la fecha exacta de la llamada y la duración?** (para el registro)
2. **¿Quién es el titular legal de Aldea?** ¿Hernán, una asociación, una cooperativa, una fundación, una sociedad?
3. **¿La DAO tiene personalidad jurídica?** En Argentina no hay figura específica; hay que elegir un vehículo legal (asociación civil, cooperativa, fundación, SAS) y envolver el protocolo.
4. **¿El crédito de intercambio es un valor negociable para la CNV?** La hipótesis es que no, porque no hay dinero ni expectativa de rentabilidad, pero hay que dictaminarlo.
5. **¿Cómo se articula con el municipio?** ¿Convenio, programa, ordenanza, espacio de mediación, beneficios fiscales?
6. **¿Cómo se resuelve el incumplimiento?** ¿Solo exclusión, devaluación y reentrada pagando? ¿Hay arbitraje? ¿Qué tribunal?
7. **¿Cómo se protege la identidad y los datos?** Seudónimo en el catálogo, identidad verificada para sanciones, datos mínimos.
8. **¿Cuál es el primer territorio?** Hernán propone conurbano; Azul queda como segundo paso.
9. **¿Quién financia la Fase 0 y la Fase 1?** Presupuesto inicial bajo (simulación USD 10–30), pero legal y piloto requieren financiamiento.
10. **¿Qué pasa con el token de recompensa?** ¿Se descarta, se deja para Fase 3 o se diseña como token de gobernanza sin valor económico?

## Frases para conservar

> “La idea mía todavía giraba en torno a la emisión de un bono físico. Mejor que tengan vencimiento: se emiten, se entregan y se vencen.”

> “El bono se va a vencer en posesión, no se va a vencer en total en todo el circuito.”

> “Es un mecanismo desarrollado exclusivamente para quien no tiene fuerza de trabajo y no está encontrando demanda. No hay dinero, entonces no hay demanda de trabajo. Es un sistema para crear demanda.”

> “El compromiso no caduca; caduca la moneda.”

> “La gente va a tener el bono blue. Le va a dar su propio valor.”

> “Yo buscaría un sector con más dinámica, más en el conurbano. Hay más economía social.”

> “La idea no es que solamente intercambien, sino que esté vivo, que intercambien ideas, pensamientos.”

## Próximos pasos

1. Hernán envía los archivos.
2. Rodrigo procesa los archivos, arma el documento ejecutivo y el modelo del circuito.
3. Rodrigo diseña y corre la simulación agéntica.
4. Reunión de validación con Hernán: revisar el modelo, el territorio y el encuadre legal.
5. Definir el alcance del MVP y el presupuesto de la Fase 0.

## Enlaces

- [[04 - Reuniones/2026/11-Noviembre/2026-11-20 - Llamada con Hernan - Transcripcion|Transcripción editada]]
- [[03 - Direccion y Estrategia/2026-11 - Documento Ejecutivo Aldea|Documento Ejecutivo Aldea]]
- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
- [[08 - Proyectos/Activos/Proyecto - Simulacion agentica/Proyecto - Simulacion agentica|Proyecto — Simulación agéntica]]
- [[00 - Centro de Mando/Kanban - Pendientes del Vault|Kanban de pendientes]]
