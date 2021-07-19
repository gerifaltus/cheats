# Docker
## Image
Comandos para administrar imagenes de docker
* **docker image ls**
  * Muestra todas las imágenes guardadas dentro del docker engine.
* **docker pull nombre_imagen** 
  * sirve para descargar una imagen desde docker hub
* docker image rm nombre-imagen | id-imagen
  * Elimina la imagen seleccionada junto con sus dependencias, si la imagen fue descargada de docker hub, se podrá descargar de nuevo.

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
* docker logs nombre-contenedor | id-contenedor
  * Muestra el log de arranque del contenedor, para saber si todo se ha ejecutado correctamente al momento de levantar el contenedor o si tiene errores y corregirlos.
* docker stop nombre-contenedor | id-contenedor
  * Sirve para detener un contenedor, cuando se use nuevamente **docker ps** no aparecerá el contenedor detenido, pero si se usa **docker ps -a** apareceran todos los contenedores incluyendo el que acaba de ser detenido con el timestamp de hace cuanto tiempo fue su ultima ejecución.
* docker rm nombre-contenedor | id-contenedor
  * Sirve para eliminar un contenedor, al eliminar ya no aparecerá cuando se ejecute **docker ps -a**
