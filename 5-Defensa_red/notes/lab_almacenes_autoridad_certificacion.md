<title coding="utf-8">Almacenes de la autoridad de certificación</title>

# Almacenes de la autoridad de certificación
# Objetivos
* Parte 1: Certificados en los que confían sus navegadores.
* Parte 2: Búsqueda de ataques Man-In-the-Middle.

# Trasfondo/Situación
Con la evolución de la web, también aumentó la necesidad de medidas de seguridad. HTTPS (la ‘S’ quiere decir seguridad), junto con el concepto de Autoridad emisora de certificados, fue presentado por Netscape allá por el año 1994 y sigue utilizándose actualmente. En esta práctica de laboratorio:
* Liste todos los certificados en los que confía su navegador (completado en su computadora)
* Utilice hashes para detectar si su conexión a Internet está siendo interceptada (completado en la máquina virtual Security Workstation)

# Recursos necesarios
* Máquina virtual Security Workstation
* Acceso a Internet

# Instrucciones
## Parte 1: Certificados en los que confían sus navegadores
HTTPS depende de una entidad externa para la validación. Conocida como Autoridad emisora de certificados (Certification Authority, CA), esta entidad externa verifica si un nombre de dominio realmente pertenece a la organización que asevera ser su titular. Si la verificación es positiva, la CA crea un certificado con firma digital que contiene información sobre la organización, incluida su clave pública.

Todo el sistema se basa en el hecho de que los navegadores web y los sistemas operativos se envían con una lista de CA de confianza. El navegador considerará como legítimo cualquier certificado firmado por cualquiera de las CA de la lista y confiarán en él automáticamente. Para fortalecer la seguridad y escalabilidad del sistema, las CA a menudo distribuyen la tarea de creación y firma de certificados en muchas CA secundarias. La CA principal se conoce como CA raíz. Si un navegador confía en una CA raíz, también confía todas sus CA secundarias.

__Nota__: Aunque los almacenes de certificados son similares en todos los navegadores, este laboratorio se centra en Chrome 81 y Firefox 75. El menú y los gráficos pueden ser diferentes en otras versiones de los navegadores web.

Sigan los pasos para mostrar el almacén de CA en sus navegadores:

### Paso 1: Mostrar los certificados raíz en Chrome
Puede realizar este paso en el equipo local o utilizar Firefox en la máquina virtual CyberOps Workstation. Si utilizamos Firefox, seguir con el Paso 2. Si no utilizamos Chrome ni Firefox, debemos buscar los pasos para mostrar los respectivos certificados raíz en Internet.

Nota: El menú y los gráficos pueden ser diferentes en otras versiones del navegador Chrome.
1. Abran el navegador web Chrome en su PC.
2. Hagan clic en el icono de los tres puntos que se encuentra en el extremo derecho de la barra de direcciones para mostrar las opciones de Chrome. Haga clic en Settings (Configuración).
3. Desplácese hacia abajo hasta Privacy and security y haga clic en Security.
4. Dirigase al final de la ventana y seleccione Manage certificates.
5. En la ventana Certificate seleccione la solapa Trusted Root Certification Authorities para mostrar todos los certificados y las Autoridades de Certificación de confianza de Chrome.

### Paso 2: Mostrar los certificados en el almacén de CA en Firefox.
Nota: El menú y los gráficos pueden ser diferentes en otras versiones del navegador Firefox y entre diferentes sistemas operativos. En este paso se muestra Firefox 94 en la máquina virtual CyberOps Workstation.
1. Abra Firefox y haga clic en el icono Menu. El icono de Menu se encuentra en el extremo derecho de la ventana de Firefox, al lado de la barra de direcciones. Haga clic en Settings (Configuración).
2. Haga clic en Privacy & Security en el panel izquierdo.
3. Desplácese hasta la sección Security y haga clic en View Certificates.
4. Se abrirá una ventana con todos los certificados y las autoridades de certificación en las que confía Firefox.

## Parte 2: Buscar ataques de intermediarios
Esta parte se realiza utilizando la máquina virtual Security Workstation.

Una de las utilidades de los hashes es verificar la integridad de los datos; pero también se pueden usar para detectar ataques de intermediarios (o Man-in-the-Middle) en HTTPS.

Para proteger los datos de los usuarios, cada vez más sitios web están adoptando el tráfico cifrado. Conocido como HTTPS, los sitios utilizan protocolos como TLS/SSL para cifrar el tráfico de los usuarios de extremo a extremo. Después de cifrar el tráfico correctamente es muy difícil que cualquier tercero que no sea el usuario o el sitio en cuestión vea el contenido del mensaje cifrado. Esto es bueno para los usuarios pero crea un problema para las organizaciones que quieren ver el contenido de ese tráfico. Las empresas y las organizaciones a menudo optan por espiar el tráfico generado por sus empleados para controlarlos. Necesitaban poder ver el contenido del tráfico cifrado TLS/SSL. Esto se hace por medio de un proxy HTTPS.

Los navegadores web confían en la identidad de un sitio web que se visita si el certificado que presenta ese sitio web está firmado por una de las CA instaladas en el almacén de certificados del navegador. Para poder espiar el tráfico cifrado TLS/SSL de sus usuarios, una empresa u organización simplemente agrega otra CA a la lista de CA instaladas del navegador del usuario.

Consideren la siguiente situación hipotética: la Empresa X contrata a un empleado nuevo y le entrega una computadora portátil nueva de la empresa. Antes de hacerlo, el departamento de TI de la empresa instala todo el software necesario para el trabajo. Entre el software y los paquetes que se instalan, el departamento de TI también incluye una CA adicional a la lista de CA de confianza. Esta CA adicional apunta a una computadora controlada por la empresa conocida como el proxy HTTPS. Como la empresa controla los patrones de tráfico, el proxy HTTPS se puede ubicar en el medio de cualquier conexión. Funciona de la siguiente manera:
1. El usuario trata de establecer una conexión segura al sitio web HTTPS H alojado en Internet. H puede ser cualquier sitio HTTPS: un banco, una tienda en línea, un servidor de correo electrónico, etc.
2. Como la empresa controla los patrones de tráfico, lo hace de modo que todo el tráfico del usuario deba pasar por el proxy HTTPS. El proxy HTTPS se hace pasar por el sitio web H y presenta un certificado autofirmado para demostrar que es H. El proxy HTTPS básicamente dice "Hola, soy el sitio HTTPS H. Aquí está mi certificado. Fue firmado por… mí mismo”.
3. Debido a que el certificado presentado está firmado por una de las CAs incluidas en el almacén de CAs de la computadora portátil (recuerde que fue añadida por TI), el navegador web cree erróneamente que se está comunicando con H. Observe que, si la CA extra no hubiera sido añadida al almacén de CAs, el portátil no confiaría en el certificado e inmediatamente se daría cuenta de que alguien más estaba intentando hacerse pasar por H.
4. La computadora portátil confía en la conexión y establece un canal seguro con el proxy HTTPS creyendo erróneamente que se está comunicando en forma segura con H.
5. El proxy HTTPS establece ahora una segunda conexión segura con H, el sitio web al que el usuario estaba intentando acceder desde el principio.
6. El proxy HTTPS es ahora el punto final de dos conexiones seguras separadas; una establecida con el usuario y otra establecida con H. Como HTTPS es el punto final de ambas conexiones, ahora puede descifrar el tráfico de las dos.
7. Ahora el proxy HTTPS puede recibir tráfico del usuario cifrado con TLS/SSL destinado a H, descifrarlo, inspeccionarlo, volver a cifrarlo con TLS/SSL y enviarlo a H. Cuando H responde, el proxy HTTPS invierte el proceso antes de reenviar el tráfico al usuario.

Observe que el proceso pasa desapercibido para el usuario, que ve la conexión como cifrada con TLS/SSL (tildes de color verde en el navegador). Si bien la conexión es segura (cifrada con TLS/SSL), se la estableció con un sitio web falso.

Incluso si su presencia pasa desapercibida para el usuario, los proxis TLS se pueden detectar fácilmente con la ayuda de hashes. Teniendo en cuenta el ejemplo anterior, debido a que el proxy HTTPS no tiene acceso a las claves privadas del sitio H, el certificado que presenta al usuario es diferente al certificado presentado por H. En cada certificado se incluye un valor conocido como fingerprint (huella digital). En esencia, una huella digital es un hash calculado y firmado por el emisor del certificado que actúa como un resumen único de todo el contenido del certificado. Si se modifica al menos una de las letras del certificado, la huella digital generará un valor completamente diferente al calcularla. Debido a esta propiedad, las huellas digitales se utilizan para comparar certificados rápidamente. Si volvemos al ejemplo anterior, el usuario puede solicitar el certificado de H y compara la huella digital que contiene con la provista al establecer la conexión con el sitio web H. Si las huellas digitales coinciden, la conexión realmente se estableció con H. Si no coinciden, la conexión se estableció con algún otro punto extremo.

Sigan los pasos que se indican a continuación para determinar si hay un proxy HTTPS en sus conexiones.

### Paso 1: Recopilar la huella digital correcta y sin modificar del certificado.
El primer paso es recopilar algunas huellas digitales de sitios. Estos es importante porque se las utilizará para compararlas más adelante. La siguiente tabla contiene las huellas digitales de los certificados de algunos sitios populares.

__Nota__: Es posible que las huellas digitales SHA-1 que se muestran en la Tabla 1 ya no sean válidas puesto que las organizaciones renuevan periódicamente sus certificados. La huella digital también se llama huella dactilar en máquinas basadas en Windows.

Tabla 1: Sitios populares y huellas digitales de sus certificados SHA-1

|__Sitio__|__Dominios cubiertos por el certificado__|__Certificate SHA-1 Fingerprint (a partir de mayo 2020)__|
|:-|:-|:-|
|www.cisco.com|www.cisco.com|E2:BD:0B:58:C6:B4:FF:91:D6:23:AB:44:0D:8F:64:76:29:4E:30:0B|
|www.facebook.com|*.facebook.com|BB:E7:A0:97:C7:92:B2:2D:00:38:12:69:E4:64:E9:04:96:4B:C7:41|
|www.wikipedia.org|*.wikipedia.org|A8:F9:F7:79:BE:DB:3E:EB:59:F0:1D:A6:34:08:A1:64:5D:28:48:44|
|twitter.com|twitter.com|73:33:BB:96:1D:DB:9C:0C:4F:E5:1C:FF:68:26:CF:5E:3F:50:AB:96|
|www.linkedin.com|www.linkedin.com|04:BC:C5:09:DD:AE:99:40:7E:99:A5:65:32:68:EC:5D:2D:D7:5A:19|

* ¿Qué son las huellas digitales? ¿Por qué son importantes?
* ¿Quién calcula las huellas digitales? ¿Cómo se las encuentra?

### Paso 2: recopile la huella digital del certificado que está utilizando la máquina virtual Security Workstation.
Ahora que tenemos las huellas digitales reales, es momento de obtener huellas de un host local y comparar los valores. Si las huellas digitales no coinciden, el certificado en uso NO pertenece al sitio HTTPS que se está verificando, lo que significa que hay un proxy HTTPS entre el servidor y el sitio HTTPS en cuestión. Si las huellas digitales coinciden, no hay ningún proxy HTTP.
1. Utilice los siguientes tres comandos encadenados para obtener la huella digital de Cisco.com. En la línea de abajo se utiliza OpenSSL para conectarse con cisco.com en el puerto443 (HTTPS), solicitar el certificado y almacenarlo en un archivo de texto de nombre cisco.pem. También se muestra la salida para ofrecer contexto.
	```shell
	[analyst@secOps ~]$ echo -n | openssl s_client -connect cisco.com:443 | sed
	-ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > ./cisco.pem
	depth=2 C = BM, O = QuoVadis Limited, CN = QuoVadis Root CA 2
	verify return:1
	depth=1 C = US, O = HydrantID (Avalanche Cloud Corporation), CN = HydrantID SSL ICA G2
	verify return:1
	depth=0 C = US, ST = CA, L = San Jose, O = "Cisco Systems, Inc.", CN = www.cisco.com
	verify return:1
	LISTO
	```
2. De manera opcional utilice el comando cat para generar una lista con el contenido del certificado obtenido y almacenarlo en el archivo de texto cisco.pem:
	```shell
	[analyst@secOps ~]$ cat cisco.pem
	-----BEGIN CERTIFICATE----
	MIIG1zCCBL+gAwIBAgIUKBO9xTQoMemc9zFHNkdMW+SgFO4wDQYJKoZIhvcNAQEL
	BQAwXjELMAkGA1UEBhMCVVMxMDAuBgNVBAoTJ0h5ZHJhbnRJRCAoQXZhbGFuY2hl
	IENsb3VkIENvcnBvcmF0aW9uKTEdMBsGA1UEAxMUSHlkcmFudElEIFNTTCBJQ0Eg
	RzIwHhcNMTcxMjA3MjIxODU1WhcNMTkxMjA3MjIyODAwWjBjMQswCQYDVQQGEwJV
	UzELMAkGA1UECAwCQ0ExETAPBgNVBAcMCFNhbiBKb3NlMRwwGgYDVQQKDBNDaXNj
	byBTeXN0ZW1zLCBJbmMuMRYwFAYDVQQDDA13d3cuY2lzY28uY29tMIIBIjANBgkq
	yvo6dWpJdSircYy8HG0nz4+936+2waIVf1BBQXZUjNVuws74Z/eLIpl2c6tANmE0
	q1i7fiWgItjDQ8rfjeX0oto6rvp8AXPjPY6X7PT1ulfhkLYnxqXHPETRwr8l5COO
	MDEh95cRxATXNAlWAwLcBT7lDmrGron6rW6hDtuUPPG/rjZeZbNww5p/nT3EXX2L
	Rh+m0R4j/tuvy/77YRWyp/VZhmSLrvZEYiVjM2MgCXBvqR+aQ9zWJkw+CAm5Z414
	Eiv5RLctegYuBUMGTH1al9r5cuzfwEg2mNkxl4I/mtDro2kDAv7bcTm8T1LsZAO/
	1bWvudsrTA8jksw+1WGAEd9bHi3ZpJPYedlL
	-----END CERTIFICATE-----
	[analyst@secOps ~]$
	```
3. Ahora que el certificado está guardado en el archivo de texto cisco.pem, utilice el siguiente comando para extraer su huella digital y mostrarla en la pantalla:
	```shell
	[analyst@secOps ~]$ openssl x509 -noout -in cisco.pem -fingerprint -sha1
	SHA1 Huella digital = 64:19:CA:40:E2:1B:3F:92:29:21:A9:CE:60:7 D: C9:0 C: 39:B5:71:3E
	[analyst@secOps ~]$
	```
	__Nota__: El valor de la huella digital puede ser diferente por dos motivos. En primer lugar, es posible que esté utilizando un sistema operativo diferente al de la máquina virtual Security Workstation. En segundo lugar, los certificados se actualizan con regularidad y cambian así el valor de la huella digital.
	* ¿Qué algoritmo de hash utilizó OpenSSL para calcular la huella digital?
	* ¿Por qué se eligió ese algoritmo específico? ¿Tiene alguna importancia?

### Paso 3: Comparar las huellas digitales
Utilicen la Tabla 1 para comparar la huella digital del certificado que se obtuvo directamente desde el sitio HTTPS de Cisco con la que se obtuvo desde sus redes. Recuerde que las huellas digitales pueden cambiar con el tiempo.
* ¿Coinciden las huellas dactilares?
* ¿Qué significa eso?

## Parte 3: Desafíos (opcional)
1. Compruebe las huellas digitales de los sitios que se muestran en la Tabla 1, pero utilizando la GUI de su navegador web.
	* Pistas: Encuentre una manera de mostrar la huella digital a través de la GUI del navegador. Recuerde: Google es útil en este ejercicio, y Windows a menudo llama Thumbprint a la huella digital.
2. Utilice el OpenSSL (Parte 2, Pasos 1 a 3) para comprobar todas las huellas digitales que aparecen en la Tabla-1

### Preguntas de reflexión
* ¿Qué es necesario para que funcione el proxy HTTPS?