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

Cuando supe que Jekyll trabaja de una forma complemtamente distinta a Wordpress fue ahí cuando me puse a investigarlo y probarlo, con Jekyll he logrado migrar mi blog alojado a modo free -sin pago- de <https://monsterpenguin.wordpress.com/> a <https://monsterpenguin.wordpress.com/>

Características de Jelyll:
- Hosting gratuito, themes y plugins
- Utiliza Markdown por default y podemos trabajar de manera offline
- Es veloz por contenido estatico y no utiliza base de datos
- Flexible, podemos agregar código Javascript en las publicaciones
- Usamos Git y es muy portable
- Dejamos todo el contenido libre

### Hosting gratuito
Para los que nos interesa tener un blog sin tener la necesidad de pagar $ dinerito por hosting, themes, plugins tenemos pocas opciones viables. Wordpress por ejemplo nos da la posibilidad de tener un blog en modo free hosting aunque limitado en algunos aspectos, por ejemplo Wordpress en modo free no nos permite instalar plugin o modificar el theme libremente en muchos casos nos puede incluir publicidad no deseada. 

Jekyll por otra parte es muy buena opción ya que no hay que pagar por themes, plugins o hosting. Como ya mencione Jekyll al hacer uso de las github pages es de hosting gratuito por parte de github, los themes podemos adquiridos forkeando otros repos o códificar los nuestros al gusto, lo mismo pasa con el tema de los plugin (eso si, hay que tener almenos noción de HTML/CSS).

### Utiliza Markdown por default
La ventaja de que Jekyll tenga Markdown de manera nativa es fantastico, ya que de la misma manera que editamos nuestro archivo README.md que ponemos dentro de nuestros proyectos de git y que subimos a github podemos elaborar nuestras publicaciones. 

En otra publicación anterior que hice sobre (Markdown) mencione la importancia y ventajas de utilizar este lenguaje de marcado de texto ligero, también explico cómo es que lo utilizo día a día para ayudarme a llevar notas de lo que voy aprendiendo sobre informática, el hecho de que que mis apuntes de estudio ya esten en formato Markdown me reduce el esfuerzo cuando los quiero convertir a una publicación para mi blog en Jekyll. Y si fuese poco Jekyll me permite trabajar de manera offline con Markdown e ir viendo exactamente como va a lucir mi publicación en formato Markdown al ser publicada en mi blog como HTML estatico.

### No utiliza base de datos 
Haré una comparativa con wordpress primero: Wordpress trabaja de manera distinta, ya que requiere de una base de datos para guardar las publicaciones, configuraciones de nuestro blog incluso, plugins, etc

Jekyll a diferencia de Wordpress no utiliza base de datos ya que todo el contenido es previamente generado desde nuestros archivos Markdown que esten dentro de nuestra carpeta *_posts* a archivos html estaticos para ser adquiridos desde la carpeta *_site*. Lo anterior nos demuestra que Jekyll no necesita hacer consultas a una base de datos para obtener las publicaciones de nuestro blog, lo que hace es obtener el archivo html dentro de la carpeta *_site* esto lo hace veloz comparandolo con wordpress.

Otra ventaja de no tener base de datos para nuestro blog es que nos despreocupamos por inyecciones SQL u otros tipos de ataques a la base de datos de nuestro sitio, ya que simplemente no cuenta con una.

### Flexible, podemos agregar código Javascript en las publicaciones
Jekyll es totalmente flexible, todo el código de nuestro blog con esta herramienta puede ser modificado, incluso podemos agregar código Javascript dentro de nuestras publicaciones, temas, templates. Para modificar el comportamiento de nuestro sitio, cosa que con Wordpress en modo free no podemos realizar.

Si quisieramos por ejemplo agregar google analytics para ver las estadisticas de visitas en nuestro blog o implementar un buscador de publicaciones en Jekyll, podemos lograrlo.

### Usamos Git y es muy portable

Otro tema importante aparte de las copias de seguridad es la portabilidad, Jekyll al usar archivos markdown dentro de un repositorio nos da una portabilidad simple y poderosa. 

Tareas como realizar backups, exportar publicaciones y llevar el control de versiones son simples con Jekyll.

El utilizar git para llevar nuestro blog nos ayuda a darle un seguimiento profesional de versiones a nuestro blog, podemos llevar el control de cambios de una manera muy precisa. 

Los respaldos y copias de todo nuestro blog las tendremos locales y remotas en los servidores de github.

### Resumen
Jekyll es una muy buena opción para todas las personas que quieran tener un blog gratuito, flexible, ligero y además cercanamente vinculado con su cuenta de github, ya que esto ultimo puede ser una gran ventaja, si ya tenemos bastantes seguidores en github, facilmente pueden enterarse de nuestro blog y sirve como buena referencia. 
{% highlight html linenos %}

{% endhighlight %}
