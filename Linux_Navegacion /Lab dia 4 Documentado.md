SEMANA 2 - DIA 4
PRACTICA DE NAVEGACION EN LINUX
================================

OBJETIVO
--------
Practicar la navegacion basica por el sistema de archivos de Linux usando:
pwd, ls, ls -a, cd, ~, ., .., rutas absolutas y rutas relativas.

CONTROL DE FOCO
---------------
No estudiar todavia:
chmod, chown, grep, find, ps, systemctl, ssh, Bash scripting,
procesos ni redes.


USUARIO NORMAL Y ROOT
---------------------
Los ejercicios deben realizarse con tu usuario normal de Ubuntu.
NO es necesario trabajar como root.

Una ruta como /home/tu_usuario es solo un ejemplo. No escribas literalmente
"tu_usuario". Para conocer tu ruta real:

    pwd

Con un usuario normal normalmente veras algo parecido a:

    /home/nombre_usuario

Si estuvieras como root, normalmente verias:

    /root

Para esta practica queremos trabajar con el usuario normal.


ACLARACION: /, /home Y ~
-------------------------

1. / = directorio raiz del sistema de archivos.

Si ejecutas:

    cd /
    pwd

el resultado correcto es:

    /

Esto NO significa que estes utilizando el usuario root. Solo significa que
estas ubicado en el directorio raiz.

2. /home = directorio que esta dentro de /.

Si ejecutas:

    cd /
    cd home
    pwd

el resultado sera:

    /home

3. ~ = HOME del usuario actual.

Si tu usuario fuera juan:

    ~ = /home/juan

Por eso:

    cd ~
    pwd

te lleva directamente al HOME de tu usuario.

Resumen:

    /       = raiz del sistema
    /home   = directorio que contiene los HOME de los usuarios
    ~       = HOME del usuario actual

Si hiciste cd / y despues cd home y obtuviste /home, esta correcto.
Para volver al HOME de tu usuario utiliza:

    cd ~
    pwd


AJUSTES PREVIOS
---------------

PASO 1 - Ir al HOME del usuario actual

    cd ~
    pwd

Guarda mentalmente la ruta que aparece. Es tu HOME real.

PASO 2 - Crear la estructura de practica

Desde tu HOME:

    mkdir -p ~/devops-lab/semana2/dia4
    mkdir -p ~/devops-lab/semana2/ejercicios
    mkdir -p ~/devops-lab/documentos

La estructura sera:

    devops-lab/
    |-- semana2/
    |   |-- dia4/
    |   `-- ejercicios/
    `-- documentos/

PASO 3 - Verificar

    ls
    ls devops-lab
    ls devops-lab/semana2

Deberias poder identificar:
- devops-lab
- dentro de devops-lab: documentos y semana2
- dentro de semana2: dia4 y ejercicios

No necesitas crear archivos todavia.


LOS 10 EJERCICIOS
=================

IMPORTANTE:
Primero intenta resolverlos sin mirar las respuestas.
Las respuestas estan todas juntas al final.


EJERCICIO 1 - IDENTIFICAR DONDE ESTAS
-------------------------------------
Desde cualquier ubicacion:
¿Que comando utilizas para saber exactamente en que directorio estas?

R: SE utiliza el comando pwd


EJERCICIO 2 - VER EL CONTENIDO
------------------------------
Desde tu HOME:
1. Muestra el contenido del directorio actual.
2. Muestra tambien los archivos/directorios ocultos.

Restriccion: utiliza solamente ls y sus opciones.

Con el siguiente comando se puede observar los siguientes directorios y/o archivos:

ls: Desktop, Downloads Pictures, Templates, devops-lab, Documents, Music, Public, Videos, snapp

ls -al: además de los directorios .cache, .config, .local, .ssh, puedo observar los archivos, .bash_history, .bash_logout, .bashrc, .profile.


EJERCICIO 3 - ENTRAR EN devops-lab
-----------------------------------
Desde tu HOME, entra en devops-lab.
Despues comprueba donde estas.

R: la ruta donde me encuentro es /home/vboxuser/devops-lab

EJERCICIO 4 - ENTRAR EN semana2
-------------------------------
Desde devops-lab, entra en semana2.
Despues comprueba donde estas.

R: la ruta donde me encuentro es /home/vboxuser/devops-lab/semana2

EJERCICIO 5 - LLEGAR A dia4 CON RUTA RELATIVA
----------------------------------------------
Desde devops-lab/semana2, llega a:
devops-lab/semana2/dia4

Utiliza una ruta relativa.
Despues comprueba tu ubicacion.

R: Actualmente para llegar a dia4 se utilizo el comando cd dia4 donde al desplegar el comando pwd se obtuvo la ruta /home/vboxuser/devops-lab/semana2/dia4


EJERCICIO 6 - VOLVER UTILIZANDO ..
-----------------------------------
Desde devops-lab/semana2/dia4, utiliza .. para volver a:
devops-lab/semana2

Despues comprueba donde estas.

R: Efectuando el comando indicado, se vuelve a la ruta /home/vboxuser/devops-lab/semana2


EJERCICIO 7 - IR A documentos CON RUTA RELATIVA
-----------------------------------------------
Desde devops-lab/semana2, llega a:
devops-lab/documentos

NO utilices una ruta absoluta.
Piensa: ¿tengo que bajar a documentos o subir primero?

Despues comprueba tu ubicacion.

R: Según la lógica, la forma mas rápida de llegar al directorio documentos es:
1.- Ejecutar el comando cd .. donde me permite devolverme al directorio anterior
2.- Ejecutar el comando cd documentos, el cual me dejara en la ruta indicada
3.- Efectuar el comando pwd donde me entregara la ruta /home/vboxuser/devops-lab/documentos


EJERCICIO 8 - VOLVER AL HOME
-----------------------------
Desde la ubicacion anterior, vuelve directamente al HOME de tu usuario.
Puedes utilizar ~.
Despues comprueba tu ubicacion con pwd.

R: al efectuar el comando cd ~, me permite volver al home dando como resultado la ruta /home/vboxuser


EJERCICIO 9 - PRACTICAR RUTA ABSOLUTA
-------------------------------------
Desde tu HOME, entra directamente en:
devops-lab/semana2/dia4

Esta vez utiliza una RUTA ABSOLUTA.
No vayas entrando directorio por directorio.

Despues comprueba donde estas.

IMPORTANTE:
La ruta depende de tu nombre real de usuario.
No copies literalmente /home/tu_usuario/...
Primero utiliza pwd para conocer tu HOME real.

R: desde Home, se efectua el comando cd devops-lab/semana2/dia4, se puede llegar de forma directa al directorio indicado, y efectuando el comando pwd, se puede verificar que estamos en /home/vboxuser/devops-lab/semana2/dia4

EJERCICIO 10 - DESAFIO FINAL
----------------------------
Comienza desde:

    ~

Realiza:
1. Ve a devops-lab.
2. Entra en semana2.
3. Entra en dia4.
4. Comprueba tu ubicacion.
5. Vuelve a semana2 utilizando ..
6. Entra en ejercicios.
7. Comprueba tu ubicacion.
8. Regresa a HOME utilizando ~.
9. Comprueba nuevamente tu ubicacion.

Restriccion: intenta utilizar solamente:

    pwd
    ls
    cd
    ~
    ..
    .

No utilices find, grep, tree ni otros comandos de navegacion.

R: comando ejecutados y respuestas esperadas:
1.- cd devops-lab
2.- cd semana2
3.- cd dia4
4.- Efectuar pwd donde obtenemos la ruta /home/vboxuser/devops-lab/semana2/dia4
5.- cd ..
6.- cd ejercicios
7.- Efectuar pwd donde obtenemos la ruta/home/vboxuser/devops-lab/semana2/ejercicios
8.- cd ~
9.- Efectuar pwd donde obtenemos /home/vboxuser/
