<title coding="utf-8">Reforzar un sistema Linux</title>

# Protección del sistema Linux
# Objetivos
* Utilice una herramienta de auditoría de seguridad para detectar vulnerabilidades del sistema.
* Implementar soluciones recomendadas para fortalecer el sistema.

# Trasfondo/Situación

La auditoría de un sistema para detectar posibles configuraciones incorrectas o servicios sin protección es un aspecto importante del fortalecimiento del sistema. Lynis es una herramienta de auditoría de seguridad de código abierto con un conjunto automatizado de scripts desarrollados para probar un sistema Linux. Lynis realiza un exhaustivo análisis del estado de su sistema. Incluye un informe detallado de las vulnerabilidades y las acciones recomendadas. En esta práctica de laboratorio, utilizará Lynis para analizar su VM y luego implementar soluciones para fortalecer su sistema.

# Recursos necesarios
* PC con CSE-LABVM instalada en VirtualBox

# Instrucciones
## Parte 1: Instale y actualice Lynis
### Paso 1: Determine la versión instalada de Lynis
1. Inicie CSE-LABVM.
2. Haga doble clic en el icono de Terminal para abrir un terminal.
3. Para determinar la última versión proporcionada por CISOfy, introduzca el siguiente comando en el terminal.
```shell
cisco@labvm:~$ sudo apt-cache policy lynis
lynis:
  Installed: 3.0.6-100
  Candidate: 3.0.6-100
  Version table:
 *** 3.0.6-100 500
        500 https://packages.cisofy.com/community/lynis/deb stable/main amd64 Packages
        500 https://packages.cisofy.com/community/lynis/deb stable/main i386 Packages
        100 /var/lib/dpkg/status
     2.6.2-1 500
        500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu focal/universe i386 Packages
```

4. Vaya a la siguiente parte si tiene la última versión de Lynis. Si Lynis no está instalado o la última versión no está instalada, vaya al siguiente paso para instalar Lynis.

### Paso 2: Instale Lynis
Lynis es una herramienta de seguridad para sistemas que ejecutan sistemas operativos basados en Unix, como Linux y macOS. Lynis se utilizará más adelante en otra actividad para fortalecer un sistema Linux. La aplicación Lynis es mantenida por CISOfy. En este paso, agregaremos el repositorio de software e instalaremos Lynis.
1. Copie y pegue el siguiente comando en una terminal para importar la clave del servidor de claves CISOfy. Esta clave es necesaria para verificar la integridad de su descarga cuando descarga lynis:
```shell
cisco@labvm:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 013baa07180c50a7101097ef9de922f1c2fde6c4
```
2. Copie y pegue el siguiente comando en una terminal para agregar el repositorio lynis mantenido por CISOfy.
```shell
cisco@labvm:~$ echo "deb https://packages.cisofy.com/community/lynis/deb/ stable main" | sudo tee /etc/apt/sources.list.d/cisofy-lynis.list
```
3. Realice una actualización después de agregar un nuevo repositorio. En el _prompt_, ingrese `sudo apt-get update`.
4. Utilice el comando apt para instalar Lynis si aún no está instalado.
```shell
cisco@labvm:~$ sudo apt install lynis
Leyendo listas de paquetes... Listo.
Construir árbol de dependencias.
Leyendo la información del estado. Listo.
Se instalarán los siguientes paquetes NUEVOS:
  lynis
0 actualizado, 1 recién instalado, 0 para eliminar y 0 no actualizado.
Necesita obtener 23,9 kB de archivos.
Después de esta operación, se usarán 1,681 kB de espacio adicional en disco.
Seleccionar paquete speedtest-cli previamente no seleccionado.
(Leyendo base de datos... 205787 archivos y directorios instalados actualmente.)
Preparándose para desempaquetar.../lynis_3.0.6-100_all.deb...
Unpacking lynis (3.0.6-100) ...
Configurando lynis (3.0.6-100)...
Disparadores de procesamiento para man-db (2.9.1-1) ...
```
5. Realice una actualización después de la instalación para asegurarse de que la versión instalada de Lynis sea la última. Cuando se le solicite, ingrese `sudo apto-get upgrade`.

## Parte 2: examinar la versión actual de Lynis.

Cambie al directorio de Lynis y luego introduzca el comando sudo lynis update info para verificar la información de actualización de Lynis. Introduzca la contraseña para la contraseña de sudo. Este comando verifica que esta es la versión más reciente y actualiza la herramienta al momento de la redacción de esta práctica de laboratorio. Si la versión instalada de Lynis no está actualizada, ingrese sudo apto-get actualizar en el indicador.
```shell
cisco @ labvm: ~ $ sudo información de actualización de Lynis
[sudo] contraseña para cisco: contraseña
== Lynis ==
Versión: 3.0.6
Estado: actualizado
Fecha de lanzamiento: 2021-07-22
  Página del proyecto       : https://cisofy.com/lynis/
Código fuente: https://github.com/CISOfy/lynis
Último paquete: https://packages.cisofy.com/

2007-2021, CISOfy - https://cisofy.com/lynis/
```

## Parte 3: ejecute la herramienta Lynis.

1. Ingrese el comando sudo lynis --auditor cisco. Es posible que deba ingresar la contraseña como contraseña nuevamente. El análisis tardará aproximadamente un minuto en ejecutarse.
```shell
cisco @ labvm: ~ $ sudo lynis --auditor cisco
```
2. Debería recibir la salida para una variedad de características del sistema que comienzan con arranque y servicios, y terminan con refuerzo, pruebas personalizadas y complementos (fase 2). La siguiente sección son los resultados de Lynis 3.0.6. Sus resultados probablemente incluyan las dos advertencias que se muestran a continuación. También puede recibir otras advertencias. Además, habrá una sección con una lista de Sugerencias, que enumera 49 en la salida de ejemplo a continuación. Solo se muestra la primera sugerencia.
```shell
[Lynis 3.0.6]

################################################## ##############################

Lynis viene SIN NINGUNA GARANTÍA EN ABSOLUTO. Esto es software libre, y ustedes
bienvenido a redistribuirlo según los términos de la Licencia pública general de GNU.
Consulte el archivo LICENCIA para obtener detalles sobre el uso de este software.
2007-2021, CISOfy - https://cisofy.com/lynis/
Soporte empresarial disponible (cumplimiento, complementos, interfaz y herramientas)

################################################## ##############################

[+] Programa de inicialización
------------------------------------
- Detección del SO ...[HECHO]
- Verificando perfiles ...[HECHO]
 
<output omitted>

[+] Arranque y servicios
------------------------------------
- Administrador de servicio [ systemd ]
- Comprobando arranque UEFI [DESACTIVADO]
- Comprobando presencia GRUB2 [ENCONTRADO]

<output omitted>

[+] Endurecimiento
------------------------------------
- Compilador (es) instalado (s) [ENCONTRADO]
- Instaló escáner de malware [NO ENCONTRADO]
- Formatos binarios no nativos [NO ENCONTRADO]

[+] Pruebas personalizadas
------------------------------------
- Ejecución de pruebas personalizadas ...[NINGUNO]

[+] Complementos (fase 2)
------------------------------------

================================================== ==============================

- [Resultados de Lynis 3.0.6] -
  Advertencias :
----------------------------
Encontró uno o más paquetes vulnerables. [PKGS-7392]
https : //cisofy.com/lynis/controls/PKGS-7392/

! Módulos de iptables cargados, pero sin reglas activas [FIRE-4512]
https : //cisofy.com/lynis/controls/FIRE-4512/

Sugerencias (49):
----------------------------
* Establecer una contraseña en el gestor de arranque GRUB para evitar alterar la configuración de arranque (por ejemplo, arranque en modo de usuario único sin contraseña) [BOOT-5122]
https: //cisofy.com/lynis/controls/BOOT-5122/

<output omitted>
================================================== ==============================
Lynis 3.0.6
Auditoría, fortalecimiento del sistema y cumplimiento para sistemas basados en UNIX
(Linux, macOS, BSD y otros)
2007-2021, CISOfy - https://cisofy.com/lynis/
Soporte empresarial disponible (cumplimiento, complementos, interfaz y herramientas)
================================================== ==============================

[SUGERENCIA]: Mejore las auditorías de Lynis agregando su configuración a custom.prf (consulte /home/cisco/Downloads/lynis/default.prf para ver todas las configuraciones).
cisco @ labvm: ~ $
```

## Parte 4: revise los resultados del análisis y aborde las advertencias
1. Desplácese hasta la sección Resultados en la salida para su análisis.
* ¿Cuántas advertencias recibió?
* ¿Cuántas sugerencias recibió?
2. Debe abordar las advertencias. Elija al menos una advertencia e investigue cómo solucionar ese problema. Puede utilizar el enlace proporcionado en la salida de advertencia como punto de partida para abordar una advertencia. Pero también es posible que deba utilizar sus habilidades de investigación en Internet para localizar información adicional.
* ¿A qué advertencia se dirige?
* ¿Cuál es su solución?
3. Implemente su solución y ejecute el comando sudo lynis --auditor cisco nuevamente. Si la advertencia que eligió ya no aparece en la sección Resultados, ¡felicitaciones! Usted acaba de aumentar el fortalecimiento de su VM de Ubuntu. Si la advertencia sigue apareciendo, vea si puede encontrar más información para ayudarlo a obtener un informe claro de Lynis en el que la advertencia ya no se informa.