# Comandos
- `FROM <image>`: Indica la **imagen base**
- `WORKDIR <dir>`: Define el directorio de trabajo dentro del contenedor
- `COPY <host_file> <container_dir>`: Copia archivos del host al contenedor
- `RUN <command>`: Ejecuta comandos en el proceso de _build_ (instalaciones, configs…)
- `ENV <name>=<value>`: Define variables de entorno
- `ARG <name>=<value>`: Permite pasar valores en tiempo de build
- `EXPOSE <port>`: Declara puertos que el contenedor usará
- `CMD ["<command>", "<arg1>", "<...>"]`: Define el comando por defecto al ejecutar el contenedor
- `ENTRYPOINT ["command"]`: Define el proceso principal (no se sobreescribe tan fácilmente).
# Buenas Prácticas en Dockerfile
- **Imagen base pequeña:** usar imágenes `slim`, `alpine` o minimalistas cuando sea posible. Ej: `FROM python:3.13-slim`.
- **Fijar versiones:** evitar `latest` para conseguir builds reproducibles. Ej: `FROM node:22.14-alpine`.
- **`.dockerignore`:** excluir archivos innecesarios del contexto de build. Ej: `.git`, `.env`, `node_modules`, `*.log`.
- **Aprovechar la caché:** copiar primero los archivos que cambian menos. 
	- Ej: `COPY package*.json ./` → `RUN npm ci` → `COPY . .`.
- **No incluir secretos:** nunca guardar contraseñas, tokens o API keys en la imagen. Ej: usar Docker Secrets o variables de entorno en runtime.
- **Usuario no-root:** ejecutar la aplicación con un usuario sin privilegios. Ej: `USER appuser`.
- **Formato exec:** usar arrays JSON en `CMD` y `ENTRYPOINT` para gestionar correctamente señales. Ej: `CMD ["python", "app.py"]`.
- **Instalar solo lo necesario:** evitar paquetes y herramientas que no se utilicen en producción. Ej: `apt-get install --no-install-recommends`.
- **Limpiar paquetes temporales:** eliminar cachés y listas de paquetes después de instalar. Ej: `rm -rf /var/lib/apt/lists/*`.
- **Reducir capas innecesarias:** agrupar operaciones relacionadas cuando sea beneficioso. 
	- Ej: `RUN apt-get update && apt-get install ... && rm -rf ...`.
- **`EXPOSE`:** documentar el puerto que utiliza la aplicación. Ej: `EXPOSE 8080`.
- **`HEALTHCHECK`:** definir una comprobación de salud cuando sea útil. Ej: `HEALTHCHECK CMD curl -f http://localhost:8080/health`.
- **Multistage builds:** separar la compilación de la ejecución para que la imagen final no contenga herramientas de desarrollo. Ej: `FROM node:22 AS builder` → `FROM nginx:alpine` → `COPY --from=builder ...`.
- **Copiar solo artefactos necesarios:** en multistage, pasar al runtime únicamente el resultado del build. 
	- Ej: `COPY --from=builder /app/dist /usr/share/nginx/html`.
- **Build reproducible:** fijar versiones de imágenes y dependencias. Ej: especificar versiones en `requirements.txt`, `package-lock.json`, `go.mod`, etc.
- **Un proceso principal por contenedor:** diseñar el contenedor alrededor de una responsabilidad principal. Ej: un contenedor para API y otro para PostgreSQL.
- **Separar desarrollo y producción:** no incluir herramientas de desarrollo en la imagen final. Ej: usar un stage `development` y otro `production`.
- **No ejecutar como root:** especialmente importante en producción. Ej: crear `appuser` y terminar con `USER appuser`.
- **Usar variables de entorno para configuración:** evitar valores específicos del entorno en el Dockerfile. Ej: `ENV PORT=8080`.
- **Mantener el Dockerfile legible:** ordenar las instrucciones de forma lógica y evitar comandos excesivamente complejos. 
	- Ej: `FROM` → dependencias → código → build → usuario → `CMD`.
# Multistage
Un **multistage build** permite utilizar varias etapas (`stages`) dentro del mismo `Dockerfile`. La idea principal es separar el **entorno necesario para construir la aplicación** del **entorno necesario para ejecutarla**.
Por ejemplo, para compilar una aplicación puedes necesitar: **Compilador, SDK, Dependencias de desarrollo, Código fuente y Herramientas de build**.

Pero para ejecutar la aplicación quizá solo necesitas: **El binario compilado, las librerías necesarias y un runtime mínimo.

Con multistage, Docker utiliza una imagen para construir y otra para ejecutar.
#### Sintaxis Básica
```dockerfile
FROM imagen AS builder

# construir aplicación

FROM imagen-runtime

COPY --from=builder /ruta/artefacto /ruta/destino
```

El primer `FROM` crea el stage de construcción y `AS builder` le asigna un nombre. Después, `COPY --from=builder` permite copiar archivos desde ese stage al stage final.
#### Ejemplo 1: Frontend React / Vite + Nginx
Un frontend React normalmente necesita Node.js para hacer el build, pero **no necesita Node.js para servir los archivos generados**. La imagen final **no contiene Node.js, npm ni el código fuente**
```dockerfile
# Stage 1: build
# node:22-alpine contiene Node.js y npm.
FROM node:22-alpine AS builder 

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .

# npm run build genera dist/.
RUN npm run build

# Stage 2: production
# El segundo stage utiliza Nginx
FROM nginx:alpine

# Solo se copia dist/
COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 80
```
#### Ejemplo 2: Go
Go es un caso especialmente bueno porque normalmente puedes generar un binario autocontenido.
**Ventaja:** una aplicación Go que inicialmente necesitaría una imagen con todo el SDK de Go puede terminar ejecutándose con una imagen mucho más pequeña.
```dockerfile
# Stage 1: build
FROM golang:1.25-alpine AS builder

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . .

RUN go build -o server .

# Stage 2: runtime
FROM alpine:3.22

WORKDIR /app

COPY --from=builder /app/server .

EXPOSE 8080

CMD ["./server"]
```
#### Ejemplo 3: Java + Maven + Spring Boot
En Java podemos utilizar Maven y el JDK completo durante el build y después utilizar solamente un runtime para ejecutar la aplicación. Esto es especialmente útil en aplicaciones **Spring Boot**.
```dockerfile
# Stage 1: build
FROM maven:3.9-eclipse-temurin-21 AS builder

WORKDIR /app

COPY pom.xml .
RUN mvn dependency:go-offline

COPY src ./src

RUN mvn clean package -DskipTests

# Stage 2: runtime
FROM eclipse-temurin:21-jre

WORKDIR /app

COPY --from=builder /app/target/*.jar app.jar

EXPOSE 8080

CMD ["java", "-jar", "app.jar"]
```
#### Ejemplo 4: C/C++
También es muy habitual en aplicaciones C/C++.
```dockerfile
# Stage 1: build
FROM gcc:15 AS builder

WORKDIR /app

COPY . .

RUN g++ -O2 -o app main.cpp

# Stage 2: runtime
FROM debian:bookworm-slim

WORKDIR /app

COPY --from=builder /app/app .

CMD ["./app"]
```
# Cuándo usarlo
- **React/Vite/Angular:** `Node.js → Nginx`.
- **Go:** `Go SDK → imagen runtime mínima`.
- **Java/Spring Boot:** `Maven + JDK → JRE`.
- **C/C++:** `GCC/Clang → runtime`.
- **Rust:** `Rust + Cargo → runtime`.
- **.NET:** `.NET SDK → ASP.NET Runtime`.