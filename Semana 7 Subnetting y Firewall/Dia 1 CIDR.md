Semana 7 Dia 1 CIDR
Contenido: /24, /16, network/host.

1. ¿Qué significa que una IPv4 tenga 32 bits?
Una dirección IPv4 está formada por 4 números separados por puntos.

Por ejemplo:

192.168.1.10

Cada número representa 8 bits, por lo tanto:
- Primer bloque: 8 bits.
- Segundo bloque: 8 bits.
- Tercer bloque: 8 bits.
- Cuarto bloque: 8 bits.
En total:
8+8+8+8=32 bits

2. ¿Qué significa /24 o /16?
Aquí está uno de los conceptos más importantes.

El /N indica cuántos bits pertenecen a la parte de Network (red).

Los bits restantes pertenecen a Host (dispositivos).

Por ejemplo:
Red /24
24 bits de red + 8 bits de host = 32 bits

Red /16
16 bits de red + 16 bits de host = 32 bits
¿Cuál es la diferencia?
- /24: deja 8 bits para identificar dispositivos.
- /16: deja 16 bits para identificar dispositivos.

Por lo tanto, una red /16 permite muchas más direcciones para dispositivos que una /24.

¿Qué significa la máscara 255.255.255.0?
Una máscara de red representa los bits de Network y Host.
Prefijo	Máscara
/8	255.0.0.0
/16	255.255.0.0
/24	255.255.255.0

En el caso de /24, los primeros tres bloques corresponden a la red y el último al host.

Por ejemplo:

192.168.1.10/24
- Network: 192.168.1
- Host: 10
Es decir, el dispositivo tiene la dirección 192.168.1.10 dentro de la red 192.168.1.0/24.

3. ¿Cuántas direcciones permite cada red?
Para calcular cuántas direcciones existen, utilizamos esta fórmula:

Direcciones totales=2^(32-N)

Recuerda que N es el prefijo de red.

Para calcular los hosts utilizables, normalmente restamos dos:
Hosts utilizables=2^(32-N)-2

¿Por qué restamos dos?

Porque reservamos:
- Una dirección para identificar la red.
- Una dirección para el broadcast.

Prefijo	Bits de host	Direcciones totales	Hosts utilizables
/24	8		256			254
/16	16		65.536			65.534
/30	2		4			2	

Por lo tanto, una red /24 tiene 256 direcciones totales y 254 direcciones utilizables para hosts.


4. Network, Broadcast y Hosts
Ahora vamos a utilizar una red concreta:
	
192.168.1.0/24

Esta red tiene 256 direcciones, desde 192.168.1.0 hasta 192.168.1.255.
Distribución de la red 192.168.1.0/24

Network
192.168.1.0: Identifica la red. No se asigna normalmente a un dispositivo.

Primer host
192.168.1.1: Primera dirección utilizable.

Último host
192.168.1.254: Última dirección utilizable.

Broadcast
192.168.1.255: Dirección utilizada para enviar tráfico a todos los hosts de esa red.

La regla general es:
- Network = todos los bits de host en 0.
- Broadcast = todos los bits de host en 1.
- Primer host = Network + 1.
- Último host = Broadcast − 1.

5. Rangos privados (RFC 1918)
Existen direcciones IPv4 reservadas para utilizarse dentro de redes privadas.

Los tres rangos principales son:
Rango privado				Prefijo
10.0.0.0 a 10.255.255.255		/8
172.16.0.0 a 172.31.255.255		/12
192.168.0.0 a 192.168.255.255		/16

¿Dónde los puedes encontrar?
- Redes domésticas.
- Máquinas virtuales Ubuntu.
- Redes internas de empresas.
- VPC de AWS y GCP.
- Redes de contenedores y Kubernetes.
¿Por qué son privadas?

Porque no se enrutan directamente a través de Internet público. Normalmente, para acceder a Internet, los dispositivos utilizan mecanismos como NAT.

Por ejemplo, tu máquina virtual Ubuntu podría tener esta IP:

192.168.1.20

Esa es una dirección privada que puede utilizar dentro de su red local.

Laboratorio
