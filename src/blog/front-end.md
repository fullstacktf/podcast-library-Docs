---
title: Front-end

---
 En este apartado vamos a desarrollar el **Front-end** de nuestro proyecto, es decir la capa de un sitio web que interactúa con los usuarios, por eso decimos que está del lado del cliente. Hemos cambiado algunas tecnologías por votación del grupo y finalmente hemos optado por trabajar con React, Typescript & Chakra UI client. En cuanto a los sprint el 2 y 3 no contenian tareas de Front-end.
 
**Contenido**   

1. [Primer sprint](#id1)
2. [Cuarto sprint](#id2)
3. [Quinto sprint](#id3)
4. [Sexto sprint](#id4)

### Primer sprint: Mockups<a name="id1"></a>
 Aquí los 4 integrantes realizamos en figma un mockup, para presentarle al Owner. A partir de allí tomamos ciertas estructuras para el diseño de nuestro proyecto final.  
   
![image a](https://laeradelamusica508526020.files.wordpress.com/2021/12/mockup.pablo_.png?w=710)

![image a](https://laeradelamusica508526020.files.wordpress.com/2021/12/mockup.maria_.png?w=736)  


 En este sprint pautamos una estructura de proyecto inicial.

 ~~~
 ├── public
    │   ├── fonts
    │   ├── images
    ├── src       
    │   ├── assets
    │   ├── components
    │   ├── pages
    │   ├── services
    │   ├── utils
    │   ├── App.jsx
    │   ├── main.jsx
    ├── .gitignore                     
    ├── index.html                   
    ├── package-lock.json
    ├── package.json
    ├── README.md
    └── vite.config.js
~~~

 Al finalizar el quinto sprint asi quedó nuestra estructura de proyecto.  
 ~~~
 ├── public
│    ├── assets    
│    │   ├── icons
│    │   │   └── podbuster.ico
│    │   ├── images
│    │   │   ├── homepage.png
│    │   │   └── microWallpaper.jpg
│    │   └── logo
│    │       └── podbuster.ico              
│    ├── index.html                  
│    ├── manifest.json
│    └── robots.txt
├── src       
│    ├── Animations
│    ├── components
│    ├── fonts
│    ├── hooks
│    ├── icons
│    ├── language
│    ├── pages
│    ├── services
│    ├── theme
│    ├── App.test.tsx
│    ├── App.tsx
│    ├── react-app-env.d.ts
│    ├── reportWebVital.ts
│    ├── setupTest.ts
│──.dockerignore
│──.gitignore
├── Dockerfile                                       
├── package-lock.json
├── package.json
├── README.md
├── tsconfig.json 
~~~

 ### Cuarto sprint: CI/CD de Front-end<a name="id2"></a>

 El proceso de integración y distribución continuas incorpora la automatización y la supervisión permanentes en todo el ciclo de vida de las aplicaciones, desde las etapas de integración y prueba hasta las de distribución e implementación. También tuvimos que implementarlo en back-end.

![image a](https://laeradelamusica508526020.files.wordpress.com/2021/12/ci-front.png?w=1024)

  ### Quinto sprint: Elección de tecnologías - Modificación Dockerfile <a name="id3"></a>

  Nuestro Dockerfile de Front-end
![image a](https://laeradelamusica508526020.files.wordpress.com/2021/12/dockerfile-fronted.png?w=537)

 En este punto estuvimos duditativos en la elección de la tecnología,en la rama develop se realizaron con *Vue.js + vuetify* distintos componentes para la página(Menú, footer y carousel). Luego de impartida la clase de *REACT*, votamos y terminamos utilizando esta última tecnología. 

 El último punto de este sprint es *Crear componentes partiendo de los mockups*. A continuación subimos algunos componentes como se solicita en el sprint: *login,register,sidebar*.

![image a](https://laeradelamusica508526020.files.wordpress.com/2021/12/sidebar1.png?w=990)


![image a](https://laeradelamusica508526020.files.wordpress.com/2021/12/login.png?w=1000)

![image a](https://laeradelamusica508526020.files.wordpress.com/2021/12/register.png?w=1024)

 
### pendientes y futuras actualizaciones<a name="id6"></a>
En el grupo tenemos pensado para futuras modificaciones sumar la lupa para realizar las busquedas.
