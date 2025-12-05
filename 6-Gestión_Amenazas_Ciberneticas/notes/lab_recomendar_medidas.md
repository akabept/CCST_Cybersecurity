<title coding="utf-8">Recomendar Medidas de Seguridad para Cumplir con los Requisitos de Cumplimiento</title>

# Recomendar Medidas de Seguridad para Cumplir con los Requisitos de Cumplimiento
# Objetivos
* __Parte 1__: Investigar los requisitos de cumplimiento.
* __Parte 2__: Recomendar soluciones de cumplimiento.

# Antecedentes
El cumplimiento de las normas de seguridad y privacidad relevantes es un desafío para la mayoría de las empresas. El cumplimiento suele ser complejo y hay mucho en juego. Las empresas con frecuencia subcontratan gran parte de la carga del cumplimiento a las empresas que se especializan en proporcionar soluciones que han demostrado cumplir con los requisitos de cumplimiento y satisfacer las auditorías de cumplimiento.

En esta práctica de laboratorio, investigará los requisitos de cumplimiento y recomendará medidas para cumplir con los requisitos de HIPAA. La Ley de Portabilidad y Responsabilidad del Seguro Médico (HIPAA) es un conjunto de regulaciones creadas en los Estados Unidos para proteger la privacidad y los derechos de los pacientes de servicios de salud. Controla cómo se puede compartir la información de atención médica del paciente. Especifica requisitos detallados que están diseñados para proteger la privacidad y la seguridad del paciente.

Todos los proveedores de servicios de salud en los Estados Unidos, desde la oficina más pequeña hasta los hospitales más grandes, deben cumplir con HIPAA. Muchos proveedores de servicios han ingresado al mercado para ayudar a los proveedores de servicios de salud a cumplir con HIPAA.

# Situación
El Dr. Anthony Larouche, un dentista, ha estado trabajando en un gran consultorio con otros dentistas. Ha decidido abrir su propia oficina. Todos los sistemas de TI relacionados con la oficina estaban a cargo de su personal de oficina. Sabe poco sobre redes de computadoras y seguridad de redes. Ha contratado a su empresa como consultores para ayudarlo a cumplir con los requisitos de seguridad técnica de HIPAA.

Se le ha pedido que cree una lista de requisitos específicos que cumplan con las Garantías Técnicas en virtud de la Regla de Seguridad de las regulaciones de cumplimiento de HIPAA.

# Recursos necesarios
* Computadora u otro inteligente con conexión a Internet

# Instrucciones
## Parte 1: Investigar los requisitos de cumplimiento
En esta parte, revisará los requisitos para cumplir con las especificaciones de seguridad de HIPAA. Las regulaciones de HIPAA constan de dos reglas, la Regla de Privacidad y la Regla de Seguridad. Nos centraremos en la regla de seguridad, que consiste en medidas de seguridad, estándares y especificaciones de implementación. Hay cinco estándares de seguridad en la protección técnica. Algunos de los estándares tienen varias especificaciones de implementación asociadas. Algunos estándares no tienen especificaciones de implementación.

### Paso 1: Familiarícese con las Protecciones de HIPAA
Busque en la Web para obtener más información sobre las protecciones de reglas de seguridad de HIPAA. Un buen sitio para buscar una descripción general de la regla de seguridad de HIPAA es el sitio: compliancy-group.com. Responda las siguientes preguntas.
* ¿Cuáles son tres ejemplos de información de salud protegida?
	* nombre, dirección, cumpleaños
* Resuma las cuatro reglas generales que todas las organizaciones de servicios de salud deben seguir en relación con la Regla de Seguridad.
	* Garantizar la confidencialidad, la integridad y la disponibilidad de toda la información de salud protegida por medios electrónicos
	* Identificar y proteger contra las amenazas cibernéticas
	* Proteger contra usos o divulgaciones no permitidos
	* Garantizar el cumplimiento de los trabajadores
* ¿Cuáles son los tres tipos de medidas de seguridad que conforman la regla de seguridad de HIPAA?
	* Administrativo, físico y técnico

### Paso 2: Revisar los documentos de la protección técnica
1. Consulte este documento para obtener una aclaración sobre las normas de seguridad técnica 164.312 (a) - (e) (2) (ii) y el tratamiento de la información médica protegida electrónica (EPHI). Consulte otras fuentes de Internet para obtener aclaraciones adicionales. Revise rápidamente el contenido del documento.
2. Complete la siguiente tabla con los nombres de estándares y las especificaciones de implementación de los estándares, cuando corresponda. Dos de las normas no tienen especificaciones de implementación.
* Garantías técnicas

__Sección__|__Estándar__|__Especificaciones de implementación__
:-|:-|:-
164.312 (a)(1)|Control de acceso|= Identificación de usuario única= Procedimiento de Acceso de Emergencia= Cierre de sesión automático= Cifrado y descifrado
164.312 (b)|Controles de auditoría|No corresponde
164.312 (c)(1)|Integridad|= Mecanismo para Autenticar iInformación Médica Protegida Electrónicamente
164.312 (d)|Autenticación de Persona o Entidad|No corresponde
164.312 (e)(1)|Seguridad de Transmisión|= Controles de integridad= Cifrado

## Parte 2: Recomendar soluciones de cumplimiento.
Las especificaciones técnicas de seguridad de HIPAA deben sugerir medidas de seguridad que mejoren o cumplan con cada requisito. Complete la siguiente tabla con sus recomendaciones. Utilice los conocimientos adquiridos en el curso hasta el momento y realice búsquedas adicionales en Internet. Descubrirá que hay muchas soluciones disponibles de las empresas que abordan cada estándar HIPAA.

__Estándar__|__Nombre_|__Control__
:-|:-|:-
164.312 (a)(1)|Control de acceso|
164.312 (a)(1)(i)|Identificación de usuario única|Todos los usuarios deben tener nombres de usuario únicos no solo para iniciar sesión, sino también para identificar quién ha creado, editado o accedido a EPHI.
164.312 (a)(1)(ii)|Procedimiento de acceso de emertgencia|HDD con almacenamiento duplicado de registros, copias de seguridad, uso de nube segura para almacenamiento y recuperación de datos.
164.312 (a)(1)(iii)|Cierre de sesión automático|Todas las computadoras deben tener políticas de seguridad de cierre de sesión después de un período de inactividad. Configure las aplicaciones relevantes para cerrar la sesión de los usuarios automáticamente después de un período de inactividad.
164.312 (a)(1)(iv)|Cifrado y descifrado|Identifique la información que se va a cifrar, cifre el HDD del servidor, ya sea en software o con unidades de cifrado automático.
164.312 (b)|Controles de auditoría|Implemente la contabilidad AAA y el seguimiento de versiones de documentos.
164.312 (c)(1)|Integridad|
164.312 (c)(2)|Mecanismo para autenticar la información de salud electrónica protegida (EPHI)|Implemente el monitoreo de la integridad de archivos (FIM)
164.312 (d)|Autenticación de Persona o Entidad|Autenticación multifactor (MFA), preguntas para restablecer la contraseña, autenticación biométrica
164.312 (e)(1)|Seguridad de Transmisión|
164.312 (e)(2)(i)|Controles de integridad|hash de seguridad de las comunicaciones en documentos transmitidos, eliminación segura de correos electrónicos y otros documentos de EPHI
164.312 (e)(2)(ii)|Cifrado|Transmisión segura WPA2 o inalámbrica mejor, VPN para acceso remoto, correo electrónico cifrado, HTTPS, eliminación de EPHI del correo electrónico no cifrado, como reenvíos y respuestas.

## Preguntas de reflexión
1. Existen muchos marcos de cumplimiento que imponen requisitos a la seguridad de la red. La relevancia de estos marcos depende del tipo de negocio y de las actividades comerciales que se realizan. PCI-DSS es un marco de cumplimiento para las empresas que aceptan pagos con tarjetas de crédito. Busque en la web los objetivos de control de PCI-DSS. Cada objetivo tiene uno o más requisitos. A partir de sus búsquedas, complete la siguiente tabla:

__Objetivos de PCI-DSS__|__Requisitos de PCI-DSS__
:-|:-
Crear y mantener una red segura|= Instalar y mantener una configuración de firewall para protección de los datos del tarjetahabiente= No utilizar los valores predeterminados suministrados por el proveedor para las contraseñas del sistema y otros parámetros de seguridad.
Proteger los datos de los tarjetahabientes|= Proteger los datos almacenados de los tarjetahabientes.= Cifrar la transmisión de los datos de los tarjetahabientes por redes abiertas y públicas.
Mantener un programa de administración de vulnerabilidades|= Usar y actualizar periódicamente el software antivirus.= Desarrollar y mantener sistemas y aplicaciones seguras.
Implementar sólidas medidas de control de acceso|= Restringir el acceso a los datos del tarjetahabiente por medio de el negocio-necesita-saber.= Asignar una ID única a cada persona que tenga acceso a una computadora.= Restringir el acceso físico a los datos de los tarjetahabientes.
Monitorear y probar las redes periódicamente|= Seguir y monitorear todo el acceso a los recursos de la red y a los datos de los tarjetahabientes.= Probar periódicamente los sistemas y procesos de seguridad.
Mantener una política de seguridad de la información|= Mantener una política que aborde la seguridad de la información para todo el personal.

2. ¿Cómo se comparan estos requisitos de cumplimiento con los requisitos de HIPAA que proporcionó anteriormente?
	* Son muy similares. La mayoría son requisitos de seguridad de sentido común que son familiares.
3. Los marcos de cumplimiento como HIPAA y PCI-DSS se aplican no solo a las grandes organizaciones, sino también a las pequeñas. Por ejemplo, todos los profesionales médicos deben cumplir con HIPAA. Todas las empresas que aceptan tarjetas de crédito deben cumplir con las PCI-DSS. De hecho, las prácticas médicas que aceptan tarjetas de crédito deben cumplir con ambos. Según su experiencia en la investigación en este laboratorio, ¿cuáles considera que son algunos de los principales desafíos para el cumplimiento de las organizaciones más pequeñas?
	* Las respuestas pueden variar. Hay muchos. Uno de los más grandes es la evaluación del cumplimiento. Las organizaciones no solo deben implementar las medidas requeridas, sino también demostrar que cumplen con la aprobación de auditorías de seguridad, someterse a evaluaciones de vulnerabilidad y compilar informes para respaldar el cumplimiento.