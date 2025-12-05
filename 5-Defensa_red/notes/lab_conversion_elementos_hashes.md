<title coding="utf-8">Convertir elementos en hashes (hashing)</title>

# Convertir elementos en _hashes_ (_hashing_)
# Objetivos
* Parte 1: Crear un hash de un Archivo de texto con OpenSSL.
* Parte 2: Verificar hashes.

# Trasfondo/Situación
Las funciones de hash son algoritmos matemáticos diseñados para tomar datos como entrada y generar una cadena de caracteres única de tamaño fijo, también conocida como hash. Diseñadas para que sean veloces, las funciones de hash son muy difíciles de revertir; es muy difícil recuperar los datos que crearon un hash determinado, basándose solamente en el hash. Otra de las propiedades importantes de las funciones hash es que hasta el cambio más pequeño realizado en los datos de entrada genera un hash completamente diferente.

Aunque se puede utilizar OpenSSL para generar y comparara hashes, hay otras herramientas disponibles. Algunas de estas herramientas están también incluidas en esta práctica de laboratorio.

# Recursos necesarios
* Máquina virtual Security Workstation

# Instrucciones
## Parte 1: Hashing de un archivo de texto con OpenSSL
OpenSSL se puede utilizar como una herramienta independiente para tareas de hash. Sigan los pasos que se indican a continuación para crear un hash de un archivo de texto:
1. Abra una ventana de terminal en la máquina virtual Security Workstation.
2. Como el archivo de texto desde el que se quiere generar el hash se encuentra en el directorio/home/analyst/lab.support.files/, cambie a ese directorio:
	```shell
	[analyst@secOps ~]$ cd /home/analyst/lab.support.files/
	```
3. Escriba el siguiente comando para listar en la pantalla el contenido del archivo de texto letter_to_grandma.txt:
	```shell
	[analyst@secOps lab.support.files]$ cat letter_to_grandma.txt
	Hi Grandma,
	I am writing this letter to thank you for the chocolate chip cookies you sent me. I got them this morning and I have already eaten half of the box! They are absolutely delicious!

	I wish you all the best. Love,
	Your cookie-eater grandchild.
	```
4. En la misma ventana de terminal ingrese el siguiente comando para generar un hash del archivo de texto. El comando utilizara SHA-2-256 como algoritmo de hashing para generar un hash del archivo de texto. El hash aparecerá en la pantalla después de que OpenSSL lo haya computado.
	```shell
	[analyst@secOps lab.support.files]$ openssl sha256 letter_to_grandma.txt
	SHA256(letter_to_grandma.txt)= deff9c9bbece44866796ff6cf21f2612fbb77aa1b2515a900bafb29be118080b
	```
	Observe el formato de la salida. OpenSSL muestra el algoritmo de hashing utilizado, SHA-256, seguido por el nombre del archivo utilizado como datos de entrada. El hash SHA-256 se muestra a si mismo después del signo igual.
5. Las funciones de hash son útiles para verificar la integridad de los datos independientemente de que se trate de una imagen, una canción o un simple archivo de texto. El cambio más pequeño produce un hash completamente diferente. Los hashes se pueden calcular antes y después de la transmisión, para luego compararlos. Si los hashes no coinciden, los datos fueron modificados durante la transmisión.
Modifiquemos el archivo de texto letter_to_grandma.txt y volvamos a calcular el hash MD5. Ejecute el siguiente comando para abrir nano, un editor de texto de línea de comandos.
	```shell
	[analyst@secOps lab.support.files]$ nano letter_to_grandma.txt
	```
	Utilizando nano, cambie la primera oración de ‘Hi Grandma’ a ‘Hi Grandpa’. Observe que solo estamos cambiando un carácter: la ‘m’ a una ‘p’. Después de hacer el cambio presione las teclas <CONTROL+X> para guardar el archivo modificado. Presione ‘Y’ (Sí) para confirmar el nombre y guardar el archivo. Presione la tecla <Intro> y saldrá de nano para continuar con el siguiente paso.
6. Ahora que se ha modificado y guardado el archivo, vuelva a ejecutar el comando para generar un hash SHA-2-256 del archivo.
	```shell
	[analyst@secOps lab.support.files]$ openssl sha256 letter_to_grandma.txt
	SHA256(letter_to_grandma.txt)= 43302c4500b7c4b8e574ba27a59d83267812493c029fd054c9242f3ac73100bc
	```
	* El hash nuevo, ¿es diferente al calculado en el punto 4? ¿Es muy diferente?
7. También se puede usar un algoritmo de hashing con una longitud de bits más larga, como SHA-2-512. Utilice el siguiente comando para generar un hash SHA-2-512 del archivo `letter_to_grandma.txt`:
	```shell
	[analyst@secOps lab.support.files]$ openssl sha512 letter_to_grandma.txt
	SHA512(letter_to_grandma.txt)= 7c35db79a06aa30ae0f6de33f2322fd419560ee9af9cedeb6e251f2f1c4e99e0bbe5d2fc32ce501468891150e3be7e288e3e568450812980c9f8288e3103a1d3
	[analyst@secOps lab.support.files]$
	```
8. Utilice sha256sum y sha512sum para generar un hash SHA-2-256 y SHA-2-512 del archivo `letter_to_grandma.txt`:
	```shell
	[analyst@secOps lab.support.files]$ sha256sum letter_to_grandma.txt
	43302c4500b7c4b8e574ba27a59d83267812493c029fd054c9242f3ac73100bc letter_to_grandma.txt
	
	[analyst@secOps lab.support.files]$ sha512sum letter_to_grandma.txt
	7c35db79a06aa30ae0f6de33f2322fd419560ee9af9cedeb6e251f2f1c4e99e0bbe5d2fc32ce501468891150e3be7e288e3e568450812980c9f8288e3103a1d3  letter_to_grandma.txt
	```
	* ¿Coinciden los hashes generados con sha256sum y sha512sum con los hashes generados en los puntos 6 y 7 respectivamente? Explique.
	__Nota__: SHA-2 es el estándar recomendado para hashing. Si bien SHA-2 aún no se ha visto comprometido de manera efectiva, las computadoras se vuelven cada vez más poderosas. Se espera que esta evolución natural pronto permita que los atacantes comprometan (vulneren) SHA-2.
	SHA-3 es el algoritmo de hashing más nuevo, y eventualmente será el reemplazo de la familia de hashes SHA-2.
	__Nota__: La máquina virtual Security Workstation solo soporta SHA-2-224, SHA-2-256 y SHA-2-512 (sha224sum, sha256sum y sha512sum respectivamente).

## Parte 2: Verificar hashes
Como se mencionó antes, un uso común de los hashes es verificar la integridad de los archivos. Sigan los pasos que se detallan a continuación para utilizar hashes SHA-2-256 y verificar la integridad de sample.img, un archivo que se descargó de Internet.
1. Junto con sample.img también se descargó sample.img_SHA256.sig, un archivo que contiene el SHA-2-256 calculado por el sitio web. En primer lugar, utilicen el comando cat para mostrar el contenido del archivo sample.img_SHA256.sig:
	```shell
	[analyst@secOps lab.support.files]$ cat sample.img_SHA256.sig
	c56c4724c26eb0157963c0d62b76422116be31804a39c82fd44ddf0ca5013e6a
	```
2. Utilice SHA256sum para calcular el hash SHA-2-256 del archivo sample.img:
	```shell
	[analyst@secOps lab.support.files]$ sha256sum sample.img
	c56c4724c26eb0157963c0d62b76422116be31804a39c82fd44ddf0ca5013e6a  sample.img
	```
	* ¿Se descargó el archivo sample.img sin ningún tipo de error? Explique.

__Nota__: Si bien comparar hashes un método relativamente robusto para detectar errores de transmisión, hay mejores formas de garantizar que el archivo no ha sido modificado. Diversas herramientas comogpg son un método mucho mejor para garantizar que el archivo descargado no ha sido modificado por terceros y que es, efectivamente, el archivo que el editor quería publicar.