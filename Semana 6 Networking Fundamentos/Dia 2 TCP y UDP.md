Estudio Semana 6 dia 2
Contenido: TCP/UDP

- Puerto: SE utiliza para identificar un servicio dentro del equipo, puede recorrer del 0 al 65535, los mas conocidos son del 0 al 1023 (22,80,443)

Que son TCP/UPD
- Son protocolos de transporte, ambos pertenecen a la capa 4 del modelo OSI y permites que 2 aplicaciones se comuniquen a través de la red

TCP o Transmission Control protocol (comunicación confiable): garantiza que los datos lleguen correctamente a su destino, manteniendo el orden de los segmentos y gestionando las retransmisiones cuando sea necesario

Utiliza el procedimiento three way handshake para establecer conexión
1.- SYN: solicito establecer conexión
2.- SYN-ACK: Recibi tu solicitud y acepto
3.- ACK: confirmo tu respuesta

ESta opción es confiable en caso de perder información, ya que utiliza los números de secuencia y confirmaciones(ACK) para identificar los datos recibidos

Utilizada en HTTP,SSH, BD como MySQL y postreSQL y transferencia de datos SFTP

UDP o User Datagram Protocol (conexion sin conexion): No necesita establecer conexion mediante Three way handshake antes de enviar informacion
No garantiza por si mismo que los paquetes:
- Lleguen a destino
- Lleguen en orden
- Sean recibidos correctamente

Este protocolo de comunicación no necesita la confirmación para comunicarse, tiene conexión directa con el servidor, y si algún paquete de datos se pierde, no lo retransmite, asi permite reducir la sobrecarga y evita esperar confirmaciones de cada envio

Ejemplo de uso DNS, VoIP, streaming en tiempo real, juegos online, QUIC y HTTP/3

- una conexión se identifica como
	IP+PUerto origen ----> IP+Puertodestino, asi se atienden miles de servidores o clientes

Laboratorio
Tarea: Explicar 5 ejemplos de uso.

Comandos efectuados
1.- ss -tuln
	Permite identificar que existen 6 protocolos UDP y 7 protocolos TCP
	UDP: podemos identificar que tenemos los puertos 323, 5353:53
	TCP: SE logra idenficar 53,22,80, 631,22
	
