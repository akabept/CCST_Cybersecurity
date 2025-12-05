# Packet Tracer - Configuración inicial del enrutador
## Objetivos
* Parte 1: Verificar la configuración predeterminada del enrutador
* Parte 2: Configurar y verificar la configuración inicial del enrutador
* Parte 3: Guardar el archivo de configuración en ejecución

## Aspectos básicos
En esta actividad, realizará tareas básicas de configuración del enrutador. Asegurará el acceso a la CLI y al puerto de la consola utilizando contraseñas encriptadas y de texto sin formato. También configurará mensajes para los usuarios que inician sesión en el enrutador. Estos avisos advierten a los usuarios no autorizados que el acceso está prohibido. Por último, verificará y guardará la configuración en ejecución.

## Instrucciones
### Parte 1: Verifique la configuración predeterminada del enrutador
#### Paso 1: Establezca una conexión de consola al R1.
1. Elija un cable de consola de las conexiones disponibles.
2. Haga clic en PCA y seleccione RS 232.
3. Haga clic en R1 y seleccione Console.
4. Haga clic en PCA > ficha Desktop > Terminal.
5. Haga clic en OK y presione Enter. Ahora puede configurar R1.

#### Paso 2: Ingrese al modo con privilegios y examinar la configuración actual.
Puede acceder a todos los comandos del enrutador en el modo EXEC privilegiado. Sin embargo, debido a que muchos de los comandos privilegiados configuran parámetros operativos, el acceso privilegiado se debe proteger con contraseña para evitar el uso no autorizado.

1. Ingrese al modo EXEC privilegiado introduciendo el comando enable.
Abra una ventana de configuración
```shell
Router> enable
Router#
```
Observe que la petición de entrada cambia en la configuración para reflejar el modo EXEC con privilegios.

2. Ingrese el comando show running-config.
```shell
Router# show running-config
```
* ¿Cuál es el nombre de host del enrutador?
* ¿Cuántas interfaces Fast Ethernet tiene el enrutador?
* ¿Cuántas interfaces Gigabit Ethernet tiene el enrutador?
* ¿Cuántas interfaces seriales tiene el enrutador?
* ¿Cuál es el rango de valores que se muestra para las líneas vty?

3. Muestre el contenido actual de la NVRAM.
```shell
Router# show startup-config
startup-config is not present
```
* ¿Por qué el enrutador responde con el mensaje startup-config is not present?

### Parte 2: Configure y verifique la configuración inicial del enrutador
Para configurar los parámetros de un enrutador, quizá deba pasar por diversos modos de configuración. Observe cómo cambia la solicitud a medida que navega por los modos de configuración de IOS.

#### Paso 1: Configure los parámetros iniciales del R1.
__Nota__: Si tiene dificultades para recordar los comandos, consulte el contenido de este tema.

Abra una ventana de configuración
1. Configure R1 como el nombre del enrutador (hostname).
2. Configure el mensaje de texto del día: Unauthorized access is strictly prohibited.
3. Encripte todas las contraseñas de texto no cifrado.

Utilice las siguientes contraseñas:
1)     EXEC privilegiado, encriptado: itsasecret
2)     Consola: letmein

#### Paso 2: Verifique los parámetros iniciales del R1.
1. Para verificar los parámetros iniciales, observe la configuración del R1.
* ¿Qué comando utiliza?

2. Salga de la sesión de consola actual hasta que vea el siguiente mensaje:
```shell
R1 con0 is now available
Press RETURN to get started.
```

3. Presione ENTER; debería ver el siguiente mensaje:
```shell
Unauthorized access is strictly prohibited.
User Access Verification
Password:
```
* ¿Por qué todos los enrutadors deben tener un mensaje del día (MOTD)?
* Si no se le solicita una contraseña antes de llegar al indicador EXEC del usuario, ¿qué comando de línea de consola olvidó configurar?

4. Introduzca las contraseñas necesarias para regresar al modo EXEC con privilegios.
* Si configura más contraseñas en el enrutador, ¿se muestran como texto no cifrado o en forma cifrada en el archivo de configuración? Explique.

### Parte 3: Guarde el archivo de configuración en ejecución
#### Paso 1: Guarde el archivo de configuración en la NVRAM.
Abra una ventana de configuración
1. Ha configurado la configuración inicial para R1. Ahora haga una copia de respaldo del archivo de configuración en ejecución en la NVRAM para garantizar que no se pierdan los cambios realizados si el sistema se reinicia o se apaga.
* ¿Qué comando introdujo para guardar la configuración en la NVRAM?
* ¿Cuál es la versión más corta e inequívoca de este comando?
* ¿Qué comando muestra el contenido de la NVRAM?

2. Verifique que todos los parámetros configurados estén registrados. De lo contrario, analice el resultado y determine qué comandos no se ejecutaron o se ingresaron incorrectamente. También puede hacer clic en Check Results en la ventana de instrucción.

#### Paso 2: Opcional: Guarde el archivo de configuración de inicio en flash.
Si bien aprenderá más sobre cómo administrar el almacenamiento flash en un enrutador en capítulos posteriores, es posible que le interese saber que, como procedimiento de respaldo adicional, puede guardar su archivo de configuración de inicio en flash. De manera predeterminada, el enrutador seguirá cargando la configuración de inicio desde la NVRAM, pero si esta se daña, puede restablecer la configuración de inicio copiándola de la memoria flash.

Complete los siguientes pasos para guardar la configuración de inicio en la memoria flash.
1. Examine el contenido de la memoria flash mediante el comando show flash:
```shell
R1# show flash
```
* ¿Cuántos archivos hay almacenados actualmente en la memoria flash?
* ¿Cuál de estos archivos cree que es la imagen de IOS?
* ¿Por qué cree que este archivo es la imagen de IOS?

2. Utilice los siguientes comandos para guardar el archivo de configuración de inicio en la memoria flash:
```shell
R1# copy startup-config flash
Destination filename [startup-config]
```
El enrutador le solicita almacenar el archivo en flash utilizando el nombre entre paréntesis. Si la respuesta es afirmativa, presione ENTER; de lo contrario, escriba un nombre adecuado y presione la tecla ENTER.

3. Utilice el comando show flash para verificar que el archivo de configuración de inicio esté guardado en la memoria flash.