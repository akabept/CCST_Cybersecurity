# Solución de problemas del gateway predeterminado
* Tabla de direccionamiento

__Dispositivo__|__Interfaz__|__Dirección IP__|__Máscara de subred__|__Default Gateway__
-:|-:|-:|-:|-:
__R1__|G0/0|192.168.10.1|255.255.255.0|N/A
__R1__|G0/1|192.168.11.1|255.255.255.0|N/A
__S1__|VLAN 1|192.168.10.2|255.255.255.0|
__S2__|VLAN 1|192.168.11.2|255.255.255.0|
__PC1__|NIC|192.168.10.10|255.255.255.0|
__PC2__|NIC|192.168.10.11|255.255.255.0|
__PC3__|NIC|192.168.11.10|255.255.255.0|
__PC4__|NIC|192.168.11.11|255.255.255.0|

## Objetivos
* Parte 1: Verificar el registro de la red y descartar problemas
* Parte 2: Implementar, verificar y registrar las soluciones

## Aspectos básicos
Para que un dispositivo se comunique en varias redes, debe estar configurado con una dirección IP, una máscara de subred y un gateway predeterminado. La puerta de enlace predeterminada se usa cuando el host desea enviar un paquete a un dispositivo de otra red. La dirección de puerta de enlace predeterminada es generalmente la dirección de la interfaz del enrutador que está conectada a la red local a la que está conectado el host. En esta actividad, terminará de registrar la red. Luego, verificará el registro de la red mediante la prueba de la conectividad completa y la solución de problemas. Los métodos de solución de problemas que usted usará constan de los siguientes pasos:

1. Verifique el registro de la red y usar pruebas para aislar problemas.
2. Determine una solución apropiada para un problema determinado.
3. Implemente la solución.
4. Realice pruebas para verificar que se haya solucionado el problema.
5. Registre la solución.

A lo largo de sus estudios de CCNA, encontrará distintas descripciones del método de solución de problemas, así como distintas formas de probar y registrar problemas y soluciones. Esto es intencional. No existe un estándar o una plantilla establecida para la solución de problemas. Cada organización desarrolla procesos y estándares de registro exclusivos (incluso si ese proceso consiste en no tener ninguno). Sin embargo, todas las metodologías de resolución de problemas efectivas generalmente incluyen los pasos anteriores.

__Nota__: Si es competente con las configuraciones de puerta de enlace predeterminadas, esta actividad puede parecer más complicada de lo que debería ser. Lo más probable es que pueda descubrir y solucionar todos los problemas de conectividad más rápido que si siguiera estos procedimientos. No obstante, a medida que avance con sus estudios, las redes y los problemas que encuentre serán cada vez más complejos. En tales situaciones, la única forma eficaz de descartar y solucionar problemas es aplicar un enfoque metódico como el que se usa en esta actividad.

## Instrucciones
### Parte 1: Verificar el registro de la red y descartar problemas
En la parte 1 de esta actividad, completará el registro y realizará pruebas de conectividad para detectar problemas. Además, determinará la solución adecuada y la implementará en la parte 2.

#### Paso 1: Verifique el registro de la red y descartar cualquier problema.
1. Para que pueda probar una red con eficacia, debe contar con el registro completo. Observe que falta determinada información en la tabla de direccionamiento. Complete la tabla de direccionamiento con la información de gateway predeterminado que falta para los switches y las PC.
2. Pruebe la conectividad a los dispositivos en la misma red. Al descartar y corregir cualquier problema de acceso local, puede probar mejor la conectividad remota, con la seguridad de que la conectividad local funciona.

Un plan de verificación puede ser tan simple como una lista de pruebas de conectividad. Use las siguientes pruebas para verificar la conectividad local y descartar cualquier problema de acceso. El primer problema ya se registró, pero debe implementar y verificar la solución durante la parte 2.

##### Registro de prueba y verificación

__Prueba__|__¿Se realizó correctamente?__|__Problemas__|__Solución__|__Verificado__
:-|:-|:-|:-|:-
PC1 a PC2|No|IP en la PC1|Cambiar la  IP de la PC1
PC1 a S1|||
PC1 a R1|||

__Nota__: La tabla es un ejemplo; debes crear tu propio documento. Puede usar lápiz y papel para dibujar una tabla, o puede utilizar un editor de texto o una hoja de cálculo. Consulte al instructor si necesita más orientación.

3. Pruebe la conectividad a los dispositivos remotos (p. ej., de la PC1 a la PC4) y registre cualquier problema. Esto se conoce frecuentemente como "conectividad completa". Esto significa que la política de red permite que todos los todos los dispositivos en una red tengan conectividad plena.

__Nota__: La prueba de conectividad remota puede no ser posible todavía, porque primero debe resolver los problemas de conectividad local. Una vez que solucione dichos problemas, vuelva a este paso y pruebe la conectividad entre redes.

#### Paso 2: Determine cuál es la solución adecuada para el problema.
1. Con sus conocimientos sobre la forma en que operan las redes y sus aptitudes para configurar dispositivos, busque la causa del problema. Por ejemplo, el S1 no es la causa del problema de conectividad entre la PC1 y la PC2. Las luces de enlace son de color verde, y ninguna configuración en el S1 provocaría que no pase el tráfico entre la PC1 y la PC2. Por lo tanto, el problema debe de estar en la PC1, en la PC2 o en ambas.
2. Verifique el direccionamiento del dispositivo para asegurarse de que coincida con el registro de la red. Por ejemplo, la dirección IP para la PC1 es incorrecta, como se verificó con el comando ipconfig.
3. Sugiera una solución con la que usted crea que se solucionará el problema y regístrela. Por ejemplo, cambiar la dirección IP de la PC1 para que coincida con el registro.

__Nota__: A menudo hay más de una solución. Sin embargo, es una práctica recomendada para la resolución de problemas implementar y verificar una solución a la vez. Implemente más de una solución podría presentar problemas adicionales en una situación más compleja.

### Parte 2: Implemente, verifique y registre las soluciones
En la parte 2 de esta actividad, implementará las soluciones que identificó en la parte 1. Luego, verificará si la solución funcionó. Es posible que deba volver a la parte 1 para terminar de descartar todos los problemas.

#### Paso 1: Implemente soluciones para abordar los problemas de conectividad.
Consulte el registro en la parte 1. Elija el primer problema e implemente la solución que sugirió. Por ejemplo, corrija la dirección IP en la PC1.

#### Paso 2: Verifique si ahora el problema está resuelto.
1. Verifique si la solución que propuso solucionó el problema realizando la prueba que usó para identificarlo. Por ejemplo, ¿la PC1 puede ahora hacer ping a la PC2?
2. Si el problema se solucionó, indíquelo en el registro. Por ejemplo, en la tabla anterior, con colocar una simple marca de verificación en la columna "Verificado" sería suficiente.

#### Paso 3: Verifique si se resolvieron todos los problemas.
1. Si todavía tiene un problema pendiente con una solución que aún no se implementó, vuelva al paso 1 de la parte 2.
2. Si se solucionaron todos los problemas actuales, ¿también solucionó todos los problemas de conectividad remota (por ejemplo, que la PC1 pueda hacer ping a la PC4)? Si la respuesta es negativa, vuelva al paso 1c de la parte 1 para probar la conectividad remota.