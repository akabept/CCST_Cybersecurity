# Usar Ping y Traceroute para probar la conectividad de red
* Tabla de direccionamiento
<table>
	<tr><th>Dispositivo<th>Interfaz<th colspan="2">Dirección IP/Prefijo<th>Puerta de enlace pred.
	<tr><td rowspan="5">R1<td>G0/0<td colspan="2">2001:db 8:1:1::1/64<td>N/A
	<tr><td>G0/1<td>10.10.1.97<td>255.255.255.224<td>N/A
	<tr><td rowspan="3">S0/0/1<td>10.10.1.6<td>255.255.255.252<td rowspan="3">N/A
	<tr><td colspan="2">2001:db 8:1:2::2/64
	<tr><td colspan="2">fe80::1
	<tr><td rowspan="5">R2<td rowspan="2">S0/0/0<td>10.10.1.5<td>255.255.255.252<td rowspan="2">N/A
	<tr><td colspan="2">2001:db8:1:2::1/64
	<tr><td rowspan="3">S0/0/1<td>10.10.1.9<td>255.255.255.252<td rowspan="3">N/A
	<tr><td colspan="2">2001:db8:1:3::1/64
	<tr><td colspan="2">fe80::2
	<tr><td rowspan="5">R3<td>G0/0<td colspan="2">2001:db 8:1:4: :1/64<td>N/A
	<tr><td>G0/1<td>10.10.1.17<td>255.255.255.240<td>N/A
	<tr><td rowspan="3">S0/1<td>10.10.1.10<td>255.255.255.252<td rowspan="3">N/A
	<tr><td colspan="2">2001:db 8:1:2::2/64
	<tr><td colspan="2">fe80::3
	<tr><td>PC1<td>NIC<td>Su respuesta<td>Su respuesta<td>Su respuesta
	<tr><td>PC2<td>NIC<td colspan="2">Su respuesta<td>Su respuesta
	<tr><td>PC3<td>NIC<td>Su respuesta<td>Su respuesta<td>Su respuesta
	<tr><td>PC4<td>NIC<td colspan="2">Su respuesta<td>Su respuesta
</table>

# Objetivos
* __Parte 1: Probar y restaurar la conectividad IPv4__
* __Parte 2: Probar y restaurar la conectividad IPv6__

# Escenario
En esta actividad, hay problemas de conectividad. Además de reunir y registrar información acerca de la red, localizará los problemas e implementará soluciones razonables para restaurar la conectividad.

__Nota__: La contraseña de EXEC del usuario es cisco. La contraseña de EXEC privilegiado es class.

# Instrucciones
## Parte 1: Pruebe y restaure la conectividad IPv4
### Paso 1: Utilice los comandos ipconfig y ping para verificar la conectividad.
1. Haga clic en PC1 y abra el símbolo del sistema.
2. Introduzca el comando ipconfig /all para obtener la información de IPv4. Complete la tabla de direccionamiento con la dirección IPv4, la máscara de subred y el gateway predeterminado.
3. Haga clic en PC3 y abra el símbolo del sistema.
4. Introduzca el comando ipconfig /all para obtener la información de IPv4. Complete la tabla de direccionamiento con la dirección IPv4, la máscara de subred y el gateway predeterminado.
5. Utilice el comando ping para probar la conectividad entre PC1 y PC3. El ping debe fallar.

### Paso 2: Localice el origen de la falla de conectividad.
1. En la PC1, introduzca el comando necesario para rastrear la ruta a la PC3.
* ¿Cuál es la última dirección IPv4 a la que se llegó correctamente?
2. El rastreo finaliza después de 30 intentos. Presione Ctrl+C para detener el rastreo antes de los 30 intentos.
3. En la PC3, introduzca el comando necesario para rastrear la ruta a la PC1.
* ¿Cuál es la última dirección IPv4 a la que se llegó correctamente?
4. Haga clic en R1. Presione Enter e inicie sesión en el router.
5. Introduzca el comando show ip interface brief para obtener una lista de las interfaces y su estado. Hay dos direcciones IPv4 en el router. Una se debe haber registrado en el paso 2a.
* ¿Cuál es la otra?
6. Introduzca el comando show ip route para obtener una lista de las redes a las que está conectado el router. Observe que hay dos redes conectadas a la interfaz `serial0/0/1`.
* ¿Cuáles son?
7. Repita los pasos 2e a 2g con el R3 y registre tus respuestas.
8. Haga clic en R2. Presione ENTER e inicie sesión en el router.
9. Ingrese el comando show ip interface brief y registre sus direcciones.
10. Ejecute más pruebas si eso permite visualizar el problema. Está disponible el modo de simulación.

### Paso 3: Proponga una solución para resolver el problema
Compare sus respuestas del paso 2 con la documentación que tiene disponible para la red.
* ¿Cuál es el error?
* ¿Qué solución propondría para corregir el problema?

### Paso 4: Implemente el plan
Implemente la solución que propuso en el paso 3b.

### Paso 5: Verifique que la conectividad esté restaurada
1. En la PC1, pruebe la conectividad a la PC3.
2. En la PC3, pruebe la conectividad a la PC1.
* ¿Se solucionó el problema?

### Paso 6: Registre la solución

## Parte 2: Pruebe y restaure la conectividad IPv6
### Paso 1: Utilice los comandos ipv6config y ping para verificar la conectividad.
1. a.     Haga clic en PC2 y abra el símbolo del sistema.
2. Introduzca el comando ipv6config /all para obtener la información de IPv6. Complete la tabla de direccionamiento con la dirección IPv6, el prefijo de subred y el gateway predeterminado.
3. Haga clic en PC4 y abra el símbolo del sistema.
4. Introduzca el comando ipv6config /all para obtener la información de IPv6. Complete la tabla de direccionamiento con la dirección IPv6, el prefijo de subred y el gateway predeterminado.
5. Pruebe la conectividad entre la PC2 y la PC4. El ping debe fallar.

### Paso 2: Localice el origen de la falla de conectividad.
1. En la PC2, introduzca el comando necesario para rastrear la ruta a la PC4.
* ¿Cuál es la última dirección IPv6 a la que se llegó correctamente?
2. El rastreo finaliza después de 30 intentos. Presione Ctrl+C para detener el rastreo antes de los 30 intentos.
3. En la PC4, introduzca el comando necesario para rastrear la ruta a la PC2.
* ¿Cuál es la última dirección IPv6 a la que se llegó correctamente?
4. Presione Ctrl+C para detener el rastreo.
5. Haga clic en R3. Presione Enter (Introducir) e inicie sesión en el router.
6. Introduzca el comando show ipv6 interface brief para obtener una lista de las interfaces y su estado. Hay dos direcciones IPv6 en el router. Una debe coincidir con la dirección de gateway registrada en el paso 1d.
* ¿Hay alguna discrepancia?
7. Ejecute más pruebas si eso permite visualizar el problema. Está disponible el modo de simulación.

### Paso 3: Proponga una solución para resolver el problema
Compare sus respuestas del paso 2 con la documentación que tiene disponible para la red.
* ¿Cuál es el error?
* ¿Qué solución propondría para corregir el problema?

### Paso 4: Implemente el plan
Implemente la solución que propuso en el paso 3b.

### Paso 5: Verifique que la conectividad esté restaurada
1. En la PC2, pruebe la conectividad a la PC4.
2. En la PC4, pruebe la conectividad a la PC2.
* ¿Se solucionó el problema?

### Paso 6: Registre la solución