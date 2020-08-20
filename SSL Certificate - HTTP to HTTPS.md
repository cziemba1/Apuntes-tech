# SSL Certificate - HTTP to HTTPS

Created: Aug 12, 2020 3:55 PM
Reviewed: No

**Symmetric Encryption**: la info esta encriptada usando una key, y la misma se transfiere ya encriptada, en ambos lados la key es la misma, mediante la cual se desencripta para accceder a la data. Si utilizan la misma key, se llama DES algoritmo (Obsoleto) o 3DES (Obsoleto).

Un algoritmo mas moderno se llama Advance Encryption System AES, que permite utilizar una key con ditintas longitudes (tambien simetrico, pero mas seguro). Siempre utilizar con la key mas larga.

**HASH:** string de una longitud fija, que utiliza un algoritmo para la encriptacion. La data es de variable longitud, cuando la hash funcion es aplicada, crea un hash de una longitud fija. Es de un solo sentido, puedo crear hash from data, pero no crear data from hash. No necesitan ninguna key, solo la funcion hash, son opcionales, le agregan sender authentication

Como funciona?: la data se envia junto con la hash. Cuando se recibe, la data se convierte a hash y se compara esa hash creada con la hash que se recibio. La encriptacion se hace previa a la hash. Si las hash no son iguales, se cancela la transferencia de info.

Hashing algoritmos:

1. MD5: output 128bit, no es el mejor. Tipico hash funcion previamente descripta, utilizado para almacenar las claves por ejemplo. La longitud de los hash son siempre 128 bits, pero cambia cuando se cambia la data
2. SHA: existen 3 tipos: SHA-1 (160bits), SHA-256 (256 bits) mas popular, SHA-512 (512 bits). Idem anterior
3. HMAC: data + secret key para generar el hash (ayuda con la autenticacion del sender)

**Asymmetric Encryption**: Dos keys con misma length: private(utilizada para encriptar data, siempre secret, lo sabe solo el owner, y solo el crea la hash) y public (disponible para cualquiera). ⇒**RSA**

Como funciona? El owner solamente sabe la private key, pero tambien conoce la public. El sender envia la data con la public key. Todos pueden verla, pero solo el owner de la private key puede desencriptarla: todos pueden enviarme mails, pero yo solo puedo leer esos mails. ⇒ data signature, nosotros nos aseguramos que la data es la que envio el owner, ya que el solo tiene la private key al generar el hash.

**PKI**: Public Key Infraestructure, diferentes protocolos, algoritmos, que permiten la comunicacion mediante trust y certificaciones: CA (certification authoritie), Intermediate CA (signature certificate). Los certificados contienen info, **contienen la public key del dueño del certificado**, info about el owner (nombre de la compañia, etc), info sobre el issuer (autoridad de la certificacion), la signature con asymmetric key: si la certificacion es firmada por el CA, y confiamos en CA, tambien confiamos en el dueño del certificado. 

Tambien existen self signed certificate: issued and signed by owner

DNS: domains donde el certificado es valido

[https://www.geocerts.com/ssl-checker](https://www.geocerts.com/ssl-checker) para chequear la chain de trust entre el owner y el issuer del certificado

[https://www.ssllabs.com/](https://www.ssllabs.com/) mas detallado y util con calificacion

![SSL%20Certificate%20-%20HTTP%20to%20HTTPS%20caf777592158438992fc04bdaa3d2cf4/Untitled.png](SSL%20Certificate%20-%20HTTP%20to%20HTTPS%20caf777592158438992fc04bdaa3d2cf4/Untitled.png)

**Cryptograhic protocol** ⇒ encriptacion de data. Hay dos tipos:

- SSL: Secure Socket Layer
- TLS: Transport Layer Security

Los certificados no dependen del certificado pueden usar uno u otro o ambos

![SSL%20Certificate%20-%20HTTP%20to%20HTTPS%20caf777592158438992fc04bdaa3d2cf4/Untitled%201.png](SSL%20Certificate%20-%20HTTP%20to%20HTTPS%20caf777592158438992fc04bdaa3d2cf4/Untitled%201.png)

Los protocolos en rosas ya estan deprecados, no utilizar.

Para la encriptacion de informarcion en HTTPS, no se utiliza RSA, ya que es lento y requiere las key pairs (public y private) en ambos lados, es decir, en el web browser y en el web server.

Se utiliza TLS, symmetric key:

![SSL%20Certificate%20-%20HTTP%20to%20HTTPS%20caf777592158438992fc04bdaa3d2cf4/Untitled%202.png](SSL%20Certificate%20-%20HTTP%20to%20HTTPS%20caf777592158438992fc04bdaa3d2cf4/Untitled%202.png)

1- Se negocia el cipher suite (protocolo a utillizar ,etc): el web brower (cliente) contiene un listado de ciper suite (cada uno contiene un tipo de algoritmo de encriptacion, un tipo de hash, el tipo de protocolo) y el webserver (server) elije uno para realizar el handshake ⇒ Client Hello, Server Hello.

2- El webserver envia el certificado ⇒ handshake protocolo: certificate. Envia toda la cadena de certificados menos el root, que ya lo tiene el cliente.

3- Web browser verifica el certificado (signature, period, certificate revokation)

4- Si todo ok, se genera la symmetric key. A veces el web browser genera la key y se la envia encriptada al web server, otras veces se utiliza un algoritmo de encriptacion que genera una coneccion privada entre ambas partes. Handshake protocolo: Server key exchange "Server Hello Done". Osea, el servidor ya le envio todo y genero la key. El cliente recibe el algoritmo de generacion de la key, un mensaje encriptado + encrypted application data. AMBOS YA CONTIENEN LA KEY ENCRIPTADA

5- Se envia y recibe data encriptada en ambas partes

**Cipher Suites**: TLS + Info sobre donde se genera la key - si el lado del cliente o del servidor - y el tipo de algoritmo utilizado + encription (AES o CHACHA) + hash algorithm

![SSL%20Certificate%20-%20HTTP%20to%20HTTPS%20caf777592158438992fc04bdaa3d2cf4/Untitled%203.png](SSL%20Certificate%20-%20HTTP%20to%20HTTPS%20caf777592158438992fc04bdaa3d2cf4/Untitled%203.png)

RSA key pair is "static" and it is not changed until certificate is renewed ⇒ debe evitarse cuando se pueda. Solo deberia utilizarse solo para server authentication, no para encriptacion de data o secure key.

ECDHE utiliza Diffie Hellman algoritmo.

![SSL%20Certificate%20-%20HTTP%20to%20HTTPS%20caf777592158438992fc04bdaa3d2cf4/Untitled%204.png](SSL%20Certificate%20-%20HTTP%20to%20HTTPS%20caf777592158438992fc04bdaa3d2cf4/Untitled%204.png)

No se utiliza public key del webserver para la encriptacion de data. DF algoritmo realiza la generacion de la key en ambos lados mediante una conexion publica y segura.