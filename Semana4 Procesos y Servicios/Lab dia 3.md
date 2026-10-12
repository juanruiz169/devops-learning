Documentación de Laboratorio 4

Contenido: service, start, stop , enable

systemd: administra los servicios y otros componentes de Linux, los cuales, los podemos encontrar en diferentes tipos de estados
	- Activo
	. detenido
	- Fallido
	. Configurado para iniciarse

Para interactuar con estos servicios tenemos el systemctl, que es la herramienta de linea de comandos para administrar systemd 

OJO: systemd no es lo mismo que systemctl

systemd: administra los servicios
systemctl: comando que se utiliza para consultar y controlar estos servicios
status: otro comando que permite la administración de servicios en Ubuntu

la forma de utilizar systemctl para controlar un servicio puede ser de 5 maneras

- systemctl status: consulta el estado de un servicio
- systemctl start: inicia un servicio
- systemctl stop: detiene un servicio
- systemctl enable: configura el inicio automatico del servicio durante el arranque
- systemctl disabled: desactiva el inicio automatico


LABORATORIO

Ejecutar comando e identificar proceso
- systemctl list-units --type=service --all
ESte comando permite listar las unidades tipo service que esten cargadas en systemd, incuyendo algunas que esten inactivas

--servicio a utilizar cron.service 

1.- Systemctl status cron (este servicio es utilizado para ejecutar tareas programadas)

2.- systemctl status systemd-journald (Servicio se ocupa de recopilar y administrar registros del sistema)

3.- systemctl is-enabled cron (comando informa si el servicio esta configurado para iniciarse automáticamente)

Prueba de parada y detenida de servicios

1.- systemctl stop cron (detiene el servicio)
2.- systemctl status cron (consultamos y validamos que servico se encuentra detenido)
3.- systemctl start cron (Iniciamos el servicio nuevamente)
4.- systemctl status cron (Permite validar nuevamente que el servicio que anteriomente estaba detenido, ahora esta corriendo)

En esta instancia solamente se realizara la prueba con el servicio cron, ya que se puede observar a través del dicho servicio la utilidad de los comandos start, stop y status

Ademas de la forma anterior del comando enable el cual permite verificar si un servicio se encuentra configurado para inicio automatico

Ademas de la forma anterior del comando enable el cual permite verificar si un servicio se encuentra configurado para inicio automatico

