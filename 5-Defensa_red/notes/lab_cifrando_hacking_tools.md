<title coding="utf-8">Cifrar y descifrar datos con una herramienta de hacker</title>

# Práctica de laboratorio. Cifrar y descifrar datos con una herramienta de hacker
# Objetivos
* __Parte 1__: Crear y cifrar archivos.
* __Parte 2__: Recuperar contraseñas de archivos Zip cifrados.

# Trasfondo/Situación
Supongan que trabajan en una gran corporación que tiene una política corporativa relacionada con los medios extraíbles. Específicamente, estipula que solo se pueden copiar documentos comprimidos cifrados en unidades Flash USB portátiles.

En esta situación hipotética, el Director Financiero (Chief Financial Officer, CFO) está en un viaje de negocios y se ha puesto en contacto con ustedes frenético pidiéndoles ayuda para resolver una emergencia. Mientas estaba de viaje por negocios, trató de descomprimir documentos importantes desde un archivo zip cifrado en una unidad USB. Sin embargo, la contraseña provista para abrir el archivo zip no es válida. El CFO se puso en contacto con ustedes para ver si podían hacer algo.

__Nota__: El escenario proporcionado es simple y solo sirve como ejemplo.

Es posible que haya algunas herramientas disponibles para recuperar contraseñas olvidadas. Esto es especialmente cierto en situaciones como esta, en las que el analista especializado en ciberseguridad podría obtener la información pertinente del CFO. La información pertinente podría ser la longitud de la contraseña y una idea de cuál podría ser. Conocer la información pertinente es radicalmente útil cuando se está tratando de recuperar una contraseña.

Entre algunos ejemplos de utilidades y programas para recuperar contraseñas podemos mencionar los siguientes: hashcat, John the Ripper y Lophtcrack. En nuestro caso utilizaremos __fcrackzip__, una utilidad simple de Linux para recuperar las contraseñas de archivos zip cifrados.

Tengan presente que los ciberdelincuentes pueden utilizar esas mismas herramientas para averiguar contraseñas desconocidas. Aunque no podrían acceder a cierta información pertinente, con el tiempo es posible que averigüen las contraseñas para abrir archivos zip cifrados. El tiempo necesario depende de la solidez y de la longitud de la contraseña. Las contraseñas más largas y más complejas (combinación de diferentes tipos de caracteres) son más seguras.

En esta práctica de laboratorio:
* Cree y cifre archivos de texto de ejemplo.
* Descifre el archivo zip cifrado.

__Nota__: Esta práctica de laboratorio debe utilizarse solo con fines instructivos. Los métodos aquí presentado NO se deben emplear para asegurar datos realmente sensibles.

# Recursos necesarios
* Máquina virtual Security Workstation

# Instrucciones
## Parte 1: Crear y cifrar archivos
En esta parte crearán algunos archivos de texto que se utilizarán para generar los archivos zip cifrados del próximo paso.

### Paso 1: Cree archivos de texto.
1. Inicie la màquina virtual Security Workstation.
2. Abra una ventana del terminal. Verifiquen que están en el directorio de inicio de analyst. De lo contrario, ingrese cd ~ en el prompt del terminal.
3. Cree una carpeta nueva de nombre Zip-Files con el comando mkdir Zip-Files.
4. Ingrese a ese directorio con el comando cd Zip-Files .
5. Ingrese lo siguiente texto para crear tres archivos de texto.
	```shell
	[analyst@secOps Zip-Files]$ echo This is a sample text file > sample-1.txt
	[analyst@secOps Zip-Files]$ echo This is a sample text file > sample-2.txt
	[analyst@secOps Zip-Files]$ echo This is a sample text file > sample-3.txt
	```
6. Utilice el comando ls para verificar que los archivos han sido creados.
	```shell
	[analyst@secOps Zip-Files]$ ls -l
	total 12
	-rw-r--r-- 1 analyst analyst 27 May 13 10:58 sample-1.txt
	-rw-r--r-- 1 analyst analyst 27 May 13 10:58 sample-2.txt
	-rw-r--r-- 1 analyst analyst 27 May 13 10:58 sample-3.txt
	```

### Paso 2: Comprimir y cifrar los archivos de texto.
A continuación crearemos varios archivos comprimidos cifrados con contraseñas de diversas longitudes. Para hacerlo, cifraremos los tres archivos de texto con la utilidad zip .
1. Utilice el siguiente comando para crear un archivo zip cifrado de nombre file-1.zip que contenga los tres archivos de texto:
	```shell
	[analyst@secOps Zip-Files]$ zip –e file-1.zip sample*
	```
2. Cuando se le solicite una contraseña, introduzca una de un carácter de su elección. En el ejemplo se introdujo la letra B . Introduzcan la misma letra cuando se les solicite verificarla.
	```shell
	[analyst@secOps Zip-Files]$ zip -e file-1.zip sample-*
	Enter password:
	Verify password:
	  adding: sample-1.txt (stored 0%)
	  adding: sample-2.txt (stored 0%)
	  adding: sample-3.txt (stored 0%)
	```
3. Repita el procedimiento para crear los siguientes 4 archivos
	* __file-2.zip__ usando una contraseña de 2 caracteres de su elección. En nuestro ejemplo utilizamos `R2`.
	* __file-3.zip__ usando una contraseña de 3 caracteres de su elección. En nuestro ejemplo utilizamos `0B1`.
	* __file-4.zip__ usando una contraseña de 4 caracteres de su elección. En nuestro ejemplo utilizamos `Y0Da`.
	* __file-5.zip__ usando una contraseña de 5 caracteres de su elección. En nuestro ejemplo utilizamos `C-3P0`.
4. Utilice el comando ls -l f* para verificar que se hayan creado todos los archivos comprimidos.
	```shell
	[analyst@secOps Zip-Files]$ ls -l f*
	-rw-r--r-- 1 analyst analyst 643 May 13 11:01 file-1.zip
	-rw-r--r-- 1 analyst analyst 643 May 13 11:02 file-2.zip
	-rw-r--r-- 1 analyst analyst 643 May 13 11:03 file-3.zip
	-rw-r--r-- 1 analyst analyst 643 May 13 11:03 file-4.zip
	-rw-r--r-- 1 analyst analyst 643 May 13 11:03 file-5.zip
	```
5. Intente abrir un zip utilizando una contraseña incorrecta, tal como se muestra.
	```shell
	[analyst@secOps Zip-Files]$ unzip file-1.zip
	Archive:  file-1.zip
	[file-1.zip] sample-1.txt password:
	password incorrect--reenter
	password incorrect--reenter:
	   skipping: sample-1.txt            incorrect password
	[file-1.zip] sample-2.txt password:
	password incorrect--reenter:
	password incorrect--reenter:
	   skipping: sample-2.txt            incorrect password
	[file-1.zip] sample-3.txt password:
	password incorrect--reenter:
	password incorrect--reenter:
	   skipping: sample-3.txt            incorrect password
	```

## Parte 2: Recuperar contraseñas de archivos Zip cifrados
En esta parte utilizará la utilidad _fcrackzip_ para recuperar contraseñas olvidadas de archivos comprimidos cifrados. Fcrackzip busca archivos cifrados en cada archivo zip dado para adivinar la contraseña utilizando métodos de fuerza bruta.

El motivo por el cual creamos archivos zip con contraseñas de diversas longitudes es ver si la longitud de la contraseña tiene alguna influencia sobre el tiempo necesario para descubrirla.

### Paso 1: Introducción a _fcrackzip_
En la ventana del terminal, introduzcan el comando `fcrackzip –h` para ver las opciones del comando asociadas.

En nuestros ejemplos utilizaremos las opciones de comando `–v`,`-u` y `-l`. La opción `-l` se incluirá a lo último porque especifica la posible longitud de la contraseña. Tienen plena libertad de experimentar con otras opciones.

### Paso 2: Recuperar contraseñas utilizando _fcrackzip_
1. Ahora intente recuperar la contraseña del archivo `file-1.zip`. Recuerden que se utilizó una contraseña de un carácter para cifrar el archivo. Por lo tanto, use el siguiente comando `fcrackzip`:
	```shell
	[analyst@secOps Zip-Files]$ fcrackzip -vul 1-4 file-1.zip
	found file 'sample-1.txt', (size cp/uc     39/    27, flags 9, chk 5754)
	found file 'sample-2.txt', (size cp/uc     39/    27, flags 9, chk 5756)
	found file 'sample-3.txt', (size cp/uc     39/    27, flags 9, chk 5757)
	
	
	PASSWORD FOUND!!!!: pw == B
	```
	* ¿Cuánto tiempo es necesario para descubrir la contraseña?
__Nota__: La longitud de la contraseña se podría haber definido en menos de 1 a 4 caracteres.
2. Ahora intente recuperar la contraseña del archivo `file-2.zip`. Recuerden que se utilizó una contraseña de dos caracteres para cifrar el archivo. Por lo tanto, use el siguiente comando `fcrackzip`:
	```shell
	[analyst@secOps Zip-Files]$ fcrackzip –vul 1-4 file-2.zip
	found file 'sample-1.txt', (size cp/uc     39/    27, flags 9, chk 5754)
	found file 'sample-2.txt', (size cp/uc     39/    27, flags 9, chk 5756)
	found file 'sample-3.txt', (size cp/uc     39/    27, flags 9, chk 5757)
	
	PASSWORD FOUND!!!!: pw == R2
	```
	* ¿Cuánto tiempo es necesario para descubrir la contraseña?
3. Repita el procedimiento y recupere la contraseña del archivo `file-3.zip`. Recuerden que se utilizó una contraseña de tres caracteres para cifrar el archivo. Cronometren la operación para averiguar cuánto tiempo se necesita para descubrir una contraseña de 3 letras. Use el siguiente comando `fcrackzip`:
	```shell
	[analyst@secOps Zip-Files]$ fcrackzip –vul 1-4 file-3.zip
	found file 'sample-1.txt', (size cp/uc     39/    27, flags 9, chk 5754)
	found file 'sample-2.txt', (size cp/uc     39/    27, flags 9, chk 5756)
	found file 'sample-3.txt', (size cp/uc     39/    27, flags 9, chk 5757)
	
	PASSWORD FOUND!!!!: pw == 0B1
	```
	* ¿Cuánto tiempo es necesario para descubrir la contraseña?
4. ¿Cuánto tiempo toma averiguar una contraseña de cuatro caracteres? Repita el procedimiento y recupere la contraseña del archivo `file-4.zip`. Cronometre la operación para ver cuánto tiempo toma descubrir la contraseña con el siguiente comando `fcrackzip`:
	```shell
	[analyst@secOps Zip-Files]$ fcrackzip –vul 1-4 file-4.zip
	found file 'sample-1.txt', (size cp/uc     39/    27, flags 9, chk 5754)
	found file 'sample-2.txt', (size cp/uc     39/    27, flags 9, chk 5756)
	found file 'sample-3.txt', (size cp/uc     39/    27, flags 9, chk 5757)
	checking pw X9M~                                   
	
	PASSWORD FOUND!!!!: pw == Y0Da
	```
	* ¿Cuánto tiempo es necesario para descubrir la contraseña?
5. ¿Cuánto tiempo toma descifrar una contraseña de cinco caracteres? Repita el procedimiento y recupere la contraseña del archivo `file-5.zip`. La contraseña tiene una longitud de cinco caracteres; por lo tanto debemos definir la opción `-l` del comando en 1-5. Nuevamente, cronometre la operación para saber cuánto tiempo toma descubrir la contraseña con el siguiente comando `fcrackzip`:
	```shell
	[analyst@secOps Zip-Files]$ fcrackzip –vul 1-5 file-5.zip
	found file 'sample-1.txt', (size cp/uc     39/    27, flags 9, chk 5754)
	found file 'sample-2.txt', (size cp/uc     39/    27, flags 9, chk 5756)
	found file 'sample-3.txt', (size cp/uc     39/    27, flags 9, chk 5757)
	checking pw C-H*~                                  
	
	PASSWORD FOUND!!!!: pw == C-3P0
	```
	* ¿Cuánto tiempo es necesario para descubrir la contraseña?
6. Recuperar una contraseña de 6 caracteres utilizando `fcrackzip`
Aparentemente, se necesita más tiempo para descubrir contraseñas más largas y, por lo tanto, son más seguras. Sin embargo, una contraseña de 6 caracteres no desalentará a un ciberdelincuente.
	* ¿Cuánto tiempo creen que demoraría fcrackzip para descubrir una contraseña de 6 caracteres?
	* Para responder esa pregunta cree un archivo de nombre `file-6.zip` utilizando una contraseña de 6 caracteres de su elección. En nuestro ejemplo utilizamos `JarJar`.
	```shell
	[analyst@secOps Zip-Files]$ zip –e file-6.zip sample*
	```
7. Repita el procedimiento para recuperar la contraseña del archivo file-6.zip con el siguiente comando fcrackzip:
	```shell
	[analyst@secOps Zip-Files]$ fcrackzip –vul 1-6 file-6.zip
	```
	* ¿Cuánto tiempo demora fcrackzip para descubrir la contraseña?
	* La simple verdad es que las contraseñas más largas son más seguras porque se necesita más tiempo para descubrirlas. ¿Qué longitud recomendarías para que una contraseña sea segura?