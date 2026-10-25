EStudio

Que es Nginx: es un software que puede funcionar como servidor Web, proxy inverso y balanceador de carga


Laboratorio

Etapa 1 — Instalar y reconocer Nginx
Primero actualiza la información de los paquetes e instala Nginx:
sudo apt update
sudo apt install nginx


Después revisa su estado:
systemctl status nginx


Y valida que la configuración sea correcta:
sudo nginx -t


Qué debes aprender de esta etapa:
- systemctl status nginx: permite conocer el estado del servicio.
- sudo nginx -t: comprueba la sintaxis de la configuración.
- active (running): indica que el servicio está activo en ese momento.
Si el servicio está instalado pero detenido, puedes iniciarlo con:
sudo systemctl start nginx


Etapa 2 — Comprobar la respuesta HTTP
Ejecuta:
curl -I http://localhost


Este comando solicita las cabeceras HTTP de la página local.
Luego ejecuta:
curl http://localhost


Este segundo comando muestra el contenido de la respuesta.
Tu objetivo no es solamente obtener un resultado: debes reconocer el código HTTP, las cabeceras que aparecen y el contenido que devuelve el servidor.
Etapa 3 — Crear tu propia página estática
Vamos a crear una página HTML sencilla dentro del directorio web habitual de Ubuntu.
Primero, crea un archivo de respaldo de la página predeterminada si existe:
if [ -f /var/www/html/index.nginx-debian.html ]; then
    sudo cp /var/www/html/index.nginx-debian.html /var/www/html/index.html.bak
fi


Ahora abre un editor para crear tu página:
sudo nano /var/www/html/index.nginx-debian.html


Introduce el siguiente contenido:
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi primer servidor Nginx</title>
</head>
<body>
    <h1>Mi primer servidor web</h1>
    <p>Estoy aprendiendo Linux y DevOps.</p>
    <p>Esta página está servida mediante Nginx.</p>
</body>
</html>


Guarda el archivo en Nano con Ctrl + O, pulsa Enter y sal con Ctrl + X.
Comprueba que el archivo existe:
ls -l /var/www/html/index.nginx-devian.html


Vuelve a consultar la página:
curl http://localhost


Resultado esperado: deberías ver el HTML de tu propia página en la terminal.
También puedes abrir http://localhost en el navegador de Ubuntu para observar cómo se representa visualmente.
Etapa 4 — Investigar los logs de Nginx
Ahora vamos a conectar lo que aprendiste en el día anterior sobre registros y diagnóstico de servicios.
Primero, observa las últimas solicitudes registradas:
sudo tail -n 10 /var/log/nginx/access.log


Después, revisa los mensajes de error:
sudo tail -n 10 /var/log/nginx/error.log


Para observar cómo aparecen nuevas solicitudes en tiempo real, puedes ejecutar:
sudo tail -f /var/log/nginx/access.log


Déjalo abierto y, desde otra terminal, ejecuta:
curl http://localhost


Observa qué nueva línea aparece. Para detener la visualización en tiempo real, pulsa Ctrl + C.
La documentación de Nginx explica que el registro de acceso y el de errores cumplen funciones distintas en el diagnóstico. 

NGINX Documentation



Etapa 5 — Provocar y analizar un error HTTP controlado
Ahora vamos a investigar un caso común: solicitar una página que no existe.
Ejecuta:
curl -i http://localhost/pagina-inexistente


Observa el código de estado que devuelve el servidor.
Después revisa el registro de acceso:
sudo tail -n 10 /var/log/nginx/access.log


Busca la solicitud que acabas de realizar y responde:
- ¿Qué ruta solicitaste? localhost/ruta-inexistente
- ¿Qué código HTTP recibiste? error 404
- ¿Qué información adicional aparece en el registro? el servicio se encuentra activo pero no encuentra la ruta especificada


Importante: una respuesta 404 Not Found no significa necesariamente que Nginx esté caído. Puede indicar que el servidor funciona correctamente, pero que el recurso solicitado no existe.
No esperes necesariamente encontrar ese 404 en error.log: el registro de acceso suele ser el lugar principal para comprobar la solicitud y su código de respuesta.
