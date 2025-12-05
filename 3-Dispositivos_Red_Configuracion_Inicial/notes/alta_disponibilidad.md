# Alta disponibilidad

La alta disponibilidad (HA, por sus siglas en inglés) es un concepto clave en la administración de redes informáticas que se refiere a la capacidad de un sistema para funcionar de manera continua y sin interrupciones significativas. En términos sencillos, se trata de asegurarse de que los servicios y aplicaciones estén disponibles para los usuarios en todo momento, incluso frente a fallos o problemas técnicos.

Para lograr alta disponibilidad, se utilizan diversas técnicas y estrategias, entre las cuales destacan:

1. __Redundancia__: Se implementan componentes duplicados en el sistema, de manera que si uno falla, otro pueda tomar su lugar sin interrumpir el servicio. Por ejemplo, tener dos servidores en lugar de uno.
2. __Balanceo de carga__: Distribuye el tráfico de red entre varios servidores para evitar que uno solo se sobrecargue. Esto no solo mejora el rendimiento sino que también aumenta la disponibilidad, ya que si un servidor falla, los otros pueden seguir manejando el tráfico.
3. __Clústeres de servidores__: Conjunto de servidores que trabajan juntos y pueden asumir las cargas de trabajo de otros servidores en caso de fallo. Esto asegura que si uno o varios servidores fallan, los servicios sigan operativos.
4. __Sistemas de respaldo y recuperación__: Incluye copias de seguridad regulares y mecanismos para restaurar los datos rápidamente en caso de fallos. Esto garantiza que la información esté siempre disponible, incluso después de una pérdida de datos.
5. __Monitoreo continuo__: Se supervisan constantemente todos los componentes del sistema para detectar y resolver problemas antes de que afecten la disponibilidad del servicio.
6. __Georredundancia__: Distribuir los recursos y datos en múltiples ubicaciones geográficas para proteger contra fallos a nivel regional, como desastres naturales.

Implementar alta disponibilidad requiere una planificación cuidadosa y una inversión en infraestructura adecuada, pero es crucial para empresas que dependen de sus sistemas informáticos para operar. La idea es minimizar el tiempo de inactividad y asegurar que los servicios estén disponibles casi todo el tiempo, lo cual es esencial para mantener la confianza de los usuarios y la continuidad del negocio.

La alta disponibilidad de un sistema se mide principalmente a través del tiempo de actividad (uptime) y se expresa en términos de porcentajes. Este porcentaje representa el tiempo que el sistema está operativo y disponible para los usuarios en un periodo determinado, generalmente un año. La métrica más comúnmente usada para este propósito es el "número de nueves", que indica la cantidad de nueves en el porcentaje de disponibilidad. Aquí tienes una explicación más detallada:

# Fórmula Básica
__Disponibilidad (%)__ = (Tiempo de actividad / Tiempo total) × 100

## Niveles de Disponibilidad
1. 90% de disponibilidad: Aproximadamente 36,5 días de inactividad al año.
2. 99% de disponibilidad: Aproximadamente 3,65 días de inactividad al año.
3. 99.9% de disponibilidad (tres nueves): Aproximadamente 8,76 horas de inactividad al año.
4. 99.99% de disponibilidad (cuatro nueves): Aproximadamente 52,56 minutos de inactividad al año.
5. 99.999% de disponibilidad (cinco nueves): Aproximadamente 5,26 minutos de inactividad al año.
6. 99.9999% de disponibilidad (seis nueves): Aproximadamente 31,5 segundos de inactividad al año.

# Medición de la Disponibilidad
Para medir la alta disponibilidad de un sistema, se utilizan las siguientes técnicas y herramientas:

1. Monitoreo de Sistemas: Herramientas como Nagios, Zabbix, PRTG, y otras soluciones de monitoreo pueden rastrear el tiempo de actividad y el tiempo de inactividad de los componentes del sistema en tiempo real.
2. Registro de Eventos: Los registros de eventos (logs) de sistemas y aplicaciones pueden ser analizados para identificar periodos de inactividad y determinar las causas subyacentes.
3. Pruebas de Resiliencia: Realizar pruebas periódicas de failover y recuperación ayuda a asegurar que los sistemas de respaldo y redundancia funcionan correctamente.
4. Acuerdos de Nivel de Servicio (SLA): Los SLA entre proveedores de servicios y clientes definen los niveles esperados de disponibilidad y especifican las penalizaciones en caso de no cumplir con esos niveles.

# Cálculo de Disponibilidad
Supongamos que tienes un sistema que experimentó 4 horas de inactividad en un año. El cálculo de la disponibilidad sería:

* __Tiempo total en un año__: 365 días × 24 horas = 8760 horas
* __Tiempo de inactividad__: 4 horas
* __Tiempo de actividad__: 8760 horas - 4 horas = 8756 horas
* __Disponibilidad (%)__ = (8756 / 8760) × 100 ≈ 99.95%

# Consideraciones Adicionales
* __MTBF (Mean Time Between Failures)__: Tiempo promedio entre fallos. Es una medida de la fiabilidad del sistema.
* __MTTR (Mean Time to Repair)__: Tiempo promedio para reparar el sistema después de un fallo. Es una medida de la capacidad del sistema para recuperarse.

Estos indicadores adicionales ayudan a tener una visión más completa de la disponibilidad y fiabilidad del sistema, permitiendo a los administradores identificar áreas de mejora y tomar medidas proactivas para aumentar la disponibilidad.

# Inactividad y Alta Disponibilidad
En el contexto de la alta disponibilidad, la inactividad se refiere específicamente al tiempo durante el cual el sistema no puede proporcionar el servicio que se supone debe ofrecer. Este tiempo de inactividad es visto como negativo porque representa periodos en los que los usuarios no pueden acceder a las aplicaciones, servicios o datos que necesitan.
La inactividad puede ser causada por diversos factores, como:

* Fallos de hardware: Problemas con servidores, discos duros, componentes de red, etc.
* Errores de software: Bugs, fallos en actualizaciones o problemas de configuración.
* Interrupciones de energía: Cortes de electricidad que afectan la operatividad del centro de datos.
* Errores humanos: Configuraciones incorrectas, errores durante el mantenimiento, etc.
* Ataques de seguridad: Ataques DDoS, hackeos, malware, entre otros.
* Desastres naturales: Terremotos, inundaciones, incendios, etc.

## Disponibilidad: Cálculo y Significado
La disponibilidad se mide para evaluar cuánto tiempo el sistema está operativo y accesible en comparación con el tiempo total esperado. Aquí te dejo un resumen del cálculo y su significado:

* __Tiempo Total__: El periodo total considerado para la medición (por ejemplo, un año).
* __Tiempo de Actividad__: El tiempo durante el cual el sistema está funcionando correctamente y proporcionando los servicios esperados.
* __Tiempo de Inactividad__: El tiempo durante el cual el sistema no está disponible para los usuarios debido a fallos, mantenimiento u otras interrupciones.

__Disponibilidad (%)__ = (Tiempo de Actividad / Tiempo Total) × 100

Por ejemplo, si en un año (8760 horas) un sistema estuvo inactivo durante 4 horas debido a un fallo, su disponibilidad sería:

* __Tiempo de Actividad__: 8760 horas - 4 horas = 8756 horas
* __Disponibilidad (%)__: (8756 / 8760) × 100 ≈ 99.95%

## Interpretación de la Disponibilidad
* __99.95% de Disponibilidad__: Esto significa que el sistema estuvo disponible el 99.95% del tiempo durante el año, pero también implica que hubo un 0.05% del tiempo (en este caso, 4 horas) en el que el sistema no estuvo disponible para los usuarios.

## Alta Disponibilidad y Mantenimiento
Es importante considerar que algunas inactividades pueden ser planificadas, como el mantenimiento regular. Para minimizar el impacto de estas inactividades planificadas, se implementan estrategias como:

* __Mantenimiento en horarios no pico__: Realizar mantenimientos durante la noche o fines de semana, cuando el impacto sobre los usuarios es menor.
* __Infraestructura redundante__: Tener componentes y sistemas duplicados que permitan realizar mantenimientos sin interrumpir el servicio.

En resumen, la alta disponibilidad se centra en maximizar el tiempo de actividad y minimizar las interrupciones, asegurando que los servicios estén accesibles para los usuarios casi todo el tiempo. La inactividad, vista como algo negativo, es cualquier periodo en el que el sistema no puede proporcionar los servicios esperados, y reducir este tiempo es el objetivo principal de las estrategias de alta disponibilidad.

<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />