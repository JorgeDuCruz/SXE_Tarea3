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
creados, en este caso el nombre que se le asignó a nuestro contenedor fue **modest_merkle**.

## 3º Parte
![3º_CrearContenedorNombre.png](SXE_Fotos_03/3º_CrearContenedorNombre.png)

Para crear un contenedor con nombre podemos usar el mismo comando anterior pero añadiendo la opción `--name <nombre>`
antes de la imagen para indicarle un nombre específico. 

En este caso, alpine tiene un problema y es que es muy probable
que si creas el contenedor, cuando lo intentes ejecutar se cierre automáticamente porque el proceso principal acaba muy rápido,
asi que aquí también tendremos que agregar algún elemento que retrase su cierre, en mi caso `-it`.

Y como se puede ver ahora hay un contenedor creado con el nombre que pusimos.

![4º_Acceder.png](SXE_Fotos_03/4º_Acceder.png)

Si hicimos todo bien, para acceder a él solo tendremos que usar `docker start <nombre-contenedor>` para que se active, como se puede ver en el **STATUS UP**. Una vez activo el contenedor
podremos usar `exec -it <nombre-contenedor> sh` entraremos directamente en la terminal de alpine.