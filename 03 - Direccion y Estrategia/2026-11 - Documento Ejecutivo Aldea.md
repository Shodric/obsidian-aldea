---
tipo: documento
estado: borrador
area: direccion
fecha: 2026-11
version: 0.1
autor: Rodrigo
actualizado: 2026-11-20
---

# Aldea — Documento Ejecutivo

> [!info] Estado del documento
> Versión **0.1**, elaborada a partir de la llamada con Hernán registrada el 2026-11-20. No es un documento legal ni una oferta de inversión. Las cifras son órdenes de magnitud a validar. Las propuestas no son decisiones aprobadas.

## Ficha

| Campo | Dato |
|---|---|
| Nombre | Aldea |
| Qué es | Red local de intercambio con créditos gratuitos que vencen mientras están quietos |
| Para quién | Personas con oficios, productos o capacidad ociosa que no encuentran demanda porque no hay dinero |
| Dónde | Argentina. Piloto a definir: conurbano bonaerense (preferido) o Azul |
| Etapa | Diseño y validación. Sin MVP construido |
| Impulsor | Hernán (Azul, Buenos Aires) |
| Tecnología y datos | Rodrigo |
| Modelo | Economía complementaria, no moneda paralela |
| Tecnología | Blockchain con smart contracts y créditos tipo UTXO; reemplazable por una base de datos si no aporta valor |

## Síntesis

Aldea es una red de intercambio entre vecinos donde cada persona **emite créditos contra lo que ofrece**: horas de un oficio, productos artesanales, clases, ropa, muebles usados. Los créditos son **gratuitos** —no se compran con dinero— y **vencen mientras están quietos**. Si no los usás, los perdés; si los transferís, el que los recibe gana un plazo nuevo. Eso hace que la rueda gire.

No es una criptomoneda ni una moneda paralela. Es un **bono de trueque dinámico**: una unidad de cuenta que representa el compromiso de entregar algo. La tecnología sirve para que ese compromiso sea verificable y para que nadie pueda emitir de la nada.

La hipótesis de fondo es simple: **hay gente con capacidad de trabajo y sin demanda, porque no hay dinero que la exprese**. Aldea crea un canal para que esa capacidad se encuentre con necesidades concretas —comida, arreglos, clases, ropa— sin pasar por el peso.

## El problema

En los barrios populares y en la economía informal conviven tres problemas que se refuerzan:

1. **Falta de dinero**: el ingreso no alcanza para cubrir necesidades básicas, y el crédito formal es caro o inexistente.
2. **Falta de demanda**: quien tiene un oficio no encuentra clientes porque nadie tiene pesos para pagarle. No es que no sepa hacer su trabajo: es que el mercado no lo convoca.
3. **Falta de confianza**: los acuerdos informales se sostienen en la palabra, pero sin garantías ni registro es difícil escalar y resolver conflictos.

Los programas de empleo y los subsidios atacan el primer problema, pero no el segundo. Las ferias y el trueque atacan el segundo, pero no el tercero. Aldea propone una infraestructura que ataca los tres a la vez.

## La propuesta

### Un circuito, no una moneda

Los participantes se registran, publican su oferta y reciben créditos por el valor de esa oferta. Con esos créditos compran lo que otros ofrecen. El crédito no se compra con pesos ni se cambia por pesos dentro del sistema: **solo sirve para intercambiar**.

### El vencimiento como motor

El crédito pierde validez si queda quieto. Al transferirse, el nuevo tenedor recibe un plazo renovado. Esto produce tres efectos:

- **Acelera la circulación**: conviene usarlo antes de que venza.
- **Desalienta la especulación**: no sirve guardarlo ni esperar que suba.
- **Evita el cierre traumático**: no hay que esperar a que venza todo el circuito de golpe.

### La DAO como contraparte

Cuando alguien compra, no queda en deuda con el vendedor: queda en deuda con **la organización**, que emite el crédito y garantiza el cumplimiento. Esa deuda se puede transferir con el crédito. La organización —una DAO con respaldo legal local— puede reclamar, mediar y sancionar.

### La obligación no vence

El crédito vence; el compromiso de entregar lo ofrecido, no. Si alguien compró y no entregó, la organización tiene un registro y puede exigirle. La sanción principal es quedar fuera del circuito; también se evalúan la devaluación del crédito y la reincorporación con un pago.

## Cómo funciona, paso a paso

1. **Alta**: la persona se registra con seudónimo y contacto. Para operar no necesita DNI; para sanciones y contratos, sí se verifica identidad.
2. **Oferta**: publica qué ofrece y el sistema le asigna un valor en créditos según una escala de valor hora y/o una cotización de referencia.
3. **Emisión**: recibe créditos contra esa oferta. Sin oferta no hay emisión. Hay un piso y un techo por participante.
4. **Catálogo**: ve las ofertas de la zona, con precios ya puestos. No se regatea.
5. **Compra**: paga con créditos. El vendedor los recibe y empieza a correr su vencimiento.
6. **Entrega**: el comprador confirma con un código, como en una compra online. Recién ahí se cierra la transacción.
7. **Ciclo**: cada período (por ejemplo, 4 semanas) abre y cierra. Para seguir participando hay que volver a ofertar.

## Qué la hace distinta

| Principio | Qué significa en la práctica |
|---|---|
| **Gratuidad** | Los créditos no se compran. Nadie necesita pesos para entrar. |
| **Caducidad** | El crédito vence en posesión. El incentivo es usar, no acumular. |
| **Respaldo en oferta** | No se puede emitir sin ofrecer algo. El respaldo es trabajo, producto o un bien usado. |
| **Precio ex ante** | El sistema fija el valor antes del intercambio. Se evita el regateo y el “bono blue”. |
| **Economía mixta** | No reemplaza el sueldo ni la economía formal: complementa lo que falta. |
| **Comunidad, no plataforma** | La gobernanza es local. La app es una herramienta, no el proyecto. |

## Componentes

### Económico
- Crédito de intercambio gratuito, fungible y divisible, con vencimiento en posesión.
- Escala de valor hora y tabla de conversión de precios.
- Piso y techo de emisión por participante.
- Ciclos de apertura y cierre.
- Fondo de estabilización y criterios de ajuste (a diseñar).

### Tecnológico
- Registro de usuarios y catálogo geolocalizado.
- Billetera con créditos tipo UTXO y vencimiento programado.
- Smart contracts para emisión, transferencia, partición y renovación.
- Confirmación de entrega con código.
- Panel de administración, reputación y resolución de disputas.

### Gobernanza
- DAO/asociación local con reglas escritas.
- Asamblea de participantes para decisiones de parámetros.
- Comité ejecutivo para operación diaria.
- Arbitraje y mediación con apoyo municipal.

### Legal
- Vehículo jurídico local (asociación civil, cooperativa, fundación o SAS).
- Contrato de membresía y contrato de intercambio.
- Política de datos personales.
- Dictamen sobre encuadre del crédito ante la CNV (hipótesis: no es valor negociable).
- Convenio con el municipio para mediación y validación territorial.

### Territorial
- Socio local con presencia en el barrio.
- Mapa de oferta y demanda.
- Espacios físicos de encuentro y capacitación.
- Articulación con ferias, cooperativas, clubes y organizaciones sociales.

## A quién sirve

| Perfil | Qué aporta | Qué necesita |
|---|---|---|
| **Oficios** (albañil, parquero, plomero, electricista, manicura, peluquería) | Horas de trabajo | Demanda constante y precios claros |
| **Productores caseros** (comida, panificados, conservas) | Productos | Insumos y clientes |
| **Artesanos y economía circular** (ropa, muebles, objetos usados) | Bienes | Visibilidad y rotación |
| **Clases y servicios personales** (guitarra, apoyo escolar, idiomas, entrenamiento) | Conocimiento y tiempo | Alumnos y horarios |
| **Desempleados y subocupados** | Tiempo y capacidad | Un punto de entrada sin dinero |
| **Comercios pequeños** | Excedentes y servicios | Más clientes y fidelización |
| **Municipio** | Territorio, legitimidad y mediación | Indicadores y una política de economía social |

## Hoja de ruta

| Fase | Nombre | Objetivo | Entregable principal | Criterio de salida |
|---|---|---|---|---|
| **0** | Simulación y validación | Probar el modelo antes de construir | Simulación agéntica + documento ejecutivo + dictamen preliminar | El modelo no se bloquea en escenarios adversos |
| **1** | Diseño legal y territorial | Elegir vehículo, territorio y aliados | Estatuto, contratos, convenio, mapa de aliados | Territorio y marco legal definidos |
| **2** | MVP y piloto | Operar con 100–300 usuarios durante 4–8 semanas | App MVP + piloto + reporte | Intercambios concretos y usuarios que repiten |
| **3** | Evaluación y réplica | Medir, ajustar y decidir el token de recompensa | Informe de evaluación + manual de réplica | Decisión fundada sobre escalar o no |

## Gobernanza y confianza

La confianza no se delega al código. Se construye con tres capas:

1. **Reglas escritas**: quién entra, qué puede ofrecer, cómo se fija el precio, qué pasa si no cumple.
2. **Contraparte identificable**: una asociación local con personas responsables, no una DAO anónima.
3. **Resolución de conflictos**: mediación, arbitraje y, en última instancia, contrato exigible.

La DAO aporta transparencia y automatización; la asociación aporta responsabilidad legal y presencia territorial. Las dos son necesarias.

## Marco legal — hipótesis de trabajo

> [!warning] Esto no es asesoramiento legal
> Las siguientes son hipótesis a validar con abogada y, si corresponde, con la CNV.

- **Crédito de intercambio**: al no comprarse con dinero, no prometer rentabilidad y solo servir para intercambiar bienes y servicios, se presume que **no es un valor negociable** bajo la Ley 26.831. Pendiente de dictamen.
- **Token de recompensa**: al ser permanente, fungible y potencialmente negociable, probablemente requiera inscripción y cumplimiento de la normativa de la CNV. **No forma parte del MVP.**
- **Datos personales**: seudónimo en el catálogo, datos mínimos, consentimiento informado y cumplimiento de la Ley 25.326.
- **Contratos**: contrato de membresía con la asociación, términos de uso, política de privacidad y reglamento de sanciones.
- **Vehículo**: asociación civil o cooperativa de trabajo, con o sin personalidad jurídica propia para la DAO. A definir.

## Sustentabilidad y costos

| Ítem | Fase 0 | Fase 1 | Fase 2 |
|---|---|---|---|
| Simulación | USD 10–30 | — | — |
| Legal | — | Por confirmar | Por confirmar |
| Desarrollo MVP | — | — | Por confirmar |
| Operación del piloto | — | — | Por confirmar |
| Comunicación y materiales | Bajo | Medio | Medio |

**Modelo de ingresos (a definir)**: membresía simbólica, aportes de aliados, convenios municipales, servicios de capacitación, financiamiento filantrópico o cooperativo. **No** se prevé cobrar comisión por intercambio en la Fase 2.

## Cómo sumarse

- **Municipios**: convenio de validación territorial, mediación y espacio físico.
- **Cooperativas y mutuales**: base de socios, infraestructura y legitimidad.
- **Universidades**: evaluación, simulación y formación.
- **Organizaciones sociales y ferias**: comunidad y territorio.
- **Desarrolladores y diseñadores**: MVP, identidad y experiencia de usuario.
- **Financiadores**: Fase 0 y Fase 1, con retorno social medible.

## Preguntas frecuentes

**¿Es una moneda?** No. Es un crédito de intercambio que solo sirve dentro de la red y que vence.

**¿Se puede cambiar por pesos?** No dentro del sistema. Fuera del sistema, cada persona decide qué hace, pero el diseño no lo promueve.

**¿Qué pasa si alguien no cumple?** Queda registrado, se le exige la entrega, se le aplican sanciones (exclusión, devaluación del crédito, reincorporación con pago) y, si corresponde, se acude a mediación.

**¿Necesito saber de cripto?** No. La aplicación debe funcionar como una billetera común. La blockchain es invisible para el usuario.

**¿Esto reemplaza mi sueldo?** No. Está pensado para complementar: la vivienda y los servicios se pagan con dinero; el trueque resuelve otros consumos.

**¿Quién manda?** Una asociación local con reglas escritas y una DAO para las decisiones colectivas. No es una plataforma de una sola persona.

## Riesgos principales

- Oferta homogénea y baja densidad de intercambios.
- Incumplimiento y free riders.
- Especulación y precios paralelos.
- Incertidumbre regulatoria.
- Baja adopción y desconfianza.
- Dependencia de Hernán y del territorio.
- Sobreingeniería tecnológica.
- Datos personales e identidad.

El detalle está en [[03 - Direccion y Estrategia/Riesgos/Indice - Riesgos|el registro de riesgos]].

## Referencias

- [[04 - Reuniones/2026/11-Noviembre/2026-11-20 - Llamada con Hernan - Transcripcion|Transcripción de la llamada con Hernán]]
- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
- [[03 - Direccion y Estrategia/Diagnostico - Economia informal y barreras|Diagnóstico — Economía informal y barreras]]
- [[03 - Direccion y Estrategia/Roadmap - Cuatro fases|Roadmap — Cuatro fases]]
- [[03 - Direccion y Estrategia/Referencias - Bibliografia|Bibliografía]]
