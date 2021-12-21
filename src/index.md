---
layout: base.njk
title: Podbuster-Documentación
templateEngineOverride: njk,md
---
### Presentación y Objetivos

 Este documento, describe el trabajo realizado en el proyecto final del Curso de programación Web Fullstack:Frontend,Backend y Devop.El mismo fue llevado a cabo desde el 14 de septiembre al 22 de diciembre de 2021.Nuestro grupo de trabajo esta conformado por :  
 
- **Rafael**
- **Pablo Hernandez**
- **Ricardo Pineda**
- **María Luján Ibrahin**

<p>El proyecto consiste en el desarrollo del sitio web Podbuster ,donde a través de una biblioteca  los usuarios pueden almacenar  y organizar sus podcast,para ello los usuarios de la aplicación deben estar registrados y logueados para acceder a los mismos.También cuenta con la funcionalidad de ver otros podcast de carácter público en la misma página.</p>

### ¿Por qué Podbuster y no otro sitio?

 Hemos construido una red de contenidos sonoros para  estar informados,entretenidos y sobre todo para pensar. Podcast Podbuster, es  una red viva y flexible  con una amplia oferta, dado que cada usuario sube su contenido por lo que se adapta a las necesidades, gustos e intereses de cada oyente.El acceso  es gratuito y global.

### ¿Cómo trabajamos?

 Semanalmente nos hemos comunicado y trabajado por distintos medios: whatsapp, reuniones a través de la aplicación Discord y utilizado horas de clases para el desarrollo del proyecto con blackboard.Utilizamos la modalidad **pair programming** en varias ocasiones, como ejemplo cuando no funcionaba la implementación de algunos endpoints dado que los 4 tenemos experiencias en distintas tecnologías.También hemos trabajado en forma **individual** y presentado los resultados en la reunión siguiente.
<p>Planificamos el trabajo  través de la metodología Agile scrum,en el cual se ha pautado junto al Owner la totalidad de 6 sprints.Donde en cada uno de ellos fue escalando la complejidad y el valor agregado del producto mínimo viable planteado en el primer sprint.</P>

![image a](https://blog.wearedrew.co/hubfs/metodolog%C3%ADa%20scrum.png) 

<p> A continuación se puede visualizar los punteos de cada sprint, en cada uno de ellos se han cumplido con las etapas de SCRUM : planificación, desarrollo, Scrum diario(daily), revisión  y retrospectiva.</p>

	
| Primer sprint | Segundo sprint | Tercer sprint |Cuarto Sprint | Quinto Sprint | Sexto Sprint |
| -- | -- | -- |-- | -- |-- |
| 1 Oct - 15 Oct| 15 Oct - 29 Oct | 29 Oct - 12 Nov| 12Nov - 23 Nov | 26 Nov -9 Dic | 9 Dic-22 Dic |
| Definición del MPV|Crear dockerfile frontend y backed| Elegir tecnología para backend| Creación y Población BBDD | Elegir tecnología a utilizar en Front | Conectar Backend y Front |
| Priorización de tareas |Crear DockerCompose  | cambios en el docker de backend | Implementación de Endpoints | Modificar en dockerfile para Front. | Crear test de componentes y páginas |
| Board GitHub actualizado | Configurar y crear DigitalOcean | Definición de los endpoint backend para el MPV | CI/CD de Frontend y Backend | Crear componentes/páginas partiendo de los mockups | Preparar presentación|
| Mockups | Definir diagrama de entidades | Implementación de algunoS de los endpoint | Test de Endpoints | Componentes/Páginas a implementar | Documentación Finalizada |


### Tecnologías utilizadas

 En el desarrollo nuestro sitio web hemos cambiado las tecnologías al transcurrir las clases y votar entre los integrantes .A continuación, en cada link puede verse el proceso y despliegue de ambos entornos.

{% include "postlist.njk" %}
