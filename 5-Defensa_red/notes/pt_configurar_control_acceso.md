<title coding="utf-8">Configurar el Control de Acceso</title>

# Packet Tracer - Configurar el Control de Acceso
# Objetivos
* __Parte 1__: Configurar y usar las credenciales de autenticación AAA.
* __Parte 2__: Configurar y usar servicios de correo electrónico.
* __Parte 3__: Configurar y usar servicios FTP.

# Trasfondo/Situación
La autenticación y la autorización son procesos de seguridad distintos en el mundo de la administración de identidades y accesos (IAM: Identity and Access Management). La autenticación utiliza contraseñas y otros métodos de identificación para confirmar que los usuarios son quienes dicen ser. Por el contrario, la autorización asigna permisos de usuario a los recursos a los que el usuario tiene permitido acceder. En esta actividad de Packet Tracer (PT) configurará la autenticación y la autorización para los servicios de red, incluidos el acceso a la red inalámbrica, el correo electrónico y los servicios FTP.
__Nota__: Esta actividad se abre en modo Physical. Sin embargo, si puede también complétela en modo Logical.
__Nota__: La mayoría de las tareas en esta actividad son calificadas. Haga clic en Check Results en cualquier momento para ver los elementos de evaluación correctos e incorrectos.

# Instrucciones
## Parte 1: configurar y usar las credenciales de autenticación AAA
### Paso 1: configurar las cuentas de usuario en el servidor AAA.
1. Vaya a Headquarters y haga clic en Wiring Closetque es el chasis de servidor alto y negro en la esquina inferior izquierda.
2. En el rackdel lado derecho haga clic en el servidor AAA-RADIUS > solapa Services y luego en AAA en SERVICES.
3. Active el servicio AAA.
4. En User Setupagregue los siguientes nombres de usuario / contraseñas.
	* `user1` / `PASSuser1!`
	* `user2` / `PASSuser2!`

### Paso 2: Configure la autenticación inalámbrica en HQ-Laptop-1.
1. Vuelva a HQ y haga clic en HQ-Laptop-1. Se encuentra dos salas a la derecha de Wiring Closet.
2. Haga clic en la solapa Config y luego en Wireless0 dentro de INTERFACES.
3. En el cuadro SSID escriba HQ-INT.
4. En el área Authentication haga clic en WPA2.
5. En el cuadro User ID introduzca user1 e ingrese PASSuser1! en el cuadro Password.
6. En la sección IP Configuration hagaclic en DHCP. Qué pocos momentos para que se acepte la oferta de DHCP. Verifique que HQ-Laptop-1 haya recibido el direccionamiento IP y se le haya asignado una dirección en la red 192.168.50.0/24.
__Nota__: Puede ser necesario alternar entre Static y DHCP para forzar a Packet Tracer a converger en su configuración. Además, haga clic en Check Results para asegurarse de haber configurado correctamente el servidor AAA y la configuración inalámbrica en la computadora portátil. Haciendo clic en Check Results se puede además forzar a Packet Tracer a converger. Si todo está configurado correctamente, continúe con la configuración de HQ-Laptop-2 y luego regrese a HQ-Laptop-1 y compruebe su configuración IP. Este problema normalmente se resuelve.

### Paso 3: Configure la autenticación inalámbrica en HQ-Laptop-2.
1. Haga clic en HQ-Laptop-2que se encuentra en la esquina superior derecha de HQ.
2. Repita los pasos anteriores para configurar los ajustes inalámbricos de HQ-Laptop-2utilizando las credenciales de user2.
3. Verifique que HQ-Laptop-2 haya recibido el direccionamiento IP y se le haya asignado una dirección en la red 192.168.50.0/24.

## Parte 2: configurar y usar los servicios de correo electrónico
### Paso 1: activar los servicios de correo electrónico y configurar las cuentas de usuario de correo electrónico.
1. Navegue hacia el armario Wiring Closet.
2. En el rackdel lado derecho haga clic en el servidor Mail > solapa Services y luego en EMAIL en SERVICES.
3. Active los servicios SMTP y POP3.
4. Establezca el dominio en mail.cyberhq.com.
5. En User Setupagregue los siguientes nombres de usuario / contraseñas. Haga clic en el signo más (+) para agregar cada par.
	* `HQuser1` / `Cisco123!`
	* `HQuser2` / `Cisco123~`
	* `BRuser1` / `Cisco123-`
	* `BRuser2` / `Cisco123+`

### Paso 2: Configure los clientes de correo electrónico.
1. Vuelva a HQ y haga clic en PC 1-1que se encuentra en la esquina inferior.
2. Haga clic en la solapa Desktop > Email. Se abrirá la configuración Configure Mail.
3. Ingrese la siguiente informacion:
	* Your Name: `Suk-Yi`
	* Email Address: `HQuser1@mail.cyberhq.com`
	* Incoming & Outgoing Email Server(s): `mail.cyberhq.com`
	* User Name: `HQuser1`
	* Password: `Cisco123!`
4. Haga clic en Guardar.
5. Utilice la información de la tabla para configurar los ajustes de correo electrónico de 2-3, HQ-Laptop-1 y Net-Admin. La PC 2-3 está en la oficina debajo de la sala de conferencias. La PC Net-Admin está en Wiring Closet.

__PC/Laptop__|__Su nombre__|__Dirección correo electrónico__|__Nombre de usuario__|__Contraseña__|
:-|:-|:-:|:-:|:-:
2-3|Ajulo|`BRuser1@mail.cyberhq.com`|`BRuser1`|`Cisco123-`
HQ-Laptop-1|Malia|`BRuser2@mail.cyberhq.com`|`BRuser2`|`Cisco123+`
Net-Admin|Cisco|`HQuser2@mail.cyberhq.com`|`HQuser2`|`Cisco123~`

### Paso 3: Enviar un correo electrónico como Suk-Yi.
1. En la PC 1-1 haga clic en Compose.
2. Redacte un correo electrónico Ajulo en `BRuser1@mail.cyberhq.com`. Ingrese un asunto y un mensaje de correo electrónico de su elección. Al finalizar haga clic en Send.
__Nota__: Packet Tracer puede tardar varios segundos en converger antes de que vea el mensaje Send Success en la parte inferior de la ventana.
__Nota__: Packet Tracer no califica este paso. Verifique que completó correctamente este paso recibiendo el correo electrónico enviado por Suk-Yi en la PC 2-3 de Ajulo.
3. Vaya a la PC 2-3 de Ajulo. Si es necesario, haga clic en la solapa Desktop > Email.
4. Haga clic en Receive y lea el correo electrónico de Suk-Yi.

## Parte 3: configurar y usar los servicios FTP
### Paso 1: activar el servicio FTP.
1. Navegue hacia el armario Wiring Closet.
2. En el rackdel lado derecho haga clic en el servidor FTP > solapa Services y luego en FTP en SERVICES.
3. Active el servicio FTP .

### Paso 2: Cree las cuentas de usuario de FTP.
1. En User Setup introduzca los siguientes nombres de usuario, contraseñas y privilegios. Haga clic en Add para agregar cada usuario.
__Nota__: Asegúrese de que el nombre de usuario malia no incluya Delete como uno de los privilegios del usuario.

__Usuario__|__Contraseña__|__Privilegios de usuario__
:-|:-|:-:
`sukyi`|`cisco123`|RWDNL (Read, Write, Delete, Rename, List)
`ajulo`|`cisco321`|RWDNL (Read, Write, Delete, Rename, List)
`malia`|`cisco123`|RWNL (Read, Write, Rename, List)

2. Verifique que cada usuario se haya creado correctamente y cierre el servidor.

### Paso 3: Transfiera archivos entre Net-Admin y el servidor FTP.
1. Haga clic en la PC Net-Admin y luego en Desktop > Command Prompt.
2. Ingrese el comando ftp 192.168.75.2 para iniciar sesión en el servidor FTP y luego autentíquese con el nombre de usuario sukyi y la contraseña cisco123.
3. Ingrese el comando dir para listar los archivos en el servidor FTP.
4. Utilice el comando get para descargar aMessage.txt.
5. Salga de la sesión de FTP.
6. Cierre el Command Prompt, haga clic enText Editor y luego en File > Open. Abra el archivo descargado aMessage.txt.
	* ¿Cuál es el mensaje en el archivo?
7. Haga clic en File > New. Escriba un mensaje de texto de su elección.
8. Haga clic en File > Save y guarde el nuevo archivo como aMessage_new.txt. Cierre Text Editor.
9. Haga clic en Command Prompt y vuelva a iniciar sesión en el servidor FTP como usuario sukyi.
10. Utilice el comando put para subir aMessage_new.txt.
11. Salga de la sesión de FTP.

### Paso 4: Verifique que los privilegios de usuario de FTP funcionen según lo configurado.
1. Vuelva a HQ y haga clic en HQ-Laptop-1, solapa Desktop > Command Prompt.
2. Inicie sesión en el servidor FTP en 192.168.75.2 con el nombre de usuario malia y la contraseña cisco123.
3. Utilice el comando delete para intentar eliminar el archivo recién cargado aMessage_new.txt.
	* ¿Pudo eliminar el archivo del servidor FTP? Explique.
4.  Utilice el comando rename para intentar cambiar el nombre de aMessage_new.txt a aMessage_rename.txt.
	```shell
	ftp> rename aMessage_new.txt aMessage_rename.txt
	```
	* ¿Pudo cambiar el nombre del archivo desde el servidor FTP?
5. Salga de la sesión de FTP y cierre la ventana HQ-Laptop-1.

<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />