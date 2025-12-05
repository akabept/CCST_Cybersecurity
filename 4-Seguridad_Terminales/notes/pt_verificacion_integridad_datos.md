<title coding="utf-8">Verificación de la Integridad de Datos y Archivos</title>

# Packet Tracer - Verificación de la Integridad de Datos y Archivos
# Objetivos
* Parte 1: Recuperar archivos después de un ataque cibernético
* Parte 2: Uso de hash para verificar la integridad de los archivos
* Parte 3: Uso de HMAC para verificar la integridad de los archivos

# Antecedentes
En esta actividad, verificará la integridad de varios archivos mediante hashes para garantizar que los archivos no se hayan alterado. Si se sospecha que algunos archivos están alterados, se enviarán a la computadora de Sally para un análisis posterior. La asignación de direcciones IP, la configuración de red y las configuraciones de los servicio ya están completas. Utilizará los dispositivos cliente para verificar y transferir cualquier archivo sospechoso.

# Recursos
* El CSE-LABVM instalado en VirtualBox
__Nota__: Se recomienda que utilice CSE-LABVM para verificar los hash de archivos MD5 en esta actividad. El CSE-LABVM se instaló durante la práctica de laboratorio: instale una máquina virtual en una computadora personal.

# Instrucciones
## Parte 1: Recuperar archivos después de un ataque cibernético
Los datos del cliente deben estar protegidos y no deben ser modificados por personal no autorizado. Al aplicar hash a los datos antes y después de archivarlos, puede saber si han cambiado incluso un carácter o incluso un bit porque los hash no coinciden. En esta parte, intentará recuperar archivos de una copia de respaldo después de un ataque cibernético.

### Paso 1: Acceda al servidor FTP desde la computadora de Mike.
1. Pulse en Sucursal y luego en Laptop BR-1.
2. Pulse en la ficha Escritorio y luego pulse en Navegador web.
3. Introduzca la URL http://www.cisco.corp y pulse en Ir.
	__Nota__: Packet Tracer puede tardar hasta un minuto en converger. Pueden hacer clic en Fast Forward Time (Adelantar el tiempo) (Alt+D) para acelerar el proceso.
5. Pulse en el enlace para descargar los archivos más actuales.

### Paso 2: Copie los valores hash de la última vez que se archivaron los archivos.
Necesita restaurar los archivos que faltan desde un servidor de respaldo ubicado en HQ. Pero primero, necesita los hash de los archivos almacenados para garantizar su integridad.
1. Introduzca la URL http://www.cisco.corp y pulse en Ir.
2. Haga clic en el enlace para ver los archivos más recientes y sus hashes.
3. Seleccione y copie todo el contenido.
4. Abra CSE-LABVM y haga clic en Menú > Pluma del editor de texto.
5. Pegue el contenido del portapapeles en el documento en blanco. Utilizará estos hash para validar si un archivo está dañado.

### Paso 3: Descargue los archivos cliente a la computadora de Mike
1. De vuelta en Packet Tracer, cierre el navegador web en la PC de Mike.
2. Haga clic en Command Prompt. Conéctese al servidor FTP de HQ ingresando ftp hq.corp en el indicador.
3. Introduzca el nombre de usuario de mike y la contraseña cisco123.
4. En el indicador de ftp>, introduzca el comando dir para ver los archivos almacenados actualmente en el servidor.
5. Descargue los seis archivos de cliente (NEclients.txt, NWclients.txt, Nclients.txt, SEclients.txt, SWclients.txt y Sclients.txt) en la PC de Mike. El ejemplo del primer archivo se muestra aquí:
```shell
ftp> get NEclients.txt
Leyendo el archivo NEclients.txt de hq.corp:
Transferencia de archivos en curso...
[Transfer complete - 584 bytes]
584 bytes copiados en 0.05 seg (11680 bytes/seg)
```
6. Después de descargar todos los archivos, introduzca el comando quit en la petición de ingreso ftp>.
7. Con el indicador PC>, introduzca el comando dir y verifique que los archivos cliente ahora se encuentren en la computadora deMike.

## Parte 2: Usar hash para verificar la integridad de los archivos
En esta parte, utilice CSE-LABVM para hacer hash del contenido de los archivos que descargó. Luego, comparará el nuevo hash con el antiguo para ver si los datos han cambiado. Cualquier archivo que haya cambiado desde que se archivó se enviará a Sally para que pueda investigar los cambios en otro momento.

### Paso 1: Compruebe los hashes en los archivos cliente de la computadora de Mike.
1. Cierre     el Command Prompt, haga clic en el Editorde Texto.
2. Haga clicen el primer documento NEclients.txty luego haga clic en Aceptar     .
3. Copie     todo el contenido del documento de texto.
4. Abra CSE-LABVM.
5. Haga doble     clic en el icono de Terminal para abrir un terminal.
6. Utilice el eco -n 'file-contenido' | El comando md5 sum crea un hash para validar los datos en el archivo NEclients.txt. Pegue el contenido del portapapeles entre comillas simples.
	```shell
	cisco @ labvm: ~ $ echo -n 'file-contenido' | md5sum
	```
7. Compare el valor hash creado aquí con los valores hash que copió en el documento de texto anterior.
	* ¿Son los dos valores hash para NEclients.txt iguales?
8. Haga un hash del contenido de los cinco archivos restantes hasta que uno de los valores no coincida con el hash calculado.
	* ¿Qué archivo fue manipulado y tiene un hash incorrecto?

### Paso 2: Escale el ataque cibernético a la supervisora de Mike, Sally.
1. Regrese a Packet Tracer y cierre el editor de texto.
2. Haga clic en Correo electrónico y luego en Redactar. Escriba un correo electrónico y envíelo a sally@branch.corp para informarle que el servidor de archivos ha sido hackeado.

### Paso 3: Descargue el archivo sosprechoso en la computadora de Sally.
1. Vaya al sitio de HQ y haga clic en HQ-Laptop-1.
2. Haga clic en la ficha Escritorio> Símbolo del sistema y escriba ftp hq.corp para conectarse al servidor FTP de HQ.
3. Introduzca el nombre de usuario de `sally` y la contraseña `cisco321`.
4. En el indicador de ftp>, introduzca el comando dir para ver los archivos almacenados actualmente en el servidor FTP remoto.
5. Descargue el archivo que se encontró alterado en el Paso 1 de la Parte 3.
6. Con el indicador ftp> , introduzca el comando quit.
7. En el indicador `C:\>` , ingrese el comando dir y verifique que el archivo del cliente manipulado esté ahora en HQ-Laptop-1 para que Sally lo analice en el futuro.

## Parte 3: Usar HMAC para verificar la integridad de los archivos
Bob es el CFO de una pequeña empresa y realiza un seguimiento de todas las finanzas. En esta parte, computará y verificará un código de autenticación de mensajes (HMAC) basado en hash de un archivo crítico para asegurarse de que sean los mismos datos desde la última vez que se utilizó el archivo. HMAC requiere una clave secreta para poder validar la integridad del archivo.
1. Haga clic en la computadora portátil de Bob, que es HQ-Laptop-2.
2. Haga clic en la pestañana Escritorio > Command Prompt, luego ingrese el comando dir y verifique que el archivo crítico denominado renta.txt esté en la computadora portátil. Cierren     la ventana del Command Prompt cuando hayan terminado.
3. Haga clic en Editor de texto y luego en Archivo > Abrir.
4. Haga clic en el documento income.txt y luego haga clic en Aceptar.
5. Seleccione y copie todo el contenido del documento.
6. En CSE-LABVM, haga clic en el botón Menú y luego en Pluma del editor de texto. Haga clic en Editar y en Pegar.
7. Haga clic en Archivo y haga clic en Guardar. Guarde el archivo con el nombre ingresos.txt. Cierre el archivo.
8. En una ventana de terminal en la VM de CSE-LABVM, utilice el siguiente comando para crear un HMAC para el archivo ingresos.txt. La clave secreta es cisco123.
	```shell
	cisco @ labvm: ~ $ OpenSSL dgst -sha256 -hmac cisco123 ingreso.txt
	```
	* ¿Cuál es el HMAC calculado para el contenido del archivo?
	* ¿Por qué el uso de HMAC es más seguro que el hash general?
	* ¿El hash de HMAC para el archivo ingreso.txt coincide con el hash original que copió en el archivo de texto en CSE-LABVM?