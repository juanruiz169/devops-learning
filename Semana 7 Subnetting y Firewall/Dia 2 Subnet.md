Semana 7 Dia 2 Subnets
Contenido: Dividir una red en subredes.

¿Qué significa Subnetear?
- Subnetear significa dividir una red en varias subredes mas pequeñas

Ejemplo:
Imagina que tienes una red:

192.168.1.0/24

Esta red tiene:
- 256 direcciones totales.
- 254 hosts utilizables.

Ahora imagina que necesitas separar tus dispositivos en dos redes:
- Red 1: computadores.
- Red 2: servidores.
En lugar de utilizar toda la red /24, puedes dividirla en dos redes /25.

División de una red /24 en dos /25
Red original
192.168.1.0/24

254 hosts utilizables

Dividimos en dos partes iguales

Subred 1 		Subred 2
192.168.1.0/25		192.168.1.128/25
126			126
Hosts utilizables	Hosts utilizables

Observa lo que sucedió:
- Antes teníamos una red /24.
- Ahora tenemos dos redes /25.
- Cada red tiene 126 hosts utilizables.

Eso es subnetear.

2. ¿Por qué cada bit que tomamos duplica las subredes?
Este es el concepto más importante del día.

Recuerda que /24 significa:
- 24 bits para Network.
- 8 bits para Host.

Cuando tomamos un bit de los hosts y lo convertimos en parte de la red, pasamos de /24 a /25.

Cada vez que aumentamos un bit en el prefijo, reducimos a la mitad la cantidad de direcciones por subred.

Mira esta progresión:
Prefijo		Cantidad de subredes	Direcciones por subred	Hosts utilizables
/24			1			256			254
/25			2			128			126
/26			4			64			62
/27			8			32			30
/28			16			16			14

Visualización de cómo se divide una red /24

Cada división representa una subred dentro de 192.168.1.0/24.

/25 — 2 subredes
.0–127   --------------  .128–255


/26 — 4 subredes
.0–63 ---------- .64–127 ---------- .128–191 ---------- .192–255


/27 — 8 subredes
.0–31 ---------- .32–63 ---------- .64–95 ---------- .96–127 ---------- .128–159 ---------- .160–191 ---------- .192–223 ---------- .224–255

Qué debes recordar: cada vez que pasas de /24 a /25, /26 o /27, aumentas la cantidad de subredes y reduces la capacidad de hosts de cada una.

3. Tamaño de bloque
Este concepto ya lo viste en el día anterior, pero ahora lo utilizaremos para construir todas las subredes.

La fórmula es:
	Bloque=256-valor del octeto de la máscara

Veamos algunos ejemplos:
Prefijo		Máscara	Operación		Bloque
/25		255.255.255.128	256 − 128	128
/26		255.255.255.192	256 − 192	64
/27		255.255.255.224	256 − 224	32
/28		255.255.255.240	256 − 240	16

Por ejemplo, para /26:

192.168.1.0/26

El bloque es 64, por lo tanto, las subredes comienzan en:
- 192.168.1.0
- 192.168.1.64
- 192.168.1.128
- 192.168.1.192

Cada subred tiene 64 direcciones totales y 62 hosts utilizables.

4. ¿Cómo elegir el prefijo según los hosts que necesito?

Aquí entramos en la parte práctica.
Imagina que tienes que crear una red para 50 computadores.

¿Qué prefijo necesitas?

Debemos buscar un prefijo que permita al menos 50 hosts utilizables.
Prefijo		Hosts utilizables	¿Sirve para 50?
/27			30			No
/26			62			Sí
/25			126			Sí
/24			254			Sí

La opción más pequeña que cumple el requisito es /26.

¿Por qué no /25? 
Porque estarías reservando más direcciones de las necesarias.

Regla: elige el prefijo más grande que permita cubrir la cantidad de hosts que necesitas, ya que así utilizas una subred más pequeña.

5. Método de resolución

Para resolver los ejercicios de subnetting, sigue este orden:
	1. Determina cuántas subredes necesitas.
	2. Determina cuántos hosts necesita cada subred.
	3. Elige el prefijo que cumpla ambos requisitos.
	4. Calcula la máscara y el tamaño del bloque.
	5. Lista las direcciones de red.
	6. Calcula el rango de hosts y el broadcast de cada subred.

Una precisión importante: si necesitas dividir una red en una cantidad exacta de subredes iguales, debes reservar suficientes bits para obtener al menos esa cantidad. Por ejemplo, para 5 subredes necesitas 3 bits, porque \(2^3=8\).

Laboratorio
1.	Resuelve estos 5 casos mostrando el procedimiento:
	1) Divide 192.168.10.0/24 en 4 subredes iguales. Lista red, rango y broadcast de cada una.
		División de 4 subnet quedaría en /26
		
		Lista de Red		Rango		Broadcast
		192.168.10.0		.0-.62		 .63
		192.168.10.64		.65-.126	 .127
		192.168.10.128		.129-190	 .191
		192.168.10.192		.193-.254	 .255
	2) Divide 10.0.0.0/24 en 2 subredes iguales.
		10.0.0.0/25 ----- 10.0.0.127/25
	3) Necesitas subredes de al menos 50 hosts dentro de 192.168.20.0/24: ¿qué prefijo usas y cuántas subredes obtienes?
		Necesitas de por lo menos un prefijo /26 y obtienes 62 subredes por subnet
	
