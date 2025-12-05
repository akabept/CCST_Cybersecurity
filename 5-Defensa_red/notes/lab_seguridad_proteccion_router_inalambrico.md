<title coding="utf-8">Configuración de seguridad y protección del router inalámbrico</title>

# Packet Tracer: Configurar el fortalecimiento y seguridad del router inalámbrico
# Objetivos
* __Parte 1__: Configurar los ajustes de seguridad básicos de un router inalámbrico
* __Parte 2__: Configurar la seguridad de la red del router inalámbrico
* __Parte 3__: Configurar la seguridad de la red de los clientes inalámbricos
* __Parte 4__: Verificar las configuraciones de conectividad y seguridad

# Trasfondo/Situación
En esta actividad de Packet Tracer configurará la seguridad inalámbrica en un router inalámbrico. Durante la instalación del router, se configuró parcialmente, pero tiene algunos problemas de seguridad que deben abordarse. También fortalecerá el router para ayudar a mitigar posibles ataques. Una vez completada la configuración de seguridad, verificará la conectividad y la configuración de seguridad.
__Nota__: La mayoría de las tareas en esta actividad son calificadas. Haga clic en Check Results en cualquier momento para ver los elementos de evaluación correctos e incorrectos.
__Nota__: El cambio al modo Logical está deshabilitado en esta actividad. Además, las ubicaciones Data Center e ISP/Telco están bloqueadas.

# Instrucciones
## Parte 1: configurar los ajustes de seguridad básicos para un router inalámbrico
La configuración inicial de un router inalámbrico doméstico puede suponer un riesgo de seguridad. Por ejemplo, si los agentes de amenazas conocen su dirección IP pública pueden buscar en Internet las credenciales de inicio de sesión predeterminadas de su router y acceder a su router de manera remota. En esta parte, cambiará la contraseña del router y deshabilitará el inicio de sesión remoto.

### Paso 1: Cambie la contraseña predeterminada del router.
Es importante establecer una contraseña muy segura o una frase de contraseña larga para evitar que usuarios no autorizados cambien las configuraciones en el router.
1. Haga clic en Home, luego en Home Office PC > solapa Desktop > Web Browser.
2. Conéctese al router Home Wireless Router en 192.168.0.1.
3. Ingrese admin como nombre de usuario y contraseña.
4. Haga clic en la solapa Administration y escriba cisconetacadrocks! en ambos campos de contraseña.
5. Desplácese hasta la parte inferior y haga clic en Save Settings.
6. El router solicita que se vuelva a autenticar. Vuelva a iniciar sesión con el usuario admin y la contraseña nueva, y luego haga clic en Continue.

### Paso 2: Deshabilite la administración remota.
Los routers inalámbricos para el hogar generalmente se envían con la configuración remota habilitada. Esto permite que los técnicos de su proveedor de servicios accedan a su dispositivo para ayudarlo a configurar su red doméstica o solucionar problemas. Sin embargo, esto puede ser un riesgo de seguridad porque un puerto debe estar abierto y en escucha para que el técnico se conecte al router. A menudo es posible cambiar el puerto y solo permitir el acceso HTTPS, pero esto no ofrece ninguna medida real de seguridad porque un agente de amenazas puede detectar puertos abiertos e iniciar un ataque de contraseña contra el router. Si la administración remota es realmente necesaria, sería mucho más seguro configurar una solución VPN. El router inalámbrico doméstico en esta actividad de Packet Tracer no admite VPN. Por lo tanto, deshabilitará la administración remota.
1. En la solapa Administration haga clic en Disabled junto a Remote Management.
2. Haga clic en Save Settings.
__Nota__: Este cambio hará que Home Wireless Router se reinicie. Cierre Web Browser y haga clic en Fast Forward Time (Alt+D). Vuelva a Home Office PC y haga clic en IP Configuration para verificar si la dirección IP está reasignada. Si es necesario, alterne entre DHCP y Static hasta que Home Office PC reciba la dirección IP de la red 192.168.0.1/24. Cierre IP Configuration y luego haga clic en Web Browser. Vaya a 192.168.0.1 y vuelva a iniciar sesión para prepararse para la parte siguiente de la actividad.

## Parte 2: Configurar la seguridad de la red del router inalámbrico
En este momento, cualquier persona que tenga un dispositivo inalámbrico en el rango de Home Wireless Router puede conectarse fácilmente y posiblemente tener acceso a dispositivos en la red. Para evitar que esto suceda, en esta parte, protegerá las redes inalámbricas para que solo los dispositivos con la configuración correcta puedan conectarse a las redes.

### Paso 1: Configure y difunda el SSID de HomeNet.
Actualmente, el router no transmite el SSID de las redes configuradas. Esta no es una medida de seguridad generalmente aceptada, principalmente porque si un agente de amenazas buscara una red para atacar, aún vería la red sin nombre. Hay herramientas disponibles para detectar el tráfico para determinar el SSID. De hecho, la práctica de desactivar la transmisión de SSID podría hacer de la red un objetivo más alto para el ataque porque el administrador está intentando ocultarla.
1. Haga clic en la solapa Wireless y luego, en cada una de las tres redes, haga clic en Enabled para SSID Broadcast.
2. Para cada una de las tres redes, cambie el SSID de default a HomeNet.
3. Haga clic en Save Settings.

### Paso 2: Configurar la seguridad de las redes inalámbricas HomeNet.
Quizás la medida de seguridad más importante fuera de cambiar la contraseña del router sea encriptar el tráfico entre el router y los clientes inalámbricos. Sin cifrado, un agente de amenazas puede utilizar herramientas fáciles de obtener y, a menudo, gratuitas para interceptar las comunicaciones con muy poco esfuerzo. Esto puede generar más ataques a medida que el agente de amenaza adquiere conocimientos sobre usted y sus redes.
1. Dentro de la solapa Wireless haga clic en Wireless Security.
2. Para cada una de las tres redes, configure lo siguiente:
	* Security Mode: WPA2 Personal
	* Encryption: AES
	* Passphrase: ciscorocks
3. Haga clic en Save Settings.

### Paso 3: Configurar la seguridad para la red inalámbrica GuestNet.
Este router permite configurar dos redes inalámbricas independientes para cada radio. Esto puede ser útil cuando desea mantener el tráfico de invitados separado del tráfico en sus otras redes.
1. Dentro de la solapa Wireless haga clic en Guest Network.
2. Para cada una de las tres redes haga clic en Enable Guest Profile y luego configure lo siguiente:
	* SSID: GuestNet
	* Broadcast SSID: Enabled
	* Security Mode: WPA2 Personal
	* Encryption: AES
	* Passphrase: guestpass
3. Haga clic en Save Settings.

## Parte 3: Configure los clientes inalámbricos
El router Home Wireless Router ha sido reforzado y se ha configurado la seguridad inalámbrica. En esta parte, conectará de manera segura los clientes inalámbricos a la red.

### Paso 1: Configurar la conectividad inalámbrica de las computadoras portátiles.
1. Haga clic en Home Laptop 1 ubicada en la sala de estar y luego haga clic en la solapa Desktop > PC Wireless.
2. Haga clic en la solapa Connect.
3. Haga clic en la primera entrada de HomeNet y luego en Connect.
4. La seguridad ya está configurada en WPA2-Personal. Ingrese ciscorocks en Pre-shared Key y luego haga clic en Connect.
5. Haga clic en la solapa Link Information. Debería ver el mensaje "You have successfully connected to the access point". Si tidavía no está conectado, revise la configuración de Home Wireless Router y realice este paso nuevamente.
6. Cierre la ventana de PC Wireless y haga clic en IP Configuration. Si la computadora portátil todavía tiene una dirección de la red "169", alterne entre DHCP y Static hasta que reciba una dirección IP de la red 192.168.0.0/24.
7. Repita este paso para Home Laptop 2 en la oficina en casa, pero utilice la primera entrada para GuestNet. Ingrese guestpass como Pre-shared Key.

### Paso 2: Configurar la conectividad inalámbrica de los dispositivos de IoT.
1. En la oficina en el hogar, en el estante superior de la estantería, haga clic en Home_Webcam.
2. Haga clic en Config > Wireless0.
3. Ingrese HomeNet en SSID.
4. Elija WPA2-PSK en Authentication e introduzca ciscorocks en PSK Pass Phrase.
5. En IP Configuration haga clic en DHCP y verifique que el dispositivo haya recibido el direccionamiento IP de la red 192.168.0.0/24. Alterne entre DHCP y Static si es necesario.
6. Repita este paso tanto para Home_Siren, ubicada en la sala de estar sobre la biblioteca, como para Home Doors.

## Parte 4: Verificar las configuraciones de conectividad y seguridad
En esta parte, probará sus configuraciones y ajustes de seguridad para asegurarse de que los dispositivos se comuniquen entre sí y de que puedan conectarse a Internet.

### Paso 1: Pruebe la conectividad a Internet de las computadoras portátiles inalámbricas.
1. Haga clic en Home Laptop 1 > solapa Desktop > Web Browser.
2. Vaya a www.ptsecurity.com. Packet Tracer puede tardar varios segundos en converger. Puede hacer clic en Fast Forward Time (Alt+D) para acelerar el proceso hasta que la página Data Center Public Web cargue.
3. Repita este paso para Home Laptop 2.

### Paso 2: Configure la seguridad para la interconectividad de GuestNet y HomeNet.
Normalmente GuestNet y HomeNet no deberían poder conectarse o compartir recursos. Recuerde que Home Laptop 2 está configurada para la red de invitados y que normalmente no debería tener acceso a los dispositivos de la red doméstica.
1. Utilice cualquier método que desee para determinar la dirección IP de Home Laptop 1.
2. Haga clic en Home Laptop 2 > solapa Desktop > Command Prompt.
3. Ingrese el comando ping seguido de la dirección IP de Home Laptop 1. Home Laptop 1 responde al ping indicando que Home Laptop 2 puede acceder a los dispositivos de la red del hogar. Deberá configurar el router para evitar que los hosts en diferentes redes se comuniquen entre sí.
4. Desde Home Office PC, si es necesario, vuelva a iniciar sesión en la página web de configuración de Home Wireless Router en 192.168.0.1.
5. Haga clic en la solapa Wireless y luego en el submenú Guest Network.
6. Desmarque la casilla junto a Allow guests to see each other and access the local network y luego haga clic en Save Settings.
7. Desde Home Laptop 2 intente hacer ping a Home Laptop 1 nuevamente. Ahora los pings deberían fallar. Esto indica que los hosts no pueden comunicarse entre las dos redes.