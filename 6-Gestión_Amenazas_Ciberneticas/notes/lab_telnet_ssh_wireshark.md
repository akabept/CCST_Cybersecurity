<title coding="utf-8">Cifrar y descifrar datos con una herramienta de hacker</title>

# Práctica de laboratorio - Uso de Wireshark para comparar el tráfico de Telnet y SSH
# Objetivos
●   Utilice Wireshark para capturar el tráfico del navegador web.

●   Utilice Wireshark para capturar el tráfico de Telnet

●   Utilice Wireshark para capturar el tráfico de Telnet

Trasfondo/Situación
Wireshark es un analizador de protocolos de red que le permite ver lo que sucede en su red a un nivel microscópico. Puede capturar paquetes y almacenarlos para su análisis. Wireshark incluye muchas herramientas para una inspección profunda de cientos de protocolos de red. En esta práctica de laboratorio, utilizará Wireshark para capturar e inspeccionar el tráfico web, el tráfico de Telnet y el tráfico de SSH.

Recursos necesarios
PC con CSE-LABVM instalada en VirtualBox

Instrucciones
Paso 1: Abra una ventana de terminal en CSE-LABVM.
a.     Inicie CSE-LABVM.

b.     Haga doble clic en el icono de Terminal para abrir un terminal.

Paso 2: Explorar el analizador de protocolos Wireshark.
a.     Para capturar tráfico en su VM, debe ejecutar Wireshark en modo promiscuo, lo que requiere ejecutar privilegios escalados utilizando sudo. Ingrese el comando sudo cableshark y luego introduzca la password para la contraseña. Se abrirá la interfaz gráfica de usuario (GUI) de Wireshark.

cisco@labvm:~$ sudo wireshark

[sudo] password for cisco: password

QStandardPaths: XDG_RUNTIME_DIR not set, defaulting to '/tmp/runtime-root'

b.     En la lista de interfaces, seleccione cualquiera y haga clic en Capture> Start en los menús. Alternativamente, puede hacer clic en el icono de aleta de tiburón. Wireshark comenzará a capturar paquetes.

c.     Si ya tiene Firefox abierto, es posible que vea tráfico capturado en la interfaz de Wireshark. Si Firefox no está abierto, continúe y ábralo ahora. En Wireshark, ahora debería ver el tráfico TCP capturado en el tercio superior de la ventana.

d.     En Firefox, ingrese a www.cisco.com para visitar el sitio web de Cisco. Después de que se cargue el sitio web, puede cerrar Firefox.

e.     Vuelva a Wireshark y haga clic en Capture> Stop en los menús. Alternativamente, puede hacer clic en el botón del cuadrado rojo junto a la aleta de tiburón.

f.     En Wireshark, verá el campo de filtro y tres paneles clave o áreas de trabajo:

=  El campo Aplicar un filtro de visualización está directamente debajo de la barra de herramientas.

=   El panel Lista de paquetes incluye las siguientes columnas para cada paquete capturado:

o    No - el número del paquete (en orden numérico).

o    Hora - la marca de tiempo del paquete

o    Origen - Dirección IP de origen origen del paquete

o    Destino - Dirección IP de destino destino del paquete

o    Protocolo - el protocolo del paquete

o    Longitud - la cantidad de bytes capturados para este paquete

o    Información - información adicional sobre el contenido del paquete

=    El panel Detalles del paquete muestra los protocolos y los campos de protocolo del paquete seleccionado. Observe que los campos se pueden expandir o contraer haciendo clic en la flecha junto al campo.

=    El panel Bytes de paquete muestra los detalles de bytes del paquete seleccionado. A medida que selecciona partes del paquete en el panel Detalles del paquete, los bytes correspondientes se resaltan en el panel Bytes del paquete. El lado izquierdo muestra la representación hexadecimal de los bytes, y el lado derecho muestra la representación ASCII.

Paso 3: Capturar y analizar el tráfico de Telnet sin cifrar.
a.     Comience una nueva captura. En el cuadro de diálogo Paquetes no guardados…, haga clic en Continue without Saving (Continuar sin guardar). Esto eliminará los paquetes de su última captura y comenzará una nueva captura.

b.     Haga doble clic en el icono de Terminal para abrir un terminal.

c.     Puede simular un inicio de sesión remoto en su VM ingresando el comando telnet localhost y luego iniciando sesión como cisco con password como contraseña.

cisco@labvm:~$ telnet localhost

Trying ::1...

Trying 127.0.0.1...

Connected to localhost.

Escape character is '^]'.

Ubuntu 20.04.2 LTS

labvm login: cisco

Password: password

Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-67-generic x86_64)

 * Documentation:  https://help.ubuntu.com

 * Management:     https://landscape.canonical.com

 * Support:        https://ubuntu.com/advantage

0 updates can be installed immediately.

0 of these updates are security updates.

Last login: Thu Mar 18 21:47:23 UTC 2021 on tty2

cisco@labvm:~$

d.     Ingrese el comando exit para finalizar la sesión de Telnet:

cisco@labvm:~$ exit

logout

Connection closed by foreign host.

cisco@labvm:~$

e.     Regrese a Wireshark y detenga la captura.

f.      En el campo Aplicar un filtro de pantalla, escriba telnet y presione Enter (Intro) para filtrar solo los paquetes de Telnet.

g.     En la barra de herramientas, haga clic en el icono de la lupa para buscar un paquete. Ahora se muestran funciones de búsqueda adicionales debajo del campo Aplicar filtro de visualización.

h.     Haga clic en las flechas junto a Filtro de visualización y cámbiela a String (Cadena). Luego haga clic en las flechas junto a la lista de paquetes y cámbiela a Detalles del paquete.

i.     Para encontrar el paquete que solicita la información de inicio de sesión, escriba labvm login: en el campo junto a Cadena, y luego presione Enter o haga clic en Buscar. Wireshark resaltará el paquete que contiene la cadena de texto "labvm login:".

j.      En el panel Detalles del paquete, haga clic en la flecha junto a Telnet para expandir su contenido. Debería ver que labvm login: son los datos para este paquete. Los datos para el paquete también se muestran en el panel Packet Bytes. Se nota que el texto se envió sin cifrar porque puede leerlo.

k.      En el panel Lista de paquetes, haga clic en el paquete resaltado conlabvm login como datos para seleccionarlo.

l.      Para encontrar el nombre de usuario y la contraseña, use la flecha hacia abajo en el teclado para seleccionar el siguiente paquete. En el panel Detalles del paquete, verá que el valor para Data (Datos) bajo Telnet es la primera letra que ingresó en el campo para el mensaje "labvm login:", que era c para cisco. Si vuelve a hacer clic en la flecha hacia abajo, verá que el siguiente paquete de datos también es c. Esto se debe a que el paquete aparece dos veces: una vez para el envío de origen al destino y otra vez para el destino que recibe el paquete. Dado que el origen y el destino son la misma interfaz (loopback 127.0.0.1), Wireshark enumera el paquete dos veces.

m.   Continúe presionando la tecla de flecha hacia abajo hasta llegar al último paquete con un valor de datos o para el nombre de usuario cisco.

n.     Siga haciendo clic en la flecha hacia abajo hasta que vea Password: en el campo Data. Continúe presionando la flecha hacia abajo para leer los datos de los siguientes ocho paquetes que revelan, una letra a la vez, que password es la contraseña del usuario cisco.

o.     Si continúa presionando la flecha hacia abajo en el resto de los paquetes capturados, verá todo el texto enviado y recibido durante la sesión de Telnet, incluidos el comando exit y el mensaje logout.

Paso 4: Capturar y analizar el tráfico SSH cifrado.
a.     Comience una nueva captura. En el cuadro de diálogo Paquetes no guardados…, haga clic en Continue without Saving (Continuar sin guardar). Esto eliminará los paquetes de su última captura y comenzará una nueva captura.

b.     Regrese a la ventana de terminal abierta o inicie una nueva sesión de terminal.

c.     Para simular un inicio de sesión SSH, introduzca el comando ssh localhost. Si es la primera vez que utiliza el comando, el sistema le advierte sobre la autenticidad de localhost y le pregunta si desea continuar. Ingrese yes y luego password como contraseña para iniciar sesión.

cisco@labvm:~$ ssh localhost

The authenticity of host 'localhost (::1)' can't be established.

ECDSA key fingerprint is SHA256:lEvtfM55v9O8L88uvZ4Em/UL4ARo8jWGE1hV8mVnDhQ.

Are you sure you want to continue connecting (yes/no/[fingerprint])? yes

Warning: Permanently added 'localhost' (ECDSA) to the list of known hosts.

cisco@localhost's password: password

Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-67-generic x86_64)

 * Documentation:  https://help.ubuntu.com

 * Management:     https://landscape.canonical.com

 * Support:        https://ubuntu.com/advantage

0 updates can be installed immediately.

0 of these updates are security updates.

Last login: Thu Mar 25 14:01:58 2021 from localhost

cisco@labvm:~$

d.     Ingrese el comando exit para finalizar la sesión de SSH

e.     Regrese a Wireshark y detenga la captura. Si dejó telnet como término de búsqueda en el campo Aplicar filtro de visualización, no se enumerarán paquetes. Cambie el término de búsqueda de telnet a ssh. Todos los paquetes de la sesión SSH ahora deben mostrarse en el panel Lista de paquetes.

f.      En el panel Detalles del paquete, expanda los campos del protocolo SSH para ver el contenido. En el panel Lista de paquetes, haga clic en el primer paquete y luego use la flecha hacia abajo para ver una variedad de paquetes SSH. Observe que el campo Datos para el protocolo SSH muestra que todos los datos están cifrados.