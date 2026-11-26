# Docker

>**Docker** es una plataforma que permite empaquetar aplicaciones y sus dependencias en **contenedores**.

Un **contenedor** es como una “mini-máquina” que incluye todo lo necesario para ejecutar un programa: sistema base, librerías, configuraciones, etc.
## Ventajas
- **Portabilidad:** funciona igual en cualquier sistema (Windows, Linux, macOS, servidor, nube…).
- **Aislamiento:** cada contenedor es independiente.
- **Ligereza:** los contenedores usan el mismo kernel del sistema, no máquinas virtuales completas.
- **Reproducibilidad:** puedes crear entornos idénticos en segundos.

## Conceptos básicos
- **Dockerfile**: Archivo que define cómo construir una imagen.
- **Imagen (image)**: Plantilla de solo lectura (por ejemplo: `ubuntu`, `nginx`, `python:3.12`).
- **Docker Hub**: Repositorio público de imágenes oficiales.
- **Contenedor**: Instancia en ejecución de una imagen.
- **Volumen**: Carpeta compartida entre el contenedor y el host (para persistir datos).
- **Red**: Permite que varios contenedores se comuniquen entre sí.

## Crear una Imagen 
```
docker build <args> <folder>
```
- `-t` o `--tag`:  Asigna nombre y etiqueta a la imagen
- `--build-arg`:  Pasa argumentos definidos con `ARG` en el Dockerfile
- `-f` o `--file`:  Especifica otro nombre o ubicación del Dockerfile
- `--no-cache`:  Construye sin usar capas anteriores (desde cero)
- `--pull`:  Fuerza descarga de la imagen base más reciente

## Ejecutar un Contenedor: 
```
docker run <args> <image> <cmd>
```
- `-d`: Ejecuta en segundo plano (detached)
- `-p`: Mapea puertos: `host:contenedor`. Ej: `-p 8080:80`
- `--name`: Asigna un nombre al contenedor. Ej: `--name miweb`
- `-e`: Define variables de entorno. Ej: `-e ENV=produccion`
- `-v`: Monta un volumen: `host:contenedor`. Ej: `-v $(pwd):/app`
- `--rm`: Elimina el contenedor al detenerlo
- `-it`: Modo interactivo con terminal (`-i` = input, `-t` = tty)
- `--network`: Conecta el contenedor a una red específica. Ej: `--network mi_red`
- `--restart`: Política de reinicio (por ejemplo: `always`, `on-failure`).
- `--cpu` / `--memory`: Limita recursos del contenedor. Ej: `--memory 512m`
- `--entrypoint`: Sobrescribe el comando por defecto. Ej: `--entrypoint /bin/sh`

## Otros Comandos
- `docker images`: Ver imágenes locales
- `docker ps`:  Ver contenedores en ejecución
- `docker ps -a`:  Ver todos los contenedores
- `docker stop <id>`: Detener un contenedor
- `docker rm <id>`: Eliminar un contenedor
- `docker rmi <id>`: Eliminar una imagen
- `docker system prune`: Limpiar recursos no usados
- `docker pull image:tag`: Descargar una Imagen de [Docker Hub](https://hub.docker.com/)