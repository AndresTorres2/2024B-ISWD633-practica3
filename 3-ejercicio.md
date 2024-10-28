## Esquema para el ejercicio
![Imagen](img/esquema-ejercicio3.PNG)

### Crear red net-wp
# COMPLETAR CON EL COMANDO COMANDO

docker network create net-wp


### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/


La información se guarda en /var/lib/mysql dentro del contenedor. Al montar un volumen, los datos se mantienen seguros, lo que garantiza que no se perderán y asegura su persistencia.


En el esquema del ejercicio carpeta del contenedor (a) es  /var/lib/mysql

Ruta carpeta host: C:\Users\tandr\ejercicio3\db

### ¿Qué contiene la carpeta db del host?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

Por el momento no contiene nada. 

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# COMPLETAR CON EL COMANDO

docker run -P -d --name mysql --env-file=${PWD}/ejercicio3/variableEntorno.env -v ${PWD}/ejercicio3/db:/var/lib/mysql --network net-wp mysql:8

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA


Ahora, la carpeta db contiene toda la información (archivos y directorios) que está almacenada en el contenedor MySQL, específicamente en el directorio /var/lib/mysql. Esto significa que cualquier dato que maneje MySQL se encuentra disponible en esa carpeta.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es (/var/www/html)

Ruta carpeta host: C:\Users\tandr\ejercicio3\www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO


docker run -d --name wordpress --network net-wp -v  C:\Users\tandr\ejercicio3\www:/var/www/html --env-file C:\Users\tandr\ejercicio3\wordpress.env  wordpress

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA


Cuando eliminas y recreas el contenedor, las configuraciones y el contenido que has añadido se conservan porque están almacenados en un volumen conectado al sistema principal. Esto asegura que cualquier cambio que realices en WordPress se mantenga intacto, incluso si decides borrar y volver a crear el contenedor.


