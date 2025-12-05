<title coding="utf-8">Recomendar medidas de seguridad de terminales</title>

# Recomendar medidas de seguridad de terminales
# Objetivos
* __Parte 1__: Recomendar procedimientos de mitigación para abordar las vulnerabilidades.
* __Parte 2__: recomendar un producto de protección de terminales para una nueva red.

# Trasfondo/Situación
Para proporcionar seguridad, los profesionales generalmente implementan una serie de medidas de seguridad de la red que funcionan en conjunto en un enfoque de seguridad por capas. Los firewalls y otros dispositivos protegen el perímetro de la red contra ataques; sin embargo, siempre es posible que las amenazas puedan eludir estas defensas. Por lo tanto, no solo es necesario proteger el perímetro de la red, sino también tomar medidas para proteger los hosts de red individuales contra riesgos. En esta práctica de laboratorio, leerá dos casos de estudio y recomendará mitigaciones de amenazas de terminales que sean adecuadas para abordar los ataques.

# Recursos necesarios
* Acceso a Internet. 

# Instrucciones
## Parte 1: Recomendar procedimientos de mitigación para abordar las vulnerabilidades
Usted trabaja en un equipo de seguridad para una empresa de fabricación. Un cliente nuevo requiere que, antes de que la empresa pueda recibir el contrato, cumpla con estándares más estrictos. Se completó una evaluación de vulnerabilidades de la red y se encontraron varias vulnerabilidades, incluidos los siguientes problemas de seguridad de terminales:
* La empresa utiliza sistemas de control de supervisión y adquisición de datos (SCADA) para supervisar y controlar sus procesos de fabricación. El software SCADA se ejecuta en el sistema operativo Windows XP.
* Los sistemas críticos permiten el uso de medios USB desconocidos.
* Los usuarios pueden acceder a la red con dispositivos de computación personal, como smartphones, tablets y computadoras portátiles.
* Los usuarios pueden navegar libremente por la WWW, incluidos los sitios de malware conocidos.
* El software antivirus inconsistente instalado en los hosts incluía versiones antiguas con un estado de actualización de firma desconocido.

Con el material cubierto en este curso y la información adicional que encuentra en Internet, complete la tabla a continuación.

__Publicación__|__Recomendación__
:-|:-
Versiones obsoletas del sistema operativo|Actualice los sistemas operativos a las últimas versiones compatibles. Si las aplicaciones no son compatibles con las nuevas versiones, aísle los sistemas en su propia red para evitar ataques
Los sistemas críticos permiten el uso de medios USB|Active el análisis de malware de medios USB en el software de protección de terminales
Uso de dispositivos de computación personal en la red|Utilice el control de acceso a la red para verificar que los sistemas que inician sesión en la red cumplan con las políticas de seguridad relacionadas con la seguridad y las configuraciones del SO
Los usuarios pueden navegar libremente por la Web|Implementar un dispositivo de seguridad web u otro medio de filtrado de solicitudes web a sitios web maliciosos conocidos
Problemas de antivirus|Estandarizar en una plataforma o sistema de seguridad que administre software antivirus y actualizaciones de firmas

## Parte 2: recomendar un producto de protección de terminales para una nueva red
Un amigo ha recibido recientemente fondos de capital de riesgo para un nuevo producto prometedor. Se prevé un rápido crecimiento. Está abriendo una ubicación para su inicio y le ha pedido que lo ayude con recomendaciones sobre medidas de seguridad de terminales para implementar en la nueva red.

Utilice su aprendizaje en el curso e investigue en Internet para recomendar un producto de seguridad integral para terminales. Tenga en cuenta que la empresa actualmente es pequeña, pero crecerá rápidamente. Proporcione los motivos de su decisión según las características del producto.

Registre su producto elegido:

__Característica__|__Valor__
:-|:-
Protección avanzada contra malware|Utiliza detección basada en firmas y en comportamientos
Gratis pero actualizable a la edición comercial|Bueno para la protección inicial, si el presupuesto lo permite, puede actualizarse a una versión comercial con más funciones
Analiza el correo electrónico|Analiza los correos electrónicos entrantes y salientes en busca de malware con el uso de Microsoft Outlook o Mozilla Thunderbird
Analiza los datos recibidos de la Web|Puede detectar scripts maliciosos
Análisis de software|Busca aplicaciones desactualizadas que puedan ser vulnerables
Protección contra ransomware|Evita que el ransomware modifique archivos de datos importantes
Galardonado y bien revisado|Muy popular, bien revisado por fuentes confiables como AV-TEST Institute