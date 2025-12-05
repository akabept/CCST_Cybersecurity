# Packet Tracer: Utilizar los comandos show de Cisco IOS
## Objetivos
* Utilizar los comandos show de Cisco IOS

## Aspectos básicos/situación
Los comandos show de Cisco IOS se usan muy frecuentemente al trabajar con equipos Cisco. En esta actividad, usaremos los comandos show en un router ubicado en un ISP.

## Instrucciones
### Parte 1: Conectarse al router Cisco 4321 del ISP.
En esta parte, utilizará el software de emulación de terminal en la PC del ISP para conectarse al enrutador Cisco 4321.
1. Haga clic en ISP PC.
2. Haga clic en la ficha Desktop (Escritorio). Seleccione Terminal. Revise la configuración del terminal y haga clic en OK (Aceptar) para continuar.
3. La línea ISPRouter > indica que está en el modo EXEC de usuarios. Presione Enter (Intro) si la línea de comandos no aparece.

### Parte 2: Aprender los comandos show.
Use la información que muestran los comandos show para responder las siguientes preguntas.

#### Paso 1: Explore los comandos show en el modo EXEC de usuario.
Abrir la ventana de configuración
1. Escriba `show ?` en la línea de comandos.
* Mencione algunos comandos show más que estén disponibles en el modo EXEC de usuario.
2. Escriba `show arp` en el cursor.
* Registre la dirección MAC y la dirección IP
3. Introduzca `show flash` en el cursor
* Registre la imagen de OS que se indica.
4. Escriba `show ip route` en la línea de comandos
* ¿Cuántas rutas aparecen en la tabla?
5. Escriba `show interfaces` en la línea de comandos.
* ¿Qué interfaz se encuentra activa y en funcionamiento?

Interfaz|Estado|Protocolo
:--|:-:|:-:
GigabitEthernet 0/0/0|Activo|
GigabitEthernet 0/0/1||Inactivo
Serial 0/0/0||
Serial 0/0/1|Inactivo|

6. Escriba `show ip interfaces` en la línea de comandos.
* Según la salida del comando, ¿qué interfaz está conectada?
7. Escriba `show version` en la línea de comandos.
* ¿Qué paquete de tecnología está habilitado en este momento en el router?
8. Introducza `show protocols` en el cursor
* ¿Qué protocolos están actualmente habilitados en el enrutador?
9. Ingrese `show running-config` en el cursor.
* ¿Cuál es la salida?

#### Paso 2: Explorar los comandos show en el modo EXEC de usuario.
1. Introduzca enable en la línea de comandos para ingresar al modo EXEC con privilegios.
* Mencione algunos otros comandos show en este modo.
2. Ingrese `show running-config` en el indicador
* ¿Cuál es la salida?