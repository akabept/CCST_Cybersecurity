<a href="./00-Curso.md"><< Menú principal del módulo</a>

# 12. ICMP
# Mensajes ICMP
## Mensajes de ICMPv4 e ICMPv6
En este tema, aprenderá acerca de los diferentes tipos de protocolos de mensajes de control de Internet (ICMP) y las herramientas que se utilizan para enviarlos.

Aunque IP es sólo un protocolo de mayor esfuerzo (_best effort_), el conjunto TCP/IP proporciona mensajes de error y mensajes informativos cuando se comunica con otro dispositivo IP. Estos mensajes se envían mediante los servicios de ICMP. El objetivo de estos mensajes es proporcionar respuestas acerca de temas relacionados con el procesamiento de paquetes IP en determinadas condiciones, no es hacer que IP sea confiable. Los mensajes de ICMP no son obligatorios y, a menudo, no se permiten dentro de una red por razones de seguridad.

El protocolo ICMP está disponible tanto para IPv4 como para IPv6. El protocolo de mensajes para IPv4 es ICMPv4. ICMPv6 proporciona estos mismos servicios para IPv6, pero incluye funcionalidad adicional. En este curso, el término ICMP se utilizará para referirse tanto a ICMPv4 como a ICMPv6.

Los tipos de mensajes ICMP y las razones por las que se envían son extensos. Los mensajes ICMP comunes a ICMPv4 e ICMPv6 y discutidos en este módulo incluyen:

* Accesibilidad al host
* Destino o servicio inaccesible
* Tiempo superado

## Accesibilidad del Host
Se puede utilizar un mensaje de eco ICMP para probar la accesibilidad de un _host_ en una red IP. El _host_ local envía una solicitud de eco ICMP a un host. Si el _host_ se encuentra disponible, el _host_ de destino responde con una respuesta de eco. En la ilustración, haga clic en el botón Reproducir para ver una animación de la solicitud de eco/respuesta de eco ICMP. Este uso de los mensajes ICMP Echo es la base de la utilidad `ping`.

<div style="padding-left: 5%;">
	<img style="float: left;width: 40%; border: black 1px solid;" src="./img/icmp_ping-01.png" />
	<img style="float: left;width: 40%; border: black 1px solid" src="./img/icmp_ping-02.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 40%; border: black 1px solid" src="./img/icmp_ping-03.png" />
	<img style="float: left;width: 40%; border: black 1px solid" src="./img/icmp_ping-04.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 40%; border: black 1px solid" src="./img/icmp_ping-05.png" />
	<img style="float: left;width: 40%; border: black 1px solid" src="./img/icmp_ping-06.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 40%; border: black 1px solid" src="./img/icmp_ping-07.png" />
	<img style="float: left;width: 40%; border: black 1px solid" src="./img/icmp_ping-08.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 40%; border: black 1px solid" src="./img/icmp_ping-09.png" />
	<img style="float: left;width: 40%; border: black 1px solid" src="./img/icmp_ping-10.png" />
	<div style="clear: both;" />
</div>

## Destino o Servicio Inalcanzable
Cuando un _host_ o gateway recibe un paquete que no puede entregar, puede utilizar un mensaje ICMP de destino inalcanzable para notificar al origen que el destino o el servicio son inalcanzables. El mensaje incluye un código que indica el motivo por el cual no se pudo entregar el paquete.

Algunos de los códigos de destino inalcanzable para ICMPv4 son los siguientes:

* 0 - Red inalcanzable
* 1 - _host_ inalcanzable
* 2 - Protocolo inalcanzable
* 3 - Puerto inalcanzable

Algunos de los códigos de destino inalcanzable para ICMPv6 son los siguientes:

* 0 - No hay ruta para el destino
* 1 - La comunicación con el destino está prohibida administrativamente (por ejemplo, firewall)
* 2 - Más allá del alcance de la dirección de origen
* 3 - No se puede alcanzar la dirección
* 4 - Puerto inalcanzable

__Nota__: ICMPv6 tiene códigos similares, pero levemente diferentes para los mensajes de destino inalcanzable.

## Tiempo Excedido
Los routers utilizan los mensajes de tiempo superado de ICMPv4 para indicar que un paquete no puede reenviarse debido a que el campo de tiempo de duración (TTL) del paquete se disminuyó a 0. Si un router recibe un paquete y disminuye el campo TTL en el paquete IPV4 a cero, descarta el paquete y envía un mensaje de tiempo superado al _host_ de origen.

ICMPv6 también envía un mensaje de tiempo superado si el router no puede reenviar un paquete IPv6 debido a que el paquete caducó. En lugar del campo TTL de IPv4, ICMPv6 usa el campo Límite de salto de IPv6 para determinar si el paquete ha expirado.

__Nota__: Los mensajes de Tiempo Excedido son utilizados por la herramienta `traceroute`.

## Mensajes ICMPv6
Los mensajes informativos y de error que se encuentran en ICMPv6 son muy similares a los mensajes de control y de error que implementa ICMPv4. Sin embargo, ICMPv6 tiene nuevas características y funcionalidad mejorada que no se encuentran en ICMPv4. Los mensajes ICMPv6 están encapsulados en IPv6.

ICMPv6 incluye cuatro mesajes nuevos como parte del protocolo de detección de vecino (ND o NDP - Neighbour Discovery Protocol).

Los mensajes entre un router IPv6 y un dispositivo IPv6, incluida la asignación dinámica de direcciones, son los siguientes:

* Mensaje de anuncio de router (RA)
* Mensaje de solicitud de router (RS)

Los mensajes entre dispositivos IPv6, incluida la detección de direcciones duplicadas y la resolución de direcciones, son los siguientes:

* Mensaje de solicitud de vecino (NS)
* Mensaje de anuncio de vecino (NA)

__Nota__: El ND de ICMPv6 también incluye el mensaje de redireccionamiento, que tiene una función similar al mensaje de redireccionamiento utilizado en ICMPv4.

### Mensajes de RA
Los enrutadores habilitados para IPv6 envían mensajes de RA cada 200 segundos para proporcionar información de direccionamiento a los hosts habilitados para IPv6. El mensaje RA puede incluir información de direccionamiento para el host, como el prefijo, la longitud del prefijo, la dirección DNS y el nombre de dominio. Un _host_ que utiliza la Configuración automática de direcciones sin estado (SLAAC) establecerá su puerta de enlace predeterminada en la dirección de enlace local del enrutador que envió el RA.

R1 envía un mensaje de RA, "Hola a todos los dispositivos habilitados para IPv6. Soy R1 y puedes usar SLAAC para crear una dirección de unidifusión global IPv6. El prefijo es `2001:db8:acad:1::/64`. Por cierto, use mi dirección local de enlace `fe80::1` como su puerta de enlace predeterminada".

<div style="width: 50%;padding-left: 20%;">
	<img src="./img/icmpv6_RA.png" />
</div>

### Mensajes de RS
Un router habilitado para IPv6 también enviará un mensaje RA en respuesta a un mensaje RS. En la figura, PC1 envía un mensaje RS para determinar cómo recibir dinámicamente su información de dirección IPv6.

R1 responde a la RS con un mensaje de RA.

PC1 envía un mensaje RS, "Hola, acabo de arrancar. ¿Hay un router IPv6 en la red? Necesito saber cómo obtener la información de mi dirección IPv6 de forma dinámica".
R1 responde con un mensaje de RA. "Hola a todos los dispositivos habilitados para IPv6. Soy R1 y puedes usar SLAAC para crear una dirección de unidifusión global IPv6. El prefijo es `2001:db8:acad:1::/64`. Por cierto, use mi dirección local de enlace `fe80::1` como su puerta de enlace predeterminada".

<div style="width: 50%;padding-left: 20%;">
	<img src="./img/icmpv6_RS.png" />
</div>

### Mensajes de NS
Cuando a un dispositivo se le asigna una dirección de unidifusión global IPv6 o unidifusión local de enlace, puede realizar una detección de dirección duplicada (DAD) para garantizar que la dirección IPv6 sea única. Para verificar la unicidad de una dirección, el dispositivo enviará un mensaje NS con su propia dirección IPv6 como la dirección IPv6 objetivo, como se muestra en la figura.

Si otro dispositivo de la red tiene esta dirección, responde con un mensaje NA. Este mensaje NA notifica al dispositivo emisor que la dirección está en uso. Si no se devuelve un mensaje NA correspondiente dentro de un cierto período de tiempo, la dirección de unidifusión es única y aceptable para su uso.

__Nota__: No se requiere DAD, pero RFC 4861 recomienda que DAD se realice en direcciones de unidifusión.

PC1 envía un mensaje NS para comprobar que una dirección sea única, "¿Quién tiene la dirección IPv6 `2001:db8:acad:1::10`, envíeme su dirección MAC?".

<div style="width: 50%;padding-left: 20%;">
	<img src="./img/icmpv6_NS.png" />
</div>

### Mensajes de NA
La resolución de direcciones se utiliza cuando un dispositivo en la LAN conoce la dirección IPv6 de unidifusión de un destino, pero no conoce la dirección MAC de Ethernet. Para determinar la dirección MAC del destino, el dispositivo envía un mensaje de NS a la dirección de nodo solicitado. El mensaje incluye la dirección IPv6 conocida (objetivo). El dispositivo que se destinó a la dirección IPv6 responde con un mensaje NA que contiene la dirección MAC de Ethernet.

En la figura, R1 envía un mensaje NS a `2001:db8:acad:1::10` pidiendo su dirección MAC.

R1 envía un mensaje NS de resolución de dirección. "¿Quién tiene la dirección IPv6 `2001:db8:acad:1::10`, envíeme su dirección MAC?"
PC1 responde con un mensaje NA. "Soy `2001:db8:acad:1::10` y mi dirección MAC es `00:aa:bb:cc:dd:ee`".

<div style="width: 50%;padding-left: 20%;">
	<img src="./img/icmpv6_NA.png" />
</div>

# Pruebas de Ping y Traceroute
## Ping - Probar la Conectividad
En el tema anterior, se le presentaron las herramientas `ping` y `traceroute` (`tracert`). En este tema, aprenderá acerca de las situaciones en las que se usa cada herramienta y cómo usarlas. `ping` es una utilidad de prueba de IPv4 e IPv6 que utiliza la solicitud de eco ICMP y los mensajes de respuesta de eco para probar la conectividad entre los hosts.

Para probar la conectividad con otro _host_ de una red, se envía una solicitud de eco a la dirección de _host_ mediante el comando `ping`. Si el _host_ en la dirección especificada recibe la solicitud de eco, responde con una respuesta de eco. A medida que se recibe cada respuesta de eco, el comando `ping` proporciona comentarios acerca del tiempo transcurrido entre el envío de la solicitud y la recepción de la respuesta. Esto puede ser una medida del rendimiento de la red.

El comando `ping` tiene un valor de tiempo de espera para la respuesta. Si no se recibe una respuesta dentro del tiempo de espera, el comando `ping` proporciona un mensaje que indica que no se recibió una respuesta. Esto puede indicar que hay un problema, pero también podría indicar que las funciones de seguridad que bloquean los mensajes de `ping` se han habilitado en la red. Es común que el primer `ping` se agote si es necesario realizar la resolución de direcciones (ARP o ND) antes de enviar la solicitud de eco ICMP.

Una vez que se envían todas las solicitudes, la utilidad `ping` proporciona un resumen que incluye la tasa de éxito y el tiempo promedio del viaje de ida y vuelta al destino.

Los tipos de pruebas de conectividad que se realizan con `ping` son los siguientes:

* Hacer `ping` al loopback local.
* Hacer `ping` a la puerta de enlace predeterminada.
* Hacer `ping` al _host_ remoto.

## Hacer Ping al Loopback
`ping` se puede usar para probar la configuración interna de IPv4 o IPv6 en el _host_ local. Para realizar esta prueba, se debe hacer `ping` a la dirección de loopback local `127.0.0.1` para IPv4 (`::1` para IPv6).

Una respuesta de `127.0.0.1` para IPv4 (o `::1` para IPv6) indica que IP está instalado correctamente en el host. Esta respuesta proviene de la capa de red. Sin embargo, esta respuesta no indica que las direcciones, las máscaras o los gateways estén configurados adecuadamente. Tampoco indica nada acerca del estado de la capa inferior de la pila de red. Simplemente, prueba el protocolo IP en la capa de red de dicho protocolo. Un mensaje de error indica que TCP/IP no funciona en el host.

* Hacer `ping` al _host_ local permite confirmar que el protocolo TCP/IP se encuentra instalado en el _host_ y que funciona.
* Hacer `ping` a `127.0.0.1` ocasiona que un dispositivo se haga `ping` a sí mismo.

<div style="width: 50%;padding-left: 20%;">
	<img src="./img/icmp_ping_props.png" />
</div>

## Hacer Ping a la Puerta de Enlace Predeterminada
También es posible utilizar el comando `ping` para probar la capacidad de comunicación de un _host_ en la red local. Esto generalmente se hace haciendo `ping` a la dirección IP de la puerta de enlace predeterminada del host. Un `ping` exitoso a la puerta de enlace predeterminada indica que el _host_ y la interfaz del enrutador que sirve como puerta de enlace predeterminada están operando en la red local.

Para esta prueba, la dirección de puerta de enlace predeterminada se usa con mayor frecuencia porque el router normalmente siempre está operativo. Si la dirección de puerta de enlace predeterminada no responde, se puede enviar un `ping` a la dirección IP de otro _host_ en la red local que se sabe que está operativo.

Si la puerta de enlace predeterminada u otro _host_ responde, entonces el _host_ local puede comunicarse con éxito a través de la red local. Si la puerta de enlace predeterminada no responde pero otro _host_ sí, esto podría indicar un problema con la interfaz del router que funciona como la puerta de enlace predeterminada.

Una posibilidad es que se haya configurado una dirección de puerta de enlace predeterminada incorrecta en el host. Otra posibilidad es que la interfaz del router puede estar en funcionamiento, pero se le ha aplicado seguridad, de manera que no procesa o responde solicitudes de `ping`.

El _host_ hace `ping` a su puerta de enlace predeterminada, enviando una solicitud de eco ICMP. La puerta de enlace predeterminada envía una respuesta de eco confirmando la conectividad.

<div style="width: 50%;padding-left: 20%;">
	<img src="./img/icmp_ping_puerta_enlace.png" />
</div>

## Hacer Ping a un Host Remoto
También se puede utilizar el comando `ping` para probar la capacidad de un _host_ local para comunicarse en una interconexión de redes. El _host_ local puede hacer `ping` a un _host_ IPv4 operativo de una red remota, como se muestra en la ilustración. El router utiliza su tabla de enrutamiento IP para reenviar los paquetes.

Si este `ping` se realiza correctamente, se puede verificar el funcionamiento de una amplia porción de la interconexión de redes. Un `ping` exitoso a través de la red confirma la comunicación en la red local, el funcionamiento del enrutador que sirve como puerta de enlace predeterminada y el funcionamiento de todos los demás enrutadores que podrían estar en la ruta entre la red local y la red del _host_ remoto.

Además, se puede verificar la funcionalidad del _host_ remoto. Si el _host_ remoto no pudiera comunicarse fuera de su red local, no habría respondido.

__Nota__: Muchos administradores de redes limitan o prohíben la entrada de mensajes ICMP a la red de la empresa; por lo tanto, la falta de una respuesta de `ping` puede ser por razones de seguridad.

<div style="padding-left: 5%;">
	<img style="float: left;width: 45%; border: black 1px solid;" src="./img/icmp_eco-1.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/icmp_eco-2.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/icmp_eco-3.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/icmp_eco-4.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/icmp_eco-5.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/icmp_eco-6.png" />
	<div style="clear: both;" />
</div>

## Traceroute - Probar el Camino
El comando `ping` se usa para probar la conectividad entre dos hosts, pero no proporciona información sobre los detalles de los dispositivos entre los hosts. `traceroute` (`tracert`) es una utilidad que genera una lista de saltos que se alcanzaron correctamente a lo largo de la ruta. Esta lista puede proporcionar información importante sobre la verificación y la solución de problemas. Si los datos llegan al destino, el rastreo indica la interfaz de cada router que aparece en la ruta entre los hosts. Si los datos fallan en algún salto a lo largo del camino, la dirección del último router que respondió al rastreo puede indicar dónde se encuentra el problema o las restricciones de seguridad.

### Tiempo de Ida y Vuelta (RTT)

El uso de traceroute proporciona tiempo de ida y vuelta para cada salto a lo largo del camino e indica si un salto no responde. El tiempo de ida y vuelta es el tiempo que tarda un paquete en llegar al host remoto y que la respuesta del host regrese. Se utiliza un asterisco (\*) para indicar un paquete perdido o sin respuesta.

Esta información se puede usar para localizar un router problemático en la ruta o puede indicar que el router está configurado para no responder. Si en la pantalla se muestran tiempos de respuesta elevados o pérdidas de datos de un salto en particular, esto constituye un indicio de que los recursos del router o sus conexiones pueden estar sobrecargados.

### TTL de IPv4 y Límite de Saltos de IPv6

Traceroute utiliza una función del campo TTL en IPv4 y el campo Límite de Salto en IPv6 en los encabezados de Capa 3, junto con el mensaje de ICMP Tiempo Excedido.

En la secuencia puede observarse cómo traceroute aprovecha el TTL.

 <div style="padding-left: 5%;">
 	<div style="font-size: 1.5em;"><b>TTL=1</b></div>
	<img style="float: left;width: 45%; border: black 1px solid;" src="./img/tracert-01.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-02.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-03.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-04.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-05.png" />
	<div style="clear: both;" />
	<br />
 	<div style="font-size: 1.5em;"><b>TTL=2</b></div>
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-06.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-07.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-08.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-09.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-10.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-11.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-12.png" />
	<div style="clear: both;" />
	<br />
 	<div style="font-size: 1.5em;"><b>TTL=3</b></div>
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-13.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-14.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-15.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-16.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-17.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-18.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-19.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-20.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-21.png" />
	<div style="clear: both;" />
	<br />
 	<div style="font-size: 1.5em;"><b>TTL=4</b></div>
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-22.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-23.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-24.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-25.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-26.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-27.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-28.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-29.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-30.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-31.png" />
	<div style="clear: both;" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-32.png" />
	<img style="float: left;width: 45%; border: black 1px solid" src="./img/tracert-33.png" />
	<div style="clear: both;" />
</div>

## Packet Tracer - Verificar el Direccionamiento IPv4 e IPv6
* <a href="./notes/pt_verificar_direccionamiento.md" target="_blank">Actividad</a>

## Packet Tracer - Usar Ping y Traceroute para Probar la Conectividad de Red
* <a href="./notes/pt_ping_traceroute_probar_conectividad.md" target="_blank">Actividad</a>

# Resumen
## Packet Tracer - Utilizar ICMP para Probar y Corregir la Conectividad de Red
* <a href="./notes/pt_icmp_probar_corregir_conectividad.md" target="_blank">Actividad</a>

## Mensajes ICMP
Aunque IP es sólo un protocolo de mayor esfuerzo, el conjunto TCP/IP proporciona mensajes de error y mensajes informativos cuando se comunica con otro dispositivo IP. Estos mensajes se envían mediante los servicios de ICMP. El objetivo de estos mensajes es proporcionar respuestas acerca de temas relacionados con el procesamiento de paquetes IP en determinadas condiciones, no es hacer que IP sea confiable. El protocolo ICMP está disponible tanto para IPv4 como para IPv6. El protocolo de mensajes para IPv4 es ICMPv4. ICMPv6 proporciona estos mismos servicios para IPv6, pero incluye funcionalidad adicional.

Se puede utilizar un mensaje de eco ICMP para probar la accesibilidad de un host en una red IP. El host local envía una solicitud de eco ICMP a un host. Si el host se encuentra disponible, el host de destino responde con una respuesta de eco.

Cuando un host o gateway recibe un paquete que no puede entregar, puede utilizar un mensaje ICMP de destino inalcanzable para notificar al origen que el destino o el servicio son inalcanzables. El mensaje incluye un código que indica el motivo por el cual no se pudo entregar el paquete.

Los enrutadores utilizan los mensajes de Tiempo Superado de ICMPv4 para indicar que un paquete no puede reenviarse debido a que el campo de Tiempo de Duración (TTL) del paquete se disminuyó a 0. Si un router recibe un paquete y disminuye el campo TTL en el paquete IPV4 a cero, descarta el paquete y envía un mensaje de tiempo superado al host de origen.

ICMPv6 también envía un mensaje de tiempo superado si el router no puede reenviar un paquete IPv6 debido a que el paquete caducó. Los mensajes informativos y de error que se encuentran en ICMPv6 son muy similares a los mensajes de control y de error que implementa ICMPv4. Sin embargo, ICMPv6 incluye cuatro nuevos protocolos como parte de ND o NDP, como se muestra a continuación:
* Mensaje de RS
* Mensaje de RA
* Mensaje de NS
* Mensaje de NA

## Pruebas `ping` y `traceroute`
Para probar la conectividad con otro host de una red, se envía una solicitud de eco a la dirección de host mediante el comando `ping`. Si el host en la dirección especificada recibe la solicitud de eco, responde con una respuesta de eco. A medida que se recibe cada respuesta de eco, el comando `ping` proporciona comentarios acerca del tiempo transcurrido entre el envío de la solicitud y la recepción de la respuesta. Esto puede ser una medida del rendimiento de la red. El comando `ping` tiene un valor de tiempo de espera para la respuesta. Si no se recibe una respuesta dentro del tiempo de espera, el comando `ping` proporciona un mensaje que indica que no se recibió una respuesta.

Los tipos de pruebas de conectividad que se realizan con `ping` son los siguientes:

* __Hacer `ping` a loopback local__. El `ping` se puede usar para probar la configuración interna de IPv4 o IPv6 en el host local. Para realizar esta prueba, se debe hacer `ping` a la dirección de loopback local.
* __Hacer `ping` a la puerta de enlace predeterminada__. Esto generalmente se hace haciendo `ping` a la dirección IP de la puerta de enlace predeterminada del host. Un `ping` exitoso a la puerta de enlace predeterminada indica que el host y la interfaz del enrutador que sirven como puerta de enlace predeterminada están operativos en la red local.
* __Hacer `ping` al host remoto__. Un `ping` exitoso a través de la red interna confirma la comunicación en la red local, el funcionamiento del enrutador que actúa como puerta de enlace predeterminada y el funcionamiento de todos los demás enrutadores que pueden estar en la ruta entre la red local y la red de el anfitrión remoto.

`tracert` es una utilidad que genera una lista de saltos que se alcanzaron con éxito a lo largo de la ruta. Esta lista puede proporcionar información importante sobre la verificación y la solución de problemas. Si los datos llegan al destino, el rastreo indica la interfaz de cada router que aparece en la ruta entre los hosts. Si los datos fallan en algún salto a lo largo del camino, la dirección del último router que respondió al rastreo puede indicar dónde se encuentra el problema o las restricciones de seguridad.

El tiempo de ida y vuelta es el tiempo que tarda un paquete en llegar al host remoto y que la respuesta del host regrese. Se utiliza un asterisco (\*) para indicar un paquete perdido o sin respuesta. Traceroute utiliza una función del campo TTL en IPv4 y el campo Límite de Salto en IPv6 en los encabezados de Capa 3, junto con el mensaje de ICMP Tiempo Excedido.

# Enlaces de interés
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<a href="#12-icmp">⬆️</a>
<a href="./00-Curso.md"><< Menú principal del módulo</a>