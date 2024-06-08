## Esquema para el ejercicio
![Imagen](imagenes/esquema-ejercicio5.PNG)

### Crear la red
```
docker network create net-wp
```

### Crear el contenedor mysql a partir de la imagen mysql:8, configurar las variables de entorno necesarias
```
docker run -P -d --name mysql --env-file=varEntorno.env --network net-wp mysql:8 
```

### Crear el contenedor wordpress a partir de la imagen: wordpress, configurar las variables de entorno necesarias
```
docker run -d --name wordpress -p 9300:80 --network net-wp wordpress
```

De acuerdo con el trabajo realizado, en la el esquema de ejercicio el puerto a es 9300

Ingresar desde el navegador al wordpress y finalizar la configuración de instalación.
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/c61dd93a-3e54-48c7-9a41-590dd9f99312)
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/7e4c9d5a-bc15-4428-99d4-8bc6145d879f)
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/cbdddbd2-0e00-4cdb-bbd1-52122e8a7fc6)

Desde el panel de admin: cambiar el tema y crear una nueva publicación.
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/dc2676b0-33aa-463b-8cc3-6dd2e270f8ca)
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/3131d389-c16a-4b64-a0aa-68a57996905c)
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/c09d3f97-d002-41c9-a3b3-ecbf068ae245)
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/5dc9ec1d-dcd2-4f6f-b54b-c9e3e94296af)


### Eliminar el contenedor wordpress
```
docker rm wordpress
```

### Crear nuevamente el contenedor wordpress
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress

### ¿Qué ha sucedido, qué puede observar?
Se observa que la configuracion del wordpress se reinicio, por lo que tocaria volver a configurar todo.
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/cfd78821-350a-49c3-b3b3-3713a6d6332b)






