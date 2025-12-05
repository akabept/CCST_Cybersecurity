<title>ICMP para Probar y Corregir la Conectividad de Red</title>

# Utilizar ICMP para Probar y Corregir la Conectividad de Red
* Tabla de direccionamiento
<table>
	<tr><th>Dispositivo<th>Interfaz<th>Dirección IP<th>Máscara/Prefijo<th>Puerta de enlace pred.
	<tr><td rowspan="6">RTR1<td rowspan="2">G0/0/0<td>192.168.1.1<td>255.255.255.0<td>N/A
	<tr><td>2001:db8:4::1<td>/64<td>N/D
	<tr><td rowspan="2">S0/1/0<td>10.10.2.2<td>255.255.255.252<td>N/A
	<tr><td>2001:db8:2::2<td>/126<td>No corresponde
	<tr><td rowspan="2">/1/1<td>10.10.3.1<td>255.255.255.252<td>N/A
	<tr><td>2001:db8:3::1<td>/126<td>No corresponde
	<tr><td rowspan="4">RTR2<td>G0/0/0<td>10.10.1.1<td>255.255.255.0<td>N/A
	<tr><td>G0/0/1<td>2001:db8:1::1<td>/64<td>N/D
	<tr><td rowspan="2">S0/1/0<td>10.10.2.1<td>255.255.255.252<td>N/A
	<tr><td>2001:db8:2::1<td>/126<td>No corresponde
	<tr><td rowspan="4">RTR3<td>G0/0/0<td>10.10.5.1<td>255.255.255.0<td>N/A
	<tr><td>G0/0/1<td>2001:db8:5::1<td>/64<td>N/D
	<tr><td rowspan="2">S0/1/0<td>10.10.3.2<td>255.255.255.252<td>N/A
	<tr><td>2001:db8:3::2<td>/126<td>No corresponde
	<tr><td>PC1<td>NIC<td>10.10.1.10<td>255.255.255.0<td>10.10.1.1
	<tr><td>Portátil A<td>NIC<td>10.10.1.20<td>255.255.255.0<td>10.10.1.1
	<tr><td>PC2<td>NIC<td>2001:db8:1::10<td>/64<td>fe80::1
	<tr><td>PC3<td>NIC<td>2001:db8:1::20<td>/64<td>fe80::1
	<tr><td>PC4<td>NIC<td>10.10.5.10<td>255.255.255.0<td>10.10.5.1
	<tr><td>Servidor1<td>NIC<td>10.10.5.20<td>255.255.255.0<td>10.10.5.1
	<tr><td>Portátil B<td>NIC<td>2001:db8:5::10<td>/64<td>fe80::1
	<tr><td>Portátil C<td>NIC<td>2001:db8:5::20<td>/64<td>fe80::1
	<tr><td rowspan="2">Servidor Corporativo<td rowspan="2">NIC<td>203.0.113.100<td>255.255.255.0<td>203.0.113.1
	<tr><td>2001:db8:acad::100<td>/64<td>fe80::1
</table>

# Objetivos
En esta actividad de Packet Tracer, utilizará ICMP para probar la conectividad de la red y localizar problemas de red. También corregirá problemas de configuración simples y restaurará la conectividad a la red.
* Use ICMP para localizar problemas de conectividad.
* Configure los dispositivos de red para corregir problemas de conectividad.

# Aspectos básicos
Los clientes se han quejado de que no pueden llegar a algunos recursos de red. Se le ha pedido que pruebe la conectividad en la red. Utilice ICMP para averiguar qué recursos son inaccesibles y las ubicaciones desde las que no se puede llegar a ellos. A continuación, utilice el seguimiento para localizar el punto en el que se interrumpe la conectividad de red. Finalmente, corrige los errores que encuentra para restaurar la conectividad a la red.

# Instrucciones
Todos los hosts deben tener conectividad con todos los demás hosts y con el servidor corporativo.
* Espere hasta que todas las luces de enlace estén verdes.
* Seleccione un host y utilice el ping ICMP para determinar qué hosts son accesibles desde ese host.
* Si se encuentra que un host no es accesible, utilice el seguimiento ICMP para localizar la ubicación general de los errores de red.
* Localice los errores específicos y corrija.