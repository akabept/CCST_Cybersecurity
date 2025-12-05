<title coding="utf-8">Implementación de controles de seguridad</title>

# Implementación de controles de seguridad
# Objetivos
* Analizar las necesidades de seguridad de una organización.
* Recomendar controles de seguridad según las necesidades de la organización.

# Trasfondo/Situación
En esta práctica de laboratorio, recomendará controles de seguridad basados en las necesidades del sistema de escuelas públicas de Greenville.

El sistema escolar consta de una escuela secundaria, una escuela secundaria y tres escuelas primarias. El distrito atiende a unos 2500 estudiantes, tiene un personal de 210 profesores, 220 administradores y personal de soporte, y 25 miembros del personal de mantenimiento. El punto de presencia de Internet y el centro de datos se encuentran en la escuela secundaria, que también alberga las oficinas administrativas. Las escuelas están interconectadas a la escuela secundaria a través de una red de fibra óptica redundante. El centro de datos aloja todos los servidores necesarios en una ubicación.

Su empresa ha sido contratada para analizar la seguridad física y la ciberseguridad del sistema escolar de Greenville. Recientemente se produjo un incidente en el que un estudiante de secundaria obtuvo las credenciales de un maestro y se conectó a la red administrativa. El estudiante alteró sus calificaciones, desactivó las cámaras de CCTV y obtuvo números de teléfono de estudiantes.

La directora de seguridad del distrito recientemente dejó su trabajo y el puesto no estaba ocupado. La seguridad había sido implementada por varios consultores y empleados y no estaba bien documentada. Su tarea es proponer controles de seguridad que se deben implementar y analizar el sistema actual para ver si utiliza esos controles. El superintendente y la junta escolar han recopilado la siguiente lista de inquietudes de seguridad. Utilizará como punto de partida para el análisis:
* Una amplia variedad de computadoras, con hardware y software obsoletos, se encuentran al azar en todo el distrito, muchas en aulas y laboratorios de aprendizaje.
* Algunos distritos escolares a nivel nacional han enfrentado demandas debido a la pérdida de información de los padres debido a violaciones de datos.
* Otro distrito escolar del estado tuvo que cerrar hasta que se restauraron los sistemas después de un ataque de ransomware que cifró datos almacenados en varias computadoras en la red del distrito.
* Los alumnos han accedido y alterado los registros académicos.
* Un padre que no estaba autorizado para ver a su hijo obtuvo acceso a una actividad después de la escuela en la escuela a la que asistió.
* En el pasado, el personal de limpieza había desconectado el servidor de la biblioteca en el centro de datos.
* La información del alumno fue divulgada por un empleado administrativo en respuesta a un correo electrónico malicioso.

# Recursos necesarios
* Dispositivo con acceso a Internet.

# Instrucciones
## Parte 1: Revisar los controles de seguridad
Revise las definiciones de los tipos de control de seguridad y las funciones a continuación.

Los controles de seguridad se pueden dividir en tres tipos:

1. Controles de seguridad física - implementados para controlar el acceso físico a personas, equipos, instalaciones e información.
2. Controles técnicos de seguridad - implementados para proteger los sistemas de hardware y software y la información que estos sistemas transmiten, procesan o almacenan.
3. Controles administrativos de seguridad - son políticas, procedimientos, reglas y pautas que el personal sigue para alcanzar los objetivos de seguridad de una organización.

Se considera que los controles de seguridad tienen tres funciones:
1. Preventivo: detener las amenazas de seguridad
2. Detective: identifique la actividad no autorizada
3. Correctivo: corrija la actividad no deseada restaurando los sistemas al estado normal de la CIA

## Parte 2: Completar una cuadrícula de controles de seguridad
Ahora completará la cuadrícula recomendando medidas específicas para cada uno de los cuadros vacíos en la cuadrícula. Recomendará medidas, sistemas o actividades de seguridad general y ciberseguridad. Suponga que el distrito escolar no tiene seguridad implementada en este momento.

Registre sus respuestas en la tabla a continuación.

<table>
	<tr><th><th>Preventivo<th>De detección<th>Correctivo
	<tr><td>Controles físicos<td><ul><li>Acceso con timbre bloqueado a edificios escolares<li>Acceso de solo administrador al centro de datos y a las instalaciones de red<li>Sistemas de rociadores<li>Alarmas de botón de pánico <li>La energía de respaldo para sistemas críticos mantenimiento regular del equipo</ul><td><ul><li>Monitoreo de CCTV<li>Alarmas de puerta, ventana y sensor de movimiento<li>Detectores de humo<li>Evaluación de vulnerabilidades y pruebas de penetración<li>Iluminación exterior</ul><td><ul><li>Reparación de daños físicos<li>Reemplazo rápido de equipos dañados o que funcionan mal<li>Mantener partes en el inventario de repuestos<li>Reemitir credenciales perdidas y tarjetas de acceso<li>Alquiler temporal de instalaciones</ul>
	<tr><td>Controles técnicos<td><ul><li>Firewalls de red o IPS<li>Firewalls y anti-virus en los dispotivos<li>Autenticación multifactor para acceder a almacenes de datos confidenciales<li>Acceso VPN para trabajar en el hogar<li>Fortalecimiento del sistema de los dispositivos de red<li>Cifrado de los datos del registro del alumno<li>Control de aplicaciones de red<li>Datos completos y respaldo del SO<li>Robusta administración de parches<li>Control de acceso a edificios basado en tarjetas Proxy DNS</ul><td><ul><li>Monitoreo de acceso y otros registros<li>Monitoreo de seguridad de la red<li>Funcionalidad IDS<li>Recopilación y análisis de datos en los dispositivos<li><i>Honeypots</i><li>AAA u otro registro <code>\</code> <li>SIEM<li>Análisis de tendencias y línea base de la red</ul><td><ul><li>Administración de parches<li>Contención y eliminación de malware<li>Restauración de datos e imagen de disco desde la copia de respaldo</ul>
	<tr><td>Controles administrativos<td><ul><li>Credencial de empleado<li>Limpieza del centro de datos y las instalaciones de red solo bajo supervisión<li>Registro de todos los invitados e identificación de invitados<li>Contratar personal de seguridad especial<li>Seguridad de la contraseña y políticas de renovación<li>Capacitación en concientización sobre seguridad para todo el personal y los estudiantes<li>Políticas y grupos de control de acceso según el rol<li>Políticas y procedimientos de administración de activos</ul><td><ul><li>Auditorías de calificación<li>Revisión del registro AAA</ul><td><ul><li>Planificación de la continuidad<li>Planificación de respuesta ante los incidentes<li>Capacitación de respuesta ante los incidentes<li>Análisis forense<li>Capacitación del usuario posterior al incidente</ul>
</table>

## Preguntas de reflexión
1. ¿Por qué son importantes los controles físicos preventivos en las escuelas?
2. ¿Qué controles administrativos preventivos son más eficaces contra la ingeniería social, incluidos los vectores que propagan el ransomware?
3. ¿Qué es esencial para evitar daños duraderos por ataques de ransomware y ahorrar dinero en pagos de ransomware para la restauración de datos?