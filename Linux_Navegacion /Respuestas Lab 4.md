RESPUESTAS ESPERADAS
====================
NO MIRES ESTA SECCION HASTA HABER INTENTADO LOS 10 EJERCICIOS.


EJERCICIO 1
-----------
    pwd


EJERCICIO 2
-----------
    ls
    ls -a


EJERCICIO 3
-----------
    cd devops-lab
    pwd

Resultado parecido a:

    /home/NOMBRE_DE_USUARIO/devops-lab


EJERCICIO 4
-----------
    cd semana2
    pwd

Resultado:

    /home/NOMBRE_DE_USUARIO/devops-lab/semana2


EJERCICIO 5
-----------
Desde semana2:

    cd dia4
    pwd

Resultado:

    /home/NOMBRE_DE_USUARIO/devops-lab/semana2/dia4


EJERCICIO 6
-----------
    cd ..
    pwd

Resultado:

    /home/NOMBRE_DE_USUARIO/devops-lab/semana2


EJERCICIO 7
-----------
Desde semana2:

    cd ../documentos
    pwd

Resultado:

    /home/NOMBRE_DE_USUARIO/devops-lab/documentos

Explicacion:
.. significa subir un nivel y documentos significa entrar en ese directorio.
Por eso cd ../documentos primero sube de semana2 a devops-lab y despues entra
en documentos.


EJERCICIO 8
-----------
    cd ~
    pwd

Resultado:

    /home/NOMBRE_DE_USUARIO


EJERCICIO 9
-----------
Debes utilizar la ruta absoluta real de tu usuario.

Por ejemplo, si pwd muestra:

    /home/juan

puedes utilizar:

    cd /home/juan/devops-lab/semana2/dia4
    pwd

Resultado:

    /home/juan/devops-lab/semana2/dia4

No utilices ese nombre si tu usuario es diferente.


EJERCICIO 10
------------
Una solucion posible:

    cd ~/devops-lab
    cd semana2
    cd dia4
    pwd
    cd ..
    cd ejercicios
    pwd
    cd ~
    pwd

Resultados importantes:

    /home/NOMBRE_DE_USUARIO/devops-lab/semana2/dia4
    /home/NOMBRE_DE_USUARIO/devops-lab/semana2/ejercicios
    /home/NOMBRE_DE_USUARIO


QUE DEBERIAS PODER EXPLICAR AL TERMINAR
=======================================
- Que hace pwd.
- Que hace ls.
- Diferencia entre ls y ls -a.
- Que hace cd.
- Que significa ~.
- Que significa ..
- Que diferencia existe entre ruta absoluta y ruta relativa.
- Por que cd ../documentos funciona desde semana2.
- Por que /home/usuario/... es una ruta absoluta.
- Diferencia entre / y /home.
- Por que cd / no significa que estes usando el usuario root.
