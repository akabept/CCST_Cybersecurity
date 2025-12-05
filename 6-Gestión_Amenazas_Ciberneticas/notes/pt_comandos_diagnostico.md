<title coding="utf-8">Uso de comandos de diagnósticorseguridad</title>

# Packet Tracer: Uso de comandos de diagnóstico
# Objetivos
* __Parte 1__: Recopilar la configuración del dispositivo del usuario final.
* __Parte 2__: Recopilar información sobre los dispositivos de red.
* __Parte 3__: Diagnosticar problemas de conectividad.

# Trasfondo/Situación
En esta actividad de Packet Tracer (PT), utilizará varios comandos para recopilar información del dispositivo y solucionar problemas de configuración y conectividad. La información del dispositivo incluye la dirección IP, el gateway predeterminado y la configuración del servidor DNS. Esta configuración es fundamental para permitir que un dispositivo se comunique en redes y se conecte a Internet.

# Instrucciones
## Parte 1: Recopilar la configuración del dispositivo del usuario final
En esta parte, documentará la configuración de la dirección IP para los dispositivos finales.

### Paso 1: Documentar la configuración de la dirección IP para HQ-Laptop-1.
1. La actividad inicia en el clúster de HQ. El armario de cableado es el chasis alto y negro en la esquina inferior izquierda del primer piso. Ubique todos los dispositivos en el primer piso: PC 1.1, 1-2, 1-3 y 1-4; impresora FL-1P; y HQ-Laptop-1.
2. Haga clic en HQ-Laptop-1 > Desktop tab > Command Prompt
3. Ingrese el comando ipconfig.
* ¿Qué dirección IPv4 se muestra para la conexión Wireless0? Puede aparecer como dirección 169.254.0.0/16 porque es posible que la conexión inalámbrica aún no se haya establecido. La dirección estará dentro de la red 192.168.50.0/24.
* Si la dirección IPv4 está en el rango de 169.254.0.0/16, ¿qué método se utiliza para asignar direcciones IPv4? ¿Por qué se le asigna a la computadora portátil una dirección IPv4 en el rango de 169.254.0.0/16? Indica que el dispositivo no pudo obtener el direccionamiento de un servidor DHCP. Por lo tanto, el dispositivo se asignó un grupo de direcciones 169.254.0.0/16 utilizado para el direccionamiento IP privado o (APIPA).
* Si la dirección IPv4 está en 169.254.0.0/16, espere unos segundos y repita el comando ipconfig.
Cuando la dirección IPv4 ya no es del rango 169.254.0.0/16, ¿cuál es la información de direccionamiento IP que se muestra? Registre sus respuestas en la tabla a continuación. 

__Wireless0__|__Información de Direccionamiento IP__
:-|:-
Dirección local de enlace IPv6 (link local)|FE80::20A:F3FF:FEE4:EEAA
Dirección IPv6|::
Dirección IPv4|192.168.50.4 (puede variar, pero estará dentro del rango de 192.168.50.0/24)
Máscara de subred|255.255.255.09
Puerta de enlace predeterminada|192.168.50.1
Servidores DNS|No corresponde

* ¿Ve alguna dirección del servidor DNS? Explique. El comando ipconfig no informa la dirección del servidor DNS.
4. Ingrese el comando ipconfig /all.
* ¿Ve alguna dirección del servidor DNS? ¿De qué se trata esto? 10.2.0.125

### Paso 2: Documentar la configuración de la dirección IP para Net-Admin.
1. Haga clic en Wiring Closet > Net-Admin > Desktop tab > Command Prompt.
2. Ingrese el comando ipconfig /all.
* ¿Cuál es la información de direccionamiento IP que se muestra en la interfaz FastEthernet0? Registre sus respuestas en la tabla a continuación.

__FastEthernet0__|__Información de Direccionamiento IP__
:-|:-
Dirección física|0001.C910.22D6 (puede variar)
Dirección local de enlace IPv6 (link local)|FE80::201:C9FF:FE10:22D6
Dirección IPv6|::
Dirección IPv4|192.168.99.9
Máscara de subred|255.255.255.09
Puerta de enlace predeterminada|192.168.99.1
Servidores DNS|0.0.0.0

## Parte 2: Recopilar información sobre los dispositivos de red
En esta parte, documentará la información sobre el enlace al ISP. Luego documentará la información de direccionamiento IP para todos los dispositivos finales en HQ y descubrirá que los dispositivos pertenecen a diferentes redes de área local virtuales (VLAN).

### Paso 1: Recopilar información de conexión de red sobre el enlace entre HQ e ISP.
El router HQ-Edge es el router entre la red HQ y el ISP. Necesitamos identificar la información del dispositivo ascendente ubicada en el ISP.
1. En el rack izquierdo del armario de cableado, haga clic en la pestaña HQ-Edge> CLI.
2. Presione Enter (Intro) para obtener el indicador HQ-Edge> y luego introduzca el comando enable.
3. Ingrese el comando show ip route | begin Gateway
* ¿Cuál es la dirección del gateway de último recurso (o gateway predeterminado)? 0.0.0.0
* ¿Por qué no se muestra la dirección del siguiente salto? No está configurado explícitamente.
4. Ingrese el comando show running-config | begin ip route.
* ¿Cómo está configurada la ruta predeterminada? ¿Utiliza la dirección del siguiente salto? Se configura con la interfaz de salida en lugar de la dirección del siguiente salto.
5. Ingrese el comando show cdp neighbors detail. 
* ¿Cuál es la dirección IPv4 de la dirección del siguiente salto (ISP)? 10.0.0.49
* ¿Qué puerto del router ISP está conectado a HQ-Edge? GigabitEthernet 1/0
* ¿Qué versión de IOS se utiliza en el router ISP? IOS (tm) PT1000 Software (PT1000-I-M), Version 12.2(28), RELEASE SOFTWARE (fc5)
6. Ingrese el comando ping 10.0.0.49.
7. Introduzca el comando show arp.
* ¿Cuál es la dirección MAC de la interfaz en el router ISP que está conectado a HQ-Edge? 0060.2FE1.903B
8. Cierre HQ-Edge y salga del armario de cableado.

### Paso 2: Recopilar información de conexión de red sobre los dispositivos en HQ.
1. De 1-1, 1-2, 1-3, 1-4, FL-1P y HQ-Laptop-1, use el comando ipconfig para encontrar sus direcciones IPv4 y gateways predeterminados.

__Dispositivo__|__Dirección IPv4__|__Información de Direccionamiento IP__
:-|:-|:-
1-1|192.168.10.2|192.168.10.1
de octubre|192.168.10.3|192.168.10.1
1-3|192.168.20.2|192.168.20.1
1-4|192.168.20.3|192.168.20.1
FL-1P|192.168.50.2|192.168.50.1
HQ-Laptop-1|192.168.50.2|192.168.50.1

2. Desde la PC 1-1, abra el símbolo del sistema (command prompt) y escriba el comando arp -a.
* ¿Qué información aparece en pantalla? No se encontraron entradas ARP.
3. Utilice el comando ping para hacer ping a 1-2, 1-3, 1-4, FL-1P y HQ-Laptop-1.
4. Introduzca el comando show arp -a.
* ¿Qué información aparece en pantalla?
```shell
  Internet Address      Physical Address      Type   192.168.10.1          000a.41ea.6b47        dynamic   192.168.10.3          0002.4a8a.d20e        dynamic ARP proporciona una tabla que asigna direcciones MAC conocidas a sus direcciones IP asociadas.
```
* ¿Por qué las entradas en la tabla ARP no contienen información sobre los dispositivos en las redes 192.168.20.0 y 192.168.50.0 aunque el ping es exitoso? 192.168.10.0/24, 192.168.20.0/24 y 192.168.50.0/24 están en diferentes VLAN. El ping de la red 192.168.10.0 a otras redes VLAN debe pasar primero por el gateway predeterminado. Por lo tanto, la tabla ARP solo contiene la información sobre los dispositivos dentro de la misma red o la misma VLAN.
5. Para encontrar la ruta que toma un paquete para llegar al servidor DNS, ingrese el comando tracert 10.2.0.125.
* ¿Qué información aparece en pantalla?
```shell
Tracing route to 10.2.0.125 over a maximum of 30 hops:   1   0 ms      2 ms      0 ms      192.168.10.1   2   12 ms     0 ms      0 ms      10.0.0.49   3   1 ms      0 ms      0 ms      10.2.0.125
```
* ¿Cuántos routers o saltos hay entre la PC 1-1 y el servidor DNS? 2

## Parte 3: Diagnosticar problemas de conectividad
En esta parte, utilizará una variedad de comandos y técnicas de diagnóstico. Utilizará el comando nslookup para consultar un servidor DNS y solucionar problemas de una base de datos DNS. Luego diagnosticará por qué falla un ping pero el acceso web es exitoso. Por último, utilizará el comando netstat para descubrir qué puertos se están escuchando en el dispositivo de destino.

### Paso 1: Pruebar una URL para investigar un problema de conectividad.
1. En PC 1-1, cierre el Command Prompt (Símbolo del sistema) y haga click en Web Browser (Navegador Web).
2. Ingrese la URL test.ptsecurity.com.
¿Aparece la página web? Si no, ¿cuál es el mensaje? No, no lo hace. El mensaje es "Host Name Unresolved".
3. Introduzca la dirección IP 192.168.75.2.
* ¿Aparece la página web? Sí
* ¿Por qué la página web se muestra usando la dirección IP pero no el nombre de dominio? La PC no puede resolver el nombre de dominio a la dirección IP.

### Paso 2: Utilizar el comando nslookup para verificar el servicio DNS.
1. Cierre el Web Browser, y después haga click en Command Prompt.
2. Ingrese el comando ping test.ptsecurity.com.
* ¿Cuál es el mensaje que se muestra? Ping request could not find host test.ptsecurity.com. Please check the name and try again.
* ¿Qué significa este mensaje? La entrada DNS no está en la base de datos del servidor DNS.
3. Ingrese el comando nslookup test.ptsecurity.com.
* ¿Cuál es el mensaje que se muestra?
```shell
Server: [10.2.0.125] Address:  10.2.0.125 *** UnKnown can't find test.ptsecurity.com: Non-existent domain.
```
* ¿Cual es el servidor servidor DNS predeterminado? 10.2.0.125
6. El comando nslookup admite el uso de un servidor DNS alternativo. Ingrese nslookup /? para conocer las opciones disponibles para el comando.
5. Ingrese el comando nslookup test.ptsecurity.com 192.168.99.3 y presione Intro.
__Nota__: Packet Tracer puede tardar varios segundos en converger.
* ¿Cuál es el mensaje que se muestra? 
```shell
C:\> nslookup test.ptsecurity.com 192.168.99.3 Server: [192.168.99.3] Address:  192.168.99.3 Non-authoritative answer: Name:   test.ptsecurity.com Address:   192.168.75.2
```
* En el paso 2c, ¿por qué no se puede resolver el nombre de dominio? Cuando se ingresa un nombre de dominio en el cuadro URL, la PC intenta resolverlo a través del servidor DNS predeterminado. En este caso, el servidor DNS predeterminado no contiene la información en su base de datos.

### Paso 3: Utilizar la salida del comando ping para diagnosticar problemas de conectividad.
1. Ingrese el comando ping mail.cybercloud.com.
¿Cuál es el mensaje que se muestra? 
```shell
C:\> ping mail.cybercloud.com Pinging 172.19.0.4 with 32 bytes of data: Request timed out. Request timed out. Request timed out. Request timed out. Ping statistics for 172.19.0.4: Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),
```
* ¿Qué información indica el mensaje? La resolución del nombre DNS se realizó correctamente. Sin embargo, el ping falló. Los posibles motivos son que el host está inactivo o que la respuesta de ICMP echo/echo está deshabilitada en el host.
2. Ingrese el comando ping www.ptsecurity.com.
* ¿Cuál es el mensaje que se muestra? Pinging 10.0.0.3 with 32 bytes of data: Request timed out. Expiró la solicitud. Reply from 10.0.0.3: Destination host unreachable. Reply from 10.0.0.3: Destination host unreachable. Ping statistics for 10.0.0.3: Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),
* ¿Qué información indica el mensaje? Hay un firewall en la ruta que bloquea el ping al destino.
3. Cierre el símbolo del sistema, abra el navegador web y vaya a www.ptsecurity.com.
* ¿Aparece la página web? Sí
* ¿Qué conclusiones se pueden sacar? El host web se está ejecutando; sin embargo, el ping al servidor web está bloqueado.

### Paso 4: Utilizar el comando netstat para buscar puertos activos y de escucha.
1. Cierre el navegador web y vuelva a abrir el símbolo del sistema.
2. En HQ, haga clic en Armario de cableado.
3. Desde el rack derecho haga click en FTP server > Desktop tab > Command Prompt.
4. Organice las ventanas de símbolo del sistema de la PC 1-1 y del servidor FTP en lado a lado.
5. Desde la ventana PC 1-1, introduzca el comando netstat.
* ¿Cuál es el mensaje que se muestra? ¿Muestra algún dato? 
```shell
C:\>netstat Active Connections   Proto  Local Address          Foreign Address        State C:\> No data is shown.
```
6. Desde el servidor FTP, introduzca el comando netstat.
* ¿Cuál es el mensaje que se muestra? ¿Muestra algún dato? 
```shell
C:\>netstat Active Connections   Proto  Local Address          Foreign Address              State   TCP    0.0.0.0:25              0.0.0.0:0                  CLOSED   TCP    0.0.0.0:110             0.0.0.0:0                  CLOSED   TCP    0.0.0.0:8443            0.0.0.0:0                  CLOSED C:\> No muestra conexiones activas hacia otros dispositivos ni está escuchando puertos.
```
7. En el servidor FTP, introduzca el comando ipconfig para determinar su dirección IP.
8. Desde la PC 1-1, inicie una sesión FTP con el servidor FTP.
9. En el servidor FTP, introduzca el comando netstat.
* ¿Cuál es el mensaje que se muestra? ¿Hay alguna información nueva? Sí, una nueva entrada muestra una entrada TCP 192.168.75.2:21 192.168.10.3:1025 ESTABLISHED.
* ¿Qué puerto es el puerto de escucha y cuál es el estado de la conexión? El puerto de escucha es TCP 21 y se establece la conexión TCP.
10. De la PC 1-1, introduzca bob como nombre de usuario.
11. Desde el servidor FTP, introduzca el comando netstat.
* ¿Cambia la información que se muestra? No.
12. De la PC 1-1, introduzca cisco123 como contraseña.
13. Desde la PC 1-1, introduzca el comando dir.
14. Desde el servidor FTP, introduzca el comando netstat.
* ¿Cambia la información que se muestra? Sí. Una nueva entrada muestra TCP 192.168.75.2:1028 192.168.10.3:1028 CLOSED.
* ¿Qué indica esta nueva entrada? Se abre una nueva conexión TCP para transferir los nombres de archivo en el directorio FTP y se cierra la conexión una vez completada la operación.
15. Desde la PC 1-1, ingrese el comando put Sample2.txt y presione Intro. Esto cargará el archivo Sanple2.txt en el servidor FTP.
16. Desde el servidor FTP, introduzca el comando netstat.
* ¿Cambia la información que se muestra? Sí. Aparece una nueva entrada:  TCP 192.168.75.2:1030 192.168.10.3:1029 CLOSING.
17. Espere unos segundos y luego ingrese el comando netstat nuevamente.
* ¿Cambia la información que se muestra? Sí. La línea de “CLOSING” desapareció.
18. Desde la PC 1-1, ingrese el comando quit.
19. Desde el servidor FTP, introduzca el comando netstat.
* ¿Cambia la información que se muestra? Sí. Ahora la TCP conexión entre 192.168.75.2:21 and 192.168.10.2:1027 está CLOSED.
20. Desde la PC1-1, cierre el Símbolo de Sistema, y después abra el Navegador Web.
21. Vaya a 192.168.75.2.
22. Desde el servidor FTP, introduzca el comando netstat.
* ¿Cambia la información que se muestra? Sí. Una nueva entrada muestra TCP 192.168.75.2:80 192.168.10.2:1030 CLOSED.
* ¿Qué indica esta nueva entrada? El host realiza una solicitud de página web 192.168.10.2. La página web se transmite (se muestra en el navegador web de la PC 1-1) y la conexión TCP se cierra.