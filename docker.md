# Docker
## Image
Comandos para administrar imagenes de docker
* **docker image ls**
  * Muestra todas las imágenes guardadas dentro del docker engine.
* **docker pull nombre_imagen** 
  * sirve para descargar una imagen desde docker hub

## Contenedor
Comandos para administrar contenedores de docker
* docker ps
  * Muestra los contenedores que están levantados y funcionando.
* docker ps -a
  * Muestra todos los contenedores tanto los que estan corriendo como los que no.
* docker container ls
  * Hace lo mismo que **docker ps | docker ps -a**
* **docker run -p 1234:4321 --name nombre-contenedor imagen-contenedor**
  * Crea y ejecuta un contenedor en base a una imagen de docker:
    * Etiqueta -p 1234:4321: es para indicar el puerto del host (puerto 1234, equipo donde se encuentra docker instalado) que estará asociado al puerto del contenedor (puerto 4321, el contenedor por sí mismo).
    * Etiqueta -name nombre-contenedor: nombre del contenedor que aparecerá cuando sea listado con **docker container ls | docler ps**
    * imagen-contenedor: nombre de la imagen desde la cual se creará el contenedor.
* docker start nombre-contenedor | id-contenedor
  * Este comando sirve para inicializar un contenedor que ya ha sido creado con el comando **docker run** y se encuentra listado en el docker engine
