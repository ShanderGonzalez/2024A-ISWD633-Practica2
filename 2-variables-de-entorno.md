# Variables de Entorno
### ¿Qué son las variables de entorno?
Son valores dinámicos que afectan el funcionamiento de un proceso en un sistema operativo. Se usan para acceder a informacion importante para configurar su funcionamiento.

### Para crear un contenedor con variables de entorno

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.

```
docker run -d --name nginx -e username=shander -e role=admin nginx:alpine
```

![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/c8660815-50c2-48e4-a441-15d4fa1f9614)

### Crear un contenedor con mysql:8 , mapear todos los puertos
```
docker run -P -d --name mysql mysql:8
```

### ¿El contenedor se está ejecutando?
No, el contenedor no se esta ejecutando

### Identificar el problema
El problema se debe a que al momento de crear el contenedor no encontro la imagen mysql:8

### Eliminar el contenedor creado con mysql:8 
```
docker rm mysql
```

### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

Previo a esto es necesario crear el archivo y colocar las variables en un archivo, **.env** se ha convertido en una convención estándar, pero también es posible usar cualquier extensión como **.txt**.
```
docker run -d --name <nombre contenedor> --env-file=<nombreArchivo>.<extensión> <nombre imagen>
```
**Considerar**
Es necesario especificar la ruta absoluta del archivo si este se encuentra en una ubicación diferente a la que estás ejecutando el comando docker run.

### Crear un contenedor con mysql:8 , mapear todos los puertos y configurar las variables de entorno mediante un archivo
```
docker run -P -d --name mysql8 --env-file=varEntorno.env mysql:8
```
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/f340620c-92db-4614-a317-842caaa4a92e)
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/a4b24a7e-3ad1-4e1c-9b7e-b00756089ece)


### ¿Qué bases de datos existen en el contenedor creado?
Existen 5 bases de datos en el contenedor:
- information_schema
- mydatabase
- mysql
- performance_schema
- sys
![image](https://github.com/ShanderGonzalez/2024A-ISWD633-Practica2/assets/94009521/f0fed874-2484-46a6-9fa5-9eeda45720ad)
