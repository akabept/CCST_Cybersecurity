<title coding="utf-8">Configurar ACL de IPv6</title>

# Configurar ACL de IPv6
* Tabla de direcciones
<table>
	<tr><th>Dispositivo<th>Interfaz<th>Dirección/Prefijo IPv6<th>Puerta de enlace predeterminada
	<tr><td>PC1<td>NIC<td><code>2001:db8:1:10::10/64</code><td><code>fe80::1</code>
	<tr><td>PC2<td>NIC<td><code>2001:db8:1:11::11/64</code><td><code>fe80::1</code>
	<tr><td>Server3<td>NIC<td><code>2001:db8:1:30::30/64</code><td><code>fe80::30</code>
</table>

# Objetivos
* __Parte 1__: configurar, aplicar y verificar una ACL de IPv6
* __Parte 2__: configurar, aplicar y verificar una segunda ACL de IPv6 

# Instrucciones
## Parte 1: configurar, aplicar y verificar una ACL de IPv6
Los registros indican que una computadora en la red 2001:db8:1:11::0/64 está actualizando repetidamente una página web. Esto está causando un ataque de denegación de servicio (DoS) contra Server3. Hasta que se pueda identificar y limpiar el cliente, debe bloquear el acceso HTTP y HTTPS a esa red mediante una lista de acceso.

### Paso 1: configurar una ACL que bloquee el acceso HTTP y HTTPS.
Configure una ACL con el nombre BLOCK_HTTP en R1 con las siguientes instrucciones.
1. Bloquear el tráfico HTTP y HTTPS para que no llegue a Server3.
```shell
R1(config)# deny tcp any host 2001:db8:1:30::30 eq www
R1(config)# deny tcp any host 2001:db8:1:30::30 eq 443
```
2. Permitir el paso del resto del tráfico IPv6.

### Paso 2: Aplique la ACL a la interfaz correcta.
Aplique la ACL a la interfaz más cercana al origen del tráfico que se desea bloquear.

### Paso 3: Verifique la implementación de la ACL.
Verifique que la ACL esté funcionando según lo previsto realizando las siguientes pruebas:
* Abra el navegador web de PC1 en `http://2001:db8:1:30::30` o `https://2001:db8:1:30::30`. Debería aparecer el sitio web.
* Abra el navegador web de PC2 en `http://2001:db8:1:30::30` o `https://2001:db8:1:30::30`. El sitio web debería estar bloqueado.
* Haga ping desde PC2 a `2001:db8:1:30::30`. El ping debería realizarse correctamente.

## Parte 2: configurar, aplicar y verificar una segunda ACL de IPv6
Ahora, en los registros se indica que su servidor recibe pings de diversas direcciones IPv6 en un ataque por negación de servicio distribuido (DDoS). Debe filtrar las solicitudes de ping de ICMP que se envían a su servidor.

### Paso 1: crear una lista de acceso para bloquear ICMP.
Configure una ACL con el nombre BLOCK_ICMP en R3 con las siguientes instrucciones:
1. Bloquear todo el tráfico ICMP desde cualquier host hacia cualquier destino.
2. Permitir el paso del resto del tráfico IPv6.

### Paso 2: Aplique la ACL a la interfaz correcta.
En este caso, el tráfico ICMP puede provenir de cualquier origen. Para asegurarse de que el tráfico ICMP esté bloqueado, independientemente de su origen o de los cambios que se produzcan en la topología de la red, aplique la ACL lo más cerca posible del destino.

### Paso 3: Verifique que funcione la lista de acceso adecuada.
1. Haga ping desde PC2 a `2001:db8:1:30::30`. El ping debe fallar.
2. Haga ping de PC1 a `2001:db8:1:30::30`. El ping debe fallar.
3. Abra el navegador web de PC1 en `http://2001:db8:1:30::30` o `https://2001:db8:1:30::30`. Debería aparecer el sitio web.
	```shell
	-----------------
	Router R1
	-----------------
	enable
	config t
	ipv6 access-list BLOCK_HTTP
	 deny tcp any host 2001:db8:1:30::30 eq www
	 deny tcp any host 2001:db8:1:30::30 eq 443
	 permit ipv6 any any
	interface GigabitEthernet0/1
	 ipv6 traffic-filter BLOCK_HTTP in
	finalizar
	-----------------
	Router R3
	-----------------
	enable
	config t
	ipv6 access-list BLOCK_ICMP
	 deny icmp any any
	 permit ipv6 any any
	interface GigabitEthernet0/0
	 ipv6 traffic-filter BLOCK_ICMP out
	finalizar
	```