<title coding="utf-8">Exploración del cifrado de archivos y datos</title>

# Packet Tracer - Exploración del cifrado de archivos y datos
# Objetivos
* Parte 1: Descubra las credenciales de la cuenta FTP para Mary
* Parte 2: Suba datos confidenciales mediante FTP
* Parte 3: Descubra las credenciales de la cuenta FTP para Bob
* Parte 4: Descargue datos confidenciales mediante FTP
* Parte 5: Descifre el contenido de un archivo confidencial

# Antecedentes
En esta actividad, tendrá acceso a contenidos cifrados de varios archivos y transferirá un archivo a través de Internet a un servidor FTP centralizado. Luego, otro usuario descargará a continuación el archivo desde el servidor FTP y descifrará el contenido de los archivos. La asignación de direcciones IP, la configuración de red y las configuraciones de los servicio ya están completas. Usará los dispositivos cliente en las diferentes regiones geográficas para transferir un archivo con datos cifrados a otro dispositivo.

Para descifrar texto y archivos en esta actividad, utilizará OpenSSL. OpenSSL es un proyecto de código abierto que proporciona un kit de herramientas robusto, comercial y completo para los protocolos de Seguridad de capa de transporte (Transport Layer Security, TLS) y Capa de sockets segura (Secure Sockets Layer, SSL). También es una biblioteca de criptografía de uso general.

__Nota__: Si bien actualmente OpenSSL es la biblioteca de criptografía obligada, el uso que se presenta en esta práctica de laboratorio NO se recomienda para lograr una protección sólida. A continuación, se presentan dos problemas de seguridad con esta práctica:
* El método que se describe en esta práctica utiliza una función de derivación de claves débil. La ÚNICA medida de seguridad es una contraseña muy fuerte.
* El método que se describe en esta práctica no garantiza la integridad del archivo de texto.

Esta actividad debe utilizarse solo como herramienta de aprendizaje. Los métodos aquí presentado NO se deben emplear para asegurar datos realmente sensibles.

# Recursos
* ElCSE-LABVM instalada en VirtualBox
	__Nota__: Se recomienda que utilice CSE-LABVM para las tareas de descifrado en esta actividad. El CSE-LABVM se instaló durante el laboratorio: instalación de una máquina virtual en una computadora personal.

# Instrucciones
## Parte 1: Descubra las credenciales de cuenta de FTP para Mary
La computadora portátil de Mary se llama Laptop BR-1 en la sucursal. Mary tiene un documento de texto en su computadora portátil que contiene la información de inicio de sesión de FTP en forma cifrada. El contenido debe estar descifrado para permitir el acceso al servidor BR que se encuentra en el armario de cableado de la sucursal.

### Paso 1: Acceda al documento de texto de la PC portátil de Mary.
1. Pulse en Laptop BR-1 > Desktop (Escritorio) > Text Editor(Editor de texto).
2. En la ventana del editor de texto, pulse en File (Archivo) > Open(Abrir).
3. Pulse en el documento ftplogin.txt y haga clic en OK.

### Paso 2: Descrifre la Información de la cuenta FTP de Mary.
1. Seleccione todo el texto del archivo maryftplogin.txt y cópielo.
2. Inicie CSE-LABVM.
3. Haga doble clic en el icono de Terminal para abrir uno.
4. Utilice el siguiente comando para descifrar el contenido del archivo y revelar la información de inicio de sesión FTP para Mary.
	```shell
	cisco @ labvm: ~ $ echo 'U2FsdGVkX1 + sKwL7uceALGKqAQ78WWown3ok73zicO8GLYu2SpMvLEwCB7HsyRC3MeimUjiXRCLwOSSahAraUrnEtkClGK4tytP9hludc6k =' OpenSSL aes-256-cbc -pbkdf2 -a -d
	```
	Este comando envía el texto cifrado a la aplicación OpenSSL. La opción `aes-256-cbc` le dice a OpenSSL que use el sistema de cifrado avanzado con una longitud de clave de 256 bits y cadena de bloque de cifrado. La opción `pbkdf2` habilita la función de derivación de clave basada en contraseña 2 que aplica un código de autenticación de mensaje basado en hash o HMAC a la contraseña junto con sal. La opción `-a` le indica a OpenSSL que debe cifrar el mensaje cifrado con un método de codificación diferente a Base64 antes de guardar el resultado en un archivo. La opción `-d` le dice a la aplicación que descifre los datos.

5. Cuando se le solicite la contraseña de descifrado, utilice `maryftp123`. Introduzca la contraseña de descifrado `aes-256-cbc`: `maryftp123`.
	* ¿Cuál es el nombre de usuario y contraseña para la facturación de FTP de Mary?
	
## Parte 2: Suba datos confidenciales mediante FTP
Mary trabaja para una agencia de tarjetas de crédito y debe enviarle un archivo que contenga los datos de algunos clientes. En la Parte 2, verificará que los datos estén cifrados antes de cargarlos en el servidor BR.

### Paso 1: Visualice al documento confidencial en la PC portátil de Mary.
1. Regrese a la computadora portátil BR-1. Abra el editor de texto, si es necesario, y haga clic en Archivo> Abrir.
2. Haga clic en el documento clientinfo.txt y luego haga clic en OK.
	* ¿En qué forma se encuentran los datos?

### Paso 2: Conéctese al el servidor BR.
1. Cierre     la ventana del Editor de Texto y despues haga clic en Command Prompt.
2. En el indicador, ingrese el comando ftp 10.0.3.30 para conectarse al servidor BR.
3. Utilice las credenciales de Mary que descifró antes para autenticar.

### Paso 3: Subir un archivo al servidor FTP.
1. En el indicador     de ftp> , introduzca el comando dir para ver los archivos almacenados actualmente en el servidor.
2. Utilice el comando put para cargar el archivo PublicInfo.txt al servidor.
3. Con el indicador ftp>, introduzca el comando dir y verifique que el archivo clientinfo.txtahora se encuentre en el servidor.
4. Introduzca el comando quit para salir de la sesión FTP.
	* Si los delincuentes cibernéticos capturaran la transferencia de archivos que cruzan Internet, ¿qué estaría en texto claro?

## Parte 3: Descubra las credenciales de la cuenta FTP para Bob
Bob necesita acceder al contenido del archivo que Mary almac}enó en el servidor BR para verificar la información del cliente. Al igual que Mary, Bob necesita descifrar su información de inicio de sesión de FTP para acceder al servidor BR y descargar el archivo.

### Paso 1: Acceda al documento de texto de la PC portátil de Bob.
1. En la sucursal, haga clic en Laptop BR-2 y abra el Editor de texto.
2. En la ventana del editor de texto, haga clic en File (Archivo) > Open (Abrir).
3. Haga clic en el documento bobftplogin.txt y luego clic en OK.

### Paso 2: Descrifre la Información de la cuenta de FTP de Bob.
1. Seleccione     todo el texto del archivo ftplogin.txt y cópielo.
2. Vuelva a la ventana de terminal en CSE-LABVM.
3. Utilice el siguiente comando para descifrar el contenido del archivo y revelar la información de inicio de sesión de FTP para Bob.
```shell
cisco @ labvm: ~ $ echo 'U2FsdGVkX1 / + 3jGTemCqs3e4dK8 + b0xfXJiq4eoU0lQgRV9aZQPqJCBsYJWc9lDQwiB2svhiWSUVhCRS5qBrjgZDZFqrqxrqqqqqqqqqqqqqqqqqqqqqqqqqqJJJJJJJJJJJJJ OpenSSL aes-256-cbc -pbkdf2 -a -d
```
4. Cuando se le solicite la contraseña de descifrado, utilice `bobftp123`. Introduzca la contraseña de descifrado `aes-256-cbc`: `bobftp123`
	* ¿Cuál es el nombre de usuario y la contraseña para la cuenta de FTP de Bob?

## Parte 4: Descargue datos confidenciales mediante FTP
En esta parte, descargará y descifrará los datos confidenciales almacenados en el servidor BR.

### Paso 1: Conéctese al el servidor BR.
1. En Branch Office en la computadora portátil BR-2, cierre la ventana del editor de texto y haga clic en el Command Prompt.
2. En el prompt, ingrese el comando ftp 10.0.3.30 para conectarse al servidor BR.
3. Utilice las credenciales de Bob que descifró antes para autenticar.

### Paso 2: Descargue el archivo en la computadora de Bob.
1. En el indicador de ftp>, introduzca el comando `dir` para ver los archivos almacenados actualmente en el servidor.
2. Utilice el comando get para descargar el archivo clientinfo.enc del servidor.
3. Introduzca el comando quit para salir de la sesión FTP.
4. En el prompt `C:\>`, introduzca el comando `dir` y verifique que el archivo clientinfo.enc ahora se encuentre en el servidor.
	* Si los delincuentes cibernéticos capturaran la transferencia de archivos que cruzan Internet, ¿qué estaría en texto claro?

## Parte 5: Descifre el contenido de un archivo confidencial
En esta parte, descifrará el archivo clientinfo.enc.

### Paso 1: Obtenga la clave de descifrado.
Ahora que Bob tiene el archivo, debe descifrarlo para poder leerlo. Anteriormente, Mary le envió a Bob un correo electrónico con la clave de descifrado del archivo. Utilice el programa de correo electrónico para recuperar la clave de cifrado del archivo clientinfo.enc.
1. Cierre el Command Prompt y despues haga clic en VPN.
2. Haga clic en el correo electrónico con el asunto «Decryption Key» y registre la clave de descifrado a continuación.
	* ¿Cuál es la clave de descifrado para acceder a la información confidencial en el archivo clientinfo.enc?

### Paso 2: Descife el contenido del archivo clientinfo.enc.
1. Cierre la ventana de correo electrónico y haga clic en Editor de texto.
2. En la ventana del editor de texto, haga clic en Archivo> Abrir, y luego haga clic en el documento clientinfo.enc y finalmente en Aceptar.
3. Seleccione     todo el texto del archivo clientinfo.txt y cópielo.
4. En CSE-LABVM, haga clic en el botón Menú y haga clic en la pluma del editor de texto.
5. Haga clic en Editar> Pegar y luego en Archivo> Guardar.
6. Guarde el archivo con el nombre clientinfo.enc.
7. Cierre la Pluma.
8. En la terminal, ingrese el comando ls para verificar que clientinfo.enc esté en el directorio actual. De lo contrario, navegue hasta el directorio donde se almacena clientinfo.enc.
9. Utilice el siguiente comando para descifrar el archivo clientinfo.enc.
	```shell
	Cisco @ labvm: ~ $ OpenSSL aes-256-cbc -pbkdf2 -a -d -in clientinfo.enc -out clientinfo.txt
	```
10. Cuando se le solicite la contraseña de descifrado, utilice la contraseña que descubrió en el correo electrónico de María.
introduzca la contraseña de descifrado aes-256-cbc:
	```shell
	cisco @ labvm: ~ $
	```
11. Ingrese el comando ls para ver que se haya agregado un nuevo archivo, clientinfo.txt, al directorio.
12. Utilice cualquier método que desee para abrir el archivo clientinfo.txt para ver el contenido descifrado.
¿Cuál es el primer nombre listado en el archivo de clientinfo.txt ?