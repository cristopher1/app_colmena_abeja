# [APP COLMENA ABEJA](#indice)

El presente proyecto fue desarrollado durante el ramo **trabajo de titulo**, para optar al titulo de **ingenierío civil informático** en la Universidad Técnica Federico Santa María (UTFSM).

### <a id="indice"></a>Índice

* <a id="introduccion"></a>[Introducción](#Introducción)
* <a id="prerrequisitos"></a> [Prerrequisitos](#Prerrequisitos)
* <a id="descarga"></a> [Descargar el repositorio](#Descargar-el-repositorio)
* <a id="entorno"></a>[Variables de entorno](#Variables-de-entorno)
  * <a id="entorno-frontend"></a>[Para el FRONTEND](#Para-el-FRONTEND)
  * <a id="entorno-api"></a>[Para la API](#Para-la-API)
* <a id="run"></a>[Ejecutar la aplicación](#Ejecutar-la-aplicación)

## [Introducción](#introduccion)

El presente repositorio tiene como finalidad almacenar las herramientas que permiten automzatizar el
despliegue del sistema. El sistema se divide en un frontend y una API (almacenadas en repositorios independientes)
y unidas en un tercer repositorio (este repositorio) mediante gitsubmodule, que además de juntar los dos
repositorios independientes, también contiene un archivo docker-compose.yml y .env.example (utilizado
para generar el archivo .env) que permitirán ejecutar el sistema de forma automática.

## [Prerrequisitos](#prerrequisitos)

El sistema ha sido probado en SO Windows 11.

* Docker Desktop con Servidor WSL 2. Ver documentación sobre [Docker Desktop para Windows](https://docs.docker.com/desktop/install/windows-install/)

## [Descargar el repositorio](#descarga)

Para descargar el repositorio use:

```python
git clone --recurse-submodules git@github.com:cristopher1/app_colmena_abeja.git
```

## [Variables de entorno](#entorno)

La información de las variables de entorno se encuentra dentro del archivo .env.example, este archivo
tiene 8 variables.

### [Para el FRONTEND](#entorno-frontend)

* `FRONTEND_PROJECT_DIRECTORY`: Nombre de la carpeta que contiene el FRONTEND y en su raíz esta el
archivo Dockerfile. Debería llamarse **frontend_app_colmena_abeja**

* `FRONTEND_STAGE`: Modo en el que se desplegará el FRONTEND. development o production

* `FRONTEND_HOST_PORT`: Puerto en el HOST, donde el FRONTEND escucha peticiones

* `FRONTEND_CONTAINER_PORT`: Puerto en el contenedor, donde el FRONTEND escucha peticiones

### [Para la API](#entorno-api)

* `API_PROJECT_DIRECTORY`: Nombre de la carpeta que contiene la API y en su raíz esta el
archivo Dockerfile. Debería llamarse **api_colmena_abeja**

* `API_STAGE`: Modo en el que se desplegará la API. development o production

* `API_HOST_PORT`: Puerto en el HOST, donde la API escucha peticiones

* `API_CONTAINER_PORT`: Puerto en el contenedor, donde la API escucha peticiones

## [Ejecutar la aplicación](#run)

Para ejecutar la aplicación siga los siguientes pasos.

* **Nota: Los archivos Dockerfile presentes en el repositorio api_colmena_abeja y frontend_app_colmena_abeja utilizan**
**Multi-stage, por lo que no debe olvidar habilitar el docker BuildKit al momento de ejecutar la aplicación.**

* **Nota: A partir de la versión 23.0 de Docker Desktop y Docker Engine se usa de forma predeterminada el BuildKit**
**Por lo que no es necesario habilitarlo de forma manual.**

1. Ingrese a la carpeta app_colmena_abeja.
2. Cree un archivo llamado .env
3. Copie el contenido del archivo .env.example a .env
4. Si gusta, modifique los valores del archivo .env
5. Repita el paso 2, 3 y 4 en api_colmena_abeja y frontend_app_colmena_abeja
6. Abra una terminal
7. Desde la terminal, ingrese a la carpeta app_colmena_abeja
8. Ejecute el comando `docker-compose up --build`

Una vez completados los pasos, el sistema debería estar ejecutandose en `http://localhost:${FROTEND_HOST_PORT}`
