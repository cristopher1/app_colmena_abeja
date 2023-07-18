# [APP COLMENA ABEJA](#indice)

El presente proyecto fue desarrollado durante el ramo **trabajo de titulo**, para optar al titulo de **ingenierío civil informático** en la Universidad Técnica
Federico Santa María (UTFSM). Este sistema busca detectar la presencia o ausencia de abeja reina dentro de una colmena, mediante la extracción de características
de los zumbidos emitidos por ella, los cuales serán procesados por una red neuronal convolucional (CNN), para finalmente indicar si existe la presencia de abeja
reina dentro de dicha colmena.

### <a id="indice"></a>Índice

* <a id="introduccion"></a>[Introducción](#Introducción)
* <a id="prerrequisitos"></a> [Prerrequisitos](#Prerrequisitos)
* <a id="descarga"></a> [Descargar el repositorio](#Descargar-el-repositorio)
* <a id="entorno"></a>[Variables de entorno](#Variables-de-entorno)
  * <a id="entorno-frontend"></a>[Para el FRONTEND](#Para-el-FRONTEND)
  * <a id="entorno-api"></a>[Para la API](#Para-la-API)
* <a id="run"></a>[Ejecutar la aplicación](#Ejecutar-la-aplicación)

## <a id="Introducción"></a> [Introducción](#introduccion)

El presente repositorio tiene como finalidad almacenar las herramientas que permiten automzatizar el despliegue del sistema. El sistema se divide en un frontend 
y una API (almacenadas en repositorios independientes) y unidas en un tercer repositorio (este repositorio) mediante git-submodule, que además de juntar los dos 
repositorios independientes, también contiene un archivo docker-compose.yml y .env.example (utilizado para generar el archivo .env) que permitirán ejecutar el 
sistema de forma automática.

## <a id="Prerrequisitos"></a> [Prerrequisitos](#prerrequisitos)

El sistema ha sido probado en SO Windows 11.

* Docker Desktop con Servidor WSL 2. Ver documentación sobre [Docker Desktop para Windows](https://docs.docker.com/desktop/install/windows-install/)

## <a id="Descargar-el-repositorio"></a> [Descargar el repositorio](#descarga)

Para descargar el repositorio use:

```console
git clone --recurse-submodules git@github.com:cristopher1/app_colmena_abeja.git
```

## <a id="Variables-de-entorno"></a> [Variables de entorno](#entorno)

La información de las variables de entorno se encuentra dentro del archivo .env.example, este archivo tiene 8 variables, que son usadas dentro del archivo
docker-compose.yml para establecer la forma en que se va a desplegar el sistema. A continuación se muestra su estructura.

https://github.com/cristopher1/app_colmena_abeja/blob/9bb1a74002ca747bb5d142e7fb5a44329cb35d2c/docker-compose.yml#L1-L21

A continuación se muestran las variables de entorno usadas en el archivo docker-compose.yml presentado anteriormente.

### <a id="Para-el-FRONTEND"></a> [Para el FRONTEND](#entorno-frontend)

https://github.com/cristopher1/app_colmena_abeja/blob/23bea7412bc6b070c52e0b026cf7102eb3c47060/.env.example#L7-L22

* `FRONTEND_PROJECT_DIRECTORY`: Nombre de la carpeta que contiene el FRONTEND y en su raíz esta el
archivo Dockerfile. Debería llamarse **frontend_app_colmena_abeja**

* `FRONTEND_STAGE`: Modo en el que se desplegará el FRONTEND. development o production

* `FRONTEND_HOST_PORT`: Puerto en el HOST, donde el FRONTEND escucha peticiones

* `FRONTEND_CONTAINER_PORT`: Puerto en el contenedor, donde el FRONTEND escucha peticiones

### <a id="Para-la-API"></a> [Para la API](#entorno-api)

https://github.com/cristopher1/app_colmena_abeja/blob/23bea7412bc6b070c52e0b026cf7102eb3c47060/.env.example#L24-L39

* `API_PROJECT_DIRECTORY`: Nombre de la carpeta que contiene la API y en su raíz esta el
archivo Dockerfile. Debería llamarse **api_colmena_abeja**

* `API_STAGE`: Modo en el que se desplegará la API. development o production

* `API_HOST_PORT`: Puerto en el HOST, donde la API escucha peticiones

* `API_CONTAINER_PORT`: Puerto en el contenedor, donde la API escucha peticiones

## <a id="Ejecutar-la-aplicación"></a> [Ejecutar la aplicación](#run)

Para ejecutar la aplicación siga los siguientes pasos.

* **Nota: Los archivos Dockerfile presentes en el repositorio api_colmena_abeja y frontend_app_colmena_abeja utilizan**
**Multi-stage, por lo que no debe olvidar habilitar el docker BuildKit al momento de ejecutar la aplicación.**

* **Nota: A partir de la versión 23.0 de Docker Desktop y Docker Engine se usa de forma predeterminada el BuildKit**
**por lo que no es necesario habilitarlo de forma manual.**

1. Ingrese a la carpeta app_colmena_abeja (desde la terminal o interfaz gráfica)
2. Cree un archivo llamado .env (en la misma carpeta donde esta el archivo .env.example)  
3. Copie el contenido del archivo .env.example a .env
4. Si gusta, modifique los valores del archivo .env
5. Repita el paso 2, 3 y 4 en api_colmena_abeja y frontend_app_colmena_abeja
6. Abra una terminal e ingrese a la carpeta app_colmena_abeja
7. Ejecute el comando `docker-compose up --build`

**Nota: En modo producción no exponga directamente el contenedor api_colmena_abeja, en su lugar use un servidor de producción como nginx para redirigir**
**las peticiones web al contenedor api_colmena_abeja.**

Una vez completados los pasos, el sistema debería estar ejecutandose en `http://localhost:${FROTEND_HOST_PORT}`
