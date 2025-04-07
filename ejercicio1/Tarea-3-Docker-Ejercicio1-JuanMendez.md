# Tarea 3 Docker

## DAW Distancia - Despliegue de Aplicaciones Web

### Juan Méndez Fernández - 05 - 04 - 2025

[TOC]

___

 ## 1. Objetivo de la tarea

Se trata de adquirir habilidades en el manejo de Docker como tecnología basada en contenedores para gestionar despliegues de aplicaciones web.

Esta tarea está dividida en tres ejercicios para practicar desde la creación de contenedores en red, pasando por la gestión de estos, hasta crear una imagen propia personalizada y documentar el proceso para afianzar los conocimientos del curso.



___

## 2. Metodología práctica

Se resuelve esta práctica por medio de contenedores utilizando Docker Engine, Docker Desktop, Docker Compose y Dockerfile, además de GitHub como repositorio con una rama para cada ejercicio. Al final se incluye un video explicativo de parte de la práctica.



_____

## 3. Preparación del repositorio

En GitHub creo un nuevo repositorio público para la tarea, localizado en el siguiente enlace: 

https://github.com/Jumenfer92/dockerTarea

![image-20250407221059417](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\image-20250407221059417.png)

Clono el repositorio para trabajar en local.

![captura02](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\captura02.png)

Ya estoy en la rama main. Después voy creando una rama por cada ejercicio.

![captura03](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\captura03.png)

___



## 4. Ejercicio 1 - Contenedores en red y Docker Desktop

Teniendo instalado `Docker Desktop` y la extensión `Port Navigator`

Primero me cambio a la rama específica para el ejercicio 1 con `git branch` y `git switch`

```bash
git branch ejercicio1
git switch ejercicio1
```

![captura04](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\captura04.png)

**Creo la red bridge `redej1` desde Docker Desktop**

![captura05](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\captura05.png)

Datos de la nueva `red bridge`:

![captura06](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\captura06.png)



**4.1 CONTENEDOR CON `mariadb` **

Lo primero es ir al buscador de Docker Desktop y hacer un _PULL_ de la imagen de `mariadb` en el botón, y para crear el contenedor acto seguido pulso en _RUN_, ambos botones en la siguiente imagen.



![captura07](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\captura07.png)

Relleno los datos del nuevo contenedor según indica la documentación Docker para las variables de entorno, contraseña `root`, usuario `Juan`, base de datos `DAW`, y contraseña de esta `sasa`, quedando de la siguiente manera:



![captura08](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\captura08.png)

Una vez arrancado con esa configuración queda:

![captura09](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\captura09.png)

Creo un script SQL para crear la tabla `modulos`

```sql
CREATE TABLE modulos (
id INT AUTO_INCREMENT PRIMARY KEY,
nmodulo VARCHAR(20) NOT NULL
);

INSERT INTO modulos (nmodulo) 
VALUES	('dwes-servidor'),('daw-despliegue'),('diw-interfaces'),('dwec-cliente'),('badat-bases');
	
```



**4.2 CONTENEDOR CON `Adminer`**



En el buscador localizo e instalo `adminer`, y hago el respectivo `pull` de la imagen y creo el contenedor con `Run`.

![captura11](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\captura11.png)

Los dos contenedores en la misma red `redej1`

![image-20250407222519778](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\image-20250407222519778.png)

**CONECTARSE A LA BASE DE DATOS MARIADB MEDIANTE ADMINER**

Entro con localhost:8080, el puerto que le asigné al `Adminer`, para loguearme en el contenedor de `mariadb`.



![image-20250407221357073](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\image-20250407221357073.png)

![image-20250407221636143](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\image-20250407221636143.png)

Inserto el código SQL anterior.

![image-20250407221856585](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\image-20250407221856585.png)

Veo que se creó la tabla correctamente en el menú `registros`



![image-20250407222105092](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\image-20250407222105092.png)



**EXTENSIÓN RESOURCE USAGE**

Busco e instalo la extensión `resource usage`. Captura de la búsqueda sobre la extensión ejecutada.

![image-20250407223003600](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\image-20250407223003600.png)

Veamos un poco más de cerca los recursos:

![image-20250407223112193](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea 3 Docker.assets\image-20250407223112193.png)

Destruyo todo para finalizar el ejercicio:



![image-20250407223658167](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea-3-Docker-Ejercicio1-JuanMendez.assets\image-20250407223658167.png)

![image-20250407223707172](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea-3-Docker-Ejercicio1-JuanMendez.assets\image-20250407223707172.png)

![image-20250407223753301](C:\Users\jumen\Documents\GitHub\juan-hub\__year2\2_MARTES_DESPLIEGUE\TAREA 3 DOCKER\ejercicio1\Tarea-3-Docker-Ejercicio1-JuanMendez.assets\image-20250407223753301.png)





_____



