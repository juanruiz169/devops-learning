Estudio Semana 6 dia 3
Contenido: Resolver nombres, registros A/AAAA/CNAME/MX.

El DNS traduce nombres a IP, por ejemplo de example.com a 172.0.0.25
Es una base de datos distribuida y jerárquica: raíz (.) → TLD (.com) → servidor autoritativo del dominio.

Que se corresponde a distribuida y jerarquica
Distribuida, indica que , no se encuentra la información del servidor no se encuentra almacenada en un solo servidor, se encuentra distribuida en miles servidores DNS
Jerarquico: los servidores se encuentran organizados en diferentes niveles, con cada nivel ayuda a encontrar el siguiente

	Raiz o root: donde se puede encontrar los servidores TLD,
		- es el nivel superior del DNS, el cual orienta la consulta a los servidores responsables de los TLD
		ejemplo: .com, .org., .NET .cl

	Servidor TLD: indica donde encontrar los servidores autoritativos del dominio
		-significa dominio de nivel superior o en ingles TOP-LEVEL DOMAIN, su función es indicar que servidores DNS son responsables de un dominio especifico

	Servidor Autoritativo: contiene los registros DNS del dominio
		- Este es el servidor que contiene la información del DNS oficial del dominio
		Por ejemplo puede tener registros como
		Registro	Función									Ejemplo
		A		Asocia un nombre con una IPv4.						web.ejemplo.com → 192.0.2.10
		AAAA		Asocia un nombre con una IPv6.						web.ejemplo.com → 2001:db8::10
		CNAME		Crea un alias que apunta a otro nombre de dominio.			tienda.ejemplo.com → web.ejemplo.com
		MX		Indica qué servidores reciben el correo del dominio.			ejemplo.com → mail.ejemplo.com
		NS		Indica cuáles son los servidores DNS autoritativos del dominio.		ns1.ejemplo.com
		TXT		Almacena información de texto asociada al dominio.			Verificación de servicios o políticas SPF.

Resolver Recursivo: corresponde al servidor DNS que se encarga de buscar por ti cuando necesitas conocer la IP de un Dominio
Este servidor realiza el trabajo:
	1. Revisa si ya conoce la respuesta y la tiene guardada en caché.
	2. Si no la tiene, consulta a los servidores DNS correspondientes.
	3. Obtiene la dirección IP.
	4. Te entrega la respuesta y la guarda temporalmente en caché.
Algunos ejemplos de resolvers públicos:
	- 8.8.8.8: Google DNS.
	- 1.1.1.1: Cloudflare DNS.	

TTL o time to live: determina cuanto tiempo puede permanecer una respuesta DNS guardada en el cache antes de que deba consultarse nuevamente, se mide en segundos 

Por ejemplo, supongamos que tienes este registro:

www.mitienda.cl → 192.0.2.10

Con un TTL de 3600 segundos:
- El resolver obtiene la dirección IP.
- Guarda esa respuesta durante 3600 segundos (1 hora).
- Durante ese tiempo puede responder usando la caché.
- Cuando vence el TTL, deberá consultar nuevamente para obtener una respuesta actualizada.

¿Por qué importa el TTL?

Imagina que cambias tu página web de servidor:
- Servidor antiguo: 192.0.2.10
- Servidor nuevo: 192.0.2.20
Si el registro tenía un TTL alto, algunos resolvers podrían seguir utilizando la dirección anterior hasta que expire su caché.

Por eso:
- TTL alto: menos consultas DNS, pero los cambios pueden tardar más en reflejarse.
- TTL bajo: los cambios pueden reflejarse antes, pero se realizan más consultas DNS.

Laboratorio
Tarea: Consultar registros de dominios públicos

1.- Consultar distintos registros 
	dig Google.com A +noall +answer
	dig Google.com AAAA +noall +answer
	dig Google.com MX +noall +answer
	dig Google.com NS +noall +answer
	dig Google.com TXT +noall +answer

2.- Buscar algún dominio que entregue CNAME para verificar como lo entrega
	dig www.github.com CNAME +noall +answer

