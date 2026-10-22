Dia 3 Semana 5 SSH 

Estudio

Que es SSH o secure Shell, es un protocolo que permite conectarse a otra maquina a través 
de una conexión cifrada para ejecutar comandos y administrar el sistema de forma remota

Ejemplo: Mi maquina Ubuntu ---> SSH -----> VM Remota

Conceptos
- Cliente SSH: desde donde se inicia la conexión 
- Servidor SSH: donde se recibe las conexiones remotas, en caso de Ubuntu normalmente se llama SSHD
- IP: la dirección de red a donde conectarse
- puerto: el punto de comunicación, normalmente se utiliza el puerto TCP 22, aunque puede configurarse otro
- usuario remoto: cuenta con la que se inicia sesión 
- cifrado: protege la comunicación para que no viaje en texto legible por la red

Estructura: 
-	ssh usuario@IP_DEL_SERVIDOR

Autenticación: contraseña frente a clave SSH
SSH necesita comprobar que eres quien dices ser. Puede hacerlo mediante distintos métodos de autenticación 

- Autenticación por contraseña: Método normal el cual si la contraseña ingresada es correcta, el servidor se conecta
- autenticación por clave publica y privada: Genera un par de claves, la publica se instala 

Las claves suelen generarse por ssh-keygen, se pueden encontrar este tipo de archivos
- Archivo		  Función
- ~/.ssh/id_ed25519	  Clave privada: debes protegerla y no compartirla.
- ~/.ssh/id_ed25519.pub	  Clave pública: puedes instalarla en los servidores autorizados.

La clave privada se puede proteger con passphrase, esto le añade protección si es que el archivo es violado


Que es SCP o Secure copy, es una herramienta para copiar archivos entre equipos a través de SSH
Ejemplo, crear un informe y copiarlo al servidor de Linux sin  utilizar un USB

Estructura: scp archivo.txt usuario@IP_DEL_SERVIDOR:/ruta/destino/

Esta estructura se utiliza para copiar desde un Ubuntu a otro

Pero también existe para copiar directamente en la maquina local
scp usuario@IP_DEL_SERVIDOR:/ruta/remota/archivo.txt .
El punto final indica la ruta actual del servidor


Diferencia fundamental
- SSH: permite acceder a una terminal remota
- acp: permite transferir archivos
- ssh-keygen: permite crear un par de claves SSH
- ssh-copy-id: facilita instalar tu clave publica con un servidor complatible

Laboratorio

1.- Se comprueba SSH
	ssh -V
	Comprueba si tienes instalado programa de conexiones SSH
2.- Comprobar Status de SSH
	systemctl status ssh
	Determina si esta instalado y cual es el estado 
	
	En el caso de indicar que la unidad no existe , verificar si el servidor esta 	instalado
	- dphg -l openssh-server

	Si con el comando anterior indica que no existe servidor, se puede instalar con los 	siguientes comandos:
	- sudo apt update
	- sudo apt install openssh-server

	Después comprobar estado
	- sudo systemctl status ssh

	Si se encuentra instalado pero detenido, se puede iniciar con:
	- sudo systemctl start ssh
3.- Identificar ip
	ip -br addr
	permite identificar la IP a la cual se puede conectar
4.- Comprobar puertos escuchando
	sudo ss -tlnp
	Buscar si existe un servicio escuchando en el puerto 22
5.- Conectarse a la VM
	ssh vboxuser@127.0.0.1
	al ser la primera conexión, se solicita confirmar la identidad del servidor, además 	se utiliza la contraseña del servidor o la de ese usuario
6.- Al conectarse ejecutar
	- whoami ----> te entrega el usuario conectado
	- hostname ----> te entrega el nombre de la maquina o IP donde te conectaste

	- whoami: vboxuser
	- hostname: 127.0.0.1 o Ubuntu-Devops
7- Luego Salir de la sesión
	Exit
8.- Crear una clave SSH
	Luego de validar conexión, se genera un par de claves para el usuario
	ssh-keygen -t ed25519
9.- comprobar los archivos creados
	ls -l ~/.ssh/
	Con este comando se pueden observar los archivos con la clave publica y privada 	generada
10.- Para autorizar la clave publica en nuestra cuenta local:
	ssh-copy-id vboxuser@127.0.0.1
11.- después validamos conectarnos nuevamente
	ssh vboxuser@127.0.0.1
	Si la autenticación se realiza utilizado la clave, si tu clave esta protegida con 	una frase de contraeña, puede que SSH te la solicite
12.- Transferencia de archivos con SCP
	echo "Practica SSH Semana 5" > prueba-ssh.txt
13.- Se copia en el directorio personal de la cuenta remota
	scp prueba-ssh.txt vboxuser@127.0.0.1:~/prueba-ssh.txt
14.- Luego se comprueba si el archivo existe 
	ssh vboxuser@127.0.0.1 'cat ~/prueba-ssh-txt'
	Se valida que la información en archivo es la que colocamos al momento de crear

