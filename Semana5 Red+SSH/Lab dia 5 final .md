Laboratorio Final dia 5 Semana 5 (en este laboratorio se junto todo de lo de las semanas anteriores para revisar estudio)

1.- Se generan directorios en rama Devops-labs en VM Ubuntu
	- sudo mkdir semana5
2.- Dentro de este directorio se crean los siguientes directorios(usuarios, esto con la finalidad de indicar a quien le corresponde que)
	- sudo mkdir juan
	- sudo mkdir maria
3.- Dentro de cada usuario se genera lo siguiente
	- sudo mkdir proyecto-lab
4.- Dentro de proyecto lab se genera las siguientes 3 
	- web
	- logs
	- documentación

Se genera este orden con la finalidad de
	1.- Definir en que semana nos encontramos
	2.- En caso de generar usuario e ingresar con ese, definir quien esta realizando la prueba 
	3.- Definir el orden correspondiente del proyecto y sus subdirectorios

5.- Para no generar un archivo nuevo, desde la ruta /var/www/HTML, se copia el archivo HTML que se encuentra en dicha ruta
	- sudo cp index.html.bak ~/devops-lab/semana5/juan/proyecto-lab/web/proyecto.html

6.- En el directorio donde se copio el archivo HTML se encuentra lo siguiente
	-Archivo.html copia
	- Archio CSS que se genero 
7.- Verificando que ambos archivos también esten en la carpeta de maria, se copian con la finalidad de dejar el mismo contenido en esa carpeta
	- sudo cp proyecto.html ~/devops.lav/semana5/maria/proyecto-lab/web/presentación.html
	- sudo cp style.css ~/devops.lav/semana5/maria/proyecto-lab/web/style.css

8.- Se generan los nuevos usuarios juan y maria y con sus respectivas contraseñas 
	-sudo useradd juan
	-sudo useradd maria
	-sudo passwd juan
	-sudo passwd maria

9.- Para poder utilizar el terminal en ambos usuarios, se genera la ruta home que no se genero al principio
	- sudo mkdir -p home/juan
	- sudo chown juan:juan /home/juan
	Este comando se utiliza también con el usuario maria, cambiando el valor juan por maria

10.- Se agrega el grupo WebAdmin el cual se agrega a juan y maria a dicho grupo
	- sudo grpadd WebAdmin
	- sudo usermod -aG WebAdmin juan
	- sudo usermod -aG WebAdmin maria

11.- En la carpeta proyecto-lab se le cambia el owner y el grupo asignado, además se le asignan nuevos permisos según corresponde
	- sudo chown juan proyecto-lab
	- sudo chmod 750 proyecto-lab, se le aplica estos permisos con la finalidad de, usuario owner, todos los permisos, grupo solo lectura y ejecución, personal ajeno a esto no puede hacer nada ni ver, leer o ejecutar

12.- Se corrige el permiso de lectura y ejecución sobre el home/vboxuser , ya que no permitia ingresar normalmente ya que la carpeta al ser creada en el devops-lab, esta pertenece a vboxuser, y este usuario no tenia permitido la lectura y ejecución de otros a sus rutas
	-sudo chmod 755 vboxuser

13.- Se realiza la modificación de los owner de las carpetas documentación y logs
	-sudo chown juan documentación
	-sudo chown juan logs
	También se valida que los usuarios solo pueden leer y ejecutar 

14.- Se realiza la instalación de nginx y si el servicio se encuentra corriendo
	- sudo install apt nginx
	- systemctl status nginx
	
15.- Se envia los archivos de la carpeta Web del usuario juan
	- sudo cp proyecto.html /var/www/HTML/proyecto.html
	- sudo cp style.css /var/www/HTML/style.css

16.- Se elimina el archivo original de nginx y se renombra el nuevo, esto con la finalidad de probar el código que se aplico en archivo nuevo
	- sudo rm index.nginx-debian.html
	- sudo cp proyecto.html /var/www/HTML/index.nginx-debian.html

17.- Se modifica el archivo default del servicio Nginx
	- cd etc/nginx/sites-available
	- sudo nano default
18.- Se elimina ruta antigua y se agrega nueva y se agrega nombre de archivo HTML a tomar en cuenta con archivo CSS
	- /var/www/miapp
	- proyecto.html
	- style.css

19.- Se crea ruta y archivo de configuración correspondiente para montar HTML local y se escuche en puerto 80
	-sudo nano /etc/nginx/sites-available/miapp
	En dicho archivo se dejara las configuraciones correspondientes y las que escuchara el localhost

20.-Se habilitara el nuevo sitio
	-sudo ln -s /etc/nginx/sites-available/miapp /etc/nginx/sites-enabled

21.- Deshabilitamos el sitio por defecto
	- sudo rm /etc/nginx/sites-enabled/default

22.- Comprobamos y reiniciamos
	-sudo nginx -t
	-sudo systemctl restart nginx

23.- Verificamos localhost

24.- Se deja al usuario juan como owner:owner de la ruta miapp donde se encuentra el archivo HTML
	-sudo chown -R juan:juan /var/www/miapp

25.- Se modifican los permisos de dicha ruta
	- sudo chmod -R 755 /var/www/miapp



Dentro de todo el laboratorio se realizaron las siguientes acciones
- Se crearon directorios con los nuevos archivos HTML y css
- Se modificaron y se crearon usuarios
- Se instalo el servicio nginx
- Se verifico y se corrio de forma local la nueva plataforma
- A dicha plataforma se le asignaron nuevos permisos y owner
- Se revisaron los accesos y los logs de los archivos 
- SE revisaron status, activaciones, detenciones y pruebas de servicios
- Se aplicaron cambios a la configuración por default de servicio nginx
