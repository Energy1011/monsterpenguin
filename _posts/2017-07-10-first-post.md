---
layout: post
title:  "Migrando  de Wordpress a Jekyll"
date:   2017-05-10 22:01:43 +0530
categories: Jekyll
author: "Energy1011"
---
# Hello Jekyll 
El día de hoy he tomado la desicion de migrar mi blog alojado en Wordpress a Jekyll, en este post pretendo cubrir los siguientes puntos:
- ¿ Qué es Jekyll ?
- Caracteristicas principales y la razónes por las cuales he decidio migrar
- Cómo migrar de wordpress a Jekyll

## ¿Qué es Jekyll? 
Jekyll es una herramienta que nos ayudara a generar blogs con contenido estatico que se sirve de las github pages de github.

Para comprdender el parrafo anterior y explicar Jekyll, primero tenemos que conocer sobre github y sus pages; Si aun no tienes claro el tema de github y sus pages lo explico a continuación, de lo contrario puedes saltar la explicación de github y pasar tranquilamente a las caracteristicas principales de Jekyll.

## Github
Github es un servicio que ofrece a sus usuarios la posiblidad de subir y publicar sus proyectos repositorios de Git, actualmente Git es un control de versiónes ampliamente utilizado y popular, los repositorios subidos a Github son accesibles desde cualquier lugar con conexión, Github cuenta con una interfaz web amigable en la que podemos navegar entre los repos de los usuarios como si fuese una red social para programadores ( En este otro post hablo sobre git y animo a otro tipo de usuarios a usarlo, no solo programadores ) comparando Github en terminos de una red social se pueden destacar los siguientes aspectos:

- Cada usuario registrado cuenta con una pagina de perfil con contenido (mayormente código de proyectos)
- Podemos realizar busqueda de usuarios y repositorios en particular.
- Exite contenido publico y privado, es decir, hay repositorios que no pueden ser accedidos publicamente pagando una cuota mensual, y los publicos son totalmente gratuito..
- Cada repositorio cuenta con un apartado para levantar issues y realizar comentarios.
- Podemos crear paginas las llamadas github pages

Este ultimo punto es en el que haremos enfasis ya que para el funcionamiento de Jekyll hace uso de este servicio adicional de Github.

El servicio de Github como ya lo mencione, cuenta con las llamadas Github Pages, que no son más que paginas de presentación de contenido HTML dentro del espacio del usuario de github. Para acceder a mi perfil usuario de Github lo puedo hacer de la siguiente manera: <https://github.com/energy1011](https://github.com/energy1011> 

Al crear una pagina Github Page accederia por ejemplo de esta otra manera:
<https://energy1011.github.io/monsterpenguin>
Todas las github pages tienen esta forma como se explica aquí:

Todo el contenido de una github page, archivos HTML, imagenes, etc. Estarán en un repositorio de github (similar a tener los archivos en cualquier otro servicio de hosting para paginas web, solo que en este caso de Jekyll todo el contenido es público)

En resumen de este apartado: Jekyll nos permite generar contenido estatico que subiremos a un repositorio que hace uso del servicio de hosting de las github pages dentro de github.


{% highlight python linenos %}

{% endhighlight %}

## Caracteristicas principales y la razónes por las cuales he decidio migrar 

Cuando supe que Jekyll trabaja de una forma complemtamente distinta a Wordpress fue ahí cuando me puse a investigarlo y probarlo.Con Jehyll he logrado migrar mi blog alojado en [https://monsterpenguin.wordpress.com/](https://monsterpenguin.wordpress.com/)
### This is HTML code block
{% highlight html linenos %}

{% endhighlight %}
