**Nginx** es un servidor web y servidor proxy de alto rendimiento. Se utiliza para:
- Servir páginas web y archivos estáticos.
- Actuar como **reverse proxy**.
- Distribuir tráfico entre varios servidores (**load balancing**).
- Terminar conexiones **TLS/HTTPS**.
- Gestionar varios sitios web desde un mismo servidor.
- Aplicar restricciones de acceso.
- Gestionar redirecciones.
- Servir como punto de entrada para aplicaciones Docker, Node.js, Python, Java, etc.

Una de sus características principales es que utiliza un modelo basado en eventos, lo que permite gestionar muchas conexiones simultáneas utilizando pocos recursos.
# Reverse Proxy
Un **reverse proxy** es un servidor que recibe las peticiones de los clientes y las reenvía a otro servidor interno.

Sin el reverse proxy el cliente conoce la IP del servidor. Cuando se usa uno este se pone en medio de la conexión de tal manera que el servidor y el proxy conocen la IP cliente pero el cliente no conoce la del servidor
# Instalación Debian / Ubuntu
```bash
# Actualizar los repositorios:
sudo apt update

# Instalar Nginx:
sudo apt install nginx

# Comprobar la versión:
nginx -v

# Comprobar el servicio:
systemctl status nginx

# Iniciar, Parar, Reiniciar y Recargar la Configuración:
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
sudo systemctl reload nginx

# Activar y Desactivar
sudo systemctl enable nginx
sudo systemctl disable nginx

# Comprobar configuración:
sudo nginx -t
sudo nginx -T

# Mostrar versión:
nginx -v
nginx -V
```
# Estructura de configuración y logs
- `/etc/nginx`: directorio de configuración de Nginx. En él se encuentran todos los archivos de configuración de Nginx.
- `/etc/nginx/nginx.conf`: archivo de configuración principal de Nginx. Esto se puede modificar para realizar cambios en la configuración general de Nginx.
- `/etc/nginx/sites-available/`: directorio en el que se pueden guardar bloques de servidor por sitio. Nginx no utilizará los archivos de configuración de este directorio a menos que estén vinculados al directorio `sites-enabled`. Normalmente, toda la configuración del bloque de servidor se realiza en este directorio y luego se habilita estableciendo un vínculo con el otro directorio.
- `/etc/nginx/sites-enabled/`: directorio en el que se almacenan los bloques de servidor habilitados por sitio. Normalmente, estos se crean estableciendo vínculos con los archivos de configuración del directorio `sites-available`.
	`sudo ln -s /etc/nginx/sites-available/miweb /etc/nginx/sites-enabled/miweb`
- `/etc/nginx/snippets`: este directorio contiene fragmentos de configuración que pueden incluirse en otras partes de la configuración de Nginx. Los segmentos de configuración potencialmente repetibles reúnen las condiciones para la conversión a fragmentos.
- `/var/log/nginx/access.log`: cada solicitud a su servidor web se registra en este archivo de registro, a menos que Nginx esté configurado para hacer algo diferente.
- `/var/log/nginx/error.log`: cualquier error de Nginx se asentará en este registro.
# Configuración
- **Bloque Server**: Define un servidor virtual. `server { ... }`
- **Listen**: Define el puerto y dirección donde escucha Nginx. Puede ser un puerto o dirección
	`listen 80;`
	`listen 443 ssl;`
	`listen 192.168.1.100:80;`
	`listen 127.0.0.1:8080;`
- **Server Name**: Define los nombres de dominio. `server_name domain.com`
- **Servir Archivos Estáticos**: `root /ruta/archivos` y `index /ruta/archivo.principal
- **Location**: Permite definir qué hacer con determinadas URL. `location /ruta { ... }
- **Proxy Pass**: Nginx actua como proxy inverso, envia el trafico a otra ip o puerto. 
	`proxy_pass http://IP:PUERTO;`
- **Redirecciones**: `return 301 https://ruta;`
- **Denegar Acceso**: `deny IP/RED/all`
- **Permitir Acceso**: `allow IP/RED/all`
### Headers Proxy Pass
```nginx
# Permiten que la aplicación conozca información sobre el cliente

location / {
    proxy_pass http://127.0.0.1:3000;
    
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
}
```
# TLS / HTTPS
Nginx puede encargarse de la conexión HTTPS y posteriormente comunicarse con la aplicación mediante HTTP.

```nginx
server {
    listen 443 ssl;
    server_name ejemplo.com;

    ssl_certificate /etc/ssl/certs/ejemplo.crt;
    ssl_certificate_key /etc/ssl/private/ejemplo.key;

    location / {
        proxy_pass http://127.0.0.1:3000;
    }
}
```
# Load balancing
Nginx también puede distribuir las peticiones entre varios servidores.
```nginx
upstream backend {
    server 127.0.0.1:3000;
    server 127.0.0.1:3001;
    server 127.0.0.1:3002;
}

server {
    listen 80;

    location / {
        proxy_pass http://backend;
    }
}
```
# Principales directivas

| Directiva             | Función                              |
| --------------------- | ------------------------------------ |
| `server`              | Define un servidor virtual           |
| `listen`              | Puerto/dirección donde escucha       |
| `server_name`         | Nombre del dominio                   |
| `location`            | Define el comportamiento de una URL  |
| `root`                | Directorio de archivos               |
| `index`               | Archivo inicial                      |
| `proxy_pass`          | Reenvía peticiones                   |
| `proxy_set_header`    | Modifica/envía headers al backend    |
| `return`              | Devuelve una respuesta o redirección |
| `rewrite`             | Reescribe URLs                       |
| `allow`               | Permite acceso                       |
| `deny`                | Deniega acceso                       |
| `auth_basic`          | Autenticación HTTP básica            |
| `ssl_certificate`     | Certificado TLS                      |
| `ssl_certificate_key` | Clave privada TLS                    |
| `expires`             | Control de caché                     |
| `gzip`                | Compresión                           |
| `access_log`          | Registro de peticiones               |
| `error_log`           | Registro de errores                  |
| `upstream`            | Define servidores backend            |
# Flujo recomendado al modificar Nginx
1. **Edita la Configuración**:
	`sudo nano /etc/nginx/sites-available/miweb`
	`sudo nano /etc/nginx/nginx.conf`	
2. **Comprobar sintaxis**: `sudo nginx -t`
3. **Recargar**:  `sudo systemctl reload nginx`
> No es necesario reiniciar Nginx para cambios normales de configuración.

