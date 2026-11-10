# Analisis de Memoria: Volatility 3
    
```bash
pip3 install volatility3 # instalar, con python3

vol -f /ruta/memoria os.plugin [--opciones]
# vol -h para ver informacion sobre plugins
```

## Windows

| Plugin | Función |
| --- | --- |
| `windows.info` | Información básica del sistema (OS, build, DTB). |
| `windows.pslist` | Lista procesos activos. |
| `windows.psscan` | Escanea estructuras de procesos (detecta procesos ocultos). |
| `windows.pstree` | Muestra procesos jerárquicamente. |
| `windows.dlllist` | Lista DLLs cargadas por proceso. |
| `windows.netstat` / `netscan` | Conexiones de red activas. |
| `windows.cmdline` | Líneas de comando de procesos. |
| `windows.dumpfiles` | Extrae archivos o regiones de memoria. |
| `windows.memmap` | Extraer memoria asociada a un pid: `--pid Nº --dump -o dir` |
| `windows.handles` | Información de handles abiertos. |
| `windows.hashdump` | Extrae hashes de cuentas. |
| `windows.malfind` | Busca inyecciones/malware en memoria. |

## MacOS    

| Plugin | Función |
| --- | --- |
| `mac.pslist` | Lista procesos. |
| `mac.netstat` | Conexiones de red. |
| `mac.lsmod` | Módulos kernel. |
| `mac.bash` | Historial de comandos. |
| `mac.list_files` | Archivos listados desde memoria. |
| `mac.malfind` | Búsqueda de malware/inyecciones. |
| `windows.memmap` | Extraer memoria asociada a un pid: `--pid Nº --dump -o dir` |

## Linux

| Plugin | Función |
| --- | --- |
| `linux.pslist` | Lista procesos. |
| `linux.bash` | Recupera historial de bash. |
| `linux.lsmod` | Módulos del kernel cargados. |
| `linux.lsof` | Archivos y sockets abiertos. |
| `linux.kmsg` | Mensajes del log kernel. |
| `linux.check_creds` | Detecta credenciales sospechosas. |
| `linux.vmayarascan` | Escanea memoria con firmas YARA. |
| `linux.sockstat` | Estados de sockets. |
| `windows.memmap` | Extraer memoria asociada a un pid: `--pid Nº --dump -o dir` |    