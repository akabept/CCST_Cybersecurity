<title coding="utf-8">Registro desde varias fuentes</title>

# Packet Tracer - Registro de múltiples fuentes
# Objetivos
* __Parte 1__: Utilizar syslog para capturar archivos de registro de varios dispositivos de red
* __Parte 2__: Observar los registros de acceso de usuarios AAA
* __Parte 3__: Observar información de NetFlow

# Trasfondo/Situación
En esta actividad, utilizarán Packet Tracer para ver datos de red generados por syslog, AAA y NetFlow.

# Instrucciones
## Parte 1: Ver entradas de registro con Syslog
### Paso 1: El servidor syslog
Syslog es un sistema de mensajería diseñado para admitir el registro remoto. Los clientes syslog envían entradas de registro a un servidor syslog. El servidor syslog concentra y almacena las entradas de registro. Packet Tracer admite operaciones básicas de syslog y se puede utilizar con fines de demostración. La red incluye un servidor syslog y clientes syslog. R1, R2, el Switch de núcleo y el Firewall son clientes syslog. Estos dispositivos están configurados para enviar sus entradas de registro al servidor syslog. El servidor syslog recoge las entradas de registro y permite que se las lea.

Las entradas de registro se categorizan en siete niveles de gravedad. Los niveles más bajos representan los eventos más graves. Los niveles son los siguientes: emergencias (0), alertas (1), crítico (2) errores (3), advertencias (4), notificaciones (5), informativo (6) y depuración (7). Los clientes syslog se pueden configurar para enviar entradas de registro a servidores syslog en función del nivel de gravedad.
1. Haga clic en el servidor syslog para abrir su ventana.
2. Seleccione la pestaña de servicios y luego seleccione SYSLOG en la lista de servicios que aparece a la izquierda.
3. Haga clic en On(Encendido) para activar el servicio de syslog.
4. Las entradas de syslog provenientes de clientes serán mostradas en la ventana de la derecha. En este momento no hay ninguna entrada.
5. Mantener la ventana abierta y visible, mientras tanto siga con el paso 2.

### Paso 2: Habiliten Syslog
Los dispositivos ya están configurados para enviar mensajes de registro al servidor syslog, pero Packet Tracer solo admite el registro para el nivel de gravedad de depuración con syslog. Por eso debemos generar mensajes del nivel de depuración (nivel 7) para que se puedan enviar al servidor syslog.
1. Haga clic en el R1 > y luego en la pestaña CLI.
2. Presione Enter para obtener el commnad prompt e introduzca el comando enable.
3. Introduzca el comando debug eigrp packets para habilitar la depuración EIGRP. La consola de la línea de comandos se llenará inmediatamente con mensajes de depuración.
4. Regrese a la pestaña de servidor syslog. Verifiquen que las entradas de registro aparezcan en el servidor syslog.
5. Después de que se hayan registrado algunos mensajes, haga clic en el boton para poner los servicios de syslo Off(Desactivados).
	* Indiquen parte de la información que se incluye en los mensajes de syslog que está mostrando el Servidor Syslog.
6. Cierre la ventana del dispositivo R1.

### Paso 3: Registrar el acceso de los usuarios
Otro tipo importante de registro está relacionado con el acceso de los usuarios. Tener registros de los inicios de sesión de los usuarios es crucial para la solución de problemas y el análisis de tráfico. Cisco IOS admite Autenticación, Autorización y Auditoría (AAA). Con AAA, es posible no solo delegar la tarea de validación de usuarios a un servidor externo, sino también a actividades de registro.

TACACS+ es un protocolo diseñado para permitir la autenticación remota a través de un servidor centralizado.

Packet Tracer ofrece compatibilidad básica con AAA y TACACS+. R2 también está configurado como servidor TACACS+. R2 le preguntará al servidor si ese usuario es válido; para ello se verificará el nombre de usuario y la contraseña y se concederá o negará el acceso en función de la respuesta. El servidor almacena las credenciales del usuario y también es capaz de registrar transacciones de inicio de sesión del usuario. Sigan los pasos que se indican a continuación para iniciar sesión en R2 y mostrar las entradas de registro relacionadas con ese inicio de sesión:
1. Haga clic en el servidor syslog para abrir su ventana.
2. Seleccione la pestaña de Desktop(Escritorio) y luego AAA Accounting(Auditoría AAA). Dejen esta ventana abierta.
3. Haga clic en R2 > CLI.
4. Presione Enter para entrar al command prompt. R2 le pedirá su nombre de usuario y contraseña antes de otorgarle acceso a su CLI. Introduzca las siguientes credenciales de usuario: analyst y cyberops como nombre de usuario y contraseña, respectivamente.
5. Regrese a la ventana de AAA Accounting Records(Registro de auditoría AAA) del servidor syslog.
	* ¿Qué información se incluye en la entrada de registro?
6. En el R2, introduzca el comando logout.
	* ¿Qué sucedió en la ventana Auditoría AAA?

## Parte 2: NetFlow y visualización
En la topología, el servidor Syslog también es un colector de NetFlow. El firewall está configurado como exportador de NetFlow.
1. Haga clic en syslog server(Servidor syslog) para abrir su ventana. Cierren la ventana Registros de Auditoría AAA.
2. Desde la pestaña de Desktop seleccione NetFlow collector(Colector de NetFlow). Se deben activar los servicios del Colector del NetFlow.
3. Desde cualquier PC, haga ping al servidor web corporativo en la dirección 209.165.200.194. Después de una breve demora, el gráfico circular se actualizará para mostrar el nuevo flujo de tráfico.
	__Nota__: Los graficos circulares que se muestran varían en función del trafico que haya en la red. Otros flujos de paquetes, como el tráfico relacionado con EIGRP, se están enviando entre los dispositivos. NetFlow está capturando esos paquetes y exportando estadísticas al Colector de NetFlow. Cuanto más tiempo se permita ejecutar NetFlow en una red se capturarán más estadísticas sobre el tráfico.

# Reflexión
Si bien las herramientas presentadas en esta actividad son útiles, cada una tiene su propio servicio y es posible que tenga que ser ejecutada en dispositivos totalmente diferentes. Una mejor manera (que se analiza más adelante en el curso) es concentrar toda la información de registro en una sola herramienta, lo que permite facilitar la referencia cruzada y hace posibles potentes funcionalidades de búsqueda. Las plataformas de Administración de información y eventos de seguridad (Security Information and Event Management, SIEM) puede recopilar archivos de registro y otros datos de diversas fuentes e integrar la información correspondiente al acceso por medio de una sola herramienta.