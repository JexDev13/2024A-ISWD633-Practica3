# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```

### Crear un volumen tipo host con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host: directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html esta ruta se obtiene al revisar la documentación
![Volúmenes](imagenes/volumen-host.PNG)
# COMPLETAR CON EL COMANDO

docker run -d --name mi_nginx -p 80:80 -v D:\html:/usr/share/nginx/html nginx:alpine

### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Aparece un error de tipo 403, esto me indica que el recurso no es accesible desde el contenedor ya que no tengo archivos de tipo html dentro de la carpeta html del host, sin embargo al incluir un template html básico el problema se soluciona.


### ¿Qué pasa con el archivo index.html del contenedor?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
El archivo index.html del contenedor se sirve al visitar http://localhost. Si la carpeta html del host está vacía, al agregar un index.html con contenido esto permitira que Nginx funcione correctamente y muestre la página.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de nginx/html
### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Al actualizar el index con el template gratuito dentro del contenedor recibe la nueva información por lo que ahora se enseña en pantalla la nueva información que puede incluir mas archivos como css o scripts de java script 
![image](https://github.com/JexDev13/2024A-ISWD633-Practica3/assets/119013519/487d392d-64fe-43ba-982d-2c8ebf023c11)


### Eliminar el contenedor
# COMPLETAR CON EL COMANDO
docker rm -f mi_nginx


### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Al tener un espacio dentro de la memoria locla del host al eliminar el contenedor se elimina la vinculación a la ruta de los archivos sin embargo los archivos persisten lo que facilita al volver a crear el contenedor este se cree con la configuración previa a la eliminación. 

### ¿Qué hace el comando pwd?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
El comando pwd muestra la ruta del directorio actual en el que estoy trabajando. Cuando se ejecuta en la terminal, se indica la ubicación exacta en el sistema de archivos, lo que me ayuda a orientarme y confirmar dónde estoy antes de ejecutar otros comandos.
Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

