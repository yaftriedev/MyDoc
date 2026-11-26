# Conceptos Básicos
- **IP:** significa *Protocolo de Internet*. Es el sistema de reglas que permite identificar dispositivos y dirigir datos entre ellos a través de una red; una **dirección IP** es el número asignado a un dispositivo para que esos datos puedan llegar a él.
- **IP pública:** dirección que identifica una conexión ante Internet. Puede ser asignada por el proveedor de Internet y compartida por varios dispositivos mediante el router.
- **IP privada:** dirección que se usa dentro de una red local, como una casa u oficina. No identifica directamente al dispositivo ante Internet; el router normalmente la traduce al salir a la red pública.
- **IP estática:** dirección que permanece fija durante un periodo prolongado. Puede configurarse manualmente o asignarse de forma fija por el proveedor o el administrador de la red.
- **IP dinámica:** dirección que se asigna automáticamente y puede cambiar con el tiempo. En una red doméstica suele asignarla el router.
- **Unicast:** tipo de comunicación en que los datos se envían desde un dispositivo a otro dispositivo concreto. Es el caso más común, como cuando visitas una página web.
- **Multicast:** tipo de comunicación en que los datos se envían a un grupo específico de dispositivos. Evita enviar una copia separada a cada dispositivo del grupo.
- **Broadcast:** tipo de comunicación en que los datos se envían a todos los dispositivos de una red local. Se utiliza en IPv4, pero no en IPv6.
- **Anycast:** tipo de comunicación en que los datos se envían a uno de varios dispositivos que comparten una dirección. La red los dirige normalmente al dispositivo disponible más cercano.
- **NAT:** función del router que cambia las direcciones IP al pasar datos entre la red local e Internet. Así, varios dispositivos con direcciones privadas pueden compartir una dirección pública.
- **CIDR:** significa *Classless Inter-Domain Routing* y es una forma de escribir qué parte de una dirección IP identifica la red y qué parte identifica los dispositivos. Se escribe con una barra y un número, como `192.168.1.0/24`; `/24` indica que los primeros 24 bits corresponden a la red.

# IPv4
Versión de IP cuyas direcciones tienen cuatro números separados por puntos. Es el formato tradicional y todavía se usa ampliamente. Tiene una capacidad total de 4 mil millones de direcciones (32 bits).

> *Ej:* `192.168.1.1`

## Direcciones Reservadas

- **Loopback o Localhost**: `127.0.0.0/8`.
- **Link Local (RFC 3927)**: `169.254.0.0/16`.
- **Rangos Privados (RFC 1918)**: `10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`.

## Tabla CDIR
| CIDR | Uso común | Hosts utilizables |
|---|---|---|
| /8 | Redes muy grandes | 16.777.214 | 
| /16 | Redes empresariales grandes | 65.534 | 
| /20 | Redes grandes o campus | 4.094 | 
| /24 | LAN de casa u oficina | 254 | 
| /26 | Departamento o segmento pequeño | 62 | 
| /30 | Enlace punto a punto | 2 | 

# IPv6
Versión de IP más nueva, con direcciones más largas que combinan números y letras. Se creó para ofrecer muchas más direcciones que IPv4. Tiene una capacidad total de 340 undecillones de direcciones (128 bits).

> *Ej:* `2001:0db8:85a3:0000:0000:8a2e:0370:7334`. Abreviado: `2001:db8:85a3::8a2e:370:7334`

## Direcciones Reservadas

- **Loopback o Localhost**: `::1/128`.
- **Link Local**: `fe80::/10`.
- **Unicast Global**: `2000::/3`.

# Modelo OSI

El modelo **OSI** (Interconexión de Sistemas Abiertos) tiene siete capas. Cada una cumple una función específica y se apoya en la capa inferior.

| Capa | Nombre | Función principal | Ejemplos |
|---|---|---|---|
| 7 | Aplicación | Ofrece servicios de red a los programas del usuario. | HTTP, DNS, SMTP |
| 6 | Presentación | Da formato a los datos y puede comprimirlos o cifrarlos. | UTF-8, JPEG, TLS |
| 5 | Sesión | Inicia, mantiene y finaliza sesiones entre aplicaciones. | Control de sesiones |
| 4 | Transporte | Gestiona la comunicación entre dispositivos y la entrega de datos. | TCP, UDP |
| 3 | Red | Determina rutas y permite direccionar paquetes entre redes. | IP, routers |
| 2 | Enlace de datos | Transmite tramas entre dispositivos conectados al mismo enlace. | Ethernet, Wi‑Fi, switches |
| 1 | Física | Transporta bits mediante señales eléctricas, ópticas o de radio. | Cables, fibra, ondas de radio |

# Modelo TCP/IP

El modelo **TCP/IP** se basa en los protocolos utilizados en Internet. Generalmente se presenta con cuatro capas:

| Capa | Función principal | Modelo OSI | Ejemplos |
|---|---|---|---|
| Aplicación | Proporciona servicios de red a las aplicaciones. | 5, 6 y 7 | HTTP, DNS, SMTP, SSH |
| Transporte | Controla la comunicación entre procesos y la entrega de datos. | 4 | TCP, UDP |
| Internet | Direcciona y enruta paquetes entre redes. | 3 | IP, ICMP |
| Acceso a la red | Gestiona el envío de datos por el medio físico y el enlace local. | 1 y 2 | Ethernet, Wi‑Fi |