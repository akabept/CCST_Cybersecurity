<title coding="utf-8">Recopilación de información del sistema después de un incidente</title>

# Recopilación de información del sistema después de un incidente
# Objetivos
* Recopilar información del sistema después de que se haya producido un incidente.
* Ver registros de posibles intrusiones.

# Trasfondo/Situación
Cuando ocurre un incidente en la organización, la persona responsable debe saber cómo responder. Una organización debe desarrollar un plan de respuesta ante los incidentes y constituir un equipo de Respuesta ante los Incidentes de Seguridad Informática (CSIRT) para administrar la respuesta. En esta práctica de laboratorio, recopilará información del sistema y revisará los registros después de que se haya producido un incidente. Realizar estas tareas inmediatamente después del incidente es importante porque los datos que residen en la RAM desaparecerán cuando se apague el sistema.

# Recursos necesarios
* PC con CSE-LABVM instalado en Virtualbox.

# Instrucciones
## Paso 1: Abrir una ventana de terminal en CSE-LABVM
1. Inicie CSE-LABVM.
2. Haga doble clic en el icono de Terminal para abrir un terminal.

## Paso 2: Recopilar información volátil del sistema comprometido.
En este paso, creará un archivo llamado report.txt que incluye una variedad de información del sistema que puede utilizarse para el análisis de incidentes. Este informe puede transferirse a una unidad USB, enviarse por correo electrónico o cargarse en un servidor en la nube para conservar la información. Luego, se puede desactivar el sistema.
1. Cambie al usuario root con el comando sudo su. Introduzca password como la contraseña de raíz
```shell
cisco @ labvm: ~ $ sudo su
[sudo] password for cisco: password
root@labvm:/home/cisco#
```
2. Ingrese el comando echo y especifique un encabezado para un archivo recién creado llamado report.txt. Ingrese el comando cat para revisar el nuevo archivo.
```shell
root@labvm:/home/cisco# echo Informe de Incidente del Investigador > report.txt
root@labvm:/home/cisco# cat report.txt
Informe de Incidente del Investigador
root@labvm:/home/cisco#
```
3. Ingrese el comando date y redirija la fecha y la marca de tiempo al archivo report.txt. Asegúrese de utilizar corchetes de doble ángulo (>>) para agregar al archivo report.txt. De lo contrario, reemplazará el contenido anterior.
__Nota__: Para documentar mejor el contenido almacenado en report.txt, utilice el comando echo para agregar un subencabezado como se muestra aquí para la Fecha y hora de inicio. Cada subpaso especificará un subencabezado para que agregue antes de recopilar información.
```shell
root@labvm:/home/cisco# echo===== Fecha y hora de inicio ===== >> report.txt
root@labvm:/home/cisco#date >> report.txt
```
4. Ingrese el comando uname para imprimir la información del sistema. Utilice la opción -a para agregar toda la información del sistema al archivo report.txt.
```shell
root@labvm:/home/cisco# echo ===== Información del sistema ===== >> report.txt
root@labvm:/home/cisco# uname -a >> report.txt
```
5. Ingrese el comando ifconfig -a y agregue toda la información de la interfaz de red al archivo report.txt.
```shell
root@labvm:/home/cisco# echo ===== Interfaces de red ===== >> report.txt
root@labvm:/home/cisco# ifconfig -a >> report.txt
```
6. El comando netstat puede recopilar todas las estadísticas de la red. Ingrese el comando con las opciones -ano para recopilar datos en todos los sockets (-a), direcciones IP en lugar de nombres de dominio (-n) e información relacionada con los tiempos de red (-o). Agregue la salida al archivo report.txt.
```shell
root@labvm:/home/cisco# echo =====Estadísticas de red===== >> report.txt
root@labvm:/home/cisco# netstat -ano >> report.txt
```
7. El comando ps reporta una foto de los procesos actuales que se ejecutan en el sistema. Ingrese el comando con las opciones -axu para enumerar todos los procesos que se ejecutan en el sistema (-a y -x) y en un formato orientado al usuario (-u). Agregue la salida al archivo report.txt.
```shell
root@labvm:/home/cisco# echo =====Procesos===== >> report.txt
root@labvm:/home/cisco# ps axu >> report.txt
```
8. El comando route enumera la tabla de enrutamiento utilizada actualmente por el sistema. Ingrese el comando con la opción -n para enumerar las direcciones IP en lugar de intentar determinar los nombres de host. Agregue la salida al archivo report.txt.
```shell
root@labvm:/home/cisco# echo =====Tabla de Enrutamiento===== >> report.txt
root@labvm:/home/cisco# route -n >> report.txt
```
9. Ingrese el comando date y agregue la fecha y la marca de hora al final del archivo para completar el informe.
```shell
root@labvm:/home/cisco# echo =====Fecha y hora de finalización===== >> report.txt
root@labvm:/home/cisco# date>> report.txt
```
10. Utilice el comando cat y canalice la salida al comando less para ver report.txt página o una línea a la vez. Presione la barra espaciadora para desplazarse hacia abajo por página o presione Intro (Enter) para desplazarse hacia abajo una sola línea. Ingrese q cuando haya terminado.
```shell
root@labvm:/home/cisco# cat report.txt | less
Informe de Incidente del Investigador
===== Fecha y hora de inicio =====
Wed 24 Mar 2021 05:06:53 PM UTC
=====Información del sistema=====
Linux labvm 5.4.0-67-generic #75-Ubuntu SMP Fri Feb 19 18:03:38 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
=====Interfaces de red=====
enp0s3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.2.15  netmask 255.255.255.0  broadcast 10.0.2.255
        inet6 fe80::a00:27ff:feb5:4bb0  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:b5:4b:b0  txqueuelen 1000  (Ethernet)
        RX packets 47719  bytes 36618515 (36.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 31406  bytes 3590109 (3.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2292  bytes 244651 (244.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2292  bytes 244651 (244.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
=====Estadísticas de la red=====
Active Internet connections (servers and established)
<output omitted>
unix  3      [ ]         STREAM     CONNECTED     22100   
unix  3      [ ]         STREAM     CONNECTED     18249   
=====Procesos=====
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.5 101896 10768 ?        Ss   Mar23   0:03 /sbin/init
root           2  0.0  0.0      0     0 ?        S    Mar23   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        I<   Mar23   0:00 [rcu_gp]
<output omitted>
root        5319  0.0  0.0      0     0 ?        I    16:31   0:00 [kworker/0:2-events]
root        5490  0.0  0.1  11492  3332 pts/1    R+   17:06   0:00 ps axu
=====Tabla de enrutamiento=====
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.2.2        0.0.0.0         UG    100    0        0 enp0s3
10.0.2.0        0.0.0.0         255.255.255.0   U     0      0        0 enp0s3
10.0.2.2        0.0.0.0         255.255.255.255 UH    100    0        0 enp0s3
===== Fecha y hora de finalización =====
Wed 24 Mar 2021 05:06:53 PM UTC
(END) q
root@labvm:/home/cisco#
```

## Paso 3: Analizar diferentes archivos de registro y conocer su importancia.
Además de capturar la información almacenada en la RAM, el sistema también mantiene una variedad de registros que debe revisar después de un incidente. Estos archivos de registro también pueden agregarse a su archivo report.txt o almacenarse por separado del sistema en caso de que el sistema deba eliminarse. Los registros de particular interés incluyen, entre otros, los siguientes:
* auth.log - registra información de autorización del sistema
* btmp.log - registra intentos fallidos de inicio de sesión
* wtmp.log - registra quién ha iniciado sesión actualmente en el sistema

1. Utilice el comando cat para ver auth.log y canalizarlo al comando less. Presione la barra espaciadora para desplazarse hacia abajo por página o presione Intro para desplazarse hacia abajo una sola línea. Ingrese q cuando haya terminado Su salida será diferente.
```shell
root@labvm:/home/cisco# cat /var/log/auth.log | less
Mar 18 21:43:57 labvm sshd[375]: Server listening on 0.0.0.0 port 22.
Mar 18 21:43:57 labvm sshd[375]: Server listening on :: port 22.
Mar 18 21:43:57 labvm systemd-logind[366]: New seat seat0.
Mar 18 21:43:57 labvm systemd-logind[366]: Watching system buttons on /dev/input/event0 (Power Button)
Mar 18 21:43:57 labvm systemd-logind[366]: Watching system buttons on /dev/input/event1 (Sleep Button)
Mar 18 21:43:57 labvm systemd-logind[366]: Watching system buttons on /dev/input/event2 (AT Translated Set 2 keyboard)
Mar 18 21:43:59 labvm sshd[408]: error: kex_exchange_identification: Connection closed by remote host
Mar 18 21:43:59 labvm sshd[407]: Accepted password for cisco from 10.0.2.2 port 57067 ssh2
Mar 18 21:43:59 labvm sshd[407]: pam_unix(sshd:session): session opened for user cisco by (uid=0)
Mar 18 21:43:59 labvm systemd-logind[366]: New session 1 of user cisco.
<output omitted>
(END) q
root@labvm:/home/cisco#
```
2. El último comando muestra una lista de los últimos usuarios conectados. Ingrese el comando con la opción -f para especificar el archivo de registro. El archivo de registro btmp muestra intentos fallidos de inicio de sesión. Su salida será diferente.
```shell
root@labvm:/home/cisco# last -f /var/log/btmp
UNKNOWN  tty6                          Thu Mar 18 21:47    gone - no logout
UNKNOWN  tty4                          Thu Mar 18 21:47    gone - no logout
UNKNOWN  tty3                          Thu Mar 18 21:47    gone - no logout
cisco    tty1                          Thu Mar 18 21:47    gone - no logout
cisco    tty1                          Thu Mar 18 21:47 - 21:47  (00:00)
btmp begins Thu Mar 18 21:47:05 2021
root@labvm:/home/cisco#
```
3. Ingrese el comando last nuevamente especificando el archivo wtmp para mostrar quién está actualmente conectado al sistema. Su salida será diferente.
```shell
root@labvm:/home/cisco# last -f /var/log/wtmp
cisco    tty7         :0               Tue Mar 23 19:38    gone - no logout
reboot   system boot  5.4.0-67-generic Tue Mar 23 14:38   still running
cisco    tty2                          Thu Mar 18 21:47 - 21:47  (00:00)
reboot   system boot  5.4.0-67-generic Thu Mar 18 21:43 - 22:02  (00:18)
wtmp begins Thu Mar 18 21:43:54 2021
```
4. Ingrese el comando exit para volver al usuario de Cisco.
```shell
root@labvm:/home/cisco# exit
cisco@labvm:~$
```