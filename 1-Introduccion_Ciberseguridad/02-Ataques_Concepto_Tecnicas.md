<a href="./00-Curso.md"><< Menú principal del módulo</a>

# 2. Ataques, conceptos y técnicas

## Analizando un Ciberataque

### Tipos de malware
Los ciberdelincuentes utilizan muchos tipos diferentes de software malicioso, o malware, para llevar a cabo sus actividades. El malware es cualquier código que se puede utilizar para robar datos, eludir los controles de acceso o causar daño o comprometer un sistema. Saber cuáles son los diferentes tipos y cómo se propagan es clave para contenerlos y eliminarlos.

* __Spyware__

<div align="center">
	<div style="width: 900px;">
	<img src="./img/spyware.png" style="float: left;width: 300px;" />
	<p style="width: 500px;" align="left">
		Diseñado para rastrearlo y espiarlo, el software espía monitorea su actividad en línea y puede registrar cada tecla que presiona en el teclado, así como capturar casi todos sus datos, incluida información personal confidencial, como sus datos bancarios en línea. El software espía lo hace modificando la configuración de seguridad de sus dispositivos.
		El spyware con frecuencia se agrupa con el software legítimo o con caballos troyanos.
	</p>
</div>
<div align="left" style="visibility: hidden;">h</div>
<br />
<br />

* <div align="left"><b>Adware</b></div>

<div align="center">
	<div style="width: 900px;">
	<img src="./img/adware.png" style="float: left;width: 300px;" />
	<p style="width: 500px;" align="left">
		El adware a menudo se instala con algunas versiones de software y está diseñado para entregar automáticamente anuncios a un usuario, la mayoría de las veces en un navegador web. ¡Lo sabes cuando lo ves! Es difícil ignorarlo cuando te enfrentas a anuncios emergentes constantes en tu pantalla.
		Es común que el adware venga con spyware.
	</p>
</div>
<div align="left" style="visibility: hidden;">h</div>
<br />
<br />

* <div align="left"><b>Puerta trasera</b></div>

<div align="center">
	<div style="width: 900px;">
	<img src="./img/puerta_trasera.png" style="float: left;width: 300px;" />
	<p style="width: 500px;" align="left">
		Este tipo de malware se utiliza para obtener acceso no autorizado al omitir los procedimientos de autenticación normales para acceder a un sistema. Como resultado, los hackers pueden obtener acceso remoto a los recursos de una aplicación y emitir comandos remotos del sistema.
		Una puerta trasera funciona en segundo plano y es difícil de detectar.
	</p>
</div>
<div align="left" style="visibility: hidden;">h</div>
<br />
<br />

* <div align="left"><b>Ransomware</b></div>

<div align="center">
	<div style="width: 900px;">
	<img src="./img/ransomware.png" style="float: left;width: 300px;" />
	<p style="width: 500px;" align="left">
		El malware está diseñado para mantener cautivo un sistema computacional o los datos que contiene hasta que se realice un pago. El ransomware generalmente funciona cifrando sus datos para que no pueda acceder a ellos.
		Algunas otras versiones de ransomware pueden aprovechar vulnerabilidades específicas del sistema para bloquearlo. El ransomware a menudo se propaga a través de correos electrónicos de phishing que lo alientan a descargar un archivo adjunto malicioso o a través de una vulnerabilidad.
	</p>
</div>
<div align="left" style="visibility: hidden;">h</div>
<br />
<br />

* <div align="left"><b>Scareware</b></div>

<div align="center">
	<div style="width: 900px;">
	<img src="./img/scareware.png" style="float: left;width: 300px;" />
	<p style="width: 500px;" align="left">
		Este es un tipo de malware que utiliza tácticas de "miedo" para engañarlo para que tome una acción específica. El scareware consiste principalmente en ventanas emergentes que aparecen para advertirle que su sistema está en riesgo y necesita ejecutar un programa específico para que vuelva a funcionar normalmente.
		Si acepta ejecutar el programa específico, su sistema se infectará con malware.
	</p>
</div>
<div align="left" style="visibility: hidden;">h</div>
<br />
<br />

* <div align="left"><b>Rootkit</b></div>

<div align="center">
	<div style="width: 900px;">
	<img src="./img/rootkit.png" style="float: left;width: 300px;" />
	<p style="width: 700px;" align="left">
		Este malware está diseñado para modificar el sistema operativo para crear una puerta trasera, que los atacantes pueden usar para acceder a su computadora de forma remota. La mayoría de los rootkits aprovecha las vulnerabilidades de software para ganar acceso a recurso que normalmente no debería ser accesibles (escalada de privilegios) y modificar los archivos del sistema.
		Los rootkits también pueden modificar las herramientas de monitoreo y análisis forense del sistema, lo que los hace muy difíciles de detectar. En la mayoría de los casos, un equipo infectado por un rootkit debe borrarse y reinstalarse cualquier software necesario.
	</p>
</div>
<div align="left" style="visibility: hidden;">h</div>
<br />
<br />

* <div align="left"><b>Virus</b></div>

<div align="center">
	<div style="width: 900px;">
	<img src="./img/virus.png" style="float: left;width: 300px;" />
	<p style="width: 800px;" align="left">
		Un virus es un tipo de programa informático que, cuando se ejecuta, se replica y se adjunta a otros archivos ejecutables, como un documento, insertando su propio código. La mayoría de los virus requieren la interacción del usuario final para iniciar la activación y se pueden escribir para que actúen en una fecha u hora específica.
		Los virus pueden ser relativamente inofensivos, como los que muestran una imagen divertida. O pueden ser destructivos, como los que modifican o eliminan datos.
		Los virus también pueden programarse para mutar a fin de evitar la detección. La mayoría de los virus ahora se esparcen por unidades USB, discos ópticos, recursos de red compartidos o correo electrónico.
	</p>
</div>
<div align="left" style="visibility: hidden;">h</div>
<br />
<br />

* <div align="left"><b>Troyano</b></div>

<div align="center">
	<div style="width: 900px;">
	<img src="./img/troyano.png" style="float: left;width: 300px;" />
	<p style="width: 500px;" align="left">
		Este malware lleva a cabo operaciones maliciosas al enmascarar su verdadera intención. Puede parecer legítimo pero, de hecho, es muy peligroso. Los troyanos aprovechan sus privilegios de usuario y se encuentran con mayor frecuencia en archivos de imagen, archivos de audio o juegos.
		A diferencia de los virus, los troyanos no se replican a sí mismos, sino que actúan como señuelo para colar software malicioso a los usuarios desprevenidos.
	</p>
</div>
<div align="left" style="visibility: hidden;">h</div>
<br />
<br />

* <div align="left"><b>Gusanos</b></div>

<div align="center">
	<div style="width: 900px;">
	<img src="./img/gusanos.png" style="float: left;width: 300px;" />
	<p style="width: 800px;" align="left">
		Este es un tipo de malware que se replica a sí mismo para propagarse de un ordenador a otro. A diferencia de un virus, que requiere un programa anfitrión para ejecutarse, los gusanos pueden ejecutarse por sí mismos. Aparte de la infección inicial del host, no requieren la participación del usuario y pueden propagarse muy rápidamente por la red.
		Los gusanos comparten patrones similares: aprovechan las vulnerabilidades del sistema, tienen una forma de propagarse y todos contienen código malicioso (carga útil) para dañar los sistemas informáticos o las redes.
		Los gusanos son responsables de algunos de los ataques más devastadores en Internet. En 2001, el gusano Code Red había infectado más de 300.000 servidores en solo 19 horas.
	</p>
</div>
<div align="left" />
<br />

### Síntomas de malware
Independientemente del tipo de malware con el que se ha infectado un sistema, estos son síntomas frecuentes de malware. Entre ellos se encuentran:

* Un aumento en el uso de la unidad de procesamiento central (CPU), lo que ralentiza el dispositivo.
* El equipo se congela o se bloquea con frecuencia.
* Una disminución en la velocidad de navegación web.
* Problemas inexplicables con las conexiones de red
* Archivos modificados o eliminados.
* Una presencia de archivos, programas o iconos de escritorio desconocidos.
* Se ejecutan procesos o servicios desconocidos.
* Los programas se cierran o reconfiguran solos.
* Se envían correos electrónicos sin el conocimiento o el consentimiento del usuario.

## Métodos de infiltración

### Ingeniería social
La ingeniería social es la manipulación a las personas para que realicen acciones o divulguen información confidencial. Los ingenieros sociales con frecuencia dependen de la disposición de las personas para ayudar, pero también se aprovechan de sus vulnerabilidades. Por ejemplo, un atacante llamará a un empleado autorizado con un problema urgente que requiere acceso inmediato a la red y apelará a la vanidad o la codicia del empleado o invocará la autoridad mediante el uso de técnicas de eliminación de nombres para obtener este acceso.

* __Pretexto__: Esto es cuando un atacante llama a una persona y miente en el intento de obtener acceso a datos privilegiados. Por ejemplo, fingir que necesita los datos personales o financieros de una persona para confirmar su identidad.
* __Infiltración__ (_tailgating_): Esto es cuando un atacante sigue rápidamente a una persona autorizada a un lugar seguro.
* __Una cosa por otra__ (_quid pro quo_): Esto sucede cuando un hacker solicita información personal de una parte a cambio de algo, como un regalo gratis.

### Denegación de servicio (DoS)
Los ataques de denegación de servicio (DoS) son un tipo de ataque de red que es relativamente sencillo de llevar a cabo, incluso por parte de un atacante no cualificado. Un ataque DoS da como resultado cierto tipo de interrupción del servicio de red a los usuarios, los dispositivos o las aplicaciones.

* __Cantidad abrumadora de tráfico__: Esto es cuando se envía una gran cantidad de datos a una red, a un host o a una aplicación a una velocidad que no pueden procesar. Esto ocasiona una disminución de la velocidad de transmisión o respuesta o una falla en un dispositivo o servicio.
* __Paquetes maliciosos formateados__: Un paquete es una colección de datos que fluye entre una computadora o aplicación de origen y una receptora a través de una red, como Internet. Cuando se envía un paquete con formato malicioso, el receptor no puede manejarlo. Por ejemplo, si un atacante reenvía paquetes que contienen errores o paquetes formateados incorrectamente que no pueden ser identificados por una aplicación, esto hará que el dispositivo receptor funcione muy lentamente o se bloquee.

Los ataques de DoS se consideran un riesgo importante porque pueden interrumpir fácilmente la comunicación y causar una pérdida significativa de tiempo y dinero.

### DoS distribuido
Un ataque DoS distribuido (DDoS) es similar a un ataque DoS pero proviene de múltiples fuentes coordinadas. Por ejemplo:

* Un atacante crea una red (botnet) de hosts infectados llamados zombies, que son controlados por sistemas de manejo.
* Las computadoras zombis constantemente analizan e infectan más hosts, creando más y más zombis.
* Cuando está listo, el hacker proporciona instrucciones a los sistemas manipuladores para que los botnet de zombies lleven a cabo un ataque de DDoS.

### Botnet
Una computadora bot se infecta generalmente por visitar un sitio web, abrir un elemento adjunto de correo electrónico o abrir un archivo de medios infectado. Una botnet es un grupo de bots, conectados a través de Internet, que pueden ser controlados por un individuo o grupo malintencionado. Puede tener decenas de miles, o incluso cientos de miles, de bots que normalmente se controlan a través de un servidor de comando y control.

Estos bots se pueden activar para distribuir malware, lanzar ataques DDoS, distribuir correo electrónico no deseado o ejecutar ataques de contraseña por fuerza bruta. Los ciberdelincuentes suelen alquilar botnets a terceros con fines nefastos.

Muchas organizaciones, como Cisco, fuerzan las actividades de red a través de filtros de tráfico de botnet para identificar cualquier ubicación de botnet.

<div align="center">
	<img src="./img/botnet.svg" />
</div>

### Ataques en el camino
Los atacantes en ruta interceptan o modifican las comunicaciones entre dos dispositivos, como un navegador web y un servidor web, ya sea para recopilar información de uno de los dispositivos o para hacerse pasar por uno de ellos.

Este tipo de ataque también se conoce como ataque de hombre en el medio o de hombre en el móvil.

Un ataque _MiTM_ (_man in the middle_) ocurre cuando un ciberdelincuente toma el control de un dispositivo sin que el usuario lo sepa. Con ese nivel de acceso, el atacante puede interceptar y capturar información sobre el usuario antes de retransmitirla a su destino. Estos tipos de ataques se utilizan a menudo para robar información financiera. Hay muchos tipos de malware que poseen capacidades de ataque MiTM.

Una variación del hombre en el medio, el _MitMo_ (_man in the mobile_) es un tipo de ataque utilizado para tomar el control de un dispositivo móvil. Cuando está infectado, el dispositivo móvil recibe instrucciones de filtrar información confidencial del usuario y enviarla a los atacantes. ZeUS es un ejemplo de paquete de malware con capacidades MitMO. Permite a los atacantes capturar silenciosamente los mensajes SMS de verificación en dos pasos que se envían a los usuarios.

### Envenenamiento SEO
Probablemente hayas oído hablar de la optimización de motores de búsqueda o SEO que, en términos simples, se trata de mejorar el sitio web de una organización para que gane una mayor visibilidad en los resultados de los motores de búsqueda.

Los motores de búsqueda como Google funcionan presentando una lista de páginas web a los usuarios en función de su consulta de búsqueda. Estas páginas web se clasifican de acuerdo con la relevancia de su contenido.

Aunque muchas empresas legítimas se especializan en la optimización de sitios web para mejorar su posición, los atacantes utilizan el SEO para hacer que un sitio web malicioso aparezca más arriba en los resultados de la búsqueda. Esta técnica se denomina envenenamiento SEO.

El objetivo más común del envenenamiento de SEO es aumentar el tráfico a sitios maliciosos que pueden albergar malware o intentar ingeniería social.

### Descirado de contraseñas Wi-Fi
Disfrutas de tu almuerzo en la cantina cuando un colega se te acerca. Parecen angustiados.

Explican que parece que no pueden conectarse a la red Wi-Fi pública en su teléfono y preguntan si tiene la contraseña de Wi-Fi privada a mano para que puedan comprobar que su teléfono funciona.

¿Cómo respondería a esto? Este colega podría estar llevando a cabo un ataque de ingeniería social, manipulándolo para que proporcione la contraseña utilizada para proteger la red inalámbrica privada de la organización. Nunca puedes ser demasiado cuidadoso.

Los hackers tienen otras técnicas bajo la manga. Algunos usan ataques de fuerza bruta, probando posibles combinaciones de contraseñas para intentar adivinar una contraseña. Otros pueden identificar contraseñas sin cifrar escuchando y capturando los paquetes enviados en la red. Esto se denomina rastreo de red. Si la contraseña está cifrada, el atacante aún puede revelarla mediante una herramienta de decodificación de contraseñas.

### Ataques de contraseña
La introducción de un nombre de usuario y una contraseña es una de las formas más populares de autenticarse en un sitio web. Por lo tanto, descubrir su contraseña es una forma fácil para que los ciberdelincuentes accedan a su información más valiosa.

__Pulverización de contraseña__: Esta técnica intenta obtener acceso a un sistema "rociando" algunas contraseñas de uso común en un gran número de cuentas. Por ejemplo, un ciberdelincuente utiliza "Password123" con muchos nombres de usuario antes de volver a intentarlo con una segunda contraseña de uso común, como "qwerty". Esta técnica permite que el perpetrador permanezca sin ser detectado, ya que evita los bloqueos frecuentes de la cuenta.

__Ataques de diccionario__: Un hacker intenta sistemáticamente todas las palabras de un diccionario o una lista de palabras de uso común como contraseña en un intento de ingresar a una cuenta protegida con contraseña.

__Ataques de fuerza bruta__: Son la forma más simple y más utilizada de obtener acceso a un sitio protegido con contraseña. Los ataques de fuerza bruta ven a un atacante utilizando todas las combinaciones posibles de letras, números y símbolos en el espacio de contraseñas hasta que lo hacen bien.

__Ataques arco iris__: Las contraseñas de un sistema informático no se almacenan como texto sin formato, sino como valores con hash (valores numéricos que identifican datos de forma única). Una tabla arcoíris es un gran diccionario de valores hash precalculados y las contraseñas a partir de las cuales se calcularon. A diferencia de un ataque de fuerza bruta que tiene que calcular cada hash, un ataque de arco iris compara el hash de una contraseña con los almacenados en la tabla rainbow. Cuando un atacante encuentra una coincidencia, identifica la contraseña utilizada para crear el hash.

__Interceptación de tráfico__: El texto sin formato o las contraseñas sin cifrar pueden ser leídas fácilmente por otras personas y máquinas al interceptar las comunicaciones. Si almacena una contraseña en texto claro y legible, cualquier persona que tenga acceso a su cuenta o dispositivo, ya sea autorizado o no, podrá leerlo.

### Tiempos de craqueo
Parece que los hackers están intentando todo para descifrar la contraseña de Wi-Fi privada de @Apollo. ¡Tenemos que asegurarnos de que la contraseña sea lo suficientemente fuerte como para resistir su ataque!

Llevar a cabo ataques de fuerza bruta implica que el atacante intente varias combinaciones posibles en un intento de adivinar la contraseña. Estos ataques generalmente involucran un archivo de lista de palabras, un archivo de texto que contiene una lista de palabras de un diccionario. Un programa como Ophcrack, L0phtCrack, THC Hydra, RainbowCrack o Medusa probará cada palabra y combinación común hasta que encuentre una coincidencia.

Debido a que los ataques de fuerza bruta toman tiempo, las contraseñas complejas toman mucho más tiempo adivinar.

### Amenazas persistentes avanzadas
Los atacantes también logran infiltrarse a través de amenazas persistentes avanzadas (APT): una operación avanzada, sigilosa, de múltiples fases y a largo plazo contra un objetivo específico. Por estas razones, un atacante individual a menudo carece de las habilidades, los recursos o la persistencia para realizar APTs.

Debido a la complejidad y al nivel de habilidad requerido para llevar a cabo un ataque de este tipo, una APT generalmente está bien financiada y generalmente apunta a organizaciones o naciones por razones comerciales o políticas.

Su objetivo principal es implementar malware personalizado en uno o más de los sistemas del objetivo y permanecer allí sin ser detectado.

## Aprovechamiento de las vulnerabilidades de seguridad
Antes de entrar en detalles, comencemos por resumir algunos términos clave que debe conocer.

Las _vulnerabilidades de seguridad_ son cualquier tipo de defecto en software o hardware. Un programa escrito para aprovechar una vulnerabilidad de seguridad conocida se denomina _exploit_. Un ciberdelincuente puede utilizar un exploit contra una vulnerabilidad para llevar a cabo un _ataque_, cuyo objetivo es obtener acceso a un sistema, a los datos que aloja o a un recurso específico.

### Vulnerabilidades de hardware
Las vulnerabilidades de hardware se presentan a menudo mediante defectos de diseño del hardware. Por ejemplo, el tipo de memoria denominada RAM consiste básicamente en muchos condensadores (un componente que puede contener una carga eléctrica) instalados muy cerca unos de otros. Sin embargo, pronto se descubrió que, debido a su proximidad, los cambios aplicados a uno de estos condensadores podrían influir en los condensadores vecinos. Por esta falla de diseño, se generó un exploit llamada Rowhammer. Al acceder repetidamente (martillar) a una fila de memoria, el exploit Rowhammer desencadena interferencias eléctricas que eventualmente corrompen los datos almacenados dentro de la RAM

#### Meltdown y Spectre
Los investigadores de seguridad de Google descubrieron Meltdown y Spectre, dos vulnerabilidades de hardware que afectan a casi todas las unidades de procesamiento central (CPU) lanzadas desde 1995 en computadoras de escritorio, computadoras portátiles, servidores, teléfonos inteligentes, dispositivos inteligentes y servicios en la nube.

Los atacantes que explotan estas vulnerabilidades pueden leer toda la memoria de un sistema determinado (Meltdown), así como los datos manejados por otras aplicaciones (Spectre). Las explotaciones de vulnerabilidad Meltdown y Spectre se denominan ataques de canal lateral (la información se obtiene de la implementación de un sistema informático). Tienen la capacidad de comprometer grandes cantidades de datos de memoria porque los ataques se pueden ejecutar varias veces en un sistema con muy pocas posibilidades de que se produzca un bloqueo u otro error.

Las vulnerabilidades de hardware son específicas de los modelos de dispositivos y generalmente no se ven atacadas por intentos comprometedores aleatorios. Si bien las vulnerabilidades de hardware son más comunes en ataques altamente dirigidos, la protección tradicional contra malware y una buena seguridad física son una protección suficiente para el usuario cotidiano.

### Vulnerabilidades de software
Las vulnerabilidades de software suelen ser provocadas por errores en el sistema operativo o en el código de la aplicación.

La vulnerabilidad SynFUL Knock permitió a los atacantes obtener el control de los enrutadores de nivel empresarial, como los enrutadores ISR de Cisco, desde los cuales podían monitorear todas las comunicaciones de red e infectar otros dispositivos de red.

Esta vulnerabilidad se introdujo en el sistema cuando una versión alterada de IOS se instaló en los routers. Para evitar esto, verifique siempre la integridad de la imagen de IOS descargada y limite el acceso físico al equipo solo al personal autorizado.

### Categorización de vulnerabilidades de software
La mayoría de las vulnerabilidades de seguridad del software se dividen en varias categorías principales.

* __Desbordamiento de búfer__: Los búferes son áreas de memoria asignadas a una aplicación. Se produce una vulnerabilidad cuando los datos se escriben más allá de los límites de un búfer. Al cambiar los datos más allá de los límites de un búfer, la aplicación puede acceder a la memoria asignada a otros procesos. Esto puede provocar un bloqueo del sistema o comprometer los datos, o proporcionar una escalada de privilegios.
* __Entrada no validada__: Los programas a menudo requieren la entrada de datos, pero estos pueden tener contenido malicioso, diseñado para obligar al programa a comportarse de forma no deseada. Por ejemplo, considere un programa que recibe una imagen para procesarla. Un usuario malintencionado podría crear un archivo de imagen con dimensiones de imagen no válidas. Las dimensiones creadas maliciosamente podrían forzar al programa a asignar búferes de tamaños incorrectos e imprevistos.
* __Condiciones de carrera__: Esta vulnerabilidad describe una situación en la que la salida de un evento depende de salidas ordenadas o programadas. Una condición de carrera se convierte en una fuente de vulnerabilidad cuando los eventos ordenados o cronometrados requeridos no ocurren en el orden correcto o en el momento adecuado.
* __Debilidad en las Prácticas de Seguridad__: Los sistemas y los datos confidenciales se pueden proteger mediante técnicas como la autenticación, la autorización y el cifrado. Los desarrolladores deben ceñirse al uso de técnicas de seguridad y bibliotecas que ya hayan sido creadas, probadas y verificadas y no deben intentar crear sus propios algoritmos de seguridad. Es probable que solo introduzcan nuevas vulnerabilidades.
* __Problemas de control de acceso__: El control de acceso es el proceso de controlar quién hace qué y va desde administrar el acceso físico al equipo hasta dictar quién tiene acceso a un recurso, como un archivo, y qué pueden hacer con él, como leer o cambiar el archivo. Muchas vulnerabilidades de seguridad se generan por el uso incorrecto de los controles de acceso.

Casi todos los controles de acceso y las prácticas de seguridad pueden superarse si un atacante tiene acceso físico al equipo objetivo. Por ejemplo, independientemente de la configuración de permisos de un archivo, un hacker puede omitir el sistema operativo y leer los datos directamente del disco. Por lo tanto, para proteger la máquina y los datos que contiene, se debe restringir el acceso físico y se deben utilizar técnicas de cifrado para proteger los datos contra robos o corrupción.

### Actualizaciones de software
El objetivo de las actualizaciones de software es mantenerse actualizado y evitar el aprovechamiento de vulnerabilidades. Microsoft, Apple y otros productores de sistemas operativos lanzan parches y actualizaciones casi todos los días y las empresas u organizaciones responsables de las aplicaciones, como los navegadores web, las aplicaciones móviles y los servidores web, suelen actualizarlas.

A pesar de que las organizaciones se esfuerzan mucho en encontrar y reparar vulnerabilidades de software, se descubren nuevas vulnerabilidades con regularidad. Es por eso que algunas organizaciones utilizan investigadores de seguridad de terceros que se especializan en encontrar vulnerabilidades en el software, o realmente invierten en sus propios equipos de pruebas de penetración dedicados a buscar, encontrar y parchear las vulnerabilidades del software antes de que puedan ser explotadas.

Project Zero de Google es un gran ejemplo de esta práctica. Después de descubrir una serie de vulnerabilidades en varios software utilizados por los usuarios finales, Google formó un equipo permanente dedicado a encontrar vulnerabilidades de software. Puede obtener más información sobre la investigación de seguridad de Google <a href="https://bugs.chromium.org/p/project-zero/issues/list?can=1&redir=1" target="_blank">aquí</a>.

## El panorama de la ciberseguridad
Probablemente haya oído hablar de las criptomonedas, pero ¿sabe exactamente qué es y cómo funciona?

### Criptomoneda
La criptomoneda es dinero digital que se puede utilizar para comprar bienes y servicios, utilizando técnicas de cifrado sólidas para asegurar las transacciones en línea. Los bancos, los gobiernos e incluso empresas como Microsoft y AT&T son muy conscientes de su importancia y se están sumando al tren de las criptomonedas.

Los propietarios de criptomonedas guardan su dinero en "billeteras" virtuales encriptadas. Cuando se lleva a cabo una transacción entre los propietarios de dos billeteras digitales, los detalles se registran en un registro electrónico descentralizado o en un sistema de cadena de bloques (blockchain). Esto significa que se lleva a cabo con cierto grado de anonimato y se autogestiona, sin interferencias de terceros, como bancos centrales o entidades gubernamentales.

Aproximadamente cada diez minutos, computadoras especiales recopilan datos sobre las últimas transacciones en criptomonedas, convirtiéndolas en acertijos matemáticos para mantener la confidencialidad.

Estas transacciones se verifican a través de un proceso técnico y altamente complejo conocido como "minería". Este paso suele implicar a un ejército de "mineros" que trabajan en PC de alta gama para resolver acertijos matemáticos y autenticar transacciones.

Una vez verificado, el libro mayor se actualiza y se copia y distribuye electrónicamente en todo el mundo a cualquier persona que pertenezca a la red _blockchain_, completando efectivamente una transacción.

### Criptojacking
El criptojacking es una amenaza emergente que se esconde en la computadora, el teléfono móvil, la tableta, la computadora portátil o el servidor de un usuario, utilizando los recursos de esa máquina para "minar" criptomonedas sin el consentimiento o el conocimiento del usuario.

¡Muchas víctimas del criptojacking ni siquiera sabían que habían sido hackeados hasta que era demasiado tarde!

## Enlaces de interés
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<a href="#2-ataques-conceptos-y-técnicas">⬆️</a>
<a href="./00-Curso.md"><< Menú principal del módulo</a>