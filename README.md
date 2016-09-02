# HTTP (Protocolo de Tranferencia de Hipertexto)
Basicos
_________________________________________________________________
#### Introducción

_________________________________________________________________
#### La Web
Internet o la web es un sistema de informacíon distribuido masivo cliente/servidor como es representado en el siguiente diagrama.
![La web](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/TheWeb.png)

Muchas apliaciones estan corriendo actualmete sobre la WEB, tales como los navegadores Web, correos electronicos, transferencia de archivos, streaming de audio y video, y mucho mas. En orden de que una correcta comunicacíon tome lugar entre el cliente y el servidor, estas aplicaciones deben concordar en un nivel de aplicación de protocolo especifico tal como HTTP, FTP SMTP, POP, y etc.

### Protocolo de Tranferencia de Hipertexto (HTTP)

![HTTP](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP.png)

HTTP (Protocolo de Tranferecia de Hipertexto) es quiza la aplicacion de protocolo mas popular usada en internet (o la Web).

* HTTP Es un protocolo cliente-servidor de solicitud/respuesta asimetrica como se ilustra. Un cliente HTTP envia una mensaje de solicitud a un servidor HTTP. El seridor, en turno, regresa un mensaje de respuesta. En otras palabras, HTTP es un  protocolo de extraccion, el cliente extrae información del servidor (mientras que el servidor extrae información del cliente).

* HTTP is protocolo sin estado, En otras palabras la solicitud actual no sabe que se ha hecho en las solicitudes previas.
* HTTP permite negociar tipos de datos y representaciones, a fin de permitir que los sistemas se construyan de forma independiente de los datos que se transfieren .
* Citando de el RFC2616: "El protocolo de tranferencia de Hipertexto es un protocolo a nivel de aplicación usado por muchas tareas mas alla de su uso como hipertexto, tales como servidores de nombres y sistemas de gestión de objetos distribuidos, a través de la extensión de sus métodos de petición, códigos de error y headers.tales."

* Cada vez que se emite una dirección URL de su navegador para obtener un recurso web utilizando HTTP e.g. http://www.nowhere123.com/index.html, el navegador convierte la URL en un mensaje de solicitud y lo envia al servidor HTTP. EL servidor HTTP interpreta la solicitud del mensaje, y te regresa un mensaje de respuesta apropiado, ya sea el recurso que solicitaste o un mensaje de error. Este proceso se ilustra a continuación

![BROWSER](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_Steps.png)

### Localizador Uniforme de Recursos (URL)
Una URL(Localizador uniforme de recursos) es usado unicamente para identificar un recurso sobre la web. URL tiene el siguiente sintaxis:
~~~
 Protocolo://hostname:port/path-and-file-name
~~~

Hay 4 partes en una URL:
1. Protocolo: El protocolo de nivel de aplicación usado por el cliente y el servidor, e.g., HTTP, FTP, y telnet.
2. Nombre del host: El nombre del dominio DNS (e.g., www.nowhere123.com) o la dirección iṕ (e.g., 192.128.1.2) del servidor.
3. Puerto: El número de puerto del servidor que esta escuchando por solicitudes de entrada de los clientes.
4. Ruta - y nombre de archivo : El nombre y la ubicación del recurso solicitado , bajo el directorio base de documentos del servidor .

Por ejemplo, en la URL http://www.nowhere123.com/docs/index.html, el protocolo de comunicación es HTTP; el hostname es www.nowhere123.com. El número de puerto o se especifico en la URL, y toma el numero por default, el cual es el puerto 80 para HTTP. La ruta y el nombre del archivo para el recurso que se encuentra es " /docs/index.html " 

Otros ejemplos de URL son:

~~~
 ftp://www.ftp.org/docs/test.txt
mailto:user@test101.com
news:soc.culture.Singapore
telnet://www.nowhere123.com/
~~~

### Protocolo HTTP

Como se menciono, cuando sea que se ingresa una URL en la caja del navegador, el navegador traduce la URL a un mensaje de solicitud de acuerdo al protocolo especificado, y envia la solictud a el servidor.

Por ejemplo, el navegador traduce la URL http://www.nowhere123.com/doc/index.html en el siguiente  mensaje de solicitud:

> GET /docs/index.html HTTP/1.1
Host: www.nowhere123.com
Accept: image/gif, image/jpeg, */*
Accept-Language: en-us
Accept-Encoding: gzip, deflate
User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)
(blank line)

Cuando este mensaje de solicitud llega al servidor , el servidor puede tomar cualquiera de estas acciones:

1. El servidor interpreta la petición recibida , mapea  la solicitud en un archivo en el directorio de documentos del servidor , y devuelve el archivo solicitado al cliente .
2. El servidor interpreta la petición recibida , mapea la solicitud en un programa guardado en el servidor, ejecuta el programa , y devuelve la salida del programa al cliente.
3. La solicitud no puede ser satisfecha , el servidor devuelve un mensaje de error

Un ejemplo de una respuesta GTTP es la siguiente:

~~~
 HTTP/1.1 200 OK
Date: Sun, 18 Oct 2009 08:56:53 GMT
Server: Apache/2.2.14 (Win32)
Last-Modified: Sat, 20 Nov 2004 07:16:26 GMT
ETag: "10000000565a5-2c-3e94b66c2e680"
Accept-Ranges: bytes
Content-Length: 44
Connection: close
Content-Type: text/html
X-Pad: avoid browser bug
~~~  

> <html><body><h1>It works!</h1></body></html>

El servidor recibe el mensaje de respuesta, lo interpreta y despliega el contenido del mensaje en la ventana del navegador de acuerdo al tipo de respuesta (Como en la cabecera de respuesta Content-Type ) . tipo de medios comunes incluyen " text / plain " , "text / html " , "image / gif" , "image / jpeg " , " audio / mpeg " , "video / mpeg " , " aplicación / pdf " y "application / pdf " 

En su estado de reposo , un servidor HTTP no hace más que escuchar a la dirección (es) IP y el puerto ( s ) especificado en la configuración de solicitud entrante .Cuando llega una petición , el servidor analiza el encabezado del mensaje , aplica las reglas especificadas en la configuración , y toma la acción apropiada. El control principal del webmaster sobre las acciones del servidor son a través  de la configuración, el cual será tratado en mayor detalle en las secciones posteriores .

### HTTP over TCP/IP

HTTP es un protocolo a nivel aplicación cliente/servidor. Esta tipicamente corre sobre una conexión TCP/IP.  (HTTP no necesita correr sobre TCP/IP. Sólo se presume un transporte fiable . Cualquier protocolo de transporte que proporcionan este tipo de garantías se pueden utilizar . ) .

TCP / IP ( Protocolo de Control de Transmición /Protocolo de Internet ) es un conjunto de protocolos de transporte y capas de red para que máquinas se comuniquen entre sí a través de la red.
IP (Protocolo de internet) es un protocolo de capa de red , se ocupa de direccionamiento de red y enrutamiento . En una red IP , cada máquina se asigna una dirección IP única (por ejemplo, 165.1.2.3 ) , y el software de IP es responsable de encaminar un mensaje desde la fuente de IP a la dirección IP de destino. En IPv4 (versión 4 de IP ) , la dirección IP se compone de 4 bytes , cada uno de los rangos de 0 a 255 , separados por puntos , que se llama una forma de cuatro puntos.
Este esquema de numeración soporta hasta 4G electrónico de la red . La última IPv6 ( IP versión 6 ) soporta más direcciones . Como memorizar el número es difícil para la mayoría de las personas, un nombre de dominio Inglés -como , como www.nowhere123.com se utiliza en su lugar. El DNS ( Servicio de nombre de dominio) traduce el nombre de dominio a la dirección IP (a través de tablas de búsqueda distribuidas ) . Una dirección IP 127.0.0.1 especial siempre se refiere a su propia máquina . Su nombre dominio es " localhost " y puede ser utilizado para la prueba de bucle local.

![TCP/IP](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_OverTCPIP.png)

TCP (Protocolo de control de transmisión ) es un protocolo de capa de transporte , responsable de establecer una conexión entre dos máquinas. TCP consta de 2 protocolos: TCP y UDP ( Datagrama de paquete de usuarios ) . TCP es fiable , cada paquete tiene un número de secuencia , y se espera un acuse de recibo . Un paquete será retransmitido si no es recibido por el receptor . la entrega de paquetes está garantizado en TCP . UDP no garantiza la entrega de paquetes, y por lo tanto no es fiable. Sin embargo , UDP tiene menos sobrecarga de la red y se puede utilizar para aplicaciones tales como vídeo y audio streaming , donde la fiabilidad no es crítica .

TCP multiplexa aplicaciones dentro de una máquina IP . Para cada máquina de IP , TCP soportes ( multiplexa ) de hasta 65.536 puertos ( o enchufes ), desde el puerto número  0 hasta 65535. Una aplicación, tal como HTTP o FTP , se ejecuta (o escucha ) en un número determinado de puerto para las solicitudes entrantes . Puerto 0 a 1023 son pre - asignados a los protocolos populares , por ejemplo , HTTP a 80 , a los 21 FTP , Telnet a 23 , a 25 SMTP , NNTP en el 119 , y el DNS a los 53. El puerto 1024 y superiores están disponibles para los usuarios 

A pesar de que el puerto TCP 80 es pre - asignado a HTTP , como el número de puerto HTTP predeterminado , esto no significa que prohíbe la ejecución de un servidor HTTP en otro número de puerto asignado por el usuario ( 1024-65535 ), tales como 8000 , 8080 , especialmente como servidor de prueba . También se puede ejecutar varios servidores HTTP en la misma máquina en diferentes números de puerto . Cuando un cliente envía una URL sin indicar explícitamente el número de puerto
http://www.nowhere123.com/docs/index.html , el navegador se conectará con el número de puerto por defecto 80 de la acogida www.nowhere123.com . Es necesario especificar el número del puerto en la URL, por ejemplo, http://www.nowhere123.com:8000/docs/index.html si el servidor está escuchando en el puerto 8000 y no el puerto por defecto 80 .
En resumen , para comunicarse a través de TCP / IP , lo que necesita saber ( a) la dirección IP o el nombre de host , ( b ) number.r puerto.

### Especificaciones HTTP
La especificación HTTP se mantiene por el W3C ( Consorcio Mundial Web ) y disponible en http://www.w3.org/standards/techs/http . Actualmente hay dos versiones de HTTP , es decir , HTTP / 1.0 y HTTP / 1.1 . La versión original , HTTP / 0.9 (1991 ) , escrito por Tim Berners -Lee , es un protocolo simple de transferencia de datos en bruto a través de Internet . HTTP / 1.0 ( 1996 ) (definido en RFC 1945 ) , ha mejorado el protocolo permitiendo mensajes MIME - como . HTTP / 1.0 no se ocupa de los problemas de servidores proxy , almacenamiento en caché de conexión persistente, hosts virtuales , y el rango de descarga . Estas características se proporcionan en HTTP / 1.1 ( 1999 ) (definido en RFC 2616 ) .

##Servidor Apache HTTP o Servidor tomcat apache
__________________________________________________________________

Se necesita un servidor HTTP (como Apache HTTP Server o Apache Tomcat ) para estudiar el protocolo HTTP .

El servidor HTTP Apache es un servidor de producción industrial-fuerza popular, producida por Apache Software Foundation ( ASF ) @ www.apache.org . ASF es una base de software de código abierto . Es decir , el servidor Apache HTTP es libre, con el código fuente

El primer servidor HTTP fue escrito por Tim Berners Lee en el CERN ( Centro Europeo de Investigación Nuclear ) en Ginebra , Suiza , que también inventó HTML . Apache fue construido en NCSA ( National Center for Supercomputing Applications , EE.UU. ) " httpd 1.3 " servidor, a principios de 1995. Apache probablemente recibe su nombre del hecho de que consiste en un código original ( desde un servidor web httpd anterior NCSA ) además de algunos parches ; o del nombre de una tribu india americana .
Leer " Apache Cómo hacer " sobre cómo instalar y configuare servidor Apache HTTP ; o " Tomcat How-to " para instalar y empezar a trabajar con Apache Tomcat

## Mensajes de solicitud y respuesta HTTP
___
El cliente y el servidor HTTP se comunican mediante el envío de mensajes de texto. El cliente envía un mensaje de petición al servidor. El servidor, a su vez, devuelve un mensaje de respuesta .
Un mensaje HTTP consta de una cabecera de mensaje y un cuerpo de mensaje opcional , separados por una línea en blanco , como se ilustra a continuación:

![SOLICITUD Y RESPUESTA](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_MessageFormat.png)

###Petición de mensaje HTTP
El formato de un mensaje de petición es el siguiente:

![REQUEST](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_RequestMessage.png)

**Linea de petición**
La primera linea del encabezado es llamada linea de petición, seguida de encabezados opcionales de petición
 La linea de petición tiene la siguiente sintaxis:
~~~
request-method-name request-URI HTTP-version
~~~
* request-method-name:El protocolo define una serie de metodos de solicitud e.g., GET,POST, HEAD y OPTIONS. El cliente puede usar uno de estos metodos pra enviar una petición al servidor.
* request-URL: especifica la fuente solicitada
* HTTP- version: 2 versiones estan actualmente en uso: HTTP/1.0 y HTTP/1.1

Ejemplos de peticiones son:
~~~
GET /test.html HTTP/1.1
HEAD /query.html HTTP/1.0
POST /index.html HTTP/1.1
~~~

**Ecabezados de petición**

Los encabezados de petición estan en la forma del nombre: valores par, multiples, separados por comas, pueden ser especificados.
~~~
request-header-name: request-header-value1, request-header-value2, ...
~~~
Ejemplos de encabezados de solicitud son:
~~~
Host: www.xyz.com
Connection: Keep-Alive
Accept: image/gif, image/jpeg, */*
Accept-Language: us-en, fr, cn
~~~

**Ejemplo** 
El siguiente muestra un mensaje de petición HTTP simple:

![HTTP request message](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_RequestMessageExample.png)
###Mensaje de Respuesta
El formatode un mensaje de respuesta HTTP es el siguiente:
![R-M](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_ResponseMessage.png)

**Linea de estado**
La primera linea es llamada "the status line" seguida de encabezados  opcionales de solicitud
La linea de estado tiene la siguiente sintaxis
>HTTP-version status-code reason-phrase

* Versión HTTP: La versión HTTP usada en esta sesión.  Either HTTP/1.0 y HTTP/1.1.
* Código de estado: un número de 3 dígitos generado por un servidor refleja el resultado de la solicitud.
* razón Frase : da una breve explicación para el código de estado .
* código de estado común y la razón frase son " 200 OK " , " 404 Not Found " , " 403 Prohibido" , " 500 Internal Server Error " .

ejemplos de linea de estado son:

~~~
HTTP/1.1 200 OK
HTTP/1.0 404 Not Found
HTTP/1.1 403 Forbidden
~~~

### **Encabezados de respuesta**
Las cabeceras de respuesta están en la forma nombre : pares de valores:
~~~
response-header-name: response-header-value1, response-header-value2, ...
Ejemplos de respuesta de encabezados son:
 Content-Type: text/html
 Content-Length: 35
 Connection: Keep-Alive
 Keep-Alive: timeout=15, max=100
~~~
El cuerpo del mensaje de respuesta contiene la fuente de datos solicitada

**Ejemplo**
El siguiente muestra un mensaje de respuesta simple

![response](https://www.ntu.edu.sg/home/ehchua/programming/webprogramming/images/HTTP_ResponseMessageExample.png)

