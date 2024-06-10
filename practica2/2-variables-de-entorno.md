# Variables de Entorno
### ¿Qué son las variables de entorno

Las variables de entorno son un conjunto de valores que pueden afectar el comportamiento de los procesos en un sistema operativo
# COMPLETAR

### Para crear un contenedor con variables de entorno

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.

docker run -d --name nginx_env -e username=myuser -e role=admin nginx:alpine

# COMPLETAR

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR

![alt text](image-9.png)

### Crear un contenedor con mysql:8 , mapear todos los puertos

docker run -d --name mysql_container -e MYSQL_ROOT_PASSWORD=rootpassword -p 3306:3306 mysql:8

# COMPLETAR

### ¿El contenedor se está ejecutando?
Sí
![alt text](image-10.png)
# COMPLETAR

### Identificar el problema
# COMPLETAR

### Eliminar el contenedor creado con mysql:8 
docker rm -f mysql_container
![alt text](image-11.png)
# COMPLETAR

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
# COMPLETAR

MYSQL_ROOT_PASSWORD=rootpassword
MYSQL_DATABASE=mydatabase
MYSQL_USER=myuser
MYSQL_PASSWORD=mypassword

docker run -d --name mysql_env_container --env-file=.env -p 3306:3306 mysql:8
![alt text](image-12.png)

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR 

![alt text](image-13.png)

### ¿Qué bases de datos existen en el contenedor creado?

information_schema
mydatabase (esta es la base de datos que especificamos en el archivo .env)
mysql
performance_schema
sys
# COMPLETAR