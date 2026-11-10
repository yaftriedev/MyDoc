# Capa Transporte: TCP vs UDP

## TCP (Transmission Control Protocol):

- **Orientado a conexión**: establece conexión antes de enviar datos (3-way handshake).
- **Fiable**: garantiza entrega, orden y sin duplicados.
- Control de flujo y congestión.
- **Más lento pero seguro.**
- **Uso**: web (HTTP/HTTPS), email, SSH, FTP.

### 3-way handshake (TCP)
```text
Cliente envía SYN.
Servidor responde SYN-ACK.
Cliente envía ACK.
Conexión establecida.
```

## UDP (User Datagram Protocol):

- **Sin conexión**: envía paquetes sin establecer conexión.
- **No fiable**: no garantiza entrega ni orden.
- **Más rápido pero puede perder datos.**
- **Uso**: streaming, VoIP, DNS, gaming, DHCP.

## Tabla Comparativa
| Aspecto | TCP | UDP |
|---|---|---|
| Conexión | Sí | No |
| Fiabilidad | Alta | Baja |
| Orden | Garantizado | No |
| Velocidad | Más lento | Más rápido |
| Cabecera | 20-60 bytes | 8 bytes |
| Uso | Web, email, SSH | Streaming, VoIP, DNS |

# Capa Aplicacion

## HTTP/HTTPS

### HTTP (HyperText Transfer Protocol)

- Protocolo de la web.
- Sin estado: cada petición es independiente.
- Métodos: GET, POST, PUT, DELETE, PATCH, HEAD, OPTIONS.
- Códigos de estado: 200 OK, 404 Not Found, 500 Internal Server Error.
- Puerto 80 o 8080.

### HTTPS (HyperText Transfer Protocol Secure)

- HTTP sobre TLS/SSL.
- Cifrado de extremo a extremo.
- Autenticación del servidor (certificados).
- Integridad de los datos.
- Estándar obligatorio en 2026.
- Puerto 443 o 8443.

### Versiones

- **HTTP/1.1**: clásico.
- **HTTP/2**: multiplexación, compresión.
- **HTTP/3**: sobre QUIC (UDP), más rápido.

### Cabeceras importantes

- **Host:** Indica el dominio del servidor al que se dirige la solicitud HTTP.
- **User-Agent:** Identifica el programa o dispositivo que realiza la solicitud.
- **Cookie:** Envía al servidor datos guardados previamente, como un identificador de sesión.
- **Authorization:** Incluye las credenciales o el método de autenticación de la solicitud.
- **Content-Type:** Especifica el formato del contenido enviado, por ejemplo, JSON.
- **Cache-Control:** Define cómo se puede almacenar en caché la respuesta y durante cuánto tiempo.

## DNS (Domain Name System):

> Traduce nombres de dominio a direcciones IP. Ejemplo: dns.google → 8.8.8.8

> Funciona sobre el Puerto 53

### Jerarquía

1. **Servidores raíz (root servers):** son el primer nivel de referencia. Hay **13 nombres lógicos**, identificados de la **A a la M** —por ejemplo, `a.root-servers.net`—, pero no son solo 13 máquinas físicas: cada nombre puede atenderse desde múltiples ubicaciones. Los servidores raíz no guardan la dirección de cada sitio web; indican qué servidores conocen el siguiente nivel, como `.com` o `.es`.
2. **Servidores TLD:** administran la información de cada dominio de nivel superior, o **TLD** (*top-level domain*), como `.com`, `.es` y `.org`. Cuando reciben una consulta, indican qué servidores son responsables del dominio consultado dentro de ese TLD.
3. **Servidores autoritativos:** contienen la información DNS oficial de un dominio, como sus direcciones IP y los servidores de correo. Por ejemplo, el servidor autoritativo de `ejemplo.com` puede devolver la dirección asociada a `www.ejemplo.com`. El propietario del dominio o su proveedor de DNS suele administrar esta zona.

### Registros DNS

- **A:** Asocia un nombre con una dirección IPv4. `www.example.com. IN A 192.0.2.1`
- **AAAA:** Asocia un nombre con una dirección IPv6. `www.example.com. IN AAAA 2001:db8::1`
- **CNAME:** Hace que un nombre sea alias de otro nombre. `blog.example.com. IN CNAME www.example.com.`
- **MX:** Indica el servidor de correo y su prioridad; un número menor tiene preferencia. `example.com. IN MX 10 mail.example.com.`
- **TXT:** Guarda texto usado para verificaciones y políticas, como SPF. `example.com. IN TXT "v=spf1 include:mail.example.net -all"`
- **NS:** Indica los servidores DNS responsables del dominio. `example.com. IN NS ns1.example.net.`
- **SOA:** Registra datos de autoridad y sincronización de la zona DNS. `example.com. IN SOA ns1.example.net. hostmaster.example.com. 2026061401 3600 900 604800 300`
- **SRV:** Especifica el servidor y puerto de un servicio. `_sip._tcp.example.com. IN SRV 10 5 5060 sip.example.com.`

> Caché: los resolvers y navegadores cachean resultados para acelerar.

### Servidores Conocidos

- **Google DNS**: `8.8.8.8`, `8.8.4.4`. El más fiable pero no es privado
- **Cloudflare**: `1.1.1.1`, `1.0.0.1`. El más rápido de los privados.
- **Quad9**: `9.9.9.9`. El más recomendable en privacidad y filtra malware.
- **OpenDNS**: `208.67.222.222`.

### DoH y DoT

> Aumenta tu Privacidad ya que ni tu ISP ni nadie interceptando tu red puede ver tus consultas DNS.

- **DoH (DNS over HTTPS, puerto 443)**: Cifrado y se mezcla con el tráfico web. Soportado por navegadores modernos.
- **DoT (DNS over TLS, puerto 853)**: Cifrado. Más fácil de bloquear que DoH.

## DHCP (Dynamic Host Configuration Protocol)

> Asigna direcciones IP automáticamente. El servidor usa el puerto 67 y el cliente el puerto 68. Para servidores o ordenadores que requieren una IP fija se puede fijar una IP estática.

### Proceso DORA

1. **Discover (cliente → servidores):** como aún no tiene una dirección IP, el cliente envía una solicitud de difusión (*broadcast*) para localizar servidores DHCP. Suele usar `0.0.0.0` como IP de origen y `255.255.255.255` como destino.
2. **Offer (servidor → cliente):** el servidor ofrece una *dirección disponible* y parámetros de red, como *máscara de subred, puerta de enlace, DNS y duración de la concesión (lease)*.
3. **Request (cliente → servidores):** el cliente anuncia qué oferta acepta. Si recibió varias, esta solicitud también informa a los otros servidores de que no fueron seleccionados.
4. **ACK (servidor → cliente):** el servidor confirma la asignación. El cliente configura la dirección y puede usarla durante el tiempo indicado en la concesión. Si no puede concederla, el servidor puede responder con **NAK**.

## Transferencia de Archivos: FTP, SFTP, SCP

- **FTP (File Transfer Protocol):** Transfiere archivos entre cliente y servidor, pero el FTP sin cifrado puede exponer credenciales y datos. Usa **TCP 21** para control; en modo activo suele usar TCP 20 para datos, mientras que en modo pasivo utiliza puertos de datos negociados.
- **SFTP (SSH File Transfer Protocol):** Permite transferir y administrar archivos mediante SSH; **no es FTP cifrado**, sino un protocolo distinto. Normalmente usa **TCP 22**.
- **SCP (Secure Copy):** Copia archivos entre equipos usando SSH. Ejemplo: `scp archivo.txt usuario@servidor:/ruta/`. En versiones actuales de OpenSSH, `scp` usa SFTP internamente de forma predeterminada.

### Alternativas Seguras

- **rsync sobre SSH:** Sincroniza archivos y directorios, transfiriendo eficientemente los cambios; es útil para copias de seguridad y actualizaciones repetidas. Ejemplo: `rsync -av carpeta/ usuario@servidor:/ruta/`.
- **Rclone:** Copia y sincroniza archivos entre el equipo local y servicios de almacenamiento en la nube; requiere configurar el destino remoto.
- **Nextcloud:** Plataforma de almacenamiento y sincronización de archivos que puede alojarse en un servidor propio o contratarse como servicio; permite compartir archivos y acceder a ellos desde distintos dispositivos.

### Correo: SMTP, IMAP, POP3

- **SMTP (Simple Mail Transfer Protocol):** Se usa para enviar correo: del cliente al servidor de envío (*submission*) y entre servidores de correo (*relay*).
  - **25/TCP:** principalmente para el intercambio entre servidores.
  - **587/TCP:** envío desde clientes o aplicaciones; normalmente se protege con **STARTTLS** y autenticación.
  - **465/TCP:** envío con **TLS implícito**, donde el cifrado comienza al establecer la conexión.

- **IMAP (Internet Message Access Protocol):** Permite consultar y administrar los mensajes que permanecen en el servidor; sincroniza acciones como leer, borrar o mover mensajes entre dispositivos.
  - **143/TCP:** conexión sin cifrado inicial; puede actualizarse a TLS mediante STARTTLS.
  - **993/TCP:** conexión cifrada desde el inicio.
  - Es la opción más práctica cuando se accede al correo desde varios dispositivos.

- **POP3 (Post Office Protocol 3):** Descarga mensajes del servidor al cliente; según la configuración, puede borrar los mensajes del servidor o dejar una copia. Sincroniza menos funciones y estados que IMAP.
  - **110/TCP:** conexión sin cifrado inicial; puede usar STARTTLS si el servidor lo admite.
  - **995/TCP:** conexión cifrada desde el inicio.
  - Sigue siendo útil en algunos casos, pero suele ser menos conveniente para usar una misma cuenta en varios dispositivos.

## SSH (Secure Shell):

> Permite acceso remoto cifrado a sistemas. Usa el puerto 22

> La autentificación puede ser por clave ssh (recomendado) o por contraseña (no recomendado por motivos de seguridad).

### Uso principal

- **Administración remota:** Permite conectarse a un servidor y ejecutar comandos desde una terminal. La conexión cifra los datos y ayuda a verificar la identidad del servidor.
- **Túneles cifrados:** Reenvían conexiones a través de un canal SSH protegido, por ejemplo, para acceder a un servicio remoto desde un puerto local.
- **Transferencia de archivos:** SFTP permite administrar archivos y directorios; SCP sirve principalmente para copiarlos entre equipos. Ambos usan SSH para proteger la conexión.
- **Git sobre SSH:** Permite clonar repositorios y enviar o descargar cambios autenticándose con claves SSH. La clave privada permanece en el equipo del usuario.

### Buenas prácticas

- Deshabilitar el inicio de sesión directo de root y usar una cuenta personal con permisos controlados.
- Preferir claves SSH y, cuando sea posible, deshabilitar la autenticación por contraseña.
- Mantener actualizado el servidor y limitar el acceso SSH a usuarios o redes autorizados.
- Usar un puerto no estándar es opcional: reduce parte del ruido de escaneos automatizados, pero no reemplaza la autenticación segura ni las reglas de firewall.
- Considerar herramientas como Fail2ban para bloquear temporalmente direcciones que acumulen intentos fallidos; no sustituye una configuración segura.

## ICMP (Internet Control Message Protocol):

> Se usa para mensajes de control y error. Por ejemplo en `ping` (echo request/reply), `traceroute` (TTL exceeded) o en mensajes de error (unreachable, time exceeded).

> No es TCP ni UDP. Es un protocolo de capa 3 (red).

> **Seguridad**: algunos firewalls bloquean ICMP por defecto.

## ARP (Address Resolution Protocol):

> Traduce direcciones IP a MAC dentro de una LAN.

### Funcionamiento

> IPv6 usa NDP (Neighbor Discovery Protocol) en lugar de ARP.

> Seguridad: ARP spoofing es un ataque común (MITM).

> Para ver cache de ARP se puede usar `arp -a` o `ip neigh`

1. Dispositivo A quiere hablar con 192.168.1.10.
2. Envía ARP request (broadcast): *¿Quién tiene 192.168.1.10?*.
3. Dispositivo B responde con su MAC.
4. A almacena la relación en su caché ARP.

## Otros protocolos importantes

- **NTP (Network Time Protocol):** Sincroniza la hora de computadoras y dispositivos de red con servidores horarios; una hora precisa ayuda a correlacionar registros y validar certificados. Usa normalmente **UDP 123**.
- **SNMP (Simple Network Management Protocol):** Permite supervisar y administrar dispositivos como routers, switches e impresoras; el gestor consulta al agente y puede recibir alertas (*traps*). Usa normalmente **UDP 161** para consultas y **UDP 162** para traps; se recomienda **SNMPv3**, que admite autenticación y cifrado.
- **LDAP (Lightweight Directory Access Protocol):** Consulta y administra directorios centralizados de usuarios, grupos y equipos, como Active Directory u OpenLDAP. Usa **TCP/UDP 389** según la operación y configuración; **LDAPS** suele usar **TCP 636** para LDAP sobre TLS.
- **Kerberos:** Protocolo de autenticación que usa tickets para que usuarios y servicios comprueben su identidad sin enviar la contraseña en cada acceso; es común en Active Directory. Usa normalmente **puerto 88 TCP y UDP**.
- **RDP (Remote Desktop Protocol):** Permite conectarse a un escritorio Windows remoto e interactuar con él. Usa normalmente **puerto 3389 TCP y UDP**; conviene limitar su acceso a redes autorizadas.
- **VNC (Virtual Network Computing):** Proporciona acceso remoto a la interfaz gráfica de distintos sistemas mediante el protocolo RFB. El puerto habitual es **TCP 5900** —y puede variar según la pantalla—; el cifrado depende de la implementación y configuración.
- **SMB (Server Message Block):** Permite compartir archivos, impresoras y otros recursos en redes, especialmente Windows; **CIFS** es un dialecto antiguo de SMB. En redes modernas suele usar **TCP 445**.
- **MQTT (Message Queuing Telemetry Transport):** Protocolo ligero para dispositivos IoT; los clientes publican mensajes y se suscriben a temas a través de un intermediario llamado *broker*. Usa comúnmente **TCP 1883 sin TLS** o **TCP 8883 con TLS**.
- **CoAP (Constrained Application Protocol):** Protocolo web ligero para dispositivos con pocos recursos; suele funcionar sobre **UDP** y utiliza un modelo de solicitud y respuesta, parecido a HTTP. Sus puertos habituales son **UDP 5683** para CoAP y **UDP 5684** para CoAPS con seguridad DTLS. 