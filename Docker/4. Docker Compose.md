# Docker Compose: qué es y cómo funciona

Docker es una herramienta muy útil para Data Scientists, pero muchos proyectos necesitan varios contenedores trabajando juntos: por ejemplo, una aplicación, una API y una base de datos. Para definir y ejecutar esos servicios como una sola aplicación se utiliza **Docker Compose**.

Compose permite declarar en un archivo YAML qué servicios necesita el proyecto, cómo se construyen o qué imágenes usan, qué puertos exponen y cómo se conectan entre sí. Después, puedes iniciar o detener el conjunto con comandos de Compose.

## ¿Por qué usar varios contenedores?

Una opción sería ejecutar varios microservicios dentro de un solo contenedor. Sin embargo, así comparten el mismo ciclo de vida y resulta más difícil mantenerlos, escalarlos o solucionar fallos. Si cada servicio se ejecuta en su propio contenedor, puedes administrarlo de forma independiente.

Con Docker Compose puedes describir las relaciones entre esos contenedores. Por ejemplo, una API puede conectarse a una base de datos usando el nombre del servicio como host. Si un servicio falla, los demás no tienen por qué detenerse automáticamente; eso depende de cómo esté configurada la aplicación y de sus dependencias.

| Enfoque | Función | Ejemplo |
|---|---|---|
| Un contenedor para varios servicios | Ejecuta varios procesos dentro de un mismo contenedor. | API y trabajador en el mismo contenedor |
| Un contenedor por servicio | Aísla los servicios y permite administrarlos por separado. | Contenedores para API, aplicación y base de datos |
| Docker Compose | Define y ejecuta el conjunto de servicios. | `docker compose up -d` |

Compose se usa mucho en desarrollo local, pruebas y entornos de trabajo pequeños. Para producción, la opción adecuada depende de la infraestructura: Compose puede integrarse en distintos flujos, pero Docker Swarm y Kubernetes tienen sus propios mecanismos de despliegue. **Kompose** puede ayudar a convertir archivos de Compose en manifiestos de Kubernetes, aunque puede ser necesario revisarlos y adaptarlos.

## El archivo `compose.yaml`

La configuración suele escribirse en un archivo llamado `compose.yaml`. En él se declaran los servicios y, cuando hace falta, las redes, los volúmenes, las configuraciones y los secretos.

| Apartado | Función | Ejemplo |
|---|---|---|
| `services` | Declara los contenedores de la aplicación. | `services: api:` |
| `networks` | Define redes para la comunicación entre servicios. | `networks: backend:` |
| `volumes` | Conserva datos fuera del ciclo de vida del contenedor. | `volumes: db_data:` |
| `configs` | Proporciona archivos de configuración a los servicios. | `configs: app_config:` |
| `secrets` | Gestiona datos sensibles en entornos compatibles. | `secrets: db_password:` |
| `version` | Campo de versión del formato, hoy normalmente innecesario. | Se suele omitir |

## Ejemplo: aplicación, API y base de datos

El siguiente ejemplo define una aplicación web, una API y una base de datos PostgreSQL. La API se conecta a la base de datos mediante el nombre del servicio `db`. El volumen `db_data` conserva los datos de PostgreSQL aunque se reemplace el contenedor.

```yaml
services:
  app:
    build: ./app
    ports:
      - "8080:8080"
    depends_on:
      - api

  api:
    build: ./api
    ports:
      - "8000:8000"
    environment:
      DATABASE_URL: postgresql://appuser:${DB_PASSWORD}@db:5432/appdb
    depends_on:
      - db

  db:
    image: postgres:16
    environment:
      POSTGRES_USER: appuser
      POSTGRES_PASSWORD: ${DB_PASSWORD}
      POSTGRES_DB: appdb
    volumes:
      - db_data:/var/lib/postgresql/data

volumes:
  db_data:
```

Crea un archivo `.env` junto al `compose.yaml` para proporcionar la contraseña:

```env
DB_PASSWORD=elige_una_contrasena
```

Añade `.env` a `.gitignore` para evitar subir credenciales al repositorio. En producción, conviene usar un sistema de gestión de secretos adecuado al entorno.

| Arg. o campo | Función | Ejemplo |
|---|---|---|
| `build` | Construye la imagen usando el directorio indicado. | `build: ./api` |
| `image` | Indica la imagen que se descargará o utilizará. | `image: postgres:16` |
| `ports` | Publica un puerto del contenedor en el host. | `"8000:8000"` |
| `environment` | Define variables de entorno para el servicio. | `POSTGRES_DB: appdb` |
| `${DB_PASSWORD}` | Sustituye el valor por una variable del entorno o de `.env`. | `POSTGRES_PASSWORD: ${DB_PASSWORD}` |
| `depends_on` | Declara una dependencia y establece el orden básico de inicio. | `depends_on: - db` |
| `volumes` | Monta un volumen u otra ruta en el contenedor. | `db_data:/var/lib/postgresql/data` |

>**Importante:** `depends_on` establece el orden básico de inicio, pero no significa por sí solo que la base de datos ya esté lista para aceptar conexiones. Para esperar a que esté saludable, puedes configurar un `healthcheck` en la base de datos y usar `condition: service_healthy` en el servicio dependiente.

## Comandos básicos

| Comando | Función | Ejemplo |
|---|---|---|
| `docker compose up` | Construye, si hace falta, e inicia los servicios. | `docker compose up` |
| `docker compose up -d` | Inicia los servicios en segundo plano. | `docker compose up -d` |
| `docker compose build` | Construye o reconstruye las imágenes. | `docker compose build api` |
| `docker compose ps` | Muestra el estado de los servicios. | `docker compose ps` |
| `docker compose logs` | Muestra los registros. | `docker compose logs api` |
| `docker compose logs -f` | Sigue los registros en tiempo real. | `docker compose logs -f api` |
| `docker compose down` | Detiene y elimina los contenedores y redes del proyecto. | `docker compose down` |

>Por defecto, `docker compose down` no elimina los volúmenes con nombre. Para borrarlos también, se puede usar `docker compose down -v`; hazlo con cuidado porque se eliminarán los datos guardados en ellos.