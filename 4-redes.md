# Redes
Las redes son un componente fundamental que permite la comunicación entre contenedores, así como la comunicación de los contenedores con el mundo exterior. 
![Imagen](imagenes/redes.PNG)
- Bridge: Esta es la red por defecto en Docker. Permite la comunicación entre contenedores en el mismo host. Cada contenedor conectado a la red bridge tiene una IP propia en la subred de la red bridge.
    -  Brige por default: Cuando se ejecuta un contenedor, Docker crea automáticamente una red de tipo bridge por default. Esta red se utiliza para permitir la comunicación entre contenedores en el mismo host. Cada contenedor conectado a esta red obtiene su propia dirección IP en la subred de la red bridge.
    - Bridge creada por nosotros: Un usuario también puede crear sus propias redes de tipo bridge en Docker. Esto puede ser útil para organizar y segmentar los contenedores de una aplicación de manera más controlada. Al crear una red bridge personalizada, se puede especificar un rango de direcciones IP y otras configuraciones de red específicas. Los contenedores conectados a esta red utilizarán las direcciones IP de la subred definida por el usuario.
- Host: Con esta red, los contenedores comparten la red del host en lugar de tener su propia interfaz de red. Esto puede mejorar el rendimiento de red, pero los contenedores pueden entrar en conflicto con los puertos del host si intentan utilizar los mismos puertos.
- None: Con esta red, se deshabilita la configuración de red. Los contenedores que usan esta red tienen su propia red de bucle invertido y no pueden comunicarse con otros contenedores a menos que se conecten explícitamente a una red.

### Crear una red de tipo bridge

```
docker network create <nombre red> -d bridge
```

### Crear un contenedor vinculado a una red

```
docker run -d --name <nombre contenedor> --network <nombre red> <nombre imagen>
```

### Para saber a qué red está conectado un contenedor

```
docker inspect <nombre contenedor>
```
ó
```
docker network inspect <nombre red> 
```

### Vincular contenedor a una red
```
docker network connect <nombre red> <nombre contenedor>
```

### Para desvincular un contenedor de una red
```
docker network disconnect <nombre red> <nombre contenedor>
```

### Para listar las redes existentes
```
docker network ls
```

### Crear los contenedores y las redes que se presentan en el esquema. Usar para todos los contenedores la imagen de nginx:alpine

![Imagen](imagenes/esquema-ejercicio-redes.PNG)
#### Creamos las redes
```
docker network create net-curso01
docker network create net-curso02
```

#### Creamos los contenedores y vinculamos a sus respectivas redes
```
docker run -d --name nginxContainer1 --network net-curso01 nginx:alpine
docker run -d --name nginxContainer2 --network net-curso01 nginx:alpine
docker run -d --name nginxContainer3 --network net-curso01 nginx:alpine
docker network connect net-curso02 nginxContainer3
docker run -d --name nginxContainer4 --network net-curso02 nginx:alpine
```

![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/f8f01994-f9bb-448a-a45c-596790a00a7e)

![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/c7e396dd-1dcf-4e91-9a69-0b319bbf6577)
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/287b6a87-766c-44bb-897f-15ebb38a31b8)

### Para eliminar las redes creadas
```
docker network rm <nombre de la red>
```
```
docker network rm net-curso01
docker network rm net-curso02
```
