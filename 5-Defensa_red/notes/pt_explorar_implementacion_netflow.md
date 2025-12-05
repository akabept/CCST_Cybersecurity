<title coding="utf-8">Explorar una implementación de NetFlow</title>

# Packet Tracer: Explorar una implementación de NetFlow
# Objetivos
* __Parte 1__: Observar los registros de flujo de NetFlow - Una dirección
* __Parte 2__: Observar registros de NetFlow correspondientes a una sesión que ingresa y sale del colector

# Trasfondo/Situación
En esta actividad utilizarán Packet Tracer para crear tráfico de red y observarán los registros de flujos de NetFlow correspondientes en un colector de NetFlow. Packet Tracer ofrece una simulación básica de la funcionalidad de NetFlow. No sustituye a aprender NetFlow en un equipo físico. Puede haber algunas diferencias entre los registros de flujos de NetFlow generados por Packet Tracer y los registros creados por un equipo de red con todas las funciones.

# Instrucciones
## Parte 1: Observe los registros de flujo de NetFlow - Una dirección
### Paso 1: Abra el colector NetFlow.
1. En el colector de NetFlow, haga clic en la pestaña de Desktop. Haga clic en el icono de colector de NetFlow.
2. Haga clic en el botón Encendido para activar el colector según sea necesario. Posicionen y cambien el tamaño de la ventana para poder verla desde la ventana de la topología de Packet Tracer.

### Paso 2: Realizar ping al gateway por defecto desde PC-1.
1. Haga clic en PC-1.
2. Abra la pestaña de Desktop y haga clic en el icono de command prompt.
3. Introducir el comando ping para probar la conectividad a la gateway por defecto en `10.0.0.1`.
```shell
C:\> ping 10.0.0.1
```
4. Después de una breve demora, la pantalla del colector de NetFlow mostrará un gráfico circular.
Nota: El primer conjunto de pings podría no ser enviado al colector de NetFlow porque el proceso ARP primero debe resolver direcciones IP y MAC. Si no aparece un gráfico circular después de 30 segundos, repitan el ping al gateway predeterminado.
5. Haga clic ya sea en el gráfico circular o en la entrada de las referencias para mostrar el registro detallado del flujo.
6. El registro de flujo tendrá entradas similares a las de la siguiente tabla. Sus marcas de hora serán diferentes.

**Entrada**|**Valor**|**Explicación**
:-|:-|:-
Traffic contribution| 100% (1/1)|Esta es la proporción de todo el tráfico representado por este flujo
IPV4 SOURCE ADDRESS| 10.0.0.10|Esta es la dirección IP de origen de los paquetes del flujo
IPV4 DESTINATION ADDRESS| 10.0.0.1|Esta es la dirección IP de destino de los paquetes del flujo
TRNS SOURCE PORT| 0|Este es el puerto de origen de la capa de transporte. El valor es 0 porque se trata de un flujo ICMP
TRNS DESTINATION PORT| 0|Este es el puerto de destino de la capa de transporte. El valor es 0 porque se trata de un flujo ICMP
IP PROTOCOL| 1|Esto identifica al servicio de la Capa 4;suele ser 1 para ICMP, 6 para TCP y 17 para UDP
timestamp first|00:47:49.593|Esta es la marca de hora correspondiente al comienzo del flujo
timestamp last|00:47:62.598|Esta es la marca de hora correspondiente al último paquete del flujo
tcp flags|0x00|Este es el valor del marcador de TCP. En este caso no participa ninguna sesión de TCP porue el protocolo es ICMP
counter bytes|512|Esta es la cantidad de bytes en el flujo
counter packets|4|Esta es la cantidad de paquetes en el flujo
interface input|Gig0/0|Esta es la interfaz del exportador de flujos que recogió el flujo en el sentido de entrada (ingreso a la interfaz del dispositivo de monitoreo)
interface output|Null|Esta es la interfaz del exportador de flujnos que recogió el flujo en el sentido de salida (regreso de la interfaz del dispositivo de monitoreo). El valor es "Null" porque se trataba de un ping a la interfaz de entrada

En este caso, el flujo representa al ping de ICMP desde el host 10.0.0.10 hacia 10.0.0.1. Había cuatro paquetes de ping en el flujo Los paquetes ingresan a la interfaz G0/0 del exportador.
	__Nota__: En esta actividad, el router perimetral se ha configurado como exportador de flujos de NetFlow. La interfaz LAN está configurada para monitorear los flujos que ingresan a ella desde la red LAN. La interfaz serial se ha configurado para recolectar flujos que ingresan a ella desde Internet. Esto se ha hecho para simplificar esta actividad.

Para ver el tráfico que coincide con una sesión bidireccional completa, el exportador de NetFlow tendría que configurarse para recoger flujos que ingresan y salen de la red.

### Paso 3: Crear tráfico adicional.
1. Haga clic en PC-2 > Desktop.
2. Abra un Command prompt y haga ping al gateway por defecto 10.0.0.1.
	* ¿Qué esperan ver en los registros de flujo del colector de NetFlow? ¿Cambiarán las estadísticas correspondientes al registro de flujo ya existente, o aparecerá un flujo nuevo en el gráfico circular?
3. Regrese a la PC-1 y repita el ping al gateway.
	* ¿Cómo se representará este tráfico? ¿Como un segmento nuevo en el gráfico circular, o modificará los valores del registro de flujo ya existente?
4. Emitir un ping desde PC-3 y PC-4 a la dirección de gateway por defecto.
	* ¿Qué debería suceder en la pantalla del colector de flujos?

## Parte 2: Observar registros de NetFlow correspondientes a una sesión que ingresa y sale del colector
El exportador de NetFlow se ha configurado para recoger los flujos que salen de la red LAN e ingresan al router desde Internet.

### Paso 1: Acceda al servidor web por dirección IP.
Antes de continuar, apaguen y enciendan el Colector de NetFlow para borrar los flujos.
1. Haga clic en la pestaña de NetFlow Collector > Physical
2. Haga clic en el botón de encendido rojo para apagar el servidor. Luego, vuelvan a hacerle clic para encenderlo nuevamente. (Nota: Es posible que se deba desplazarse afuera o alejar el enfoque)
3. En el colector de NetFlow, haga clic en la pestaña de Desktop.
4. Haga clic en el icono de colector de NetFlow. Hagan clic en el botón de opción “On” (“Activado”) para activar el colector. Cierren la ventana del Colector de NetFlow.
5. Antes de acceder a un servidor web desde PC-1, prediga cuantos flujos habrá en el gráfico circular. Explique.

Basándose en los que saben sobre protocolos de red y NetFlow, predigan los valores correspondientes a las solicitudes de páginas web que salen de la red LAN.

**Campo de registro**|**Valor**|**Directrices**
:-:|:-:|:-:
Dirección IP origen| su respuesta |No corresponde
Dirección IP destino| su respuesta |No corresponde
Puerto de origen| 1025-5000 (MS Windows de manera predeterminada, qu es lo que utilizar PT) |Se trata de un valor aproximado que se crea dinámicamente
Puerto de destino| su respuesta |No corresponde
Interfaz de entrada| su respuesta |No corresponde
Interfaz de salida| su respuesta |No corresponde

Predigan los valores correspondientes a la respuesta de la página web que ingresa al router del exportador de NetFlow desde Internet.

**Campo de registro**|**Valor**|**Directrices**
:-:|:-:|:-:
Dirección IP origen|su respuesta |No disponible
Dirección IP destino|su respuesta |No disponible
Puerto de origen|su respuesta |No disponible
Puerto de destino|1025-5000|Este es cualquier valor asignado aleatoriamente desde el rango de puertos efímeros
Interfaz de entrada|su respuesta |No disponible
Interfaz de salida|su respuesta |No disponible

6. Haga clic en PC-1 > Desktop. Si es necesario, cierren la ventana del Símbolo del sistema. Hagan clic en el icono del navegador web.
7. En el navegador web de la PC-1, ingrese 192.0.2.100 y haga clic en Go. Aparecerá la página web del Sitio web de ejemplo.
8. Después de una breve demora, un nuevo gráfico circular aparecera en el colector de NetFlow. Verán al menos dos segmentos circulares correspondientes a la solicitud y a la respuesta HTTP. Podrían ver un tercer segmento si se excedió el tiempo de espera del caché de ARP correspondiente a PC-1.
9. Haga clic en cada segmento circular de HTTP para mostrar el registro y verificar sus predicciones.
10. Haga clic en el enlace a la página de Copyrights.
	* ¿Qué ocurrió? Explique. (Pista: compare el número de puerto en el host correspondiente a los flujos)
	* Compare los flujos. Sin contar las diferencias obvias en la marca de hora, las direcciones IP de origen y destino, los puertos y las interfaces, ¿qué más difiere entre los flujos de la solicitud y de la respuesta?

### Paso 2: Acceda a un servidor web madiante la URL.
1. Apague y encienda el colector de NetFlow para borrar los flujos.
2. Encienda el servicio de colector de NetFlow.
3. Antes de que acceda al servidor web por su URL.
	* ¿Qué cree que verá en la pantalla del colector de NetFlow?
4. En la PC-1, introduzca www.example.com en el campo de URL y presione Go
5. Después de que los flujos aparezcan en la pantalla, inspeccione cada registro de flujo.
	* ¿Qué valores ve para el campo del protocolo IP del registro del flujo? ¿Qué significan estos valores?
	
