# Tarea 3 Docker - Ejercicio 3

## DAW Distancia - Despliegue de Aplicaciones Web

### Juan Méndez Fernández - 05 - 04 - 2025 - fichero ejercicio 3

[TOC]

___

 ## 1. Objetivo de la tarea

Se trata de adquirir habilidades en el manejo de Docker como tecnología basada en contenedores para gestionar despliegues de aplicaciones web.

Esta tarea está dividida en tres ejercicios para practicar desde la creación de contenedores en red, pasando por la gestión de estos, hasta crear una imagen propia personalizada y documentar el proceso para afianzar los conocimientos del curso.



___

## 2. Metodología práctica

Se resuelve esta práctica por medio de contenedores utilizando Docker Engine, Docker Desktop, Docker Compose y Dockerfile, además de GitHub como repositorio con una rama para cada ejercicio. Al final se incluye un video explicativo de parte de la práctica.



_____

## 3. Ejercicio 3 - Imagen con Dockerfile

**QUÉ ES DOCKERFILE**

Dockerfile es un fichero con instrucciones para construir una imagen personalizada, como si fuese una receta para crear paso a paso el entorno necesario.

El fichero es dockerfile sin extensión al final, y le sirve a Docker para instalar dependencias, copiar ficheros, configurar variables, y otras funciones. Vamos, que sirve para automatizar la creación de la imagen Docker y luego ya compartir la aplicación con otros o desplegarla en producción.



**IMAGEN CON DOCKERFILE PARA APLICACIÓN WEB**

Creo un sitio web sencillo para la tarea, con un Dockerfile dentro del directorio.

![image-20250418142205550](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418142205550.png)

Fichero `html`

![image-20250418142602259](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418142602259.png)

Fichero `css`

![image-20250418142616011](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418142616011.png)

Fichero `php` del enunciado

![image-20250418144427749](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418144427749.png)

`Dockerfile` donde se indica que la imagen es `php:7.4-apache`, que copia los ficheros del directorio a `/var/www/html` cambiando de paso los permisos.

![image-20250418144149158](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418144149158.png)

Para crear la imagen uso `docker build`  seguido de mi usuario, un directorio para el ejercicio3 y el punto de la ruta del mismo directorio donde tengo los ficheros.

```bash
docker build jumenfer92/ejercicio3 .
```



En la ruta donde los tengo:

![image-20250418144945373](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418144945373.png)

Build en proceso... ok.

![image-20250418145514574](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418145514574.png)

![image-20250418145521701](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418145521701.png)

Compruebo que funciona creando un contenedor con:

```bash
docker run -d -p 8000:80 jumenfer92/ejercicio3
```

![image-20250418145710829](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418145710829.png)

Web ejercicio 3 funcionando:

![image-20250418145829744](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418145829744.png)

Ahora subo la `imagen` a `DockerHub` logueándome y haciendo push

```bash
docker login
docker push jumenfer92/ejercicio3
```



![image-20250418150053008](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418150053008.png)

Ahora destruyo la imagen en el local:

```bash
docker rmi jumenfer92/ejercicio3
```

Primero el contenedor:

![image-20250418150437657](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418150437657.png)

Luego la imagen:

![image-20250418150513988](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418150513988.png)

Veo que ya no está ejercicio3 con `docker images`

![image-20250418150606290](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418150606290.png)

Hago el `pull` de la imagen para descargarla de mi cuenta de DockerHub y veo que se baja correctamente:

```bash
docker pull jumenfer92/ejercicio3
docker images
```

![image-20250418150737297](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418150737297.png)

Pruebo que está bien con un contenedor:

```bash
docker run -d -p 1111:80 jumenfer92/ejercicio3
```

![image-20250418150836950](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418150836950.png)

![image-20250418150950613](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418150950613.png)

Compruebo que se ve bien la fecha php:

![image-20250418151030182](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio3\Tarea3DockerEjercicio3JuanMendez.assets\image-20250418151030182.png)

-----

