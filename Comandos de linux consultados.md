Comandos Basicos de Linux a tener siempre en cuenta 

- man [command]: al llamar este comando, se puede obtener el manual completo del comando indicado por ejemplo : man ls, este comando traerá todo el manual de ls
- ls: listar todos los archivos y directorios en la ruta que te encuentras, si ejecutas este comando ls [ruta], te mostrara lo que se encuentra en la ruta especificada
- cd: Permite cambiar de directorio donde te encuentras actualmente
- pwd: imprime la ruta del directorio donde te encuentras actualmente
- mkdir [Archivo/carpeta]: Crear carpetas y/o archivos con este comando, cabe mencionar que con este solo comando se pueden crear varias a la vez
- rmdir [carpeta]: Eliminar carpetas con este comando, cabe recalcar que para utilizar este comando, la carpeta debe estar vacia
- mv [archivo] [NuevaRuta/nuevonombre]: comando para mover archivos a otra ruta como para renombrar el mismo
- cp [Archivo] [NombreotroArchivo/ruta]: Comando para copiar, se puede copiar dentro de la misma ruta o dentro de otro directorio
- open [Archivo o directorio]: te permite abrir un archivo (ojo que este comando es mas de MacOS que de Linux)
- touch [Archivo]: Creación de archivos Vacios, si existe el archivo en tema, actualiza la marca de tiempo 
- find: Busca archivos y directorios a partir de una ubicación y permite aplicar diferentes criterios de búsqueda.
- ln: se utiliza para crear enlaces, que es un enlace, es un puntero a otro archivo, o un archivo que apunta a otro archivo
	- existen 2 tipos de enlaces Hard link y soft link:
		- Hard link: Se crea ln [original] [link], tiene limitaciones, no se puede enlazar a directorios y no se puede enlazar a sistemas de archivos externos
		- Soft link: Se crea ln -s [original] [link], tiene mas posibilidades , se puede enlazar con otros sistemas y/o directorios, pero siempre a tener en cuenta, cuando se 					elimina el original, el enlace se rompe.
- gzip [filename]: se puede comprimir un archivo usando el protocolo de compresión llamado LZ77, cuando se genera el archivo .gz, el original, se elimina, existen extensiones que permiten que esto no se genere asi
- gunzip [filename.gz]: Realiza la eliminación de la extensión .gz, descomprimiendo por la data original
- tar: permite agrupar múltiples archivos y directorios en un único archivo, llamado archivo tar.
- alias: se utiliza para crear atajos de comandos que uno desee crear, ejemplo: " alias ll='ls -al' ", esto genera que cada vez que se utilice el comando ll, se realice la accion que se puede obtener con el comando indicado
- cat: Muestra el contenido de uno o varios archivos y también permite concatenarlos.
- less: permite visualizar archivos grandes página por página, sin cargar todo el contenido de manera práctica en la terminal.
- Tail: Este comando te permite visualizar las ultimas 10 líneas de archivo indicado, a diferencia de Cat, este permite ver cambios del archivo en tiempo real
- wc: Se utiliza para contar elementos dentro de archivos o entradas de texto, este comando puede contar líneas, palabras, bytes y caracteres
	Ejemplo: El archivo a revisar es archivo.txt el cual contiene el siguiente mensaje:
		Hola mundo
		Estoy aprendiendo Linux
		DevOps es interesante
	Aplicando el comando wc archivo.txt, el comando retornaría los siguiente:
		3 8 54 archivo.txt, lo cual indica que el archivo tiene 3 líneas, 8 palabras y 54 bytes
- grep: Busca coincidencias de texto o patrones dentro de archivos o de una entrada recibida por la terminal.
	grep "texto_a_buscar" archivo
- sort: Ordena líneas de texto.
- uniq: sirve principalmente para eliminar líneas consecutivas duplicadas. 
- diff: Compara dos archivos y muestra las diferencias entre ellos.
- echo: imprime por terminal la salida del argumento que le pasaste
- chown [username] [filename]: (change owner) permite cambiar el propietario y/o grupo propietario de un archivo o directorio. En Linux, cada archivo y directorio 
tiene asociado un usuario propietario y un grupo, los cuales determinan sobre quiénes se aplican los permisos definidos mediante chmod.
- chmod: (change mode) permite modificar los permisos de acceso de archivos y directorios. Estos permisos determinan qué puede hacer el propietario, el grupo y los demás usuarios sobre un recurso.Ejemplo: 
	drwxr-xr-x@ 13 Flavio staff   416  Feb 17 2020 ./
	Desglosando la data vemos que, el primer carácter indica que tipo de archivo es, 
		d corresponde a directorio
		- corresponde a archivo normal
		l corresponde a un enlace
	Los tres permisos principales son:
		Permiso	Significado
		r	Read → leer
		w	Write → escribir/modificar
		x	Execute → ejecutar

		Y existen tres grupos a los que se pueden aplicar:

		Símbolo	Significado
		u	User → propietario
		g	Group → grupo
		o	Others → demás usuarios
- umask: define qué permisos se restringen por defecto cuando se crean nuevos archivos y directorios
- du: permite calcular el tamaño de un directorio, dependiendo como se utilice puede traerte la data en detalle o solo el valor en byte
- df: se utiliza para traer la data de como se esta utilizando el disco, con el comando "df -h", se puede obtener la data mas legible 
- basename: segun como entregue una ruta, este comando te entrega el ultimo valor que se pueda encontrar en dicha ruta, puede ser un archivo o un directorio
- dirname: con este comando, si se le entrega una ruta, con un termino de archivo texto, te entregara la ruta de los directorios antes de llegar a dicho archivo
- ps: si actualmente te encuentras corriendo muchos procesos, con este comando puedes listarlos todos
- top: se utiliza para mostrar en tiempo real de forma dinamica los procesos que se encuentran ejecutando en el sistema
- kill: Enviar una señal a un proceso.
	kill -HUP - colgar / kill -INT -interrumpir / kill -KILL - no envia el kill al proceso, lo envia al SO, que lo detiene y termina / 
	kill -TERM - terminar / kill -CONT - continuar / kill -STOP - no envia el kill al proceso, lo envia al SO, lo detiene pero NO lo termina
- killall [name]: Envía una señal a los procesos que coinciden con un nombre determinado.
- jobs: muestra los trabajos iniciados desde la terminal actual que están ejecutándose, detenidos o en segundo plano.
- bg: Permite continuar en segundo plano un trabajo que estaba detenido.

- fg: Permite continuar en primer plano un trabajo que estaba detenido
- type: nos puede permitir identificar una de las 4 siguientes opciones: un ejecutable, un programa incorporado en Shell, una función Shell, un alias
