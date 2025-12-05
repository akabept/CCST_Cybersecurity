<title coding="utf-8">Uso de comandos de diagnósticorseguridad</title>

# Packet Tracer: Investigar la Recuperación ante un Desastre
# Objetivos
* __Parte 1__: Revisar la configuración de un switch.
* __Parte 2__: Realizar una copia de respaldo en un servidor TFTP.
* __Parte 3__: Reemplazar un switch que falló.
* __Parte 4__: Restaurar las operaciones de red.

# Trasfondo/Situación
En esta actividad de Packet Tracer (PT), hará una copia de respaldo de los archivos de configuración del switch, reemplazará un switch que falló por uno nuevo y luego restaurará las operaciones de red aplicando la configuración respaldada del switch que falló al nuevo switch. Afortunadamente, los archivos de configuración de respaldo se guardaron en un servidor de protocolo TFTP (Trivial File Transfer Protocol, protocolo trivial de transferencia de archivos). Debe restaurar los archivos del servidor TFTP para que el router vuelva a estar en línea con el menor tiempo de inactividad posible.

Nota: La actividad se abre en el Wiring Closet para HQ. Aunque puede salir del armario de cableado, todas las tareas de esta actividad se realizarán dentro del armario de cableado. El cambio al modo lógico está deshabilitado.

# Instrucciones
## Parte 1: Revisar la configuración de un switch
En esta parte, revisará y documentará la configuración actual del switch MDF-1 en el armario de cableado HQ. Esta información será necesaria para configurar manualmente un switch de reemplazo y verificar que el nuevo switch funcione como se espera.

### Paso 1: Observar el contenido de la NVRAM.
1. Haga clic en la pestaña MDF-1 > CLI y presione Enter.
2. Ingrese el comando enable y luego el comando dir nvram para observar el contenido de la NVRAM.
* ¿Cuál es el tamaño del archivo de configuración de inicio?

### Paso 2: Documente las VLAN y otra información de configuración importante.
1. Introduzca el comando show vlan
	* ¿Cuales VLANs se han configurado en MDF-1?
2. Introduzca el comando show run Revise la salida para documentar la siguiente información, que deberá configurar manualmente en un switch después de un desastre.
	* Registre las siguientes configuraciones en la siguiente tabla:
	
	|Configuración de MDF-1|Resultado del comando|
	|:-|:-|
	|Dirección IP de VLAN 99|Aquí su respuesta|
	|Dirección IP del gateway predeterminado|Aquí su respuesta|
	|Asignación de la VLAN de la interfaz F0/1|Aquí su respuesta|
	|LAN nativa y estado de troncal de G0/1|Aquí su respuesta|

## Parte 2: Realizar una copia de respaldo en un servidor TFTP
En esta parte, copiará los archivos de configuración para el switch MDF-1 en el servidor TFTP. Luego verificará que los archivos estén presentes en el servidor TFTP.

### Paso 1: Habilitar el servicio TFTP en el servidor FTP.
1. En el armario de cableado, en el rack derecho, haga clic en el servidor FTP server > Desktop tab > Command Prompt.
2. Ingrese el comando ipconfig.
	* ¿Cuál es la dirección IP del servidor FTP?
3. Haga clic en la pestaña Services y luego haga clic en TFTP.
4. Habilite el servicio TFTP.

### Paso 2: Cargue vlan.dat y los archivos de configuración de inicio en el servidor TFTP.
1. Haga clic en MDF-1 y luego en la prestaña CLI, si es necesario. Si cerró sesión, ingrese el comando enable nuevamente.
2. Ingrese el comando copy flash tftp y especifique vlan.dat como nombre de archivo de origen. Usted documentó la dirección IP en el paso anterior. Ingrese MDF-1_vlan.dat para el nombre del archivo de destino.
	* Anote el comando que se indica a continuación.
3. Ingrese el comando copy startup-config tftp para copiar la configuración asl servidor TFTP. Usted documentó la dirección IP en el paso anterior. Ingrese MDF-1_startup-config como el nombre del archivo destino.
	* Anote el comando que se indica a continuación.

### Paso 3: Verifique que los archivos estén en el servidor TFTP.
Haga clic en Servidor TFTP. En TFTP en SERVICIOS, verifique que los dos archivos estén enumerados en la sección File. Si es necesario, actualice la lista de archivos haciendo clic en otro servicio y luego en el servicio TFTP nuevamente.

## Parte 3: Reemplazar un switch fallido
Suponga que el switch MDF-1 ha fallado. Esto puede deberse a una sobrecarga de energía, un chip dañado o algún otro riesgo ambiental o falla de hardware. En esta parte, instalará un switch de reemplazo y moverá las conexiones de cable del switch fallido al nuevo switch.

### Paso 1: Agregue un nuevo switch a la red.
1. En la mesa en el armario de cableado, busque spare-switch_01.
2. Haga clic y arrástrelo al rack debajo de HQ-WLC-1.
3. Haga clic en la pestaña de spare-switch_01 > CLI y presione Enter .
4. Ingrese los siguientes comandos para ver las interfaces.
	```shell
	enable
	configure terminal
	interface range f0/1 - 23, g0/1 - 2
	shutdown
	exit
	```

### Paso 2: Mueva las conexiones de cable del switch MDF-1 al nuevo switch.
1. En la barra de herramientas superior, haga clic en Zoom in (Ampliar) varias veces hasta que pueda ver fácilmente las conexiones de los cables para MDF-1 y spare-switch_01.
Alternativamente, puede hacer clic derecho en cada switch y elegir Inspect Front (Inspeccionar el frente). Pero deberá hacerlo cada vez que mueva una conexión de MDF-1 a spare-switch_01.
2. Haga clic y arrastre una conexión de cable de MDF-1 al mismo número de puerto en spare-switch_01. Repita hasta que todos los cables pasen de MDF-1 a spare-switch_01.
3. Para verificar que los cables estén en los puertos correctos, haga clic con el botón derecho en spare-switch_01 y seleccione Inspect Front. Acérquese y luego flote el mouse de cada cable, espere la ventana emergente de información y asegúrese de que las conexiones de cable correspondan con esta tabla.
	
	|Puerto de la interfaz MDF-1|Dispositivo conectado|
	|:-|:-|
	|F0/1|FTP Server|
	|F0/2|MAIL Server|
	|F0/3|AAA-RADIUS Server|
	|F0/15|Net-Admin PC|
	|F0/19|FL-1 F0/19|
	|F0/20|FL-1 F0/20|
	|F0/21|FL-1 F0/21|
	|F0/22|FL-1 F0/22|
	|G0/1|HQ Edge Router|

4. Haga clic derecho en el Rack y elija Manage All Cables on Rack (Administrar todos los cables en el rack).
5. Desinstale MDF-1 del Rack. Haga clic y arrástrelo a la mesa.
6. En la barra de herramientas superior, haga clic en Zoom Reset (Restablecer zoom).

## Parte 4: Restaurar las operaciones de red
En esta parte, configurará manualmente el nuevo switch para que pueda acceder al servidor TFTP. Luego copiará los archivos de configuración del servidor TFTP al nuevo switch y verificará que el switch funcione como se espera.

### Paso 1: Configure spare-switch_01 para acceder a la red.
Para acceder al servidor TFTP a través de la red, al switch de repuesto se le necesitará configurar manualmente la información de la red . Ingrese la siguiente configuración en spare-switch_01 para conectarlo a la red y prepararlo para el acceso al servidor TFTP.
```shell
vlan 99
name Admin
exit
interface vlan 99
ip address 192.168.99.150 255.255.255.0
exit
ip default-gateway 192.168.99.1
interface fa0/1
switchport mode access
switchport access vlan 75
no shutdown
interface g0/1
switchport mode trunk
switchport trunk native vlan 99
no shutdown
end
```

### Paso 2: Pruebar la conectividad al servidor TFTP.
Ingrese ping 192.168.75.2 para verificar que spare-switch_01 pueda acceder al servidor TFTP.

### Paso 3: Descargar los archivos vlan.dat y startup-config del servidor TFTP.
1. Ingrese el comando copy tftp flash. Especifique la dirección IP del servidor TFTP. El nombre del archivo de origen es MDF-1_vlan.dat. El nombre del archivo de destino DEBE ser vlan.dat. Confirme que desea sobrescribir el archivo vlan.dat actual.
	* Anote el comando que se indica a continuación.
2. Ingrese el comando dir flash para verificar que el archivo vlan.dat esté en el directorio.
	* Anote el comando que se indica a continuación.
3. Ingrese el comando copy tftp startup-config. Especifique la dirección IP del servidor TFTP. El nombre del archivo de origen es MDF-1_startup-config. El nombre del archivo de destino DEBE ser startup-config.
	* Anote el comando que se indica a continuación.
4. Ingrese el comando dir nvram para verificar que el archivo de configuración de inicio (startup-config) esté ahora en la NVRAM.
	* Anote el comando que se indica a continuación.
	* ¿Cuál es el tamaño del archivo de configuración de inicio (startup-config)?
	* ¿Es del mismo tamaño que la configuración de inicio registrada en la Parte 1, Paso 1?

### Paso 4: Vuelva a cargar y verifique que el nuevo switch ahora tenga la configuración correcta.
1. Ingrese el comando reload. El archivo de configuración de inicio se copiará en la RAM y se convertirá en la configuración en ejecución.
	__Importante__: Responda no a la solicitud, System configuration has been modified. Save?, Presione Enter para confirmar el reinicio.
	* Anote el comando que se indica a continuación.
2. Después de que el switch se vuelva a cargar, revise la configuración.
	* El nombre de host ahora será MDF-1.
	* Ingrese el comando show vlan y verifique que las VLAN documentadas en la Parte 1, Paso 2, estén listadas.
	* Ingrese el comando show ip interface brief. Verifique que todos los puertos físicos conectados estén activos.