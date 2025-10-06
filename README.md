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

Para crear un contenedor con nombre podemos usar el mismo comando anterior pero añadiendo la opción de `--name <nombre>`
antes de la imagen para indicarle un nombre específico. 

En este caso, alpine tiene un problema y es que es muy probable
que si creas el contenedor, cuando lo intentes ejecutar se cierre automáticamente porque el proceso principal acaba muy rápido,
asi que aquí también tendremos que agregar algún elemento que retrase su cierre, en mi caso `-it`.

Y como se puede ver ahora hay un contenedor creado con el nombre que pusimos.

![4º_Acceder.png](SXE_Fotos_03/4º_Acceder.png)

Si hicimos todo bien, para acceder a él solo tendremos que usar `docker start <nombre-contenedor>` para que se active, como se puede ver en el **STATUS UP**. Una vez activo el contenedor
podremos usar `exec -it <nombre-contenedor> sh` entraremos directamente en la terminal de alpine.

## 4º Parte
![5º_IpYPing.png](SXE_Fotos_03/5º_IpYPing.png)

Dentro de la terminal podemos usar `ip a` para ver la ip del contenedor, en este caso *172.17.0.2* y también
podemos hacer ping con google con `ping google.com`.

## 5º Parte

![6ºCrear_Y_Aceder_Contenedor2.png](SXE_Fotos_03/6ºCrear_Y_Aceder_Contenedor2.png)

De la misma manera que creamos el anterior contenedor crearemos otro nuevo y lo ejecutaremos siguiendo los pasos anteriores.

![7ºIP2_Y_Ping2->1.png](SXE_Fotos_03/7ºIP2_Y_Ping2_1.png)

Una vez en la terminal podemos buscar la IP de este contenedor y hacer ping entre los contenedores al saber la IP del anterior
con `ping 172.17.0.2` y veremos que efectivamente se pueden conectar los dos contenedores.

## 6º Parte

![8ºSalirTerminalYEstado.png](SXE_Fotos_03/8ºSalirTerminalYEstado.png)

Para salir de la terminal simplemente podemos escribir `exit` en la terminal de alpine y nos dejará salir.

Si comprobamos ahora el estado de los contenedores podremos ver que ninguno de ellos se detuvo.

## 7º Parte

![9ºEspacioEnMemoria.png](SXE_Fotos_03/9ºEspacioEnMemoria.png)

Con el comando `docker system df` podremos ver la memoria en el disco duro que usa docker.
Como previamente ya había hecho cosas antes en docker puede que tenga más memoria usada de la que se usaría para estos pasos.

## 8º Parte

![11ºComandoRAM.png](SXE_Fotos_03/11ºComandoRAM.png)

Con el comando `docker stats` podemos ver, entre otras cosas, la memoria RAM que usa docker.

![10ºRam.png](SXE_Fotos_03/10ºRam.png)

Ahora podemos ver que cada uno de los contenedores ocupa aproximadamente unos 700 KiB de memoria RAM.
