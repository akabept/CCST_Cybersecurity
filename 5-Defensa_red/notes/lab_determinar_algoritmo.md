<title coding="utf-8">Determinar el algoritmo de cifrado que se utilizará</title>

# Práctica de laboratorio. Determinar el algoritmo de cifrado que se utilizará
# Objetivos
* __Parte 1__: Proteger los datos personales.
* __Parte 2__: Proteger los datos inalámbricos.
* __Parte 3__: Proteger los datos corporativos entre sitios.

# Trasfondo/Situación
Internet se utiliza por una variedad de motivos, incluidos el trabajo, el juego, el entretenimiento y más. Hay varios protocolos, algoritmos y métodos disponibles para asegurar el acceso en línea.

Esta práctica de laboratorio incluye tres escenarios. En cada escenario completará algunos pasos y luego investigará en Internet para responder preguntas, incluyendo cuál es el mejor algoritmo de cifrado para cada escenario.

# Recursos necesarios
* Una PC Windows con acceso a Internet.

# Instrucciones
## Parte 1: Proteger los datos personales
En esta situación usted es un estudiante que usa una computadora compartida. Desea guardar información confidencial en esta computadora pero no desea que otros accedan a esos datos.

### Paso 1: Cree un archivo de texto
1. Abra el Explorador de archivos buscándolo o usando la combinación de teclas `Windows + E`.
2. Vaya a una ubicación de trabajo y cree una nueva carpeta con el nombre que desee.
__Nota__: Para mostrar las extensiones de archivo haga clic en `Ver > Opciones`. En la ventana Opciones de carpeta haga clic en la solapa `Ver` y luego desmarque `Ocultar extensiones para tipos de archivos conocidos`.
3. Dentro de la carpeta haga clic derecho en el espacio vacío y haga clic en `Nuevo > Documento de texto`.
4. Cambie el nombre a `File-1.txt` y haga doble clic para abrir el archivo.
5. Ingrese algún texto, como "Esto es una prueba", y luego guarde y cierre el archivo.

### Paso 2: Analice cómo podría proteger este archivo
Suponga que de alguna manera debe proteger este archivo para que no sea leído, robado o alterado.
* ¿Cómo podría hacer eso?
* ¿Qué algoritmo de cifrado (por ejemplo DES, 3DES o AES) debe utilizar si pudiera cifrar el archivo?  ¿Por qué?

### Paso 3: Descargue e instale 7-Zip
1. Busque `7-Zip download` en Internet y descargue este programa de compresión gratuito de código abierto.
2. Instale 7-Zip.

### Paso 4: inspeccionar los formatos de archivo y los métodos de cifrado de 7-Zip
1. En la ventana Explorador de archivos haga clic con el botón derecho en `File-1.txt` y seleccione `7-Zip > Agregar al archivo...`.
2. En el menú desplegable junto a Formato de archivo, elija el formato zip.
3. 7-Zip proporciona dos métodos de cifrado para el formato zip. _ZipCrypto_ es un método.
* ¿Cuál es el otro método?
* ¿Cuáles son las diferencias entre cada método? (Pista: consulte la Ayuda).
* ¿Qué método debería usar si quisiera tener el cifrado más seguro?

### Paso 5: Comprima y cifre el archivo File-1
1. Con la ventana `Agregar al archivo` aún abierta, ingrese la contraseña que desee en el campo `Ingresar contraseña`.
2. Haga clic en `Aceptar` para comprimir y cifrar el archivo. Esto crea un nuevo archivo archivado llamado `File-1.zip`.
3. Para eliminar permanentemente el archivo original haga clic en él y presione `Shift-Delete`. Se le pedirá que confirme que quiere elimine el archivo permanentemente. Haga clic en `Sí`.

### Paso 6: Descifre el archivo cifrado y comprimido _File-1.zip_
1. Con el Explorador de archivos aún abierto, haga clic con el botón derecho en `File-1.zip` y luego elija `7-Zip > Extraer aquí`.
2. Aparece la ventana `Ingresar contraseña`. Introduzca su contraseña para descifrar `File-1.txt` y haga clic en `Aceptar`.
3. Abra el archivo `File-1.txt` para verificar que su mensaje original esté allí.

## Parte 2: Proteger los datos inalámbricos
En este escenario usted tiene una pequeña empresa con base en el hogar que brinda soporte de TI a los ciudadanos locales. Un nuevo cliente ha solicitado que los configure con el mejor acceso inalámbrico. Específicamente, hacen lo siguiente:
* Una gran casa de tres pisos de 5000 pies cuadrados
* Varios dispositivos personales antiguos y nuevos, incluidos teléfonos inteligentes, tablets, computadoras, televisores inteligentes, Oculus 2, impresoras y más.
* Cuatro nuevos dispositivos habilitados para Wi-Fi 6 (802.11ax).

Después de investigar un poco decide recomendar el sistema Linksys Atlas Pro 6, Dual-Band Mesh Wi-Fi 6 System 3-Pack. Este sistema debería admitir los dispositivos enumerados y proporcionar la seguridad inalámbrica requerida.

Los routers wifi generalmente ofrecen varias opciones de seguridad para cifrar datos inalámbricos. ¿Qué opción de cifrado debería usar en este escenario?

### Paso 1: Investigue el router inalámbrico de Linksys
1. Busque en Internet "Linksys Atlas Pro 6, Dual-Band Mesh Wi-Fi 6 System". Su búsqueda proporcionará muchos enlaces posibles. Sin embargo, elija el enlace proporcionado por Linksys.com.
2. Revise las características del router para ver si cumple con las especificaciones requeridas.

### Paso 2: Investigue las opciones de seguridad
El sistema Linksys Atlas ofrece tres funciones de seguridad.
* ¿Cuáles son las funciones de seguridad disponibles con este sistema?
* ¿Qué opción de seguridad deberían usar estos clientes?

## Parte 3: Proteger los datos corporativos entre sitios
En este escenario trabaja para una pequeña organización con varios sitios que están interconectados a través de Internet pública. Es fundamental que los datos corporativos entre los sitios estén protegidos mientras viajan por Internet.

Las redes privadas virtuales (VPN) se utilizan comúnmente entre las sucursales y los sitios centrales para proteger los datos y garantizar la autenticación de origen. La organización utiliza Cisco Integrated Series Routers (ISRs) para admitir VPN IPsec de sitio a sitio entre los sitios. Internet Protocol Security o IPsec es un marco de trabajo que permite especificar qué mecanismo de cifrado, autenticación e integridad utilizar.

En esta parte tiene la tarea de recomendar los mejores algoritmos de encriptación y autenticación para implementar en el Cisco ISR 4321 utilizando IOS XE 17. Para ello deberá investigar varios protocolos admitidos por VPN con IPSec.

### Paso 1: Investigar los algoritmos de cifrado IPsec
1. Realice una búsqueda en Internet de “Security for VPNs with IPsec Configuration Guide, Cisco IOS XE 17”.
2. Elija el primer enlace de cisco.com para abrir Book Table of Contents.
3. Haga clic en el enlace Configuring Security for VPNs with IPsec.
4. Desplácese hacia abajo hasta Supported Standards para responder las siguientes preguntas.
	* ¿Qué algoritmos de cifrado criptográfico admiten las VPN con IPsec?

### Paso 2: Investigar los algoritmosde autenticación e integridad de IPsec
En la sección Supported Standards , ¿qué algoritmos de hash se utilizan para autenticar datos y verificar la integridad?

### Paso 3: Recomendar un algoritmo de encriptación y autenticación
Para satisfacer las necesidades de la empresa, ¿qué algoritmo de cifrado y algoritmo de hash debería recomendar para garantizar una protección adecuada para los datos que atraviesan Internet?