# Configuración de funciones de seguridad en Windows y Linux
# Objetivos
* Parte 1: Actualizar Windows y Linux
* Parte 2: Política de seguridad local de Windows
* Parte 3: Configurar reglas de firewall
* Parte 4: Instalar y ejecutar aplicaciones

# Recursos necesarios
* Una PC con Windows 10.
* Esta máquina virtual CSE-LABVM
* Acceso a Internet

# Trasfondo/Situación
En esta práctica de laboratorio, actualizará los sistemas Windows y Linux. Configurará la política de seguridad local y las reglas de firewall en Windows. En Linux, instalará dos aplicaciones: _chkrootkit_ y _Lynis_.

# Instrucciones
## Parte 1: Actualice Windows y Linux
Continuamente se descubren nuevas vulnerabilidades y métodos de ataque. Es una buena idea mantener su PC actualizada para mitigar el aprovechamiento de las vulnerabilidades conocidas.

### Paso 1: Verifique la conectividad entre CSE-LABVM y la computadora host de Windows.
En este paso, verificará la conectividad a Internet para poder descargar actualizaciones. Además, verificará la conectividad entre CSE-LABVM y la PC con Windows para poder realizar tareas más adelante en esta práctica de laboratorio.
1. Antes de iniciar CSE-LABVM, selecciónelo y elija __Configuración > Red__. Para el `adaptador 1`, cambie la opción __Adjunto a: a Adaptador en puente__. Luego puede elegir el adaptador. Muchas computadoras tienen dos adaptadores: uno para redes inalámbricas y otro para redes cableadas. Elija el que usa su computadora para conectarse a Internet.
2. Inicie CSE-LABVM y espere a que arranque.
3. En CSE-LABVM, abra un terminal e introduzca la dirección IP para determinar su dirección IP.
4. En la computadora host de Windows, abra un símbolo del sistema e introduzca ipconfig para determinar su dirección IP.
	* Registre la dirección IP para CSE-LABVM y PC con Windows.
		* CSE-LABVM: 
		* Windows: 
5. Desde las solicitudes de comando respectivas, haga _ping_ en un sitio web de su elección para verificar que el host de Windows y CSE-LABVM puedan conectarse a Internet.
6. Verifique que el host de Windows pueda hacer _ping_ al CSE-LABVM.
7. Desde CSE-LABVM, intente hacer _ping_ al host de Windows. Es posible que CSE-LABVM no pueda hacer _ping_ al host de Windows debido a la configuración de firewall predeterminada en Windows. Modificará la regla del firewall más adelante en esta práctica de laboratorio para permitir el _ping_ a través del Firewall de Windows. Presione `<CTRL> + <C>` para detener los pings si es necesario.

### Paso 2: Verificación de actualizaciones de Windows
1. En el menú Inicio de Windows, busque Buscar actualizaciones.
2. En la ventana de Windows Update, puede revisar las actualizaciones opcionales y el historial de actualizaciones. Explore todas las opciones disponibles relacionadas con Windows Update y responda las siguientes preguntas.
	* ¿Cuándo fue la última vez que el sistema buscó actualizaciones?
	* ¿Cuáles son sus horas activas actuales? ¿Qué hará Windows fuera del horario de atención?

### Paso 3: actualización y actualización de Linux
1. En CSE-LABVM, introduzca el comando apto-get para ver la lista de comandos disponibles. El comando apto para actualizar siempre debe realizarse antes de una actualización.
2. Ingrese el comando `sudo apto-get update` para volver a sincronizar los archivos de índice del paquete de sus fuentes. Introduzca la contraseña `password` cuando se le solicite.
	```shell
	cisco@labvm:~$ sudo apt-get update
	[sudo] password para cisco:
	```
3. En el terminal, ingrese el comando `sudo apto-get` actualizar para recuperar y actualizar los paquetes instalados actualmente con nuevas versiones disponibles. Este comando no eliminará los paquetes instalados actualmente. Si no se puede actualizar la versión más reciente, no se realizarán cambios en los paquetes.
Introduzca la contraseña `password` cuando se le solicite. Responda `y` cuando se le pregunte si desea continuar. Este proceso puede demorar algunos minutos.
	```shell
	[sudo] password para cisco:
	Leyendo listas de paquetes... Listo.
	Construir árbol de dependencias.
	Leyendo la información del estado. Listo.
	Calculando la actualización... Listo.
	<output omitted>
	Necesita obtener 479 MB de archivos.
	Después de esta operación, se usarán 53.7 kB de espacio adicional en disco.
	¿Desea continuar? [Y/n] Y
	```

## Parte 2: política de seguridad local de Windows (opcional)
La Política de seguridad local de Windows de un sistema es un conjunto de información sobre la seguridad de su computadora. En esta parte, configurará la política de contraseña local, la configuración de bloqueo de cuenta y la política de auditoría.
__Nota__: La política de seguridad local solo viene con las ediciones Windows Pro o Enterprise. Si tiene la edición Home, puede buscar en Internet tutoriales sobre "Cómo habilitar la política de seguridad local (_secpol.msc_)". Por ejemplo, el sitio web <a href="majorgeeks.com" target="_blank">Major Geeks</a> tiene un excelente tutorial. Si no se le permite o prefiere no cambiar la política de seguridad local en su host de Windows, lea esta parte y pase a la siguiente.

### Paso 1: Configurar la política de contraseña local en Windows
Ha determinado que la política de seguridad para la contraseña es la siguiente:
* Un usuario debe utilizar una contraseña única al menos en 2 cambios de contraseña.
* Las contraseñas deben tener al menos 8 caracteres.
* Las contraseñas deben cambiar cada 90 días.
* Solo se puede cambiar la contraseña una vez al día.
* Una contraseña debe constar de tres de los siguientes cuatro elementos:
	* Al menos un carácter alfabético en minúsculas.
	* Al menos un carácter alfabético en mayúsculas.
	* Al menos un carácter numérico.
	* Al menos un carácter de símbolo.
1. Desplácese hasta la Política de seguridad local buscando primero y abriendo el Panel de control.
2. Pulse en __Herramientas Administrativas > Buscar política de seguridad local__.
3. Abra __Política de seguridad local__.
	* Enumere algunas configuraciones de políticas de seguridad:
4. Expanda __Políticas de cuenta__ y pulse en __Política de contraseñas__. Se muestran seis políticas en el panel derecho con sus configuraciones de seguridad predeterminadas asociadas.
5. La primera política, __Exigir historial de contraseñas__, se utiliza para establecer la cantidad de contraseñas únicas que el usuario debe introducir antes de permitirle reutilizar una contraseña. Haga doble pulsación en __Exigir historial de contraseñas__ para abrir la ventana __Exigir propiedades del historial de contraseñas__. Establezca el valor en `2`.
6. Mediante los requisitos de la política de seguridad del Paso 1, llene los valores que debe establecer en __Política de seguridad local__ para las configuraciones de seguridad de política de contraseñas restantes.

	|__Política__|__Configuración de seguridad__|
	|:-|-|
	|Exigir el historial de contraseñas||
	|Vigencia máxima de la contraseña||
	|Antigüedad mínima de contraseña||
	|Longitud mínima de la contraseña||
	|La contraseña debe cumplir con los requisitos de complejidad||
	|Guarde las contraseñas mediante cifrado reversible||
	
	__Nota__: La configuración de seguridad __Almacenar contraseñas con cifrado reversible__ debe estar desactivada en todo momento. Almacenar contraseñas mediante cifrado reversible es esencialmente lo mismo que almacenar las versiones de texto no cifrado de las contraseñas. Por este motivo, esta política nunca debe activarse a menos que los requisitos de aplicaciones sobrepasen la necesidad de proteger la contraseña.
7. Haga doble pulsación en cada una de las políticas y establezca los valores según las entradas en la tabla anterior.

### Paso 2: pruebe la configuración de seguridad de la política de contraseñas.
Pruebe las configuraciones de seguridad de políticas de contraseña intentando cambiar la contraseña. Intente con una nueva contraseña que no cumpla con la longitud o los requisitos de complejidad.
1. En el menú Inicio, busque "Cambiar contraseña".
2. Pulse en `Cambiar contraseña`. Pulse en `Cambiar`.
3. Ingrese su contraseña actual. Pulse en el botón `Siguiente` para continuar.
4. Ingrese la contraseña actual y proporcione su contraseña nueva dos veces. Asegúrese de que su nueva contraseña no cumpla con los requisitos de longitud o complejidad que configuró en el paso anterior. Haga clic en el botón `Siguiente` para continuar.
5. Haga clic en `Finish`. Se le debe indicar con un mensaje que su nueva contraseña no cumple con los requisitos de políticas de contraseña. Haga clic en `Cerrar` para continuar.

### Paso 3: Configure las configuraciones seguridad de la política de bloqueo de cuentas.
1. Vuelva a la ventana Política de seguridad local.
2. En las __Políticas de cuenta ampliadas__ pulse en __Política debloqueo de cuenta__. Se muestran tres políticas en el panel derecho con sus configuraciones de seguridad predeterminadas asociadas.
3. Cambie la configuración predeterminada a lo siguiente:
	* Un usuario debe esperar 10 minutos para que el contador se restablezca.
	* Los usuarios son bloqueados de la computadora después de 5 intentos de ingresar la contraseña correcta.
	* ¿Cuánto tiempo debe esperar el usuario antes de intentar volver a iniciar sesión?
	* ¿Cuántas veces se le permite a un usuario intentar iniciar sesión antes de que se bloquee la cuenta?

### Paso 4: configure los ajustes de seguridad de la política de auditoría.
1. Expanda el menú __Políticas locales__ y luego pulse en __Política de auditoría__.
2. Haga doble pulsación en __Auditar eventos de inicio de sesión de cuenta__ para abrir la ventana __Propiedades__.
3. Pulse en la pestaña __Configuración de seguridad local__, y luego en las casillas de verificación para __Correcto__ y __Error__.
4. Pulse en la pestaña __Explicar__ para obtener información sobre esta configuración de seguridad. Pulse en `Aceptar` para cerrar la ventana __Propiedades__.
5. Continúe revisando cada configuración de seguridad. Pulse en la pestaña __Explicar__ para cada uno y lea lo que hace.

## Parte 3: Configurar reglas de firewall
El tráfico ingresa y sale de los dispositivos mediante puertos. El firewall controla el flujo del tráfico. Piense en el firewall como un guardia de seguridad que controla el tráfico entrante y saliente según las reglas del firewall.

En esta parte, configurará el firewall de Windows Defender en Windows.

### Paso 1: Investigar el firewall de Windows Defender
1. Desde el menú __Inicio__, busque y abra el __Firewall de Windows Defender__. El estado normal del firewall de Windows es Activado.
__Nota__: Si utiliza una PC con Windows administrada por una organización, es posible que vea el mensaje: Para su seguridad, el administrador del sistema administra algunas configuraciones.
	* ¿Cuáles son los beneficios del Firewall de Windows?
2. En el panel izquierdo de la ventana, pulse en Permitir una aplicación o función a través de Firewall de Windows Defender l. En la ventana Aplicaciones y funciones permitidas, los programas y servicios que el Firewall de Windows no está bloqueando aparecerán con una marca de verificación.
__Nota__: Puede agregar aplicaciones a esta lista. Esto puede ser necesario si tiene una aplicación que requiere comunicaciones externas pero, por alguna razón, el Firewall de Windows no puede realizar la configuración automáticamente.
La creación de demasiadas excepciones en el archivo __Programas y servicios__ puede tener consecuencias negativas.
	* Describa una consecuencia negativa de tener demasiadas excepciones.
3. Pulse en Cancelar para salir de la ventana Permitir aplicaciones.

### Paso 2: configure las funciones de seguridad avanzada en el Firewall de Windows para permitir solicitudes de eco.
__Nota__: Este paso puede no estar permitido por la política de seguridad de su organización.

En este paso, creará una regla de entrada que permitirá los paquetes de solicitud de eco a través del firewall.
1. En el panel izquierdo de la ventana __Windows Firewall__ (Firewall de Windows), pulse en __Advanced settings__ (Configuración avanzada).
2. En __Firewall de Windows Defender con seguridad avanzada en la Máquina Local__, se pueden configurar las reglas de entrada, las reglas de salida y las reglas de seguridad de conexión. También puede hacer clic en __Supervisar__ para ver el estado de reglas configuradas.
3. Pulse en __Reglas entrantes__ y, en el panel __Acciones__, pulse en __Nueva regla__.
4. En el Asistente para nueva regla de entrada, seleccione __Personalizado__ y pulse en __Siguiente__ dos veces. Ahora debe estar en el paso de protocolo y puertos.
5. Para __Tipo de protocolo__, seleccione `ICMPv4` y pulse en __Personalizar__.
6. En la ventana __Personalizar configuración de ICMP__, seleccione __Tipos de ICMP específicos__, seleccione __Solicitud de eco__ y pulse en `Aceptar`.
7. Pulse en `OK` (Aceptar) tres veces. Ahora debe estar en el paso __Perfil__.
8. Anule la selección de __Public__ (Public) para que la PC con Windows no responda a una solicitud de eco en una ubicación de red pública, como un cibercafé. Haga clic en el botón __Siguiente__ para continuar.
9. Proporcione un nombre para la nueva regla entrante que proporcione una buena descripción de la regla y haga clic en __Finalizar__. Ahora debería ver su regla en la parte superior de la lista de __Reglas de entrada__ en el cuadro de diálogo __Firewall de Windows Defender con seguridad avanzada__.
10. Ahora la regla se ha creado y habilitado. Verifique que CSE-LABVM pueda hacer _ping_ al host de Windows y recibir respuestas.

## Parte 4: Instalar y ejecutar aplicaciones
En esta parte, instalará dos nuevas aplicaciones en CSE-LABVM: __chkrootkit__ y __Lynis__. La aplicación __chkrootkit__ se descargará de un repositorio de software. Sin embargo, agregaremos un nuevo repositorio para poder instalar __Lynis__, provisto por CISOfy.

### Paso 1: Instale y ejecute chkrootkit
La herramienta __chkrootkit__ se utiliza para verificar si hay signos de un _rootkit_ en un sistema local. _Rootkit_ es un tipo de malware que puede permanecer oculto en su computadora y puede ser utilizado para causar daños significativos a su dispositivo por _hackers_.
1. En una terminal, introduzca el comando `sudo apt` para instalar __chkrootkit__. Introduzca la contraseña `password` cuando se le solicite.
	```shell
	Cisco @ labvm: ~ $ sudo apt chkrootkit
	[sudo] password para cisco:
	```
2. Ingrese el comando `sudo chkrootkit` para ejecutar una comprobación de _rootkit_.
	```shell
	cisco @ labvm: ~ $ sudo chkrootkit
	```
3. La salida se puede filtrar para buscar cadenas interesadas, como gusanos. El comando `chkrootkit` se puede canalizar junto con el comando `grep` con la opción `–i` para ignorar la distinción de mayúsculas y minúsculas en las cadenas de interés.
	```shell
	cisco @ labvm: ~ $ sudo chkrootkit | grep -i gusano
	Buscando archivos LPD Worm y directorios ... no se encontró nada
	Buscando archivos y directorios de Ramen Worm ... no se encontró nada
	Buscando Adore Worm ... No se encontró nada.
	Buscando ShitC Worm ... no se encontró nada
	Buscando Omega Worm ... no se encontró nada
	Buscando Sadmind / IIS Worm ... no se encontró nada
	Buscando archivos y directorios predeterminados de TC2 Worm ... no se encontró nada
	! Cisco 32822 pts / 0 grep --color = auto -i gusano
	```

### Paso 2: Instalar Lynis
Lynis es una herramienta de seguridad para sistemas que ejecutan sistemas operativos basados en Unix, como Linux y macOS. Lynis se utilizará más adelante en otra actividad para fortalecer un sistema Linux. CISOfy mantiene la aplicación L ynis.CISOfy. En este paso, agregaremos el repositorio de software e instalaremos Lynis.
1. Copie y pegue el siguiente comando en un terminal para importar la clave del servidor de claves CISOfy. Esta clave es necesaria para verificar la integridad de la descarga cuando descarga Lynis:
	```shell
	Cisco @ labvm: ~ $ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 013baa07180c50a7101097ef9de922f1c2fde6c4
	Ejecución: /tmp/apt-key-gpghome.8C6X477onz/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys 013baa07180c50a7101097ef9de922f1c2fde6c4
	gpg: key FEBB7D1812576482: key pública "CISOfy software sign<software@cisofy.com> "importado
	gpg: Número total procesado: 1
	gpg: importado: 1
	```
2. Copie y pegue el siguiente comando en una terminal para agregar el repositorio de Lynis que mantiene CISOfy.
	```shell
	cisco @ labvm: ~ $ echo "deb https://packages.cisofy.com/community/lynis/deb/ estable main" | sudo tee /etc/apt/sources.list.d/cisofy-lynis.list
	deb https://packages.cisofy.com/community/lynis/deb/ estable main
	```
3. Realice una actualización después de agregar un nuevo repositorio. Cuando se le solicite, ingrese `sudo apto-get update`.
4. Utilice el comando `apt` para instalar Lynis si aún no está instalado.
	```shell
	Cisco @ Labvm: ~ $ sudo apto instalar Lynis
	Leyendo listas de paquetes... Listo.
	Construir árbol de dependencias.
	Leyendo la información del estado. Listo.
	Se instalarán los siguientes paquetes NUEVOS:
	Lynis
	0 actualizado, 1 recién instalado, 0 para eliminar y 0 no actualizado.
	Necesita obtener 23,9 kB de archivos.
	Después de esta operación, se usarán 1,681 kB de espacio adicional en disco.
	Seleccionar paquete speedtest-cli previamente no seleccionado.
	(Leyendo base de datos... 205787 archivos y directorios instalados actualmente.)
	Preparándose para desempaquetar ... / lynis_3.0.6-100_all.deb ...
	Desembalaje de Lynis (3.0.6-100) ...
	Configuración de Lynis (3.0.6-100) ...
	Procesando activadores para man-db (2.9.1-1) ...
	```
	* En la salida, ¿cuál es la versión instalada de Lynis?
5. Para verificar la versión instalada, ingrese el comando lynis show version en la terminal.
	```shell
	cisco @ labvm: ~ $ lynis show version
	3.0.6
	```
6. Si desea determinar la última versión proporcionada por CISOfy, introduzca el siguiente comando en el terminal.
	```shell
	cisco @ labvm: ~ $ sudo lynis --version --remote || lynis update info
	Lynis:
	Instalado: 3.0.6-100
	Candidato: 3.0.6-100
	Tabla de versiones:
	 *** 3.0.6-100 500
	500 https://packages.cisofy.com/community/lynis/deb estable / paquetes de amd64
	500 https://packages.cisofy.com/community/lynis/deb estable / paquete principal de i386
	100 / var / lib / dpkg / status
	2.6.2-1 500
	500 paquetes http://archive.ubuntu.com/ubuntu focal / universe amd64
	500 paquetes http://archive.ubuntu.com/ubuntu focal / universe i386
	```
7. Puede ejecutar `sudo apt-get update` y `sudo apto-get upgrade` nuevamente para asegurarse de contar con las últimas actualizaciones de CISOfy.
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />