Estudio Semana 6 dia 4
Contenido: Request, response, methods, status codes, TLS a nivel conceptual.

Request/response(solicitud/respuesta): Esta es la forma técnica para entender la respuesta de cliente/servidor

	- Cliente: puede ser el navegador o una aplicación que solicita información
	- Servidor: recibe la solicitud, procesa y devuelve una respuesta

Cliente ----> HTTP Request ---->Servidor <---- HTTP Response <---- Cliente

- Cliente: Navegador, Solicita una pagina web
- HTTP Request: Método + ruta + headers + body(si corresponde)
	- Método: que quieres hacer(GET+POST,etc)
	- Ruta: que recurso necesitas, por ejemplo /usuarios
	- Headers: información adicional sobre la solicitud, como el tipo de 	contenido aceptado
	- Body: datos que envias al servidor
- Servidor: Nginx/Apache/Aplicación, procesa la solicitud
- HTTP Response: Status + headers + body (si corresponde)
- Cliente: Recibe la respuesta

Metoto HTTP 
Los métodos indican qué acción quieres realizar sobre un recurso del servidor.

Método	Función					Ejemplo
GET	Consultar información.			Obtener una lista de usuarios.
POST	Enviar datos o crear un recurso.	Registrar un usuario.
PUT	Reemplazar un recurso completo.		Actualizar todos los datos de un usuario.
PATCH	Modificar parcialmente un recurso.	Cambiar solamente su correo.
DELETE	Eliminar un recurso.			Eliminar un usuario.

Una forma sencilla de recordarlos:
- GET = Leer.
- POST = Crear o enviar.
- PUT = Reemplazar.
- PATCH = Modificar parcialmente.
- DELETE = Eliminar.

Códigos de estado HTTP (Status Codes)
Cuando el servidor responde, utiliza un código numérico para indicar qué ocurrió con la solicitud.

Existen cinco grandes categorías:
2xx: Éxito
La solicitud se procesó correctamente.
Ejemplo: 200 OK: respuesta correcta.

3xx: Redirección
El cliente debe seguir otra ubicación o utilizar una respuesta almacenada.
Ejemplo: 301: redirección permanente. 302: redirección temporal.

4xx: Error del cliente
Existe un problema con la solicitud o los permisos.
Ejemplo: 403 Forbidden: acceso denegado. 404 Not Found: recurso no encontrado.

5xx: ror del servidor
El servidor o algún componente que utiliza no pudo completar la solicitud.
Ejemplo: 500: error interno. 502: respuesta inválida de un servidor upstream. 503: servicio no disponible.

HTTPS = HTTP dentro de TLS
Primero, diferenciemos ambos conceptos:
- HTTP: protocolo utilizado para comunicar clientes y servidores web.
- HTTPS: utiliza HTTP protegido mediante TLS (Transport Layer Security).
¿Qué aporta TLS?

1. Cifrado: Evita que terceros puedan leer fácilmente la información que viaja entre el cliente y el servidor.
Por ejemplo, cuando ingresas información en una página HTTPS, el tráfico viaja cifrado.

2. Autenticación del servidor: El servidor presenta un certificado digital que permite verificar su identidad y que está asociado al dominio correspondiente.
Este certificado normalmente está firmado por una autoridad certificadora (CA).

3. Integridad: Permite detectar modificaciones no autorizadas del tráfico durante la comunicación.

Comparación HTTP y HTTPS
HTTP: Comunicación sin cifrado TLS.
Puerto habitual: 80.

HTTPS: Comunicación protegida mediante TLS.
Puerto habitual: 443.

Laboratorio
Tarea: Usar curl para GET/headers y documentar 200/301/404/500.

1.- Realizar un curl -I https://example.com

2.	Mira la conversación completa e identifica la línea de request, Host, User-Agent, el status y Content-Type:
curl -v https://example.com 2>&1 | head -40

3.	Provoca y documenta cada código (200, 301, 404, 500):
curl -s -o /dev/null -w "%{http_code}\n" https://httpbin.org/status/200
curl -sI http://github.com | head -3          # redirección a https
curl -s -o /dev/null -w "%{http_code}\n" https://httpbin.org/status/404
curl -s -o /dev/null -w "%{http_code}\n" https://httpbin.org/status/500

4.	Si httpbin no responde, anótalo y usa tu Nginx de la semana 5 para el 200 y el 404 (curl -I http://localhost/no-existe).

5.	Compara GET con POST:
curl -s https://httpbin.org/get
curl -s -X POST -d "nombre=juan" https://httpbin.org/post
6.	Mira el certificado TLS (emisor y vigencia):
echo | openssl s_client -connect example.com:443 -servername example.com 2>/dev/null | openssl x509 -noout -subject -issuer -dates

	Esta consulta entrega los headers 

2.- 
