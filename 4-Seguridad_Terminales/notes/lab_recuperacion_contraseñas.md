<title coding="utf-8">Recuperación de contraseñas</title>

# Recuperación de contraseñas
# Objetivos
* Utilice una herramienta para recuperar las contraseñas de los usuarios.
* Cambiar una contraseña de usuario a una contraseña más segura.

# Trasfondo/Situación

Existen cuatro cuentas de usuario: Alice, Bob, Eve y Eric, en un sistema Linux. También está la cuenta de superusuario Cisco. Las cuentas de usuario en la VM no están destinadas a ser seguras, ya que la VM es un entorno de espacio aislado y no está diseñada para aplicaciones del mundo real. En esta práctica de laboratorio, utilizará John the Ripper, una herramienta de recuperación de contraseña de código abierto, para recuperar las contraseñas de las cinco cuentas.

# Recursos necesarios
* PC con CSE-LABVM instalada en VirtualBox

# Instrucciones 
## Parte 1: abra una ventana de terminal en CSE-LABVM.
1. Inicie CSE-LABVM.
2. Haga doble clic en el icono de Terminal para abrir un terminal.

## Parte 2: combinar contraseñas y nombres de usuario en un archivo de texto.
1. Ingrese el siguiente comando para cambiar el directorio donde se encuentra John el Destripador:
```shell
cisco @ labvm: ~ $ cd Descargas / john / run
cisco @ labvm: ~ / Downloads / john / run $
```
2. Utilice el comando `unshadow` para combinar el archivo `/etc/passwd` donde se almacenan las cuentas de usuario, con el archivo `/etc/shadow` donde se almacenan las contraseñas de usuarios, en un nuevo archivo denominado `mypasswd`. Introduzca `contraseña` como contraseña de superusuario, si se le solicita. La sintaxis básica para el comando es la siguiente:
```shell
cisco@ubuntu:~/Downloads/john-1.8.0/run$ sudo ./unshadow /etc/passwd /etc/shadow > mypasswd
[sudo] password for cisco: password
cisco @ labvm: ~ / Downloads / john / run $
```

## Parte 3: Ejecute John the Ripper para recuperar las contraseñas.
1. Para ver que las contraseñas aún no se han recuperado (descifrado), ingrese el comando./john --show mypasswd.
```shell
cisco@labvm:~/Downloads/john/run$ ./john --show mypasswd
Directorio creado: /home/cisco/.john
0 hashes decontraseña descifrados, quedan 5
cisco @ labvm: ~ / Downloads / john / run $
```
2. El programa, John el Destripador, utiliza un diccionario predefinido llamado `password.lst` con un conjunto estándar de reglas predefinidas para administrar el diccionario y recuperar todos los _hashes_ de la contraseña de _md5crypt_ y el tipo de cifrado. En el la línea de comando, introduzca el siguiente comando para recuperar las contraseñas almacenadas en el archivo `mypasswd`.
```shell
cisco@labvm:~/Downloads/john/run$ ./john --wordlist=password.lst --rules mypasswd --format=crypt
Cargaron 5 hashes de contraseñas con 5 sales (salts) diferentes (cripta, cripta genérica (3) [? / 64])
Presione 'q' o Ctrl-C para cancelar, casi cualquier otra tecla de estado.
password1        (Eric)
password         (cisco)
password         (Eve)
12345 (Bob)
123456 (Alicia)
5g 0: 00: 00: 00 100% 6.097g / s 117.0p / s 585.3c / s 585.3C / s # Cuentas de cursos CSE de laboratorio - Contabilidad de autorización de autenticación..natasha
Use la opción "--show" para mostrar todas las contraseñas descifradas de manera confiable
Sesión completada
cisco @ labvm: ~ / Downloads / john / run $
```
3. Ingrese el comando `./john --show mypasswd` nuevamente para ver si las contraseñas están descifradas.
```shell
cisco@labvm:~/Downloads/john/run$ ./john --show mypasswd
cisco: contraseña: 900: 900: Analista de ciberseguridad ,,,: / home / cisco: / bin / bash
Alice:123456:1000:1000::/home/Alice:/bin/bash
Bob:12345:1001:1001::/home/Bob:/bin/bash
Eve:password:1002:1002::/home/Eve:/bin/bash
Eric:password1:1003:1003::/home/Eric:/bin/bash

5 hashes decontraseña descifrados, quedan 0
cisco @ labvm: ~ / Downloads / john / run $
```

## Parte 4: cambie la contraseña de un usuario a una versión más segura e intente recuperarla.
1. Cree su propia contraseña segura o utilice un generador de contraseñas en línea para crear una.
2. Busque un "verificador de seguridad de la contraseña" en línea para probar la seguridad de su contraseña. Su contraseña debería tardar al menos miles de años en descifrarse.
3. Utilice sus privilegios de superusuario para cambiar la contraseña de Eric de password1 al valor de su nueva contraseña segura. Asegúrese de recibir el mensaje "La contraseña se actualizó correctamente".
```shell
cisco @ labvm: ~ / Downloads / john / run $ sudo passwd Eric
[sudo] password for cisco: password
Nueva contraseña:<your_new_strong_password>
Vuelva a escribir la contraseña nueva:<your_new_strong_password>
passwd: contraseña actualizada exitosamente
cisco @ labvm: ~ / Downloads / john / run $
```
4. Ejecute unshadow y luego vuelva a ver a John para ver si puede descifrar la contraseña de Eric. Si cambió la contraseña de Eric por una que sea lo suficientemente sólida como para demorar miles de años en descifrarla, esperará mucho tiempo. Cuando haya terminado de esperar, introduzca `q` o `Ctrl + C` para detener a John the Ripper.
```shell
cisco@labvm:~/Downloads/john/run$ ./john --wordlist=password.lst --rules mypasswd --format=crypt
Cargaron 5 hashes de contraseñas con 5 sales (salts) diferentes (cripta, cripta genérica (3) [? / 64])
1 hash de contraseña restante
Presione 'q' o Ctrl-C para cancelar, casi cualquier otra tecla de estado.
0g 0: 00: 00: 17 7% 0g / s 599.6p / s 599.6c / s 599.6C / s reddog1..mark1
Sesión cancelada
```
5. Ingrese el comando `./john --show mypasswd` para ver que solo se descifraron cuatro contraseñas y que queda una.
```shell
cisco@labvm:~/Downloads/john/run$ ./john --show mypasswd
cisco: contraseña: 900: 900: Analista de ciberseguridad ,,,: / home / cisco: / bin / bash
Alicia: 123456: 1000: 1000 :: / home / Alicia: / bin / bash
Bob: 12345: 1001: 1001 :: / home / Bob: / bin / bash
Eva: contraseña: 1002: 1002 :: / home / Eve: / bin / bash

4 hashes decontraseña descifrados, queda 1
cisco @ labvm: ~ / Downloads / john / run $
```