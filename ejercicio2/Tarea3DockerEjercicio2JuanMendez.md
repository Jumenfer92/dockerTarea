# Tarea 3 Docker

## DAW Distancia - Despliegue de Aplicaciones Web

### Juan Méndez Fernández - 05 - 04 - 2025 - fichero ejercicio 2

[TOC]

___

 ## 1. Objetivo de la tarea

Se trata de adquirir habilidades en el manejo de Docker como tecnología basada en contenedores para gestionar despliegues de aplicaciones web.

Esta tarea está dividida en tres ejercicios para practicar desde la creación de contenedores en red, pasando por la gestión de estos, hasta crear una imagen propia personalizada y documentar el proceso para afianzar los conocimientos del curso.



___

## 2. Metodología práctica

Se resuelve esta práctica por medio de contenedores utilizando Docker Engine, Docker Desktop, Docker Compose y Dockerfile, además de GitHub como repositorio con una rama para cada ejercicio. Al final se incluye un video explicativo de parte de la práctica.



_____

## 3. Ejercicio 2 - Docker Compose

**QUÉ ES COMPOSE**

Es una herramienta de Docker que te permite **definir y ejecutar múltiples contenedores** como si fueran uno solo, usando un archivo llamado `docker-compose.yml`

Es decir que si tengo una aplicación web que necesita un servidor como puede ser `nginx`, una base de datos como `mariadb` y otras cosas, en vez de levantar todo uno por uno, con Compose puedo levantar todo con una sola instrucción como:

```bash
docker-compose up
```



**QUÉ ES FILEBROWSER**

Es una app web que corre en un contenedor y te da una **interfaz gráfica para explorar, subir, mover, renombrar o eliminar archivos** del servidor directamente desde el navegador.

Permite por ejemplo ver los archivos al estilo explorador de windows pero por web. Acciones como subir y descargar archivos, crear carpetas, editar archivos de texto, compartir enlaces, proteger con contraseñas... de forma super cómoda según he descubierto en esta práctica.



**DESARROLLO DEL EJERCICIO 2**

Utilizo el siguiente fichero .yaml

```
version: '3.8'

services:
  filebrowser:
    image: hurlenko/filebrowser
    container_name: filebrowser
    ports:
      - "8080:8080"
    volumes:
      - ./datos:/data
      - ./config:/config
    environment:
      - FB_BASEURL=/filebrowser
    restart: unless-stopped

```

![image-20250408172429084](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio2\Tarea3DockerEjercicio2JuanMendez.assets\image-20250408172429084.png)

**FILE BROWSER **

Despliego en el directorio del ejercicio 2 donde tengo el fichero .yaml mediante

```
`docker compose up -d
```

![image-20250416203506719](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio2\Tarea3DockerEjercicio2JuanMendez.assets\image-20250416203506719.png)

Después pruebo desde el navegador a entrar en la aplicación mediante:

```
http://localhost:8080
```

Efectivamente puedo entrar:

![image-20250416203743591](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio2\Tarea3DockerEjercicio2JuanMendez.assets\image-20250416203743591.png)

Una vez logueado creo algún directorio y fichero para ver que funciona correctamente.

![image-20250416203916068](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio2\Tarea3DockerEjercicio2JuanMendez.assets\image-20250416203916068.png)

Creo también el usuario juan en el menú de ajustes.

![image-20250416204024589](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio2\Tarea3DockerEjercicio2JuanMendez.assets\image-20250416204024589.png)

Edito uno de los ficheros y me lo descargo al PC principal.

![image-20250416204200963](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio2\Tarea3DockerEjercicio2JuanMendez.assets\image-20250416204200963.png)

![image-20250416204228357](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio2\Tarea3DockerEjercicio2JuanMendez.assets\image-20250416204228357.png)

En conclusión se trata de una herramienta facilísima de desplegar y muy cómoda de usar.



_____





