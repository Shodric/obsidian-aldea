---
tipo: documento
estado: historico
area: archivo
fuente: "Aldea_Pitch_Empresarial_v2_sin_recompensa.docx"
actualizado: 2026-11-20
---

> [!info] Copia de trabajo
> Extraído automáticamente del documento original `Aldea_Pitch_Empresarial_v2_sin_recompensa.docx`. El original está en `16 - Archivo/2026/Aldea_Pitch_Empresarial_v2_sin_recompensa.docx` y no se edita. Esta copia sirve para buscar y enlazar desde Obsidian.

**ALDEA**

*Plataforma de trueque con créditos gratuitos y de caducidad individual, orientada a emprendedores artesanos y trabajadores de oficios.*

Resumen ejecutivo

Aldea es una aplicación móvil que permite a pequeños emprendedores, artesanos y trabajadores de oficios intercambiar bienes y servicios sin necesidad de dinero. Los participantes se agrupan por zona geográfica y operan con tokens de intercambio, que se otorgan gratuitamente al inscribirse en proporción a la oferta que cada uno declara. Cada token tiene su propio plazo de caducidad desde el momento en que se recibe: no puede quedarse quieto, tiene que circular. El resultado es un mercado local dinámico, sin dependencia del dinero en efectivo. El proyecto adapta un modelo de moneda social pensado originalmente para un municipio y lo traslada a una plataforma privada con gobernanza automática.

El problema

- Los pequeños emprendedores y artesanos suelen tener capacidad ociosa (tiempo, stock, habilidades) que no se traduce en ingresos por falta de demanda en efectivo.

- El acceso al crédito formal es limitado o costoso para este segmento, lo que restringe su capacidad de sostenerse en períodos de baja liquidez.

- Las redes de trueque informales (grupos de mensajería, ferias barriales) son desorganizadas, no escalan y carecen de mecanismos de confianza.

La solución

Una app móvil donde cada usuario declara qué bienes o servicios ofrece y recibe gratuitamente un saldo inicial de tokens de intercambio. Con ellos compra bienes o servicios de otros usuarios de su zona. La diferencia central del modelo es la caducidad individual: cada token que un prosumidor recibe, ya sea en la emisión inicial o como pago por una venta, tiene un tiempo limitado para ser gastado. Si lo usa, circula hacia el siguiente participante. Si lo deja quieto, se vence solo ese token. Así se premia el movimiento y se evita el atesoramiento, sin que todos los usuarios pierdan sus tokens en una misma fecha de cierre.

Cómo funciona

1.  El usuario se registra, elige su zona (barrio o localidad) y publica su oferta de bienes y servicios, con moderación del administrador.

2.  Recibe gratuitamente tokens de intercambio, proporcionales a la oferta declarada. Esa cantidad queda como su compromiso mínimo de venta.

3.  Compra con tokens a otros participantes de su zona; el pago se hace en el momento de aceptar el trueque.

4.  Cada token recibido por una venta arranca su propio reloj de caducidad. Si no se gasta a tiempo, se pierde.

5.  Un algoritmo automático registra la reputación de cada usuario y aplica sanciones cuando corresponde.

El token de intercambio

|  |  |
|----|----|
| **Característica** | **Definición** |
| Cómo se obtiene | Gratis al inscribirse, proporcional a la oferta declarada, y por cada venta realizada |
| Caducidad | Individual: cada token vence si permanece sin gastar durante su plazo |
| Función | Unidad de intercambio; 1 crédito = X horas de trabajo |
| Valor externo | Ninguno: no cotiza ni se convierte a moneda de curso legal |
| Pago | Directo e inmediato al aceptar el trueque; el pago es la confirmación de recepción |

Riesgo principal y mitigación

**Riesgo identificado:** un usuario se inscribe, recibe tokens gratuitos y los usa solo para consumir, pero se niega a aceptar tokens cuando otros quieren comprarle, escudándose en que los tokens vencen igual. Es el free-rider que nunca actúa como vendedor real y vacía al sistema de oferta.

**Mecanismos de mitigación:**

- Compromiso mínimo obligatorio: cada usuario debe aceptar tokens por un monto equivalente a lo que recibió al inscribirse.

- Sanción solo a quien se niega a vender: el rechazo explícito cuenta de inmediato como negativa; el silencio recibe un recordatorio antes de computarse como rechazo.

- Sin sanción por falta de demanda: quien no recibió ninguna solicitud de compra no tuvo oportunidad de cumplir, y no se le penaliza.

- Consecuencia automática: suspensión para participar del ciclo siguiente, con reducción de reputación.

Mercado objetivo

Pequeños emprendedores, artesanos y trabajadores de oficios (gasistas, electricistas, diseñadores, costureras, gastronómicos, entre otros) que cuentan con capacidad de producción u oferta de servicios pero enfrentan restricciones de demanda en efectivo, típicamente en economías locales o barriales.

Próximos pasos

1.  Validar el modelo con un grupo piloto cerrado (50 a 100 usuarios) en una zona geográfica acotada.

2.  Definir el plazo de caducidad de los tokens a partir de los resultados del piloto.

3.  Desarrollar la app móvil (React Native) con backend de gestión de tokens, caducidad individual y reputación.

4.  Escalar progresivamente a nuevas zonas y rubros.
