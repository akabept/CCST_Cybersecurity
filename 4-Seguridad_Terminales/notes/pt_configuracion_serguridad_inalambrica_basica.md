<title coding="utf-8">Configurar la seguridad inalámbrica básica</title>

# Packet Tracer - Configurar la seguridad inalámbrica básica
# Objetivos
Configurar la seguridad inalámbrica básica con WPA2 Personal.

# Trasfondo/Situación
El dueño de una pequeña empresa descubre que la red inalámbrica debe estar protegida del acceso no autorizado. Ha decidido usar WPA2 Personal para su red.

# Instrucciones
## Parte 1: Verificar la conectividad.

1. Acceda a Escritorio > Navegador en la computadora portátil.
2. Introduzca www.cisco.pka en la URL. Se abrirá la página web.

## Parte 2: Configurar la seguridad inalámbrica básica.
1. Introduzca `192.168.1.1` en el navegador web para acceder al router inalámbrico. Escriba admin como nombre de usuario y contraseña.
2. Haga clic en el menú Wireless (Inalámbrico). Seleccione el menú Wireless Security (Seguridad inalámbrica).
3. En este momento, el modo de seguridad está deshabilitado. Para una red de 2,4 GHz, cambie el modo de seguridad a WPA2 Personal. Para las redes de 5 GHz, puede dejarlas como deshabilitadas.
4. En el campo de la frase de contraseña, escriba `Network123`.
5. Desplácese hasta la parte de abajo de la página y haga clic en Save Settings (Guardar configuración). Cierre el navegador web.

## Parte 3: Actualizar la configuración inalámbrica en la computadora portátil.
1. Haga clic en PC Wireless en la pestaña Desktop.
2. Haga clic en la pestaña Conectar . Seleccione Academia y haga clic en Conectar.
3. Introduzca `Network123` como clave precompartida. Haga clic en Conectar.
4. Cierre la ventana PC inalámbrica .

## Parte 4: Verificar la conectividad.
1. Acceda al Navegador web.
2. Introduzca www.cisco.pka en la URL. Verifique que aparezca la página web después de agregar la configuración inalámbrica básica.
3. Si no puede acceder a la página web, verifique la configuración inalámbrica del router inalámbrico y la computadora portátil. Verifique también que la computadora portátil esté conectada al router inalámbrico.