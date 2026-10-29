Estudio Dia 2 Semana 5 DNS y Curl

DNS: DOMAIN NAME SYSTEM o nombre de dominio del sistema es el sistema que permite consultar información asociada a nombres de dominio incluidas direcciones IP

la ruta de conexión indicaría la siguiente

VM o Maquina local ----> DNS (dirección asociada al nombre) ----> Servidor de destino

Este esquema es simplificado: puede haber cachés y otros componentes entre los pasos. Además, resolver un dominio no garantiza que el servidor web esté disponible. La resolución DNS y la comunicación HTTP son etapas diferentes.

Conceptos que debes aprender

- Dominio: nombre legible, como example.com.
- Resolución DNS: consulta que obtiene información asociada al dominio.
- Registro A: asocia un nombre con una dirección IPv4.
- Registro AAAA: asocia un nombre con una dirección IPv6.
- Caché DNS: conserva respuestas durante un tiempo para evitar consultas repetidas.
- Servidor DNS: componente que responde consultas DNS o ayuda a resolverlas.

Que se debe entender por HTTP y HTTPS
-HTTP: protocolo que define cómo un cliente solicita recursos y cómo un servidor responde.
-HTTPS: HTTP protegido mediante TLS, que proporciona cifrado y autenticación del servidor

Curl: Envía una solicitud HTTP o HTTPS.
Servidor Web: Devuelve un código de estado, cabeceras y, habitualmente, un cuerpo de respuesta.

Hay tres conceptos especialmente importantes:

- Código de estado: indica el resultado de la solicitud desde la perspectiva HTTP. Por ejemplo, 
	 200 indica éxito, 
	 301 o 302 indican redirección y 
	 404 indica que el recurso solicitado no se encontró.
- Cabeceras (headers): contienen metadatos sobre la solicitud o respuesta.
- Cuerpo (body): contiene el contenido devuelto, como HTML, JSON u otros datos.

Curl -I https://example.com

Entrega las cabeceras y los valores que deben investigar
HTTP/ ----> Codigo de estado y versión de HTTP indicada en la respuesta
content-type ----> Tipo de contenido devuelto
content-length ----> Longitud del contenido, si se proporciona
Date ----> fecha indicada por el servidor
Server ----> información del servidor que responde, si se expone
location ---->Destino indicado cuando utiliza una redireccion

curl -v https://example.com

Muestra la información adicional sobre la comunicación como detalles de la conexión y de la solicitud


Laboratorio

Se utilizara un dominio reservado: example.com

1.- getent hosts example.com
Consola: 2606:4700:10::6814:179a    example.com
	 2606:4700:10::ac42:93f3    example.com
¿Se obtuvo una respuesta?
Si se obtuvo respuesta
¿Qué dirección o direcciones aparecieron?
en la consulta se lograron obtener 2 direcciones (2606:4700:10::6814:179a / 2606:4700:10::ac42:93f3)
¿Qué tipo de dirección IP observé?
Se observaron direcciones IPv6
¿Qué puedo concluir?
No tendría claridad y que se puede concluir

2.- resolvectl query example.com
Resultado obtenido: 104.20.23.154
	 	    172.66.147.243
	 	    2606:4700:10::6814:179a
		    2606:470:10:ac42:93f3
Diferencias observadas: se puede observar IPv4 y IPv6
Conclusión: el DNS indicado permite en consulta IPv4 y IPv6

3.- curl https://example.com
¿Qué contenido apareció?
El contenido de la pagina HTML del DNS
¿Qué información obtuve?
La cabecera y el cuerpo de la plataforma
¿Qué información no apareció directamente?
El código de Estado, el cual indicaría si la plataforma se encuentra disponible, con lentitud o con problemas

4.- curl -I http://example.com
Código de estado: 200 ok
Cabeceras identificadas: date, content-type, connection, server, last modified, Allow, Accept ranges, age, CF-cache-status, cf-ray,alt-svc
Significado de las cabeceras: 
Date: fecha indicada en el servidor
content tipe: tipo de contenido
Connection: tipo de protocolo HTTP
server: tipo de servidor
Last modified: ultima modificación de la pagina o DNS
Allow: los permisos permitidos que tenemos sobre la plataforma
Accept ranges:  tipo de datos aceptados
Age: edad
cf-cache-status: Indica si Cloudflare utilizó una copia almacenada en caché
cf-ray: Permite identificar y rastrear una solicitud procesada por Cloudflare.
alt-svc: Anuncia protocolos y puertos alternativos disponibles para la comunicación.

Observaciones: al aplicar dicho comando, aparecieron bastantes cabeceras mas de las que se estudiaron en primera instancia

5.- curl -v https://example.com
Información relevante de la conexión: permite conocer y verificar pruebas de conectividad y respuesta al DNS indicado
Resultado de la solicitud: Respuesta detallada de la conectividad, IPv4 y IPv6 de dicho DNS entre otras cosas
Errores o advertencias, si aparecieron: no existieron mensajes de este tipo

6. Análisis
¿Qué relación existe entre DNS y HTTP?
DNS corresponde al nombre del dominio que un defina y el HTTP, es la respuesta al sitio web con el protocolo correspondiente
¿Qué diferencia hay entre una cabecera y el cuerpo de una respuesta?
La cabecera nos entrega la información principal de los protocolos y los aceptables del DNS y el cuerpo nos entrega toda la información detallada de pruebas de conexión y respuesta de dicho sitio
¿Qué evidencias permiten determinar si la solicitud tuvo éxito?
en ambos casos curl -I o -v, se puede obtener una solicitud o 200 o con alguna otra respuesta
¿Qué investigaría si la solicitud fallara?
aplicaría el cur -v y analizaría a detalle los mensajes que me entregaría la consola para poder ir determinando cual es el problema que se podría estar presentando 


7.- Conclusión

Se logro aprender que
Dns se define como el nombre de dominio que uno le da a la plataforma donde uno realizara una petición de información
HTTP/HTTPS, explica los medios de respuesta y protección que se puede utilizar en una plataforma
El uso de curl, permite la observación de los campos tanto específicos como análisis en detalle de toda la data que pueda entregar el DNS, con la finalidad de obtener un análisis o informe mas detallado, esto con el fin de lograr identificar componentes, warning o fallas que pueda presentar
