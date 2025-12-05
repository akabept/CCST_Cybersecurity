# Packet Tracer - Implementación de conectividad básica
## Tabla de direccionamiento

__Dispositivo__|__Interfaz__|__Dirección IP__|__Máscara de subred__
:-|:-|-:|-:
S1|VLAN 1|192.168.1.253|255.255.255.0
S2|VLAN 1|192.168.1.254|255.255.255.0
PC1|NIC|192.168.1.1|255.255.255.0
PC2|NIC|192.168.1.2|255.255.255.0

## Objetivos
* Parte 1: Realizar una configuración básica en S1 y S2
* Parte 2: Configurar las PC
* Parte 3: Configurar la interfaz de administración de switches

## Aspectos básicos/Situación
En esta actividad, primero se efectuarán las configuraciones básicas del switch. Luego implementaremos la conectividad básica configurando las direcciones IP en los switches y PC. Cuando haya finalizado la configuración de la asignación de direcciones IP, utilizará diversos comandos show para verificar las configuraciones y utilizará el comando ping para verificar la conectividad básica entre los dispositivos.

## Instrucciones
### Parte 1: Realizar la configuración de SVI en S1 y S2
#### Paso 1: Configurar un nombre de host en el S1.
Abrir la ventana de configuración
1. Haga clic en S1 y, a continuación, haga clic en la ficha CLI.

2. Ingrese al modo EXEC con privilegios. Luego ingrese al modo de configuración global.
```shell
Switch> enable
Switch# configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
```

3. Defina S1 como nombre de host.
```shell
Switch(config)# hostname S1
S1(config)#
```

#### Paso 2: Configurar S1 con una dirección IP.
Los switches se pueden usar sin ninguna configuración. Los switches reenvían información desde un puerto hacia otro sobre la base de direcciones de control de acceso al medio (MAC).
* ¿Por qué necesita un switch una dirección IP?

1. En el modo de configuración global, introduzca los siguientes comandos para configurar S1 con una dirección IP en VLAN 1.
```shell
S1(config)# interface vlan 1
S1(config-if)# ip address 192.168.1.253 255.255.255.0
S1(config-if)# no shutdown
%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan1, changed state to up
```
* ¿Qué hace el comando no shutdown?

2. Salga del modo de configuración global y guarde la configuración.
```shell
S1(config-if)# end
S1#
S1# copy running-config startup-config
Destination filename [startup-config]?
Building configuration...
[OK]
```

3. Verificar la configuración de la dirección IP en S1.
```shell
S1# show ip interface brief
<output omitted>
 Vlan1 192.168.1.253 YES manual up up
```

#### Paso 3: Configurar S2 con un nombre de host y una dirección IP.
En este paso, configurará S2 con un nombre de host y una dirección IP.

Abra la ventana de configuración:

1. Haga click en S2. En la pestaña CLI, ingrese al modo de configuración global.
2. Configure el switch S2 (conmutador) utilizando la información incluida en la tabla de direccionamiento.
3. Use la información en la tabla de direccionamiento, repita el mismo proceso para configurar el switch S2 con una dirección IP.
4. Salga del modo de configuración. Verificar la configuración de la dirección IP en S2.
```shell
S2# show ip interface brief
<output omitted>
 Vlan1 192.168.1.254 YES manual up up
```
5. Guarde el archivo de configuración en la NVRAM. Escriba el comando copy running-config startup-config para guardar la configuración.

### Parte 2: Configurar las PCs
En esta parte, configurará PC1 y PC2 con direcciones IP y verificará la conectividad de red.

#### Paso 1: Configure ambas PC con direcciones IP.
1. Haga clic en PC1 y, luego haga clic en la pestaña Desktop (Escritorio).
2. Haga clic en IP Configuration (Configuración de IP). En la Tabla de direcciones anterior, puede ver que la dirección IP de PC1 debe ser 192.168.1.1 y la máscara de subred 255.255.255.0. Introduzca esta información para la PC1 en la ventana Configuración de IP.
3. Repita los pasos anteriores para PC2. Utilice la dirección IP que figura en la tabla de direcciones para PC2.

#### Paso 2: Pruebe la conectividad desde las PC.
1. Haga clic en PC1. Cierre la ventana Configuración de IP si todavía está abierta. En la ficha Escritorio, haga clic en Símbolo del sistema.
2. Ingrese el comando ping y la dirección IP de S1.
```shell
Packet Tracer PC Línea de comandos 1.0
PC> ping 192.168.1.253
```
* ¿Tuvo éxito? Explique.

3. Desde la PC1, haga ping a S2 y PC2.
4. Repita los pings a S1, S2 y PC1 desde PC2.
Todos los ping deben tener éxito. Si el resultado del primer ping es 80%, vuelva a intentarlo; ahora debería ser 100%. Más adelante, aprenderá por qué es posible que un ping falle la primera vez. Si no puede enviar un comando ping a ninguno de los dispositivos, revise la configuración en busca de errores.

#### Paso 3: Verifique la conectividad de la red desde los switches (conmutadores).
Puede verificarse la conectividad de la red mediante el comando ping. Es muy importante que haya conectividad en toda la red.
1. Desde S1, envíe un comando ping a los otros dispositivos en la red. A continuación, se muestra el ping a PC1 como ejemplo.
```shell
S1> ping 192.168.1.1

Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 192.168.1.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 0/0/1 ms
```

2. Desde S2, envíe un comando ping a los otros dispositivos en la red.

Todos los ping deben tener éxito. Si el resultado del primer ping es 80%, vuelva a intentarlo; ahora debería ser 100%. Más adelante, aprenderá por qué es posible que un ping falle la primera vez. Si no puede enviar un comando ping a ninguno de los dispositivos, revise la configuración en busca de errores.
