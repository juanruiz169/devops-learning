Se han creado el directorio PruebaPer y el archivo Permisos.txt

Existen 2 forma de poder aplicar el comando chmod donde se realizo una manera con el directorio y otra con el archivo

1.- Directorio
  en el directorio al momento de crearlo mantenia la siguiente configuracion
  drwxr-xr-x PruebaPer (Se omite lo que viene al medio, ya que no va al caso)
  SE puede encontrar 4 tipos 
    a (all) , u (user), g(group), o(others)
    2 formas 
    + (agregar permiso), - (quitar permiso)
    3 permisos
    r (read), w(write), x(execute)
  La forma de aplicar este comando se encuentra de la siguiente manera
  Si al usuario deseo quitarle el permiso de escribir y ejecutar aplico el siguiente comando
    chmod u-wx PruebaPer/   Este comando indica que deseo quitarle los permisos de escritura y ejecucion al usuario principal
    chmod go+w PruebaPer/    Este comando indica que deseo agregarle el permiso de escritura a grupo y otros
    chmod go-x PruebaPer/   Esta ejecucion indica que deseo quitarle el permiso de ejecutar a grupo y otros
Luego de ejcutar estos comandos, los permisos del directorio se podrias observar de la siguiente manera
    dr--rw-rw   PruebaPer

2.- Archivo
  El archivo al ser creado mantiene la siguiente configuracion
  -rwxr-xr-x Permisos.txt
  Los permisos se pueden encontrar en varias combinaciones
  Primero se observan los valores
    r - Lectura - 4
    w - Escritura - 2
    x - Ejecucion - 1

  0 - Sin permisos
  1 - Solo ejecutar
  2 - Solo Escritura
  3 - Escritura y ejecucion
  4 - Lectura
  5 - lectura y ejecucion
  6 - Lectura y escritura
  7 - Todos los permisos

Para poder modificar los permisos se puede aplicar de la siguiente manera
  chmod 623 Archivo.txt
  Este comando indica que
    6 al usuario se le dan los permisos de lectura y escritura
    2 al grupo solo permisos de escritura
    3 a otros se le dan los permisos de escritura y ejecucion
  con finalidad se estaria quedando de esta manera el ls -l
  -rw--w--wx  Archivo.txt
Se pueden realizar muchas mas combinaciones segun lo que se necesite


Explicar 644 y 755.

el chmod 644 archivo.txt indica que:
  6: al usuario se le dan los permisos de lectura y escritura
  4: al grupo se le da el permiso de lectura
  4: a otros se le da el permiso de lectura
aplicando ls -l se podria observar de la siguiente manera
-rw-r--r-- Archivo.txt

el chmod 755 archivo.txt
  7: al usuario se le dan todos los permisos
  5: al grupo se le da el permiso de lectura y ejecucion
  5: a otros se le da el permiso de lectura y ejecucion
aplicando ls -l se podria observar de la siguiente manera
-rwxr-xr-x Archivo.txt
