# Linux y Bash

## Qué es Linux

**Linux** es un **sistema operativo libre y de código abierto** basado en **Unix**, que permite la **gestión de hardware**, **programas**, **usuarios** y **recursos del sistema** de forma eficiente y segura.

### Componentes principales

- **Kernel (núcleo)**: administra el hardware, memoria, procesos y control de dispositivos.
- **Sistema de archivos**: organiza los datos en directorios y archivos.
- **Servicios y procesos**: programas que se ejecutan, ya sea en segundo plano o interactuando con el usuario.
- **Distribuciones (distros)**: versiones adaptadas del sistema con diferentes enfoques y herramientas.

### Características clave

- **Multitarea**: puede ejecutar varios programas simultáneamente.
- **Multiusuario**: varios usuarios pueden usar el sistema al mismo tiempo.
- **Seguridad**: permisos estrictos, aislamiento de usuarios y configuraciones de firewall.
- **Portabilidad**: funciona en servidores, escritorios, dispositivos embebidos y móviles.

### Ventajas de Linux

- **Gratuito y de código abierto**.
- **Seguro y estable**, ideal para servidores y sistemas críticos.
- **Flexible**, funciona desde servidores y PCs hasta dispositivos embebidos.
- **Gran comunidad y documentación**, con soporte abundante.

## Distribuciones más populares

| Distro | Características | Público objetivo |
| --- | --- | --- |
| **Ubuntu** | Basada en Debian, amigable, amplia comunidad, soporte de software moderno | Principiantes y escritorios |
| **Linux Mint** | Basada en Ubuntu, escritorio tradicional, fácil de usar | Usuarios de escritorio que vienen de Windows |
| **Debian** | Muy estable, enfoque en robustez, repositorios grandes | Servidores, desarrollo y entusiastas |
| **Fedora** | Últimas versiones de software, innovadora, entorno GNOME | Desarrolladores y usuarios avanzados |
| **CentOS** | Derivada de Red Hat, estable y segura | Servidores empresariales |
| **Arch Linux** | Minimalista, muy personalizable, rolling release | Usuarios avanzados que quieren controlar todo |
| **Alpine Linux** | Extremadamente ligera, seguridad enfocada, usada en contenedores | Contenedores Docker, sistemas embebidos y servidores ligeros |

## Usuarios y permisos

>Linux es **multiusuario**: cada usuario tiene **UID (User ID)** y pertenece a **grupos (GID)**.

### Roles principales
- **Root (superusuario)**: acceso total al sistema.
- **Usuarios normales**: permisos limitados.
### Conceptos importantes
- Control de acceso mediante **usuarios y grupos**.
- Cambios de permisos y propiedad permiten **proteger datos sensibles.**

### Tipos de usuarios en Linux

Cada archivo o directorio está asociado a tres categorías de usuarios.

- **Propietario (Owner)** → Usuario que creó o es dueño del archivo.
- **Grupo (Group)** → Grupo de usuarios asignado al archivo.
- **Otros (Others)** → Todos los demás usuarios que no son ni propietario ni parte del grupo.

### Tipos de permisos

- **Lectura (r) →** Puede **ver el contenido** del archivo o listar el directorio
- **Escritura (w) →** Puede **modificar o borrar** el archivo; crear/eliminar archivos dentro de un directorio.
- **Ejecución (x) →** Puede **ejecutar** un archivo o **entrar en un directorio** (`cd`)

### Cómo leer Permisos en Notación Numérica

> **Valores de cada permiso**: `r = 4`, `w = 2`, `x = 1`, `- = 0`

```
-rw-r--r-- → 644
    
rw- → r(4) + w(2) + -(0) = 6
r-- → r(4) + -(0) + -(0) = 4
r-- → r(4) + -(0) + -(0) = 4
``` 
### Estructura de los Permisos de un Archivo o Carpeta

1. **Primer carácter** → tipo de archivo
    - `-`  → archivo normal
    - `d` → directorio
    - `l` → enlace simbólico
    - `c` → dispositivo de caracteres
    - `b` → dispositivo de bloques
2. **Siguientes 9 caracteres** → permisos divididos en los tres grupos (3 caracteres cada uno, rwx). Para ello se colocará la letra si se concede el permiso o `-` si no.

## Sistema de archivos

Linux organiza los archivos en un **árbol jerárquico** que comienza en la raíz `/`. Cada directorio tiene un propósito específico:

- **/** → Raíz del sistema, punto de inicio del árbol de directorios.
    - Contiene todos los demás directorios.
- **/bin** → Comandos esenciales para todos los usuarios.
    - Ejemplos: `ls`, `cp`, `mv`, `cat`.
    - Permisos: `rwxr-xr-x` (root dueño, otros pueden ejecutar).
- **/sbin** → Comandos del sistema que requieren permisos de root.
    - Ejemplos: `shutdown`, `fdisk`, `ifconfig`.
    - Permisos: `rwxr-xr-x`.
- **/etc** → Archivos de configuración del sistema y servicios.
    - Ejemplos: `passwd`, `fstab`, `hosts`.
    - Permisos: `rw-r--r--` para archivos críticos, root dueño.
- **/home** → Directorios personales de usuarios.
    - Ejemplo: `/home/usuario`.
    - Permisos: `drwx------` (solo usuario dueño y root pueden acceder).
- **/var** → Archivos variables que cambian durante el funcionamiento del sistema.
    - Subdirectorios importantes:
        - `/var/log` → logs del sistema
        - `/var/spool` → colas de impresión y correos
        - `/var/lib` → bases de datos y estado de servicios
    - Permisos: `drwxr-xr-x`, archivos de log `rw-r-----`.
- **/tmp** → Archivos temporales generados por aplicaciones o el sistema.
    - Permisos: `drwxrwxrwt` (**sticky bit** activo para seguridad).
    - Se limpia automáticamente al reiniciar.
- **/usr** → Programas, librerías y documentación de usuario.
    - Subdirectorios:
        - `/usr/bin` → ejecutables de usuario
        - `/usr/sbin` → ejecutables de administración (root)
        - `/usr/lib` → librerías compartidas
        - `/usr/share` → datos, iconos, documentación
    - Permisos: `drwxr-xr-x`.
- **/dev** → Archivos especiales que representan dispositivos.
    - Ejemplos: `/dev/sda` (disco), `/dev/tty` (terminal), `/dev/null`.
    - Permisos: `crw-rw-rw-` o `brw-rw----`.
- **/boot** → Archivos necesarios para el arranque del sistema.
    - Ejemplos: `vmlinuz` (kernel), `initrd.img`, GRUB.
    - Permisos: `rw-r--r--` para archivos, root dueño.
- **/lib** → Librerías esenciales para binarios en `/bin` y `/sbin`.
    - Ejemplos: `libc.so.6`, `libm.so`.
    - Permisos: `rwxr-xr-x`.
- **/media** → Puntos de montaje de dispositivos externos automáticos.
- **/mnt** → Puntos de montaje temporales para discos u otros sistemas.
- **/proc** → Sistema de archivos virtual que muestra información del kernel y procesos.
- **/sys** → Información y control de dispositivos y drivers del kernel.
- **/run** → Información de runtime: PID de procesos, sockets activos.
    - Temporal, se limpia al reiniciar.
- **/lost+found** → Archivos recuperados tras errores de disco en particiones ext4/ext3.

> Todo en Linux es un **archivo**, incluso los **dispositivos físicos**.

> Los permisos de archivos controlan **quién puede leer, escribir o ejecutar**.

## Procesos y gestión

> Un **proceso** es una **instancia en ejecución de un programa**.

- Tiene un **PID (Process ID)** único.
- Está asociado a un **usuario** (quien lo ejecutó).
- Puede tener un **proceso padre (PPID)**.
- Consume **recursos del sistema** (CPU, memoria, E/S).
- Tiene un **estado** (en ejecución, detenido, zombie, etc.).
    - **R (Running):** en ejecución o listo para ejecutarse.
    - **S (Sleeping):** en espera de un recurso o evento (estado común).
    - **D (Uninterruptible sleep):** espera ininterrumpible (por ejemplo, E/S de disco).
    - **T (Stopped):** detenido por señal o usuario (`Ctrl + Z`).
    - **Z (Zombie):** terminó pero no fue eliminado por el padre.
    - **I (Idle):** inactivo (esperando trabajo, típico del kernel).

### **Tipos de procesos**

| Tipo | Descripción | Ejemplo |
| --- | --- | --- |
| **Interactivo** | Iniciado por el usuario desde la terminal. | `ls`, `nano`, `python script.py` |
| **Background** | Se ejecuta sin bloquear la terminal. | `./script.sh &` |
| **Daemon (servicio)** | Se ejecuta automáticamente al inicio del sistema, sin interacción del usuario. | `sshd`, `cron`, `cupsd` |
| **Hijo (child)** | Creado por otro proceso (padre). | `bash` lanza `ls` → `ls` es hijo de `bash` |
| **Zombie** | Proceso finalizado pero aún registrado en la tabla de procesos. | Ocurre por errores de gestión del padre |
| **Huérfano (orphan)** | Su proceso padre terminó antes que él; adoptado por `init` o `systemd`. | — |

### **Identificadores importantes**

- **PID:** identificador único del proceso.
- **PPID:** identificador del proceso padre.
- **UID:** usuario propietario.
- **GID:** grupo propietario.
- **TTY:** terminal asociada (si la tiene).

### **Archivos virtuales del sistema relacionados**

- `/proc/[PID]/` → carpeta virtual con información del proceso.
- `/proc/[PID]/status` → muestra estado, memoria, CPU, usuario, etc.
- `/proc/cpuinfo` → información de CPU.
- `/proc/meminfo` → estado de la memoria.
- `/proc/loadavg` → carga promedio del sistema.