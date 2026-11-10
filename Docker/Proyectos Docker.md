# LAMP en Docker
- Dockerfile
```
FROM php:8.3-apache
RUN docker-php-ext-install mysqli
```
- compose.yml
```
services:
  web:
    build: .
    networks:
      - backend-net
    ports:
      - "8080:80"
    restart: always
    volumes:
      - ./src:/var/www/html/:ro
    depends_on:
      - db
  db:
    image: mysql:8.4
    networks:
      - backend-net
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: app
      MYSQL_USER: app
      MYSQL_PASSWORD: app
    restart: always
    volumes:
      - ./mysql-data:/var/lib/mysql
volumes:
  mysql-data:
  src:
networks:
  backend-net:
```
- src/
	- index.php / index.html
	- otros archivos del codigo fuente
- mysql-data/