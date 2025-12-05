# Investigar un panorama de Amenazas
## Objetivos
* Parte 1: Investigar una vulnerabilidad de configuración de la red.
* Parte 2: investigar una vulnerabilidad de malware de suplantación de identidad.
* Parte 3: Investigar una red inalámbrica y la vulnerabilidad de DNS.

## Trasfondo/Situación
El panorama de amenazas consta de todas las vulnerabilidades que los agentes de amenazas pueden aprovechar. Cada incidente de ciberseguridad implica la explotación de vulnerabilidades por diferentes tipos de agentes de amenazas. Algunos agentes de amenazas quieren dinero, otros quieren ser famosos y otros quieren destruir información e infraestructura.

En esta actividad, investigará tres vulnerabilidades que los agentes de amenazas pueden aprovechar.

__Nota__: En esta actividad, tanto el centro de datos como los sitios de ISP / Telco están bloqueados.

## Instrucciones
### Parte 1: Investigar una vulnerabilidad de configuración de la red
A veces, las vulnerabilidades de seguridad de la red pueden ocurrir por accidente. Por ejemplo, olvidarse de actualizar el software de servidor o host puede exponer vulnerabilidades conocidas que podrían mitigarse fácilmente con una simple actualización. De manera similar, pueden introducirse vulnerabilidades cuando un dispositivo de red no está configurado correctamente o un dispositivo es defectuoso. En esta parte, explorará una vulnerabilidad que resulta de un dispositivo que no está configurado correctamente con las mejores prácticas de seguridad.

#### Paso 1: Use una red de invitados para obtener acceso a otros dispositivos en la red.
1. En Greenville, ubique el teléfono inteligente 3 a las afueras de la ubicación de inicio.

	Mary es la dueña de este smartphone. Es amiga de Bob y vive en la casa. Mary está estudiando para eventualmente obtener un trabajo en defensa de ciberseguridad y está familiarizada con las pruebas de penetración de la red. Se dio cuenta de que una red inalámbrica para invitados está abierta y accesible para todos. Se conectó a la red de invitados y usó Nmap para ejecutar un análisis, que puede identificar y descubrir detalles sobre todos los dispositivos activos. Uno de los dispositivos parece ser una cámara web. Su dirección IP es 192.168.100.101.

2. Pulse en Smartphone 3, y luego en Command Prompt. Introduzca el comando ping 192.168.100.101 Después de uno o dos mensajes de "Tiempo de espera de solicitud agotado", los pings restantes deben ser correctos.

	Mary informa a Bob que la red es muy vulnerable a los ataques. Alguien podría tomar el control de la cámara web, por ejemplo, y ver videos desde el interior de la casa. Bob invita a María a entrar, investigar el problema y proponer una solución.

#### Paso 2: Explore la red doméstica para identificar la vulnerabilidad.
1. Haga clic en Inicio. Sabiendo que los routers domésticos generalmente controlan las redes inalámbricas domésticas, Mary se dirige directamente a la oficina en casa y se sienta detrás del escritorio. Utilizará la PC Home Office para conectarse al router. Pero primero debe determinar la dirección IP.
2. Haga clic en PC Home Office> Pestaña Escritorio> Command Prompt y escriba el comando ipconfig.
El gateway predeterminado es la dirección IP del router inalámbrico doméstico.
	* ¿Cuál es la dirección IP?
3. A continuación, Mary utiliza el navegador web para conectarse al router inalámbrico doméstico. Cierre el Command Prompt (Símbolo del sistema) y haga click en Web Browser(Navegador Web) . Ingrese la dirección IP del gateway predeterminado.
4. Bob no tiene la documentación del router ni conoce las credenciales de inicio de sesión. Mary busca el modelo de router en Internet y descubre que las credenciales predeterminadas usan admin tanto para el nombre de usuario como para la contraseña. Inicie sesión en el router inalámbrico doméstico.
5. Haga clic en Wireless Revise la configuración inalámbrica básica para cada una de las tres radios que forman parte del router inalámbrico.
	* ¿Cuáles de las radios están activas?
	* ¿Cuáles son los SSID asignados a estas radios?
6. Haga clic en el submenú Wireless Security (Seguridad inalámbrica).
	* ¿La seguridad está activada para cada una de las radios? ¿Se configuran las contraseñas?
7. Mary pudo acceder a la red desde el exterior sin iniciar sesión; por lo tanto, ella investiga más a fondo. Haga clic en el submenú Red de invitados e investigue la configuración.
	* ¿La red de usuarios temporales está activa? Si es así, ¿en qué radio?
	Una red inalámbrica de usuarios temporales solo debe proporcionar acceso a Internet a los usuarios temporales. No debe permitir que los invitados accedan a los dispositivos en la red local dentro de la casa. En este caso, los invitados pueden acceder a la red local. Esto indica que el router doméstico está mal configurado.
	* ¿Qué propondría que haga Bob para proteger esta red?

### Parte 2: Investigar una vulnerabilidad de malware de suplantación de identidad
La suplantación de identidad es un tipo de ataque de ingeniería social en el que un agente de amenazas se disfraza como una fuente legítima y confiable para engañarlo para que instale malware en su dispositivo o para compartir información personal o financiera. Los ataques de suplantación de identidad generalmente ocurren a través de correos electrónicos o llamadas telefónicas. A diferencia de otras vulnerabilidades de red, la principal vulnerabilidad en los ataques de suplantación de identidad son los usuarios de la red. Por este motivo, una defensa importante contra la suplantación de identidad es capacitar a los usuarios sobre cómo prevenir ataques de suplantación de identidad.

En esta parte, simulará e investigará un ataque de suplantación de identidad.

__Nota__: Esta actividad es solo para fines de demostración. Escribir y enviar mensajes de correo electrónico de suplantación de identidad no es ético y se considera un ataque criminal en la mayoría de las jurisdicciones.

#### Paso 1: Actúe como un agente de amenazas y cree un correo electrónico de suplantación de identidad.
1. Vaya a la red del Café
2. Haga clic en la computadora portátil Café Hacker> ficha Escritorio> Correo electrónico.
3. Haga clic en Compose.

Utilice su imaginación para escribir un correo electrónico de suplantación de identidad. Su objetivo es persuadir al usuario para que copie y pegue una URL de su mensaje de correo electrónico en su navegador. Incluya el enlace pix.example.com en el correo electrónico. Puede buscar, por ejemplo, correos electrónicos de suplantación de identidad en línea para ver cómo los agentes de amenazas escriben este tipo de correo electrónico.

__Nota__: Los enlaces en correos electrónicos de suplantación de identidad suelen ser enlaces activos o "activos". Todo lo que la víctima tiene que hacer es hacer clic. Sin embargo, Packet Tracer no admite el uso de enlaces activos dentro del cliente de correo electrónico.

4.Envíe su correo electrónico a tres personas dentro de la red de la sucursal. Sus direcciones de correo electrónico son las siguientes:
* user1@mail.isp.net
* user2@mail.isp.net
* user3@mail.isp.net

#### Paso 2: Abra los correos electrónicos recibidos del agente de amenazas.
1. Acceda a la sucursal.
2. Haga clic en uno de los dispositivos, ya sea PC-BR1, Laptop BR-1 o Laptop BR-2.
3. Haga clic en la pestaña Desktopy luego haga clic en Email y finalmente en Receive (Recibir). Debería recibir el correo electrónico que acaba de enviar.

__Nota__: Packet Tracer puede tardar varios segundos en converger. Es posible que deba hacer clic en Recibir varias veces si el correo electrónico no se recupera correctamente.

4. Opcional: vaya a los otros dispositivos de la víctima, abra su cliente de correo electrónico y haga clic en Recibir para verificar que también recibió su correo electrónico de suplantación de identidad.

#### Paso 3: Actúe como una víctima y siga las instrucciones de suplantación de identidad.
__Nota__: Packet Tracer puede tardar varios segundos en converger. Pueden hacer clic en Fast Forward Time (Adelantar el tiempo) (Alt+D) para acelerar el proceso.
1. Lea el correo electrónico y copie la dirección del sitio web.
2. Cierre el Navegador de Correo , y luego haga clic en el Navegador Web.
3. Pegue la URL en el campo URL y accede con `Go`.
	* ¿Qué sucedió cuando se cargó la página web?
	* ¿Cómo se llama este tipo de ataque?
	* En una situación del mundo real, este correo electrónico generalmente se transmite por un virus que envía automáticamente correos electrónicos maliciosos a todas las direcciones de su lista de contactos. Describa el daño que este tipo de ataque puede causar dentro de una organización.

### Parte 3: Investigar red inalámbrica y una vulnerabilidad de DNS
El usuario promedio de la red tiende a confiar en las redes Wi-Fi abiertas en lugares públicos. El uso de Wi-Fi en su lugar, los servicios de datos móviles pueden proporcionar velocidades de transmisión de datos más rápidas y ser más rentables. Sin embargo, los agentes de amenazas pueden configurar una computadora portátil con una interfaz Wi-Fi que pueda actuar como punto de acceso y cliente de Wi-Fi. Esto significa que los creadores de amenazas pueden crear sus propias redes inalámbricas y transmitir un SSID convincente a las posibles víctimas en lugares públicos. Los actores de amenazas utilizan estos puntos de acceso dudosos para crear ataques de ataque principal. En este ataque, los creadores de amenazas pueden capturar y leer todo el tráfico inalámbrico de los dispositivos que se asocian con el punto de acceso dudoso, lo que posiblemente aprenda nombres de usuario, contraseñas y otra información confidencial.

En esta parte, investigará cómo se puede utilizar un punto de acceso dudoso para atraer a los usuarios a conectarse a una red inalámbrica falsa. Cuando se combinan con servicios de red como DHCP y DNS, los usuarios pueden ser víctimas de ataques maliciosos a sitios web mediante el secuestro de DNS.

#### Paso 1: Conéctese a la red inalámbrica del agente de amenazas.
1. Navegue hasta el Café. Observe al actor de amenazas sentado en la esquina.
2. Haga clic en la Hacker Backpack e investigue el contenido. En su mochila, tiene un router inalámbrico y un sniffer de red. Su objetivo es interceptar el tráfico de usuarios y dirigirlo a un servidor malicioso.
3. Regrese a Café y haga clic en la computadora portátil del cliente de Cafe> ficha Escritorio> Aplicación inalámbrica de PC.
4. Haga clic en la pestaña Connect. Será necesario que haga clic en Actualizar para ver la lista de redes disponibles.
	* Si estuviera en el Cafe, ¿a qué red inalámbrica elegiría conectarse? Explique.
5. Haga clic en cualquiera de los nombres de red de Cafe_WI-FI_FAST y luego en Conectar.

#### Paso 2: Visite su sitio de medios sociales favorito.
1. Cierre la aplicación PC Wireless y haga clic en Navegador web.
2. En el campo URL, ingrese amigos.example.com y haga clic en Ir. Se supone que este sitio web es una red social legítima en esta simulación.
	* ¿Qué ocurrió?
	* ¿Cuál fue la URL del servidor de malware que se utilizó en el escenario de ataque de suplantación de identidad? ¿Es lo mismo?
	
#### Paso 3: Investigar el origen del ataque.
1. Cierre el Navegador Web y luego haga clic en IP Configuration(Configuración de IP) .
2. En el Café, haga clic en Laptop VPN> ficha Desktop> IP Configuration.
3. Haga clic en Cafe Customer (Cliente del Café) en la barra de tareas para volver a verlo y luego organice las dos ventanas de configuración de IP una al lado de la otra. Compare los valores entre los dos dispositivos.
	* ¿Cuáles son las diferencias entre las direcciones de las dos computadoras portátiles?
4. Investigar la computadora portátil Cafe Hacker.
	* ¿Cuál es su dirección IP? ¿Por qué es esto significativo?
	* En la computadora portátil del Hacker del Cafe, haga clic en la ficha Servicios> DNS.Hacker
5. Busque el nombre del sitio web de amigos.example.com. Tenga en cuenta que la dirección IP es la misma dirección IP asociada con pix.example.com del ataque de suplantación de identidad anterior.
6. En Servicios, haga clic en DHCP. Tenga en cuenta que la dirección del servidor DNS distribuida a los hosts a través de DHCP es la misma asignada al cliente de Cafe.
	* ¿Cuáles son los pasos en este ataque?

## Resumen
En esta actividad, hemos analizado tres formas diferentes en las que las vulnerabilidades pueden generar vulnerabilidades. Como usuario informado de la red o profesional de ciberseguridad, es su responsabilidad pensar en las diferentes maneras en que dichas vulnerabilidades pueden detectarse y mitigarse antes de que ocurra un ataque cibernético.