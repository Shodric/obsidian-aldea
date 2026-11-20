---
tipo: documento
estado: historico
area: archivo
fuente: "Aldea_Aproximacion_Tecnica_v6_sin_recompensa.docx"
actualizado: 2026-11-20
---

> [!info] Copia de trabajo
> Extraído automáticamente del documento original `Aldea_Aproximacion_Tecnica_v6_sin_recompensa.docx`. El original está en `16 - Archivo/2026/Aldea_Aproximacion_Tecnica_v6_sin_recompensa.docx` y no se edita. Esta copia sirve para buscar y enlazar desde Obsidian.

**ALDEA**

*Aproximación técnica para el desarrollo de la plataforma (v6 — caducidad individual del token de intercambio)*

Basado en el Proyecto Moneda Social (H. Cabrera, 2018–2024), adaptado de un esquema municipal a un proyecto privado con gobernanza algorítmica.

0\. Origen y adaptación del modelo

Aldea retoma la base conceptual del Proyecto Moneda Social: un bono de trueque gratuito, no cotizable en moneda oficial, útil únicamente como bien de cambio (sin función de ahorro) y con caducidad para incentivar su circulación. El proyecto original concebía su implementación desde un municipio, con asambleas comunitarias y un área de Economía Social como garantes del consenso y del control. En la versión privada, ese rol se reemplaza por un algoritmo automático de sanciones y reputación.

|  |  |
|----|----|
| **Elemento del proyecto original** | **Adaptación en Aldea (privado)** |
| Asambleas comunitarias + Área de Economía Social municipal | Algoritmo automático de sanciones y reputación |
| Remito/recibo en papel certificado por un equipo municipal | Confirmación digital de recepción integrada al pago |
| Valor de referencia en tiempo de trabajo (1 bono = X h/t) | Se mantiene: 1 crédito = X horas de trabajo, valor fijo |
| Mínimo y máximo de bonos por compromiso declarado | Se mantiene como parámetro configurable |
| Vencimiento de todos los bonos de una tanda en una misma fecha | Cambia: cada token vence individualmente según el tiempo que permanece sin gastar |
| Implementación a cargo del municipio | Producto privado, con potencial de licenciamiento y escalado propio |

1\. El token de intercambio y su caducidad individual

Aldea trabaja con un único token, de uso interno: gratuito, sin valor en moneda oficial y con caducidad. Se usa para pagar bienes y servicios dentro de la zona del usuario.

|  |  |
|----|----|
| **Aspecto** | **Definición** |
| Función | Medio de pago del trueque; unidad de cuenta (1 crédito = X horas de trabajo) |
| Emisión | Gratuita al inscribirse, proporcional a la oferta declarada, y generada con cada venta (el comprador paga, el vendedor recibe) |
| Caducidad | Individual, por tenencia: cada token vence si permanece sin gastar durante su plazo |
| Valor externo | Ninguno: no cotiza ni se convierte a moneda |

Mecánica de caducidad por tenencia

1.  Cada vez que un prosumidor recibe tokens, ya sea por la emisión inicial o como pago de una venta, se crea un lote con su propia fecha de recepción y su propia fecha de vencimiento (recepción más el plazo vigente).

2.  Al gastar, el sistema descuenta primero los lotes más próximos a vencer (el más antiguo primero), para que el usuario pierda lo menos posible.

3.  Si un lote cumple su plazo sin haberse gastado, vence solo ese lote; el resto del saldo del usuario no se ve afectado.

4.  Al ser transferidos como pago, los tokens se convierten en un lote nuevo para quien los recibe, con su reloj propio.

5.  La app muestra el saldo desglosado por fecha de vencimiento y envía avisos antes de que un lote venza.

**Efecto buscado:** el crédito circula de forma continua y no existe un momento de cierre en el que todos pierdan a la vez. Quien recibe un pago tiene un tiempo acotado para convertirlo en otro intercambio, y el atesoramiento deja de ser posible sin perder valor.

2\. El riesgo central del modelo y su solución

**Riesgo identificado:** un usuario se inscribe, recibe tokens gratuitos y los usa solo para consumir, pero luego se niega a aceptar tokens como pago cuando otros quieren comprarle, escudándose en que esos tokens vencen. Es un free-rider que nunca actúa como vendedor real y vacía al sistema de oferta efectiva.

**Mecanismo de solución: compromiso mínimo obligatorio**

1.  Al inscribirse, el usuario declara su oferta y recibe tokens en proporción a esa declaración.

2.  Ese monto recibido se fija como compromiso mínimo de venta: el usuario debe aceptar tokens, a cambio de su oferta, por al menos esa cantidad.

3.  Mientras no haya cubierto su compromiso, está obligado a aceptar las solicitudes de compra sobre la oferta que publicó.

4.  El sistema notifica el avance del compromiso durante el ciclo.

5.  Si al cierre del ciclo incumplió por negarse a vender, se aplica una sanción automática: suspensión para participar del ciclo siguiente.

Distinción crítica: no cumplir no es lo mismo que negarse a cumplir

La sanción recae exclusivamente sobre quien se niega a vender, no sobre quien no recibió demanda suficiente para cubrir su compromiso. Un usuario que publicó su oferta correctamente pero no tuvo solicitudes de compra no incumplió nada de su parte; sancionarlo sería penalizar mala suerte de mercado, no mala fe.

**Mecanismo de identificación del rechazo**

- El sistema registra cada solicitud de compra recibida sobre una oferta publicada, junto con la respuesta del oferente: aceptada, rechazada explícitamente o sin respuesta.

- Rechazo explícito: cuenta de inmediato como negativa a vender. Con un solo rechazo ya se configura la negativa.

- Silencio: se envía una notificación de recordatorio con un plazo breve adicional. Recién si tras ese recordatorio el usuario sigue sin responder, se computa como rechazo.

- Ausencia de demanda: si el usuario no recibió ninguna solicitud de compra, no se evalúa incumplimiento de su compromiso mínimo.

**Regla de aplicación:** la sanción se activa únicamente cuando existe al menos un rechazo (explícito o por silencio confirmado) sobre solicitudes efectivamente recibidas. La falta de cobertura del compromiso debida solo a falta de demanda no genera sanción.

3\. Zonas y ciclos

La caducidad no depende del cierre del ciclo, pero las zonas y los ciclos se mantienen como marco de organización del sistema.

|  |  |
|----|----|
| **Aspecto** | **Definición** |
| Agrupación | Por zona predefinida (barrio o localidad), por la cercanía necesaria para el traslado de bienes y la prestación de servicios |
| Rol del ciclo | Marco para inscribirse, evaluar el compromiso mínimo y aplicar sanciones. No es el momento en que vencen los tokens |
| Duración del ciclo | Sugerida por el sistema según la cantidad de participantes activos en la zona; ajustable por el administrador |
| Valor de referencia | 1 crédito = X horas de trabajo, valor fijo |
| Traslado y flete | Fuera del sistema de tokens; se acuerda directamente entre las partes |

4\. Pago, entrega y confirmación

- Entrega inmediata: el pago con tokens y la recepción del bien o servicio ocurren de forma simultánea; el acto de pagar es la confirmación de recepción.

- Entrega diferida (el servicio se presta después del pago): la transacción queda pendiente de cumplimiento hasta la fecha acordada. Si no se cumple y se registra reclamo, se aplica sanción (suspensión del ciclo siguiente).

5\. Arquitectura general

App móvil y backend

React Native (Expo) para la app, compilable en iOS y Android mediante EAS. Backend en Supabase (Postgres) o Firebase, con funciones del lado del servidor para el motor de lotes y caducidad, el control del compromiso mínimo y el algoritmo de sanciones y reputación.

Estructura de datos principal

|  |  |
|----|----|
| **Entidad** | **Contenido** |
| Usuarios | Perfil, zona, rubro, reputación, límite de exposición |
| Zonas | Definición geográfica (barrio o localidad) y parámetros del ciclo vigente |
| Ciclos | Zona asociada, inicio y cierre, cantidad de participantes, volumen total, estado |
| Lotes de tokens | Usuario, monto, origen (emisión inicial o venta), fecha de recepción, fecha de vencimiento, estado (vigente, gastado, vencido) |
| Compromisos | Usuario, ciclo, monto recibido al inscribirse, monto cubierto, estado (cumplido, pendiente, incumplido) |
| Ofertas | Bien o servicio, equivalencia en horas, modalidad (inmediata o diferida), estado de moderación |
| Solicitudes de compra | Oferta asociada, comprador, fecha, estado (aceptada, rechazada, sin respuesta, recordatorio enviado, rechazo por silencio confirmado) |
| Transacciones | Comprador, vendedor, oferta, modalidad, lotes utilizados, fecha, estado |
| Reclamos | Transacción diferida asociada, motivo, resolución |

6\. Módulos funcionales

1.  Registro y perfil: alta de usuario, zona, declaración de oferta, cálculo del saldo inicial y del compromiso mínimo.

2.  Gestión de zonas y ciclos: apertura y cierre, duración sugerida según participantes, ajuste manual.

3.  Motor de lotes y caducidad: creación de un lote con cada recepción, gasto del lote más antiguo primero, vencimiento automático de lotes sin gastar y avisos previos.

4.  Control de compromiso mínimo: seguimiento en tiempo real y obligatoriedad de aceptar solicitudes sobre la oferta publicada.

5.  Gestión de solicitudes de compra: registro de cada solicitud y su resolución, como base objetiva para distinguir negativa a vender de falta de demanda.

6.  Catálogo: publicación de ofertas con modalidad inmediata o diferida y moderación previa.

7.  Transacciones: pago directo con confirmación simultánea o marcado de pendiente en las diferidas.

8.  Algoritmo de sanciones y reputación: límites y suspensiones automáticas.

9.  Notificaciones push: lote próximo a vencer, avance del compromiso, transacción pendiente, sanción aplicada.

7\. Estimación de esfuerzo (orientativa)

|  |  |
|----|----|
| **Etapa** | **Duración estimada** |
| MVP funcional (registro, zonas y ciclos, lotes con caducidad individual, compromiso mínimo, catálogo, transacciones inmediatas) | 9–13 semanas |
| Transacciones diferidas y algoritmo de sanciones y reputación | 3–5 semanas adicionales |
| Ajustes post-piloto y refinamiento de parámetros (plazo de caducidad, límites) | 2–4 semanas |

Estimación para un equipo chico (1 a 2 desarrolladores full-stack). La caducidad por lote suma complejidad respecto de un vencimiento colectivo, porque cada recepción genera un registro y cada gasto debe recorrer los lotes vigentes, pero es un cambio acotado dentro del motor de créditos. Los costos de infraestructura iniciales son bajos.

8\. Decisiones clave pendientes

- Plazo de caducidad del token: duración y si es fijo o ajustable por zona o por nivel de actividad.

- Si el reloj se reinicia en cada recepción: esta versión asume que cada token recibido como pago genera un lote nuevo con su propio plazo completo.

- Cómo se mide el compromiso mínimo respecto de los lotes vencidos: si un usuario pierde tokens por no gastarlos, qué parte cuenta como ya cubierta.

- Plazo máximo permitido para una transacción diferida antes de considerarla incumplida.

- Criterio de definición de zonas y qué ocurre si una zona no alcanza masa crítica.

- Alcance del piloto: se recomienda una sola zona acotada, para probar la caducidad por lote y el compromiso mínimo antes de escalar.
