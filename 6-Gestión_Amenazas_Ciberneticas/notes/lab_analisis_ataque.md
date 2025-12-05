<title coding="utf-8">Análisis del ataque</title>

# Análisis del ataque
# Objetivos
* __Parte 1__: investigar los IOC.
* __Parte 2__: investigar la actividad maliciosa.
* __Parte 3__: investigar la actividad más maliciosa.

# 

Introducción
Una vez que se ha informado y validado una alerta, se debe completar el análisis forense digital y la respuesta a incidentes. En una organización grande, los miembros del equipo de respuesta ante incidentes (CSIRT) son responsables de este proceso. El equipo de respuesta generalmente consiste en cazadores de amenazas veteranos y técnicos y analistas de ciberseguridad seleccionados. Para ayudar al equipo de respuesta de incidentes, hay varias herramientas y recursos disponibles.

En esta práctica de laboratorio, utilizará el servicio de detección de malware interactivo en línea ANY.RUN y la matriz Mitre ATT & CK para investigar posibles actividades maliciosas.

ANY.RUN ofrece un servicio gratuito en el que los usuarios de la comunidad pueden cargar archivos sospechosos de malware para su análisis. Proporciona un conjunto muy completo de funciones de análisis que le permite investigar con seguridad el comportamiento del malware. El sandbox ANY.RUN puede ejecutar el malware de manera dinámica y mostrar detalles de lo que hace el malware por medio de una una interfaz de análisis segura.

__Nota__: Utilizará la versión gratuita de ANY.RUN, que tiene funciones limitadas y solo puede ejecutar muestras de malware en una máquina virtual con Windows 7 de 32 bits. Dos versiones más avanzadas están disponibles para una suscripción mensual. Las versiones Searcher (Buscadores) y Hunter (Cazadores) proporcionan funciones avanzadas de acceso y otros sistemas operativos (por ejemplo, Windows 10).

# Situación
Usted está trabajando como técnico cibernético y ha sido seleccionado para trabajar con el equipo de respuesta ante incidentes de XYZ, Inc. Un analista de ciberseguridad le ha pedido que evalúe los valores hash de las alertas de seguridad generadas por el Sistema de Prevención de Intrusiones (IPS). El IPS ha marcado una serie de eventos como potencialmente maliciosos.

Utilizará la herramienta en línea ANY.RUN y la matriz Mitre ATT & CK para realizar un análisis forense basado en los valores hash proporcionados.

# Recursos necesarios
* Un dispositivo con acceso a Internet.

# Instrucciones
## Parte 1: Investigar los IOC
En esta parte, utilizará el sitio web ANY.RUN para clasificar los valores de hash identificados para ver si son maliciosos, sospechosos o benignos.

### Paso 1: Explore el sitio ANY.RUN
1. Abra un navegador web y vaya a la página ANY.RUN.
2. En la parte superior de la página web hay enlaces disponibles que comienzan con “WHY US” (Por qué nosotros). Haga clic en SERVICE (SERVICIO) en el menú horizontal para ir a la interfaz de servicio de sandbox.
3. Haga clic en uno de los países del mapa para ver la lista de envíos públicos de ese país. Los usuarios de la comunidad pueden ver un análisis detallado de cada envío.
4. Explore y familiarícese con este tablero. La herramienta ANY.RUN tiene muchas opciones disponibles que serán de gran valor para un analista de ciberseguridad. Aproveche esta oportunidad para obtener más información sobre la herramienta.

### Paso 2: Validar los hash sospechosos
En este paso, investigará algunos hash MD5 de archivos que el analista de ciberseguridad identificó en la tabla a continuación. Verificará si son potencialmente maliciosos, sospechosos o benignos.
1. Para buscar valores hash, haga clic en Public Tasks (Tareas Públicas) en el menú de la izquierda.
Esto abre la página Public submissions (Envíos públicos) que muestra una lista de tareas públicas organizadas por el envío más reciente. Tenga en cuenta que cada tarea está etiquetada con el veredicto de análisis que identifica el envío como ninguna amenaza detectada (es decir, benigna), actividad sospechosa o actividad maliciosa.
2. El analista de ciberseguridad le ha pedido que valide varios valores hash. Complete la siguiente tabla copiando y pegando el valor hash MD5 identificado en el cuadro de búsqueda en la parte superior derecha de la ventana y presione Enter.

|Valores de Hash MD5 de IOC|Malicioso / sospechoso / benigno| Nombre de archivo asociado
:-|:-|:-|
2fd03624e271ec70349ce56fb30f563b|Aquí su respuesta|Aquí su respuesta|
c419df63e0121d72411285780c2fc6cc|Aquí su respuesta|Aquí su respuesta|
3acf52e5a62d50bdcedcb89174bf5492|Aquí su respuesta|Aquí su respuesta|
766b774626947000e67e0b318f558e94|Aquí su respuesta|Aquí su respuesta|
422a6ca28a7e4d8e5e498523c6f049f4|Aquí su respuesta|Aquí su respuesta|
b497845beb135740e6caed03a2020036|Aquí su respuesta|Aquí su respuesta|

## Parte 2: Investigar la actividad maliciosa
En esta parte, utilizará el sitio web ANY.RUN para investigar la actividad maliciosa identificada en la parte anterior. Desde la herramienta ANY.RUN, pasará a diferentes herramientas para examinar la actividad maliciosa. Por último, utilizará la matriz Mitre ATT & K para identificar las tácticas y técnicas utilizadas por los agentes de amenazas.

### Paso 1: Investigar el primer árbol de proceso de hash malicioso.
1. Desde la página de envíos públicos ANY.RUN, busque el primer valor hash malicioso identificado en la Parte 1, paso 2b.
2. Haga clic en la entrada resultante para abrirla en el entorno limitado ANY.RUN. La interfaz de análisis ANY.RUN proporciona información sobre muchos aspectos del comportamiento del malware.
__Nota__: Si se muestra más de un envío, haga clic en el envío con el nombre del archivo wireframe.exe.
3. En el lado derecho de la pantalla, verá el árbol de procesos que muestra un grupo de barras azules horizontales en una estructura similar a un árbol anidado. Muestra todos los procesos de software que se utilizaron en el ataque. Algunos de ellos son componentes de software de Windows y otros son parte del malware.
* ¿Cuáles son los nombres de los procesos utilizados en esta actividad?
	* wireframe.exe, cmd.exe, timeout.exe y NvidiaGPU.exe.

### Paso 2: Investigar el informe de texto de actividad maliciosa.
Encima del árbol de procesos hay tres cuadros de texto etiquetados como “Text report” (Informe de texto), “Processes graph” (Gráfico de procesos) y ATT&CK matrix (Matriz de ATT y CK).
1. Haga clic en el Text report para abrir un informe en una nueva ventana del navegador web.
2. Desplácese por el documento para ver el informe generado.
* ¿Cuál es el valor SHA256 asociado a esta actividad?

### Paso 3: Investigar el gráfico de procesos de actividad maliciosa.
1. Regrese a la página web de análisis y haga clic en Processes graph.
	* ¿Qué proceso se ejecutó primero?
	* ¿Cuál es el nombre del proceso en el cuadro resaltado en rojo?
2. Haga clic en el cuadro resaltado en rojo.
	* ¿Cuál es el peligro identificado?

### Paso 4: Investigar la actividad maliciosa en la matriz de ATT y CK
1. Regrese a la página web de análisis y haga clic en ATT&CK matrix para abrir la página de ATT&CK matrix.
	* ¿Cuántas tácticas, técnicas y eventos hay relacionados con esta actividad maliciosa?
	* ¿Cuáles son las tácticas utilizadas por los agentes de la amenaza?
2. Haga clic en las diversas técnicas que se utilizaron.
	* ¿Qué técnica se identifica como Danger (Peligro)?

## Parte 3: Investigar la actividad más maliciosa
En esta parte, repetirá los pasos de la Parte 2 para examinar las otras dos entradas maliciosas descubiertas en la Parte 1.

### Paso 1: Investigar el segundo árbol de proceso de hash malicioso.
1. Regrese a la página de Public submissions en ANY.RUN y busque el segundo valor de hash malicioso identificado en la Parte 1, paso 2b.
2. Haga clic en la entrada resultante para abrirla en el entorno de prueba de ANY.RUN.
	* ¿Cuál es el nombre en el árbol de procesos utilizado en esta actividad?
3. Abra el Text Report (Informe de texto).
	* ¿Cuál es el valor SHA256 asociado a esta actividad?
4. Regrese a la página web de análisis y abra el Processes graph.
	* ¿Cuáles son los peligros identificados?
5. Regrese a la página web de análisis para abrir ATT&CK matrix.
	* ¿Cuántas tácticas, técnicas y eventos hay relacionados con esta actividad maliciosa?
	* ¿Cuáles son las tácticas utilizadas por los agentes de la amenaza?
6. Haga clic en las diversas técnicas que se utilizaron.
	* ¿Qué técnicas se identifican como peligrosas?

### Paso 2: Investigar el tercer árbol de proceso de hash malicioso
1. Vuelva a la página Public submissions de ANY.RUN y busque el tercer valor de hash malicioso identificado en la Parte 1, paso 2b.
2. Haga clic en la entrada resultante para abrirla en el entorno limitado ANY.RUN.
	* ¿Cuál es el nombre en el árbol de procesos utilizado en esta actividad?
3. Abra el Text Report (Informe de texto).
	* ¿Cuál es el valor SHA256 asociado a esta actividad?
4. Regrese a la página web de análisis y abra el Processes graph.
	* ¿Qué peligros muestra?
5. Regrese a la página web de análisis para abrir ATT&CK matrix.
	* ¿Cuántas tácticas, técnicas y eventos hay relacionados con esta actividad maliciosa?
	* ¿Cuáles son las tácticas utilizadas por los agentes de la amenaza?

# Preguntas de reflexión
1. Explique de qué manera el análisis forense y la respuesta ante incidentes se parecen mucho a la aplicación de la ley que intenta resolver un caso penal.
2. Dos de nuestras actividades maliciosas se referían a Redline. ¿Qué es la línea roja?



