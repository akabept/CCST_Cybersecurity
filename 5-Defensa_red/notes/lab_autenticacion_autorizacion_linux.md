<title coding="utf-8">Configurar la autenticación y la autorización en Linux</title>

# Configurar la autenticación y la autorización en Linux
# Objetivos
__Parte 1__: agregar un nuevo grupo para usuarios.
__Parte 2__: agregar usuarios al nuevo grupo.
__Parte 3__: cambiar de usuario y modificar permisos.
__Parte 4__: modificar los permisos en modo absoluto.

# Trasfondo/Situación
En esta práctica de laboratorio utilizará la línea de comandos de Linux para crear un grupo para nuevos usuarios y agregar usuarios al grupo. A cada usuario se le asignará una contraseña para la autenticación al iniciar sesión. Luego, modificará los permisos para autorizar los privilegios de lectura, escritura y ejecución para usuarios y grupos.

# Recursos necesarios
* PC con CSE-LABVM instalada en VirtualBox

# Instrucciones
## Parte 1: agregar un nuevo grupo para usuarios
En esta parte agregará un nuevo grupo para los usuarios a la máquina virtual.

### Paso 1: Abra una ventana de terminal en el CSE-LABVM.
1. Inicie CSE-LABVM.
2. Haga doble clic en el icono de Terminal para abrir un terminal.

### Paso 2: Escalar los privilegios al nivel de root .
Ingrese el comando sudo su e ingrese password como contraseña cuando se le solicite.
```shell
cisco@labvm:~$ sudo su
[sudo] password for cisco:
root@labvm:/home/cisco#
```

### Paso 3: Agregue un nuevo grupo llamado HR.
Ingrese el comando groupadd HR .
```shell
root@ubuntu:/home/cisco# groupadd HR
```

### Paso 4: Verifique que se haya agregado el nuevo grupo.
Ingrese el comando cat /etc/group para verificar que se agregó HR.
```shell
root@labvm:/home/cisco# cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
<output omitted>
Alice:x:1000:
Bob:x:1001:
Eve:x:1002:
Eric:x:1003:
Xnobody:x:1004:
HR:x:1005:
```

El nuevo grupo HR se muestra en la parte inferior del archivo `/etc/group` con una ID de grupo de 1005.

## Parte 2: agregar usuarios al nuevo grupo
En esta parte agregará las cuentas de usuario de Jenny y Joe al grupo HR.

### Paso 1: Agregue a Jenny como usuario nuevo y muévala al grupo HR.
1. Complete lo siguiente para agregar a Jenny como usuario:
	* Ingrese el comando adduser jenny y presione Enter.
	* Ingrese jenPass como contraseña y presione Enter.
	* Vuelva a escribir la nueva contraseña y presione Enter.
	* Ingrese Jenny para el nombre completo y presione Enter.
	* Para el resto de la configuración presione Enter.
	* Ingrese Y para verificar que la información sea correcta y presione Enter.
	```shell
	root@labvm:/home/cisco# adduser jenny
	Adding user `jenny' ...
	Adding new group `jenny' (1006) ...
	Adding new user `jenny' (1005) with group `jenny' ...
	Creating home directory `/home/jenny' ...
	Copying files from `/etc/skel' ...
	New password: jenPass
	Retype new password: jenPass
	passwd: password updated successfully
	Changing the user information for jenny
	Enter the new value, or press ENTER for the default
	       Full Name []: Jenny
	       Room Number []:
	       Work Phone []:
	       Home Phone []:
	       Other []:
	Is the information correct? [Y/n] Y
	root@labvm:/home/cisco#
	```
2. Mueva a jenny al grupo HR. Ingrese el comando usermod -G HR jenny para mover a jenny al grupo HR.
	```shell
	root@ubuntu:/home/cisco# usermod –G HR jenny
	```
### Paso 2: Agregue a Joe como nuevo usuario y muévalo al grupo HR.
1. Ingrese el comando adduser joe y complete los pasos para asignar a joe la contraseña joePass y el nombre completo Joe.
	```shell
	root@labvm:/home/cisco# adduser joe
	Adding user `joe' ...
	Adding new group `joe' (1007) ...
	Adding new user `joe' (1006) with group `joe' ...
	Creating home directory `/home/joe' ...
	Copying files from `/etc/skel' ...
	New password: joePass
	Retype new password: joePass
	passwd: contraseña actualizada exitosamente
	Changing the user information for joe
	Enter the new value, or press ENTER for the default
		Full Name []: Joe
		Room Number []:
		Work Phone []:
		Home Phone []:
		Other []:
	Is the information correct? [Y/n] Y
	```
2. Coloque el usuario Joe en el grupo HR.
	```shell
	root@labvm:/home/cisco# usermod –G HR joe
	```

### Paso 3: compruebe los usuarios creados recientemente en el archivo passwd.
Ingrese el comando cat /etc/passwd para verificar los nuevos usuarios en el archivo passwd.
```shell
root@labvm:/home/cisco# cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
<output omitted>
Xnobody:x:1004:1004::/home/Xnobody:/bin/sh
jenny:x:1005:1006:Jenny,,,:/home/jenny:/bin/bash
joe:x:1006:1007:Joe,,,:/home/joe:/bin/bash
```

### Paso 4: vea los usuarios creados en el archivo shadow .
Ingrese el comando cat /etc/shadow para verificar los nuevos usuarios en el archivo shadow.
```shell
root@labvm:/home/cisco# cat /etc/shadow
root:!:18704:0:99999:7:::
daemon:*:18704:0:99999:7:::
bin:*:18704:0:99999:7:::
sys:*:18704:0:99999:7:::
<output omitted>
Xnobody:!:18704:0:99999:7:::
jenny:$6$VmEFD7wi6zHV8VH5$m2K8U2wpONkvTXzf9uSxSHitbcwAQMEmNiYg8ICnBpdct9dxqr3Hh8EGvxaIasa9fUw.mtB4GGkQYvoZHAFSa/:18705:0:99999:7:::
joe:$6$Ga2C7801c2vb7ias$G9OdK91gnLCnq.5vgpUJjn0/KyWKkXmRemqoGJgBFH0QejpmRYZxQhmS42eZG0SBApc1Z2Q/gsfwuD6oLUh.W.:18705:0:99999:7:::
```

## Parte 3: cambiar de usuario y modificar permisos
En esta parte iniciará sesión como jenny, explorará directorios y cambiará los permisos.

### Paso 1: Cambiar el usuario de root a jenny.
1. Para cambiar al escritorio de Jenny, haga clic en Menú en la parte inferior izquierda del escritorio y haga clic en Logout.
2. Haga clic en Switch User en el cuadro de diálogo.
3. Haga clic en Jenny en la lista de usuarios disponibles e introduzca la contraseña jenPass.
4. El escritorio de Jenny se carga. Desde aquí puede hacer clic con el botón derecho en el escritorio y elegir Open in Terminal.
	```shell
	jenny@labvm:~/Desktop$
	```

### Paso 2: Explore el entorno de Jenny.
1. Ingrese en comando pwd para ostrar el contenido del directorio actual y luego cambie al directorio /home con el comando cd ../...
```shell
jenny@labvm:~/Desktop$ pwd
/home/jenny/Desktop
jenny@labvm:~/Desktop$ cd ../..
jenny@labvm:/home$
```
2. Ingrese el comando ls -l para mostrar todos los directorios en /home, sus permisos y sus usuarios.
```shell
jenny@labvm:/home$ ls -l
total 28
drwxr-xr-x  2 Alice Alice 4096 Mar 18 21:58 Alice
drwxr-xr-x  2 Bob   Bob   4096 Mar 18 21:58 Bob
drwxr-xr-x 12 cisco cisco 4096 Mar 19 20:02 cisco
drwxr-xr-x  2 Eric  Eric  4096 Mar 18 21:58 Eric
drwxr-xr-x  2 Eve   Eve   4096 Mar 18 21:58 Eve
drwxr-xr-x  9 jenny jenny 4096 Mar 19 19:58 jenny
drwxr-xr-x  2 joe   joe   4096 Mar 19 19:44 joe
```
El sistema operativo Linux tiene un total de 10 letras o guiones en los campos de permiso: Por ejemplo, estos directorios principales tienen los siguientes permisos: drwxr-xr-x.
* Una d en el primer campo indica que se trata de un directorio. Un guion (-) significa que es un archivo.
* El siguiente conjunto de tres caracteres es para el permiso del usuario (rwx). Por ejemplo, el usuario jenny es el propietario del directorio y puede leer, escribir y ejecutar el archivo. (read, write y execute).
* El segundo conjunto de caracteres es para los permisos de grupo (r-x). El grupo es jenny, lo que significa que ningún grupo, excepto jenny, puede escribir en este directorio.
* El tercer conjunto de caracteres es para los permisos de cualquier otro usuario o grupo (r-x). Cualquier otro usuario o grupo en la computadora puede leer o ejecutar, pero no puede escribir en el directorio.
3. Como Jenny, ingrese el comando cd joe para entrar en el directorio de Joe. Tenga en cuenta que podemos navegar hasta el directorio de Joe porque el permiso para otros es r-x. La x permite que cualquier usuario ingrese al directorio.
```shell
jenny@labvm:/home$ cd joe
jenny@labvm:/home/joe$
```
4. Mientras está en el directorio de Joe, introduzca el comando touch new.txt para crear un archivo. Se lo rechaza porque el usuario Jenny no tiene permiso para escribir en el directorio de Joe.
```shell
jenny@labvm:/home/joe$ touch new.txt
touch: cannot touch 'new.txt': Permission denied
jenny@labvm:/home/joe$
```
5. Ingrese el comando cd .. para salir del directorio de inicio de Joe.
```shell
jenny@labvm:/home/joe$ cd ..
jenny@labvm:/home$
```

### Paso 3: Inicie sesión como root.
Joe puede no querer que Jenny pueda leer el contenido de su directorio. El acceso root u otro superusuario puede cambiar los permisos del directorio para denegar a Jenny, o cualquier otro usuario o grupo, acceso de lectura al directorio de inicio de Joe.
1. Inicie sesión con el usuario cisco y password como contraseña. Utilice el comando su cisco.
```shell
jenny@labvm:/home$ su cisco
Contraseña:
```
2. Ingrese el comando sudo -i para cambiar a root e introduzca password como contraseña.
```shell
cisco@labvm:~$ sudo -i
[sudo] password for cisco: password
```

### Paso 4: Modifique los permisos para el directorio de inicio de Joe.
Vaya al directorio de inicio e introduzca el comando chmod o-x joe para cambiar el permiso del directorio de inicio de Joe a no ejecutable para otros usuarios y grupos.
```shell
root@labvm:~# cd /home
root@labvm:/home# chmod o-x joe
root@labvm:/home# ls -1
total 28
drwxr-xr-x  2 Alice Alice  4096 Mar 18 21:58
drwxr-xr-x  2 Bob   Bob    4096 Mar 18 21:58
drwxr-xr-x 12 cisco cisco  4096 Mar 19 20:02
drwxr-xr-x  2 Eric  Eric   4096 Mar 18 21:58
drwxr-xr-x  2 Eve   Eve    4096 Mar 18 21:58
drwxr-xr-x  9 jenny jenny  4096 Mar 20 14:02
drwxr-xr--  2 joe   joe    4096 Mar 19 19:44
```

### Paso 5: Verifique que Jenny ya no pueda acceder al directorio de Joe.
1. Cierre la sesión como usuario root y el usuario cisco.
```shell
root@labvm:/home# exit
logout
cisco@labvm:~$ exit
logout
jenny@labvm:/home$
```

2. Ingrese el comando cd joe para intentar navegar al directorio de Joe. Observe que el permiso es denegado.
```shell
jenny@labvm:/home$ cd joe
bash: cd: joe: Permission denied
jenny@labvm:/home$
```
La siguiente tabla muestra ejemplos de otras maneras en que se puede utilizar el comando chmod:

__Comando chmod__|__Resultados__
:-:|:-|
`chmod u+rwx`|Agrega permisos de lectura, escritura y ejecución para el usuario
`chmod u+rw`|Agrega permisos de lectura y escritura para el usuario
`chmod o+r`|Agrega permisos de lectura para otros
`chmod g-rwx`|Elimina permisos de lectura, escritura y de ejecución para el grupo

## Parte 4: modificar los permisos en modo absoluto
En la parte anterior cambió los permisos en modo simbólico. En modo simbólico, el administrador utiliza el comando chmod con una combinación de letras y símbolos para agregar o eliminar permisos. En esta parte, utilizará el comando chmod y los valores octales para establecer permisos para cada triplete de permisos (rwx) para usuario, grupo y otros.

### Paso 1: Cambie el usuario de jenny a joe.
1. Para cambiar al escritorio de Joe haga clic en Menu en la parte superior izquierda del escritorio. En la parte inferior del menú desplegable, haga clic en el botón con la información de herramientas End the current session.
2. Haga clic en Switch User en el cuadro de diálogo.
3. Haga clic en Joe en la lista de usuarios disponibles e introduzca la contraseña joePass.
4. El escritorio de Joe se carga. Desde aquí puede hacer clic con el botón derecho en el escritorio y elegir Open in Terminal.
```shell
joe@labvm:~/Desktop$
```

### Paso 2: Explore el entorno de Joe.
1. Ingrese en comando pwd para mostrar el contenido del directorio actual y luego cambie al directorio /home con el comando cd ../...
```shell
joe@labvm:~/Desktop$ pwd
/home/joe/Desktop
joe@labvm:~/Desktop$ cd ../..
joe@labvm:/home$
```
2. Ingrese el comando ls -l para mostrar todos los directorios en /home, sus permisos y sus usuarios. Observe que la carpeta de Joe está configurada para que “otros” no puedan acceder a la carpeta.
```shell
joe@labvm:/home$ ls -l
total 28
drwxr-xr-x  2 Alice Alice 4096 Mar 18 21:58 Alice
drwxr-xr-x  2 Bob   Bob   4096 Mar 18 21:58 Bob
drwxr-xr-x 12 cisco cisco 4096 Mar 19 20:02 cisco
drwxr-xr-x  2 Eric  Eric  4096 Mar 18 21:58 Eric
drwxr-xr-x  2 Eve   Eve   4096 Mar 18 21:58 Eve
drwxr-xr-x  9 jenny jenny 4096 Mar 20 14:02 jenny
drwxr-xr--  9 joe   joe   4096 Mar 20 15:01 joe
```

### Paso 3: utilice el modo absoluto para modificar y luego verifique los permisos para el directorio de Joe.
Otra manera de asignar permisos además de utilizar permisos simbólicos es utilizar permisos absolutos. Los permisos absolutos usan un número de tres dígitos octal para representar los permisos de propietario, de grupo y de otros.

La siguiente tabla describe cada valor absoluto y los permisos correspondientes:

__Número__|__Permisos__
:-:|:-|
7|Lectura, escritura y ejecución
6|Lectura y escritura
5|Lectura y ejecución
4|Lectura
3|Escritura y ejecución
2|Escritura
1|Ejecución
0|Ninguno

Al escribir el comando `chmod 764 examplefile` se asignarán los siguientes permisos al archivo "examplefile":

__Dígito__|__Equivalente binario__|__Permiso__
:-:|:-:|:-
7 (usuario)|111| 1 - Lectura; 1 - Escritura; 1 - Ejecución
6 (grupo)|110| 1 - Lectura; 1 - Escritura; 0 - Sin ejecución
5 (otros)|100| 1 - Lectura; 0 - Sin escritura; 0 - Sin ejecución

1. Modifique el campo "others" de la carpeta de Joe para que otros puedan leer y ejecutar, pero no escribir manteniendo el campo "user" con los permisos para leer, escribir y ejecutar.
```shell
joe@labvm:/home$ chmod 705 joe
```
2. Liste los permisos de archivo del directorio actual para ver que los cambios absolutos se hayan realizado.
```shell
joe@labvm:/home$ ls -l
total 28
drwxr-xr-x  2 Alice Alice 4096 Mar 18 21:58 Alice
drwxr-xr-x  2 Bob   Bob   4096 Mar 18 21:58 Bob
drwxr-xr-x 12 cisco cisco 4096 Mar 19 20:02 cisco
drwxr-xr-x  2 Eric  Eric  4096 Mar 18 21:58 Eric
drwxr-xr-x  2 Eve   Eve   4096 Mar 18 21:58 Eve
drwxr-xr-x  9 jenny jenny 4096 Mar 20 14:02 jenny
drwx---r-x  9 joe   joe   4096 Mar 20 15:01 joe
joe@labvm:/home$
```

### Paso 4: Cree un archivo en el directorio Joe.
Cambie al directorio joe, utilice el comando touch test.txt para crear un archivo y luego liste el contenido del directorio.
```shell
joe@labvm:/home$ cd joe
joe@labvm:~$ touch test.txt
joe@labvm:~$ ls -l
total 12
drwxr-xr-x 2 joe joe 4096 Mar 20 15:00 Desktop
drwxr-xr-x 2 joe joe 4096 Mar 20 15:00 Documents
drwxr-xr-x 2 joe joe 4096 Mar 20 15:00 Downloads
-rw-rw-r-- 1 joe joe    0 Mar 20 15:33 test.txt
joe@labvm:~$
```

### Paso 5: Cambie el usuario de Joe a Jenny.
1. Para cambiar al escritorio de Jenny, haga clic en Menu en la parte superior izquierda del escritorio. En la parte inferior del menú desplegable, haga clic en el botón con la información de herramientas End the current session.
2. Haga clic en Switch User en el cuadro de diálogo.
3. Haga clic en Jenny en la lista de usuarios disponibles e introduzca la contraseña jenPass.
4. El escritorio de Jenny se carga. Desde aquí puede hacer clic con el botón derecho en el escritorio y elegir Open in Terminal.
```shell
jenny@labvm:~/Desktop$
```

### Paso 6: Cambie al directorio de inicio y liste su contenido.
```shell
jenny@labvm:~/Desktop$ cd ../..
jenny@labvm:/home$ ls -l
total 28
drwxr-xr-x  2 Alice Alice 4096 Mar 18 21:58 Alice
drwxr-xr-x  2 Bob   Bob   4096 Mar 18 21:58 Bob
drwxr-xr-x 12 cisco cisco 4096 Mar 19 20:02 cisco
drwxr-xr-x  2 Eric  Eric  4096 Mar 18 21:58 Eric
drwxr-xr-x  2 Eve   Eve   4096 Mar 18 21:58 Eve
drwxr-xr-x  9 jenny jenny 4096 Mar 20 14:02 jenny
drwx---r-x  9 joe   joe   4096 Mar 20 15:01 joe
jenny@labvm:/home$
```

### Paso 7: Cambie al directorio joe y liste el contenido del directorio.
Observe que el usuario jenny, como miembro de "others", tiene acceso de lectura al directorio joe y también tiene acceso de lectura para el archivo "test.txt".
```shell
jenny@labvm:/home$ cd joe
jenny@labvm:/home/joe$ ls -l
total 12
drwxr-xr-x 2 joe joe 4096 Mar 20 15:00 Desktop
drwxr-xr-x 2 joe joe 4096 Mar 20 15:00 Documents
drwxr-xr-x 2 joe joe 4096 Mar 20 15:00 Downloads
-rw-rw-r-- 1 joe joe    0 Mar 22 14:33 test.txt
jenny@labvm:/home/joe$
```

### Paso 8: Intente crear un archivo en el directorio joe.
Observe cómo se le niega al usuario jenny permiso para escribir en el directorio joe.
```shell
jenny@labvm:/home/joe$ touch jenny.txt
touch: cannot touch 'jenny.txt': Permission denied
jenny@labvm:/home/joe$
```

### Paso 9: Cambie el usuario de jenny a cisco y cierre la máquina virtual.
1. Haga clic en Menu en la parte superior izquierda del escritorio. En la parte inferior del menú desplegable, haga clic en el botón con la información de herramientas End the current session.
2. Haga clic en Switch User en el cuadro de diálogo.
3. Haga clic en Cybersecurity Analyst en la lista de usuarios disponibles e introduzca password como contraseña.
4. Haga clic en File > Close, elija Save the machine state y luego haga clic en OK.

<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />