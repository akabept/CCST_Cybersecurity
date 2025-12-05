# Observar la Resolución de DNS
## Objetivos
### Parte 1: Observar la conversión de un URL en una dirección IP mediante DNS
### Parte 2: Observar la búsqueda DNS mediante el comando nslookup en un sitio web
### Parte 3: Observar la búsqueda DNS mediante el comando nslookup en servidores de correo

## Aspectos básicos / situación
Cuando se escribe una dirección del localizador uniforme de recursos (URL), como http://www.cisco.com, en un navegador web, se invoca el sistema de nombres de dominio (DNS). La primera parte del URL describe el protocolo que se utiliza. Los protocolos comunes son el protocolo de transferencia de hipertexto (HTTP), el protocolo de transferencia de hipertexto sobre la capa de sockets seguros (HTTPS) y el protocolo de transferencia de archivos (FTP).

El DNS utiliza la segunda parte de la dirección URL, que en este ejemplo es www.cisco.com. DNS traduce el nombre de dominio (www.cisco.com) a una dirección IP para permitir que el host de origen llegue al servidor de destino. En esta práctica de laboratorio, observará DNS en acción y utilizará el comando nslookup (búsqueda de servidor de nombres) para obtener información adicional de DNS.

## Recursos necesarios
1 PC (Windows con acceso a Internet y símbolo del sistema)

## Instrucciones
### Parte 1: Observe la conversión de un URL en una dirección IP mediante DNS
a. Abra una ventana de intérprete de comandos de Windows
b. En el símbolo del sistema, haga ping al URL de Internet Corporation for Assigned Names and Numbers (ICANN), www.icann.org. ICANN coordina las funciones de DNS, de las direcciones IP, de la administración del sistema de nombres de dominio superior y de la administración del sistema de servidores raíz. El equipo debe traducir www.icann.org a una dirección IP para saber adónde enviar los paquetes del protocolo de mensajes de control de Internet (ICMP).

La primera línea de la salida muestra www.icann.org convertido a una dirección IP por DNS. Debería poder ver el efecto del DNS, aun cuando haya un firewall instalado en la institución que impida enviar pings o aun cuando el servidor de destino haya impedido hacer ping al servidor web.

__Nota__: Si el nombre de dominio se resuelve en una dirección IPv6, use el comando ping -4 www.icann.org para traducirlo a una dirección IPv4, si lo desea.
```bash
C:\> ping www.icann.org

Pinging www.vip.icann.org [2620:0:2d0:200::7] with 32 bytes of data:
Reply from 2620:0:2d0:200::7: time=43ms
Reply from 2620:0:2d0:200::7: time=41ms
Reply from 2620:0:2d0:200::7: time=44ms
Reply from 2620:0:2d0:200::7: time=39ms

Ping statistics for 2620:0:2d0:200::7:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 39ms, Maximum = 44ms, Average = 41ms

C:\> ping -4 www.icann.org

Pinging www.vip.icann.org [192.0.32.7] with 32 bytes of data:
Reply from 192.0.32.7: bytes=32 time=41ms TTL=241
Reply from 192.0.32.7: bytes=32 time=42ms TTL=241
Reply from 192.0.32.7: bytes=32 time=42ms TTL=241
Reply from 192.0.32.7: bytes=32 time=43ms TTL=241

Ping statistics for 192.0.32.7:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 41ms, Maximum = 43ms, Average = 42ms
```
* Registre las direcciones IP de www.icann.org.

c. Escriba las direcciones IPv4 del paso b en un navegador web, en lugar de la URL. Escriba `https://192.0.32.7` en el navegador web. Si el equipo tiene una dirección IPv6, puede introducir la dirección IPv6 `https://[2620:0:2d0:200::7]` en el navegador web.
d. Observe que la página web de inicio de ICANN se muestra sin utilizar DNS.
* A la mayoría de los seres humanos nos resulta más fácil recordar palabras que números. Si le indica a alguien que acceda a www.icann.org, probablemente lo recordará, pero si le indica que acceda a 192.0.32.7, le resultará difícil recordar una dirección IP. Los equipos informáticos procesan números (sistema binario). El DNS es el proceso por el cual las palabras se traducen por números. Además, hay una segunda traducción que tiene lugar. Los seres humanos pensamos en números con base 10. En informática, se procesan números con base 2. La dirección IP 192.0.32.7 con base 10 es equivalente a 11000000.00000000.00100000.00000111 con base 2. ¿Qué sucede si corta estos números con base 2 y los pega en un navegador?

e. En el símbolo del sistema, haga ping a www.cisco.com.

__Nota__: Si el nombre de dominio se resuelve en una dirección IPv6, use el comando ping -4 www.cisco.com para traducirlo por una dirección IPv4, si lo desea
```bash
C:\> ping www.cisco.com

Pinging origin-www.cisco.com [2600:1408:7:1:9300::90] with 32 bytes of data:
Reply from 2600:1408:7:1:9300::90: time=70ms
Reply from 2600:1408:7:1:9300::90: time=74ms
Reply from 2600:1408:7:1:9300::90: time=72ms
Reply from 2600:1408:7:1:9300::90: time=71ms

Ping statistics for 2600:1408:7:1:9300::90:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 70ms, Maximum = 74ms, Average = 71ms

C:\> ping -4 www. cisco.com

Pinging e2867.dsca.akamaiedge.net [172.230.155.162] with 32 bytes of data:
Reply from 172.230.155.162: bytes=32 time=7ms TTL=54
Reply from 172.230.155.162: bytes=32 time=6ms TTL=54
Reply from 172.230.155.162: bytes=32 time=7ms TTL=54
Reply from 172.230.155.162: bytes=32 time=6ms TTL=54

Ping statistics for 172.230.155.162:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 6ms, Maximum = 7ms, Average = 6ms
```
* Cuando hace ping a www.cisco.com, ¿obtiene la misma dirección IP que la del ejemplo? Explique.
* Escriba la dirección IP que obtuvo cuando hizo ping a www.cisco.com en un navegador. ¿Aparece el sitio web? Explique.

### Parte 2: Observe la búsqueda DNS mediante el comando nslookup en un sitio web
1. En el símbolo del sistema, escriba el comando nslookup.
```bash
C:\> nslookup
```
* ¿Cuál es el servidor DNS predeterminado que se utiliza?
2. Observe que el símbolo del sistema cambió por el símbolo "mayor que" (>). Este es el símbolo de nslookup. Desde aquí, puede introducir comandos relacionados con el DNS.
En el indicador, escriba __?__ para ver una lista de todos los comandos disponibles que puede usar en modo nslookup.
3. En el indicador de nslookup, escriba www.cisco.com.
```bash
> www.cisco.com
Default Server: one.one.one.one
Address: 1.1.1.1

Non-authoritative answer:
Name: e2867.dsca.akamaiedge.net
Direcciones: 2600:1404:a:395: :b33
          2600:1404:a:38e: ::b33
          172.230.155.162
Alias: www.cisco.com
          www.cisco.com.akadns.net
          wwwds.cisco.com.edgekey.net
          wwwds.cisco.com.edgekey.net.globalredir.akadns.net
```
* ¿Cuál es la dirección IPv4 traducida?
__Nota__: Lo más probable es que la dirección IP de su ubicación sea diferente porque Cisco usa servidores duplicados en varias ubicaciones en todo el mundo.
* ¿Es la misma dirección IP que aparece con el comando ping?
* En las direcciones, además de la dirección IP `172.230.155.162`, hay los siguientes números: `2600:1404:a:395: :b33` y `2600:1404:a:38e: ::b33`. ¿De qué se trata?
c. En el indicador nslookup, escriba la dirección IP del servidor web de Cisco que acaba de encontrar. Si no conoce el URL, puede usar el comando nslookup para obtener el nombre de dominio de una dirección IP.
```bash
> 172.230.155.162
Default Server: one.one.one.one
Address: 1.1.1.1

Name: a172-230-155-162.deploy.static.akamaitechnologies.com
Address: 172.230.155.162
```
* Puede utilizar la herramienta nslookup para traducir nombres de dominio a direcciones IP. También puede utilizarla para traducir direcciones IP a nombres de dominio.
* Mediante la herramienta nslookup, registre las direcciones IP asociadas con www.google.com.

### Parte 3: Observar la búsqueda de DNS con el comando nslookup en n servidores de correo
1. En el indicador nslookup, escriba set type=mx para usar nslookup ara identificar servidores de correo.
```bash
> set type=mx
```

2. En el indicador nslookup, escriba cisco.com.
```bash
> cisco.com
Server: one.one.one.one
Address: 1.1.1.1

Non-authoritative answer:
cisco.com MX preference = 20, mail exchanger = rcdn-mx-01.cisco.com
cisco.com MX preference = 30, mail exchanger = aer-mx-01.cisco.com
cisco.com MX preference = 10, mail exchanger = alln-mx-01.cisco.com
```
Un principio fundamental del diseño de red es la redundancia (la configuración de más de un servidor de correo). De esta manera, si no es posible acceder a uno de los servidores de correo, el equipo que realiza la consulta intenta con el segundo servidor. Los administradores de correo electrónico determinan qué servidor de correo se contacta primero utilizando la preferencia MX. Primero se contacta al servidor de correo con el valor de __ __ más bajo.
* Según el resultado de la imagen de arriba, ¿qué servidor de correo se contactará primero cuando se envíe correo electrónico a cisco.com?
3. En el símbolo del sistema de nslookup, escriba exit para volver al símbolo del sistema normal del equipo.
4. En el símbolo del sistema, escriba ipconfig /all.
* Escriba las direcciones IP de todos los servidores DNS que utilice su escuela.
* ¿Cuál es el propósito fundamental del DNS?
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<a href="#observar-la-resolución-de-dns">⬆️</a>