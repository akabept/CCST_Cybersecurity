<title coding="utf-8">Configurar ACL de IPv4 extendida: Escenario 1</title>

# Configurar ACL de IPv4 extendida: Escenario 1
* Tabla de direcciones
<table>
	<tr><th>Dispositivo<th>Interfaz<th>Dirección IP<th>Máscara de subred<th>Puerta de enlace predeterminada
	<tr><td rowspan="3">R1<td>G0/0<td><code>172.22.34.65</code><td><code>255.255.255.224</code><td rowspan="3">N/D
	<tr><td>G0/1<td><code>172.22.34.97</code><td><code>255.255.255.240</code>
	<tr><td>G0/2<td><code>172.22.34.1</code><td><code>255.255.255.192</code>
	<tr><td>Servidor<td>NIC<td><code>172.22.34.62</code><td><code>255.255.255.192</code><td><code>172.22.34.1</code>
	<tr><td>PC1<td>NIC<td><code>172.22.34.66</code><td><code>255.255.255.224</code><td><code>172.22.34.65</code>
	<tr><td>PC2<td>NIC<td><code>172.22.34.98</code><td><code>255.255.255.240</code><td><code>172.22.34.97</code>
</table>

# Objetivos
* __Parte 1__: Configure, aplique y verifique una ACL extendida numerada
* __Parte 2__: Configure, Aplique y Verifique una ACL extendida con nombre

# Trasfondo/Situación
Dos empleados necesitan acceder a los servicios que proporciona el servidor. `PC1` solo necesita acceso FTP mientras que `PC2` solo necesita acceso a la web.

# Intrucciones
## Parte 1: Configurar, aplicar y verificar una ACL numerada extendida
### Paso 1: Configurar una ACL para permitir FTP e ICMP desde la LAN de PC1.
1. Desde el modo de configuración global en `R1` ingrese el siguiente comando para determinar el primer número válido para una lista de acceso extendida.
	```shell
	R1(config)# access-list ?
	  <1-99>     IP standard access list
	  <100-199>  IP extended access list
	```
2. Agregue `100` al comando, seguido de un signo de interrogación.
	```shell
	R1(config)# access-list 100 ?
	  deny    Especificar paquetes a rechazar
	  permit  Especificar paquetes a reenviar
	  remark  Comentario de la entrada de la lista de acceso
	```
3. Para permitir el tráfico FTP, ingrese `permit`, seguido por un signo de interrogación.
	```shell
	R1(config)# access-list 100 permit ?
	  ahp    Authentication Header Protocol
	  eigrp  Cisco's EIGRP routing protocol
	  esp    Encapsulation Security Payload
	  gre    Cisco's GRE tunneling
	  icmp   Internet Control Message Protocol
	  ip     Any Internet Protocol
	  ospf   OSPF routing protocol
	  tcp    Transmission Control Protocol
	  udp    User Datagram Protocol
	```
4. Una vez configurada y aplicada, esta ACL debería permitir FTP e ICMP. ICMP aparece en la lista anterior, pero FTP no. Esto se debe a que FTP es un protocolo de capa de aplicación que utiliza TCP en la capa de transporte. Ingrese TCP para refinar aún más la ayuda de ACL.
	```shell
	R1(config)# access-list 100 permit tcp ?
	8  A.B.C.D  Dirección origen
	  any      Cualquier host de origen
	  host     Un único host de origen
	```
5. La dirección de origen puede representar un solo dispositivo, como PC1, utilizando la palabra clave host y luego la dirección IP de PC1. El uso de la palabra clave any permite cualquier host en cualquier red. El filtrado también se puede realizar mediante una dirección de red. En este caso, es cualquier host que tiene una dirección que pertenece a la red 172.22.34.64/27. Ingrese esta dirección de red, seguida de un signo de interrogación.
	```shell
	R1(config)# access-list 100 permit tcp 172.22.34.64 ?
	  A.B.C.D  Source wildcard bits
	```
6. Calcule la máscara comodín determinando el opuesto binario de la máscara de subred `/27`.
	```shell
	1111111111111111111111.11100000 = 255.255.255.224
	00000000.0000000000000000.00011111 = 0.0.0.31
	```
7. Ingrese la máscara comodín seguida de un signo de interrogación.
	```shell
	R1(config)# access-list 100 permit tcp 172.22.34.64 0.0.0.31 ?
	  A.B.C.D  Dirección de destino
	  any      Cualquier host de destino
	  eq       Coincidir solo con los paquetes en un número de puerto determinado
	  gt       Coincidir solo con los paquetes con un número de puerto mayor
	  host     Un único host de destino
	  lt       Coincidir sólo con los paquetes con un número de puerto inferior
	  neq      Coincidir solo con los paquetes que no están en un número de puerto determinado
	  range    Coincidir solo con los paquetes en el rango de números de puerto
	```
8. Configura la dirección de destino. En este escenario, estamos filtrando el tráfico para un único destino, que es el servidor. Introduzca la palabra clave host seguida de la dirección IP del servidor.
	```shell
	R1(config)# access-list 100 permit tcp 172.22.34.64 0.0.0.31 host 172.22.34.62 ?
	  dscp         Coincidir con paquetes con un valor dscp dado
	  eq           Coincidir solo con los paquetes en un número de puerto determinado
	  established  established
	  gt           Coincidir solo con los paquetes con un número de puerto mayor
	  lt           Coincidir sólo con los paquetes con un número de puerto inferior
	  neq           Coincidir solo con los paquetes que no están en un número de puerto determinado
	  precedence   Coincidir con paquetes con un valor de precedencia determinado
	  range        Coincidir solo con los paquetes en el rango de números de puerto
	  <cr>
	```
9. Tenga en cuenta que una de las opciones es <cr> (carriage return). En otras palabras, puede pulsar Enter y la declaración permitiría todo el tráfico TCP. Sin embargo, sólo estamos permitiendo el tráfico FTP; por lo tanto, introduzca la palabra clave eq seguida de un signo de interrogación para mostrar las opciones disponibles. Luego, ingrese ftp y presione latecla Enter.
	```shell
	R1(config)# access-list 100 permit tcp 172.22.34.64 0.0.0.31 host 172.22.34.62 eq ?
	  <0-65535>  Número de puerto
	  ftp        File Transfer Protocol (21)
	  pop3       Post Office Protocol v3 (110)
	  smtp       Simple Mail Transport Protocol (25)
	  telnet     Telnet (23)
	  www        World Wide Web (HTTP, 80)
	R1(config)# access-list 100 permit tcp 172.22.34.64 0.0.0.31 host 172.22.34.62 eq ftp
	```
10. Cree una segunda declaración de la lista de acceso para permitir el tráfico ICMP (ping, etc.) desde PC1 a Server. Observe que el número de la lista de acceso es el mismo y que no es necesario detallar un tipo específico de tráfico ICMP.
	```shell
	R1(config)# access-list 100 permit icmp 172.22.34.64 0.0.0.31 host 172.22.34.62
	```
11. Todo el resto del tráfico es denegado por defecto.
12. Ejecute el comando show access-list y verifique que la lista de accceso 100 contenga las declaraciones correctas. Observe que la declaración deny any any no aparece al final de la lista de acceso. La ejecución predeterminada de una lista de acceso es que si un paquete no coincide con una sentencia de la lista de acceso, no se permite a través de la interfaz.
	```shell
	R1#show access-lists
	Extended IP access list 100
	    10 permit tcp 172.22.34.64 0.0.0.31 host 172.22.34.62 eq ftp
	    20 permit icmp 172.22.34.64 0.0.0.31 host 172.22.34.62
	```

### Paso 2: Aplique la ACL en la interfaz correcta para filtrar el tráfico.
Desde la perspectiva de R1, el tráfico al que se aplica la ACL 100 es entrante desde la red conectada a la interfaz Gigabit Ethernet 0/0. Ingrese al modo de configuración de interfaz y aplique la ACL.
__Nota__: En una red operativa real, no es una buena práctica aplicar una lista de acceso no probada a una interfaz activa.
```shell
R1(config)# interface gigabitEthernet 0/0
R1(config-if)# ip access-group 100 in
```
### Paso 3: Verifique la implementación de la ACL.
1. Haga ping desde PC1 a Server. Si los pings no se realizan correctamente, verifique las direcciones IP antes de continuar.
2. FTP desde PC1 a Server. Tanto el nombre de usuario como la contraseña son cisco.
	```shell
	PC> ftp 172.22.34.62
	```
3. Salga del servicio FTP.
	```shell
	ftp> quit
	```
4. Haga ping de PC1 a PC2. El host de destino no debería ser accesible, porque la ACL no permitía explícitamente el tráfico.

## Parte 2: Parte 2: Configurar, aplicar y verificar una ACL extendida nombrada
### Paso 1: Configurar una ACL para permitir el acceso HTTP e ICMP desde la LAN de PC2.
1. Las ACL nombradas comienzan con la palabra ip. Desde el modo de configuración global del R1, introduzca el siguiente comando seguido por un signo de interrogación.
	```shell
	R1(config)# ip access-list ?
	extended Lista de acceso extendida
	standard Lista de acceso estándar
	```
2. Puede configurar ACLs estándar y extendidas con nombre. Esta lista de acceso filtra tanto las direcciones IP de origen como de destino, por lo tanto, debe ser extendida. Ingrese HTTP_ONLY como mombre. (Para la puntuación Packet Tracer, el nombre distingue entre mayúsculas y minúsculas y las sentencias de lista de acceso deben ser el orden correcto.)
	```shell
	R1(config)# ip access-list extended HTTP_ONLY
	```
3. El indicador de comandos (prompt) cambia. Ahora está en el modo de configuración de ACL extendida con nombre. Todos los dispositivos en la LAN de la PC2 necesitan acceso TCP. Introduzca la dirección de red, seguida de un signo de interrogación.
	```shell
	R1(config-ext-nacl)# permit tcp 172.22.34.96 ?
	  A.B.C.D  Bits comodines de origen
	```
4. Una forma alternativa de calcular un comodín es restar la máscara de subred de 255.255.255.255.
	```shell
	  255.255.255.255
	- 255.255.255.240
	-----------------
	=   0.  0.  0. 15
	R1(config-ext-nacl)# permit tcp 172.22.34.96 0.0.0.15
	```
5. Termine la declaración especificando la dirección del servidor como lo hizo en la Parte 1, y filtrando el tráfico www.
	```shell
	R1(config-ext-nacl)# permit tcp 172.22.34.96 0.0.0.15 host 172.22.34.62 eq www
	```
6. Cree una segunda declaración de la lista de acceso para permitir el tráfico ICMP (ping, etc.) desde PC2 a Server. Nota: la petición de entrada se mantiene igual, y no es necesario detallar un tipo específico de tráfico ICMP.
	```shell
	R1(config-ext-nacl)# permit icmp 172.22.34.96 0.0.0.15 host 172.22.34.62
	```
7. Todo el resto del tráfico es denegado por defecto. Salga del modo de configuración de ACL con nombre extendido.
8. Ejecute el comando show access-list cy verifique que la lista de accesso HTTP_ONLYcontenga las instrucciones correctas.
	```shell
	R1# show access-lists
	Extended IP access list 100
	10 permit tcp 172.22.34.64 0.0.0.31 host 172.22.34.62 eq ftp
	20 permit icmp 172.22.34.64 0.0.0.31 host 172.22.34.62
	Extended IP access list HTTP_ONLY
	10 permit tcp 172.22.34.96 0.0.0.15 host 172.22.34.62 eq www
	20 permit icmp 172.22.34.96 0.0.0.15 host 172.22.34.62
	```

### Paso 2: Aplique la ACL en la interfaz correcta para filtrar el tráfico.