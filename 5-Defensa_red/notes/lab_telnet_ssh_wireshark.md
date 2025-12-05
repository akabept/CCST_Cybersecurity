<title coding="utf-8">Examinar Telnet y SSH en Wireshark</title>

# Práctica de laboratorio. Examinar Telnet y SSH en Wireshark
# Objetivos
* __Parte 1__: Examinar una sesión de Telnet con Wireshark.
* __Parte 2__: Examinar una sesión de SSH con Wireshark.

# Trasfondo/Situación
En esta actividad de laboratorio configurarán un router para que acepte conectividad de SSH y Wireshark para capturar y ver sesiones de Telnet y SSH. Esto demostrará la importancia del cifrado con SSH.

# Recursos necesarios
* Máquina virtual Security Workstation

# Instrucciones
## Parte 1: Examinar una sesión de Telnet con Wireshark
Utilizarán Wireshark para capturar y ver los datos transmitidos de una sesión de Telnet.

### Paso 1: Capture los datos.
1. Inicie la máquina virtual Security Workstation e inicie sesión con el usuario analyst y la contraseña cyberops.
2. Abra una ventana de terminal e inicie Wireshark.
	```shell
	[analyst@secOps ~]$ wireshark &
	```
3. Inicie una captura de Wireshark en la interfaz Loopback: lo.
4. Abra otra ventana de terminal. Inicien una sesión de Telnet a host local. Introduzca el nombre de usuario analyst y la contraseña cyberops cuando el sistema se lo solicite. Tenga en cuenta que puede tardar varios minutos para que aparezcan los indicadores "conectado al host local" e inicio de sesión.
	```shell
	[analyst@secOps ~]$ telnet localhost
	Trying ::1...
	Connected to localhost.
	Escape character is '^]'.
	 
	Linux 4.10.10-1-ARCH (unallocated.barefruit.co.uk) (pts/12)
	 
	secOps login: analyst
	Password:
	Last login: Fri Apr 28 10:50:52 from localhost.localdomain
	[analyst@secOps ~]$
	```
5. Detenga la captura de Wireshark después de haber ingresado las credenciales de usuario.

### Paso 2: Examinar la sesión de Telnet.
1. Aplique un filtro que solo muestre tráfico relacionado con Telnet. Introduzca `telnet` en el campo de filtro y haga clic en `Apply`.
2. Haga clic derecho sobre una de las líneas `Telnet` en la sección `Packet list` de Wireshark y, en la lista desplegable, seleccione `Follow > TCP Stream`.
3. La ventana Follow TCP Stream muestra los datos para su sesión de Telnet con la máquina virtual Security Workstation. Toda la sesión se muestran como texto plano, incluida la contraseña. Observen que el nombre de usuario que introdujeron aparece con caracteres duplicados. Esto se debe al ajuste de eco en Telnet para permitirle ver los caracteres que escribe en la pantalla.
4. Cuando termine de revisar la sesión de Telnet en la ventana `Follow TCP Stream` , haga clicen `Close`.
5. Escriba `exit` en el terminal para salir de la sesión de Telnet.
	```shell
	[analyst@secOps ~]$ exit
	```

## Parte 2: Examinar una sesión de SSH con Wireshark
En la Parte 2 establecerán una sesión de SSH con el host local. Se usará Wireshark para capturar y ver los datos de esta sesión de SSH.
1. Inicie otra captura de Wireshark usando la interfaz `Loopback: lo`.
2. Establecerá una sesión SSH con localhost. En el cursor de la ventana de terminal introduzca `ssh localhost`. Introduzca `yes` para seguir con la conexión. Introduzca `cyberops` cuando el sistema se lo solicite.
	```shell
	[analyst@secOps ~]$ ssh localhost
	The authenticity of host 'localhost (::1)' can't be established.
	ECDSA key fingerprint is SHA256:1xZuV8NMeVsNQPRrzVf9nXHzdUP+EtgVouZVbWH80XA.
	Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
	Warning: Permanently added 'localhost' (ECDSA) to the list of known hosts.
	analyst@localhost's password:
	Last login: Sat May 23 10:18:47 2020Stop the Wireshark capture.
	```
3. Aplique un filtro SSH a los datos de la captura de Wireshark. Introduzca `ssh` en el campo de filtro y haga clic en `Apply`.
4. Haga clic con el botón derecho en una de las líneas `SSHv2` en la sección `Packet list` de Wireshark y, en la lista desplegable, seleccione `Follow > TCP Stream`.
5. Examine la ventana `Follow TCP Stream` en su sesión SSH. Los datos se cifraron y son ilegibles. Compare los datos de la sesión de SSH con los datos de la sesión de Telnet.
6. Luego de haber examinado su sesión SSH haga clic en `Close`.
7. Cierre Wireshark.

## Pregunta de reflexión
* ¿Por qué se prefiere SSH en lugar de Telnet para conexiones remotas?