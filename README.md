# SXE_Tarea3

## 1º Parte

![1º.png](SXE_Fotos_03/1º.png)

Para descargar una imagen sin hacer nada más podemos usar el comando `docker pull <Imagen>`
sustituyendo la imagen por el nombre de la imagen que queremos, en este caso, alpine.

Para comprobar que se descargó correctamente con `docker image ls` muestra todas las imágenes descargadas.

## 2º Parte

![2ºA.png](SXE_Fotos_03/2ºA.png)

Para crear un contenedor sin ejecutarlo se usa el comando `docker create <Imagen>`, en este caso alpine.
Para comprobar el nombre se puede usar el comando `docker ps -a` para mostrar todos los contenedores
creados, en este caso el nombre que se le asigno a nuestro contenedor fue **modest_merkle**.

