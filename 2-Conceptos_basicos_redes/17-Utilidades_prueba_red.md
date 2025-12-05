<a href="./00-Curso.md"><< Menú principal del módulo</a>

# 17. Utilidades de prueba de red
## Comandos de solución de problemas
### Descripción General de los Caomandos de Solución de Problemas
Existen varias utilidades de software disponibles que permiten ayudar a identificar problemas de redes. La mayoría de estas utilidades se proporciona con el sistema operativo como comandos de interfaz de línea de comandos. La sintaxis de los comandos puede variar según el sistema operativo.

Éstas son algunas de las utilidades disponibles:

* __ipconfig__. Muestra información de la configuración IP.
* __ping__. Prueba las conexiones con otros hosts IP.
* __netstat__. Muestra las conexiones de red.
* __tracert__. Muestra la ruta exacta recorrida hasta el destino.
* __nslookup__. Directamente solicita al servidor de nombres información sobre un dominio de destino.

### El comando _ipconfig_
Cuando un dispositivo no obtiene una dirección IP o tiene una configuración de IP incorrecta, no puede comunicarse en la red ni acceder a Internet. En dispositivos Windows, puede ver la información de configuración IP con el comando `ipconfig` en la línea de comandos. El comando `ipconfig` tiene varias opciones útiles, como `/all`, `/release` y `/renew`.

* `ipconfig` se utiliza para ver información sobre la configuración IP actual de un host. Al ejecutar este comando desde la línea de comandos se muestra la información de configuración básica que incluye: dirección IP, máscara de subred y puerta de enlace predeterminada.
* `/all` muestra información adicional, que incluye la dirección MAC y las direcciones IP de la puerta de enlace predeterminada y los servidores DNS. También indica si DHCP está activado, la dirección del servidor DHCP y la información de arrendamiento. ¿Qué puede aportar esta utilidad en el proceso de resolución de problemas? Sin una configuración IP adecuada, el host no puede participar en comunicaciones por la red. Si el host no conoce la ubicación de los servidores DNS no puede traducir los nombres y convertirlos en direcciones IP.
* `/release` y `renew`, si la información de direccionamiento IP se asigna dinámicamente, el comando `ipconfig /release` liberará los enlaces DHCP actuales. `ipconfig /renew` solicitará información de configuración actualizada del servidor DHCP. Un host puede contener información de configuración IP defectuosa o desactualizada; para volver a adquirir conectividad solo se requiere una simple renovación de esta información. Si después de enviar la configuración IP el host no puede obtener información actualizada del servidor DHCP, es posible que no haya conectividad de red. Verifique que la NIC tenga iluminada una luz de enlace, lo que indica que existe una conexión física con la red. Si esto no soluciona el problema, quizás exista un inconveniente en el servidor DHCP o en las conexiones de red con el servidor DHCP.

### Packet Tracer - Usar el Comando _ipconfig_
#### Objetivos
* Usar el comando `ipconfig` para identificar configuraciones incorrectas en una PC.

#### Aspectos básicos/Situación
El propietario de una pequeña empresa no puede conectarse a Internet desde una de las cuatro PC de la oficina. Todas las PC están configuradas con direcciones IP estáticas que usan la red `192.168.1.0/24`. Las PC deben poder acceder al servidor web `www.cisco.pka`. Use el comando `ipconfig /all` para identificar qué PC está configurada incorrectamente.

#### Instrucciones
* __Parte 1: Verificar las configuraciones__
1. Acceda al símbolo del sistema en cada PC y escriba el comando `ipconfig /all` en el indicador.
2. Examine la configuración de dirección IP, máscara de subred y puerta de enlace predeterminada en cada PC. Asegúrese de registrar esta configuración IP para cada PC a fin de identificar si alguna de ellas está configurada incorrectamente.

* __Parte 2: Corregir configuraciones incorrectas__
1. Seleccione la PC que está configurada incorrectamente.
2. Haga clic en la ficha ___Desktop > IP Configuration___ para corregir la configuración.

### El comando _ping_
Probablemente la utilidad de red más usada sea `ping`. La mayoría de los dispositivos habilitados para IP admiten algún tipo de comando `ping` para probar si los dispositivos de red son accesibles o no a través de la red IP.

Si la configuración IP parece estar correctamente configurada en el host local, a continuación vuelva a probar la conectividad de red mediante el comando `ping`. El comando `ping` puede ir seguido de una dirección IP o del nombre de un host de destino. En el ejemplo, el usuario hace `ping` a la puerta de enlace predeterminada en `10.10.10.1` y luego hace `ping` a `www.cisco.com`.

Al enviar un comando `ping` a una dirección IP, se envía un paquete conocido como solicitud de eco a través de la red a la dirección IP especificada. Si recibe la solicitud de eco, el host de destino responde con un paquete denominado respuesta de eco. Si la fuente recibe la respuesta de eco, la respuesta de la dirección IP específica verifica la conectividad. El `ping` no se realiza correctamente si aparece un mensaje como tiempo de espera de solicitud o falla general.

Si se envía un comando `ping` a un nombre, como `www.cisco.com`, primero se envía un paquete a un servidor DNS para resolver el nombre en una dirección IP. Una vez obtenida la dirección IP, se reenvía la solicitud de eco a la dirección IP y se continúa el proceso. Si el comando `ping` enviado a la dirección IP funciona, pero el `ping` enviado al nombre no, es muy probable que exista un problema con DNS.

### Resultados de _ping_
Si los comandos de `ping` enviados tanto al nombre como a la dirección IP son exitosos, pero el usuario aún no puede acceder a la aplicación, lo más probable es que el problema resida en la aplicación en el host de destino. Por ejemplo: quizás no se esté ejecutando el servicio solicitado.

Si no funciona ninguno de los dos comandos `ping`, es muy probable que el problema sea la conectividad de red en la ruta hacia el destino. De suceder esto, lo habitual es enviar un comando `ping` a la puerta de enlace predeterminada. Si este comando `ping` funciona correctamente, el problema no es local. Si el comando `ping` enviado a la puerta de enlace predeterminada falla, entonces el problema reside en la red local.

En algunos casos, el `ping` puede fallar pero la conectividad de red no es el problema. Un `ping` puede fallar debido al cortafuegos en el dispositivo emisor o receptor, o un enrutador en la ruta que está bloqueando los `ping`.

El comando `ping` básico suele enviar cuatro ecos y esperar respuestas para cada uno. Sin embargo, esto se puede modificar para incrementar su utilidad. Las opciones presentadas en la figura muestran características adicionales disponibles.

### Packet Tracer - Usar el comando _ping_
#### Objetivos
Usar el comando ping para identificar configuraciones incorrectas en una PC.

#### Aspectos básicos/situación
El dueño de una pequeña empresa descubre que algunos usuarios no pueden acceder a un sitio web. Todas las PC están configuradas con direcciones IP estáticas. Use el comando ping para identificar el problema.

#### Instrucciones
* __Parte 1: Verificar la conectividad__
Acceda a la ficha Desktop (Escritorio) > Web Browser (Navegador web) de cada PC e introduzca la URL `www.cisco.pka`. Identifique las PC que no se pueden conectar con el servidor Web.
__Nota__: Todos los dispositivos requieren un tiempo para realizar el proceso de arranque. Deje pasar hasta un minuto para recibir una respuesta de la Web.
¿Cuáles PC tienen problemas para conectarse al servidor Web?

* __Parte 2: Hacer _ping_ al servidor web desde la PC con problemas de conectividad.__
	1. En la PC, acceda a ___Command Prompt___ desde la pestaña ___Desktop___.
	2. Cuando se le solicite, ingrese `ping www.cisco.pka`.
	¿Obtuvo una respuesta al _ping_? ¿Qué dirección IP se muestra en la respuesta, en caso de existir alguna?

* __Parte 3: Hacer _ping_ al servidor web desde las PC configuradas correctamente.__
	1. En la PC, acceda a ___Command Prompt___ desde la pestaña ___Desktop___.
	2. Cuando se le solicite, ingrese `ping www.cisco.pka`.
	¿El _ping_ produjo una respuesta? ¿Qué dirección IP se devolvió, si la hay?

* __Parte 4: Hacer _ping_ a la dirección IP del servidor web desde la PC con problemas de conectividad.__
	1. En la PC, acceda a ___Command Prompt___ desde la pestaña ___Desktop___.
	2. Intente llegar a la dirección IP del servidor web con el comando _ping_.
	¿El _ping_ produjo una respuesta? De ser así, entonces la PC puede comunicarse con el servidor Web a través de la dirección IP, pero no a través del nombre de dominio. Esto puede indicar un problema en la configuración del servidor DNS en la PC.

* __Parte 5: Comparar la información del servidor DNS en las PC.__
	1. Acceda al ___Command Prompt___ de las PC sin ningún problema.
	2. Con el comando `ipconfig /all`, examine la configuración del servidor DNS en las PC sin ningún problema.
	3. Acceda al ___Command Prompt___ de las PC con problemas de conectividad.
	4. Con el comando `ipconfig /all`, examine la configuración del servidor DNS en las PC con problemas de conectividad. ¿Coinciden las dos configuraciones?

* __Parte 6: Realizar los cambios de configuración necesarios en las PC.__
	1. Navegue a la pestaña __Desktop__ de las PC con problemas y haga los cambios de configuración necesarios en ___IP Configuration___.
	2. Mediante el __Web Browser__ dentro de la ficha __Desktop__, conéctese con `www.cisco.pka` para verificar que los cambios de configuración hayan resuelto el problema.

## Resumen
### Comandos de solución de problemas
Hay disponibles varios programas de utilidad de software que pueden ayudar a identificar problemas de red. El sistema operativo proporciona la mayoría de estas utilidades como comandos CLI.

Éstas son algunas de las utilidades disponibles:

* ___ipconfig___: Muestra información de la configuración IP
* ___ping___: Prueba las conexiones con otros hosts IP
* ___netstat___: Muestra las conexiones de red
* ___tracert___: Muestra la ruta exacta recorrida hasta el destino
* ___nslookup___: Directamente solicita al servidor de nombres información sobre un dominio de destino

El comando `ipconfig` se utiliza para ver información sobre la configuración IP actual de un _host_. Al ejecutar este comando desde la línea de comandos se muestra la información de configuración básica que incluye: dirección IP, máscara de subred y puerta de enlace predeterminada.

El comando `ipconfig /all` muestra información adicional, que incluye la dirección MAC y las direcciones IP de la puerta de enlace predeterminada y los servidores DNS. También indica si DHCP está activado, la dirección del servidor DHCP y la información de arrendamiento.

Si la información de direccionamiento IP se asigna dinámicamente, el comando `ipconfig /release` liberará los enlaces DHCP actuales. `ipconfig /renew` solicitará información de configuración actualizada del servidor DHCP. Un _host_ puede contener información de configuración IP defectuosa o desactualizada; para volver a adquirir conectividad solo se requiere una simple renovación de esta información.

Probablemente la utilidad de red más usada sea _ping_. La mayoría de los dispositivos habilitados para IP admiten algún tipo de comando _ping_ para probar si los dispositivos de red son accesibles o no a través de la red IP. Al enviar un comando _ping_ a una dirección IP, se envía un paquete conocido como solicitud de eco a través de la red a la dirección IP especificada. Si recibe la solicitud de eco, el _host_ de destino responde con un paquete denominado respuesta de eco. Si la fuente recibe la respuesta de eco, la respuesta de la dirección IP específica verifica la conectividad.

## Enlaces de interés
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<a href="#17-utilidades-de-prueba-de-red">⬆️</a>
<a href="./00-Curso.md"><< Menú principal del módulo</a>