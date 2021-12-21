---
title: Back-end
---

 En este apartado vamos a desarrollar el **backend** de nuestro proyecto,es decir la capa de acceso a datos.Hemos cambiado algunas tecnologías por votación del grupo y finalmente hemos optado por trabajar con Nodejs,Express y Mongodb.
 
**Contenido**   

1. [Primer sprint](#id1)
2. [Segundo sprint](#id2)
3. [Tercer sprint](#id3)
4. [Cuarto sprint](#id4)
5. [Quinto sprint](#id5)
6. [Sexto sprint](#id6)

### Primer sprint: Definición del MPV y prioridades<a name="id1"></a>
 En el primer sprint el equipo tuvo que mostrar al owner cómo iba  diseñar el proyecto, estableciendo el producto minimo viable,el cual sería crear un sitio web a partir de una biblioteca donde el usuario cuenta con las funcionalidades de 1) registro y logueo para acceder a los podcast, 2) una vez logueado pueda incluir podcast en su biblioteca insertando una URL válida. Por ejemplo de plataformas como youtube.com, 3) El usuario/a tendrá una pantalla especifica para ver sus podcast favoritos y acceder a su contenido, 4) puede ver pagina de episodios de podcast más recientes con un resumen del mismo, icono del episodio, título, descripción, fecha de emisión original, y un botón para marcarlo como favorito.  
  
  El proyecto  fue estructurado bajo la idea  de una base de datos relacional, MariaDB,pusimos en la balanza los pro y contras y elegimos por votación una base de Datos NoSQL: **MongoDB**
Al owner le presentamos el siguiente diagrama,aunque ya a la sprint entrante hicimos l modificación.  


![image a](https://laeradelamusica508526020.files.wordpress.com/2021/12/diagrama-mariadb.png?w=535)

 

![image a](https://laeradelamusica508526020.files.wordpress.com/2021/12/diagrama-mongodb.png?w=572)  
El diagrama de MongoDB,es inicial.Hemos modificado la estructura, por ejemplo las colecciones en bbdd no es insertOne sino insertMany 


### Segundo sprint: Dockerfile, Dockercompose y DigitalOcean.<a name="id2"></a>



 Para poner en práctica nuestro proyecto, pautamos una estructura inicial 

~~~
├── controllers
        ├── podcasts.js
    ├── server.js
    ├── init       
    │   ├── 01_user.sql
    │   ├── 02_podcast.sql
    │   ├── 03_category.sql  
    ├── package.json
    ├── package-lock.json  
~~~

 Tras haber trabajado en ella a quedado con la siguiente estructura para la entrega final:  

~~~
Podcast-library-Backend
│───Mongo-data/db
│     ├── seed.js
│───src
│     ├── controllers
│        ├──auth.js 
│        ├──dashboard.js
│        ├──podcasts.js
│        ├──user.js
│        ├──validate-token.js 
│     ├── Models
│        ├──podcasts.js
│        ├──user.js
│        ├──server.js
│     ├── Tests
│        ├── podcast.test.js
│        ├── user.test.js
├── server.js
├── dockerignore
├── gitignore  
├── Docker-compose.yml
├── Dockerfile
├── package-lock.json
├── package.json
├── README.md
├── run.sh
├── start.sh  
~~~

 Entre las tareas pautadas en el sprint, tuvimos que crear nuestro Dockerfile.Basicamente  son los archivos que contienen las instrucciones que crean las imagenes y estos deben estar guardados dentro de un build context, es decir, un directorio. Este directorio es el que contiene todos los archivos necesarios para construir nuestra imagen, de ahí lo de build context.
 En  DockerFile, especificaremos todo lo que necesitaremos con respecto al sistema operativo, las variables de entorno y cómo ejecutar nuestra aplicación.

![image a](https://laeradelamusica508526020.files.wordpress.com/2021/12/docker-imagen.png?w=1024)

*En el dockerfile vamos a ejecutar distintos comandos*

- En **FROM** aquí estamos seleccionando la imagen  node versión 17-slim del sistema operativo Docker Hub( es un repositorio global que contiene imágenes que podemos extraer localmente). En nuestro caso, estamos eligiendo una imagen de Node más liviana ya  que la versión que elegimos en principio ocupaba gran parte de la memoria del servidor de DigitalOcean.
- En **WORKDIR**  definimos un directorio de trabajo : *“src”*. Esta es una forma de configurar lo que sucederá más adelante en el siguiente comando .
- En **COPY** package.json estamos copiando los archivos del directorio donde estamos especificando un directorio a través de este comando.  

- Seguido ejecutaremos el comando en la terminal *”run npm install”* .En nuestro caso, instalaremos todas las bibliotecas que necesitamos para desarrollar nuestra aplicación Node.js con Express. 

- Luego ejecutaremos el comando *"run npm install nodemon -g"*  

- **EXPOSE**: Aquí significa que abriremos el puerto 8000 y es a través de esta puerto es que nos comunicamos con nuestro contenedor.

- **ENTRYPOINTS**: Aquí es donde debemos indicar cómo comenzaremos nuestra aplicación. El comando inicialmente era “app.js”, luego lo renombramos a “server.js”  
 En la siguiente imagén puede verse la configuracíon que utilizamos para el archivo package.json y server.js.  
 
![image a](https://laeradelamusica508526020.files.wordpress.com/2021/12/pack-y-server-imagen.png?w=1024)  


#### DigitalOcean
 Luego de adquirir nuestro dominio <strong>podbuster.live</strong>, realizamos las configuraciones necesarias en nuestro servidor  de DigitalOcean.

+ Creamos un droplet e instalamos docker.  
+ configuramos Cloudflare y gestionamos los DNS.  
+ Realizamos la configuración del Nginx como servidor y Vinculamos  el dominio.  

![image a](https://laeradelamusica508526020.files.wordpress.com/2021/12/dopler.png?w=1024)

![image a](https://laeradelamusica508526020.files.wordpress.com/2021/12/dns-digital-ocean-1.png?w=1024)

![image a](https://laeradelamusica508526020.files.wordpress.com/2021/12/dominio-digital-ocean-1.png?w=1024)
<br>




### Tercer sprint: Definición e inplementación de Endpoints. <a name="id3"></a>  
 Aquí definimos que endpoints  eran necesarios para nuestro MPV:
~~~
GET - "/podcasts/all" - Returns all podcast.
GET - "/podcasts/:id" - Returns podcast by ID.
GET - "/podcasts/title/:title" - Returns a podcast by title.
GET - "/podcasts/genre/:genre" - Returns podcasts by category.
GET - "/podcasts/author/:author" - Returns podcasts by author.
POST - "/podcasts/:id" - add a podcast per id.
DELETE - "podcasts/:id" - Delete podcast by ID.
GET - "/users/:id" - Returns a user by id.
DELETE - "/users/:id" - Delete user by ID.
POST - "/users/:id" - add a user per id.
~~~  


**_Implementación inicial de endpoints_**


Poder sacarlos ha sido dificultoso.La estructura de los mismos en el backend es la siguiente:  

 ![image endpoints](https://laeradelamusica508526020.files.wordpress.com/2021/12/ejemplo-de-endoints-1.png?w=1024)  

Implementación :
Aqui va un print de pantalla del endpoint funcionando.


### Cuarto sprint: Creación y población de BBDD - CI/CD. <a name="id4"></a>
 Varios son los puntos que componen este sprint.Por un lado tuvimos que crear la base de datos y luego poblarla.En este último punto lo realizamos de manera distinta,uno coloco el número de id de usuario manualmente y "db.user.insertOne" y el otro integrante de forma automatica con "db.user.insertMany", ambos dejamos que se asigne de forma automatica el "_id: ObjectId".Se subieron ambos a github,se elegió trabajar con el formato "db.user.insertMany",quedando los otros datos de "db.user.insertOne" para integrarlos en la base final.  

 ![image endpoints](https://laeradelamusica508526020.files.wordpress.com/2021/12/poblacion-bbdd.png?w=1024)


En cuanto a nuestro CI/CD
 a quedado así tras el quinto sprint:  

 ![image ci](https://laeradelamusica508526020.files.wordpress.com/2021/12/ci-1.png?w=867)  

 ![image ci](https://laeradelamusica508526020.files.wordpress.com/2021/12/cd.png) 

 Empezamos a realizar la *Authentication* y los *tests*,pero no llegamos a presentarle todo al Owner.  
 ![image Autenthication](https://laeradelamusica508526020.files.wordpress.com/2021/12/authentication2.png?w=600)  
 
 ![image Autenthication1](https://laeradelamusica508526020.files.wordpress.com/2021/12/authentication-1.png?w=653)  

 ![image Autenthication](https://laeradelamusica508526020.files.wordpress.com/2021/12/ahutenticacion.png?w=686)  


### Quinto sprint:Culminación de Authentication y testing. <a name="id5"></a>
Las tareas de este sprint,corresponden todas a Front-end.Tras el retraso que sufrimos en el sprint anterior,usamos este sprint para realizar algunas las tareas adeudadas.En cuanto a los archivos de *Authentication*,fueron reemplazados por el archivo auth.js 

![image Auth](https://laeradelamusica508526020.files.wordpress.com/2021/12/auth1.png?w=1024)  


![image Auth](https://laeradelamusica508526020.files.wordpress.com/2021/12/auth2-1.png?w=1024)  

##### Testing

 Para realizar las pruebas hemos utilizado Postman + Mocha + chai.Hemos realizado las configuraciones dentro de la carpeta Tests,en los archivos podcast.test.js y en user.test.js:

 ![image testing](https://laeradelamusica508526020.files.wordpress.com/2021/12/testing-1-2.png?w=1024)

![image testing](https://laeradelamusica508526020.files.wordpress.com/2021/12/testing-2.png?w=622)  

### sexto sprint<a name="id6"></a>

*Conexión  entre Frontend y Back-end*

 Pendiente



