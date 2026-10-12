Documentación Laboratorio Final Semana 4

En esta ocasión se revisara el servico fwupd, el cual se encarga de gestionar las actualizaciones del firmware de los componentes del equipo


1.- En primera instancia se revisara el estado del servicio
	systemctl status fwupd
	Consola muestra por pantalla que el servicio se encuentra:
	- Activo (corriendo
	- PID: 4767
	- Memoria utilizada: 28.6M  con un peak de 29.4M
	- CPU: 965ms

	Ademeas muestra un pequeño log cuando intenta agregar un dispositivo, pero en el proceso fallo

2.- Verificar si el servicio se encuentra activo
	systemctl is-active fwupd
	Respuesta del sistema: Active

3.- Verificar si el servicio se encuentra habilitado para inicio automatico
	systemctl is-enabled fwupd
	Respuesta del sistema: static, indica entonces que este programa, no se puede iniciar por medios de las formas habituales, normalmente lo inicia otra unidad o una dependencia

4.- Verificar si es que existe algún servicio asociado a este servicio
	- ps fwupd
		Muestra la información básica del servicio
	- pgrep fwupd
		Muestra el PID del servicio
	

Según lo que se puede observar con los comandos respectivos, encontramos que:
- No existe ningún proceso asociado al servicio
- el PID del servicio es el 4767
- el usuario ejecutor es root
- Actualmente se encuentra en estado running o active
- Según lo que se observo en la identificación del proceso, o en el paso 1, se observo que no existen diferencias en la entrega de información

5.- Examinar los registros

Se ejecuta en primera instancia journatctl -u fwupd -n 50 --no-pager, donde se puede encontrar que:
- 1.- Primera linea, arranque del servicio
- 2.- Segunda a cuarta linea, error al agregar dispositivos
- 3.- Linea 5, servicio quedo preparado
- 4.- Servicio completado

Con este primer comando, se puede observar este mismo patron varias veces indicando lo mismo, actualmente no se puede analizar a detalle cual es el componente que esta intentando agregar y cual seria el motivo por el cual esta fallando

La ultima vez que ocurrió fue hoy 11/10, además de los errores informados no se observan mas errores

En segunda instancia se ejecuta el comando journalctl -b -p err --no-pager, donde podemos observar los errores al momento del arranque del sistema, donde lo se observa errores al servicio que nos encontramos revisando 

Cabe mencionar que las ejecuciones de este servicio, permite verificar que fallo, a veces permite identificar de forma inmediata la causa, otras veces solo indica que fallo


Diagnostico final

Con las evidencias anteriores y según lo investigado del servicio fwupd, PI 4767, se encuentra que 
- El servicio se encuentra operativo sin ningún problema, solamente se a encontrado que en varias instancias, este mismo servicio a querido agregar un dispositivo sin éxito, lo cual, no a generado problemas sobre el SO o procesos siguientes.

Como se puede verificar esto, y poder solucionar, se debe verificar a mayor profundidad, cual es el dispositivo que esta intentando agregar el servicio, y ver cuales son los problemas de compatibilidad que no están permitiendo que se pueda agregar dicho dispositivo.
