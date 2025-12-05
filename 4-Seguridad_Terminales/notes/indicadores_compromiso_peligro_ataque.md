# Indicadores de compromiso, de peligro y de ataque

Los términos "Indicadores de Compromiso" (IoC), "Indicadores de Peligro" (IoT) e "Indicadores de Ataque" (IoA) son fundamentales para la identificación y respuesta ante amenazas cibernéticas. Aquí te explico cada uno:

## Indicadores de Compromiso (IoC - _Indicators of Compromise_)
Los Indicadores de Compromiso son rastros o evidencias que sugieren que un sistema ha sido comprometido por un ciberataque o una actividad maliciosa. Estos indicadores se utilizan para detectar y confirmar la presencia de una brecha en la seguridad. Los IoC suelen ser el resultado de un análisis post-incidente y permiten identificar la naturaleza y el alcance del ataque.

* Ejemplos:
	* Archivos o procesos inusuales.
	* Comunicaciones con direcciones IP o dominios maliciosos.
	* Registros modificados o eliminados en los sistemas.
	* Actividades sospechosas en los logs de red o de sistema.
	* Los IoC son útiles para responder ante incidentes conocidos, ayudando a los analistas a identificar ataques ya reconocidos.

## Indicadores de Peligro (IoT - _Indicators of Threat_)
Los Indicadores de Peligro son señales que sugieren la posibilidad de un ataque inminente o la existencia de condiciones que aumentan el riesgo de un ciberataque. Estos se enfocan en analizar comportamientos o señales que sugieren que una amenaza está presente y que el sistema podría estar en riesgo, pero no necesariamente ha sido comprometido aún.

* Ejemplos:
	* Aumento en las actividades de escaneo de puertos por parte de direcciones IP desconocidas.
	* Actividades de sondeo de vulnerabilidades conocidas.
	* Comportamientos anómalos o fuera de lo común por parte de usuarios o sistemas en la red.
	* Los IoT permiten a las organizaciones adoptar un enfoque proactivo y prevenir ataques antes de que comprometan los sistemas.

## Indicadores de Ataque (IoA - _Indicators of Attack_)
Los Indicadores de Ataque son patrones o señales que permiten identificar las tácticas, técnicas y procedimientos (TTPs) que un atacante está utilizando activamente en una red o sistema. A diferencia de los IoC, que generalmente se descubren después de un incidente, los IoA son señales activas durante un ataque y pueden ayudar a los defensores a mitigar la amenaza en tiempo real.

* Ejemplos:
* Intentos de escalación de privilegios en un sistema.
* Uso de herramientas como Mimikatz para extraer contraseñas.
* Movimientos laterales dentro de una red comprometida.
* Comandos ejecutados desde herramientas como PowerShell con parámetros sospechosos.
* Los IoA permiten a los defensores de seguridad actuar de manera anticipada para interrumpir el ataque antes de que ocurra un daño significativo.

## En resumen:
* IoC (Indicadores de Compromiso) reflejan rastros de una brecha de seguridad que ya ocurrió.
* IoT (Indicadores de Peligro) alertan sobre condiciones que sugieren una amenaza inminente.
* IoA (Indicadores de Ataque) identifican señales y comportamientos de un ataque en curso, permitiendo la detección proactiva.

Estos conceptos son complementarios y juegan un papel crítico en una estrategia integral de ciberseguridad, ayudando tanto a prevenir como a responder a incidentes de manera efectiva.