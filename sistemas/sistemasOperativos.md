# Guía básica de sistemas operativos

Un **sistema operativo (SO)** es el software que coordina el hardware y permite ejecutar aplicaciones. Actúa como intermediario entre programas, usuario y componentes como el procesador, la memoria, los discos y los dispositivos conectados.

## Partes principales

- **Kernel o núcleo:** administra el procesador, la memoria, los dispositivos y los procesos. Las aplicaciones solicitan servicios al kernel mediante interfaces del sistema.
- **Controladores (drivers):** permiten que el kernel se comunique con dispositivos concretos, como tarjetas de red, cámaras o impresoras.
- **Sistema de archivos:** organiza los datos en archivos y carpetas, y registra dónde se guardan en el almacenamiento.
- **Servicios y procesos del sistema:** realizan tareas en segundo plano, como conectar a una red, iniciar sesión o gestionar audio.
- **Interfaz de usuario:** puede ser gráfica —ventanas, iconos y menús— o de línea de comandos.
- **Aplicaciones:** programas que el usuario ejecuta sobre el SO.

Una distinción útil es **modo kernel**, con acceso privilegiado al hardware, frente a **modo usuario**, donde normalmente corren aplicaciones con permisos limitados.

## Qué ocurre al encender un equipo

El proceso típico en una computadora es:

1. El **firmware** de la placa —BIOS antigua o UEFI moderna— inicializa el hardware y busca un dispositivo de arranque.
2. El firmware ejecuta un **gestor o cargador de arranque**.
3. El cargador coloca el kernel en memoria y le transfiere el control.
4. El kernel inicializa dispositivos y prepara el sistema de archivos principal.
5. Se inicia el primer proceso de usuario, que arranca servicios y prepara la pantalla de inicio de sesión.

En Linux, esta secuencia suele incluir firmware, GRUB u otro cargador, kernel, `initramfs` y un sistema de inicio como `systemd`; los detalles varían según el equipo y la distribución. 

### BIOS

La BIOS (Basic Input/Output System) es un tipo de firmware de la placa base. Al encender el equipo, realiza una comprobación inicial del hardware —por ejemplo, memoria y teclado— y busca desde qué dispositivo arrancar. Luego entrega el control al cargador de arranque (Bootloader).

En equipos modernos, la BIOS tradicional suele haber sido sustituida por UEFI, un firmware más actual. Aun así, muchas personas dicen “BIOS” para referirse a la configuración de arranque en general.

### Bootloader

Es el componente que inicia el sistema operativo. En una computadora, UEFI suele localizar y ejecutar un cargador como GRUB o Windows Boot Manager; en muchos teléfonos, el bootloader carga Android y puede ofrecer modos de recuperación o servicio. Puede estar bloqueado para impedir que se carguen sistemas no autorizados. Desbloquearlo o modificarlo puede borrar datos y afectar la seguridad del dispositivo.

### GRUB

**GRUB** es un cargador de arranque común en Linux. Puede mostrar un menú para escoger entre sistemas operativos o kernels y, después, cargar el kernel elegido y, cuando se necesita, el `initramfs`. No es el sistema operativo: funciona antes de que el kernel de Linux haya arrancado.

## Sistemas operativos conocidos

| Sistema | Dónde se usa principalmente | Características generales |
|---|---|---|
| **Windows** | PC de escritorio y portátiles | Amplia compatibilidad con programas y hardware |
| **macOS** | Computadoras Mac | Sistema de Apple, integrado con su hardware |
| **GNU/Linux** | Servidores, PC, supercomputadoras y dispositivos integrados | Hay muchas distribuciones, como Ubuntu, Debian y Fedora; suele permitir gran variedad de configuraciones |
| **Android** | Teléfonos, tabletas y otros dispositivos | Basado en el kernel Linux, con una plataforma y aplicaciones adaptadas a dispositivos móviles |
| **iOS / iPadOS** | iPhone y iPad | Sistemas de Apple diseñados para sus dispositivos móviles |
| **BSD** | Servidores, redes y usos especializados | Familia tipo Unix; FreeBSD y OpenBSD son ejemplos |

Que Android use el kernel Linux no significa que sea igual a una distribución GNU/Linux de escritorio: el entorno, las bibliotecas, las aplicaciones y la gestión del dispositivo son distintos.

## Sistemas de archivos

Un sistema de archivos define cómo se guardan y encuentran carpetas, nombres, permisos y datos en un volumen. **No es lo mismo que una partición**: una partición es una división del disco; el sistema de archivos organiza los datos dentro de ella.

| Sistema de archivos | Uso habitual |
|---|---|
| **NTFS** | Instalaciones de Windows. |
| **APFS** | Versiones modernas de macOS y dispositivos Apple compatibles. |
| **ext4** | Muy común en distribuciones Linux. |
| **exFAT** | Unidades externas que se quieren compartir entre sistemas. |
| **FAT32** | Dispositivos antiguos o de amplia compatibilidad; tiene límites importantes, incluido un máximo de 4 GB por archivo. |

La compatibilidad depende del sistema y de los controladores instalados: no conviene asumir que cualquier SO podrá escribir en cualquier formato.

En Linux, los discos y particiones suelen **montarse** dentro del árbol de directorios, por ejemplo en `/mnt` o `/media`. En Windows se suelen mostrar como unidades con letras, como `C:` o `D:`.

## Conceptos que conviene conocer

- **Proceso:** programa que está ejecutándose.
- **Memoria virtual:** mecanismo por el que el sistema administra la memoria y aísla procesos; puede apoyarse en almacenamiento cuando hace falta.
- **Permisos y usuarios:** controlan quién puede leer, modificar o ejecutar archivos y tareas.
- **Particiones:** divisiones de un dispositivo de almacenamiento; pueden alojar sistemas, datos o recuperación.
- **Interfaz gráfica y terminal:** dos formas de dar instrucciones al sistema. La terminal resulta útil para administración, pero los comandos pueden cambiar archivos y configuraciones.
- **Actualizaciones:** corrigen problemas, añaden mejoras y, en muchos casos, cierran vulnerabilidades.
- **Copia de seguridad:** una copia separada de los datos importantes ayuda a recuperarlos ante errores o fallos del dispositivo.