<title coding="utf-8">Recomendar medidas de mitigación de amenazas</title>

# Recomendar medidas de mitigación de amenazas
## Objetivos
* Parte 1: revisar un incidente en una productora de video
* Parte 2: revisar un incidente en una empresa minorista

## Trasfondo/Situación
El conocimiento de las vulnerabilidades y los ataques a la red es solo una parte de la lucha. La mitigación de amenazas es el objetivo final del personal de seguridad de la red.

En esta práctica de laboratorio, leerá dos casos de estudio que describen incidentes de seguridad de la red. Es su trabajo recomendar medidas de mitigación de amenazas para abordar cada incidente.

## Instrucciones
### Parte 1: Revisar un incidente en una productora de video
All Time Video Inc. es una empresa que produce video para varios clientes. Utilizan métodos de producción de video digital y almacenan su contenido en servidores especializados de administración de contenido. Están muy orgullosos de sus bibliotecas de contenido que incluyen una amplia gama de material de archivo que se puede utilizar en videos sobre muchos temas.

La gerencia de la empresa recibió un correo electrónico de un grupo de agentes de amenazas. En el correo electrónico, los agentes de amenazas afirman que han podido robar varios terabytes de recursos de video y proyectos de los servidores de administración de contenido. Los agentes de amenazas amenazan con cargar los recursos de video a varios servidores en Internet a menos que la empresa pague una suma de dinero. La administración de All Time Video está preocupada porque perderán ventaja competitiva si sus activos se hacen públicos.

La empresa ha contratado un equipo de seguridad externo para investigar el incidente. La investigación descubrió que un lote de unidades USB gratuitas que estaban disponibles en una reciente feria de videos estaban infectadas con malware. El malware infectó varios hosts en la red de All Time Video y también se propagó a través de la red a otras máquinas. El malware analizó la red en busca de varios tipos de software de administración de contenido y determinó la versión del software. El malware luego aprovechó las vulnerabilidades en una versión anterior sin parches del software para obtener acceso. Una vez que se obtuvo el acceso, el malware notificó a los hackers que pudieron instalar software que utiliza túneles DNS para robar datos gradualmente de los servidores. Esto se utilizó para evadir la detección. Durante varios meses, los agentes de amenazas almacenan terabytes de recursos de video.

#### Paso 1: Analice el ataque.
Como miembro del equipo de seguridad de All Time Video, deberá aportar sus ideas sobre cómo se puede mitigar un ataque como este. Comience identificando las condiciones que conducen al ataque.
* ¿Qué tenía que suceder para que este ataque ocurriera?
	1. Las unidades USB infectadas se utilizaron en equipos conectados a la red.
	2. El malware escaneó la red para identificar las direcciones IP de los servidores que ejecutan el software de administración de contenido.
	3. El malware apuntó a vulnerabilidades de software de servidor conocidas para obtener acceso privilegiado al servidor.
	4. Los agentes de amenazas tuvieron acceso al servidor desde fuera de la red e instalaron software que enviaba archivos fuera de la red.

#### Paso 2: Recomendar técnicas de mitigación.
Para cada evento que ocurrió durante este incidente, utilice su acceso a Internet para investigar posibles técnicas de mitigación. Usted es libre de utilizar cualquier fuente de información que pueda encontrar para recomendar técnicas de mitigación de amenazas procesables.
1. Educar a los usuarios sobre los peligros de introducir medios potencialmente inseguros en el lugar de trabajo. Configure el software de detección de virus para analizar medios externos.
2. Supervise la red en busca de tráfico inusual, como la actividad de análisis de fuentes internas que no se utilizan para la administración de redes.
3. Mantenga el software empresarial actualizado con las últimas versiones y parches.
4. Controle el acceso a la red con firewalls o IPS, proteja los recursos internos del acceso externo.

### Parte 2: revisar un incidente en una empresa minorista
Una empresa minorista mediana se especializa en componentes de guitarra personalizados. Un cliente llamó para informar a la empresa que sus datos personales y la información de su tarjeta de crédito están en Internet. Una investigación muestra que los agentes de amenazas pudieron infiltrarse en la red de la empresa a través de la conexión de red de un proveedor de equipos. El propósito de la conexión es monitorear una herramienta para trabajar la madera controlada por computadora que se utiliza para crear cuellos y cuerpos de guitarra. Una seguridad débil en el proveedor permitió a los agentes de amenazas aprovechar esta conexión. Los creadores de amenazas pudieron localizar y acceder al servidor que se utiliza para aceptar pagos de productos a través de Internet. Los agentes de tratamiento aprovecharon una cuenta de usuario y una contraseña débil para acceder a la base de datos de clientes. Todos los detalles del cliente estaban en un archivo fácil de leer. El archivo se cargó en un servidor que utilizan los hackers y la información se vendió a otros hackers.

#### Paso 1: Analizar el ataque
Lea la descripción del incidente y enumere los pasos del ataque.
1. El acceso a la red interna se obtuvo a través de una red de terceros.
2. Analizar en busca de servidor de pago.
3. Se utilizaron credenciales débiles para el acceso.
4. Información del cliente fácil de identificar.
5. Archivo de datos del cliente robado.

#### Paso 2: Recomendar técnicas de mitigación.
Para cada evento que ocurrió durante este incidente, recomiende medidas que puedan mitigar el evento.
1. El acceso a la red interna se obtuvo a través de una red de terceros.
2. Analizar en busca de servidor de pago.
3. Se utilizaron credenciales débiles para el acceso.
4. Información del cliente fácil de identificar.
5. Archivo de datos del cliente robado.

#### Reflexión
1. ¿Qué recursos específicos encontró en la Web que le permitieron recomendar medidas de mitigación?
	* Hay muchos recursos disponibles en la web que pueden contribuir a su conocimiento de la ciberseguridad. Debe registrar los sitios que le resulten más útiles en un archivo o guardados en su navegador en las carpetas que lo ayudarán a revisarlos según sea necesario. Guardar las URL en un archivo permite realizar anotaciones para identificar los detalles de los sitios.
2. Busque en la Web las 5 principales amenazas de ciberseguridad que enfrentan las pequeñas y medianas empresas (SMB) o las empresas (SME). Enumere las amenazas en la tabla y sugiera técnicas de mitigación que puedan ayudar a contrarrestarlas. Las respuestas variarán, con diferentes sitios web que enumeran diferentes amenazas. No se trata de un problema nuevo. Solo asegúrese de que la información sea reciente e investigue brevemente la fuente de información para verificar su calidad.
	* ¿Dónde encontró su información? Copie y pegue la URL a continuación.
	* ¿Cuál es el nombre de la organización que proporcionó la información?
	* ¿Cuál es la naturaleza de la organización?
	* Completa la tabla.
	
	__Amenaza__|__Recomendaciones de mitigación__
	:-|:-
	`completar`|`completar`
	`completar`|`completar`
	`completar`|`completar`
	`completar`|`completar`
	`completar`|`completar`
