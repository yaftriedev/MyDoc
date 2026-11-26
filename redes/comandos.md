# Ping
```bash
# Enviar 4 paquetes
ping -c 4 example.com

# Enviar paquetes hasta detenerlo con Ctrl+C
ping example.com

# Fijar el intervalo entre paquetes (segundos)
ping -i 2 example.com

# Definir el tamaño del paquete (bytes)
ping -s 1200 example.com

# Usar IPv4 o IPv6
ping -4 example.com
ping -6 example.com

# Establecer un límite de tiempo (segundos)
ping -w 10 example.com

# Mostrar el resumen estadístico al detener
ping -c 10 example.com
```

# Dig
```bash
# Consulta DNS básica
dig example.com

# Consultar tipos de registro comunes
dig example.com A
dig example.com AAAA
dig example.com MX
dig example.com NS
dig example.com TXT
dig example.com CNAME
dig example.com SOA

# Consultar un servidor DNS específico
dig @1.1.1.1 example.com
dig @8.8.8.8 example.com MX

# Búsqueda inversa de una dirección IP
dig -x 8.8.8.8

# Mostrar solo la respuesta
dig +short example.com
dig +short example.com MX

# Mostrar la ruta de delegación DNS
dig +trace example.com

# Usar TCP en vez de UDP
dig +tcp example.com

# Mostrar estadísticas y detalles de la consulta
dig +stats example.com
```

# Traceroute
```bash
# Trazar la ruta hacia un destino
traceroute example.com

# Usar IPv4 o IPv6
traceroute -4 example.com
traceroute -6 example.com

# Limitar la cantidad máxima de saltos
traceroute -m 20 example.com

# Cambiar la cantidad de pruebas por salto
traceroute -q 1 example.com

# Usar ICMP en lugar del método predeterminado
traceroute -I example.com

# Usar TCP hacia un puerto concreto
traceroute -T -p 443 example.com

# Alternativa que suele estar disponible en Linux
tracepath example.com
```

# IP
```bash
# Mostrar interfaces y direcciones
ip addr
ip -br addr

# Mostrar interfaces activas
ip link

# Mostrar la tabla de rutas
ip route

# Mostrar vecinos de la red local (caché ARP/NDP)
ip neigh

# Consultar una interfaz concreta
ip addr show dev eth0

# Consultar la ruta que se usaría hacia un destino
ip route get 1.1.1.1
```

# SS
```bash
# Mostrar sockets TCP y UDP en escucha
ss -tuln

# Mostrar conexiones TCP
ss -tn

# Mostrar conexiones UDP
ss -un

# Mostrar procesos asociados a sockets (puede requerir sudo)
sudo ss -tulpn

# Mostrar estadísticas de sockets
ss -s

# Filtrar conexiones por puerto local
ss -tn 'sport = :443'

# Filtrar conexiones hacia un puerto remoto
ss -tn 'dport = :443'

# Mostrar sockets Unix
ss -x
```

# Nmap
```bash
# Revisar un equipo propio o autorizado
nmap 192.168.1.10

# Revisar varios equipos indicados
nmap 192.168.1.10 192.168.1.20

# Revisar puertos específicos
nmap -p 22,80,443 192.168.1.10

# Revisar un rango pequeño de puertos
nmap -p 1-1000 192.168.1.10

# Detectar servicios y versiones en puertos encontrados
nmap -sV 192.168.1.10

# Revisar los puertos más comunes
nmap --top-ports 100 192.168.1.10

# Revisar únicamente la disponibilidad del host, sin escanear puertos
nmap -sn 192.168.1.10

# Revisar equipos de una red propia y autorizada
nmap -sn 192.168.1.0/24

# Guardar resultados en varios formatos
nmap -oA resultado 192.168.1.10

# Guardar resultados en texto normal
nmap -oN resultado.txt 192.168.1.10

# Revisar la propia máquina
nmap 127.0.0.1
```

# Tcpdump
```bash
# Capturar tráfico en una interfaz
sudo tcpdump -i eth0

# Listar interfaces disponibles
sudo tcpdump -D

# Mostrar direcciones y puertos numéricos
sudo tcpdump -i eth0 -nn

# Limitar la captura a 50 paquetes
sudo tcpdump -i eth0 -c 50

# Capturar tráfico de un host
sudo tcpdump -i eth0 host 192.168.1.10

# Capturar tráfico hacia o desde una dirección
sudo tcpdump -i eth0 src host 192.168.1.10
sudo tcpdump -i eth0 dst host 192.168.1.10

# Filtrar por puerto
sudo tcpdump -i eth0 port 53

# Filtrar por protocolo
sudo tcpdump -i eth0 tcp
sudo tcpdump -i eth0 udp
sudo tcpdump -i eth0 icmp

# Combinar filtros
sudo tcpdump -i eth0 'host 192.168.1.10 and port 443'

# Mostrar contenido en formato ASCII cuando sea legible
sudo tcpdump -i eth0 -A

# Guardar una captura en un archivo
sudo tcpdump -i eth0 -w captura.pcap

# Leer una captura guardada
tcpdump -nn -r captura.pcap

# Limitar la captura a 100 paquetes y guardarla
sudo tcpdump -i eth0 -c 100 -w captura.pcap
```

# CURL
```bash
# ARGUMENTOS PRINCIPALES DE CURL

# -X <método>
# Especifica el método HTTP: GET, POST, PUT, DELETE, etc.
-X GET
-X POST

# -H "<cabecera>"
# Añade una cabecera HTTP, por ejemplo Content-Type o Authorization
-H "Content-Type: application/json"
-H "Authorization: Bearer TU_TOKEN"

# -d "<datos>"
# Envía datos en el cuerpo de la petición (por defecto usa POST si no se indica -X)
-d "usuario=juan&clave=1234"
-d '{"nombre": "Juan"}'
```

```bash
# PETICIÓN GET
# Obtener todos los usuarios
curl -X GET https://api.ejemplo.com/usuarios

# PETICIÓN GET con autenticación
# Obtener perfil de usuario autenticado
curl -X GET https://api.ejemplo.com/perfil -H "Authorization: Bearer TU_TOKEN"

# PETICIÓN POST (JSON)
# Crear un nuevo usuario
curl -X POST https://api.ejemplo.com/usuarios \
     -H "Content-Type: application/json" \
     -d '{"nombre": "Juan", "email": "juan@correo.com"}'

# PETICIÓN POST (formulario)
# Iniciar sesión con usuario y contraseña
curl -X POST https://api.ejemplo.com/login \
     -d "usuario=juan&clave=1234"

# PETICIÓN PUT
# Actualizar datos del usuario con ID 1
curl -X PUT https://api.ejemplo.com/usuarios/1 \
     -H "Content-Type: application/json" \
     -d '{"email": "nuevo@correo.com"}'

# PETICIÓN DELETE
# Eliminar usuario con ID 1
curl -X DELETE https://api.ejemplo.com/usuarios/1

# PETICIÓN CON ARCHIVO (multipart/form-data)
# Subir un archivo
curl -X POST https://api.ejemplo.com/upload \
     -F "archivo=@/ruta/a/archivo.txt"

# GUARDAR RESPUESTA EN ARCHIVO
# Descargar respuesta en un archivo local
curl -o datos.json https://api.ejemplo.com/datos

# MOSTRAR CABECERAS DE RESPUESTA
# Ver encabezados HTTP completos
curl -i https://api.ejemplo.com/usuarios
```