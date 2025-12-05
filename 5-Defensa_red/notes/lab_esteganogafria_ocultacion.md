<title coding="utf-8">Uso de esteganografía para ocultar datos</title>

# Práctica de laboratorio. Uso de esteganografía para ocultar datos
# Objetivos
Utilice la esteganografía para ocultar un documento en un archivo JPEG.

# Trasfondo/Situación
La ventaja de la esteganografía con respecto a la criptografía es que el mensaje secreto no atrae ninguna atención especial. Nadie sabría nunca que una imagen contenía un mensaje secreto al ver el archivo, ya sea electrónicamente o en copia impresa. En esta práctica de laboratorio utilizará Steghide, un programa de esteganografía de código abierto, para ocultar un archivo de datos dentro de un archivo de imagen.

# Recursos necesarios
PC con CSE-LABVM instalado en Virtualbox

# Instrucciones
## Paso 1: Abra una ventana de terminal en CSE-LABVM.
1. Inicie CSE-LABVM.
2. Haga doble clic en el icono de Terminal para abrir un terminal.

## Paso 2: Revise los archivos que se utilizarán para la esteganografía.
1. Ingrese el comando cd Downloads/ para cambiar al directorio Downloads y luego liste el contenido del directorio.
	```shell
	cisco@labvm:~$ cd Downloads/
	cisco@labvm:~/Downloads$ ls -l
	total 472
	drwxr-xr-x 8 cisco cisco   4096 Jan 27 01:30 jcryptool
	drwxrwxr-x 3 cisco cisco   4096 Mar 18 18:11 john
	-rw-rw-rw- 1 cisco cisco 455357 Mar 22 16:10 keyboard.jpg
	drwxrwxr-x 6 root  root    4096 Mar 18 17:46 lynis
	-rw-rw-r-- 1 cisco cisco   9912 Mar 22 16:13 secret.odt
	cisco@labvm:~/Downloads$
	```
	Ocultará el contenido del archivo `secret.odt` dentro del archivo `keyboard.jpg`.
2. Ingrese el comando `libreoffice secret.odt &` para abrir el archivo `secret.odt` en LibreOffice.
	```shell
	cisco@labvm:~/Downloads$ libreoffice secret.odt &
	```
	* ¿Cuál es el mensaje en el archivo `secret.odt`?
3. Haga clic en File > Exit LibreOffice para salir de LibreOffice y cerrar el archivo.
4. En la ventana de terminal presione Enter para obtener un nuevo símbolo del sistema y luego ingrese el comando gimp keyboard.jpg & para abrir el archivo "keyboard.jpg" en GIMP.
	```shell
	cisco@labvm:~/Downloads$ gimp keyboard.jpg &
	```
5. Haga clic en File > Quit para salir de GIMP y cerrar el archivo.
6. En la ventana de terminal, presione Enter para obtener un nuevo símbolo del sistema.

## Paso 3: Utilice Steghide para integrar el contenido del archivo secret.odt dentro del archivo teclado.jpg.
1. En el símbolo del sistema, ingrese el siguiente comando steghide. Cuando se le solicite una contraseña, utilice Cisco. Reintroduzca la contraseña cuando se le solicite.
	```shell
	cisco@labvm:~/Downloads$ steghide embed -cf keyboard.jpg -ef secret.odt
	Enter passphrase: Cisco
	Re-Enter passphrase: Cisco
	embedding "secret.odt" in "keyboard.jpg"... done
	cisco@labvm:~/Downloads$
	```
2. Abra los archivos secret.odt y keyboard.jpg.
	* ¿Se modificaron estos archivos?
	
## Paso 4: Verifique que secret.odt esté oculto en el archivo keyboard.jpg.
1. Ingrese el comando steghide info keyboard.jpg , escriba y en el símbolo del sistema, ingrese la clave de cifrado Cisco y luego presione Enter.
	```shell
	cisco@labvm:~/Downloads$ steghide info keyboard.jpg
	"keyboard.jpg":
	  format: jpeg
	  capacity: 26.6 KB
	¿Intentar obtener información sobre los datos incrustados? (y/n) y
	Enter passphrase: Cisco
	  embedded file "secret.odt":
	    size: 9.7 KB
	    encrypted: rijndael-128, cbc
	    compressed: yes
	cisco@labvm:~/Downloads$
	```

## Paso 5: Extraiga el archivo secret.odt del archivo keyboard.jpg.
1. Ingrese el comando steghide extract -sf keyboard.jpg, ingrese la clave de cifrado Cisco y luego escriba y en el símbolo del sistema.
	```shell
	cisco@labvm:~/Downloads$ steghide extract -sf keyboard.jpg
	Enter passphrase: Cisco
	the file "secret.odt" does already exist. overwrite ? (y/n) y
	wrote extracted data to "secret.odt".
	cisco@labvm:~/Downloads$
	```
2. Abra el archivo extraído secret.odt con LibreOffice.
	* ¿Pudo abrir el archivo? ¿El mensaje secreto es el mismo que antes?