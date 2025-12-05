<title coding="utf-8">Generación y uso de una firma digital</title>

# Generación y uso de una firma digital
# Objetivos
* Utilice OpenSSL para generar una firma digital.
* Firmar un documento con la firma digital.
* Verifique que un documento firmado ha sido modificado.

# Trasfondo/Situación
Una firma digital es una técnica matemática utilizada para validar la autenticidad y la integridad de un mensaje digital. El propósito de una firma digital es evitar la manipulación y la suplantación de identidad en las comunicaciones digitales. En muchos países, incluido Estados Unidos, las firmas digitales tienen la misma importancia legal que las formas tradicionales de documentos firmados. El gobierno de los Estados Unidos actualmente publica las versiones electrónicas de presupuestos, leyes y proyectos parlamentarios con firmas digitales.

Un algoritmo de firma digital consiste en un proceso de creación y verificación de firma. El usuario A genera la firma digital y el usuario B verifica la firma mediante el proceso de verificación. Tanto el firmante como el verificador tienen una clave pública y una privada que utilizan para completar cada proceso.

En esta práctica de laboratorio utilizará el kit de herramientas OpenSSL para generar una firma digital. Luego generará un documento, lo firmará con la firma digital y finalmente validará la autenticidad e integridad del documento. Por último, cambiará el documento y luego validará que el documento ya no es auténtico porque su integridad se ha visto comprometida.

# Recursos necesarios
* PC con CSE-LABVM instalado en Virtualbox

# Instrucciones
## Parte 1: abra una ventana de terminal en CSE-LABVM.
1. Inicie CSE-LABVM.
2. Haga doble clic en el icono de Terminal para abrir un terminal.

## Parte 2: generar y ver una clave privada.
1. Para generar una clave privada, use el comando openSSL `genpkey`. El comando genera una clave privada usando el algoritmo RSA y la envía a un archivo denominado `private_key.pem`.
	```shell
	cisco@labvm:~$ openssl genpkey -algorithm RSA -out private_key.pem
	........................+++++
	...+++++
	cisco@labvm:~$
	```
2. Utilice el comando `cat` para ver `private_key.pem`.
	```shell
	cisco@labvm:~$ cat private_key.pem
	-----BEGIN PRIVATE KEY-----
	MIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQC1db50XOYeDTAy
	GnQLRwGusr7us0Mi44hfFUmai3QHzelqRBxO06ujv9fFwQ8e5QsaQWbph+RVTQBu
	<output omitted>
	R7TLUOrewnIlkMuVLk8II2EQAXTMmvvZOICCiTSvm8gflx/FRJmUEiTf0I0MVUai
	X6O9rDJOjnoHBbi67+fgN0sn
	-----END PRIVATE KEY-----
	cisco@labvm:~$
	```
## Parte 3: generar y ver una clave pública.
1. Para generar una clave pública utilice el comando openssl pkey. El comando toma su private_key.pem como entrada y luego envía una clave pública (-pubout -out) a un archivo llamado public_key.pem.
	```shell
	cisco@labvm:~$ openssl pkey -in private_key.pem -pubout -out public_key.pem
	cisco@labvm:~$
	```
2. Utilice el comando `cat` para ver `public_key.pem`.
	```shell
	cisco@labvm:~$ cat public_key.pem
	-----BEGIN PUBLIC KEY-----
	MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAtXW+dFzmHg0wMhp0C0cB
	rrK+7rNDIuOIXxVJmot0B83pakQcTtOro7/XxcEPHuULGkFm6YfkVU0Abq/1ccub
	SFZFb1kKobMutMhxvfBQjQr3jo1j6aG12yMvrQudvSlaxHTvuDpMlhPY3IrBjkMz
	2Lx0SjjOC9uD3CzaMwu6JWnhRt0svH7n6cZNXDfIlsYpcjLg9JqKrWEO3Ooq05q1
	e2JEAuDOXte+M2O0ZC7cjSyxCiOfD2IEXkBq41H7xgIKTq2WJ8f+/RXEdC5Mx6Xx
	fu7pQXN9gT9LbUPlLJfUG7vTCs2d2AA6TBUyUuzH2mS61KwWcT8VRAWtWdr/sPSK
	AQIDAQAB
	-----END PUBLIC KEY-----
	cisco@labvm:~$
	```

## Parte 4: cree un nuevo documento que será firmado digitalmente.
1. Utilice el comando echo para crear un archivo de texto llamado contract.txt.
	```shell
	cisco@labvm:~$ echo Please transfer 2,000,000 US Dollars to Mr. Jester by 6pm today! > contract.txt
	cisco@labvm:~$
	```
2. Utilice el comando cat para ver el archivo contract.txt.
	```shell
	cisco@labvm:~$ cat contract.txt
	Please transfer 2,000,000 US Dollars to Mr. Jester by 6pm today!
	```

## Parte 5: use la clave privada para firmar digitalmente el nuevo documento.
1. Para firmar el documento use el comando openSSL dgst . El comando dgst puede tomar cualquier número de valores de resumen de mensaje. En este ejemplo utilizará SHA 256 y luego utilizará private_key.pem para generar una firma para el documento contract.txt.
	```shell
	cisco@labvm:~$ openssl dgst -sha256 -sign private_key.pem -out signature contract.txt
	cisco@labvm:~$
	```
2. Utilice el comando cat para ver el archivo de firma. El archivo es un archivo binario. Presionar Enter para obtener una nueva línea.
	```shell
	cisco@labvm:~$ cat signature
	H�&/J�c�M�$R�xpA��*t�>�ѣmr�C      jw��q]t'�#ot"%_B�X���~�k��p3����-���̣
	<output omitted>
	ROˤ    ��D?Nz�����f�<�H�~�P5nJ���hqG�&28Jcisco@labvm:~$
	```

## Parte 6: Verificar la autenticidad e integridad del documento.
La tecnología de firma digital permite al destinatario verificar la autenticidad e integridad del archivo. El proceso de verificación de la firma digital es para garantizar que un mensaje dado haya sido firmado por la clave privada que corresponde a una clave pública determinada.

Para verificar que el documento sea auténtico y no haya sido alterado, utilice el comando openSSL dgst con la opción verify y public_key.pem.
```shell
cisco@labvm:~$ openssl dgst -sha256 -verify public_key.pem -signature signature contract.txt
Verified OK
```

## Parte 7: simular un agente de amenaza cambiando el destinatario especificado en el archivo contract.txt.
1. Utilice gedit para abrir el archivo contract.txt.
	```shell
	cisco@labvm:~$ gedit contract.txt
	```
2. Cambie "Mr. Jester" por "Mr. Viper".
3. Haga clic en `File > Quit` y luego en `Save` en el cuadro de diálogo.

## Parte 8: Verifique que se haya comprometido la integridad del documento.
Vuelva a usar el comando openSSL dgst con la opción verify para validar que la verificación del documento ahora falla.
```shell
cisco@labvm:~$ openssl dgst -sha256 -verify public_key.pem -signature signature contract.txt
Verification Failure
cisco@labvm:~$
```