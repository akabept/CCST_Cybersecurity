<title coding="utf-8">Instalación de una máquina virtual en una computadora personal</title>

# Instalación de una máquina virtual en una computadora personal
# Objetivos
* Parte 1: Preparar una computadora para la virtualización
* Parte 2: Importar una máquina virtual en el inventario de VirtualBox

# Trasfondo/Situación
El poder computacional y los recursos, han aumentado enormemente en los últimos 10 años. Uno de los beneficios de tener procesadores de varios núcleos y grandes cantidades de RAM es la capacidad para usar virtualización. Gracias a la virtualización, una o más computadoras virtuales pueden operar dentro de una sola computadora física. Las computadoras virtuales que se ejecutan dentro de computadoras físicas se denominan "máquinas virtuales”. Las máquinas virtuales se conocen como “guests (invitados)” y las computadoras físicas se conocen como “hosts (huéspedes)”. Cualquier persona con una computadora y sistema operativo modernos puede ejecutar máquinas virtuales.

Se ha creado un archivo de imagen de máquina virtual para que pueda instalarlo en su computadora. En esta práctica de laboratorio, descargará e importará este archivo de imagen usando una aplicación de virtualización de escritorio, como VirtualBox.

# Recursos necesarios
* Computadora con un mínimo de 4 GB de RAM adicionales y 50 GB de espacio libre en disco asignado para ejecutar máquinas virtuales
* Acceso a Internet de alta velocidad para descargar Oracle VirtualBox y el archivo de imagen de máquina virtual

__Nota__: El archivo de imagen es de aproximadamente 2,5 GB, y puede crecer hasta 5 GB después de que la máquina virtual esté en funcionamiento. Aunque puede eliminar el archivo de imagen después de que se importe la máquina virtual, el requisito de espacio libre en disco de 50 GB es para los usuarios que deciden guardar el archivo de imagen.

__Nota__: Para instalar y ejecutar máquinas virtuales de 64 bits en una computadora física host, la computadora necesita ser un sistema de 64 bits y contar con tecnología de virtualización de hardware habilitada en BIOS. Si no puede instalar la imagen de máquina virtual, es posible que deba reiniciar su computadora e ingresar al modo de configuración en BIOS para habilitar la tecnología de virtualización de hardware en la configuración avanzada del sistema.

# Instrucciones
## Parte 1: preparar un servidor para la virtualización
En la parte 1, descargará e instalará el software de virtualización de escritorio y también descargará un archivo de imagen que se puede utilizar para completar las prácticas de laboratorio durante el curso. Para esta práctica de laboratorio, la máquina virtual ejecuta Linux.

### Paso 1: descargue e instale VirtualBox
VMware Workstation Player y Oracle VirtualBox son dos programas de virtualización que puede descargar e instalar para admitir el archivo de imagen. En esta práctica de laboratorio, utilizará VirtualBox.
1. Navegue hasta https://www.VirtualBox.org/.
2. Elija y descargue el archivo de instalación adecuado según su sistema operativo.
3. Una vez que hayan descargado el archivo de instalación de VirtualBox, ejecuten el instalador y acepten la configuración de instalación predeterminada.

### Paso 2: descargue el archivo de imagen de la máquina virtual
El archivo de imagen se creó de acuerdo con el Formato Abierto de Virtualización (OVF). El OVF es un estándar abierto para empaquetar y distribuir servicios virtualizados. Un paquete OVF tiene varios archivos ubicados en un directorio. Este directorio luego se distribuye como un paquete OVA. Este paquete contiene todos los archivos OVF necesarios para la implementación de máquinas virtuales. La máquina virtual utilizada en esta práctica de laboratorio se exportó de acuerdo con el estándar OVF.

Haga clic aquí para descargar CSE-LABVM y los archivos OVA de la estación de trabajo de seguridad.

__Nota__: Este archivo es de 5 GB de tamaño y puede tardar más de una hora en descargarse, dependiendo de la velocidad de su conexión a Internet.

Parte 2: importar la máquina virtual en el inventario de VirtualBox
En la parte 2, importará la imagen de la máquina virtual a VirtualBox e iniciará la máquina virtual.

### Paso 1: importe el archivo de máquina virtual en VirtualBox
1. Abra VirtualBox. Haga clic en Archivo > Importar dispositivo... para importar la imagen de máquina virtual.
2. En la ventana Dispositivo para importar, especifique la ubicación del archivo .OVA. Haga clic en el botón Siguiente para continuar.
3. Aparece la ventana Apply Settings (Aplicar parámetros). En el campo Carpeta base del equipo, es posible que deba hacer clic en la flecha desplegable y cambiar el destino seleccionando Otro y buscando una carpeta (puede usar la carpeta Documentos del usuario). Configure la Política de direcciones MAC para generar nuevas direcciones MAC para todos los adaptadores de red. Deje el resto de las configuraciones como predeterminadas. Haga clic en Import (Importar).
4. Cuando el proceso de importación termine, podrá observar que la nueva máquina virtual ha sido añadida al inventario de VirtualBox en el panel izquierdo. La máquina virtual está lista para usarse.

### Paso 2: inicie la máquina virtual e inicie sesión
1. En el inventario que se muestra a la izquierda, seleccione la máquina virtual que desea utilizar. En este ejemplo, seleccionará la máquina virtual CSE-LABVM.
2. Haga clic en el botón Iniciar. Es la flecha verde ubicada en la parte superior de de VirtualBox. Aparecerá una ventana nueva y el proceso de arranque de la máquina virtual iniciará.
	__Nota__: Si la máquina virtual no puede iniciar, deshabilite el controlador USB entrando a la configuración de la máquina virtual y desactivando la configuración de controlador USB en la sección USB o vaya a la página web de descarga de VirtualBox y descargue e instale el paquete de extensión de VirtualBox, de Oracle VM.
3. Cuando se completa el proceso de arranque, la máquina virtual iniciará sesión automáticamente y cargará el escritorio. Si necesita acceso de superusuario en cualquier momento, utilice las siguientes credenciales para la máquina virtual CSE-LABVM:
	* Nombre de usuario: cisco
	* Password: password
 __Nota__: La ventana que ejecuta la máquina virtual es una computadora completamente diferente de su host. Funciones como copiar y pegar no funcionarán entre las dos sin cambiar la configuración predeterminada en VirtualBox. Observe los enfoques del teclado y el mouse. Cuando haga clic dentro de la ventana de la máquina virtual, el mouse y el teclado operarán el sistema operativo guest. Su sistema operativo host ya no detectará las teclas o los movimientos del mouse. Presione la tecla CTRL derecha para regresar el enfoque del teclado y del mouse al sistema operativo host.

### Paso 3: Familiarícese con CSE-LABVM.
La máquina virtual de CSE-LABVM que acaba de instalar es una de las VM que utilizará en el curso. Familiarícese con los iconos de la lista a continuación:
Los iconos lanzadores están a la izquierda (de arriba a abajo):
* Inicio de cisco - directorio de inicio del usuario, cisco
* Escaneo de DPI - comando de acceso directo para aumentar la resolución
* Navegador web Firefox
* jcryptool - herramienta de criptografía y criptoanálisis
* Teclado - acceso rápido para cambiar la distribución del teclado
* Terminal - acceso a la línea de comandos
* Wireshark - succionador de paquetes y analizador de protocolos de red

1. Abra la aplicación de terminal. Escriba el comando ip address en el intérprete de comandos, para determinar la dirección IP de la máquina virtual.
	* ¿Cuáles son las direcciones IP asignadas a su máquina virtual?
2. Localice e inicie la aplicación del navegador web.
	* ¿Puede entrar a su motor de búsqueda favorito?

### Paso 4: Cierre CSE-LABVM.
1. Presione la tecla Ctrl derecha para liberar el cursor de la máquina virtual. Ahora vaya al menú ubicado en la parte superior de la ventana de la máquina virtual y elija Archivo > Cerrar para cerrar la máquina virtual.
	* ¿Qué opciones están disponibles?
2. Haga clic en el botón de opción Guardar el estado de la máquina y haga clic en Aceptar. La próxima vez que inicie la máquina virtual, podrá volver a trabajar en el sistema operativo en su estado actual.

### Paso 5: importe e inicie la máquina virtual Security Workstation e inicie sesión.
1. Para importar la estación de trabajo de seguridad, siga los mismos procedimientos que utilizó para importar CSE-LABVM.
2. En el inventario que se muestra a la izquierda, seleccione la estación de trabajo de seguridad.
3. Haga clic en el botón Inicio y se iniciará el proceso de arranque de la máquina virtual.
4. Si recibe un error sobre su adaptador Ethernet, haga clic en Cambiar configuración de red. En la lista desplegable Nombre, elija el adaptador de red que utiliza su computadora para conectarse a Internet y haga clic en Aceptar.
5. Cuando se le solicite, cambie el usuario a analista, introduzca Cyberops como contraseña y haga clic en Iniciar sesión.

### Paso 6: Familiarícese con la estación de trabajo de seguridad.
La máquina virtual de la estación de trabajo de seguridad se basa en la distribución de Arch Linux para que pueda ejecutar una variedad de servicios con un impacto mínimo en los recursos de la máquina host. Siéntase libre de explorar la VM tanto como desee. Sin embargo, esta VM se explorará con más detalle en laboratorios posteriores.

### Paso 7: Cierre la estación de trabajo de seguridad.
En el menú de VirtualBox, elija Archivo > Cerrar, elija Guardar estado de la máquina y haga clic en Aceptar.

### Reflexión
¿Cuáles son las ventajas y desventajas de usar una máquina virtual?