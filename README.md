# SXE_Tarea3: Uso Básico de Docker

---

## 1. Descargar una Imagen

![1º.png](SXE_Fotos_03/1º.png)

Para descargar una imagen sin hacer nada más, podemos usar el siguiente comando:

```bash
docker pull alpine
```

Esto descargará la imagen `alpine` desde Docker Hub.

Una vez descargada, para comprobar que la imagen se encuentra en el sistema, se puede usar el comando:

```bash
docker image ls
```

Este comando mostrará todas las imágenes descargadas localmente.

---

## 2. Crear un Contenedor sin Ejecutarlo

![2ºA.png](SXE_Fotos_03/2ºA.png)

Para crear un contenedor a partir de la imagen descargada, sin ejecutarlo, usamos:

```bash
docker create alpine
```

Este comando solo crea el contenedor, pero no lo inicia.

Para comprobar que se ha creado correctamente, podemos usar:

```bash
docker ps -a
```

Este comando lista todos los contenedores, incluidos los que están detenidos.  
En este caso, Docker asignó automáticamente el nombre **modest_merkle** al contenedor creado.

---

## 3. Crear un Contenedor con Nombre

![3º_CrearContenedorNombre.png](SXE_Fotos_03/3º_CrearContenedorNombre.png)

Para crear un contenedor con un nombre específico, utilizamos el mismo comando que antes pero añadiendo la opción `--name`:

```bash
docker create --name dam_alp1 -it alpine
```

> Alpine no ejecuta ningún proceso por defecto. Por lo tanto, al iniciar un contenedor basado en esta imagen, se cerrará automáticamente si no se le indica que mantenga la terminal abierta.  
> Por eso, también se añaden las opciones `-it` al momento de crear el contenedor, lo cual permite una sesión interactiva y evita que se cierre inmediatamente.

Después de ejecutar el comando, el contenedor quedará creado con el nombre que se haya especificado.

---

### Iniciar y Acceder al Contenedor

![4º_Acceder.png](SXE_Fotos_03/4º_Acceder.png)

Para iniciar el contenedor creado anteriormente y acceder a su terminal:

1. Iniciar el contenedor con el comando:

```bash
docker start dam_alp1
```

Si el contenedor se ha iniciado correctamente, en la columna STATUS aparecerá **UP**.

2. Acceder a su terminal utilizando:

```bash
docker exec -it dam_alp1 sh
```

Esto abrirá una terminal interactiva dentro del contenedor `alpine`.

---

## 4. Ver la IP del Contenedor y Hacer Ping

![5º_IpYPing.png](SXE_Fotos_03/5º_IpYPing.png)

Una vez dentro del contenedor, se pueden realizar dos acciones:

1. Ver la IP del contenedor con el comando:

```bash
ip a
```

En este caso, se muestra la IP `172.17.0.2`.

2. Comprobar la conectividad a internet haciendo ping a Google:

```bash
ping google.com
```

Esto permite verificar que el contenedor tiene acceso a la red externa.

---

## 5. Crear y Acceder a un Segundo Contenedor

![6ºCrear_Y_Aceder_Contenedor2.png](SXE_Fotos_03/6ºCrear_Y_Aceder_Contenedor2.png)

Se repite el proceso anterior para crear y acceder a un segundo contenedor `alpine`.

1. Crear el contenedor con nombre y opciones interactivas:

```bash
docker create --name dam_alp2 -it alpine
```

2. Iniciarlo y acceder a su terminal con:

```bash
docker start dam_alp2
docker exec -it dam_alp2 sh
```

---

### Ver la IP del Segundo Contenedor y Hacer Ping al Primero

![7ºIP2_Y_Ping2->1.png](SXE_Fotos_03/7ºIP2_Y_Ping2_1.png)

Desde la terminal del segundo contenedor:

1. Ver su dirección IP con:

```bash
ip a
```

2. Usar la IP obtenida anteriormente del primer contenedor para hacer ping:

```bash
ping 172.17.0.2
```

Esto demuestra que los dos contenedores pueden conectarse entre sí a través de la red de Docker.

---

## 6. Salir del Contenedor y Verificar su Estado

![8ºSalirTerminalYEstado.png](SXE_Fotos_03/8ºSalirTerminalYEstado.png)

Para salir de la terminal del contenedor:

```bash
exit
```

Esto nos devuelve al sistema anfitrión.

Luego, se puede comprobar el estado de los contenedores con:

```bash
docker ps -a
```

En este caso, aunque se haya salido de la terminal, los contenedores siguen en ejecución si no se han detenido manualmente.

---

## 7. Ver el Espacio Ocupado por Docker

![9ºEspacioEnMemoria.png](SXE_Fotos_03/9ºEspacioEnMemoria.png)

Con el siguiente comando se puede ver cuánto espacio ocupa Docker en el disco duro:

```bash
docker system df
```

El resultado muestra el espacio utilizado por imágenes, contenedores, volúmenes y cachés.

Nota: Ya se han hecho otras tareas con Docker anteriormente por lo que la memoria usada es mayor que la esperada solo por estos pasos.

---

## 8. Ver el Uso de Memoria RAM

![11ºComandoRAM.png](SXE_Fotos_03/11ºComandoRAM.png)

Para ver el uso de recursos (como CPU y memoria RAM) en tiempo real por cada contenedor, se utiliza:

```bash
docker stats
```

![10ºRam.png](SXE_Fotos_03/10ºRam.png)

En este caso, se observa que cada contenedor ocupa aproximadamente **700 KiB de RAM**.
