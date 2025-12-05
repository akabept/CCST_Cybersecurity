<a href="./00-Curso.md"><< Menú principal del módulo</a>

# Análisis forense digital y análisis y respuesta a incidentes
# Manejo de evidencia y atribución del ataque
## Informática Forense Digital
Ahora que se han investigado e identificado las alertas válidas, ¿qué se debe hacer con las pruebas? Inevitablemente, el analista especializado en ciberseguridad descubrirá evidencia de actividades delictivas. Con el fin de proteger la organización y para evitar la ciberdelincuencia, es necesario identificar los actores de amenaza, informar a las autoridades competentes y brindar pruebas para respaldar la acusación. Los analistas de ciberseguridad de categoría 1 suelen ser los primeros en descubrir delitos. Deben saber cómo manejar la evidencia correctamente y atribuírsela a los actores de amenaza.

La informática forense digital consiste en la recuperación e investigación de la información que se encuentra en dispositivos digitales en relación con actividades delictivas. Los indicadores de compromiso son la evidencia de que se ha producido un incidente de ciberseguridad. Esta información puede consistir en datos en dispositivos de almacenamiento, en la memoria volátil de la computadora, o los rastros de ciberdelincuencia que se conservan en los datos de la red, como pcaps y registros. Es esencial que se conserven todos los indicadores de compromiso para futuros análisis y atribución de ataques.

En términos generales, la ciberdelincuencia se puede caracterizar como proveniente del interior o el exterior de la organización. Las investigaciones privadas se realizan a individuos dentro de la organización. Estos individuos podrían simplemente comportarse de maneras que violan los acuerdos de usuario o manifestar otra conducta no delictiva. Cuando los individuos son sospechosos de participar en actividades delictivas que involucran el robo o la destrucción de propiedad intelectual, una organización puede optar por involucrar a las autoridades encargadas del orden público, en cuyo caso la investigación se vuelve pública. Los usuarios internos también pueden usar la red de la organización para llevar a cabo otras actividades delictivas que no están relacionadas con la misión de la organización, pero sí violan diversas leyes. En este caso, los funcionarios públicos llevarán a cabo la investigación.

Cuando un atacante externo ataca una red y roba o altera datos, es necesario recopilar evidencia para documentar el alcance del ataque. Diversos organismos reguladores especifican una serie de acciones que una organización debe adoptar cuando se ponen en riesgo distintos tipos de datos. Los resultados de la investigación forense pueden ayudar a identificar las medidas que deben tomarse.

Por ejemplo, las regulaciones de US HIPAA estipulan que, si ocurre una violación de datos que involucra información de pacientes, se debe notificar a las personas afectadas. Si la violación involucra a más de 500 personas en un estado o jurisdicción, se debe notificar también a los medios de comunicación. La investigación de informática forense digital debe utilizarse para determinar qué personas fueron afectadas y certificar la cantidad de individuos involucrados a fin de que pueda efectuarse la notificación correspondiente de acuerdo con las reglas de la HIPAA.

Es posible que la propia organización sea objeto de una investigación. Los analistas de ciberseguridad pueden encontrarse en contacto directo con evidencia forense digital que detalle la conducta de los miembros de la organización. Los analistas deben conocer los requisitos relativos a la preservación y el manejo de dicha evidencia. Si no lo hacen correctamente, esto podría ocasionar sanciones penales para la organización y hasta para el analista de ciberseguridad si se establece que hubo intención de destruir pruebas.

## El proceso forense digital
Es importante que una organización desarrolle procesos y procedimientos bien documentados para el análisis forense digital. El cumplimiento reglamentario puede exigir esta documentación y las autoridades pueden inspeccionarla en caso de una investigación pública.

La publicación especial 800-86 de NIST Guía para la Integración de Técnicas Forenses en Respuesta a Incidentes es un recurso valioso para las organizaciones que requieren orientación en el desarrollo de planes forenses digitales. Por ejemplo, recomienda que la informática forense se realice mediante el proceso de cuatro fases.

A continuación se describen las cuatro fases básicas del proceso forense de pruebas digitales.

<div style="width: 50%; padding-left: 20%;">
	<img src="./img/proceso-forense-evidencia-digital.png" />
</div>

1. __Recolección__. Esta es la identificación de posibles fuentes de datos forenses y la obtención, el manejo y el almacenamiento de esos datos. Esta etapa es fundamental porque se debe tener especial cuidado para no dañar, perder u omitir datos importantes.
2. __Examen__. Esto implica evaluar y extraer información relevante de los datos recopilados. Esto puede implicar la descompresión o el descifrado de los datos. Es posible que sea necesario eliminar información irrelevante para la investigación. La identificación de evidencia real en grandes recopilaciones de datos puede ser un proceso muy difícil y lento.
3. __Análisis__. Esto implica sacar conclusiones de los datos Se deben documentar las características salientes; por ejemplo: personas, lugares, horas y eventos, entre otras. Este paso puede implicar también la correlación de datos de múltiples fuentes.
4. __Informes__. Esto implica preparar y presentar la información que resulte del análisis. La elaboración de informes debe ser imparcial y se deben ofrecer explicaciones alternativas si corresponde. Deben incluirse las limitaciones del análisis y los problemas que se enfrentaron. También deben hacerse sugerencias para profundizar la investigación y tomar medidas adicionales.

## Tipos de evidencia
En los procedimientos legales y en términos generales, la evidencia se clasifica como directa o indirecta. La evidencia directa es aquella consta de la evidencia que indudablemente poseía el acusado o de afirmaciones de un testigo presencial que vio directamente el comportamiento delictivo.
Adicionalmente, la evidencia se clasifica del siguiente modo:
* __Mejor evidencia__. Esto es evidencia de que está en su estado original. Esta evidencia podrían ser los dispositivos de almacenamiento utilizados por un acusado o archivos que se pueda probar que no fueron alterados.
* __Evidencia corroborativa__. Esta es evidencia que respalda una afirmación que se desarrolla a partir de la mejor evidencia.
* __Evidencia indirecta__. Esta es una evidencia que, en combinación con otros hechos, establece una hipótesis. También se conoce como evidencia circunstancial. Por ejemplo, la existencia de pruebas que demuestren que un individuo ya cometió delitos similares puede respaldar la afirmación de que la persona cometió el delito del que se la acusa.

## Orden de recolección de evidencia
IETF RFC 3227 proporciona pautas para la recolección de evidencia digital. Describe un orden para la recolección de evidencia digital según la volatilidad de los datos. Los datos almacenados en la memoria RAM son los más volátiles y se perderán cuando se apague el dispositivo. Además, podría suceder que los datos importantes en la memoria volátil se sobrescriban mediante procesos rutinarios de la máquina. Por lo tanto, la recolección de evidencia digital debe comenzar con las pruebas más volátiles hasta llegar a las menos volátiles, como se muestra en la figura.

### Prioridad de recolección de evidencias

<div style="width: 30%; padding-left: 30%;">
	<img src="./img/prioridad-recoleccion-evidencias.png" />
</div>

Un ejemplo de recolección de evidencia desde la más volátil a la menos volátil es el siguiente:
* Registros de memoria, memoria caché.
* Tabla de routing, caché de ARP, tabla de procesos, estadísticas del núcleo, memoria RAM.
* Sistemas de archivos temporales.
* Medios no volátiles, fijos y extraíbles.
* Registros remotos y datos de monitoreo.
* Topologías e interconexiones físicas.
* Medios de archivado, cinta u otros tipos de copias de respaldo.

Deben registrarse detalles de los sistemas desde los que se recopiló la evidencia, lo que incluye quién tiene acceso a los sistemas y en qué nivel de permisos. Estos detalles deben incluir configuraciones de hardware y software para los sistemas desde los que se obtuvieron los datos.

## Cadena de custodia
Aunque es posible que la evidencia se haya recopilado de fuentes que respaldan la atribución del delito a un individuo acusado, puede cuestionarse la veracidad de las pruebas aduciendo que podrían haberse alterado o fabricado después de la recopilación. Para contrarrestar este argumento, debe definirse y respetarse una rigurosa cadena de custodia.

La cadena de custodia implica la recolección, el manejo y el almacenamiento seguro de la evidencia. Deben mantenerse registros detallados de lo siguiente:
* ¿Quién descubrió y recopiló la evidencia?
* Todos los detalles sobre el manejo de la evidencia, incluidos momentos, lugares y personal involucrado.
* ¿Quién era el responsable principal de la evidencia, cuándo se le asignó la responsabilidad y cuándo cambió la custodia?
* Quién tiene acceso físico a la evidencia mientras está almacenada. El acceso debe limitarse solamente al personal esencial.

## Integridad y preservación de los datos
Al recopilar datos, es importante que se conserven en su estado original. La marca de hora de los archivos debe conservarse. Por esto, debe copiarse la evidencia original y los análisis deben realizarse solamente en las copias del original. Esto permite evitar la pérdida o modificación accidental de las pruebas. Dado que las marcas de hora pueden formar parte de la evidencia, se debe evitar abrir archivos desde el medio original.

Deberá registrarse el proceso utilizado para crear copias de la evidencia que se utiliza en la investigación. Siempre que sea posible, las copias deben ser copias directas de nivel de bit de los volúmenes de almacenamiento originales. Debería ser posible comparar la imagen del disco archivado y la imagen del disco investigada para identificar si se ha manipulado el contenido del disco investigado. Por esta razón, es importante archivar y proteger el disco original para mantenerlo en su condición original, sin alteraciones.

La memoria volátil podría contener evidencia forense, por lo que deben utilizarse herramientas especiales para preservar dicha evidencia antes de que el dispositivo se apague y las pruebas se pierdan. Los usuarios no deben desconectar, desenchufar ni apagar máquinas infectadas, a menos que el personal de seguridad lo indique explícitamente.

El seguimiento de estos procesos garantizará que se conserven todas las pruebas de conducta ilícita y que se puedan identificar indicadores de avenencia.

## Atribución del ataque
Después de que se ha evaluado el nivel del ciberataque y se ha recopilado y preservado la evidencia, el equipo de respuesta ante los incidentes puede comenzar a identificar el origen del ataque. Como sabemos, existe una amplia variedad de actores de amenazas, que abarca desde individuos descontentos y hackers, hasta ciberdelincuentes y bandas criminales o incluso naciones. Algunos delincuentes actúan desde el interior de la red, mientras que otros pueden estar del otro lado del mundo. La sofisticación de la ciberdelincuencia también varía. Las naciones pueden emplear a grandes grupos de individuos altamente capacitados para llevar a cabo un ataque y ocultar sus rastros, mientras que otros actores de amenaza pueden elegir presumir abiertamente de sus actividades delictivas.

La atribución de una amenaza hace referencia a la acción de determinar a la persona, organización o nación responsable de una intrusión o ataque exitosos.

La identificación de los actores responsables de una amenaza debe darse por medio de la investigación sistemática y fundamentada de la evidencia. Mientras que puede resultar útil especular también sobre la identidad de los agentes de amenaza identificando posibles motivaciones para un incidente, es importante no dejar que esto desvíe la investigación. Por ejemplo, atribuir un ataque a un competidor comercial puede desviar la investigación de la posibilidad de que una banda criminal o una nación sean los responsables.

En las investigaciones con base en evidencias, el equipo de respuesta ante los incidentes correlaciona las tácticas, las técnicas y los procedimientos (TTP, Tactics, Techniques and Procedures) empleados en el incidente con los de otros ataques conocidos. Los ciberdelincuentes, al igual que muchos otros delincuentes, tienen características específicas que se repiten en la mayoría de sus delitos. Las fuentes de inteligencia de amenazas pueden ayudar a relacionar las TTP identificadas por una investigación con fuentes conocidas de ataques similares. Sin embargo, esto pone de relieve un problema con la atribución de la amenaza. Es muy improbable que la evidencia de ciberdelincuencia sea directa. Identificar similitudes entre las TTP de agentes de amenazas conocidos y desconocidos es evidencia circunstancial.

Algunos aspectos de una amenaza que pueden ayudar a la atribución son la ubicación de los hosts o dominios originarios, las características del código utilizado en malware, las herramientas utilizadas y otras técnicas. A veces, en el ámbito de la seguridad nacional, no es posible atribuir abiertamente las amenazas porque esto dejaría al descubierto métodos y capacidades que necesitan protección.

Para las amenazas internas, la administración de activos desempeña un papel fundamental. Descubrir los dispositivos desde donde se inició un ataque puede llevar directamente al agente de amenaza. Las direcciones IP, las direcciones MAC y los registros de DHCP pueden ayudar a rastrear las direcciones usadas en el ataque hasta llegar a un dispositivo específico. Los registros de AAA son muy útiles en este sentido, ya que detallan quién tuvo acceso a los recursos de red, en qué momento lo hizo y qué recursos eran.

## El marco MITRE ATT&CK
Una forma de atribuir un ataque es modelar el comportamiento del actor de amenazas. El marco de Tácticas Adversariales, Técnicas y Conocimiento Común (ATT&CK) de MITRE permite detectar tácticas, técnicas y procedimientos del atacante como parte de la defensa de amenazas y la atribución de ataques. Esto se hace mapeando los pasos de un ataque a una matriz de tácticas generalizadas y describiendo las técnicas que se utilizan en cada táctica. Las tácticas consisten en los objetivos técnicos que un atacante debe lograr para ejecutar un ataque y las técnicas son los medios por los que se realizan las tácticas. Por último, los procedimientos son las acciones específicas tomadas por los actores de amenazas en las técnicas identificadas. Los procedimientos son el uso documentado de técnicas en el mundo real por parte de los actores de amenazas.

El marco MITRE ATT&CK es una base de conocimiento global sobre el comportamiento de los actores de amenazas. Se basa en la observación y el análisis de ataques en el mundo real con el propósito de describir el comportamiento del atacante, no el ataque en sí. Está diseñado para permitir el intercambio automatizado de información mediante la definición de estructuras de datos para el intercambio de información entre su comunidad de usuarios y MITRE.

La figura muestra un análisis de una explotación de ransomware de la excelente caja de arena en línea ANY.RUN. Las columnas muestran las tácticas de matriz de ataque empresarial, con las técnicas que utiliza el malware dispuestas debajo de las columnas. Al hacer clic en la técnica, se enumeran los detalles de los procedimientos que utiliza la instancia específica de malware con una definición, explicación y ejemplos de la técnica.

__Nota__: Haga una búsqueda en Internet de MITRE ATT&CK para obtener más información sobre la herramienta.

### Matriz MITRE ATT&CK para una Explotación de Ransomware

<div style="padding-left: 15%;">
	<img src="./img/matriz-mitre-attack.png" />
</div>

## Práctica de laboratorio - Recopilación de información del sistema después de un incidente
* <a href="./notes/lab_recopilacion_info_tras_incidente.md" target="_blank">Recopilación de información del sistema después de un incidente</a>

# La cadena de eliminación cibernética
## Pasos de la cadena de eliminación cibernética
La Cadena de Eliminación Cibernética fue desarrollada por Lockheed Martin para identificar y evitar ciberintrusiones. Hay siete pasos a la Cadena de Eliminación Cibernética. Enfocarse en estos pasos ayuda a los analistas a entender las técnicas, herramientas y procedimientos de los actores de amenaza. Al responder a un incidente de seguridad, el objetivo es detectar y detener el ataque lo antes posible en el transcurso de la cadena de eliminación. Cuanto antes se detenga el ataque, menor será el daño y menor será la información que el atacante obtenga acerca de la red atacada.

En la Cadena de Eliminación Cibernética, se detalla qué debe hacer un atacante para alcanzar su objetivo. Los pasos de la Cadena de Eliminación Cibernética se muestran en la figura.

Si el atacante es detenido en cualquier etapa, se rompe la cadena del ataque. Romper la cadena significa que el defensor frustró con éxito la intrusión del actor de amenaza. Los actores de amenaza tienen éxito solamente si completan el paso 7.

__Nota__: Actor de amenaza es el término utilizado en este curso para referirse al participante que instiga el ataque. Sin embargo, Lockheed Martin utiliza el término "adversario" en su descripción de la Cadena de Eliminación Cibernética. Por lo tanto, los términos adversario y actor de amenaza, se usan como sinónimos en este tema.

<div style="padding-left: 15%;">
	<img src="./img/pasos-cadena-eliminacion.png" />
</div>

## Reconocimiento
El Reconocimiento tiene lugar cuando el actor de amenaza realiza una búsqueda, reúne inteligencia y selecciona objetivos. Esto le permite determinar al actor de amenaza si vale la pena realizar el ataque. Cualquier información pública puede ayudar a determinar qué, dónde, y cómo fue el ataque realizado. Hay mucha información disponible para el público, especialmente en el caso de organizaciones importantes; esto incluye artículos de prensa, sitios web, actas de conferencias y dispositivos de red orientados al público. Cada vez hay más información disponible sobre los empleados en las redes sociales.

El actor de amenaza escogerá objetivos descuidados o sin protección porque hay una mayor posibilidad de penetrarlos y atacarlos exitosamente. El actor de amenaza analiza toda la información que obtiene para determinar su importancia y ver si revelan otras vías posibles de ataque.

La tabla resume algunas de las tácticas y defensas que se utilizan durante el paso de reconocimiento.

<table>
	<tr><th>Tácticas del adversario<th>Defensa del SOC
	<tr><td>Planear y realizar investigaciones:<br /><ul><li>Recolectar correos electrónicos<li>Identificar empleados en redes sociales<li>Recopilar información de relaciones públicas (comunicados de prensa, premios, asistentes a conferencias, etc.)<li>Descubrir servidores orientados a Internet<li>Realizar escaneos de la red para identificar direcciones IP y puertos abiertos</ul><td>Descubrir la intención del adversario:<br /><ul><li>Alertas de registro web y datos de búsqueda histórica<li>Análisis del navegador del minado de dastos<li>Crear guías para detectar comportamientos que idiquen actividad de reconocimiento<li>Priorizar la defensa en torno a las tecnologías y las personas a las que apunta la actividad de reconocimiento</ul>
</table>

## Armamentización
El objetivo de este paso es utilizar la información de reconocimiento para desarrollar un arma contra sistemas o individuos que sean blancos específicos en la organización. Para el desarrollo de esta arma, el diseñador utilizará las vulnerabilidades de los activos que se detectaron y las incorporará en una herramienta que pueda implementarse. Después de que la herramienta se haya utilizado, se espera que el actor de amenaza haya logrado su objetivo de tener acceso al sistema o la red de destino, lo que afecta el estado de un objetivo o de toda la red. El actor de amenaza examinará en más detalle la seguridad de la red y los activos para poner de manifiesto debilidades adicionales, obtener el control de otros activos e implementar ataques adicionales.

No es difícil elegir un arma para el ataque. El actor de amenaza solo necesita ver qué ataques están disponibles para las vulnerabilidades que detectó. Hay muchos ataques prediseñados y ampliamente probados. Uno de los problemas de estos ataques es que, debido a que son tan conocidos, es muy probable que también los conozcan los defensores. A menudo, es más eficaz utilizar un ataque de día cero para evitar los métodos de detección. Un ataque de día cero utiliza un arma desconocida para los defensores y los sistemas de seguridad de la red. El actor de amenaza puede elegir desarrollar su propia arma específicamente diseñada para evitar la detección, con la información que obtuvo sobre la red y los sistemas. Los atacantes han aprendido a crear numerosas variantes de sus ataques para evadir las defensas de la red.

La tabla resume algunas de las tácticas y defensas que se utilizan durante el paso de armamentización.

<table>
	<tr><th>Tácticas del adversario<th>Defensa del SOC
	<tr><td>Preparar y organizar la operación:<br /><ul><li>Obtener una herramienta automatizada para entregar la carga útil de malware (arma)<li>Seleccionar o crear un documento para presentar a la víctima<li>Seleccionar o crear una puerta trasera y una infraestructura de comando y control</ul><td>Detectar y recolectar artefactos de armamento:<br /><ul><li>Asegurarse de que las reglas y firmas de IDS estén actualizadas<li>Realizar un análisis completo de malware<li>Crear detecciones para el comportamiento de las armas conocidas<li>¿Es el malware antiguo, "listo para usar" o nuevo que podría indicar un ataque personalizado?<li>Recopilar archivos y metadatos para análisis futuros<li>Determinar qué artefactos de armamento son comunes a qué campañas</ul>
</table>

## Entrega
Durante este paso, el arma se transmite al objetivo mediante un vector de entrega. Esto puede ocurrir usando un sitio web, un medio USB extraíble o un archivo adjunto de correo electrónico. Si no se entrega el arma, el ataque no tiene éxito. El actor de amenaza utilizará muchos métodos diferentes para aumentar las posibilidades de entrega de la carga útil, como encriptar las comunicaciones, modificar el código para que parezca legítimo u ocultar el código. Los sensores de seguridad son tan avanzados que pueden detectar el código malicioso, a menos que se altere para evitarlo. El código puede modificarse para parecer inocente y tener la capacidad de realizar las acciones necesarias, aunque podría demorar más tiempo en ejecutarse.

La tabla resume algunas de las tácticas y defensas que se utilizan durante el paso de entrega.

<table>
	<tr><th>Tácticas del adversario<th>Defensa del SOC
	<tr><td>Lanzar malware al objetivo:<br /><ul><li>Directo contra servidores web<li>Entrega indirecta a través de:<ul><li>Correo electrónico malicioso<li>Malware en memoria USB<li>Interacciones en las redes sociales<li>Sitios web compromentidos</ul></ul><td>Bloquear la entrega de malware:<br /><ul><li>Analizar la ruta de infraestructura utilizada para la entrega<li>Comprender los servidores objetivo, las personas y los datos disponibles para atacar<li>Inferir la intención del adversario en función de los objetivos<li>Recopilar registros web y de correo electrónico para la reconstrucción forense</ul>
</table>

## Explotación
Una vez aplicada el arma, el actor de la amenaza la utiliza para quebrar la vulnerabilidad y obtener el control del objetivo. Los objetivos de ataque más comunes son las aplicaciones, las vulnerabilidades de sistemas operativos y los usuarios. El atacante debe utilizar un ataque que tenga el efecto deseado. Esto es muy importante porque, si se ejecuta el ataque incorrecto, está claro que no funcionará, pero los efectos secundarios imprevistos, como una denegación de servicio o reinicios reiterados del sistema, causarán una atención indebida que podría informar fácilmente a los analistas de ciberseguridad sobre el ataque y las intenciones del actor de la amenaza.

La tabla resume algunas de las tácticas y defensas que se utilizan durante el paso de aprovechamiento.

<table>
	<tr><th>Tácticas del adversario<th>Defensa del SOC
	<tr><td>Explotar una vulnerabilidad para obtener acceso:<br /><ul><li>Usar vulnerabilidades de software, de harware o humanas<li>Adquirir o desarrollar el ataque<li>Utilizar un ataque desencadenado por el adversario para las vulnerabilidades del servidor<li>Usar el ataque activado por la víctima, como abrir un archivo adjunto de correo electrónico o un enlace web malicioso</ul><td>Entrene a los empleados, asegure el código y endurezca los dipositivos:<br /><ul><li>Capacitar a los empleados de concientización sobre la seguridad y hacer pruebas periódicas de correo electrónico<li>Capacitar a desarrolladores web para asegurar el código<li>Escaneo regular de vulnerabilidades y pruebas de penetración<li>Medidas de endurecimiento de puntos finales<li>Auditoría de puntos finales para determinar de forma forense el origen del ataque</ul>
</table>

## Instalación
En este paso, el actor de amenaza establece una puerta trasera al sistema para poder seguir teniendo acceso al objetivo. Para preservar esta puerta trasera, es importante que el acceso remoto no alerte a los analistas de ciberseguridad ni a los usuarios. Para ser eficaz, el método de acceso debe sobrevivir a los análisis antimalware y al reinicio de la computadora. Este acceso persistente también puede permitir las comunicaciones automatizadas, que resultan especialmente eficaces cuando se necesitan varios canales de comunicación al comandar una botnet.

La tabla resume algunas de las tácticas y defensas que se utilizan durante el paso de instalación.

<table>
	<tr><th>Tácticas del adversario<th>Defensa del SOC
	<tr><td>Instalar una puerta trasera persistente:<br /><ul><li>Instalar webshell en el servidor web para un acceso persistente<li>Crear un punto de persistencia agregando servicios, clave de ejecución automática, etc.<li>Algunos adversarios modifican la marca de tiempo del malware para que aparezca como parte del sistema operativo</ul><td>Detectar, registrar y analizar la actividad de instalación:<br /><ul><li>HIPS para alertar sobre rutas de instalación comunes<li>Determinar si el malware requiere privilegios elevados o privilegios de usuario<li>Auditoría de puntos finales para descubrir creaciones de arvhivos anormales<li>Determinar si el malware es  una amenaza conocida o una nueva variante</ul>
</table>

## Comando y control
En este paso, el objetivo es establecer el comando y control (CnC o C2) con el sistema objetivo. Los hosts atacados suelen enviar información fuera de la red a un controlador en Internet. Esto ocurre porque la mayoría del malware requiere la interacción manual para exfiltrar datos de la red. El actor de amenaza utiliza los canales de CnC para emitir comandos al software que instala en el objetivo. El analista de ciberseguridad debe ser capaz de detectar comunicaciones de CnC para descubrir el host atacado. Esto puede hacerse con tráfico no autorizado de Internet Relay Chat (IRC) o tráfico excesivo hacia los dominios sospechosos.

La tabla resume algunas de las tácticas y defensas que se utilizan durante el paso de comando y control.

<table>
	<tr><th>Tácticas del adversario<th>Defensa del SOC
	<tr><td>Abrir un canal para la manipulación de los objetivos:<br /><ul><li>Abrir un canal de comunicación b idireccional a la infraestructura CNC<li>Los canales CNC más comunes son a través de protocolos web, DNS y de correo electrónico<li>La infraestructura CNC puede ser propiedad del adversario o de otra red víctima</ul><td>Última oportunidad para bloquear la operación:<br /><ul><li>Investigar posibles nuevas infraestructuras CNC<li>Descubrir la infraestructura CNC a través del análisis de malware<li>Aísle el tráfico DNS a los servidores DNS sospechosos, especialmente DNS dinámico<li>Evite el impacto bloqueando o deshabilitando el canal CNC<li>Consolidar el número de puntos de presencia de Internet<li>Personalizar las reglas de bloqueo de los protocolos CNC en los servidores proxy web</ul>
</table>

## Acciones sobre objetivos
El paso final de la Cadena de Eliminación Cibernética es cuando el actor de amenaza logra su objetivo original. Este puede ser el robo de datos, la ejecución de un ataque de DDoS, o el uso de la red atacada para crear y enviar correo electrónico no deseado o mina de Bitcoin. Llegado este momento, el actor de amenaza está profundamente arraigado en los sistemas de la organización, ocultando sus movimientos y cubriendo sus rastros. Es extremadamente difícil eliminar el actor de amenaza de la red.

La tabla resume algunas de las tácticas y defensas que se utilizan durante el paso de acciones en objetivos.

<table>
	<tr><th>Tácticas del adversario<th>Defensa del SOC
	<tr><td>Coseche las recompensas de un ataque existoso:<br /><ul><li>Recopilar credenciales de usuario<li>EScalada de privilegios<li>Reconocimiento interno<li>Movimiento lateral  a través del medio ambiente<li>Recopilar y filtrar datos<li>Destruir sistemas<li>Sobrescribir, modificar o corromper datos</ul><td>Detectar mediante el uso de pruebas forenses:<br /><ul><li>Establecer manual de respuesta a incidentes<li>Detectar la filtración de datos, el movimiento lateral y el uso no autorizado de credenciales<li>Respuesta inmediata del analista para todas las alertas<li>Análisis forenses de puntos finales para una clasificación rápida<li>Capturas de paquetes para recreación de la actividad<li>Realizar evaluación de daños</ul>
</table>

# El modelo de diamante del análisis de la cadena de eliminación
## Descripción general del modelo de diamante
El Modelo de Diamante del Análisis de Intrusión está compuesto de cuatro partes, como se muestra en la figura. El modelo representa un incidente o evento de seguridad. En el Modelo de Diamante, un evento es una actividad de tiempo limitado que está restringido a un paso específico donde el adversario utiliza la capacidad sobre la infraestructura para atacar una víctima para lograr un resultado específico.

Las cuatro características principales de un evento de intrusión son el adversario, la capacidad, la infraestructura y la víctima:
* __Adversario__. Estas son las partes responsables de la intrusión.
* __Capacidad__. Esta es una herramienta o técnica que utiliza el adversario para atacar a la víctima
* __Infraestructura__. Esta es la ruta o rutas de red que los adversarios utilizan para establecer y mantener el comando y control de sus capacidades.
* __Víctima__. Este es el objetivo del ataque. Sin embargo, la víctima podría ser el objetivo inicial y, luego, el atacante puede utilizarla como parte de la infraestructura para iniciar otros ataques.

El adversario usa capacidades sobre la infraestructura para atacar a la víctima. El modelo puede interpretarse como diciendo: «El adversario usa la infraestructura para conectarse con la víctima. El adversario desarrolla la capacidad de explotar a la víctima». Por ejemplo, un adversario podría usar una funcionalidad como el malware sobre la infraestructura de correo electrónico para aprovecharse de la víctima.

Las metacaracterísticas amplían un poco el modelo para incluir los siguientes elementos importantes:

* __Marca de hora__. Esto indica la hora de inicio y fin de un evento y es una parte integral de la agrupación de actividad maliciosa.
* __Fase__. Este concepto es análogo al de los pasos en la Cadena de Eliminación Cibernética; la actividad maliciosa incluye dos o más pasos ejecutados seguidamente para lograr el resultado deseado.
* __Resultado__. Esto definir lo que el adversario obtuvo en el evento. Los resultados pueden documentarse como uno o más de los siguientes: confidencialidad afectada, integridad afectada y disponibilidad afectada.
* __Dirección__. Esto indica la dirección del evento en el Modelo de Diamante. Algunas direcciones son adversario a infraestructura, infraestructura a víctima, víctima a infraestructura e infraestructura a adversario.
* __Metodología__. Esto se utiliza para clasificar el tipo general del evento, como exploración de puertos, suplantación de identidad, ataque de entrega de contenido, saturación SYN, etc.
* __Recursos__. Existen uno o más recursos externos utilizados por el adversario para el evento de intrusión, como software, conocimiento del adversario, información (por ejemplo, nombre de usuario/contraseñas) y activos para llevar a cabo el ataque (hardware, fondos, instalaciones, acceso a la red).

<div style="width: 50%; padding-left: 20%;">
	<img src="./img/modelo-diamante.png" />
</div>

## Cómo desplazarse por el modelo de diamante
Como analistas especializados en ciberseguridad, es posible que se les pida que utilicen el Modelo de Diamante del Análisis de Intrusiónes para diagramar una serie de eventos de intrusión. El Modelo de Diamante es ideal para ilustrar de qué manera el atacante pasa de un evento al siguiente.

Por ejemplo, en la figura, un empleado informa que su computadora se comporta de manera extraña. El técnico de seguridad realiza un análisis del host que indica que la computadora está infectada con malware. Un análisis del malware revela que el malware contiene una lista de nombres de dominio de CnC. Estos nombres de dominio se resuelven en una lista de direcciones IP. Luego, estas direcciones IP se utilizan para identificar al adversario, así como para investigar los registros a fin de determinar si otras víctimas de la organización utilizan el canal de CnC.

Caracterización del modelo de diamante de un exploit.

<div style="width: 50%; padding-left: 20%;">
	<img src="./img/modelo-diamante-1.png" />
</div>

## El modelo de diamante y la cadena de eliminación cibernética
Ejemplos de hilos de actividad.

Los adversarios no ejecutan un solo evento. En cambio, los eventos se entretejen en una cadena en la que cada evento debe completarse con éxito antes del siguiente. Esta serie de eventos puede asignarse a la Cadena de Eliminación Cibernética analizada previamente en el capítulo.

En el siguiente ejemplo (que se muestra en la figura), se ejemplifica el proceso integral de un adversario a medida que atraviesa verticalmente la Cadena de Eliminación Cibernética, utiliza un host afectado para desplazarse horizontalmente hacia otra víctima, y empieza otro subproceso de la actividad:

1. El adversario realiza una búsqueda web sobre la empresa víctima Gadgets, Inc. y recibe, como parte de los resultados, el nombre de dominio gadgets.com.
2. El adversario utiliza gadgets.com, el dominio que acaba de detectar, para realizar una nueva búsqueda de "administrador de red gadgets.com". Así, descubre publicaciones de usuarios en los foros alegando que son administradores de red de gadgets.com. Los perfiles de usuario revelan sus direcciones de correo electrónico.
3. El adversario envía correos electrónicos de suplantación de identidad con un troyano adjunto a los administradores de red de gadgets.com.
4. Un administrador de red (NA1) de gadgets.com abre el archivo adjunto malicioso. Esto ejecuta el ataque incluido y permite seguir con la ejecución de código.
5. El host atacado de NA1 envía un mensaje HTTP Post a una dirección IP para registrarla con un controlador de CnC. El host atacado de NA1 recibe una respuesta HTTP.
6. Mediante ingeniería inversa, se revela que el malware tiene direcciones IP adicionales configuradas que actúan como una copia de respaldo si el primer controlador no responde.
7. Mediante un mensaje de respuesta HTTP de CnC enviado al host de NA1, el malware comienza a actuar como un web proxy para nuevas conexiones de TCP.
8. Mediante la información del proxy ejecutado en el host de NA1, el adversario realiza una búsqueda web con las palabras "la investigación más importante de todos los tiempos" y encuentra a la víctima 2, Interesting Research Inc.
9. El adversario consulta la lista de contactos de correo electrónico de NA1 para buscar contactos de Interesting Research, Inc. y descubre el contacto del Director principal de investigaciones de Interesting Research, Inc.
10. El Director principal de investigaciones de Interesting Research, Inc. recibe un correo electrónico de phishing dirigido desde la dirección de correo electrónico de NA1 de Gadget, Inc. enviado desde el host de NA1 con la misma carga útil del evento 3.

El adversario tiene ahora dos víctimas afectadas desde las que puede iniciar ataques adicionales. Por ejemplo, el adversario podría analizar la lista de contactos del Director Principal de Investigaciones en busca de posibles víctimas adicionales. El adversario también podría configurar otro proxy para exfiltrar todos los archivos del Director Principal de Investigaciones.

__Nota__: Este ejemplo es una adaptación del ejemplo del Departamento de Defensa de los Estados Unidos de la publicación "El Análisis de Intrusiones del Modelo de Diamante".

<div style="width: 50%; padding-left: 20%;">
	<img src="./img/hilos-actividad.png" />
</div>

## Práctica de laboratorio - Análisis del ataque
* <a href="./notes/lab_analisis_ataque.md" target="_blank">Análisis del ataque</a>

# Respuesta a incidentes
## Establecer una capacidad de respuesta a incidentes
La respuesta a incidentes implica los métodos, políticas y procedimientos que utiliza una organización para responder a un ataque cibernético. Los objetivos de la respuesta ante incidentes son limitar el impacto del ataque, evaluar los daños causados e implementar procedimientos de recuperación. Debido a la posible pérdida a gran escala de bienes e ingresos que pueden causar los ciberataques, es esencial que las organizaciones creen y mantengan planes detallados de respuesta a incidentes y designen al personal responsable de ejecutar todos los aspectos de ese plan.

Las recomendaciones del NIST (U.S. National Institute of Standards and Technology ) para la respuesta ante los incidentes se detallan en su Publicación especial 800-61 (Revisión 2) titulada "Guía de manejo de incidentes de seguridad informática" que se muestra en la figura.

Nota: Aunque este capítulo resume gran parte del contenido en el estándar NIST 800-61r2, debería familiarizarse con la publicación entera para cubir todos los temas del examen Entendiendo Operaciones Fundamentales Ciberseguridad de Cisco (Understanding Cisco Cybersecurity Operations Fundamentals).

<div style="width: 50%; padding-left: 20%;">
	<img src="./img/computer-incident-reporting-guide.png" />
</div>

El estándar 800-612r del NIST proporciona pautas para el manejo de incidentes, especialmente para analizar datos relacionados con el incidente y determinar la respuesta adecuada para cada incidente. Es posible respetar las pautas independientemente de las plataformas de hardware, los sistemas operativos, los protocolos o las aplicaciones que se utilicen.

El primer paso para una organización es establecer una capacidad de respuesta ante los incidentes de seguridad informática (CSIRC, computer security incident response capability). NIST recomienda crear políticas, planes y procedimientos para establecer y mantener un CSIRC.
* __Elementos de la política__. Una política de respuesta ante los incidentes detalla cómo deben manejarse los incidentes de acuerdo con la misión, el tamaño y la función de la organización. La política debe revisarse periódicamente a fin de modificarla para que cumpla con los objetivos de la hoja de ruta que se haya trazado. Entre los elementos de política figuran los siguientes:
	* Declaración del compromiso de la gerencia.
	* Propósito y objetivos de la política.
	* Alcance de la política.
	* Definición de incidentes de seguridad informática y términos relacionados.
	* Estructura organizacional y definición de roles, responsabilidades y niveles de autoridad.
	* Calificaciones de priorización o gravedad de incidentes.
	* Acciones de desempeño.
	* Formularios de informes y contacto.
* __Elementos del plan__. Un buen plan de respuesta ante los incidentes ayuda a minimizar el daño causado por un incidente. También ayuda a mejorar el programa de respuesta ante los incidentes en general, ajustándolo según las lecciones aprendidas. El plan debe garantizar que cada parte implicada en la respuesta ante un incidente comprenda claramente lo qué hará y lo qué harán los demás. Los elementos del plan son los siguientes:
	* Misión.
	* Estrategias y metas.
	* Aprobación de la cúpula gerencial.
	* Enfoque organizativo para la respuesta ante los incidentes.
	* Cómo se comunicará el equipo de respuesta ante los incidentes con el resto de la organización y con otras organizaciones.
	* Métricas para medir la funcionalidad de respuesta ante los incidentes.
	* Cómo encaja el programa en la organización general.
* __Elementos del procedimiento__. Los procedimientos que se siguen durante una respuesta ante un incidente deben respetar el plan de respuesta ante los incidentes. Los elementos de procedimientos son los siguientes:
	* Procesos técnicos.
	* Usar técnicas.
	* Rellenar formularios.
	* Siguiendo listas de comprobación.

 	Estos son los procesos comunes operativos estándar (SOP) Estos SOP deben ser detallados para tener en mente la misión y los objetivos de la organización cuando se los sigue. Los SOP minimizan los errores que podría causar el personal cuando está bajo presión mientras participa en el manejo de incidentes. Es importante compartir y poner en práctica estos procedimientos, asegurándose de que sean útiles, precisos y adecuados.

## Partes interesadas en la respuesta a incidentes
Otros grupos e individuos dentro de la organización también pueden estar involucrados en el manejo de incidentes. Es importante asegurarse de que cooperen antes de que ocurra un incidente. Sus conocimientos y habilidades pueden ayudar al Equipo de Respuesta a Incidentes de Seguridad Informática (CSIRT) a manejar el incidente rápida y correctamente. Estas son algunas de las partes interesadas que pueden estar involucradas en el manejo de un incidente de seguridad:
* __Gerencia__. Los gerentes crean las políticas que todos deben respetar. También diseñan el presupuesto y están a cargo de dotar de personal a todos los departamentos. La Gerencia debe coordinar la respuesta ante los incidentes con otras partes interesadas y minimizar el daño causado por el incidente.
* __Protección de la información__. Es posible que sea necesario convocar a este grupo para cambiar elementos, como las reglas de firewall, durante algunas etapas de la administración de incidentes como contención o recuperación.
* __Soporte de TI__. Este es el grupo que trabaja con la tecnología en la organización y la comprende al máximo. Dado que el conocimiento del Soporte de TI es muy amplio, es más probable que sean ellos quienes ejecuten las medidas correctas para minimizar la efectividad del ataque o proteger adecuadamente la evidencia.
* __Departamento legal__. Es una mejor práctica tener un departamento de asuntos legales que revise políticas, planes y procedimientos relativos a los incidentes para asegurarse de que no violen pautas locales o federales. Además, si cualquier incidente tiene consecuencias jurídicas, un experto legal tendrá que involucrarse. Esto podría incluir acusaciones, recolección de evidencia o demandas.
* __Relaciones públicas y con los medios__. Hay momentos en los que se debe informar sobre un incidente a los medios de comunicación y al público, como cuando se pone en riesgo información personal durante un incidente.
* __Recursos humanos__. Es posible que el departamento de Recursos Humanos necesite implementar medidas disciplinarias si el incidente lo causa un empleado.
* __Planificadores de continuidad del negocio__. Los incidentes de seguridad pueden alterar la continuidad de los negocios de una organización. Es importante que los responsables de la planificación de continuidad de los negocios conozcan los incidentes de seguridad y su impacto en la totalidad de la organización. Esto les permitirá realizar cambios en los planes y las evaluaciones de riesgo.
* __Administración de las instalaciones y la seguridad física__. Cuando ocurre un incidente de seguridad debido a un ataque físico, como la infiltración (tailgating) o mirar por encima del hombro, es posible que sea necesario informar e involucrar a estos equipos. También es su responsabilidad proteger las instalaciones que contienen evidencias de una investigación.

### La certificación del modelo de madurez de ciberseguridad
El marco de certificación del modelo de madurez de ciberseguridad (CMMC) fue creado para evaluar la capacidad de las organizaciones que desempeñan funciones para el Departamento de Defensa de los Estados Unidos (DoD) para proteger la cadena de suministro militar de interrupciones o pérdidas debidas a incidentes de ciberseguridad. Las brechas de seguridad relacionadas con la información del Departamento de Defensa (DoD) indicaron que los estándares del NIST no eran suficientes para mitigar el creciente y cambiante panorama de amenazas, especialmente de los actores de amenazas de los estados-nación. Para que las empresas reciban contratos del DoD, dichas empresas deben estar certificadas. La certificación consta de cinco niveles, con diferentes niveles requeridos dependiendo del grado de seguridad requerido por el proyecto.

El CMMC especifica 17 dominios, cada uno de los cuales tiene un número variable de capacidades asociadas a él. La organización se califica por el nivel de madurez que se ha alcanzado para cada uno de los dominios. Uno de los dominios se refiere a la respuesta a incidentes. Las capacidades asociadas con el dominio de respuesta a incidentes son las siguientes:
* Planes de respuesta a incidentes
* Detectar e informar de eventos
* Desarrollar e implementar una respuesta a un incidente declarado
* Realizar revisiones posteriores a incidentes
* Prueba de respuesta a incidentes

La CMMC certifica las organizaciones por nivel. Para la mayoría de los dominios, hay cinco niveles, sin embargo, para la respuesta a incidentes, sólo hay cuatro. Cuanto mayor sea el nivel certificado, más madura será la capacidad de ciberseguridad de la organización. A continuación se muestra un resumen de los niveles de madurez del dominio de respuesta a la incidencia.
* __Nivel 2__. Establecer un plan de respuesta a incidentes que siga el proceso NIST. Detecte, informe y priorice eventos. Responder a los eventos siguiendo procedimientos predefinidos. Analizar la causa de los incidentes para mitigar problemas futuros.
* __Nivel 3__. Documentar e informar a las partes interesadas que hayan sido identificadas en el plan de respuesta a incidentes. Pruebar la capacidad de respuesta a incidentes de la organización.
* __Nivel 4__. Utilizar el conocimiento de las tácticas, técnicas y procedimientos del atacante (TPT) para refinar la planificación y ejecución de la respuesta a incidentes. Establezca un centro de operaciones de seguridad (SOC) que facilite una capacidad de respuesta 24/7.
* __Nivel 5__. Utilizar técnicas de recopilación de datos forenses informáticos aceptadas y sistemáticas, incluido el manejo y almacenamiento seguros de datos forenses. Desarrollar y utilizar respuestas manuales y automatizadas en tiempo real a posibles incidentes que sigan patrones conocidos.

<div style="width: 50%; padding-left: 20%;">
	<img src="./img/cybersecurity-maturity-model-certification.png" />
</div>

## Ciclo de vida de respuesta a incidentes del NIST
NIST definir cuatro pasos en el ciclo de vida del proceso de respuesta ante los incidentes, como se ve en la figura.
* __Preparación__. Los miembros del CSIRT reciben capacitación sobre cómo responder ante un incidente. Los miembros del CSIRT deben desarrollar continuamente su conocimiento de las amenazas emergentes.
* __Detrección y análisis__. Mediante el monitoreo continuo, el CSIRT identifica, analiza y valida rápidamente un incidente.
* __Contención, erradicación y recuperación__. El CSIRT implementa procedimientos para contener la amenaza, erradicar el impacto en los activos de la organización y utilizar copias de respaldo para restaurar datos y software. Es posible que, durante esta fase, se regrese a la detección y el análisis para obtener más información o para ampliar el alcance de la investigación.
* __Actividades posteriores al incidente__. Luego, el CSIRT documenta cómo se manejó el incidente, recomienda cambios para respuestas futuras y especifica cómo evitar que vuelva a suceder.

El ciclo de vida de respuesta a incidentes pretende ser un proceso de aprendizaje reafirmante en el que cada incidente alimente el proceso para el manejo de futuros incidentes. Cada una de estas fases se analiza más detalladamente en este tema.

<div style="width: 50%; padding-left: 20%;">
	<img src="./img/ciclo-vida-repuesta-incidentes.png" />
</div>

## Preparación
La fase de preparación tiene lugar cuando se crea el CSIRT y se lo capacita. Esta fase ocurre cuando se adquieren e implementan las herramientas y los activos que serán necesarios para que el equipo investigue los incidentes. La siguiente lista tiene ejemplos de acciones que también tienen lugar durante la fase de preparación:
* Los procesos organizativos se crean para abordar la comunicación entre las personas y el equipo de respuesta. Esto incluye elementos como la información de contacto para las partes interesadas, otros CSIRT y la autoridad encargada del orden público, un sistema de seguimiento de problemas, smartphones, software de cifrado, etc.
* Se crean instalaciones para alojar al equipo de respuesta y al SOC.
* Se adquiere el hardware y software necesario para el análisis de incidentes y la mitigación. Esto puede incluir software de informática forense, computadoras de repuesto, servidores y dispositivos de red, dispositivos de respaldo, analizadores de paquetes y analizadores de protocolos.
* Las evaluaciones de riesgos se utilizan para implementar controles que limitarán la cantidad de incidentes.
* La validación de la implementación de hardware y software de seguridad se realiza en dispositivos de usuarios finales, servidores y dispositivos de red.
* Se desarrollan materiales de capacitación para usuarios con el fin de concientizarlos sobre la seguridad.

Es posible que hagan falta recursos de análisis de incidentes adicionales. Ejemplos de estos recursos son una lista de activos críticos, diagramas de red, listas de puertos, hash de archivos esenciales y lecturas de los valores de referencia de la actividad de la red y el sistema. El software de mitigación también es un elemento importante al prepararse para manejar un incidente de seguridad. Es posible que se necesite una imagen de un sistema operativo limpio y archivos de instalación de aplicaciones para recuperar una computadora de un incidente.

A menudo, el CSIRT suele tener preparado un kit de emergencia. Se trata de una caja portátil con muchos de los elementos mencionados antes para ayudar a establecer una respuesta rápida. Algunos de estos elementos pueden ser una computadora portátil con el software apropiado instalado, medios de respaldo, y cualquier otro hardware, software o información para ayudar en la investigación. Es importante inspeccionar el kit de emergencia periódicamente para instalar actualizaciones y asegurarse de que todos los elementos necesarios están disponibles y listos para usar. También resulta útil implementar el kit de emergencia con el CSIRT para asegurarse de que los miembros del equipo sepan cómo utilizar correctamente el contenido.

<div style="width: 50%; padding-left: 20%;">
	<img src="./img/fase-preparacion.png" />
</div>

## Detección y análisis

<div style="width: 50%; padding-left: 20%;">
	<img src="./img/fase-deteccion-analisis.png" />
</div>

Dado que hay muchas maneras diferentes en las que puede ocurrir un incidente de seguridad, es imposible crear instrucciones que abarquen completamente cada paso para manejarlos. Los distintos tipos de incidentes requieren respuestas diferentes.
* __Vectores de ataque__. Una organización debe estar preparada para manejar cualquier incidente, pero debe centrarse en los tipos más comunes de incidentes para poder resolverlos con rapidez. Estos son algunos de los tipos de vectores de ataque más comunes:
	* __Web__. Cualquier ataque que se inicia desde un sitio web o una aplicación alojada en un sitio web.
	* __Correo electrónico__. Cualquier ataque que se inicia desde un correo electrónico o archivo adjunto de correo electrónico.
	* __Pérdida o robo__. Cualquier equipo que use la organización, como una computadora portátil o de escritorio, o un smartphone, pueden proporcionar la información necesaria para que alguien inicie un ataque.
	* __Suplantación__. Cuando se sustituye a alguien o algo con intenciones maliciosas.
	* __Desgaste__. Cualquier ataque que utiliza la fuerza bruta para atacar dispositivos, redes o servicios.
	* __Medios__. Cualquier ataque que se inicie con medios de almacenamiento externos o extraíbles.
* __Detección__. Algunos incidentes son fáciles de detectar, mientras que otros pueden pasar inadvertidos durante meses. Es posible que la detección de incidentes de seguridad sea la fase más difícil en el proceso de respuesta ante los incidentes. Los incidentes se detectan con muchos métodos diferentes y no todos son muy detallados ni claros. Hay métodos automatizados de detección, como el software antivirus o un IDS. También hay métodos manuales mediante informes de usuario.

	Es importante determinar con precisión el tipo de incidente y la magnitud de sus efectos. Las señales que indican un incidente se clasifican en dos categorías:
	* __Precursor__. Es una señal que indica que un incidente podría ocurrir en el futuro. Cuando se detectan los precursores, un ataque puede evitarse modificando las medidas de seguridad para abordar específicamente el tipo de ataque detectado. Ejemplos de precursores son las entradas del registro que muestran una respuesta a un análisis de puertos, o una vulnerabilidad recién descubierta en el servidor de web de la organización.
	* __Indicador__. Es una señal que indica que un incidente podría haber ocurrido o está ocurriendo actualmente. Algunos ejemplos de indicadores son un host que se infectó con malware, varios inicios de sesión incorrectos de origen desconocido, o una alerta de IDS.
* __Análisis__. El análisis de incidentes es difícil porque no todos los indicadores son exactos. En un mundo perfecto, cada indicador debería analizarse para saber si es exacto. Esto es casi imposible debido a la cantidad y variedad de incidentes registrados e informados. El uso de algoritmos complejos y aprendizaje mecanizado ayuda, en ocasiones, a determinar la validez de los incidentes de seguridad. Esto es más frecuente en organizaciones grandes que sufren miles o incluso millones de incidentes a diario. Un método que puede utilizarse es la creación de perfiles de la red y el sistema. La creación de perfiles consiste en medir las características de la actividad prevista en dispositivos y sistemas de redes para que los cambios se puedan identificar más fácilmente.

	Cuando un indicador de cambio es exacto, no significa necesariamente que se haya producido un incidente de seguridad. Algunos indicadores tienen lugar por otros motivos además de la seguridad. Por ejemplo, un servidor que deja de funcionar continuamente puede tener una memoria RAM deficiente en lugar de estar sufriendo un ataque de desbordamiento del búfer. Para estar seguros, incluso los síntomas ambiguos o contradictorios deben analizarse para determinar si ha ocurrido un incidente de seguridad real. El CSIRT debe reaccionar rápidamente para validar y analizar los incidentes. Esto se realiza siguiendo un proceso predefinido y documentando cada paso.
* __Definición del alcance__. Cuando el CSIRT cree que se ha producido un incidente, debe realizar inmediatamente un análisis inicial para determinar el alcance de los hechos, por ejemplo, qué redes, sistemas o aplicaciones se vieron afectados, qué o quién originó el incidente y cómo está ocurriendo. Esta actividad de determinación del alcance debe proporcionar información suficiente para que el equipo priorice las actividades posteriores, como la contención del incidente y un análisis más profundo de los efectos del incidente.
* __Notificación de incidentes__. Cuando se analiza y prioriza un incidente, el equipo de respuesta ante los incidentes debe notificar a las personas interesadas y partes externas para que todos los que necesitan involucrarse desempeñen sus funciones. Algunos ejemplos de las personas a las que debe notificarse normalmente son los siguientes:
	* Director General de Información (CIO).
	* Director de seguridad informática.
	* Director local de seguridad informática.
	* Otros equipos de respuesta ante los incidentes dentro de la organización.
	* Equipos externos de respuesta ante los incidentes (si corresponde).
	* Propietario del sistema.
	* Recursos Humanos (para casos que involucran a empleados, como el acoso por correo electrónico).
	* Relaciones públicas (para los incidentes que pueden generar publicidad).
	* Departamento de asuntos legales (para los incidentes que podría tener ramificaciones legales).
	* US-CERT (obligatorio en el caso de los organismos federales y los sistemas utilizados en nombre del gobierno federal).
	* Autoridad encargada del orden público (si corresponde).

## Contención, erradicación y recuperación

<div style="width: 50%; padding-left: 20%;">
	<img src="./img/fase-contencion-erradicacion-recuperacion.png" />
</div>

Después de detectar un incidente de seguridad y realizar análisis suficientes para determinar que es válido, se lo debe contener a fin de decidir qué hacer al respecto. Es necesario definir estrategias y procedimientos para la contención de incidentes antes de que un incidente ocurra e implementarlas antes de que el daño se propague.
* __Estrategia de contención__. Para cada tipo de incidente, se debe crear e imponer una estrategia de contención. Estas son algunas condiciones para determinar el tipo de estrategia que se debe crear para cada tipo de incidente:
	* ¿Cuánto tiempo se demorará en implementar y completar una solución?
	* ¿Cuánto tiempo y cuántos recursos se necesitarán para implementar la estrategia?
	* ¿Cuál es el proceso para preservar la evidencia?
	* ¿Se puede redirigir a un atacante hacia un sandbox para que el CSIRT pueda documentar de manera segura la metodología del atacante?
	* ¿Cuál será el impacto en la disponibilidad de los servicios?
	* ¿Cuál es la magnitud del daño en los recursos o activos?
	* ¿Cuán efectiva es la estrategia?

	Durante la contención, se pueden producir más daños. Por ejemplo, no siempre es recomendable desconectar el host atacado de la red. El proceso malicioso podría avisar de esta desconexión al controlador de CnC y desencadenar un borrado de datos o la encriptación del objetivo. Aquí es donde la experiencia y los conocimientos pueden ayudar a contener un incidente que no se contemple en el alcance de la estrategia de contención.
* __Evidencia__. Durante un incidente, debe recopilarse evidencia para resolverlo. La evidencia también es importante para la posterior investigación por parte de las autoridades. Es fundamental disponer de documentación clara y concisa relativa a la preservación de la evidencia. Para que la evidencia sea admisible en un tribunal, su recolección debe ajustarse a reglas específicas. Después de recopilar la evidencia, se debe explicar correctamente. A esto se lo conoce como cadena de custodia. Estos son algunos de los elementos más importantes que deben registrarse cuando se documenta evidencia utilizada en la cadena de custodia:
	* Ubicación de la recuperación y el almacenamiento de toda la evidencia.
	* Los criterios de identificación de la evidencia, como el número de serie, la dirección MAC, el nombre de host o la dirección IP.
	* Información de identificación para todas las personas que participaron en la recopilación o manipulación de la evidencia.
	* Hora y fecha en que se recopiló la evidencia y cada vez que se manipuló.

	Es fundamental capacitar a cualquier persona involucrada en el manejo de evidencia sobre cómo protegerla adecuadamente.
* __Identificación del atacante__. La identificación de los atacantes no es tan importante como contener y erradicar el ataque, y recuperar los hosts y servicios. Sin embargo, identificar a los atacantes minimizará el impacto en los activos y servicios esenciales de la empresa. Estas son algunas de las acciones más importantes que pueden realizarse para intentar identificar un host atacante durante un incidente de seguridad:
	* Utilizar bases de datos de incidentes para investigar actividades relacionadas. Esta base de datos puede ser interna o estar ubicada en organizaciones que recogen datos de otras organizaciones y los reúnen en bases de datos de incidentes, como la base de datos de la comunidad de VERIS.
	* Validar la dirección IP del atacante para determinar si es viable. El host puede responder a una solicitud de conexión o no hacerlo. Esto puede ocurrir porque el host se configuró para ignorar las solicitudes o porque la dirección ya se reasignó a otro host.
	* Utilizar un motor de búsqueda en Internet para obtener más información sobre el ataque. Es posible que otra organización o individuo haya publicado información sobre un ataque desde la dirección IP de origen identificada.
	* Monitorear los canales de comunicación que algunos atacantes usan, como IRC. Dado que los usuarios pueden ocultarse en el anonimato en los canales de IRC, es posible que hablen sobre los ataques en estos canales. A menudo, la información recopilada gracias a este tipo de monitoreo es engañosa y debe tratarse como indicios, no hechos.
* __Erradicación, recuperación y corrección__. Después de la contención, el primer paso para la erradicación consiste en identificar todos los hosts que necesitan correcciones. Se deben eliminar todos los efectos del incidente de seguridad. Esto incluye las infecciones de malware y las cuentas de usuario atacadas. También se deben aplicar correcciones o parches en todas las vulnerabilidades que el atacante aprovechó, de modo que el incidente no se repita.

	Para recuperar los hosts, deben usarse copias de respaldo limpias y recientes, o se deben reconstruir los hosts con medios de instalación si no hay copias de seguridad disponibles o también se vieron afectadas. También, deben implementarse completamente actualizaciones y parches en los sistemas operativos y el software instalado en todos los hosts. Deben modificarse todas las contraseñas de hosts y contraseñas de sistemas esenciales según la política de seguridad de las contraseñas. Este puede ser un buen momento para validar y actualizar la seguridad de la red, las estrategias de respaldo y las políticas de seguridad. Los atacantes suelen repetir los ataques en los sistemas o utilizan un ataque similar dirigido a recursos adicionales; por lo tanto, es necesario prevenir esto lo mejor posible. Hace falta concentrarse en lo que pueda repararse rápidamente y dar prioridad a las operaciones y los sistemas esenciales.

## Actividades posteriores al incidente

<div style="width: 50%; padding-left: 20%;">
	<img src="./img/fase-post-incidente.png" />
</div>

Después de que las actividades de respuesta ante los incidentes erradican las amenazas y la organización comienza a recuperarse de los efectos del ataque, es importante mirar hacia atrás y reunirse periódicamente con todas las personas involucradas para analizar los acontecimientos que tuvieron lugar y las acciones de todos los individuos durante el manejo del incidente. Esto proporcionará una plataforma para aprender qué se hizo bien, qué se hizo mal, qué se podría cambiar y qué se debe mejorar.

Después de manejar un incidente importante, la organización debe llevar a cabo una reunión de "lección aprendida" para examinar la eficacia del proceso de manejo de incidentes e identificar el fortalecimiento que hace falta en los controles y las prácticas vigentes de seguridad. Algunas buenas preguntas para formularse durante la reunión son las siguientes:
* ¿Exactamente qué pasó y cuándo?
* ¿Con qué eficacia trabajaron el personal y la dirección durante el manejo del incidente?
* ¿Se respetaron los procedimientos documentados? ¿Fueron los adecuados?
* ¿Qué información se necesitó antes?
* ¿Se tomaron medidas o acciones que podrían haber inhibido la recuperación?
* ¿Qué harían de manera diferente el personal y la dirección la próxima vez que ocurra un incidente similar?
* ¿Cómo se podría mejorar el intercambio de información con otras organizaciones?
* ¿Qué medidas correctivas pueden evitar incidentes similares en el futuro?
* ¿Qué precursores o indicadores deben tenerse en cuenta para detectar incidentes similares en el futuro?
* ¿Qué otras herramientas o recursos se necesitan para detectar, analizar y mitigar incidentes futuros?

## Recolección y retención de datos de incidentes
Gracias a las reuniones de "lecciones aprendidas", los datos recopilados pueden utilizarse para determinar el costo de un incidente por razones presupuestarias, así como determinar la eficacia del CSIRT e identificar las posibles debilidades de seguridad en todo el sistema. Los datos recopilados deben ser procesables. Solo deben recopilarse datos que puedan utilizarse para definir y refinar el proceso de manejo de incidentes.

Una mayor cantidad de incidentes manejados puede demostrar que algo en la metodología de respuesta ante los incidentes no está funcionando correctamente y debería mejorarse. También podría demostrar incompetencia de parte del CSIRT. Una menor cantidad de incidentes puede demostrar que la seguridad de red y hosts ha mejorado. También podría demostrar una falta de detección de incidentes. Los recuentos individuales de cada tipo de incidente pueden resultar efectivos para mostrar las fortalezas y debilidades del CSIRT y de las medidas de seguridad implementadas. Estas subcategorías pueden ayudar a definir dónde residen las debilidades, en lugar de indicar solamente que existen.

El tiempo de cada incidente proporciona información sobre la cantidad total de mano de obra utilizada y el tiempo total que tomó cada fase del proceso de respuesta ante los incidentes. El tiempo que demoró la primera respuesta también es importante, así como cuánto tardó la notificación del incidente y su derivación fuera de la organización si fuera necesario.

Es importante realizar una evaluación objetiva de cada incidente. La respuesta ante un incidente resuelto puede analizarse para determinar su eficacia. La publicación especial 800-61 de NIST proporciona los siguientes ejemplos de actividades que se realizan durante la evaluación objetiva de un incidente:
* Revisar los registros, formularios, informes y otra documentación del incidente para ver si se respetan las políticas y los procedimientos de respuesta ante los incidentes.
* Identificar qué precursores e indicadores del incidente se registraron para determinar la eficacia del registro y la identificación del incidente.
* Determinar si el incidente causó daños antes de detectarlo.
* Determinar si se identificó la causa real del incidente e identificar el vector de ataque, las vulnerabilidades aprovechadas y las características de los sistemas, las redes y las aplicaciones que sufrieron el ataque.
* Determinar si el incidente ya ocurrió antes.
* Calcular el daño monetario aproximado del incidente (por ejemplo, información y procesos empresariales esenciales afectados por el incidente).
* Medir la diferencia entre la evaluación inicial del impacto inicial y la evaluación final del impacto.
* Identificar qué medidas podrían haber evitado el incidente (si hubiera).
* Valorar subjetivamente cada incidente exige que los miembros del equipo de respuesta ante los incidentes evalúen su propio desempeño, así como el de otros miembros del equipo y de todo el equipo. Otra valiosa fuente de información es el propietario de un recurso atacado, ya que este puede determinar si cree que el incidente se manejó con eficacia y si el resultado fue satisfactorio.

Cada organización debe tener desarrollada una política que detalle cuánto tiempo debe conservarse la evidencia de un incidente. A menudo, la evidencia se conserva durante muchos meses o años después de que ocurre el incidente. En algunos casos, las normas de cumplimiento pueden exigir el período de retención. Estos son algunos de los factores que determinan la retención de evidencia:
* __Procesamiento__. Cuando se procesa judicialmente a un atacante por un incidente de seguridad, la evidencia debe conservarse hasta después de finalizar con todas las acciones legales. Esto puede ser durante varios meses o muchos años. En acciones judiciales, no se debe pasar por alto ni subestimar ningún tipo de evidencia. La política de una organización podría indicar que cualquier evidencia relativa a un incidente que haya derivado en acciones legales nunca debe eliminarse ni destruirse.
* __Tipo de datos__. Una organización puede especificar qué tipos específicos de datos deben mantenerse durante un período determinado. Elementos como correo electrónico o texto deben conservarse solo durante 90 días. Los datos más importantes, como los que se utilizan en la respuesta ante un incidente (que no haya derivado en acciones legales), deben conservarse durante tres años o más.
* __Costo__. Si hay mucho hardware y muchos medios de almacenamiento que deben almacenarse durante un tiempo prolongado, eso puede ser costoso. Es necesario recordar que, a medida que la tecnología cambia, deben almacenarse también los dispositivos funcionales que sean compatibles con hardware y medios de almacenamiento obsoletos.

## Requisitos de informes e intercambio de información
El equipo legal debe consultar las regulaciones gubernamentales para determinar con exactitud la responsabilidad de la organización de informar el incidente. Además, los directivos necesitarán determinar qué comunicación adicional es necesaria con otras partes interesadas, como clientes, proveedores, partners, etc.

Más allá de los requisitos legales y las consideraciones sobre las partes interesadas, el NIST recomienda que una organización trabaje en conjunto con otras para compartir información sobre incidentes. Por ejemplo, la organización podría registrar el incidente en la base de datos de la comunidad de VERIS.

Las recomendaciones fundamentales del NIST para el intercambio de información son las siguientes:
* Planificar la coordinación de incidentes con participantes externos antes de que ocurran incidentes.
* Consultar con el departamento legal antes de iniciar cualquier tarea de coordinación.
* Intercambiar información sobre el incidente durante todo el ciclo de vida de respuesta ante los incidentes.
* Intentar automatizar al máximo el proceso de intercambio de información.
* Sopesar los beneficios del intercambio de información con las desventajas de compartir información confidencial.

Compartir con otras organizaciones la mayor cantidad posible de información relevante sobre el incidente.

## Práctica de laboratorio - Análisis del ataque
* <a href="./notes/lab_manejo_incidentes.md" target="_blank">Manejo de incidentes</a>

# Recuperación ante desastres
Es fundamental mantener la organización en funcionamiento cuando se produce un desastre. Pero, ¿qué situaciones constituyen un desastre y cómo amenazan el funcionamiento o la seguridad de una organización?

## Tipos de desastres
Un desastre incluye cualquier evento de causa natural o humana que daña los activos o la propiedad y perjudica la capacidad de la organización para seguir operando.
* __Desastres naturales__. Los desastres naturales difieren según laubicación y, a veces, son difíciles de predecir. Se pueden dividir en las siguientes categorías:
	* Los desastres geológicos como los terremotos, derrumbres, erupciones volcánicas y tsunamis.
	* Los desastres meteorológicos como los huracanes, tornados, tormentas de nieve, rayos y granizo.
	* Los desastres sanitarios incluyen enfermedades generalizadas, cuarentenas y pandemias.
	* Los desastres variados incluyen incencdios, inundaciones, tormentas solares y avalanchas.
* __Desastres provocados por el hombre__. Los desastres provocados por el hombre impilcan personas y organ izaciones y se dividen en las siguientes categorías:
	* Los eventos laborales como las huelgas, paros y recesiones.
	* Los eventos sociopolíticos como el vandalismo, bloqueos, protestas, sabotaje, terrorismo y guerra.
	* Los eventos materiales como derrames e incendios peligrosos.
	* Las interrupciones de los servidios como los cortes de electricidad, interrupciones en las comunicaciones, escasez de combustible y lluvia radiactiva.

## Plan de recuperación ante desastres
Una organización pone su Plan de Recuperación ante Desastres (_Disaster Recovery Plan_ - DRP) en acción mientras el desastre está en curso y los empleados intentan proteger los sistemas críticos en línea.

El DRP incluye las actividades que realiza la organización para evaluar, salvar, reparar y restaurar instalaciones o activos dañados.

Para crear el DRP, responda las siguientes preguntas:
* ¿Quién es responsable de este proceso?
* ¿Qué necesita la persona para realizar el proceso?
* ¿Dónde realiza la persona el proceso?
* ¿Cuál es el proceso?
* ¿Por qué es importante el proceso?

Un DRP debe identificar qué procesos de la organización son más importantes. Durante el proceso de recuperación, la organización debe priorizar restaurar sus sistemas de misión críticos.

## Implementación de controles de recuperación ante desastres
Los controles de recuperación tras un desastre minimizan los efectos de un desastre para garantizar que los recursos y procesos empresariales puedan reanudar la operación.
* __Controles preventivos__. Las medidas preventivas incluyen controles que impiden que ocurra un desastre. Su objetivo es identificar y mitigar los riesgos.
* __Controles de detección__. Las medidas de detección incluyen controles que detectan eventos no deseados. Estas medidas descubren nuevas posibles amenazas.
* __Controles correctivos__. Las medidas correctivas incluyen controles que restauran el sistema después de un evento o desastre.

## Planificación de la continuidad del negocio
La continuidad de los negocios es uno de los conceptos más importantes de la seguridad informática. Tener planes en marcha garantizará la continuidad del negocio independientemente de lo que pueda ocurrir.

Un plan de continuidad empresarial (BCP) es un plan más amplio que plan de recuperación ante desastres (DRP), dado que incluye el envío de sistemas críticos a otra ubicación mientras la reparación de la instalación original está en curso. En tal escenario, el personal continúa realizando todos los procesos empresariales de manera alternativa hasta que se reanudan las operaciones normales.

La creación de un plan de continuidad comercial comienza con la realización de un análisis de impacto comercial (BIA) para identificar procesos comerciales críticos, recursos y relaciones entre sistemas. El BIA se centra en las consecuencias de la interrupción de funciones comerciales críticas y examina las consideraciones clave que se enumeran a continuación.
* __Objetivos de tiempo de recuperación (RTO's)__. La cantidad máxima de tiempo tolerable que un sistema, red o aplicación puede no estar disponible después de una falla o un desastre.
* __Objetivos del punto de recuperación (RPO's)__. La vida útil promedio de un activo determinado antes de que falle.
* __Tiempo promedio para reparar (MTTR)__. El tiempo promedio requerido para reparar un componente fallado.
* __Tiempo medio entre fallas (MTBF)__. El tiempo promedio que transcurre entre una falla y la siguiente.

## Consideraciones de continuidad de negocio
Los controles de continuidad de los negocios son mucho más que una simple copia de respaldo de los datos y redundancia del hardware. Las organizaciones necesitan empleados para configurar y operar correctamente los sistemas. Los datos pueden ser irrelevantes hasta que proporcionan información.

Una organización debe tener en cuenta lo siguiente:
* La asignación de las personas adecuadas en los lugares correctos.
* Configuraciones de la documentación.
* Establecimiento de canales alternos de comunicación tanto de voz como de datos.
* El suministro eléctrico.
* Identificando todas las dependencias para las aplicaciones y los procesos para su correcta comprensión.
* Entendiendo cómo realizar las tareas automatizadas manualmente.

## Mejores prácticas de continuidad de negocio
El Instituto Nacional de Estándares y Tecnología (NIST) desarrolló mejores prácticas en relación con la continuidad de los negocios.
1. Desarrolle la declaración de política: Escriba una política que proporcione orientación para desarrollar un plan de continuidad de los negocios y asigne roles para realizar tareas.
2. Realice la evaluación de impacto comercial: identifique los sistemas y procesos críticos y priorícelos en función de la necesidad.
3. Calcule el riesgo: Identificar vulnerabilidades, amenazas y calcular riesgos.
4. Identifique controles preventivos: Identificar e implementar controles y contramedidas para reducir el riesgo.
5. Desarrollar estrategias de recuperación: Elaborar métodos para recuperar rápidamente los sistemas críticos.
6. Desarrollar el plan de contingencia: Escribir procedimientos para mantener la organización en funcionamiento durante un estado caótico.
7. Pruebe el plan: verifique la eficacia del plan en situaciones en tiempo real.
8. Mantenga el plan: Actualícelo periódicamente.

## Ejerciendo su plan de recuperación ante desastres
Hay varios métodos diferentes disponibles para capacitar al personal y probar el plan de recuperación ante desastres de la organización.
* __Ejercicios de mesa__. El más simple es un ejercicio de mesa en el que los participantes se sientan alrededor de una mesa con un facilitador que proporciona información relacionada con un incidente del escenario y los procesos que se están examinando. No se invocan procesos o procedimientos reales; solo se discuten. Esto puede dar lugar a que se den cuenta de que cierto tipo de incidente no está cubierto actualmente en los planes existentes.
* __Pruebas funcionales__. Otro tipo de ejercicio es una prueba funcional donde se prueban ciertos aspectos de un plan para ver qué tan bien funcionan (y qué tan bien preparado está el personal).
* __Ejercicios operativos__. Los más extremos son los ejercicios operativos completos o simulaciones. Estos están diseñados para interrumpir los servicios para verificar que todos los aspectos de un plan estén en su lugar y sean suficientes para responder al tipo de incidente que se está simulando.

## Packet Tracer - Investigar la recuperación ante un desastre
* <a href="./notes/pt_investigar_recuperacion.md" target="_blank">Investigar la recuperación ante un desastre</a>

## Práctica de laboratorio - Recomendar medidas de recuperación tras un desastre
* <a href="./notes/lab_recomendaciones_tras_desastre.md" target="_blank">Recomendar medidas de recuperación tras un desastre</a>

# Resumen
## Manejo de evidencia y atribución del ataque
La informática forense digital consiste en la recuperación e investigación de la información que se encuentra en dispositivos digitales en relación con actividades delictivas. Los indicadores de compromiso son la evidencia de que se ha producido un incidente de ciberseguridad. Estos deben conservarse para futuros análisis y atribuciones de ataques. Una organización necesita desarrollar procesos y procedimientos bien documentados para el análisis forense digital. La publicación especial 800-86 de NIST Guía para la Integración de Técnicas Forenses en Respuesta a Incidentes es un recurso valioso. El proceso forense incluye cuatro pasos: recolección, examen, análisis y presentación de informes. IETF RFC 3227 Describe un orden para la recolección de evidencia digital según la volatilidad de los datos. La cadena de custodia implica la recolección, el manejo y el almacenamiento seguro de la evidencia.

La identificación de los actores responsables de la amenaza (llamada atribución de amenazas) debe darse por medio de la investigación sistemática y fundamentada de la evidencia. En las investigaciones con base en evidencias, el equipo de respuesta ante los incidentes correlaciona las tácticas, las técnicas y los procedimientos (TTP, Tactics, Techniques and Procedures) empleados en el incidente con los de otros ataques conocidos. Las fuentes de inteligencia de amenazas pueden ayudar a relacionar las TTP identificadas por una investigación con fuentes conocidas de ataques similares. Para amenazas internas, descubrir los dispositivos desde donde se inició un ataque puede llevar directamente al actor de amenaza. Una forma de atribuir un ataque es modelar el comportamiento del actor de amenazas. El marco de Tácticas Adversariales, Técnicas y Conocimiento Común (ATT&CK) de MITRE permite a los técnicos en ciberseguridad detectar tácticas, técnicas y procedimientos del atacante como parte de la defensa de amenazas y la atribución de ataques.

## La cadena de eliminación cibernética
Hay siete pasos a la Cadena de Eliminación Cibernética. Estos pasos ayudan a los analistas a entender las técnicas, herramientas y procedimientos de los actores de amenazas. Al responder a un incidente de seguridad, el objetivo es detectar y detener el ataque lo antes posible en el transcurso de la cadena de eliminación.

Los pasos de la Cadena de Eliminación Cibernética (Cyber Kill Chain) son reconocimiento, armamentización, entrega, explotación, instalación, comando y control, y acciones sobre objetivos. El Reconocimiento tiene lugar cuando el actor de amenaza realiza una búsqueda, reúne inteligencia y selecciona objetivos. Armamentización es utilizar la información de reconocimiento para desarrollar un arma contra sistemas o individuos que sean blancos específicos en la organización. Durante la Entrega, el arma es transmitida a los objetivos utilizando un vector de entrega. Una vez que el arma ha sido entregada, el actor de la amenaza la Explota para obtener el control del objetivo. La Instalación se realiza cuando el actor de amenazas establece una puerta trasera al sistema para poder seguir accediendo al objetivo. Para preservar esta puerta trasera, es importante que el acceso remoto no alerte a los analistas de ciberseguridad ni a los usuarios. Comando y Control, o CnC, establece el control del actor de amenaza sobre el objetivo del sistema. El actor de amenaza utiliza los canales de CnC para emitir comandos al software que instaló en el objetivo. Acciones sobre Objetivos describe al agente de amenaza consiguiendo su objetivo original. Este puede ser el robo de datos, la ejecución de un ataque de DDoS, o el uso de la red atacada para crear y enviar correo electrónico no deseado o mina de Bitcoin.

## El modelo de diamante del análisis de la cadena de eliminación
El Modelo de Diamante del Análisis de Intrusiónes representa un incidente o un evento de seguridad. Un evento es una actividad de tiempo limitado que está restringido a un paso específico donde el adversario utiliza la capacidad sobre la infraestructura para atacar una víctima para lograr un resultado específico. Los cuatro componentes principales de un evento de intrusión son el adversario, la capacidad, la infraestructura y la víctima. Las metacaraterísticas, las cuales amplían ligeramente el modelo, incluyen: Marca de tiempo, Fase, Resultado, Dirección, Metodología y Recursos.

Como analistas especializados en ciberseguridad, es posible que se les pida que utilicen el Modelo de Diamante del Análisis de Intrusiónes para diagramar una serie de eventos de intrusión. Los adversarios no ejecutan un solo evento. En cambio, los eventos se entretejen en una cadena en la que cada evento debe completarse con éxito antes del siguiente. Esta serie de eventos puede asignarse a la Cadena de Eliminación Cibernética

## Respuesta a incidentes
La respuesta a incidentes implica los métodos, políticas y procedimientos que utiliza una organización para responder a un ataque cibernético. Los objetivos de la respuesta a incidentes son limitar el impacto del ataque, evaluar los daños causados e implementar procedimientos de recuperación. Es esencial que las organizaciones creen y mantengan planes detallados de respuesta a incidentes y designen al personal responsable de ejecutar todos los aspectos de ese plan. Las recomendaciones del NIST para la respuesta a incidentes se detallan en su Publicación especial 800-61 Revisión 2 titulada “Guía de Manejo de Incidentes de Seguridad Informática”.

El primer paso para una organización es establecer una capacidad de respuesta ante los incidentes de seguridad informática (CSIRC, computer security incident response capability). NIST recomienda crear políticas, planes y procedimientos para establecer y mantener un CSIRC. Algunas de las partes interesadas de CSIRC incluyen la Gerencia, Aseguramiento de Información, Soporte de TI, el Departamento Legal, Relaciones Públicas y con los Medios, Recursos Humanos, Planificadores de Continuidad Comercial, Seguridad Física y Administración de las Instalaciones. El equipo legal debe consultar las regulaciones gubernamentales para determinar la responsabilidad de la organización de informar el incidente. Más allá de los requisitos legales y las consideraciones sobre las partes interesadas, el NIST recomienda que una organización trabaje en conjunto con otras para compartir información sobre incidentes. Cada organización debe tener desarrollada una política que detalle cuánto tiempo debe conservarse la evidencia de un incidente.

El marco de Certificación del Modelo de Madurez de Ciberseguridad (CMMC) fue creado para evaluar la capacidad de las organizaciones que desempeñan funciones para el Departamento de Defensa de los Estados Unidos (DoD) para proteger la cadena de suministro militar de interrupciones o pérdidas debidas a incidentes de ciberseguridad. El CMMC especifica 17 dominios, cada uno de los cuales tiene un número variable de capacidades asociadas a él. La organización se califica por el nivel de madurez que se ha alcanzado para cada uno de los dominios. La CMMC certifica las organizaciones por nivel.

NIST definir cuatro pasos en el ciclo de vida del proceso de respuesta ante los incidentes: 1. Preparación, 2. Detección y Análisis, 3. Contención, Erradicación y Recuperación, y 4. Actividades Posteriores al Incidente. La fase de preparación tiene lugar cuando se crea el CSIRT y se lo capacita. Esta fase ocurre cuando se adquieren e implementan las herramientas y los activos que serán necesarios para que el equipo investigue los incidentes. Los incidentes se detectan con muchos métodos diferentes y no todos son muy detallados ni claros. Hay dos categorías para las señales de un incidente: Precursor e Indicador. El uso de algoritmos complejos y aprendizaje mecanizado ayuda, en ocasiones, a determinar la validez de los incidentes de seguridad. Un método que puede utilizarse es la creación de perfiles de la red y el sistema.

Cuando el CSIRT cree que se ha producido un incidente, debe realizar inmediatamente un análisis inicial para determinar el alcance de los hechos, por ejemplo, qué redes, sistemas o aplicaciones se vieron afectados, qué o quién originó el incidente y cómo está ocurriendo. Cuando se analiza y prioriza un incidente, el equipo de respuesta ante los incidentes debe notificar a las personas interesadas y partes externas para que todos los que necesitan involucrarse desempeñen sus funciones. Es fundamental disponer de documentación clara y concisa relativa a la preservación de la evidencia. La identificación de los atacantes no es tan importante como contener y erradicar el ataque, y recuperar los hosts y servicios. Después de la contención, el primer paso para la erradicación consiste en identificar todos los hosts que necesitan correcciones. Todos los efectos del incidente de seguridad y todas las vulnerabilidades que aprovechó el atacante también deben corregirse o parchearse para que el incidente no vuelva a ocurrir. Después de un incidente, la organización debe informar para revisar la efectividad del proceso de manejo de incidentes e identificar el fortalecimiento necesario para los controles y prácticas de seguridad existentes.

## Recuperación ante desastres
Los desastres naturales difieren según la ubicación y, a veces, son difíciles de predecir. Los desastres causados por el hombre involucran a personas u organizaciones. Un DRP incluye actividades que la organización lleva a cabo para evaluar, recuperar, reparar y restaurar las instalaciones y los activos dañados. Las medidas preventivas incluyen controles que impiden que ocurra un desastre. Las medidas de detección incluyen controles que detectan eventos no deseados. Las medidas correctivas incluyen controles que restauran el sistema después de un evento o desastre.

Los controles de continuidad de los negocios son mucho más que una simple copia de respaldo de los datos y redundancia del hardware. La creación de un plan de continuidad comercial comienza con la realización de un análisis de impacto comercial (BIA) para identificar procesos comerciales críticos, recursos y relaciones entre sistemas. El BIA se centra en las consecuencias de la interrupción de las funciones comerciales críticas y examina las consideraciones clave que se enumeran aquí: RTO, RPO, MTTR y MTBF. El Instituto Nacional de Estándares y Tecnología (NIST) desarrolló mejores prácticas en relación con la continuidad de los negocios.

La capacitación para el plan de recuperación ante un desastre puede utilizar varios métodos. Considere un ejercicio de mesa en el que los participantes se sienten alrededor de una mesa con un facilitador que proporciona información relacionada con un incidente de escenario y procesos que se están examinando. No se invocan procesos o procedimientos reales; solo se discuten. Otro tipo de ejercicio es una prueba funcional en la que se prueban ciertos aspectos de un plan para ver qué tan bien funcionan (y qué tan bien preparado está el personal). At the most extreme are full operational exercises, or simulations. Estos están diseñados para interrumpir los servicios a fin de verificar que todos los aspectos de un plan estén implementados y sean suficientes para responder al tipo de incidente simulado.

# Enlaces de interés
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<a href="#implementación-de-controles-de-seguridad">⬆️</a>
<a href="./00-Curso.md"><< Menú principal del módulo</a>