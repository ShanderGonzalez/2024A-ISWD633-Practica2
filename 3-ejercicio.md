### Crear contenedor de Postgres sin que exponga los puertos. Usar la imagen: postgres:11.21-alpine3.17
```
docker run -d --name postgresContainer --env-file=varPostgres.env postgres:11.21-alpine3.17
```
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/c4669bff-6479-46a6-8b3d-95f6de88512a)

### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4
```
docker run -d -p 8080:80 --name pgadminContainer --env-file=pgadmin.env dpage/pgadmin4
```
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/ea9c1092-1ecf-477d-b4d6-726617af5eff)

La figura presenta el esquema creado en donde los puertos son:
- a: 8080
- b: 80
- c: 5432

![Imagen](imagenes/esquema-ejercicio3.PNG)

## Desde el cliente
### Acceder desde el cliente al servidor postgres creado.
- http://localhost:8080/
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/fc337798-10fe-4e5c-ac91-b745a93394db)

### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre.
```
docker exec -it postgresContainer psql -U postgres -d postgres
```
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/868f6f21-6f38-42c4-b27c-52ff2ddbb4cd)

## Desde el servidor postgresql
### Acceder al servidor
### Conectarse a la base de datos info
```
docker exec -it postgresContainer /bin/bash
/# psql -h 172.17.0.5 -p 5432 -U postgres -d info
```
### Realizar un select *from personas
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/82d572f7-3269-46d7-96ca-995733ce2078)
