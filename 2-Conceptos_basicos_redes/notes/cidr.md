# CIDR
El enrutamiento entre dominios sin clases (CIDR - _Classless Inter-Domain Routing_) es un método de asignación de direcciones IP que mejora la eficiencia del enrutamiento de datos en Internet. Cada máquina, servidor y dispositivo de usuario final que se conecta a Internet tiene asociado un número único, denominado dirección IP. Los dispositivos se encuentran y se comunican entre sí mediante estas direcciones IP. Las organizaciones utilizan el CIDR para asignar direcciones IP de manera flexible y eficiente en sus redes.

## ¿Cuáles son los diferentes formatos de direcciones IP?
Una dirección IP tiene dos partes:

La dirección de red es una serie de dígitos numéricos que apuntan al identificador único de la red. 
La dirección del host es una serie de números que indican el identificador del dispositivo principal o individual en la red.
Hasta principios de la década de 1990, las direcciones IP se asignaban mediante el sistema de direccionamiento por clases. Se fijó la longitud total de la dirección y también se fijó el número de bits asignados a las partes de red y host.

### Direcciones por clases
Una dirección IPv4 se compone de 32 bits. Cada cadena de números separados por el punto consta de 8 bits, representados de 0 a 255 en forma numérica. Las organizaciones pueden comprar tres clases de direcciones IPv4. 

* __Clase A__. Una dirección IPv4 de clase A tiene 8 bits de prefijo de red. Por ejemplo, considere `44.0.0.1`, donde `44` es la dirección de red y `0.0.1` es la dirección del host.
* __Clase B__. Una dirección IPv4 de clase B tiene 16 bits de prefijo de red. Por ejemplo, considere `128.16.0.2`, donde `128.16` es la dirección de red y `0.2` es la dirección del host.
* __Clase C__. Una dirección IPv4 de clase C tiene 24 bits de prefijo de red. Por ejemplo, considere `192.168.1.100`, donde `192.168.1` es la dirección de red y `100` es la dirección del host. 

### Direcciones sin clases
Las direcciones de enrutamiento entre dominios sin clases (CIDR) utilizan el enmascaramiento de subred de longitud variable (VLSM) para alterar la proporción entre los bits de la dirección de red y del host en una dirección IP. Una máscara de subred es un conjunto de identificadores que devuelve el valor de la dirección de red a partir de la dirección IP al convertir la dirección del host con ceros. 

Una secuencia de VLSM permite a los administradores de red dividir un espacio de direcciones IP en subredes de varios tamaños. Cada subred puede tener un recuento de hosts flexible y un número limitado de direcciones IP. Una dirección IP de CIDR agrega un valor de sufijo que indica el número de bits del prefijo de la dirección de red a una dirección IP normal.

Por ejemplo, `192.0.2.0/24` es una dirección de CIDR IPv4 en la que los primeros 24 bits, o `192.0.2`, son la dirección de red.

## ¿Cuáles son las limitaciones del direccionamiento IP por clases que supera el CIDR?
Antes del enrutamiento entre dominios sin clases (CIDR), las direcciones IP tenían clases y generaban ineficiencias. Analizaremos algunas de estas deficiencias a continuación. 

### Direccionamiento IP inflexible
En un sistema de direccionamiento por clases, cada clase admitía un número fijo de dispositivos:

* La Clase A admitía 16.777.214 hosts.
* La Clase B admitía 65.534 hosts.
* La Clase C admitía 254 hosts.

La disposición por clases era ineficiente a la hora de asignar direcciones IP y generaba un desperdicio de espacios de direcciones IP.

Por ejemplo, una organización con 300 dispositivos no podría utilizar una dirección IP de Clase C, que solo permitía 254 dispositivos. Por lo tanto, la organización se habría visto obligada a solicitar una dirección IP de Clase B, que proporcionaba 65.534 direcciones de host únicas. Sin embargo, solo se habrían conectado 300 dispositivos, lo que habría dejado 65.234 espacios de direcciones IP sin usar.

### Limitaciones en el diseño de redes
Las IP por clases limitaban su capacidad de combinar redes según fuera necesario. Por ejemplo, estas direcciones IP pertenecen a diferentes redes de Clase C en la arquitectura de clases: 
```
192.168.1.0
192.168.0.0
```

Como administrador de red, no podría haber combinado ambas redes porque la máscara de subred de clase C estaba fijada como `255.255.255.0`.

## ¿Cuáles son las ventajas del CIDR?
Con el enrutamiento entre dominios sin clases (CIDR), su organización tiene más flexibilidad a la hora de asignar direcciones IP y enrutar datos entre dispositivos.

### Reducción del desperdicio de direcciones IP
El CIDR proporciona flexibilidad a la hora de determinar las asignaciones de identificadores de red y host en una dirección IP. Puede utilizar el CIDR para aprovisionar la cantidad necesaria de direcciones IP para una red determinada y reducir el desperdicio. Además, el CIDR reduce las entradas de la tabla de enrutamiento y simplifica el enrutamiento de paquetes de datos. 

### Transmisión rápida de datos
El CIDR permite a los enrutadores organizar las direcciones IP en varias subredes de manera más eficiente. Una subred es una red más pequeña que existe dentro de una red. Por ejemplo, todos los dispositivos conectados a un router están en la misma subred y tienen el mismo prefijo de dirección IP.

Con el CIDR, su organización puede crear y consolidar varias subredes. Esto permite que los datos lleguen a la dirección de destino sin tomar rutas innecesarias. 

### Creación de una nube privada virtual
Una nube privada virtual (VPC - _Virtual Private Cloud_) es un espacio digital privado alojado en la nube. Permite a su organización aprovisionar cargas de trabajo en un entorno aislado y seguro. Una VPC usa direcciones IP de CIDR cuando transfiere paquetes de datos entre dispositivos conectados. 

### Creación de superredes de forma flexible
Una superred es un grupo de subredes con prefijos de red similares. El CIDR ofrece flexibilidad a la hora de crear superredes, lo que no es posible en la arquitectura de enmascaramiento convencional. Por ejemplo, su organización puede combinar direcciones IP en un solo bloque de red mediante una notación como la siguiente:
```
192.168.1 /23 
192.168.0 /23
```
Esta notación aplica una máscara de subred de `255.255.254.0` a la dirección IP, que devuelve los primeros 23 bits como dirección de red. El router solo necesita una entrada en la tabla de enrutamiento para administrar los paquetes de datos entre los dispositivos de las subredes.

## ¿Cómo funciona el CIDR?
El enrutamiento entre dominios sin clases (CIDR) permite a los enrutadores de red enrutar paquetes de datos al dispositivo respectivo en función de la subred indicada. En lugar de clasificar la dirección IP en función de las clases, los enrutadores recuperan la dirección de red y del host tal como se especifica en el sufijo de CIDR.

Es importante entender los bloques de CIDR y la notación de CIDR para aprender cómo funciona el CIDR.

### Bloques de CIDR
Un bloque de CIDR es un conjunto de direcciones IP que comparten el mismo prefijo de red y el mismo número de bits. Un bloque grande se compone de más direcciones IP y un sufijo pequeño.

La _Internet Assigned Numbers Authority_ (IANA) asigna bloques de CIDR grandes a los registros regionales de Internet (RIR - _Regional Internet Registers_). Luego, el RIR asigna bloques más pequeños a los registros locales de Internet (LIR - _Local Internet Registers_), que luego los asignan a las organizaciones. Mientras tanto, los usuarios privados solicitan bloques de CIDR a sus proveedores de servicios de Internet.

<div align="center">
	<img src="../img/cidr_block.png" />
</div>

### Notación de CIDR
La notación de CIDR representa una dirección IP y un sufijo que indica los bits del identificador de red en un formato especificado. Por ejemplo, puede expresar `192.168.1.0` con un identificador de red de 22 bits como `192.168.1.0/22`.

## ¿Cómo se usa el CIDR en IPv6?
IPv6 es un sistema de direccionamiento de red diseñado para reemplazar a IPv4. IPv6 usa un identificador único de 128 bits, que le permite contener 1028 veces más direcciones IP que IPv4.

Una dirección IPv6 se compone de 8 valores hexadecimales separados por dos puntos. IPv6 permite un espacio de direcciones mucho mayor para dar cabida al creciente número de dispositivos que se conectan a Internet en la actualidad.

En el enrutamiento entre dominios sin clases (CIDR), las direcciones IPv6 se pueden agregar con prefijos de longitud de bits arbitraria, similares a las direcciones IPv4. Por ejemplo, `2001:0db8: /32` es una dirección de CIDR IPv6, con los primeros 32 bits, o `2001:db8`, como dirección de red.

<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />