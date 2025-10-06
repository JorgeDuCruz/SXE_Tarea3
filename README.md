# SXE_Tarea3: Uso Básico de Docker

---

## 1. Descargar una Imagen

![1º.png](SXE_Fotos_03/1º.png)

Para descargar una imagen sin ejecutarla:

```bash
docker pull <imagen>
```

En este caso:

```bash
docker pull alpine
```

Para comprobar que se descargó correctamente:

```bash
docker image ls
```

---

## 2. Crear un Contenedor sin Ejecutarlo

![2ºA.png](SXE_Fotos_03/2ºA.png)

Para crear un contenedor sin ejecutarlo:

```bash
docker create alpine
```

Ver los contenedores creados:

```bash
docker ps -a
```

El nombre asignado automáticamente en este caso fue: **modest_merkle**.

---

## 3. Crear un Contenedor con Nombre

![3º_CrearContenedorNombre.png](SXE_Fotos_03/3º_CrearContenedorNombre.png)

Para crear un contenedor con un nombre personalizado:

```bash
docker create --name <nombre> -it alpine
```

Nota: Alpine puede cerrarse automáticamente al ejecutarse por no tener un proceso en segundo plano. Por eso se recomienda usar la opción `-it` para interactuar con el contenedor.

---

### Iniciar y Acceder al Contenedor

![4º_Acceder.png](SXE_Fotos_03/4º_Acceder.png)

1. Iniciar el contenedor:

```bash
docker start <nombre-contenedor>
```

2. Acceder a la terminal del contenedor:

```bash
docker exec -it <nombre-contenedor> sh
```

---

## 4. Comprobar Conectividad e IP

![5º_IpYPing.png](SXE_Fotos_03/5º_IpYPing.png)

Dentro del contenedor:

- Ver la IP del contenedor:

```bash
ip a
```

- Probar conectividad con Google:

```bash
ping google.com
```

---

## 5. Crear un Segundo Contenedor y Ver Conectividad

![6ºCrear_Y_Aceder_Contenedor2.png](SXE_Fotos_03/6ºCrear_Y_Aceder_Contenedor2.png)

Sigue los mismos pasos anteriores para crear y acceder a un segundo contenedor.

---

### Comprobar Conectividad entre Contenedores

![7ºIP2_Y_Ping2->1.png](SXE_Fotos_03/7ºIP2_Y_Ping2_1.png)

Desde el segundo contenedor, hacer ping al primero con su IP:

```bash
ping 172.17.0.2
```

Esto demuestra que los contenedores pueden comunicarse entre sí.

---

## 6. Salir del Contenedor y Ver Estado

![8ºSalirTerminalYEstado.png](SXE_Fotos_03/8ºSalirTerminalYEstado.png)

Salir del contenedor:

```bash
exit
```

Comprobar el estado de los contenedores:

```bash
docker ps -a
```

Los contenedores siguen activos.

---

## 7. Ver Espacio en Disco Usado por Docker

![9ºEspacioEnMemoria.png](SXE_Fotos_03/9ºEspacioEnMemoria.png)

Para consultar el espacio en disco usado por Docker:

```bash
docker system df
```

Es posible que veas más uso si previamente realizaste otras tareas con Docker.

---

## 8. Ver Uso de Memoria RAM

![11ºComandoRAM.png](SXE_Fotos_03/11ºComandoRAM.png)

Para consultar el uso de RAM por parte de Docker:

```bash
docker stats
```

![10ºRam.png](SXE_Fotos_03/10ºRam.png)

Cada contenedor ocupa aproximadamente 700 KiB de RAM.
