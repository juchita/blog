---
Description: "Sysarmy - Comunidad de sistemas"
Keywords:
- sysadmin 
- sistemas
- desarrollo
- developer
- administración de sistemas
- administrador de sistemas
- linux
- cloud
- docker
- kubernetes
Section: 
Slug: como-funciona-netflix-el-complejo-proceso-en-terminos-sencillos
Tags:
- sysarmy
Thumbnail: /blog/assets/https3a2f2fcdn-images-1-medium-com2fmax2f16002f04q74mywyhitabob1-jpg.jpeg
Title: Cómo funciona Netflix - el complejo proceso en términos sencillos
Topics:
- Development
- Leadership
- Systems
Url: 2017/12/06/como-funciona-netflix-el-complejo-proceso-en-terminos-sencillos
date: 2017-12-06
markup: html
---


<p><em>Artículo original en inglés: <a href="https://medium.com/refraction-tech-everything/how-netflix-works-the-hugely-simplified-complex-stuff-that-happens-every-time-you-hit-play-3a40c9be254b" target="_blank" rel="noopener">https://medium.com/refraction-tech-everything/how-netflix-works-the-hugely-simplified-complex-stuff-that-happens-every-time-you-hit-play-3a40c9be254b</a></em></p>

<p>{{< figure src="assets/image.png" link="assets/image.png" >}}</p>

<p>Hace poco volvió <i>Stranger Things</i> con su segunda temporada y se puso fin a la larga espera que tenía en vilo a todos los amantes de la ciencia ficción. Para estas personas, empezar una maratón es algo tan sencillo como disponer de un dispositivo o un control remoto, abrir la aplicación de Netflix y apretar “Reproducir”. Una gratificación sencilla, rápida e instantánea.</p>
<p>Lo que no resulta tan sencillo es todo el proceso que se pone en marcha al ejecutar Netflix, un servicio que transmite alrededor de 250 millones de horas de video por día a 98 millones de suscriptores en 190 países. En este contexto, ofrecer entretenimiento de calidad en cuestión de <i>pocos segundos</i> a cada usuario no es cualquier cosa. Y, si bien se traduce en crear una infraestructura de primera categoría a una escala nunca antes vista en un servicio de Internet, también implica que hay que negociar y mantener contentos a todos los participantes de esta experiencia, desde las empresas de producción que distribuyen el contenido, hasta los proveedores de Internet que tienen que hacer frente al intenso tráfico en la red generado por Netflix.</p>
<p>A continuación, en pocas palabras y en los términos más simples, te contamos cómo funciona Netflix.</p>
<hr />

<p>{{< figure src="assets/https3a2f2fcdn-images-1-medium-com2fmax2f20002f1m-o7evqhtuhwo2muv71eww.png" link="assets/https3a2f2fcdn-images-1-medium-com2fmax2f20002f1m-o7evqhtuhwo2muv71eww.png" >}}</p>

       Dave Hahn, Sr. Engineer del Departamento de Cloud Operations &amp; Reliability Engineering de Netflix, muestra la arquitectura completa de la empresa en un diagrama de flujo. (Amazon Web Services/YouTube)</h6>
<p>&nbsp;</p>
<h2>Cientos de microservicios englobados en un servicio gigante</h2>
<p>Para comprender cómo se estructura Netflix desde el punto de vista tecnológico, lo vamos a ilustrar con un ejemplo.</p>
<p>Vamos a suponer que la aplicación Mapas de tu celular rastrea tu ubicación todo el tiempo y guarda información compleja sobre los lugares a los que vas en un archivo, <i>ubicaciones.txt</i>. A su vez, creás una aplicación a la que llamás LocoList que, si Mapas está instalada en tu teléfono, levanta el archivo <i>ubicaciones.txt</i> y muestra todos los lugares grabados en ese archivo como una lista sencilla. Funciona sin el más mínimo error.</p>
<p>Bien, digamos ahora que los desarrolladores de Mapas se dan cuenta de que es mejor guardar esa información en un lugar diferente y lanzan una actualización que ya no crea ni guarda el archivo <i>ubicaciones.txt</i> en tu teléfono. De esta manera, LocoList ya no puede localizar este archivo del que depende toda su información y tampoco existe otra manera en que pueda extraer la información desde Mapas. LocoList deja de funcionar. Fuiste.</p>
<p>Todo el tiempo invertido en LocoList se fue al tacho porque un cambio que se realizó en Mapas dejó inservible a tu aplicación. Si bien a esta escala no parece un asunto grave, si lo pasamos a la escala de un servicio enorme como Netflix, que la aplicación entera quede en desuso porque se realizó un cambio no solo puede arruinarle la experiencia a los usuarios, también significa que hay que reescribir el resto de las partes de la aplicación para adaptarse a ese pequeño cambio que realizaste. Esta estructura es lo que llamamos <i>arquitectura monolítica. </i></p>
<p>Netflix marcó literalmente el inicio de una revolución hace diez años al reescribir las aplicaciones que ejecutan la totalidad del servicio bajo una <i>arquitectura de microservicios</i>, lo que implica que cada aplicación, o el código y los recursos de cada <i>microservicio</i>, son independientes. Por principio, no comparten el código con otras aplicaciones. Entonces, cuando dos aplicaciones necesitan comunicarse, usan una <i>interfaz de programación de aplicaciones </i>(API, por sus siglas en inglés), un conjunto de reglas muy controladas que los dos programas pueden manejar. De esta forma, los desarrolladores pueden hacer numerosos cambios en cada aplicación, sean mínimos o exhaustivos, siempre y cuando se aseguren de que se respeta la API. Dado que los programas conocen bien la API del otro, las modificaciones no van a interrumpir el intercambio de información.</p>
<p>Netflix estima que utiliza alrededor de 700 microservicios para controlar cada una de las numerosas partes que conforman la totalidad del servicio: un microservicio guarda todos los programas que viste, otro debita la suscripción mensual de tu tarjeta de crédito, otro le brinda a tu dispositivo los archivos de video correctos para que pueda reproducirlos, otro evalúa tu historial de programas vistos y usa algoritmos para generar una lista de películas que te pueden gustar, otro te brinda los nombres y las imágenes de esas películas para que se vean en una lista en el menú principal. Y esto es tan solo la punta del iceberg. Los ingenieros de Netflix pueden modificar cualquier parte de la aplicación para introducir cambios nuevos de forma rápida y sin que ninguna otra parte del servicio se interrumpa.</p>
<p>En conclusión ¿por qué una arquitectura de microservicios es tan importante para Netflix? Bien, estos son los resultados obtenidos gracias a elegir esta arquitectura:</p>

<p>{{< figure src="assets/https3a2f2fcdn-images-1-medium-com2fmax2f20002f1d05id2iyngxnlcbp9alkcg.png" link="assets/https3a2f2fcdn-images-1-medium-com2fmax2f20002f1d05id2iyngxnlcbp9alkcg.png" >}}</p>

<h2>Amazon Web Services/YouTube</h2>
<p>Cientos de microservicios, miles de cambios diarios en la producción, decenas de miles de instancias, cientos de miles de interacciones de clientes por minuto, millones de clientes, mil millones de métricas, diez mil millones de horas de visualización. <b>Una decena de ingenieros de operaciones</b>.</p>

<p>{{< figure src="assets/https3a2f2fcdn-images-1-medium-com2fmax2f20002f0ks4owh9ze8lp3qv5-jpg.jpeg" link="assets/https3a2f2fcdn-images-1-medium-com2fmax2f20002f0ks4owh9ze8lp3qv5-jpg.jpeg" >}}</p>

<h6>Un Datacenter en Frankfurt, Alemania. (Nils Juenemann/nilsjuenemann.de)</h6>
<h2><b>¿Dónde se ejecutan todos estos microservicios? </b></h2>
<p>Para que todo esto funcione se necesita una red masiva de servidores. En el pasado eran propiedad de Netflix, pero dado el paso vertiginoso con el que crecían y sumado a la necesidad de dar continuidad a ese crecimiento, llegaron a la conclusión de que las cosas se iban a complicar si se abocaban a construir sistemas informáticos capaces de dar soporte a su software, con el consiguiente trabajo de correcciones y modificaciones para adaptarlos a sus necesidades. Por lo tanto, tomaron la valiente decisión de <i>deshacerse del mantenimiento de sus servidores </i>y subieron toda la información a la nube. O sea, todo se ejecuta desde servidores externos que se hicieron cargo del mantenimiento del hardware, lo que le permitió a los ingenieros de Netflix crear cientos de programas e instalarlos de forma rápida en los servidores. Los servidores externos elegidos para la infraestructura basada en la nube son los de Amazon Web Services (AWS).</p>
<p>Un momento. <i>¿Amazon? ¿Los tipos esos que también ejecutan Prime Video? ¿Cómo van a dejar <b>todo el servicio</b></i> <i>en manos de un archirrival? </i></p>
<p>Bueno, son muchas las empresas que tienen una especie de acuerdo de caballeros en los que se comprometen a trabajar para el otro a pesar de competir en la misma categoría. Un buen ejemplo es lo que ocurre entre Samsung y Apple, que compiten en el ámbito de los teléfonos móviles y, al mismo tiempo, las piezas más esenciales del iPhone son manufacturadas por el gigante coreano. Netflix fue cliente de AWS antes de la aparición de Prime Video. Que ahora sean competidores no implica que se instale una hostilidad entre ellos.</p>
<p>Tal como se desarrollaron los eventos, la alianza entre Netflix y Amazon resultó ser una situación en la que todos salieron beneficiados. Netflix se convirtió en uno de los clientes más importantes de AWS, impulsándolos a desarrollar sus capacidades al máximo y a innovar constantemente en las formas de utilizar los diferentes servidores de AWS para los distintos usos (ejecutar los microservcios, guardar películas, manejar el tráfico en internet) hasta sacar el mayor provecho posible. Por su parte, AWS mejoró sus sistemas para permitir que Netflix realizara cargas masivas en sus servidores, así como también permitió un uso mucho más flexible de sus productos y, por último, utilizó toda la toda la experiencia ganada y la puso al servicio de las necesidades de miles de otros clientes. Por un lado, AWS se jacta de que Netflix es su cliente más importante; por el otro, Netflix tiene la posibilidad de mejorar en forma rápida sus servicios y de mantenerlos estables gracias a AWS. Y esto se da, incluso, si Netflix le quita popularidad a Prime Video, o viceversa.</p>
<hr />

<p>{{< figure src="assets/https3a2f2fcdn-images-1-medium-com2fmax2f16002f0ntnj87imozw3kdgg.png" link="assets/https3a2f2fcdn-images-1-medium-com2fmax2f16002f0ntnj87imozw3kdgg.png" >}}</p>

<h6>ScaleScale/scalescale.com</h6>
<h2><b>El largo camino desde el rollo a la pantalla</b></h2>
<p>¿Qué utilidad podría tener un servicio de transmisión de programas de televisión y películas sin, por supuesto, programas de televisión y películas para transmitir? Para Netflix, el camino entre el productor de la película y el cliente es un proceso largo y arduo:</p>
<ul>
<li>Si se trata de un programa o película que no es producido por ellos (es decir, no es una serie original de Netflix), tienen que negociar los derechos de reproducción con las empresas que se encargan de distribuir el material. Esto significa que tienen que pagar una suma de dinero importante a cambio de los derechos legales que permiten que sus clientes en las diferentes regiones del mundo puedan reproducir el contenido. Con frecuencia, la empresa que distribuye el material (o hasta incluso Netflix) puede haber firmado contratos de exclusividad con otro servicio de video o canal de televisión en determinadas regiones, lo que implica que Netflix puede no estar autorizado a distribuir el servicio a esos clientes, o va a poder hacerlo en una fecha posterior. Por ejemplo, esta fue la razón por la que el estreno de la quinta temporada de <i>House of Cards en el Oriente Medio se retrasó hasta el 30 de junio, un mes entero más tarde en comparación con el resto de los más de 150 países que disfrutaron el show a partir del 30 de mayo.</i></li>
<li>Guarda las copias digitales originales del programa o de la película en los servidores de AWS. Estas copias se guardan en alta definición, como la de los cines, y Netflix tendrá que procesar ese contenido antes de que alguien lo pueda ver.</li>
<li>Netflix funciona en miles de dispositivos y cada uno de ellos reproduce el contenido en un formato de video y archivo de sonido distinto. Se destina otro conjunto de servidores AWS que toman el archivo original de video y lo convierten en cientos de archivos, cada uno con el objetivo de reproducir la totalidad de un programa o película en un tipo particular de dispositivo y en un tamaño de pantalla o calidad de video determinados. Un archivo va a funcionar exclusivamente para iPad, otro para el teléfono Android en full HD, otro para una TV Sony que puede reproducir video a 4K y sonido Dolby, otro para una computadora con Windows, etcétera. Se pueden crear más archivos con calidad de video variables para simplificar el proceso de carga en una conexión de Internet pobre. Esto es lo que se denomina <i>transcodificar. Además, se agrega a los archivos una porción de código especial para restringirlos con lo que se conoce como <i>gestión de derechos digitales (DRM, por sus siglas en inglés), una medida tecnológica contra la piratería. </i></i></li>
<li>La aplicación o el sitio web de Netflix determina qué tipo de dispositivo estás usando y busca el archivo exacto para el programa que querés ver. Ese archivo se creó exclusivamente para las reproducciones en tu dispositivo, con una calidad de video determinada por la velocidad de tu conexión a Internet en ese momento.</li>
</ul>
<p>Este último paso, el de buscar el archivo indicado, es fundamental porque, a fin de cuentas, es en este momento en que Internet entrega el video desde los servidores AWS al dispositivo del cliente. Si no funciona de forma correcta o no se realiza el mantenimiento necesario, el resultado puede ser un servicio muy lento o que no funcione, y esto sería en los hechos el fin de la empresa. Internet es el cordón umbilical que conecta a Netflix con sus clientes y entregar el contenido que el usuario desea en el menor tiempo posible es un trabajo que les insume mucho esfuerzo. Todo esto ocurre en una red muy concurrida, en la que millones de servicios compiten por su lugar.</p>
<h2><b>La carrera en contra del margen de tiempo</b></h2>

<p>{{< figure src="assets/https3a2f2fcdn-images-1-medium-com2fmax2f16002f0fwefhrv6nludifrl.png" link="assets/https3a2f2fcdn-images-1-medium-com2fmax2f16002f0fwefhrv6nludifrl.png" >}}</p>

<h6>Una síntesis de CDN (CDN Reviews/cdnreviews.com)</h6>
<p>El espectro completo de operaciones que forman parte del ecosistema de Netflix (el software, el contenido y la tecnología) se vuelve inservible si la conexión de Internet del usuario final es muy pobre para soportar la calidad de video. En líneas generales, Internet funciona de esta manera: cuando hacés alguna cosa que necesita acceso a la red, se envía una <i>solicitud</i> a tu proveedor de servicios de Internet (ISP, por sus siglas en inglés). El ISP envía esa solicitud a los servidores de destino que maneja el sitio web, y esos servidores generan una <i>respuesta</i> que se repite en tu computadora y le da forma al resultado. Para Netflix y otros sitios de primer nivel, en los que se repiten millones de horas de contenido de video a lo largo de Internet entre los servidores y los usuarios, hace falta una red de servidores mucho más amplia para que el servicio funcione de forma correcta. Esto se logra gracias a la Red de entrega de contenidos (CDN, por sus siglas en inglés).</p>
<p>Básicamente, las CDN toman el sitio web original y el contenido que se encuentra en el sitio, y lo copian a lo largo de cientos de servidores localizados en todo el mundo. Por lo tanto, cuando iniciás sesión desde Budapest, en vez de conectarse al servidor principal de Netflix en los Estados Unidos, se va a cargar una copia igual de ese contenido ubicada en el servidor CDN más cercano a Budapest. De esta manera, se reduce en gran medida la latencia (el tiempo entre una solicitud y una respuesta) y todo se carga con mucha velocidad. Los CDN son la razón por la que los sitios web con un número enorme de usuarios como Google, Facebook o YouTube son capaces de cargar contenido con rapidez, sin importar dónde estés o con qué velocidad de Internet contás.</p>

<p>{{< figure src="assets/https3a2f2fcdn-images-1-medium-com2fmax2f16002f04q74mywyhitabob1-jpg.jpeg" link="assets/https3a2f2fcdn-images-1-medium-com2fmax2f16002f04q74mywyhitabob1-jpg.jpeg" >}}</p>

<h6>Las cajas Open Connect de Netflix, que se entregan a los proveedores de internet. (NDTV Gadgets360/gadgets.ndtv.com)</h6>
<p>En un principio, Netflix utilizaba una variedad de redes CDN operadas por gigantes como Akamai, Level 3 y Limelight Networks. Sin embargo, el crecimiento en la cantidad de usuarios se tradujo en la necesidad de entregar mayor cantidad de contenido a más lugares y, al mismo tiempo, a costos más bajos. En consecuencia, crearon su propia CDN: <b>Open Connect</b>.</p>
<p>En este caso, en lugar de utilizar los servidores AWS, instalaron sus propios servidores alrededor del mundo. Pero estos servidores tienen un único propósito: guardar contenido de forma eficiente y entregarlo a los usuarios. Netflix cierra acuerdos con proveedores de servicios de Internet y les entrega la caja roja que se ve en la foto superior sin costo alguno. Los proveedores las instalan junto con sus servidores. Estas cajas <i>Open Connect</i> descargan la librería de Netflix de esa región desde los servidores principales en los Estados Unidos. En los casos en que existen múltiples servidores, cada uno va a guardar el contenido más popular entre los usuarios de la región para darle prioridad a la velocidad. Por lo tanto, es probable que una película poco popular tarde más en cargarse que un episodio de <i>Stranger Things</i>. Ahora bien, cuando te conectás a Netflix, la caja <i>Open Connect</i> más cercana a vos te envía el contenido que necesitás y, por lo tanto, los videos se van a cargar mucho más rápido que si la aplicación lo cargara desde el servidor principal.</p>
<p>Se puede considerar a las cajas como discos duros ubicados en todo el mundo que guardan videos y, mientras más cerca estén, más rápido vas a poder bajar y cargar el contenido. Se esconden muchos otros trucos tras bambalinas: como se explica en <a href="https://scaleyourcode.com/interviews/interview/11" target="_blank" rel="noopener">esta entrevista</a> (en inglés), cada vez que reproducís un programa, Netflix localiza las diez cajas <i>Open Connect</i> más cercanas a vos que ya cargaron el programa. El sitio web o la aplicación de Netflix intentarán a continuación detectar cuál de estas cajas es la más cercana o funciona más rápido de acuerdo a tu conexión de Internet para luego cargar el video desde esa ubicación. Esta es la razón por la que los videos se ven al comienzo borrosos pero se vuelven nítidos de repente: Netflix cambia de servidor hasta conectarse con ese que te va a brindar la mejor calidad de video.</p>
<hr />

<p>{{< figure src="assets/https3a2f2fcdn-images-1-medium-com2fmax2f20002f1bjv-jh_v8m3wjrpf1ucsnw.png" link="assets/https3a2f2fcdn-images-1-medium-com2fmax2f20002f1bjv-jh_v8m3wjrpf1ucsnw.png" >}}</p>

<h6> Captura de pantalla del autor</h6>
<h2><b>En pocas palabras…</b></h2>
<p>Esto es lo que ocurre cada vez que reproducís un video en Netflix:</p>
<ul>
<li>Cientos de microservicios, o pequeños programas independientes, trabajan en conjunto para conformar un gran servicio: Netflix</li>
<li>El contenido, que fue adquirido de forma legal o que cuenta con licencia de reproducción, se convierte a un tamaño determinado por tu pantalla y se lo protege contra la piratería.</li>
<li>Una serie de servidores ubicados en todo el mundo hacen una copia del contenido y lo guardan para que el servidor más cercano a vos te lo entregue con la máxima calidad y velocidad posibles.</li>
<li>Cuando elegís un programa, la aplicación de Netflix va de servidor en servidor hasta encontrar el que va a cargar el video.</li>
<li>Así, te deprimís con la vida de locos de BoJack Horseman, te deleitás con Dev en <i>Master of None y desarrollás una fobia al futuro de la tecnología con las historias de <i>Black Mirror. Tu vida se acorta a expensas de las maratones de series y te volvés en una bolsa de papas, tirado todo el día en el sillón. </i></i></li>
</ul>
<p>Parecía tan sencillo, ¿no?</p>
<p>&nbsp;</p>
<hr />
<p><em>Artículo original en inglés: <a href="https://medium.com/refraction-tech-everything/how-netflix-works-the-hugely-simplified-complex-stuff-that-happens-every-time-you-hit-play-3a40c9be254b" target="_blank" rel="noopener">https://medium.com/refraction-tech-everything/how-netflix-works-the-hugely-simplified-complex-stuff-that-happens-every-time-you-hit-play-3a40c9be254b</a></em></p>
<p>&nbsp;</p>
