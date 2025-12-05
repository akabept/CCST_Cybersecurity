<title coding="utf-8">Configurar ACL de IPv4 extendida escenario 2</title>

# Configurar ACL de IPv4 extendida escenario 2
* Tabla de direcciones
<table>
	<tr style="background-color: #dbe5f1;"><th>Dispositivo<th>Interfaz<th>Dirección IP<th>Máscara de subred<th>Puerta de enlace predeterminada
	<tr><td rowspan="2">RT1<td>G0/0<td><code>172.31.1.126</code><td><code>255.255.255.2224</code><td rowspan="2">N/D
	<tr><td>S0/0/0<td><code>209.165.1.2</code><td><code>255.255.255.252</code>
	<tr><td>PC1<td>NIC<td><code>172.31.1.101</code><td><code>255.255.255.224</code><td><code>172.31.1.126</code>
	<tr><td>PC2<td>NIC<td><code>172.31.1.102</code><td><code>255.255.255.224</code><td><code>172.31.1.126</code>
	<tr><td>PC3<td>NIC<td><code>172.31.1.103</code><td><code>255.255.255.224</code><td><code>172.31.1.126</code>
	<tr><td>Servidor1<td>NIC<td><code>64.101.255.254</code><td><td>
	<tr><td>Servidor2<td>NIC<td><code>64.103.255.254</code><td><td>
</table>
<table>
	<tr style="background-color: #f2dbdb;"><th>Dispositivo<th>Interfaz<th>Dirección IP<th>Máscara de subred<th>Puerta de enlace predeterminada
	<tr><td>RT1<td>G0/0<td><code>172.31.1.126</code><td><code>255.255.255.224</code><td>N/D
	<tr><td>RT1<td>S0/0/0<td><code>209.165.1.2</code><td><code>255.255.255.252</code><td>N/A
	<tr><td>PC1<td>NIC<td><code>172.31.1.101</code><td><code>255.255.255.224</code><td><code>172.31.1.126</code>
	<tr><td>PC2<td>NIC<td><code>172.31.1.102</code><td><code>255.255.255.224</code><td><code>172.31.1.126</code>
	<tr><td>PC3<td>NIC<td><code>172.31.1.103</code><td><code>255.255.255.224</code><td><code>172.31.1.126</code>
	<tr><td>Servidor1<td>NIC<td><code>64.101.255.254</code><td><code>255.254.0.0</code><td><code>64.100.1.1</code>
	<tr><td>Servidor2<td>NIC<td><code>64.103.255.254</code><td><code>255.254.0.0</code><td><code>64.102.1.1</code>
</table>

# Objetivos
* __Parte 1__: Configure una ACL extendida con nombre
* __Parte 2__: Aplique y verifique la ACL extendida

# Trasfondo/Situación
En este escenario, se permiten dispositivos específicos en la LAN a varios servicios en servidores ubicados en Internet.

# Instrucciones
## Parte 1: Configurar una ACL Extendida Nombrada (Named Extended ACL)
Configure una ACL con nombre para implementar la siguiente política:
* Bloquear los accesos HTTP y HTTPS desde PC 1 a los servidores Server1 y Server2. Los servidores están dentro de la nube, y solo conoce sus direcciones IP.
* Bloquear el acceso FTP desde PC2 a los servidores Server1 y Server2.
* Bloquear el acceso ICMP desde PC3 a los servidores Server1 y Server2.

__Nota__: Para fines de puntuación debe configurar las sentencias en el orden especificado en los siguientes pasos.

### Paso 1: Denegar el acceso de PC1 a los servicios HTTP y HTTPS en los servidores Server1 y Server2.
1. Crear una lista de acceso IP nombrada extendida en el router RT1 que denegará el acceso de PC1 a los servicios HTTP y HTTPS de los serrvidores Server1 y Server2. Se requieren cuatro declaraciones de control de acceso. Para esta actividad utilice ACL como nombre de la lista de acceso nombrada.
	* ¿Cuál es el comando para empezar la configuración de una lista de acceso extendida con el nombre ACL?
2. Comience la configuración de ACL con la sentencia que deniega el acceso desde PC1 a Server1, solo para HTTP (puerto 80). Recurra a la tabla de direccionamiento para obtener las direcciones IP de PC1 y Server1.
	```shell
	RT1(config-ext-nacl)# deny tcp host 172.31.1.101 host 64.101.255.254 eq 80
	```
3. A continuación ingrese la sentencia que deniega el acceso de PC1 a Server1, solo para HTTPS (puerto 443).
	```shell
	RT1(config-ext-nacl)# deny tcp host 172.31.1.101 host 64.101.255.254 eq 443
	```
4. Ingrese la sentencia que deniega el acceso de PC1 a Server2, solo para HTTP.  Recurra a la tabla de direccionamiento para obtener la dirección IP de Server2.
	```shell
	RT1(config-ext-nacl)# deny tcp host 172.31.1.101 host 64.103.255.254 eq 80
	```
5. Ingrese la sentencia que deniega el acceso de PC1 a Server2, solo para HTTPS.
	```shell
	RT1(config-ext-nacl)# deny tcp host 172.31.1.101 host 64.103.255.254 eq 443
	```

### Paso 2: Denegar el acceso de PC2 a los servicios FTP en Server1 y Server2.
Consulte la tabla de direccionamiento para la dirección IP de la PC2.
1. Ingrese la sentencia que deniega el acceso de PC2 a Server1, solo para FTP (solo el puerto 21).
	```shell
	RT1(config-ext-nacl)# deny tcp host 172.31.1.102 host 64.101.255.254 eq 21
	```
2. Ingrese la sentencia que deniega el acceso de PC2 a Server2, solo para FTP (solo para el puerto 21).
	```shell
	RT1(config-ext-nacl)# deny tcp host 172.31.1.102 host 64.103.255.254 eq 21
	```

### Paso 3: Impedir que PC3 ejecute el comando ping hacia los servidores Server1 y Server2.
Recurra a la tabla de direccionamiento para obtener la dirección IP de PC3.
1. Ingrese la sentencia que deniega el acceso ICMP de PC3 a Server1.
	```shell
	RT1(config-ext-nacl)# deny icmp host 172.31.1.103 host 64.101.255.254
	```
2. Ingrese la sentencia que deniega el acceso ICMP de PC3 a Server2.
	```shell
	RT1(config-ext-nacl)# deny icmp host 172.31.1.103 host 64.103.255.254
	```

### Paso 4: Permitir cualquier otro tráfico IP.
De manera predeterminada, las listas de acceso deniegan todo el tráfico que no coincide con alguna regla de la lista. Escriba el comando que permita todo el tráfico que no coincida con ninguna de las instrucciones de lista de acceso configuradas.

### Paso 5: Verificar la configuración de la lista de acceso antes de aplicarla a una interfase.
Antes de aplicar cualquier lista de acceso, la configuración debe verificarse para asegurarse de que no hay errores tipográficos y de que las instrucciones están en el orden correcto.  Para ver la configuración actual de la lista de acceso utilice el comando `show access-lists` o el comando `show running-config`.
```shell
RT1# show access-lists
Extended IP access list ACL
10 deny tcp host 172.31.1.101 host 64.101.255.254 eq www
20 deny tcp host 172.31.1.101 host 64.101.255.254 eq 443
30 deny tcp host 172.31.1.101 host 64.103.255.254 eq www
40 deny tcp host 172.31.1.101 host 64.103.255.254 eq 443
50 deny tcp host 172.31.1.102 host 64.101.255.254 eq ftp
60 deny tcp host 172.31.1.102 host 64.103.255.254 eq ftp
70 deny icmp host 172.31.1.103 host 64.101.255.254
80 deny icmp host 172.31.1.103 host 64.103.255.254
90 permit ip any any

RT1# show running-config | begin access-list
ip access-list extended ACL
deny tcp host 172.31.1.101 host 64.101.255.254 eq www
deny tcp host 172.31.1.101 host 64.101.255.254 eq 443
deny tcp host 172.31.1.101 host 64.103.255.254 eq www
deny tcp host 172.31.1.101 host 64.103.255.254 eq 443
deny tcp host 172.31.1.102 host 64.101.255.254 eq ftp
deny tcp host 172.31.1.102 host 64.103.255.254 eq ftp
deny icmp host 172.31.1.103 host 64.101.255.254
deny icmp host 172.31.1.103 host 64.103.255.254
permit ip any any
```

Cerrar la ventana de configuración.
__Nota__: La diferencia entre las salidas de los comandos `show access-lists` y `show running-config` es que el comando `show access-lists` incluye los números de secuencia asignados a las sentencias de configuración. Estos números de secuencia permiten la edición, eliminación e inserción de líneas individuales dentro de la configuración de lista de acceso. Los números de secuencia también definen el orden de procesamiento de las sentencias de control de acceso individuales, comenzando por el número de secuencia más bajo.

## Parte 2: Aplique y verifique la ACL extendida
El tráfico que se filtrará proviene de la red 172.31.1.96/27 y tiene como destino las redes remotas. La ubicación adecuada de la ACL depende de la relación del tráfico con respecto a RT1. En general, las listas de acceso extendido deben colocarse en la interfaz más cercana al origen del tráfico.

### Paso 1: Aplicar la ACL a la interfase correcta y en la dirección correcta.
__Nota__: En una red operativa (en producción) nunca debe aplicarse una ACL no testeada a una interfase activa. Esta no es una buena práctica y puede interrumpir el funcionamiento de la red.
* ¿En qué interfaz se debe aplicar la ACL nombrada y en qué dirección?

Ingrese los comandos de configuración para aplicar la ACL a la interfaz.

### Paso 2: prueba el acceso para cada PC.
1. Acceder a los sitios web de Server1 y Server2 utilizando el navegador de PC1. Utilice los protocolos HTTP y HTTPS. Utilice el comando `show access-lists` para ver qué declaración de la lista de acceso permitió o denegó el tráfico. La salida del comando show access-lists muestra la cantidad de paquetes que coinciden con cada declaración desde la última vez que se borraron los contadores o se reinició el router.
__Nota__: Para borrar los contadores en una lista de acceso utilice el comando clear access-list counters .
	```shell
	RT1#show ip access-lists
	Extended IP access list ACL
	10 deny tcp host 172.31.1.101 host 64.101.255.254 eq www (12 match(es))
	20 deny tcp host 172.31.1.101 host 64.101.255.254 eq 443 (12 match(es))
	30 deny tcp host 172.31.1.101 host 64.103.255.254 eq www
	40 deny tcp host 172.31.1.101 host 64.103.255.254 eq 443
	50 deny tcp host 172.31.1.102 host 64.101.255.254 eq ftp
	60 deny tcp host 172.31.1.102 host 64.103.255.254 eq ftp
	70 deny icmp host 172.31.1.103 host 64.101.255.254
	80 deny icmp host 172.31.1.103 host 64.103.255.254
	90 permit ip any any
	```
2. Acceda al FTP de Server1 y de Server2 con PC1. El nombre de usuario y la contraseña es `cisco`.
3. Haga ping a Server1 y Server2 desde PC1.
4. Repita del Paso 2a al Paso 2c con PC2 y PC3 para verificar el correcto funcionamiento de la lista de acceso.
	```shell
	--------------------
	Router RT1
	--------------------
	enable
	configure terminal
	ip access-list extended ACL
	 deny tcp host 172.31.1.101 host 64.101.255.254 eq www
	 deny tcp host 172.31.1.101 host 64.101.255.254 eq 443
	 deny tcp host 172.31.1.101 host 64.103.255.254 eq www
	 deny tcp host 172.31.1.101 host 64.103.255.254 eq 443
	 deny tcp host 172.31.1.102 host 64.101.255.254 eq ftp
	 deny tcp host 172.31.1.102 host 64.103.255.254 eq ftp
	 deny icmp host 172.31.1.103 host 64.101.255.254
	 deny icmp host 172.31.1.103 host 64.103.255.254
	 permit ip any any
	interface GigabitEthernet0/0
	 ip access-group ACL in
	finalizar
	```

<br />
<br />
<br />
<br />
<br />
<br />
<br />



	