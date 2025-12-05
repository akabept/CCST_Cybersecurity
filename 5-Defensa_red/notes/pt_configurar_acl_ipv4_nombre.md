<title coding="utf-8">Configurar ACL de IPv4 estándar con nombre</title>

# Configurar ACL de IPv4 estándar con nombre
* Tabla de direcciones
<table>
	<tr><th>Dispositivo<th>Interfaz<th>Dirección IP<th>Máscara de subred<th>Puerta de enlace predeterminada
	<tr><td rowspan="4">R1<td>F0/0<td><code>192.168.10.1</code><td><code>255.255.255.0</code><td rowspan="4">N/D
	<tr><td>F0/1<td><code>192.168.20.1</code><td><code>255.255.255.0</code>
	<tr><td>E0/0/0<td><code>192.168.100.1</code><td><code>255.255.255.0</code>
	<tr><td>E0/1/0<td><code>192.168.200.1</code><td><code>255.255.255.0</code>
	<tr><td>Servidor de archivos<td>NIC<td><code>192.168.200.100</code><td><code>255.255.255.0</code><td><code>192.168.200.1</code>
	<tr><td>Servidor web<td>NIC<td><code>192.168.100.100</code><td><code>255.255.255.0</code><td><code>192.168.100.1</code>
	<tr><td>PC0<td>NIC<td><code>192.168.20.3</code><td><code>255.255.255.0</code><td><code>192.168.20.1</code>
	<tr><td>PC1<td>NIC<td><code>192.168.20.4</code><td><code>255.255.255.0</code><td><code>192.168.20.1</code>
	<tr><td>PC2<td>NIC<td><code>192.168.10.3</code><td><code>255.255.255.0</code><td><code>192.168.10.1</code>
</table>

# Objetivos
* __Parte 1__: Configure y Aplique una ACL estándar con nombre
* __Parte 2__: Verifique la implementación de la ACL

# Trasfondo/Situación
El administrador de red ejecutivo le ha solicitado que cree una ACL con nombre estándar para impedir el acceso a un servidor de archivos. El servidor de archivos contiene la base de datos para las aplicaciones web. Sólo la estación de trabajo de `Web Manager PC1` y el servidor web necesitan tener acceso al servidor de archivos. Debe denegarse el resto del tráfico al servidor de archivos.

# Instrucciones
## Parte 1: Configure y aplique una ACLestándar con nombre
### Paso 1: Verifiquela conectividad antes de configurar y aplicar la ACL.
Las tres estaciones de trabajo deberían poder hacer _ping_ tanto al servidor web como a servidor de archivos.

### Paso 2: Configure una ACL estándar con nombre.
Abra la ventana de configuración.
1. Configure la siguiente ACL con nombre en R1.
	```shell
	R1(config)# ip access-list standard File_Server_Restrictions
	R1(config-std-nacl)# permit host 192.168.20.4
	R1(config-std-nacl)# permit host 192.168.100.100
	R1(config-std-nacl)# deny any
	```
__Nota__: A efectos de puntuación, el nombre de la ACL distingue entre mayúsculas y minúsculas y las instrucciones deben estar en el mismo orden que se muestra.

2. Utilice el comando `show access-lists` para verificar el contenido de la lista de acceso antes de aplicarla a una interfaz. Asegúrese de que no ha escrito mal ninguna dirección IP y de que las instrucciones están en el orden correcto.
	```shell
	R1# show access-lists
	Standard IP access list File_Server_Restrictions
	10 permit host 192.168.20.4
	20 permit host 192.168.100.100
	30 deny any
	```

### Paso 3: Aplique la ACL con nombre.
1. Aplique la salida de ACL en la interfaz `Fast Ethernet 0/1`.
__Nota__: En una red operativa real, aplicar una lista de acceso a una interfaz activa no es una buena práctica y debe evitarse si es posible.
	```shell
	R1(config-if)# ip access-group File_Server_Restrictions out
	```
2. Guarde la configuración.

## Parte 2: Verifique la implementación de ACL
### Paso 1: Verifique la configuración y la aplicación de la ACL en la interfaz.
Abrir la ventana de configuración. Utilice el comando `show access-lists` para verificar para verificar la configuracion de la ACL. Utilice el comando `show run` o `show ip interface fastethernet 0/1` para verificar que la ACL está aplicada correctamente a la interfaz.

### Paso 2: Verificar que la ACL esté funcionando correctamente.
Las tres estaciones de trabajo deberían poder hacer _ping_ al servidor web, pero solo `PC1` y el servidor web Server deberían hacer _ping_ al servidor de archivos. Repita el comando `show access-lists` para ver el número de paquetes que coinciden con cada sentencia.

Cerrar la ventana de configuración.
```shell
-----------------
Router R1
-----------------
enable
configure terminal
ip access-list standardFile_Server_Restrictions
 permit host 192.168.20.4
 permit host 192.168.100.100
 deny any
interface f0/1
 ip access-group File_Server_Restrictions out
```