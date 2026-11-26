# Bash: Utilidades Básicas


## Utilidades de gestión de archivos y directorios
- `ls` → lista el contenido de un directorio.
    - `ls -l` → muestra detalles (permisos, tamaño, fechas).
- `cd` → cambia de directorio.
- `pwd` → muestra la ruta del directorio actual.
- `cp` → copia archivos o directorios.
- `mv` → mueve o renombra archivos/directorios.
- `rm` → elimina archivos o directorios.
- `mkdir` → crea directorios.
- `rmdir` → elimina directorios vacíos.
- `find` → busca archivos según nombre, tipo o fecha.
    - Ejemplo: `find /home -name "*.txt"`
- `locate` → busca rápidamente archivos indexados (usa `updatedb` para actualizar el índice).
- `du` → muestra el tamaño de archivos/directorios.
    - Ejemplo: `du -h /home`
- `df` → muestra espacio disponible en discos.
    - Ejemplo: `df -h`

## Utilidades de visualización y manipulación de texto
- `cat` → muestra el contenido completo de un archivo.
- `less` / `more` → muestra el contenido de forma paginada.
- `head` → muestra las primeras líneas de un archivo.
- `tail` → muestra las últimas líneas de un archivo (útil para logs).
    - Ejemplo: `tail -f /var/log/syslog` → seguimiento en tiempo real.
- `grep` → busca patrones de texto dentro de archivos.
    - Ejemplo: `grep "error" /var/log/syslog`
- `sort` → ordena líneas de texto.
- `uniq` → elimina líneas duplicadas.
- `cut` → extrae columnas o campos de texto.
- `tr` → reemplaza o elimina caracteres.
- `awk` → lenguaje de procesamiento de texto para columnas.
    - Ejemplo: `awk '{print $1,$3}' archivo.txt`
- `sed` → editor de texto en línea, ideal para reemplazos.
    - Ejemplo: `sed 's/viejo/nuevo/g' archivo.txt`

## Utilidades de sistema y procesos
- `ps` → muestra los procesos activos.
    - `ps -aux` → muestra detalles.
- `top` → monitoriza procesos en tiempo real.
- `htop` → versión avanzada de `top` (con interfaz interactiva).
- `kill` → termina procesos por PID.
- `pkill` → termina procesos por nombre.
- `nice` / `renice` → establece o cambia la prioridad de procesos.
- `uptime` → muestra tiempo activo del sistema y carga media.
- `free` → muestra el uso de memoria RAM y swap.
- `vmstat` → estadísticas de procesos, memoria, E/S y CPU.
- `lsof` → lista archivos abiertos por procesos.
- `dmesg` → muestra mensajes del kernel (útil para hardware).

## Utilidades de red
- `ping` → comprueba conectividad con otro host.
- `ifconfig` (o `ip addr`) → muestra o configura interfaces de red.
- `ip route` → muestra la tabla de enrutamiento.
- `netstat` (o `ss`) → muestra conexiones de red y puertos abiertos.
- `nslookup` / `dig` → consulta DNS.
- `wget` → descarga archivos desde Internet.
- `curl` → transfiere datos desde o hacia un servidor.
- `scp` → copia archivos entre máquinas mediante SSH.
- `ssh` → accede a servidores remotos de forma segura.
- `traceroute` → muestra la ruta que sigue un paquete hasta su destino.
- `nmap` → escanea redes y puertos (requiere instalación).

## Utilidades de compresión y empaquetado
- `tar` → empaqueta y desempaqueta archivos.
    - Ejemplo: `tar -czvf archivo.tar.gz carpeta/`
- `gzip` / `gunzip` → comprime o descomprime archivos `.gz`.
- `zip` / `unzip` → crea y extrae archivos `.zip`.
- `bzip2` / `bunzip2` → compresión alternativa más eficiente.
- `xz` / `unxz` → compresión de alto nivel.

## Utilidades de administración del sistema
- `sudo` → ejecuta comandos como superusuario.
- `su` → cambia de usuario o inicia sesión como root.
- `passwd` → cambia la contraseña de un usuario.
- `adduser` / `useradd` → crea nuevos usuarios.
- `deluser` / `userdel` → elimina usuarios.
- `groupadd` / `groupdel` → gestiona grupos de usuarios.
- `chown` → cambia propietario y grupo de un archivo.
    - Ejemplo: `chown juan:usuarios archivo.txt`
- `chmod` → cambia permisos de archivo (numéricos o simbólicos).
    - Ejemplo: `chmod 755 script.sh`
- `chgrp` → cambia solo el grupo de un archivo.
- `hostname` → muestra o cambia el nombre del host.
- `date` → muestra o cambia la fecha y hora.
- `timedatectl` → gestiona la zona horaria.

## Utilidades de información del sistema
- `uname -a` → muestra información del kernel y sistema operativo.
- `lsb_release -a` → muestra detalles de la distribución.
- `hostnamectl` → información del host y del sistema operativo.
- `lscpu` → información del procesador.
- `lsblk` → muestra dispositivos de bloques (discos, particiones).
- `lspci` → lista dispositivos PCI.
- `lsusb` → lista dispositivos USB conectados.

## Utilidades de paquetes (según distribución)

### Debian / Ubuntu
- `apt update` → actualiza la lista de paquetes.
- `apt upgrade` → instala actualizaciones disponibles.
- `apt install <paquete>` → instala un paquete.
- `apt remove <paquete>` → desinstala un paquete.
- `apt search <nombre>` → busca un paquete.
### Arch Linux
- `pacman -S <paquete>` → instala.
- `pacman -R <paquete>` → elimina.
- `pacman -Sy` → sincroniza base de datos.
- `pacman -Syu` → actualiza el sistema.
### Fedora / RHEL / CentOS
- `dnf install <paquete>`
- `dnf remove <paquete>`
- `dnf update`
### Alpine Linux
- `apk update`
- `apk add <paquete>`
- `apk del <paquete>`

## Utilidades de registro y monitoreo
- `journalctl` → muestra logs de `systemd`.
- `tail -f /var/log/syslog` → sigue los logs del sistema en tiempo real.
- `dmesg` → mensajes del kernel (hardware, arranque, errores).
- `uptime` → muestra tiempo encendido y carga promedio.
- `vmstat` → estadísticas de procesos, memoria y CPU.
- `iotop` → monitoriza uso de disco por proceso.
- `sar` → reporta actividad del sistema (requiere `sysstat`).

# Bash: Operadores de dirección

| Operador | Dirección | Acción | Sobrescribe / Añade |
| --- | --- | --- | --- |
| `>` | salida → archivo | Redirige salida estándar | Sobrescribe |
| `>>` | salida → archivo | Redirige salida estándar | Añade |
| `<` | archivo → entrada | Redirige entrada estándar | — |
| `<<` | texto → entrada | Inserta bloque de texto (here doc) | — |

# Bash: Variables

```bash
# Se declaran como var=valor (sin espacios).
nombre="Paco"
edad=25

# Para acceder a ellos se usa $var
echo $nombre
echo "Tengo $edad años"

# Variables de entorno: Son variables del sistema accesibles globalmente
echo $HOME      # Ruta del usuario
echo $USER      # Nombre del usuario
echo $PATH      # Directorios donde se buscan comandos

# Para crear una variable de entorno
export VAR="valor"

# Sustitución de comandos
fecha=$(date)
echo "Hoy es $fecha"

# Lectura desde teclado
read -p "Introduce tu nombre: " nombre
echo "Hola, $nombre
```

# Bash: Condicionales

```bash
if [ condición ]; then
    # comandos si se cumple
elif [ otra_condición ]; then
    # comandos si se cumple la segunda
else
    # comandos si no se cumple ninguna
fi
```

| Comparador | Numerico | Comparador | Caracteres | Prueba | Archivos |
| --- | --- | --- | --- | --- | --- |
| `-eq` | Igual (`=`) | `=` | Igual | `-e archivo` | Existe |
| `-ne` | No igual | `!=` | Distinto | `-f archivo` | Es un archivo regular |
| `-lt` | Menor que | `-z` | Cadena vacía | `-d archivo` | Es un directorio |
| `-le` | Menor o igual | `-n` | Cadena no vacía | `-r archivo` | Tiene permiso de lectura |
| `-gt` | Mayor que |  |  | `-w archivo` | Tiene permiso de escritura |
| `-ge` | Mayor o igual |  |  | `-x archivo` | Tiene permiso de ejecución |

# Bash: Bucles

```bash
# Bucle for: Recorre una lista de valores
for i in 1 2 3 4 5; do
  echo "Número: $i"
done

# Bucle for: Recorriendo archivos
for archivo in *.txt; do
  echo "Archivo: $archivo"
done

# Bucle for: Con rango de números
for i in {1..5}; do
  echo "Iteración $i"
done

# Bucle for: estilo c
for (( i=0; i<5; i++ )); do
  echo "Valor: $i"
done

# Bucle while do
while [ condición ]; do
  # Comandos a ejecutar
done

# break → Sale del bucle inmediatamente.
# continue → Salta a la siguiente iteración.
for i in {1..10}; do
  if [ $i -eq 5 ]; then
    echo "Salto el número 5"
    continue
  fi
  echo "Número: $i"
  if [ $i -eq 8 ]; then
    echo "Rompo el bucle"
    break
  fi
done
```

# Firewall: `iptables`

```bash
iptables -A [chain] [condiciones] -j [accion]
sudo netfilter-persistent save
```

| Chains | Significado |
| --- | --- |
| `INPUT` | Tráfico destinado a tu máquina |
| `OUTPUT` | Tráfico generado por tu máquina |
| `FORWARD` | Tráfico que atraviesa tu máquina |

| Condiciones | Qué hace | Ejemplo |
| --- | --- | --- |
| `-p` | Protocolo | `-p tcp` |
| `-s` | IP/red de origen | `-s 192.168.1.10` |
| `-d` | IP/red destino | `-d 10.0.0.5` |
| `-i` | Interfaz de entrada | `-i eth0` |
| `-o` | Interfaz de salida | `-o eth0` |
| `--sport` | Puerto origen | `--sport 443` |
| `--dport` | Puerto destino | `--dport 80` |

| Acción  `-j` | Qué hace |
| --- | --- |
| `ACCEPT` | Permite el paquete |
| `DROP` | Descarta silenciosamente |
| `REJECT` | Rechaza y envía respuesta |
| `LOG` | Registra el paquete |
| `RETURN` | Vuelve a la chain anterior |
| `DNAT` | Cambia destino |
| `SNAT` | Cambia origen |
| `MASQUERADE` | NAT dinámico |