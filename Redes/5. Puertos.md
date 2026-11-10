# Puertos y Servicios

| Puerto/protocolo | Nombre | Descripción |
| --- | --- | --- |
| 1/tcp | tcpmux | Multiplexor TCP |
| 5/tcp | rje | Entrada de trabajo remota |
| 7/tcp | echo | Protocolo [Echo](https://es.wikipedia.org/wiki/Echo_(inform%C3%A1tica)) (Eco) Responde con eco a llamadas remotas |
| 11/tcp | systat | Servicio del sistema para listar los puertos conectados |
| 13/tcp | daytime | Protocolo [Daytime](https://es.wikipedia.org/wiki/Daytime), envía la fecha y hora actuales |
| 17/tcp | qotd | [Quote of the Day](https://es.wikipedia.org/wiki/QOTD), envía la cita del día |
| 18/tcp | msp | Protocolo de envío de mensajes |
| 19/tcp | chargen | Protocolo [Chargen](https://es.wikipedia.org/wiki/Chargen) o **Generador de caracteres**, envía flujos infinitos de caracteres |
| 20/tcp | ftpS-data | [FTPS](https://es.wikipedia.org/wiki/File_Transfer_Protocol_Shield?action=edit&redlink=1) File Transfer Protocol (Protocolo de Transferencia de Ficheros) - datos |
| 21/tcp | ftp-control | [FTP](https://es.wikipedia.org/wiki/File_Transfer_Protocol) File Transfer Protocol (Protocolo de Transferencia de Ficheros) - control |
| 22/tcp | ssh | [SSH](https://es.wikipedia.org/wiki/SSH), [scp](https://es.wikipedia.org/wiki/Secure_Copy), [SFTP](https://es.wikipedia.org/wiki/SFTP) |
| 23/tcp | telnet | [Telnet](https://es.wikipedia.org/wiki/Telnet) manejo remoto de equipo, inseguro |
| 25/tcp | smtp | [SMTP](https://es.wikipedia.org/wiki/SMTP) Simple Mail Transfer Protocol (Protocolo Simple de Transferencia de Correo) |
| 37/tcp | time | [Time Protocol](https://es.wikipedia.org/wiki/Time_Protocol). Sincroniza hora y fecha |
| 39/tcp | rlp | Protocolo de ubicación de recursos |
| 42/tcp | nameserver | Servicio de nombres de Internet |
| 43/tcp | nickname | Servicio de directorio [WHOIS](https://es.wikipedia.org/wiki/WHOIS) |
| 49/tcp | tacacs | Terminal Access Controller Access Control System para el acceso y autenticación basado en TCP/IP |
| 50/tcp | re-mail-ck | Protocolo de verificación de correo remoto |
| 53/tcp and udp | domain | [DNS](https://es.wikipedia.org/wiki/DNS) Domain Name System (Sistema de Nombres de Dominio), por ejemplo [BIND](https://es.wikipedia.org/wiki/BIND) |
| 53/udp |  | [FaceTime](https://es.wikipedia.org/wiki/FaceTime) |
| 63/tcp | whois++ | Servicios extendidos de [WHOIS](https://es.wikipedia.org/wiki/WHOIS) (WHOIS++) |
| 66/tcp and udp | Oracle SQLNet | Software de red que permite acceso remoto entre los programas y la [base de datos Oracle](https://es.wikipedia.org/wiki/Oracle_Database). |
| 67/udp | bootps | [BOOTP](https://es.wikipedia.org/wiki/BOOTP) BootStrap Protocol (servidor), también usado por [DHCP](https://es.wikipedia.org/wiki/DHCP) |
| 68/udp | bootpc | [BOOTP](https://es.wikipedia.org/wiki/BOOTP) BootStrap Protocol (cliente), también usado por [DHCP](https://es.wikipedia.org/wiki/DHCP) |
| 69/udp | tftp | [TFTP](https://es.wikipedia.org/wiki/TFTP) Trivial File Transfer Protocol (Protocolo Trivial de Transferencia de Ficheros) |
| 70/tcp | gopher | [Gopher](https://es.wikipedia.org/wiki/Gopher) |
| 79/tcp | finger | [Finger](https://es.wikipedia.org/wiki/Finger_(protocolo)) |
| 80/tcp | http | [HTTP](https://es.wikipedia.org/wiki/HTTP) HyperText Transfer Protocol (Protocolo de Transferencia de HiperTexto) ([WWW](https://es.wikipedia.org/wiki/WWW)) |
| 88/tcp | kerberos | [Kerberos](https://es.wikipedia.org/wiki/Kerberos) Agente de autenticación |
| 95/tcp | supdup | Extensión del protocolo [Telnet](https://es.wikipedia.org/wiki/Telnet) |
| 101/tcp | hostname | Servicios de nombres de host en máquinas SRI-NIC |
| 107/tcp | rtelnet | Telnet remoto |
| 109/tcp | pop2 | [POP](https://es.wikipedia.org/wiki/Post_Office_Protocol)2 Post Office Protocol ([Correo electrónico](https://es.wikipedia.org/wiki/Correo_electr%C3%B3nico)) |
| 110/tcp | pop3 | [POP3](https://es.wikipedia.org/wiki/POP3) Post Office Protocol ([Correo electrónico](https://es.wikipedia.org/wiki/Correo_electr%C3%B3nico)) |
| 111/tcp | sunrpc | [sunrpc](https://es.wikipedia.org/wiki/Sunrpc) |
| 113/tcp | auth | [ident](https://es.wikipedia.org/wiki/Ident?action=edit&redlink=1) (auth) antiguo sistema de identificación |
| 115/tcp | sftp | [SFTP (Simple FTP)](https://en.wikipedia.org/wiki/File_Transfer_Protocol#Simple_File_Transfer_Protocol) Protocolo de transferencia de archivos simple |
| 117/tcp | uupc-path | Servicios de rutas de Unix-to-Unix Copy Protocol (UUCP) |
| 119/tcp | nntp | [NNTP](https://es.wikipedia.org/wiki/NNTP) usado en los grupos de noticias de [usenet](https://es.wikipedia.org/wiki/Usenet) |
| 123/udp | ntp | [NTP](https://es.wikipedia.org/wiki/NTP) Protocolo de sincronización de tiempo |
| 135/tcp | epmap | [epmap](https://es.wikipedia.org/wiki/Epmap?action=edit&redlink=1) |
| 137/udp | netbios-ns | [NetBIOS](https://es.wikipedia.org/wiki/NetBIOS) Servicio de nombres |
| 138/udp | netbios-dgm | [NetBIOS](https://es.wikipedia.org/wiki/NetBIOS) Servicio de envío de datagramas |
| 139/tcp | netbios-ssn | [NetBIOS](https://es.wikipedia.org/wiki/NetBIOS) Servicio de sesiones |
| 143/tcp | imap | [IMAP](https://es.wikipedia.org/wiki/IMAP)4 Internet Message Access Protocol ([Correo electrónico](https://es.wikipedia.org/wiki/Correo_electr%C3%B3nico)) |
| 161/udp | snmp | [SNMP](https://es.wikipedia.org/wiki/SNMP) Simple Network Management Protocol |
| 162/udp | snmptrap | [SNMP-trap](https://es.wikipedia.org/wiki/SNMP#Trap) |
| 174/tcp | mailq | Cola de transporte de correos electrónicon MAILQ |
| 177/tcp | xdmcp | [XDMCP](https://es.wikipedia.org/wiki/XDMCP) Protocolo de gestión de displays en [X11](https://es.wikipedia.org/wiki/X11) |
| 178/tcp | nextstep | Servidor de ventanas [NeXTStep](https://es.wikipedia.org/wiki/NeXTStep) |
| 179/tcp | bgp | [Border Gateway Protocol](https://es.wikipedia.org/wiki/Border_Gateway_Protocol) |
| 194/tcp | irc | [Internet Relay Chat](https://es.wikipedia.org/wiki/Internet_Relay_Chat) |
| 199/tcp | smux | SNMP UNIX Multiplexer |
| 201/tcp | at-rtmp | Enrutamiento [AppleTalk](https://es.wikipedia.org/wiki/AppleTalk) |
| 202/tcp | at-nbp | Enlace de nembres AppleTalk |
| 204/tcp | at-echo | Echo AppleTalk |
| 206/tcp | at-zis | Zona de información AppleTalk |
| 209/tcp | qmtp | Protocolo de transferencia rápida de correo (QMTP) |
| 210/tcp | z39.50 | Base de datos NISO Z39.50 |
| 213/tcp | ipx | El protocolo de intercambio de paquetes entre redes (IPX) |
| 220/tcp | imap3 | [IMAP](https://es.wikipedia.org/wiki/IMAP) versión 3 |
| 245/tcp | link | Servicio LINK / 3-DNS iQuery |
| 347/tcp | fatserv | Servicio de administración de cintas y archivos FATMEN |
| 363/tcp | rsvp_tunnel | Túnel RSVP |
| 369/tcp | rpc2portmap | Portmapper del sistema de archivos Coda |
| 370/tcp | codaauth2 | Servicios de autenticación del sistema de archivos Coda |
| 372/tcp | ulistproc | UNIX LISTSERV |
| 389/tcp | ldap | [LDAP](https://es.wikipedia.org/wiki/LDAP) Protocolo de acceso ligero a Directorios |
| 427/tcp | svrloc | Protocolo de ubicación de servicios (SLP) |
| 434/tcp | mobileip-agent | Agente móvil del Protocolo Internet |
| 435/tcp | mobilip-mn | Gestor móvil del Protocolo Internet |
| 443/tcp | https | [HTTPS](https://es.wikipedia.org/wiki/HTTPS)/[SSL](https://es.wikipedia.org/wiki/Transport_Layer_Security) usado para la transferencia segura de páginas web |
| 444/tcp | snpp | Protocolo simple de Network Pagging |
| 445/tcp | | microsoft-ds Microsoft-DS ([Active Directory](https://es.wikipedia.org/wiki/Active_Directory), compartición en [Windows](https://es.wikipedia.org/wiki/Windows), gusano [Sasser](https://es.wikipedia.org/wiki/Sasser?action=edit&redlink=1), Agobot) o también es usado por Microsoft-DS compartición de ficheros |
| 465/tcp | smtps | [SMTP](https://es.wikipedia.org/wiki/SMTP) Sobre [SSL](https://es.wikipedia.org/wiki/Transport_Layer_Security). Utilizado para el envío de correo electrónico ([Correo electrónico](https://es.wikipedia.org/wiki/Correo_electr%C3%B3nico)) |
| 500/udp |  | [IPSec](https://es.wikipedia.org/wiki/IPSec) ISAKMP, Autoridad de Seguridad Local |
| 512/tcp |  | [exec](https://es.wikipedia.org/wiki/Exec?action=edit&redlink=1) |
| 513/tcp |  | [Rlogin](https://es.wikipedia.org/wiki/Rlogin) |
| 514/udp |  | [syslog](https://es.wikipedia.org/wiki/Syslog) usado para logs del sistema |
| 515/tcp |  | usado para la impresión en windows |
| 520/udp | rip | [RIP](https://es.wikipedia.org/wiki/Routing_Information_Protocol) Routing Information Protocol (Protocolo de Información de Enrutamiento) |
| 521/udp | ripng | [RIP](https://es.wikipedia.org/wiki/Routing_Information_Protocol) Routing Information Protocol IPv6 (Protocolo de Información de Enrutamiento Internet v6)[[2]](https://es.wikipedia.org/wiki/Anexo:Puertos_de_red#cite_note-2) |
| 587/tcp | smtp | [SMTP](https://es.wikipedia.org/wiki/SMTP) Sobre [TLS](https://es.wikipedia.org/wiki/Transport_Layer_Security) |
| 591/tcp |  | [FileMaker](https://es.wikipedia.org/wiki/FileMaker) 6.0 *(alternativa para HTTP, ver puerto 80)* |
| 631/tcp |  | [CUPS](https://es.wikipedia.org/wiki/Common_Unix_Printing_System) sistema de impresión de Unix |
| 666/tcp |  | identificación de [Doom](https://es.wikipedia.org/wiki/Doom_(videojuego_de_1993)) para jugar sobre TCP |
| 993/tcp | imaps | [IMAP](https://es.wikipedia.org/wiki/IMAP)4 sobre [SSL](https://es.wikipedia.org/wiki/Transport_Layer_Security) ([Correo electrónico](https://es.wikipedia.org/wiki/Correo_electr%C3%B3nico)) |
| 995/tcp |  | POP3 sobre [SSL](https://es.wikipedia.org/wiki/Transport_Layer_Security) ([Correo electrónico](https://es.wikipedia.org/wiki/Correo_electr%C3%B3nico)) |

# Puertos Registrados o Asignados

| Puerto/protocolo | Descripción |
| --- | --- |
| 1001/tcp | [SOCKS](https://es.wikipedia.org/wiki/SOCKS) Proxy |
| 1194/udp | [OpenVPN](https://es.wikipedia.org/wiki/OpenVPN) Puerto por defecto en NAS Synology y QNAP |
| 1337/tcp | suele usarse en máquinas comprometidas o infectadas |
| 1352/tcp | IBM Lotus Notes/Domino RCP |
| 1433/tcp | [Microsoft-SQL-Server](https://es.wikipedia.org/wiki/Microsoft_SQL_Server) |
| 1434/tcp | Microsoft-SQL-Monitor |
| 1494/tcp | [Citrix MetaFrame](https://es.wikipedia.org/wiki/Citrix_MetaFrame?action=edit&redlink=1) Cliente IC |
| 1512/tcp | [WINS](https://es.wikipedia.org/wiki/Windows_Internet_Naming_Service) Windows Internet Naming Service |
| 1521/tcp | [Oracle](https://es.wikipedia.org/wiki/Oracle) puerto de escucha por defecto |
| 1701/udp | Enrutamiento y Acceso Remoto para VPN con L2TP. |
| 1720/udp | [H.323](https://es.wikipedia.org/wiki/H.323) |
| 1723/tcp | Enrutamiento y Acceso Remoto para VPN con PPTP. |
| 1761/tcp | [Novell](https://es.wikipedia.org/wiki/Novell) Zenworks Remote Control utility |
| 1812/udp y tcp | [RADIUS](https://es.wikipedia.org/wiki/RADIUS) authentication protocol, `radius` |
| 1813/udp y tcp | [RADIUS](https://es.wikipedia.org/wiki/RADIUS) accounting protocol, `radius-acct` |
| 1883 tcp | MQTT protocol |
| 1863/tcp | [MSN Messenger](https://es.wikipedia.org/wiki/MSN_Messenger) |
| 1935/tcp | [FMS](https://es.wikipedia.org/wiki/FMS) Flash Media Server |
| 2049/tcp | [NFS](https://es.wikipedia.org/wiki/Network_File_System) Archivos del sistema de red |
| 2082/tcp | [cPanel](https://es.wikipedia.org/wiki/CPanel) puerto por defecto |
| 2083/tcp | [CPanel](https://es.wikipedia.org/wiki/CPanel) puerto por defecto sobre SSL |
| 2086/tcp | [Web Host Manager](https://es.wikipedia.org/wiki/Web_Host_Manager?action=edit&redlink=1) puerto por defecto |
| 2427/udp | Cisco [MGCP](https://es.wikipedia.org/wiki/MGCP) |
| 3000/tcp | [React](https://es.wikipedia.org/wiki/React) |
| 3030/tcp and udp | [NetPanzer](https://es.wikipedia.org/wiki/NetPanzer?action=edit&redlink=1) |
| 3074/tcp | [Xbox Live](https://es.wikipedia.org/wiki/Xbox_Live) |
| 3074/udp | [Xbox Live](https://es.wikipedia.org/wiki/Xbox_Live) |
| 3128/tcp | [HTTP](https://es.wikipedia.org/wiki/HTTP) usado por [web caches](https://es.wikipedia.org/wiki/Web_cache?action=edit&redlink=1) y por defecto en [Squid cache](https://es.wikipedia.org/wiki/Squid_cache?action=edit&redlink=1) |
| 3128/tcp | [NDL-AAS](https://es.wikipedia.org/wiki/NDL-AAS?action=edit&redlink=1) |
| 3306/tcp | [MySQL](https://es.wikipedia.org/wiki/MySQL) sistema de gestión de bases de datos |
| 3389/tcp | RDP ([Remote Desktop Protocol](https://es.wikipedia.org/wiki/Remote_Desktop_Protocol)) Terminal Server |
| 3396/tcp | [Novell](https://es.wikipedia.org/wiki/Novell) agente de impresión NDPS |
| 3690/tcp | [Subversion](https://es.wikipedia.org/wiki/Subversion) (sistema de control de versiones) |
| 3799/udp | [RADIUS](https://es.wikipedia.org/wiki/RADIUS) CoA -change of authorization |
| 4200/tcp | Angular, puerto por defecto |
| 4443/tcp and udp | [AOL Instant Messenger](https://es.wikipedia.org/wiki/AOL_Instant_Messenger) (sistema de mensajería)[[3]](https://es.wikipedia.org/wiki/Anexo:Puertos_de_red#cite_note-3) |
| 4662/tcp | [eMule](https://es.wikipedia.org/wiki/EMule) (aplicación de compartición de ficheros) |
| 4672/udp | [eMule](https://es.wikipedia.org/wiki/EMule) (aplicación de compartición de ficheros) |
| 4899/tcp | RAdmin (Remote Administrator), herramienta de administración remota (normalmente [troyanos](https://es.wikipedia.org/wiki/Troyano_(inform%C3%A1tica))) |
| 5000/tcp | [Universal plug-and-play](https://es.wikipedia.org/wiki/UPnP) |
| 5001/tcp | Agente v6 [Datadog](https://es.wikipedia.org/wiki/Datadog)[[4]](https://es.wikipedia.org/wiki/Anexo:Puertos_de_red#cite_note-4) |
| 5060/udp | [Session Initiation Protocol](https://es.wikipedia.org/wiki/Session_Initiation_Protocol) (SIP) |
| 5190/tcp | [AOL](https://es.wikipedia.org/wiki/AOL) y [AOL Instant Messenger](https://es.wikipedia.org/wiki/AOL_Instant_Messenger) |
| 5222/tcp | [Jabber/XMPP](https://es.wikipedia.org/wiki/Extensible_Messaging_and_Presence_Protocol) conexión de cliente |
| 5223/tcp | [Jabber/XMPP](https://es.wikipedia.org/wiki/Extensible_Messaging_and_Presence_Protocol) puerto por defecto para conexiones de cliente SSL |
| 5269/tcp | [Jabber/XMPP](https://es.wikipedia.org/wiki/Extensible_Messaging_and_Presence_Protocol) conexión de servidor |
| 5432/tcp | [PostgreSQL](https://es.wikipedia.org/wiki/PostgreSQL) sistema de gestión de bases de datos |
| 5517/tcp | [Setiqueue](https://es.wikipedia.org/wiki/Setiqueue?action=edit&redlink=1) proyecto SETI@Home |
| 5631/tcp | [PC-Anywhere](https://es.wikipedia.org/wiki/PC-Anywhere?action=edit&redlink=1) protocolo de escritorio remoto |
| 5632/udp | [PC-Anywhere](https://es.wikipedia.org/wiki/PC-Anywhere?action=edit&redlink=1) protocolo de escritorio remoto |
| 5400/tcp | [VNC](https://es.wikipedia.org/wiki/VNC) protocolo de escritorio remoto (usado sobre [HTTP](https://es.wikipedia.org/wiki/HTTP)) |
| 5500/tcp | [VNC](https://es.wikipedia.org/wiki/VNC) protocolo de escritorio remoto (usado sobre [HTTP](https://es.wikipedia.org/wiki/HTTP)) |
| 5600/tcp | [VNC](https://es.wikipedia.org/wiki/VNC) protocolo de escritorio remoto (usado sobre [HTTP](https://es.wikipedia.org/wiki/HTTP)) |
| 5700/tcp | [VNC](https://es.wikipedia.org/wiki/VNC) protocolo de escritorio remoto (usado sobre [HTTP](https://es.wikipedia.org/wiki/HTTP)) |
| 5800/tcp | [VNC](https://es.wikipedia.org/wiki/VNC) protocolo de escritorio remoto (usado sobre [HTTP](https://es.wikipedia.org/wiki/HTTP)) |
| 5900/tcp | [VNC](https://es.wikipedia.org/wiki/VNC) protocolo de escritorio remoto (conexión normal) |
| 6000/tcp | [X11](https://es.wikipedia.org/wiki/X11) usado para X-windows |
| 6024-6025/udp | Tigermeeting Android client discovery |
| 6026/tcp | Tigermeeting client/server communication |
| 6030-6031/udp | Tigermeeting Admin user discovery |
| 6032/tcp | Tigermeeting API for cloud management - TigerDriver |
| 6112/udp | [Blizzard](https://es.wikipedia.org/wiki/Blizzard_Entertainment) |
| 6129/tcp | [Dameware](https://es.wikipedia.org/wiki/Dameware?action=edit&redlink=1) Software conexión remota |
| 6346/tcp | [Gnutella](https://es.wikipedia.org/wiki/Gnutella) compartición de ficheros (Limewire, etc.) |
| 6347/udp | [Gnutella](https://es.wikipedia.org/wiki/Gnutella) |
| 6348/udp | [Gnutella](https://es.wikipedia.org/wiki/Gnutella) |
| 6349/udp | [Gnutella](https://es.wikipedia.org/wiki/Gnutella) |
| 6350/udp | [Gnutella](https://es.wikipedia.org/wiki/Gnutella) |
| 6355/udp | [Gnutella](https://es.wikipedia.org/wiki/Gnutella) |
| 6667/tcp | [IRC](https://es.wikipedia.org/wiki/IRC) [IRCU](https://es.wikipedia.org/wiki/IRCU?action=edit&redlink=1) Internet Relay Chat |
| 6881/tcp | [BitTorrent](https://es.wikipedia.org/wiki/BitTorrent) puerto por defecto |
| 6969/tcp | [BitTorrent](https://es.wikipedia.org/wiki/BitTorrent) puerto de tracker |
| 7100/tcp | Servidor de Fuentes [X11](https://es.wikipedia.org/wiki/X11) |
| 7100/udp | Servidor de Fuentes [X11](https://es.wikipedia.org/wiki/X11) |
| 7659/tcp y udp | [Polypheny](https://es.wikipedia.org/wiki/Polypheny?action=edit&redlink=1) interfaz de usuario (sistema de gestión de bases de datos) |
| 8000/tcp | [iRDMI](https://es.wikipedia.org/wiki/IRDMI?action=edit&redlink=1) por lo general, usado erróneamente en sustitución de 8080. También utilizado en el servidor de streaming ShoutCast. |
| 8080/tcp | [HTTP](https://es.wikipedia.org/wiki/HTTP) [HTTP-ALT](https://es.wikipedia.org/wiki/HTTP-ALT?action=edit&redlink=1) ver puerto 80. [Tomcat](https://es.wikipedia.org/wiki/Tomcat) lo usa como puerto por defecto. |
| 8118/tcp | [privoxy](https://es.wikipedia.org/wiki/Privoxy) |
| 9009/tcp | [Pichat](https://es.wikipedia.org/wiki/Pichat?action=edit&redlink=1) peer-to-peer chat server |
| 9898/tcp | Gusano Dabber (troyano/virus) |
| 10000/tcp | [Webmin](https://es.wikipedia.org/wiki/Webmin) (Administración remota web) |
| 19226/tcp | [Panda Security](https://es.wikipedia.org/wiki/Panda_Security) Puerto de comunicaciones de Panda Agent. |
| 12345/tcp | [NetBus](https://es.wikipedia.org/wiki/NetBus) [en:NetBus](https://en.wikipedia.org/wiki/NetBus) (troyano/virus) |
| 25565/tcp | [Minecraft](https://es.wikipedia.org/wiki/Minecraft) Puerto por defecto usado por servidores del juego. |
| 31337/tcp | [Back Orifice](https://es.wikipedia.org/wiki/Back_Orifice) herramienta de administración remota (por lo general troyanos) |
| 41121/tcp | Protocolo de transferencia utilizado por [Pandora FMS](https://es.wikipedia.org/wiki/Pandora_FMS).[[5]](https://es.wikipedia.org/wiki/Anexo:Puertos_de_red#cite_note-5) |
| 42000/tcp | Utilizado por [*Percona Monitoring Management*](https://es.wikipedia.org/wiki/Percona#Productos) para recoger [métricas generales](https://es.wikipedia.org/wiki/M%C3%A9trica_del_software).[[6]](https://es.wikipedia.org/wiki/Anexo:Puertos_de_red#cite_note-Percona-Monitoring-Managament-6) |
| 42001/tcp | Utilizado por *Percona Monitoring Management* para recabar datos de desempeño.[[6]](https://es.wikipedia.org/wiki/Anexo:Puertos_de_red#cite_note-Percona-Monitoring-Managament-6) |
| 42002/tcp | Utilizado por *Percona Monitoring Management* para recabar métricas de [MySQL](https://es.wikipedia.org/wiki/MySQL).[[6]](https://es.wikipedia.org/wiki/Anexo:Puertos_de_red#cite_note-Percona-Monitoring-Managament-6) |
| 27017/tcp | Utilizado por *Percona Monitoring Management* para recabar métricas de [MongoDB](https://es.wikipedia.org/wiki/MongoDB).[[6]](https://es.wikipedia.org/wiki/Anexo:Puertos_de_red#cite_note-Percona-Monitoring-Managament-6) |
| 42004/tcp | Utilizado por *Percona Monitoring Management* para recabar métricas de [ProxySQL](https://es.wikipedia.org/wiki/ProxySQL?action=edit&redlink=1).[[6]](https://es.wikipedia.org/wiki/Anexo:Puertos_de_red#cite_note-Percona-Monitoring-Managament-6) |
| 45003/tcp | [Calivent](https://es.wikipedia.org/wiki/Calivent?action=edit&redlink=1) herramienta de administración remota SSH con análisis de paquetes. |