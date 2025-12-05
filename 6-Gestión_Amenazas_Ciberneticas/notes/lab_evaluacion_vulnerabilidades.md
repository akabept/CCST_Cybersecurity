<title coding="utf-8">Evaluación de vulnerabilidades</title>

# Evaluación de vulnerabilidades
# Objetivos
En esta práctica de laboratorio, revisaremos las características de un ejemplo de informe de vulnerabilidad de pruebas penetrantes.
* __Parte 1__: Aprenda sobre los creadores de un informe de evaluación de vulnerabilidad.
* __Parte 2__: Revisar las secciones del informe.

# Trasfondo/Situación
Las evaluaciones de vulnerabilidad pueden ser realizadas internamente o por contratistas externos. Las evaluaciones de vulnerabilidad generalmente están automatizadas. Los hosts de red accesibles se identifican y luego se analizan con herramientas de evaluación de vulnerabilidades. El análisis crea muchos datos que asignan las direcciones IP del host a las vulnerabilidades detectadas. A partir de estos datos, se pueden crear datos de resumen y visualizaciones para simplificar la interpretación del informe.

Cuando se identifican, las vulnerabilidades a menudo se clasifican por gravedad, a menudo utilizando un medio estándar para hacerlo, como CVSS. Además, a menudo se proporciona información de referencia para permitir una investigación más profunda si es necesario. Por lo general, se proporciona un número de CVE que es fácil de investigar más a fondo.

El informe puede sugerir técnicas de mitigación comunes que proporcionan orientación al personal de ciberseguridad sobre cómo eliminar las vulnerabilidades que se han identificado.

# Recursos necesarios
* Computadora con acceso a Internet.
* Ejemplo de informe de evaluación de vulnerabilidad.

# Instrucciones
## Parte 1: Aprenda sobre los creadores de un informe de evaluación de vulnerabilidad
### Paso 1: Investigue el origen del informe.
El informe que utilizaremos para este laboratorio fue creado por el servicio de Higiene Cibernética de NCATS.
Investigue NCATS en Internet y responda las siguientes preguntas.
* ¿Qué significa NCATS?
* ¿Qué es el Servicio de Escaneo de Vulnerabilidades de Higiene Cibernética? Busque en la web para obtener más información.
* ¿Qué otros servicios de ciberseguridad hay disponibles de NCATS?
* ¿Para quién están disponibles estos servicios?

### Paso 2: Busque y abra el informe.
1. El enlace al informe que revisaremos está directamente en la sección Higiene Cibernética: Escaneo de Vulneravilidad de la página de NCATS. Para acceder al enlace desde el motor de búsqueda de Google, ingrese lo siguiente: site: us-cert.cisa.gov/ CyHy
2. Abra el informe y revise la tabla de contenido para tener una idea de lo que se incluye.

## Parte 2: Revisar las secciones del informe
Las primeras dos secciones del informe explican su uso previsto y proporcionan una descripción general de alto nivel de los resultados del informe.

### Paso 1: Revise la sección Cómo usar el informe.
Es importante comprender el uso previsto de cualquier informe de evaluación de seguridad. Un buen informe proporcionará pautas útiles y específicas para el uso de la evaluación.

__Nota__: Dado que este informe es un ejemplo, la organización para la que se preparó el informe se denomina Organización de muestra (muestra).

Revisen la sección uno del reporte y responda las siguientes preguntas.
* ¿Cuál es el objetivo del informe?
* ¿En qué sección del informe puede encontrar una descripción general de alto nivel de los resultados de la evaluación, incluidas algunas comparaciones del rendimiento semanal?
* ¿Dónde puede encontrar una lista detallada de resultados y recomendar mitigaciones para cada vulnerabilidad?
* ¿Qué le permite abrir fácilmente los resultados del análisis en una hoja de cálculo u otro documento tabular?

### Paso 2: Revise la tarjeta de reporte de Higiene Cibernética.
Mire la tarjeta de reporte de Higiene Cibernética. Esto proporciona un resumen de alto nivel de los resultados de la evaluación. Esta organización se analiza semanalmente, por lo que se proporciona información de tendencias con los resultados del análisis actual.
* ¿Qué porcentaje de los hosts analizados fue vulnerable? ¿Cómo se compara esto con el análisis anterior?
* Las vulnerabilidades se clasifican por gravedad. ¿Qué nivel de gravedad representa la mayor cantidad de hosts recientemente vulnerables?
* ¿Qué clase de vulnerabilidad requiere más tiempo para mitigar a la organización?
* El análisis incluyó 293,005 direcciones IP, pero evaluó solo 3,986 hosts. ¿Por qué crees que es así?

### Paso 3: Revise el Resumen Ejecutivo.
Vaya al Resumen Ejecutivo Lea esta sección y responda las siguientes preguntas.
* ¿Qué dos funciones principales incluyó la evaluación y qué hosts evaluó?
* ¿Cuántos tipos distintos de vulnerabilidades se identificaron?
* De las cinco vulnerabilidades principales por ocurrencia, ¿cuál era el protocolo o sistema común más vulnerable?
* De las cinco categorías principales por grado de riesgo, ¿qué vulnerabilidades parecen estar relacionadas con una pieza específica de hardware de red? ¿Cuál es el dispositivo?
* Busque en la Web en “MikroTik Router OS 6.41.3 SMB”. Busque la entrada de CVE para esta vulnerabilidad en el sitio web de la Base de Datos de Vulnerabilidad Nacional (NVD). ¿Cuál es la puntuación básica de CVSS y la calificación de gravedad?
* Busque el informe de divulgación completo de esta CVE buscando en la web o haciendo clic en un enlace de referencia. En el informe de divulgación completo, ¿cuáles son dos formas de mitigar la vulnerabilidad?
* ¿Qué tipo de vulnerabilidad es esta y qué puede hacer un atacante cuando es explotado?
* ¿Qué debe haber hecho la organización de muestra para evitar que esta vulnerabilidad crítica aparezca en su red?

### Paso 4: Revise la metodología y el proceso de evaluación.
Es importante evaluar la metodología utilizada para crear una evaluación de vulnerabilidades a fin de determinar la calidad del trabajo realizado. Revise el material en esa sección del informe.
* En la sección Proceso, el informe menciona una red IP desde la que se realizó el análisis. ¿Cuál es la red IP y para quién está registrada? ¿Por qué es importante decirle esto a la organización de muestra?
* ¿Qué califica a una computadora para ser designada como host para los efectos de este informe?
* ¿Qué herramienta utilizó el análisis para la asignación de red? ¿Qué herramienta se utilizó para la evaluación de vulnerabilidades?
* ¿Quién ofrece el producto Nessus y cuál es la limitación de la versión de descarga gratuita de Nessus?
* ¿Vulnerabilidades con qué rango de puntuaciones de CVSS se clasifican como de “alta” gravedad?

### Paso 5: Investigar las vulnerabilidades detectadas.
Vaya a la sección 7 del informe y busque la Tabla 6. Los nombres de vulnerabilidad constan de una frase descriptiva estándar. Seleccione una descripción y búsquela en la Web. Debería ver un enlace a tenable.com para cada una de ellas. Tenable mantiene páginas de referencia para las vulnerabilidades que Nessus puede detectar.
1. Abra la página de referencia de la vulnerabilidad y revise la información que le proporciona Tenable. Lea la sinopsis y la descripción de la vulnerabilidad. Algunas páginas de referencia proporcionan medidas de mitigación sugeridas.
2. Seleccione tres de las vulnerabilidades de la lista de vulnerabilidades principales y repita este proceso. Revise la vulnerabilidad, el número de CVE, la descripción y las medidas de mitigación, si las hubiera. Investigue la vulnerabilidad si está interesado.

### Paso 6: Investigar la mitigación de vulnerabilidades.
Vaya al apéndice C del informe. Se enumeran técnicas de mitigación para muchas de las vulnerabilidades detectadas. Responda las siguientes preguntas.
* ¿Cuál es la dirección IP del host que ejecuta un servicio PHP vulnerable? ¿Por qué cree que esta vulnerabilidad existe en este host?
* ¿Qué debe hacerse para mitigar esta vulnerabilidad?
* Hay muchos problemas asociados con SSL. ¿Cuáles son algunas de las medidas de mitigación recomendadas en el informe?

## Preguntas de reflexión
* Describa la evaluación de vulnerabilidades que realizó el NCCIC, incluido cómo se realizó, las herramientas utilizadas y una breve descripción de los resultados.
* ¿Cómo son útiles los nombres de vulnerabilidad para futuras investigaciones?
* Proporcione tres acciones que podría tomar según la información proporcionada en un informe de Higiene Cibernética.