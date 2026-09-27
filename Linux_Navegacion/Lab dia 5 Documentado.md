1. Crear una estructura de directorios.
2. Crear varios archivos.
3. Introducir contenido.
4. Copiar y mover archivos.
5. Buscar archivos.
6. Buscar texto.
7. Contar líneas/palabras.
8. Ordenar información.
9. Comparar archivos.
10. Crear un archivo comprimido.
11. Consultar información mediante man.



Respuestas 
1.- Estructura de Escritorios
	/home/vboxuser/devops-lab/ejercicios/ruta1/ejercicios
	/home/vboxuser/devops-lab/ejercicios/ruta1/Documentos
	/home/vboxuser/devops-lab/ejercicios/Ruta2/Ejercicios
	/home/vboxuser/devops-lab/ejercicios/Ruta2/Documentos
2.- Creación de Archivos
	En la ruta 1 y 2 de los directorios Ejercicios y Documentos se crearon los archivos Prueba.txt y Archivo.txt

3.- Todos los archivos generados en el paso anterior se ha dejado con data

4.- En el directorio de ruta1/Docuemntos, se genero la copia de ambos archivos, y se movieron al directorio anterior, la copia de Prueba y Archivo original, ambos al directorio anterior, ósea a ruta1, donde aplicando el comando ls, se puede observar que ambos archivos se mantienen ahí

5.- con el comando find, dependiento de donde uno se encuentre actualmente puede realizar la consulta
find .: consulta desde el directorio donde uno se encuentra
find /: verifica todos los directorios donde te encuentras
find [ruta]: verifica una ruta en especifico

6.- Efectuando el comando grep al archivo PruebaCopia.txt, buscando la palabra pipeline, se encontraron 2 coincidencias
Comando efectuado: grep "pipeline" PruebaCopia.txt

7.- Utiizando el comando wc se logra obtener la cantidad de líneas y palabras en el texto PruebaCopia.txt
wc -l PruebaCopia.txt y wc -w PRuebaCopia.txt

8.- Aplicando el comando sort obtenemos por pantalla el archivo ordenado o dependiendo como lo apliquemos, puede ordena y guardar la data del mismo archivo

9.- Utilizando el comando Diff se pueden obtener las diferencias entre un archivo y otro, de ser necesario el archivo indicado a comparar se puede, eliminar, añadir data o modificar

10.-Utilizando el comando gzip en el archivo PRuebaCopia.txt, se genero el archivo con la extensión .gz

11.-En cada situación, si no se conoce alguna información bien o como poder utilizar un apéndice de algún comando, se utiliza el comando man [comando]el cual despliega toda la información de ese comando

 
