<title coding="utf-8">Uso de algoritmos de cifrado clásicos y modernos</title>

# Práctica de laboratorio. Uso de algoritmos de cifrado clásicos y modernos
# Objetivos
* __Parte 1__: usar un algoritmo de cifrado clásico.
* __Parte 2__: usar un algoritmo de cifrado simétrico moderno.
* __Parte 3__: usar un algoritmo de cifrado asimétrico moderno.

# Trasfondo/Situación
La criptografía moderna se basa principalmente en la teoría matemática y la práctica de la informática. Los algoritmos criptográficos están diseñados en torno a supuestos de complejidad computacional, lo que los hace difíciles, si no imposibles, de romper para un actor de la amenaza. JCrypTool es una herramienta de software de código abierto independiente de la plataforma y forma parte del proyecto de código abierto CrypTool. JCrypTool es una plataforma de aprendizaje electrónico ampliable que presenta la criptografía, el criptoanálisis y la seguridad informática de forma moderna y fácil de usar. Esta práctica de laboratorio utilizará JCrypTool para introducir algoritmos criptográficos clásicos, modernos, simétricos y asimétricos.

# Recursos necesarios
* PC con CSE-LABVM instalado en Virtualbox

# Instrucciones
## Parte 1: Use un algoritmo de cifrado clásico
En criptografía, un cifrado es un algoritmo para realizar el cifrado o el descifrado. Un cifrado es un conjunto de pasos (un algoritmo) para realizar tanto un cifrado, como el correspondiente descifrado. Los primeros cifrados en criptografía se diseñaron para permitir el cifrado y el descifrado a mano, mientras que los que se desarrollan y utilizan en la actualidad solo son posibles mediante el uso de computadoras. Los algoritmos clásicos son los inventados hasta alrededor de los años 50.

Un cifrado César, también conocido como cifrado por desplazamiento, es una de las técnicas de cifrado más simples y conocidas. El método lleva el nombre de Julio César, quien lo utilizó en su correspondencia privada. César es un tipo de cifrado de sustitución en el que cada letra del texto es reemplazada por una letra a un número fijo de posiciones del alfabeto. Por ejemplo, con un desplazamiento a la izquierda de 3, la letra D se reemplazaría por la A, la E se convertiría en B, etc.

### Paso 1: Inicie CSE-LABVM
### Paso 2: Abra y explore JCrypTool
1. Haga doble clic en el icono de jcryptool en el escritorio. Se abre el directorio jcryptool.
2. Haga doble clic en el icono de JCrypTool.

La herramienta tiene cuatro ventanas:
* __File Explorer__: se utiliza para localizar, abrir y guardar archivos.
* __Help__: se utiliza para localizar archivos de ayuda y tutoriales.
* __Currently Open File__: contiene archivos para operar con herramientas criptográficas. El archivo `unsaved001.txt` debería estar abierto.
* __Crypto Explorer__: proporciona acceso a herramientas criptográficas. De manera predeterminada, Crypto Explorer no se muestra. Para abrirlo haga clic en `Window > Show View > Crypto Explorer`.

### Paso 3: utilice el algoritmo César para cifrar un mensaje de texto.
1. Para comenzar, deberá completar el archivo abierto actualmente con el mensaje que desea cifrar. Resalte todo el texto en el archivo `unsaved001.txt` y reemplácelo con el siguiente mensaje:
	`LA CRIPTOGRAFÍA ES DIVERTIDA. ¿PUEDE LEER ESTE MENSAJE SECRETO?`
2. En Crypto Explorer, haga clic en Classic si no está expandido y haga doble clic en Caesar.
3. En la sección Operation seleccione Encrypt si aún no está seleccionado.
4. En la sección Alphabet verifique que las opciones Select alphabet y Upper Latin (A-Z) estén seleccionadas. Si no, selecciónelos ahora.
5. En la sección Key cambie Enter key using a character a K. Deje todas las demás opciones con sus valores predeterminados.
6. Haga clic en Finish para guardar las opciones y cifrar los datos.
7. Un nuevo archivo llamado `out001.txt` se abre con el mensaje cifrado.

### Paso 4: Descifrar el texto cifrado con el algoritmo César.
1. Mueva el archivo `out001.txt` a la ventana File Explorer, si es necesario. Esto garantiza que Crypto Explorer utilizará este archivo como archivo activo. También puede cerrar el archivo `unsaved001.txt`.
2. En la solapa Crypto Explorer haga doble clic nuevamente en el algoritmo Caesar.
3. En la sección Operation seleccione Decrypt.
4. Seleccione la misma configuración para descifrar el texto cifrado actual en el archivo de salida `out001.txt`.
5. Haga clic en Finish para guardar las opciones y descifrar los datos.
6. Cierre todos los archivos en File Explorer. No hay necesidad de guardarlos.

### Paso 5: Cambie la configuración del algoritmo César.
1. Cree un nuevo archivo de texto de entrada seleccionando `File > New > Empty File en Texteditor`.
2. Escriba el siguiente mensaje: `La criptografía es divertida. ¿Puede leer este mensaje secreto?`.
3. En la solapa `Crypto Explorer` haga doble clic nuevamente en el algoritmo _Caesar_.
4. `Encrypt` ya debería estar seleccionado. En `Select alphabet` establezca el valor en `Upper and lower Latin (A-Z, a-z)`. Para la cantidad de desplazamiento a lo largo del alfabeto establezca el valor en `13`.
5. Haga clic en `Finish` para guardar las opciones y cifrar los datos.
6. Cierre el archivo en `File Explorer`. No hay necesidad de guardarlo.

Exploración adicional: experimente por su cuenta con Caesar y otros algoritmos de criptografía clásicos para ver cómo funcionan.

## Parte 2: usar un algoritmo de cifrado simétrico moderno
En esta parte, utilizará un algoritmo de cifrado simétrico moderno. Una de las versiones más populares de un algoritmo criptográfico moderno es Advanced Encryption Standard (AES). AES es un cifrado criptográfico simétrico en software y hardware que se utiliza en todo el mundo para cifrar datos sensibles. El cifrado AES requiere una clave de cifrado para controlar el proceso de cifrado y descifrado. Este algoritmo se considera un protocolo criptográfico sólido basado en su complejidad y una longitud de clave de 128 bits.

### Paso 1: utilice el cifrado AES para cifrar un mensaje de texto.
1. Cree un nuevo archivo de texto de entrada seleccionando `File > New > Empty File en Texteditor`.
2. Escribe el siguiente mensaje: `La criptografía es divertida. ¿Puede leer este mensaje secreto?`
3. En la solapa `Crypto Explorer` pulse en `Symmetric` para expandirlo si fuera necesario y luego haga doble clic en `AES`.
4. Utilice la siguiente configuración.
	* Operation: `Encrypt`
	* Key source: `Custom key`
	* Key length: `128`
	* Key (hex): `AA 00 00 00 00 00 00 00 00 00 00 00 00 00 00 FF`
	* Mode: `(ECB) Electronic Codebook`
	* Padding: `PKCS#5 Padding`
5. Haga clic en `Finish`. Se abre un archivo de salida con la extensión `.bin`. Verá cuatro filas con 16 valores hexadecimales en cada fila. El texto cifrado se muestra a la derecha para cada fila.

### Paso 2: utilice AES para descifrar un mensaje de texto.
1. Haga doble clic en `AES` nuevamente.
2. Cambie `Operation` a `Decrypt` y luego utilice la configuración del paso 1 para descifrar el texto cifrado.
3. Haga clic en `Finish` para guardar las opciones y descifrar los datos. Se abre un archivo de salida con la extensión `.bin` conteniendo el texto descifrado.
4. Cierre todos los archivos.

## Parte 3: usar un algoritmo de cifrado asimétrico moderno
En esta parte utilizará un algoritmo de cifrado asimétrico moderno. A diferencia del cifrado simétrico, el cifrado asimétrico cifra y descifra los datos mediante dos claves criptográficas separadas pero conectadas matemáticamente. Estas claves se conocen como 'clave pública' y 'clave privada'. Para que una persona envíe un mensaje cifrado a otra persona mediante cifrado asimétrico, le solicita una clave pública y luego la utiliza para cifrar un mensaje con un algoritmo acordado. La otra persona descifra el mensaje con su clave privada. El mensaje no se puede descifrar con la clave pública.

### Paso 1: Utilice el cifrado asimétrico RSA para cifrar un archivo de texto.
1. Cree un nuevo archivo de texto de entrada seleccionando `File > New > Empty File en Texteditor`.
2. Escribe el siguiente mensaje: `La criptografía es divertida. ¿Puede leer este mensaje secreto?`.
3. En `Crypto Explorer` haga clic en `Asymmetrical` para expandirlo y luego haga doble clic en `RSA` para abrir la configuración del algoritmo.
4. Utilice la siguiente configuración:
	* Operation: `Encrypt`
	* Keystore: haga clic en `Create a new pair in the keystore`.
	* En el cuadro de diálogo New key pair introduzca lo siguiente:
		* Contact name: `John Smith`
		* Password: `Secret`
		* Deje todas las demás entradas como predeterminadas.
5. Haga clic en `Finish`.
6. Haga clic en `Finish` en el cuadro de diálogo `RSA - encryption` para cifrar los datos. Se abre un archivo de salida con la extensión `.bin` con el texto cifrado.

### Paso 2: utilice el cifrado asimétrico de RSA para descifrar un archivo de texto.
1. Haga doble clic en `RSA`.
2. Seleccione `Decrypt` para la operación.
3. Seleccione `Key = “John Smith” – public key – 1024`.
4. Haga clic en `Finish` para descifrar el texto cifrado.
5. Introduzca la contraseña `Secret`. Haga clic en `Aceptar`.
