Semana 7 Dia 3 Routing
Contenido: Default gateway y rutas.

1. ¿Qué es Routing (enrutamiento)?
El Routing o enrutamiento es el proceso mediante el cual un equipo decide por dónde debe enviar un paquete de red para llegar a una dirección IP de destino.

Para tomar esa decisión, Linux consulta una tabla de rutas, que contiene información sobre las redes a las que puede llegar y qué camino debe utilizar.

Por ejemplo, imagina que tu equipo tiene esta configuración:
- IP: 192.168.1.20
- Máscara: /24
- Gateway: 192.168.1.1

Tu equipo necesita comunicarse con otros dos destinos:
Destino			¿Qué sucede?
192.168.1.50		Está en la misma red, por lo que se comunica directamente.
8.8.8.8			Está fuera de su red, por lo que utiliza el gateway.

2. ¿Qué sucede cuando el destino está en la misma red?
Supongamos que tu Ubuntu tiene la IP 192.168.1.20/24 y quiere comunicarse con 192.168.1.50.

Ambos pertenecen a la red 192.168.1.0/24.

Por lo tanto, Linux sabe que puede enviar el paquete directamente al equipo de destino.

Pero necesita conocer su dirección MAC para poder entregarlo dentro de la red local.

Para eso utiliza ARP (Address Resolution Protocol), que permite descubrir la dirección MAC asociada a una dirección IPv4.

3. ¿Qué sucede cuando el destino está en otra red?
Ahora supongamos que quieres comunicarte con 8.8.8.8.

Tu equipo tiene la IP 192.168.1.20/24, por lo que sabe que 8.8.8.8 no pertenece a su red local.

En ese caso, envía el paquete a su Default Gateway, que normalmente es el router de la red.

El router recibe el paquete y busca cómo llegar al destino, reenviándolo al siguiente salto correspondiente.

Una diferencia importante: el paquete IP mantiene como destino 8.8.8.8, pero la trama Ethernet se entrega inicialmente a la MAC del gateway.

4. ¿Qué significa que gana la ruta más específica?
Este concepto se conoce como Longest Prefix Match (coincidencia de prefijo más largo).

Significa que cuando existen varias rutas que podrían utilizarse para llegar a un destino, Linux selecciona la ruta que tenga el prefijo más largo y específico.

Por ejemplo, imagina que tu tabla de rutas contiene:
Ruta	Significado
0.0.0.0/0	Cualquier destino.
192.168.0.0/16	Direcciones dentro de 192.168.x.x.
192.168.10.0/24	Direcciones dentro de 192.168.10.x.

Si quieres llegar a 192.168.10.50, las tres rutas coinciden.

Sin embargo, Linux elige:

192.168.10.0/24

¿Por qué?

Porque /24 es más específico que /16, y /16 es más específico que /0.

Orden de prioridad por especificidad:

/24 → /16 → /0

La ruta /0 se conoce como ruta por defecto y se utiliza cuando no existe una ruta más específica que coincida.

5. ¿Qué significa cada campo de ip route?
Cuando ejecutas:
- ip route

Linux muestra su tabla de rutas.

Un ejemplo simplificado sería:
	default via 192.168.1.1 dev enp0s3
	192.168.1.0/24 dev enp0s3 proto kernel scope link src 192.168.1.20

Veamos qué significa cada campo:
Campo			Significado
default			Ruta utilizada cuando no existe una ruta más específica.
192.168.1.0/24		Red de destino.
via			Dirección IP del siguiente salto (gateway).
dev			Interfaz de red por la que sale el paquete.
src			Dirección IP de origen preferida.
proto			Indica cómo se creó o qué protocolo instaló la ruta.
scope			Indica el alcance de la ruta.

Dos valores que encontrarás frecuentemente:
- proto kernel: ruta creada automáticamente por el kernel al configurar una dirección IP.
- scope link: destino directamente conectado a la interfaz, sin necesitar un gateway.



Laboratorio
Tarea del plan: Interpretar ip route.

1. Lee tu tabla de rutas:
	- ip route
	- ip route show default

2. Anota cada línea y explícala en una frase: destino, via, dev, src.
	destino: 10.0.2.15
	via 10.0.2.2
	dev enp0s3
	src 10.0.2.15

3. Pregúntale al kernel qué ruta usaría (cambia la IP de LAN por una de tu red):
	ip route get 8.8.8.8
	ip route get 10.0.2.15
	ip route get 127.0.0.1

4.	Mira los saltos hasta un destino. ¿Cuántos saltos hay? ¿Cuál es el primero y por qué?
	tracepath -n example.com
	Observando existen 2 saltos
	El primero es el 10.0.2.2 que tomo 1.025ms

5.	Responde sin ejecutar: si tu equipo es 192.168.1.20/24 y quieres llegar a 192.168.2.5, ¿a quién envía el paquete y por qué?
	la conectividad entre el inicio y la entrega es de forma local, por lo que es conectividad directa


	

