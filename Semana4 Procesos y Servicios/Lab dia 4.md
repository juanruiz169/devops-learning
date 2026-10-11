Documentación Lab 5

Logs: es un registro de eventos del SO, servicio o aplicación 

Que tipo de información se puede encontrar:
- inicio o detención de un servicio
- errores de ejecución de un programa
- intentos de autenticación
- eventos relacionados al sistema
- problemas que pueden ayudar a dignosticar un fallo

Comandos:

- journalctl: consulta los registros admin por systemd
- journalctl -u servicio: filtra los registros de un servicio especifico
- journalctl -p err: filtra mensajes de prioridad de error
- tail: muestra las ultimas líneas de un archivo


Laboratorio:

1.- journalctl -n 20 --no-pager
Consulta los registros del sistema, este comando permite ver los últimos 20 registros sin abrir un visor interactivo

2.- journalctl -u cron -n 20 --no-pager
Consulta los registros de un servicio, este comando muestra los últimos 20 registros relacionados con crom, si el servicio esta disponible y existen registros

3.- journalctl -b -p err --no-pager
Buscar errores del arranque actual

Desglozando la consulta:
- -b: limita el arranque actual
- -p err: filtra los mensajes de prioridad de error
- --no-pager: muestra el resultado directamente en el terminal

 
