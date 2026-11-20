---
tipo: transcripcion
estado: activo
fecha: 2026-11-20
fecha_llamada: por confirmar
hora: por confirmar
lugar: Llamada / videollamada
participantes: Hernan; Rodrigo
area: direccion
fuente: "[[16 - Archivo/2026/transcripcion_original.txt]]"
actualizado: 2026-11-20
---

# Llamada con Hernán — Transcripción editada

> [!info] Cómo leer esta transcripción
> - **Fecha exacta de la llamada**: por confirmar. El registro se cargó el **2026-11-20**.
> - **Participantes**: Hernán (impulsor de la idea) y Rodrigo (tecnología y análisis de datos).
> - **Fuente**: [[16 - Archivo/2026/transcripcion_original.txt|transcripción automática original]] (~14.400 palabras, sin puntuación ni hablantes).
> - **Criterio de edición**: se conservan ideas, ejemplos, cifras y giros; se corrigieron errores evidentes de reconocimiento de voz y se quitaron repeticiones y muletillas. Las omisiones se marcan con `[...]`. Lo que no pudo confirmarse se marca `[por confirmar]`.
> - **No es una transcripción taquigráfica**: es una edición de legibilidad. Para citas textuales, verificar contra el audio original.
> - **Términos**: Hernán alterna “bono”, “crédito”, “punto” y “token”. En esta edición se usan **bono** y **crédito de intercambio** para la unidad que vence, y **token de recompensa** para el token permanente que se evalúa más adelante.

## Mapa de la conversación

1. [[#1. El origen — la crisis de 2001 y las monedas sociales|Origen de la idea]]
2. [[#2. El circuito original en papel|Circuito original en papel]]
3. [[#3. El giro digital — UTXO con vencimiento|Giro digital y blockchain]]
4. [[#4. Los dos proyectos — crédito de intercambio y token de recompensa|Los dos proyectos]]
5. [[#5. Regulación, registro y alcance del MVP|Regulación y MVP]]
6. [[#6. Cómo se fija el valor|Cómo se fija el valor]]
7. [[#7. El problema del cumplimiento — ¿quién obliga a cumplir?|Cumplimiento y confianza]]
8. [[#8. La DAO como contraparte|La DAO como contraparte]]
9. [[#9. Sanciones, incentivos y límites|Sanciones e incentivos]]
10. [[#10. El circuito en la práctica|El circuito en la práctica]]
11. [[#11. Territorio, oficios y economía mixta|Territorio y economía mixta]]
12. [[#12. Simulación con agentes de IA|Simulación con IA]]
13. [[#13. Archivos, contactos y próximos pasos|Archivos y próximos pasos]]

---

## 1. El origen — la crisis de 2001 y las monedas sociales

**Hernán:** La idea viene de lejos. Hace mucho tiempo, desde la crisis del 2001 y todo el fenómeno del trueque, me quedó ese bichito de por qué no se desarrollaron más monedas sociales o formatos de trueque que estuvieran libres de los efectos del dinero fiduciario.

En esa época, comienzos de los 2000, había una movida en Europa —España y un par de países— y yo miraba unos videos en YouTube, que recién empezaba. Empecé a investigar por mi cuenta, de forma autodidacta, cómo funcionaba la economía en un sentido bien básico, bien antropológico. [...]

En algún momento se me ocurrió la idea de emitir **créditos que funcionaran exclusivamente para el trueque**, como bien de cambio, y que tuvieran dos características: **gratuitos en su emisión** y **caducos**, con un tiempo de vencimiento. Si no los usás, no te sirven. Lo pensé cuando todavía no existía blockchain ni todo eso; la idea era crear bonos físicos.

Después investigué que en Austria, en un proyecto municipal, se desarrolló un sistema de monedas o bonos sociales con un fenómeno que llamaban **oxidación**: el bono iba perdiendo valor con el tiempo. Era un formato para forzar el uso. Yo no quería complicarme con eso —vi cómo trabajaba y era complejo: el organizador tenía que recibir, marcar, controlar—, así que preferí que los bonos **tuvieran vencimiento** y listo: se emiten, se entregan y se vencen.

## 2. El circuito original en papel

**Hernán:** La entrega era en proporción a lo que uno estuviera dispuesto a dar. Por ejemplo, yo soy parquero y pongo a disposición, durante el lapso del circuito —que se llama “Mes”—, 30 horas de cortar pasto. Entonces cobro un equivalente por eso en bonos.

En ese momento pensaba en algo parecido a lo que hace el **Chonobank** [por confirmar nombre]: que las horas de trabajo valgan más o menos lo mismo para todos. Un valor hora. Entonces tenías el equivalente de 30 horas en ese crédito y, mientras los tenías, podías comprarle a otro que ofrecía tortas fritas: ponía a disposición 20 docenas y recibía la cantidad de bonos equivalente.

Incluso armé una ecuación —después te la mando— para llegar al valor de un producto en relación con el tiempo de un servicio. Terminaba recayendo en alguna cotización de precios: el valor de la hora de trabajo se trasladaba a los productos y eso resultaba en un bono.

Esas personas usaban los bonos para comprar las tortas fritas; la de las tortas recibía los bonos y con esos bonos le pagaba al albañil; el albañil cobraba esos bonos; todo giraba hasta que, en algún momento, se vencían.

Había una tensión: llega un momento en que la gente no quiere recibir bonos porque se van a vencer. Entonces buscaba **sanciones** para que nadie pudiera rechazar un bono si no había cumplido primero con su tiempo. Si ya cumpliste con tus 30 horas de parquero y te ofrecen más bonos, podés rechazarlos porque ya cumpliste y ya recibiste lo que te correspondía. Pero mientras estás trabajando, vas cobrando y gastando. En un momento eso se frena. La idea es que, antes de que se liquide el sistema, se haga una nueva emisión. Todo eso suena a un sistema físico.

## 3. El giro digital — UTXO con vencimiento

**Hernán:** En un principio lo empecé como una **app cerrada**: se arma un circuito, todos se juntan, se inscriben con lo que van a producir, reciben bonos a cambio y los disponen.

Pero después, cuando empecé a estudiar blockchain y a ver cómo funcionaba el tema de los **UTXO**, dije: quizás lo mejor es que el bono tenga caducidad **mientras está quieto**. Vos cobrás, se parte el UTXO que tenías y te queda uno más chiquito; ese UTXO se vence si no lo gastás. Una vez que lo gastás y lo pasás a otro, se genera un UTXO nuevo, y ese se va a vencer cuando esté en posesión de otra persona.

Lo pensé así porque me parecía más justo: no hay que esperar un momento de cierre total, sino que todo el tiempo está funcionando. El bono se vence **en posesión**, no se vence todo el circuito de golpe. Esa fue la idea.

**Rodrigo:** ¿Cómo distinguís los que están en posesión de los que están en tránsito?

**Hernán:** Los que están en posesión son los que me da otra persona; esos son los que tengo. Lo pensé a partir de Bitcoin: un protocolo donde los UTXO tienen caducidad. Tenés un UTXO de 10 bonos; los 10 puntos se te empiezan a vencer. Rompés el UTXO y gastás 5. Esos 5, cuando se los pasás a otro, generan un UTXO nuevo con una renovación de tiempo.

**Rodrigo:** Ahí hay una restricción técnica, y ahí sí es fungible: estás particionando los puntos como si fuera una moneda. Eso ya no es un bono; aunque no sea intercambiable por otros dineros, es fungible, y ahí entra la CNV.

**Hernán:** Yo lo pienso como un bono social: es un NFT que equivale a cierta cantidad, pero el valor es implícito entre las personas. Cada uno le da el valor que quiere.

**Rodrigo:** Técnicamente no es lo mismo, porque un NFT no es fungible. Pero regulatoriamente, para la CNV, estás haciendo un intercambio de un producto por un servicio. No hay plata de por medio; el NFT es la manera de comprobar que se cumplió el intercambio. La idea es que funcione como un **bono de trueque dinámico**. La gratuidad implica que esos tokens no tienen un valor en sí ni una cotización previa; simplemente son el compromiso de intercambiar.

**Hernán:** Claro. La gente igual le va a dar un valor, aunque vos no quieras. Va a decir “una hora de mi trabajo no vale dos empanadas”, y ahí empiezan las negociaciones. Y ahí empieza el mercado.

**Rodrigo:** Es el “bono blue”. La gente le va a dar su propio valor.

**Hernán:** Por eso el vencimiento tiene otro propósito: que no llegue a haber un cambio de precios justificable. Que se venza antes de que cambien los precios de las cosas. Y por eso también los precios están puestos de antemano: no se negocian.

## 4. Los dos proyectos — crédito de intercambio y token de recompensa

**Hernán:** También pensaba en un sistema de incentivos, viendo cómo funciona la compensación basada en tokens. Quizás la misma actividad de participar y generar la dinámica podría generar cada tanto un **token permanente**, distinto.

Entonces correrían dos cosas: por un lado, un token **netamente para bien de cambio**, que se vence mientras está quieto y se renueva a medida que lo movés; por otro, después de cierto tiempo de trabajo, un **token de recompensa** estable, fungible, que ya tendría otra calidad: se podría intercambiar con otros tokens y otras monedas, y eso sí lo llevaría al mundo de las criptofinanzas.

Eso es lo que me fue cerrando. Lo otro que te estoy diciendo está escrito. Me ayudó Clau [Claude] a darle las últimas formas. Están los dos: un **pitch empresarial** para venderlo rápido y que se entienda, y un **pitch más técnico** para el que lo tenga que desarrollar. Y están los dos proyectos: uno sin el token de recompensa y otro con el token de recompensa mencionado.

Si hay que desarrollar un producto mínimo viable, quizás sea conveniente al principio lanzar **solamente el token de intercambio**, sin complicarse con el token de recompensa, porque eso requiere otras habilitaciones, registrar en la CNV y un montón de cosas más. El MVP con el token de intercambio es más fácil de desarrollar.

## 5. Regulación, registro y alcance del MVP

**Rodrigo:** Habría que buscar las regulaciones primero.

**Hernán:** Sí. Entiendo que un token que sea netamente de cambio, que no se cruce con dinero para nada, no va a tener tantas complejidades de regulación: es una plataforma donde todo el mundo ofrece productos y servicios, y por ofrecer recibe puntos que después usa para intercambiar. No hay guita en el medio.

De hecho, pensaba que la registración sea sin mayores datos: el nombre que cada uno quiera poner, un seudónimo si quiere, y un contacto para arreglar los intercambios. Sin necesidad de poner DNI ni nada, porque no hace falta. Para ese tipo de registro básico, alcanza.

Ahora, cuando entra el otro token, ahí sí, obviamente, porque por lo menos al momento de sacarlo de la aplicación y ponerlo a girar en otro contexto. No sé ni siquiera cómo se hacen esas articulaciones. Cuando uno desarrolla un token de tipo fiduciario, no sé cómo hacés para ubicarlo en un exchange y esas cosas; no tengo idea.

**Rodrigo:** Se haría con una wallet propia, que deberíamos tener, y se mueve en la red mediante esas wallets. Pero el tema de la emisión es todo un tema: hay que establecer si tiene valor, si no tiene valor, cómo calculamos el valor.

**Hernán:** Exacto. Pero en este caso no sería un token estilo fiduciario, sería uno fungible.

**Rodrigo:** Ahí no habría problema porque, nada, intercambiamos NFTs; serían como bonos. Lo que tiene es que el valor... yo lo pienso como un logaritmo o un protocolo que debe darle valor a la oferta de trabajo que uno propone. Por ejemplo, yo propongo ofertar tantas horas de cortar pasto o tantas horas de trabajo de albañil, y que haya una escala donde automáticamente se le otorgue la cantidad de créditos o bonos que valora esa cantidad de oferta de horas.

## 6. Cómo se fija el valor

**Rodrigo:** Pongamos el ejemplo del albañil: hay albañiles que cobran más y otros menos, en base a la experiencia. Uno que está arrancando no cobra lo mismo que uno que tiene 20 años de experiencia. ¿Cómo comprobamos esa experiencia?

**Hernán:** Ahí la cuestión es medio “cara de perro”: se ofrece un valor por tanta cosa y lo tomás o lo dejás. Es un mecanismo desarrollado exclusivamente para quien no tiene fuerza de trabajo y no está encontrando demanda. No hay dinero, entonces no hay demanda de trabajo. Es un sistema para **crear demanda**.

**Rodrigo:** ¿Y por qué lo emitiría?

**Hernán:** Porque al no haber demanda, requerimos que las personas **emitan sus propios bonos**, los intercambien con quien quieran, pero tienen un vencimiento. Ahí está el tema del vencimiento.

**Rodrigo:** ¿Por qué elegiste establecerle un vencimiento al bono?

**Hernán:** Para que tenga **velocidad de intercambio**, para que nadie lo quiera guardar. A vos te regalan algo y sabés que lo podés usar un cierto tiempo; entonces lo vas a querer usar cuanto antes. Quizás en otro momento dudarías, dirías “no lo gasto”, pero sabés que si te duerme se vence. Y aparte fue gratuito en su origen, así que lo vas a gastar. Eso genera una dinámica.

Obviamente, eso tiene que funcionar en un ecosistema donde haya variedad de productos y servicios, donde haya interés de intercambio. Cuando lo pensaba en el proyecto original de la moneda social, pensaba en un municipio que articule con alguna empresa local que aporte mercadería —por ejemplo, una empresa de lácteos— para enriquecer la oferta. Pero eso ya sale un poco del esquema de emprendedores autónomos y artesanos. A las empresas no les sirve este tipo de bono de intercambio; sería más una opción de arreglo político. Cuando lo pensaba como programa municipal, también me preguntaba si esta plataforma podría ser útil a un municipio. En general, los estados son medio desconfiados de la economía social y de ese tipo de economía alternativa. Pero cuando las papas queman y hay mucha recesión, es a las papas.

## 7. El problema del cumplimiento — ¿quién obliga a cumplir?

**Rodrigo:** Se me viene a la mente el tema del intercambio. Yo le doy mis bonos a un albañil. ¿Cómo hacemos el cálculo al no ser fungible? El NFT no es fungible. Este bono representa cierta cantidad de puntos. No se lo podríamos dar a través de un NFT, a no ser que tenga un valor asociado. No le puedo dar lo mismo a un albañil que a un dentista por el mismo tiempo trabajado. ¿Cómo lo establecerías?

**Hernán:** Dos mecanismos. Uno: que el tiempo de todos valga igual, que es quizá menos complicado. Y el otro: tener una **escala de valor hora** según el oficio. Es para oficios de poca escala: albañiles, parqueros, la chica que hace las uñas, clases de guitarra, clases particulares, artesanos, productores de comidas artesanales, vendedores de ropa de economía circular. Incluso alguien común podría ofertar cosas usadas: “no quiero vender mi mueble”, se le da un valor en puntos según una cotización por la foto, y otro lo cambia.

Es básicamente para que quien no tiene un mango se haga de unos créditos que le pueden salvar las papas, haciendo una serie de intercambios de cosas artesanales, venta directa, productores locales. Está muy pensado en sentido regional.

**Rodrigo:** El mayor problema es que una persona cuando no tiene no se pone a gastar en cosas que no la alimentan. Todo bien con la gente de la feria, pero si no tengo un mango no voy a gastar mi tiempo en cosas que no puedo comer, que no le puedo dar de comer a mi familia. Se me ocurre que los municipios van a tener que estar, porque podrían dar y gestionar esa emisión de bonos a las personas que están sin trabajo, y esas personas los pueden cambiar con otras que hacen changas dentro de la economía alternativa. Y los supermercados, kioscos, podrían aceptarlos y recibir a cambio excepciones fiscales. ¿Viste que hay que pagar ABL? Imaginate si me descontás de ABL por esos bonos.

**Hernán:** Eso, en su momento, cuando lo proponía, se llama **bono municipal**. Se ha usado en Europa. Pero después lo pensé en un sentido privado: simplemente se ofrece una plataforma que todo el mundo se descarga en su app. Vos descargás, das tu dato para que te localicen, ofertás lo que vas a ofertar y ya recibís unos puntos de intercambio. Entonces accedés al catálogo de todos los que están en la zona cercana, ves qué podés adquirir con tus puntos y empieza el intercambio.

Cuando contactás a alguien —“me interesan tus empanadas”—, ya están ofertadas a un precio X, porque el precio no se regatea. Cuando las carga, el sistema las carga con un precio; vas, las compras, y pasan los puntos. El de las empanadas tiene los puntos que recibió cuando ofertó, más los que le pagaste. Con esos dos puntos sumados, que se van a empezar a vencer, dice: “bueno, ¿qué necesito antes de que se venzan?”. Encuentra a un muchacho que hace jardinería, que tiene cotizada su hora en tantos puntos. “¿Me alcanza para tres horas?”. Listo, encarga tres horas, le paga, y el parquero tiene los puntos que recibió más los que vos le pagaste. Y así sigue el circuito.

## 8. La DAO como contraparte

**Rodrigo:** ¿Quién me obliga a cumplir con vos o con alguien más? El protocolo tiene que hacer algo. No podés sancionar a una persona que no tiene nada. ¿Con qué la vas a atar? Legalmente no la podés obligar. El sistema la sanciona no dejándola entrar a otro circuito de trueque, porque se vincula un Gmail.

**Hernán:** No, tiene que ser con **identidad**. Se registra como persona y esa persona queda asociada a una cuenta. Siempre que cumpla la ley de almacenamiento de datos personales, no hay problema.

**Rodrigo:** El tema es que a mí no me interesa participar en esta economía social. Voy, compro dos kilos de milanesa y listo, chau, no lo uso más. ¿Quién me va a perseguir? No hay manera de obligar a las personas, a no ser que se entregue algo en garantía. Uno se apalanca con algo: “pongo esta moto en garantía”.

**Hernán:** Para mí siempre fue el apalancamiento el **compromiso de trabajo y de productos**. Ese era el sostén detrás del token. Si uno quiere comprar milanesas en el supermercado, se anota después en la plataforma y entra con esas milanesas cotizadas en tantos tokens; con tokens contrata al parquero. [...]

**Rodrigo:** Ahí habría que meter árbitros, el sistema de arbitraje. Ya hay que meter cosas judiciales, contratos. A ver: el compromiso podría no caducar. Caduca la moneda, pero no caduca el compromiso. Entonces, en algún momento alguien te va a demandar lo que tenés ahí, porque alguien no se va a querer quedar con que se le venza, aunque sea algo que no le sirva. Antes de que se le venza un token, se va a comprar algo, aunque no lo quiera comer.

**Hernán:** Sí, o podés renovar el período porque lo almacenás, no sé, un mes, dos meses. Pero si intercambiás con otra persona por otra cosa, para después intercambiarlo por algo que el mes que viene sabés que va a estar en el supermercado —como los pan dulces, que ahora vienen en Navidad—, ahí ya no habría problema, porque al fin y al cabo estás haciendo mover la economía. Uno se compromete a hacer entrega de servicios o de productos, no exactamente de ese mismo producto. “Yo solicito tokens y pongo a disposición 10 docenas de empanadas”. Los tokens en mi posesión se van a vencer, pero **mi compromiso no se vence**. En un momento alguien me va a venir a decir “me debés”.

**Rodrigo:** Me parece que lo estamos viendo mal. Lo estamos viendo como token, y estos son **smart contracts**. Nosotros lo que estamos haciendo es establecer un contrato entre esa persona y nuestra sociedad, entre la organización DAO. Establecés el contrato con nuestra sociedad; la otra persona que está en el medio, que está ofertando —yo te oferté milanesas—, perfecto. La asociación no le da a la persona, sino que le da estos tokens a quien vendió la milanesa. Entonces esa persona no está en deuda con el vendedor, está en deuda con nosotros. Nosotros seríamos quienes le reclamamos a esa persona, mostrando que en el tablero —en este dashboard donde aparecen los productos o servicios— dice: “tal persona está obligada, tiene cuatro horas de trabajo obligadas”. Ya intercambió milanesas con nosotros, entonces está obligada a cumplir ese trabajo. Y después, cuando trabaja, se le asigna otro UTXO, otro smart contract: “esta persona le pagó a tal persona”, y la titularidad del smart contract ahora pasa a ser de quien lo volvió a contratar. Yo contraté al albañil que compró la milanesa. El valor de la milanesa se va trasladando de una persona a otra.

**Hernán:** Me gusta. Y así claramente no tendría vencimiento, sino que esta persona... listo, yo ahora otra vez tengo obligación de entregar mis servicios. Yo contraté a alguien obteniendo su deuda; compro su deuda, compro su milanesa, y tendría que entregar esa deuda a otra persona que la requiere. Y se hace circular.

**Rodrigo:** Y ahí viene: yo soy empleado del supermercado y le digo “quiero comprar tu servicio de programación”. Bueno, está bien, intercambio el servicio. Y ahora esta persona está obligada. ¿Quién le paga al empleado del supermercado?

**Hernán:** No lo pensé en el sentido de empleados. Lo empecé en el sentido de... En este tipo de economías alternativas se le llama **prosumidor**: productor y consumidor al mismo tiempo. Por eso nadie debería ser poseedor de un token de intercambio si no tiene nada que ofrecer. La oferta se da cuando producís algo; si no producís, no. Se trata de buscar un esquema donde haya intercambios de igualdad, horizontal, no una cuestión de empleadores.

**Rodrigo:** En el ejemplo del supermercado, me imagino que la persona que vendía milanesas era una señora que en la esquina de su casa vende milanesas. Para pagarle, puedo hacerlo directamente con ella o subirlo a un **pool de oferta**, un pool de mercado donde están todas las ofertas de horarios hábiles. Alguien puede intercambiar ese smart contract. Yo puedo ayudar a la señora por cierta cantidad de horas que ella quiera, por esa cantidad de milanesas. O decir “que pague la DAO”, y yo me comprometo a cumplir otro tipo de trabajo. Pero a la señora se le asigna una compensación requerida que, al fin y al cabo, alguien tiene que cumplir.

**Hernán:** Es que el esquema es que uno, cuando la señora produjo milanesas, recibió X. Por otro lado, había ofertado corte de pasto. La señora no tiene corte de pasto, no le interesa lo que oferta este muchacho, pero este muchacho, por ofertar corte de pasto, tiene los tokens a disposición para adquirir milanesa. Entonces adquiere milanesa. La señora tiene los tokens que recibió por ofertar las milanesas y además los tokens que recibió del cortapasto, que no le va a cortar el pasto. Pero ella buscará en el mercado otras cosas que le interesen: ropa de la que hace ropa en economía circular. Se va y le compra la blusa y los pantalones a esa señora con esos tokens. Y esa señora, que ofertó una serie de prendas, con eso le paga al del cortapasto. Y el cortapasto puede ir a cortar pasto. Es una dinámica más o menos circular, chiquita.

## 9. Sanciones, incentivos y límites

**Rodrigo:** ¿Qué pasa si alguien oferta algo que no piensa entregar? Compra milanesas y después no entrega las sillas.

**Hernán:** Eso ya es un conflicto, no una viveza: está faltando a su palabra. Cuando tengo la obligación de cumplir ciertas horas laborales porque me comprometí con otra persona y no lo cumplo, o lo hago de mala manera —un albañil que te hace mal la pared—, ahí hay un sistema de puntuación. Claude me proponía un esquema de scoring. [...]

**Rodrigo:** Cintia, la señora con la que hablábamos el otro día, me contaba de una aplicación que se llama **Minga**, que ya tenía un pre-MVP. El concepto era similar, pero con intercambio de plata de por medio, no tokens. En la entrega, como en Mercado Libre, cuando te entregan el producto vos le entregás un código y ahí la transacción está realizada. Ese sistema se puede implementar: hasta que no se entrega ese código, no está confirmada la transacción.

**Hernán:** Sí. Y acá el ente estatal nos podría ser útil, por lo menos para probar y generar confianza. Al tener la obligatoriedad de cumplir al firmar el contrato con la DAO —que sería el ente superior, el que legisla—, si vos no querés cambiar, tenés los bonos, tenés una obligación. Si no cumplís tu obligación en cierto período, se ejecuta el smart contract diciendo “hay que ir a tribunales”, entre comillas, porque le tenemos que otorgar confianza a los otros que intercambian. Si no, no tienen confianza. La gente mala siempre va a estar. Ahí es donde puede intervenir el municipio otorgando los servicios legales o de mediación entre la organización y esa persona. La organización, en este caso, sería el municipio; la DAO sería... bueno, la DAO tendría que ser votada. Pero el Consejo debería ser parte de la parte legal, más que nada el municipio.

**Rodrigo:** ¿Qué tipo de sanción pueden poner? Porque no podés sancionar a una persona que no tiene nada.

**Hernán:** Para mí la única sanción viable era la sanción **dentro del mismo esquema**. No podés renovar. Ya te gastaste todo lo que tenías; si tenías ganas de seguir participando, no vas a poder hacerlo porque tenés una marca de que rechazaste cumplir con tus servicios o productos ante la solicitud de un intercambio con tokens.

**Rodrigo:** Eso te mete en el Veraz. “No te podés meter más en el sistema”. Y hay mucha gente que no le interesa.

**Hernán:** El protocolo no te deja entrar más. Tenés que cumplir. Y pondría también un **piso y un límite** de lo que podés ofertar y, por tanto, de los créditos que podés recibir. No voy a poner un auto a disposición y con eso hacerme los tokens como para vaciar todo el mercado y después no entregarlo. Siempre hablamos de un tope muy básico, que hay que estudiar: un valor que no sea mucho riesgo. Me comprometía a entregar una cantidad de producto que, más o menos, serían unos 100.000 pesos como máximo y 20.000 como mínimo [cifras de ejemplo, a definir].

**Rodrigo:** Si no lo cumpliste, no vas a estafar a nadie concreto ni al sistema. Si hay mucha dinámica, el sistema se renueva solo, le encuentra la vuelta. Si hay 200 inscriptos, vos no me rechazaste, le pongo una sanción, pero tengo mis tokens y busco comprar otra cosa. El circuito sigue. Ahora, si eso lo hacen todos, es evidencia de que el sistema no sirve para ese grupo.

**Hernán:** En momentos de recesión como los que hay ahora, la gente va a tratar de buscar lo máximo posible. ¿Te imaginás cuánta gente se endeudó con Mercado Libre y le chupa un huevo pagarle? La gente, en momentos de recesión, lamentablemente es así; después, cuando termina la recesión, esperan que venza la deuda y listo. En cambio, nosotros tenemos que fortalecer un **sistema de confianza**. ¿Cómo damos confianza? Con mano dura. No puede ser que una persona no pague y no pague las consecuencias.

**Rodrigo:** Siendo DAO, siendo el representante de Azul, del municipio, que gestiona el proyecto... ¿Qué tipo de sanción pueden poner? La gente encuentra un esquema nuevo y va a tratar de romperlo.

**Hernán:** La idea es que prospere. Para prosperar tenemos que decirle: “mirá, vos no cumpliste, firmaste un contrato con la DAO —o con el municipio—, entonces tenés una obligación”. ¿Te lo agregamos en el ABL? No sé si se podría. Yo intento creer que la sanción tiene que estar **en línea con el incentivo**. El incentivo es participar y tener la posibilidad de seguir colocando tus productos y acceder a otras cosas porque hay un sistema alternativo que no está por fuera de la recesión. Querés estar en ese sistema. El hecho de no cumplir te deja fuera. [...]

**Rodrigo:** Se me ocurre que la mejor manera sería ir **devaluando el precio de su bono**. Rechazaste cinco ofertas: tu bono vale 5% menos. Y así sucesivamente, para decirle “usalo lo antes posible, porque estás rechazando todas las ofertas de trabajo que te estamos proponiendo”.

**Hernán:** Hay un costado **neo-keynesiano** en mi propuesta: la dinámica por encima de todo. Por eso lo de que sea caduco, que haya ofertas y que no haya muchas opciones de estar rechazando. Incluso el precio debería estar pautado de antemano. Vos anotás “quiero vender este juego de sillas”; el sistema dice que el juego está a un equivalente de 100.000 pesos, o te lo dividen por silla a 30.000. Vos lo aceptás o no. Si lo aceptás, tenés 100.000 pesos en bonos para gastar. Si no, no entrás y ves otra posibilidad. Yo haría que el sistema dé un valor desde el comienzo a lo que estás ofertando. Que no sea cuestión de regateo. Entonces yo ya sé que X se está ofertando a tanta cantidad y, si me alcanza, se las compro, porque el precio ya está puesto. El chabón estaba dudoso del precio y no quiere venderlas, pero bueno, aprobó con ese precio. No puedo ir a ofertarle un precio más bajo.

**Rodrigo:** Ahí metemos plata.

**Hernán:** Sí, es el concepto de plata, pero va a ser una **unidad de medida** dentro del sistema. El bono va a ser una unidad de medida. Yo había hecho una ecuación: un promedio del valor de las horas de trabajo, que se cotizan en tanta cantidad de dinero; eso es igual a un bono. Entonces, si tenés tortas fritas que salen tanta guita, se compara con ese valor de la hora promedio de trabajo y como resultante te da X cantidad de bonos. Eso es lo que el mercado va a ofertar por tu producción. Vos, cuando entrás, le ponés un valor en plata; ese valor se traduce en X bonos. El sistema dirá si es excesivo o no. Podemos poner un criterio o no. Corremos el riesgo de que se infle mucho si todo el mundo empieza a poner el precio que se le ocurre antes de cargarlo. Es un riesgo que se corre. Por eso creo que hay muchas cosas que no podemos saber si no dejamos que labore ruede. Hay que tener planes, alternativas, ir anticipando, pero mucho es cuestión de desarrollar el modelo y hacerlo girar.

## 10. El circuito en la práctica

**Rodrigo:** A ver si entendí: te inscribís, ofertás lo que vas a dar, recibís puntos por inscribirte, accedés al catálogo de la zona, comprás con puntos, el que vendió recibe puntos, y esos puntos se van venciendo. Si querés seguir, tenés que volver a ofertar. ¿Es así?

**Hernán:** Sí. Y si no tuviste demanda de lo tuyo, tuviste un límite: cambiaste lo que tenías en la mano y no más. Ayudaste a la dinámica del mercado aportando tus tokens y haciéndolos girar, pero no te quedó de más. Tendrás que esperar a inscribirte nuevamente en otra apertura del ciclo para poder ofertar de nuevo. Obviamente uno va a querer poner algo que se venda, porque quiere ganar más y seguir teniendo tokens. Y una persona, por más de que no intercambie tokens con otra, puede usar sus propios tokens emitidos por sí mismo para intercambiarlos por comida.

**Rodrigo:** Pará: si una persona emite y no trabaja, o no vende, tenemos emisión infinita.

**Hernán:** Por eso está el tema de los **ciclos**. Esto tiene que cerrar y se tiene que volver a armar. Hay que estudiar los ciclos de cierre.

**Rodrigo:** Se me ocurre que se podrían generar al momento de producir un intercambio. Yo quiero comprar empanadas, no tengo bonos, pero tendría que haber una **bolsa de bonos** de dónde sacarlos, porque yo no los puedo emitir. Pero los tengo que respaldar. Tendría que haber una obligación por detrás.

**Hernán:** Eso tendría que ser una **obligación negociable**. Ese es el mejor ejemplo del mercado. Vos, al querer intercambiar por eso, ya te comprometés: tenés una obligación por detrás de ejecutar esas horas trabajadas. Por eso la sanción era “estabas obligado a no rechazar oferta de token por demanda de trabajo”. Si no aceptabas, no podías ingresar después en X cantidad de ciclos.

**Rodrigo:** Pero si no hay demanda, no sé cómo obligás a alguien a que cree su demanda.

**Hernán:** Es una demanda comunitaria. Me imagino un tablero donde hay oferta: “tal persona compró tales cosas y por eso intercambia”. Podemos hacer una especie de ciclo. Vos tenés un tablero donde dice “Hernán le cambió a Rodrigo clases de jiu-jitsu; por lo tanto, Rodrigo está obligado a entregarle esas horas a Hernán”. Pero si Hernán no las quiere, puede pasárselas a otra persona. El bono es el que está haciendo la vez.

**Rodrigo:** ¿Quién me obliga a cumplir? Emitimos el bono, emitimos el contrato entre nosotros, pero ¿quién me obliga? Hay que buscar el protocolo. Y no podés sancionar a una persona que no tiene nada.

**Hernán:** Legalmente es un contrato. El sistema sanciona no dejándote ingresar en otro circuito de trueque. Como se vincula un Gmail...

**Rodrigo:** No, tiene que ser con identidad. Se registra como persona y esa persona queda asociada a una cuenta. Siempre que cumpla la ley de almacenamiento de datos personales, no hay problema.

## 11. Territorio, oficios y economía mixta

**Hernán:** Está muy pensado en sentido regional. En la comunidad de feriantes que yo conocía hay una tendencia a producir todo lo mismo, porque todos apuntan a venderle a un tipo de sujeto que pasea y quiere comprar. Yo insistía en la oficina: ¿cómo incorporamos a los que hacen oficios —zapatero, cortapasto, toda esa gente—? Están todos muy enfocados en los feriantes o los artesanos, y hay otro mundo de gente en la economía informal que tenemos que traer. Si juntamos toda esa base de información y les ofrecemos esto, hay variedad de ofertas y eso puede generar más interés en la demanda.

**Rodrigo:** También tenés que fijarte en los productores. Si no tenemos a nadie que produzca, muy lindo si metemos todos cortadores de pasto, pero necesitás gente que dé el valor que la gente dice.

**Hernán:** Yo traté de empezar por lo antropológico: cuáles son nuestras demandas cotidianas. La vivienda no la podemos meter, es muy compleja. Los servicios también son casi imposibles.

En un momento fui muy fanático de la economía alternativa y buscaba sistemas netamente alternativos. Después dije: busquemos **esquemas mixtos**, donde un sistema pueda convivir con el otro sin tener que suprimir al otro. Vos cobrás un sueldo, tenés una changa por otro lado —carpintería, por ejemplo—, y la carpintería también la disponés para el sistema de trueque. Con mi sueldo formal pago alquiler, servicios y demás, y trato de rebuscármela para conseguir los otros insumos: las facturas para el mate, el plomero, la clase de guitarra. Eso lo voy tirando a resolver con este otro esquema, el trueque. Esa sería la idea.

También sumamos la posibilidad de que, si no sos artesano ni productor, vendas cosas usadas. Me acuerdo de un hackatón de chicos que ganaron el segundo puesto con una app para ofertar electrónica usada. Yo lo que estoy pensando es mucho más amplio en la oferta. No es tan difícil defenderlo porque cubrís una demanda muy específica inmediatamente.

**Rodrigo:** ¿Puede escalar?

**Hernán:** Yo creo que sí, pero quizás no de la forma que uno... Tampoco la idea sería escalar. La idea sería **cubrir la demanda** y que la gente lo haga crecer. Vos no lo hacés crecer; la infraestructura está y la gente decide si se suma o no. No hace falta planificar la escalabilidad del día cero. Sí tener ciertos gatillos para ir resolviendo, pero no planificar todo. Lo que pase y lo que se encuentre en el medio, iremos viendo qué adaptación quiere hacer el protocolo para cumplir con esa demanda de escalabilidad, si se justifica o no.

**Rodrigo:** ¿Dónde lo harías? ¿En Azul?

**Hernán:** Yo pensaba hacerlo acá en Azul, pero en el pueblo hay 120.000 personas. En la comunidad de feriantes hay una tendencia a producir todo lo mismo. Yo buscaría un sector con más dinámica, más en el conurbano. Hay más economía social y más dinámica, y quizás ahí se puedan conseguir rápidamente 200, 300 usuarios que bajen la aplicación, oferten sus productos y se pueda hacer un testeo. Acá en Azul la economía es más depresiva y todos producen lo mismo, pensando en venderle al que está de paseo. Todo el mundo hace panificados, comidas... La comida es importante que esté, pero también hay otras cosas.

**Rodrigo:** ¿Y el municipio?

**Hernán:** Sí, requeriría un municipio. Pero yo soy empleado municipal en esa área y no quisiera mezclar las cosas hasta que el producto no esté más acabado. Cuando el producto sea viable y tenga aprobación, ahí sí vengo y lo oferto. Pero no lo haría en principio, porque recién lo empezaría a ofertar entre gente que me conoce; no daría abasto de la cantidad de consultas particulares que me caerían todo el tiempo. Sería muy complejo. Aunque sería lo mejor.

**Rodrigo:** Ahí entran los agentes de inteligencia artificial.

**Hernán:** Sí. Y también hay que tener en cuenta el contexto del lugar, una persona a la cual acudir. Si no estás allá con las manos en el barro, no se va a poder hacer nada. Parece un desconocido y te dicen “vení, metete”, y anda a cagar. Por eso, estando ahí es un beneficio. Además hay cercanía con gente que nos puede dar ayuda en la parte legal. Moisés [por confirmar] es abogada, pero está hasta las manos. No sé si nos cobre. Hay interés en que las cosas funcionen.

## 12. Simulación con agentes de IA

**Rodrigo:** Para probar el modelo antes de lanzarlo, se me ocurre crear agentes que imiten el comportamiento de una ciudadanía. ¿Conocés Minecraft? En Minecraft se hizo una simulación de vida; hay personajes tipo aldeanos que intercambian productos, hacen trueque. Estaría bueno ver si se puede crear una simulación no animada, a nivel agéntico, y que saque conclusiones: ¿dónde se bloquea?

**Hernán:** Sí. Yo encima estoy estudiando análisis de datos, así que se podría hacer un buen análisis y ver las estadísticas.

**Rodrigo:** Se me ocurre arrancar con 10 agentes variados e ir subiendo. Para subirlos necesitamos mucho poder de cómputo. ¿Cuánto costo dedicarle a esa etapa de análisis antes del desarrollo? Tiene que haber un punto donde decir “ya analizamos”.

**Hernán:** Creo que se puede crear un ambiente. El problema no sería tanto el poder de cómputo, sino las inteligencias artificiales. Tendríamos que invertir unos 20, 30 dólares para hacer esa prueba. Creo que con 10 dólares lo podemos hacer.

Lo que tenemos que hacer es que cada uno tenga su propio cerebro, su propia casita. En su casa le asignamos una personalidad: “tal persona, se le crea un alma, es esta persona”. Le creamos un catálogo con las cosas que tiene en su casa, sus habilidades, sus conocimientos. “Sos una persona que tiene su alma, que es esta, que es Hernán, y hace tal, tal, tal cosa; en su heladera tiene tal cosa, en su almacén tiene tal cosa”, para que haga los trueques. Y después le decimos: “esta es tu lista de bonos; actualmente tenés cero, pero cuando intercambiás un producto...”. Ahí hay que crear un script.

**Rodrigo:** El simulador que me mostraste, ¿qué tenía?

**Hernán:** Claude me hizo un simulador en JSX. Tiene tipos de actores: activo, pasivo, free rider, inactivo. Un motor de simulación. Cantidad: 40 activos, 30 pasivos, 15 free riders. Créditos al inscribirse. Duración del ciclo: cuatro semanas. “Simular ciclo”. El resultado decía “mercado saludable” y que algunos superaron su compromiso y ganaron tokens. Si aumentás la cantidad de free riders, la dinámica se obstruye. Habría que ver cómo hace los cálculos; eso te desconozco. Es estadística pura, basada en probabilidades y cantidades, sin demanda. Después el cálculo supongo que es en base a la cantidad de activos y pasivos.

**Rodrigo:** Lo ideal va a ser simularlo con IA, que los agentes interactúen entre ellos y se pongan a intercambiar, ver en cuántos días se hicieron tantos intercambios, cómo se movió la economía, si creció, bajó. Y también qué tipo de atajos quieren crear, porque la IA, cuando le das libertad, engaña. En la simulación de Minecraft se dieron cuenta de que había sociedad: crearon una sociedad de 100 agentes y algunos creaban un monopolio, otros un comercio, otros se dedicaban a matar gente de la nada para robarle los tokens. En este caso no tendría sentido, pero sí que crean ser personas.

**Hernán:** Lo que estaría bueno es analizar con qué nivel de participación optimista, neutra, especulativa y escéptica va funcionando. Si son 25 y 55, pasa tal cosa. Si ponemos un 10 de esto... El sistema va a ir cayéndose a medida que disminuya la participación comprometida y optimista y aumente la especulativa.

**Rodrigo:** En este tipo de simulación no manejás estadísticas, manejás **personalidades**, porque al fin y al cabo vamos a manejar personas. A uno le ponés que es de los más detractores del mundo cripto, pero se da cuenta de su bondad y al final hace crecer el sistema. Puede cambiar la personalidad. Eso depende de la temperatura. ¿Te acordás que habíamos hablado con el profe? Le das una temperatura para que no actúe en base a reglas fijas. Para este caso no lo queremos en temperatura uno; lo queremos en menor temperatura para que sea un poco más dinámico, que un día piense una cosa y al otro día otra. Se puede tener un diálogo, una mesa de diálogo general o un diálogo entre dos personas, que van intercambiando, se van convenciendo. La idea no es que solamente intercambien, sino que esté vivo, que intercambien ideas, pensamientos. Si no, con esta calculadora ya lo tenemos y no nos va a dar este resultado.

**Hernán:** ¿Y qué modelos usarías?

**Rodrigo:** DeepSeek tiene límites: el último permite 43.000 llamadas cada cinco horas. Cada llamada es un diálogo. Entre 10 personas, tal vez nos gastamos las 43.000 en cinco horas. Yo probaría primero con este, que vale 15.000 pesos para hacer la prueba inicial, y si cacheamos, se pueden tener 86.000 conversaciones. Como van a ser personas, deberían conservar su memoria, sus diálogos. Si pega el caché, llegás a 86.000 ejecuciones de diálogo, incluido el pensamiento. Hay modelos gratis con casi 100.000 llamadas; no son los más inteligentes, pero para algo gratis sería lo ideal.

**Hernán:** Sí, usaría los gratis para la prueba inicial.

## 13. Archivos, contactos y próximos pasos

**Hernán:** A la idea le puse **Aldea** en su momento.

**Rodrigo:** Me encanta.

**Hernán:** Te voy a mandar los archivos. Está el modelo original de moneda social, que empecé por 2016 y fui renovando hasta 2023-2024. Después están los que se llaman **Aldea**, los últimos que hice con Clau, buscando un pitch empresarial y una aproximación técnica. En uno está el token de recompensa solamente como modelo, sin el token; en el otro está el token de recompensa mencionado. También te mando el simulador JSX que me hizo Claude. No soy un recanchero [sic] con la IA; muy básico lo que podía promptear.

**Rodrigo:** Mandámelos. Los abro en el editor y vemos si podemos ejecutar el simulador. [...]

**Hernán:** También está la posibilidad de un **ingreso básico universal** mínimo: tal vez esa persona no tiene nada que intercambiar, o tiene pero no le alcanza. Para mover la rueda mensualmente, entregarle un bono que represente, no sé, 10.000 pesos. Esa es la idea que está en el pitch: un token de recompensa en paralelo, como compensación por participar. Lo pensaba como incentivo para que uno quiera meterse al sistema con cosas que dejen de usar ciertos criterios de oferta y demanda. “Yo entro, la primera vez oferté clases particulares de primaria y no conseguí nada; solamente me gasté los tokens que tenía. Ahora ingreso de vuelta, pero vi que hay más demanda de clases de inglés, entonces doy clases de inglés”. Eso incentiva a ofertar cosas que sean demandadas y hace prosperar el sistema. Pero ahí hay que calcular quién lo emite, cómo lo emite y qué valor tiene. Es muy complejo.

Incluso pensé: si lo hiciera a través de una sociedad, una empresa con cierto patrimonio que desarrolla esto y emite un token fiduciario, lo pondría en valor tierra. El valor de una hectárea de tierra está fragmentado en tantos tokens y está girando. Si la tierra aumenta su valor, o la empresa puede comprar más tierra, emite más tokens y se reparte más cantidad entre los participantes que cumplen y le dan dinámica al sistema. O les da acciones de la empresa. Se me ocurrían cosas así.

**Rodrigo:** ¿En Azul o en otro lado?

**Hernán:** Yo buscaría un sector con más dinámica, más en el conurbano. Hay más economía social y más dinámica. Ahí se consiguen rápidamente 200, 300 usuarios. En Azul la economía es más depresiva y todos producen lo mismo. Pero también hay que ver los contactos: conozco gente que conoce gente. Me interesaba esta chica que tiene contactos. Y hay una abogada, Moisés, que está hasta las manos. [...]

**Hernán:** Bueno, te mando todo por WhatsApp.

**Rodrigo:** Dale. [...]

---

## Cierre editorial

La llamada no termina con decisiones formales: termina con un **acuerdo de intercambio de archivos** y la idea de probar el modelo con una simulación antes de construir el MVP. Las propuestas que quedan abiertas se registran en [[04 - Reuniones/2026/11-Noviembre/2026-11-20 - Llamada con Hernan - Apuntes|Apuntes de la llamada]] y en el registro de decisiones.

## Enlaces

- [[04 - Reuniones/2026/11-Noviembre/2026-11-20 - Llamada con Hernan - Apuntes|Apuntes de la llamada]]
- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
- [[03 - Direccion y Estrategia/2026-11 - Documento Ejecutivo Aldea|Documento Ejecutivo Aldea]]
- [[16 - Archivo/2026/transcripcion_original.txt|Transcripción original]]
