<title coding="utf-8">Configurar ACL de IPv4 estándar numeradas</title>

# Configurar ACL IPv4 estándar numeradas
* Tabla de direcciones
<table>
	<tr><th>Dispositivo<th>Interfaz<th>Dirección IP<th>Máscara de subred<th>Puerta de enlace predeterminada
	<tr><td rowspan="4">R1<td>G0/0<td><code>192.168.10.1</code><td><code>255.255.255.0</code><td rowspan="4">N/D
	<tr><td>G0/1<td><code>192.168.11.1</code><td><code>255.255.255.0</code>
	<tr><td>S0/0/0<td><code>10.1.1.1</code><td><code>255.255.255.252</code>
	<tr><td>S0/0/1<td><code>10.3.3.1</code><td><code>255.255.255.252</code>
	<tr><td rowspan="3">R2<td>G0/0<td><code>192.168.20.1</code><td><code>255.255.255.0</code><td rowspan="4">N/A
	<tr><td>S0/0/0<td><code>10.1.1.2</code><td><code>255.255.255.252</code>
	<tr><td>S0/0/1<td><code>10.2.2.1</code><td><code>255.255.255.252</code>
	<tr><td rowspan="3">R3<td>G0/0<td><code>192.168.10.1</code><td><code>255.255.255.0</code><td rowspan="4">N/A
	<tr><td>S0/0/0<td><code>10.3.3.2</code><td><code>255.255.255.252</code>
	<tr><td>S0/0/1<td><code>10.2.2.2</code><td><code>255.255.255.252</code>
	<tr><td>PC1<td>NIC<td><code>192.168.10.10</code><td><code>255.255.255.0</code><td><code>192.168.10.1</code>
	<tr><td>PC2<td>NIC<td><code>192.168.11.10</code><td><code>255.255.255.0</code><td><code>192.168.11.1</code>
	<tr><td>PC3<td>NIC<td><code>192.168.30.10</code><td><code>255.255.255.0</code><td><code>192.168.30.1</code>
	<tr><td>Servidor web<td>NIC<td><code>192.168.20.254</code><td><code>255.255.255.0</code><td><code>192.168.20.1</code>
</table>

# Objetivos
* __Parte 1__: Planifique una implementación de ACL
* __Parte 2__: Configure, Aplique y Verifique una ACL estándar

# Trasfondo/Situación
Las listas de control de acceso (ACL) estándar son scripts de configuración del router que controlan si un router permite o deniega paquetes según la dirección de origen. Esta actividad se concentra en definir criterios de filtrado, configurar ACL estándar, aplicar ACL a interfaces de router y verificar y evaluar la implementación de la ACL. Los routers ya están configurados, incluidas las direcciones IP y el enrutamiento del Protocolo de Enrutamiento de la puerta de enlace Interior Mejorado (EIGRP).

# Instrucciones
## Parte 1: Planificar una implementación de ACL
### Paso 1: Investigar la configuraciónde red actual.
Antes de aplicar cualquier ACL a una red, es importante confirmar que tenga conectividad completa. Elija una computadora y haga ping a otros dispositivos en la red para verificar que la red tenga plena conectividad. Debería poder hacer ping correctamente a todos los dispositivos.

### Paso 2: Evalúe dos políticas de red y planifique implementaciones de ACL.
1. Las siguientes políticas de red están implementadas en `R2`:
* La red `192.168.11.0/24` no tiene acceso al servidor web en la red `192.168.20.0/24`.
* Todo otro acceso está permitido.

Para restringir el acceso desde la red `192.168.11.0/24` al servidor web en `192.168.20.254` sin interferir con otro tráfico, se debe crear un ACL en `R2`. La lista de acceso debe colocarse en la interfaz de salida al servidor web. Se debe crear una segunda regla en `R2` para permitir el resto del tráfico.

2. Las siguientes políticas de red están implementadas en `R3`:
* La red `192.168.10.0/24` no puede comunicarse con la red `192.168.30.0/24`.
* Todo otro acceso está permitido.

Para restringir el acceso desde la red `192.168.10.0/24` a la red `192 168.30/24` sin interferir con otro tráfico, se debe crear una lista de acceso en `R3`. La lista de acceso debe colocarse en la interfaz de salida a PC3. Se debe crear una segunda regla en `R3` para permitir el resto del tráfico.

## Parte 2: Configure, aplique y verifique una ACL Estándar
### Paso 1: Configure y aplique una ACL estándar numerada en R2.
1. Cree una ACL utilizando el número 1 en `R2` con una declaración que niegue el acceso a la red `192.168.20.0/24` desde la red `192.168.11.0/24`. Abra la ventana de configuración.
	```shell
	R2(config)# access-list 1 deny 192.168.11.0 0.0.0.255
	```
2. Por defecto, una lista de acceso niega todo el tráfico que no coincide con ninguna regla. Para permitir el resto del tráfico, configure la siguiente instrucción:
	```shell
	R2(config)# access-list 1 permit any
	```
3. Antes de aplicar una lista de acceso a una interfaz para filtrar el tráfico, es una buena prácticas revisar el contenido de la lista de acceso para verificar que filtrará el tráfico como se espera.
	```shell
	R2# show access-lists
	Standard IP access list 1
	10 deny 192.168.11.0 0.0.0.255
	20 permit any
	```
4. Para que la ACL realmente filtre el tráfico, debe aplicarse a alguna operación del router. Aplique la ACL colocándola para el tráfico saliente en la interfaz `GigabitEthernet 0/0`.
__Nota__: En una red operativa real no es una buena práctica aplicar una lista de acceso no probada a una interfaz activa.
	```shell
	R2(config)# interface GigabitEthernet0/0
	R2(config-if)# ip access-group 1 out
	```

### Paso 2: Configure y aplique una ACL estándar numerada en R3.
1. Cree una ACL utilizando el número 1 en R3 con una declaración que niegue el acceso a la red 192.168.30.0/24 desde la red de PC1 (192.168.11.0/24).
	```shell
	R3(config)# access-list 1 deny 192.168.10.0 0.0.0.255
	```
2. Por defecto, una ACL niega todo el tráfico que no coincide con ninguna regla. Para permitir el resto del tráfico, cree una segunda regla para la ACL 1.
	```shell
	R3(config)# access-list 1 permit any
	```
3. Verifique que la lista de acceso esté configurada correctamente.
	```shell
	R3# show access-lists
	Standard IP access list 1
	10 deny 192.168.10.0 0.0.0.255
	20 permit any
	```
4. Aplique la ACL colocándola para el tráfico saliente en la interfaz GigabitEthernet 0/0.
	```shell
	R3(config)# interface GigabitEthernet0/0
	R3(config-if)# ip access-group 1 out
	```
### Paso 3: Verifique la configuración y funcionalidad de la ACL.
1. Ingrese el comando show run o show ip interface gigabitethernet 0/0 para verificar las ubicaciones de la ACL.
2. Con las dos ACL en su lugar, el tráfico de red está restringido de acuerdo con las políticas detalladas en la Parte 1. Utilice las siguientes pruebas para verificar las implementaciones de ACL:
* Un _ping_ de `192.168.10.10` a `192.168.11.10` tiene éxito.
* Un _ping_ de `192.168.10.10` a `192.168.20.254` tiene éxito.
* Un _ping_ de `192.168.11.10` a `192.168.20.254` falla.
* Un _ping_ de `192.168.10.10` a `192.168.30.10` falla.
* Un _ping_ de `192.168.11.10` a `192.168.30.10` tiene éxito.
* Un _ping_ de `192.168.30.10` a `192.168.20.254` tiene éxito.
3. Ejecute de nuevo el comando show access-lists en los routers R2 y R3. Debería ver un resultado que indica el número de paquetes que han coincidido con cada línea de la lista de acceso. 
__Nota__: El número de coincidencias mostradas para sus routers puede ser diferente debido al número de pings que se envían y reciben.
	```shell
	R2# show access-lists
	Standard IP access list 1
	10 deny 192.168.11.0 0.0.0.255 (4 match(es))
	20 permit any (8 match(es))

	R3# show access-lists
	Standard IP access list 1
	10 deny 192.168.10.0 0.0.0.255 (4 match(es))
	20 permit any (8 match(es))

	-----------
	Router R2
	-----------
	enable
	configure terminal
	interface GigabitEthernet0/0
	ip access-group 1 out
	access-list 1 deny 192.168.11.0 0.0.0.255
	access-list 1 permit any
	end
	
	-----------
	Router R3
	-----------
	enable
	configure terminal
	interface GigabitEthernet0/0
	ip access-group 1 out
	access-list 1 deny 192.168.10.0 0.0.0.255
	access-list 1 permit any
	end
	```