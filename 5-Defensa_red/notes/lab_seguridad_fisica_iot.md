<title coding="utf-8">Implementar la seguridad física con dispositivos de IoT</title>

# Implementar la seguridad física con dispositivos de IoT
# Objetivos
* __Parte 1__: Conectar dispositivos de IoT a la red
* __Parte 2__: Agregar dispositivos de IoT al servidor de registro:
* __Parte 3__: Explorar la funcionalidad de los dispositivos de seguridad de IoT

# Trasfondo/Situación
En un intento por aumentar la seguridad física de su hogar, ha decidido instalar algunos dispositivos de Internet de las cosas (IoT) para permitirle monitorear su hogar de manera remota mientras está fuera. En esta actividad de Packet Tracer instalará un dispositivo de IoT para mejorar la seguridad del hogar. Luego configurará todos los dispositivos de IoT para que se conecten a la red inalámbrica y se comuniquen con un servidor de registro de IoT remoto.

# Instrucciones
## Parte 1: Conectar los dispositivos de IoT a la red
En esta parte conectará los dispositivos de IoT a la red inalámbrica e implementará el filtrado de direcciones MAC.

### Paso 1: Conecte la sirena a la puerta
1. Haga clic en Home y localice Home_Siren y Home Doors en la sala de estar.
2. En la barra de herramientas en la parte inferior, haga clic en Connections > IoT Custom Cable, que es la penúltima opción.
3. Haga clic en Home_Siren > DO interface, y luego haga clic en Home Doors > DO interface.
4. Mantenga presionada la tecla ALT y haga clic en la puerta para abrirla y cerrarla. Observe que abrir la puerta ahora activará la sirena.

### Paso 2: Asocie todos los dispositivos de IoT a la red inalámbrica HomeNet.
El router inalámbrico Home Wireless Router está preconfigurado para usar WPA2-PSK y el filtrado de direcciones MAC para controlar quién puede asociarse con la red y qué dispositivos pueden usar la red para transferir tráfico. Todos los dispositivos nuevos deben cumplir con la configuración actual.
1. Localice los cuatro dispositivos inalámbricos de IoT:
	* Home_Siren
	* Home Doors
	* Home_Motion_Sensor (ventanas de la oficina en el hogar)
	* Home_Webcam (estantería de oficina en el hogar)
2. Haga clic en Home_Sireny luego en la solapa Config > Wireless0.
3. Configure el SSID y el modo de Autenticación.
	* __SSID__: HomeNet
	* __Authentication__: WPA2-PSK
	* __Pass Phrase__: ciscorocks
4. En IP Configuration haga clic en DHCP. Verifique que el dispositivo haya recibido una dirección IP de la red 192.168.0.0/24.
__Nota__: Puede ser necesario alternar entre Static y DHCP para forzar a Packet Tracer a converger en su configuración.
5. Registre la dirección MAC del dispositivo de IoT. Formatee las direcciones con dos puntos entre cada dos números hexadecimales en lugar de un punto entre cada cuatro números hexadecimales. Este formato es necesario para el siguiente paso cuando aplique el filtrado de direcciones MAC.
	* Home_Siren: 
	* Home Doors: 
	* Home_Motion_Sensor: 
	* Home_Webcam: 
6. Repita estos pasos para cada dispositivo de IoT.

### Paso 3: Configure el filtrado de direcciones MAC para permitir los dispositivos de IoT.
1. Haga clic en Home Office PC > solapa Desktop > Web Browser
2. Inicie sesión en el router Home Wireless Router en 192.168.0.1. Use admin para el nombre de usuario y la contraseña.
3. Haga clic en Home Wireless Router > solapa GUI.
4. Haga clic en Wirelessy luego en Wireless MAC Filter.
5. Verifique que el filtro esté habilitado para el puerto inalámbrico de 2,4 GHz y que esté configurado para permitir que las PC accedan a la red inalámbrica.
6. Agregue a la tabla las direcciones MAC de los cuatro dispositivos IoT.
7. Desplácese hasta la parte inferior y haga clic en Save Settings.
8. El router Home Wireless Router se reiniciará. Cierre el Web Browsery luego haga clic en IP Configuration. Si es necesario, alterne los botones DHCP y Static para renovar la configuración de IP de modo que Home Office PC obtenga una dirección IP de la red 192.168.0.0/24.

## Parte 2: Agregue dispositivos de IoT al servidor de registro:
En esta parte se registrará para obtener una cuenta con un servicio de monitoreo remoto de IoT. Luego registrará los dispositivos de IoT para comunicarse con el servicio. Esto le permitirá monitorear de manera remota los dispositivos de IoT a través de un portal web.

### Paso 1: Cree una cuenta en el ISP IoT Registration Server.
1. En Home Office PC cierre IP Configuration y luego haga clic en Web Browser.
2. Vaya a `http://10.3.0.125`.
3. Haga clic en _Sign up now_ y cree una nueva cuenta con el nombre de usuario `HomeUser` y la contraseña `Pa$$w0rd`.

### Paso 2: registre los dispositivos de IoT en el servidor de registro
Cada uno de los cuatro dispositivos de IoT debe estar registrado en un servidor de registro para monitorear y administrar el dispositivo de manera remota. Repita los siguientes pasos para cada dispositivo de IoT.
1. Haga clic en el dispositivo y luego en la solapa Config > Settings en GLOBAL.
2. Desplácese hasta la sección IoT en la parte inferior de la página e ingrese la siguiente información:
	* Seleccione Remote Server
	* Dirección del servidor: 10.3.0.125
	* Nombre de usuario: `HomeUser`
	* Contraseña: `Pa$$w0rd`
3. Haga clic en el botón Connect. El botón cambiará a Connecting y luego a Refresh en unos segundos. El dispositivo de IoT ahora está registrado en el servidor.
__Nota__: Si no cambia a Refresh es posible que haya ingresado la información de manera incorrecta. Por lo tanto, vuelva a ingresar la información y repita este paso.
4. Repita los pasos anteriores para registrar todos los dispositivos de IoT.

### Paso 3: Verifique que todos los dispositivos estén registrados.
1. Regrese al Web Browser en Home Office PC. Si es necesario, vaya a `10.3.0.125` e inicie sesión con el nombre de usuario `HomeUser` y la contraseña `Pa$$w0rd`.
2. Verifique que los cuatro dispositivos de IoT estén registrados en el servidor.

## Parte 3: Explorar la funcionalidad de los dispositivos de seguridad de IoT
En esta parte explorará la funcionalidad de los dispositivos de IoT y supervisará sus estados en el servidor de registro de IoT.

### Paso 1: Observe y controle los dispositivos de IoT desde el servidor de registro.
1. Desde el Web Browser en Home Office PC, haga clic en cada sección para cada dispositivo de IoT para mostrar los detalles del dispositivo.
	* ¿Cuál es el estado de cada dispositivo?
2. Haga clic en el rectángulo rojo debajo de Home Doors para activarlo.
	* ¿Qué ocurrió?
3. Haga clic en el rectángulo de la puerta nuevamente para desactivar el dispositivo.
	* ¿Qué ocurrió?
4. Haga clic en el rectángulo verde de Home_Webcam.
	* ¿Qué ocurrió?
5. Haga clic en el rectángulo verde nuevamente para activar Home_Webcam.
6. Haga clic en el círculo rojo de Home_Motion_Sensor. No pasará nada porque el sensor de movimiento solo envía información al servidor de registro. Este es un ejemplo de un dispositivo que solo se puede monitorear.

### Paso 2: interactúe con los sensores en el hogar.
En Packet Tracer, los dispositivos de IoT normalmente se pueden activar manteniendo presionada la tecla ALT y haciendo clic en el dispositivo (ALT-clic). El sensor de movimiento se activa manteniendo presionada la tecla ALT y moviendo el mouse sobre el sensor. Tenga la pantalla del servidor de registro de IoT visible para estas acciones.
1. Haga ALT-clic sobre la puerta.
	* ¿Qué ocurrió?
2. Haga ALT-clic en la cámara web.
	* ¿Qué ocurrió?
3. Presione la tecla ALT y mueva el mouse sobre el sensor de movimiento.
	* ¿Qué ocurrió?

## Preguntas de reflexión
1. ¿Qué ventajas ofrecen los dispositivos habilitados para IoT para la seguridad del hogar?
2. ¿Cuál es la ventaja de usar un servidor de registro para dispositivos habilitados para IoT?
3. Busca en Internet qué tipos de dispositivos habilitados para IoT se utilizan para la seguridad en el hogar.