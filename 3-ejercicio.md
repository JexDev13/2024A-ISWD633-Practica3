## Esquema para el ejercicio
![Imagen](imagenes/esquema-ejercicio3.PNG)

### Crear red net-wp
# COMPLETAR CON EL COMANDO COMANDO
docker network create net-wp


### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (a) es (COMPLETAR CON LA RUTA)
Ruta carpeta host: D:docker/ejercicio3/db

### ¿Qué contiene la carpeta db del host?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
La carpeta D:\docker\ejericio3\db en el host contendría los archivos y datos persistentes de MySQL si se configurara para almacenar datos allí ademas de la variable de entorno para MySQL.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# COMPLETAR CON EL COMANDO
docker run -d --name mysql-container --network net-wp --env-file D:\DockerEnv\mySql.env -v D:\docker\ejercicio3\db:/var/lib/mysql mysql:8


### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Se lleno automaticamente despues de crear el contenedor y se lleno con los archivos de configuración de MySQL sin embargo tambien podria almenecer datos de persistencia como lo seria la base de datos o tablas básicas.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta contenedor (b) es (COMPLETAR CON LA RUTA)
Ruta carpeta host: D:\docker/ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO
docker run -d --name wordpress-container --network net-wp --env-file D:\DockerEnv\wp.env -v D:\docker\ejercicio3\www:/var/www/html -p 8080:80 wordpress:latest

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Como ambos contenedores fueron creados con un volumen en el momento que se elimino los contenedores los archivos persistieron en la maquina host por lo que al volver a crear los contenedores de MySQL y Wordpress estos guardaron la configuración existente por lo que la ultima entrada a la base de datos se mantuvo con normalidad.



