<title coding="utf-8">Configurar la autenticación basada en servidor con TACACS+ y RADIUS</title>

# Configurar la autenticación basada en servidor con TACACS+ y RADIUS
# Tabla de direcciones

<table>
	<tr><th>Dispositivo<th>Interfaz<th>Dirección IP<th>Máscara de subred<th>Puerta de enlace predeterminada<th>Puerto del switch
	<tr><td rowspan="2">R1<td>G0/1<td>192.168.1.1<td>255.255.255.0<td>N/A<td>S1 F0/1
	<tr><td>S0/0/0 (DCE)<td>10.1.1.2<td>255.255.255.252<td>No corresponde<td>No corresponde
	<tr><td rowspan="3">R2<td>G0/0<td>192.168.2.1<td>255.255.255.0<td>N/A<td>S2 F0/2
	<tr><td>S0/0/0<td>10.1.1.1<td>255.255.255.252<td>No corresponde<td>No corresponde
	<tr><td>S0/0/1 (DCE)<td>10.2.2.1<td>255.255.255.252<td>No corresponde<td>No corresponde
	<tr><td rowspan="2">R3<td>G0/1<td>192.168.3.1<td>255.255.255.0<td>N/A<td>S3 F0/5
	<tr><td>S0/0/1<td>10.2.2.2<td>255.255.255.252<td>No corresponde<td>No corresponde
	<tr><td>Servidor TACACS+<td>NIC<td>192.168.2.2<td>255.255.255.0<td>192.168.2.1<td>S2 F0/6
	<tr><td>Servidor RADIUS<td>NIC<td>192.168.3.2<td>255.255.255.0<td>192.168.3.1<td>S3 F0/1
	<tr><td>PC-A<td>NIC<td>192.168.1.3<td>255.255.255.0<td>192.168.1.1<td>S1 F0/2
	<tr><td>PC-B<td>NIC<td>192.168.2.3<td>255.255.255.0<td>192.168.2.1<td>S2 F0/1
	<tr><td>PC-C<td>NIC<td>192.168.3.3<td>255.255.255.0<td>192.168.3.1<td>S3 F0/18
</table>

# Objetivos
* Configurar la autenticación AAA basada en servidor mediante TACACS +.
* Verifique la autenticación AAA basada en el servidor desde el cliente PC-B.
* Configurar la autenticación AAA basada en servidor mediante RADIUS.
* Verifique la autenticación AAA basada en el servidor desde el cliente PC-C.

# Trasfondo/Situación
La topología de la red muestra los routers R1, R2 y R3. Actualmente, toda la seguridad administrativa se basa en el conocimiento de la contraseña enable secret. Su tarea es configurar y probar soluciones AAA locales y basadas en servidor.

Configurará el router R2 para admitir la autenticación basada en servidor utilizando el protocolo TACACS+. El servidor TACACS+ ha sido preconfigurado con lo siguiente:
* Cliente: R2 con la palabra clave tacacspa55
* Cuenta de usuario: Admin2 y contraseña admin2pa55

Finalmente, configurará el router R3 para admitir la autenticación basada en servidor utilizando el protocolo RADIUS. El servidor RADIUS ha sido preconfigurado con lo siguiente:
* Cliente: R3 con la palabra clave radiuspa55
* Cuenta de usuario: Admin3 y contraseña admin3pa55

Los routers también han sido preconfigurados con lo siguiente:
* Contraseña enable secret: ciscoenpa55
* Protocolo de enrutamiento OSPF con autenticación MD5 utilizando la contraseña: MD5pa55

__Nota__: Las líneas de consola y vty no han sido preconfiguradas.
__Nota__: Las imágenes de IOS más recientes utilizan un algoritmo de hash de cifrado más seguro; sin embargo, la versión de IOS soportada actualmente en Packet Tracer usa MD5. Utilice siempre la opción más segura disponible en su equipo físico.

# Parte 1: Configurar en R2 la autenticación AAA basada en servidor utilizando TACACS+
## Paso 1: probar la conectividad.
* Haga ping de PC-A a PC-B.
* Haga ping de PC-A a PC-C.
* Haga ping de PC-B a PC-C.

## Paso 2: configure una entrada de base de datos local de respaldo llamada Admin.
Para fines de respaldo, configure un nombre de usuario local `Admin2` y una contraseña `admin2pa55`.

## Paso 3: Verifique la configuración del servidor TACACS+.
Haga clic en el servidor TACACS+. En la solapa "Services", haga clic en "AAA". Observe que hay una entrada de configuración de red para `R2` y una entrada de configuración de usuario para `Admin2`.

## Paso 4: Configure los detalles del servidor TACACS+ en R2.
Configure la dirección IP y la clave secreta del servidor AAA TACACS en `R2`.
__Nota__: Los comandos tacacs-server host y tacacs-server key están en desuso. Actualmente, Packet Tracer no soporta el nuevo comando tacacs server.
```shell
R2(config)# tacacs-server host 192.168.2.2
R2(config)# tacacs-server key tacacspa55
```

## Paso 5: Configure la autenticación de inicio de sesión AAA para el acceso a la consola en R2.
Habilite AAA en `R2` y configure todos los inicios de sesión para autenticarse mediante el servidor AAA TACACS+. Si no está disponible, utilice la base de datos local.

## Paso 6: Configure la consola de línea para usar el método de autenticación AAA definido.
Configure la autenticación AAA para que el inicio de sesión de la consola utilice el método de autenticación AAA predeterminado.

## Paso 7: Verifique el método de autenticación AAA.
Verifique el inicio de sesión user `EXEC` utilizando el servidor AAA TACACS+.

# Parte 2: Configurar en R3 la autenticación AAA basada en servidor utilizando RADIUS
## Paso 1: configurar una entrada de base de datos local de respaldo llamada Admin.
Para fines de respaldo, configure un nombre de usuario local `Admin3` y una contraseña `admin3pa55`.

## Paso 2: Verifique la configuración del servidor RADIUS.
Haga clic en el servidor "RADIUS". En la solapa "Services", haga clic en "AAA". Observe que hay una entrada de configuración de red para `R3` y una entrada de configuración de usuario para `Admin3`.

## Paso 3: Configure los detalles del servidor RADIUS en R3.
Configure la dirección IP y la clave secreta del servidor AAA RADIUS en `R3`.
__Nota__: Los comandos radius-server host y radius-server key están en desuso. Actualmente, Packet Tracer no soporta el nuevo comando radius server.
```shell
R3(config)# radius-server host 192.168.3.2
R3(config)# radius-server key radiuspa55
```

## Paso 4: Configure la autenticación de inicio de sesión AAA para el acceso a la consola en R3.
Habilite AAA en `R3` y configure todos los inicios de sesión para autenticarse mediante el servidor AAA RADIUS. Si no está disponible, utilice la base de datos local.

## Paso 5: Configure la consola de línea para usar el método de autenticación AAA definido.
Configure la autenticación AAA para que el inicio de sesión de la consola utilice el método de autenticación AAA predeterminado.

## Paso 6: Verifique el método de autenticación AAA.
Verifique el inicio de sesión user EXEC utilizando el servidor AAA RADIUS.

## Paso 7: Revise los resultados.
El porcentaje de finalización debe ser del 100%. Haga clic en Comprobar resultados para ver los comentarios y la verificación de los componentes requeridos que se han completado.