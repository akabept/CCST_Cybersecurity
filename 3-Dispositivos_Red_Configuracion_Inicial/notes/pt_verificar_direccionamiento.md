# Identificación del direccionamiento IPv4 e IPv6
* Tabla de direccionamiento
<table>
	<tr><th>Dispositivo<th>Interfaz<th colspan="2">Dirección IP/Prefijo<th>Puerta de enlace pred.
	<tr><td rowspan="5">R1<td rowspan="2">G0/0<td>10.10.1.97<td>255.255.255.224<td>N/D
	<tr><td colspan="2">2001:db 8:1:1::1/64<td>N/D
	<tr><td rowspan="3">S0/0/1<td>10.10.1.6<td>255.255.255.252<td>N/D
	<tr><td colspan="2">2001:db 8:1:2::2/64<td>N/D
	<tr><td colspan="2">fe80::1	<td>N/D
	<tr><td rowspan="5">R2<td rowspan="2">S0/0/0<td>10.10.1.5<td>255.255.255.252<td>N/A
	<tr><td colspan="2">2001:db8:1:2::1/64<td>N/A
	<tr><td rowspan="3">S0/0/1<td>10.10.1.9<td>255.255.255.252<td>N/A
	<tr><td colspan="2">2001:db8:1:3::1/64<td>N/A
	<tr><td colspan="2">fe80::2	<td>N/A
	<tr><td rowspan="5">R3<td rowspan="2">G0/0<td>10.10.1.17<td>255.255.255.240<td>N/A
	<tr><td colspan="2">2001:db 8:1:4::1/64<td>N/A
	<tr><td rowspan="3">S0/0/1<td>10.10.1.10<td>255.255.255.252<td>N/A
	<tr><td colspan="2">2001:db8:1:3::2/64<td>N/A
	<tr><td colspan="2">fe80::3	<td>N/A
	<tr><td rowspan="2">PC1<td rowspan="2">NIC<td>Su respuesta<td>Su respuesta<td>Su respuesta
	<tr><td colspan="2">Su respuesta<td>Su respuesta
	<tr><td rowspan="2">PC2<td rowspan="2">NIC<td>Su respuesta<td>Su respuesta<td>Su respuesta
	<tr><td colspan="2">Su respuesta<td>Su respuesta
</table>

# Objetivos
* __Parte 1: Completar la documentación de la tabla de direccionamiento__
* __Parte 2: Probar la conectividad mediante el comando ping__
* __Parte 3: Descubrir la ruta mediante su rastreo__

# Aspectos básicos
La técnica dual-stack permite que IPv4 e IPv6 coexistan en la misma red. En esta actividad, investigará la implementación de una técnica dual-stack, incluidos la documentación de la configuración de IPv4 e IPv6 para terminales, la prueba de conectividad para IPv4 e IPv6 mediante el comando ping y el rastreo de la ruta de terminal a terminal para IPv4 e IPv6.

# Parte 1: Completar la documentación de la tabla de direccionamiento
## Paso 1: Usar el comando ipconfig para verificar el direccionamiento IPv4.
1. Haga Click en PC1 y abra el Command Prompt.
2. Introduzca el comando ipconfig /all para obtener la información de IPv4. Complete la tabla de direccionamiento con la dirección IPv4, la máscara de subred y el gateway predeterminado.
3. Haga Click en PC2 y abra el Command Prompt.
4. Introduzca el comando ipconfig /all para obtener la información de IPv4. Complete la tabla de direccionamiento con la dirección IPv4, la máscara de subred y el gateway predeterminado.

## Paso 2: Usar el comando ipv6config para verificar el direccionamiento IPv6.
1. En la PC1, introduzca el comando ipv6config /all para obtener la información de IPv6. Complete la tabla de direccionamiento con la dirección IPv6, el prefijo de subred y el gateway predeterminado.
2. En la PC2, introduzca el comando ipv6config /all para obtener la información de IPv6. Complete la tabla de direccionamiento con la dirección IPv6, el prefijo de subred y el gateway predeterminado.

# Parte 2: Probar la conectividad mediante el comando ping
## Paso 1: Usar el comando ping para verificar la conectividad IPv4.
1. En la PC1, haga ping a la dirección IPv4 de la PC2.
* ¿El resultado fue correcto?
2. En la PC2, haga ping a la dirección IPv4 de la PC1.
* ¿El resultado fue correcto?

## Paso 2: Usar el comando ping para verificar la conectividad IPv6.
1. En la PC1, haga ping a la dirección IPv6 de la PC2.
* ¿El resultado fue correcto?
2. En la PC2, haga ping a la dirección IPv6 de la PC1.
* ¿El resultado fue correcto?

# Parte 3: Descubrir la ruta mediante su rastreo
## Paso 1: Usar el comando tracert para descubrir la ruta IPv4.
1. En la PC1, rastree la ruta a la PC2.
```shell
PC> tracert 10.10.1.20
```
* ¿Qué direcciones se encontraron en el camino?
* ¿A qué interfaces se asocian las cuatro direcciones?
2. En la PC2, rastree la ruta a la PC1.
* ¿Qué direcciones se encontraron en el camino?
* ¿A qué interfaces se asocian las cuatro direcciones?

## Paso 2: Usar el comando tracert para detectar la ruta IPv6.
1. En la PC1, rastree la ruta a la dirección IPv6 de la PC2.
```shell
PC> tracert 2001:db8:1:4::a
```
* ¿Qué direcciones se encontraron en el camino?
* ¿A qué interfaces se asocian las cuatro direcciones?
2. En la PC2, rastree la ruta a la dirección IPv6 de la PC1.
* ¿Qué direcciones se encontraron en el camino?
* ¿A qué interfaces se asocian las cuatro direcciones?