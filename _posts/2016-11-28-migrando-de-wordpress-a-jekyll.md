---
layout: post
title:  "Migrando  de Wordpress a Jekyll"
date:   2017-07-25 22:01:43 +0530
categories: jekyll
author: "Energy1011" 
image: "logo-jekyll.png"

---

# Hello Jekyll 
El día de hoy he tomado la desicion de migrar mi blog alojado en wordpress a jekyll, en este post pretendo cubrir los siguientes puntos:
- ¿ Qué es jekyll ?
- Caracteristicas principales y la razónes por las cuales he decidio migrar
- Cómo migrar de wordpress a jekyll

## ¿Qué es Jekyll? 
Jekyll es una herramienta que nos permite generar blogs con contenido estatico que se alojan en github con las github pages.

Para comprdender cómo funciona jekyll, primero tenemos que conocer sobre github y sus pages. Si aún no tienes claro el tema de github y sus pages lo explico a continuación, de lo contrario puedes saltar la explicación de github y pasar tranquilamente a las caracteristicas principales de jekyll.

## Github
Github es un servicio que ofrece a sus usuarios la posiblidad de subir y publicar sus proyectos en repositorios de git, actualmente git es un control de versiónes ampliamente utilizado y popular, tan iutilizado y popular que no solo los programadores pueden hacer uso de git (hablé sobre esto en este post [Git para todos](wwww.google.com)). Los repositorios/proyectos subidos a github son accesibles desde cualquier lugar con conexión, github cuenta con una interfaz web amigable en la que podemos navegar entre los repos de los usuarios *como si fuese una red social para programadores*, comparando Github en terminos de una red social se pueden destacar los siguientes aspectos:

- Cada usuario registrado cuenta con una página de perfil con contenido (en la mayoría de los casos código de proyectos)
- Podemos realizar busqueda de usuarios y repositorios en particular.
- Exite contenido publico y privado, es decir, hay repositorios que no pueden ser accedidos publicamente, pero para esto es necesario pagar una cuota mensual en github, las cuentas de github "comunes" son gratuitas y sin limite de repos.
- Cada repositorio cuenta con un apartado para levantar issues y realizar comentarios.
- Podemos crear paginas las llamadas github pages.

Este último punto es en el que haremos enfasis, ya que los sitios en jekyll hacen uso de este servicio de github. Las github pages son un servicio adicional para servir paginas de contenido HTML dentro del espacio del usuario registrado en github. Para mayor información [aquí](wwww.google.com)

Por ejemplo: Para acceder a mi perfil de usuario de Github lo puedo hacer con la siguiente dirección <https://github.com/energy1011](https://github.com/energy1011>  (Mi nombre de usuario está hasta el final de la dirección)

Por otra lado mi blog en jekyll desplegado en una githubpage se puede acceder con la siguiente dirección:
<https://energy1011.github.io/monsterpenguin>
(Nombre de usuario .github.io y luego el nombre del blog) las direcciones de github pages explican [aquí](wwww.google.com)

Todo el contenido de una github page, archivos HTML, imagenes, estarán en un repositorio de github (similar a tener los archivos en cualquier otro servicio de hosting para paginas web, solo que en este caso con jekyll todo el contenido de nuesto blog será público, se  podrá ver todo el contenido de nuestro blog dentro de su repo).

En resumen jekyll nos permite generar contenido estatico que subiremos a un repositorio que hace uso del servicio de hosting de las github pages.


## Caracteristicas principales que resaltan las razónes por las cuales he decidio migrar 

Con Jekyll he logrado migrar mi blog de wordpress gratuito <https://monsterpenguin.wordpress.com/> a <https://energy1011.github.io/monsterpenguin> y voy a hacer algunas comparaciones entre jekyll y wordpress, al final las dos son herramientas distintas que nos permiten crear blogs pero internamente funcionan diferente.

Características de jekyll:
- Hosting gratuito, así como también encontraremos themes y plugins libres.
- Utiliza markdown por default y podemos trabajar de manera offline al crear nuestras publicaciones.
- Es veloz por ser de contenido estatico y no utiliza base de datos.
- Flexible, costumizable, podemos agregar código Javascript.
- Usamos git y es muy portable.
- Dejamos todo el contenido accesible desde github, podemos clonar y hacer forks de otros blogs asi como otros pueden clonar y hacer forks del nuestro.

## Hosting gratuito


## Utiliza Markdown por default
La ventaja de que Jekyll tenga Markdown de manera nativa es fantastico, ya que de la misma manera que editamos los archivos README.md que ponemos dentro de nuestros proyectos de git y que subimos a github podemos elaborar nuestras publicaciones, jekyll se encarga de convertir los archivos .md en paginas html estaticas. 

En otra publicación anterior que hice sobre markdown [aquí](www.google.com) mencione la importancia y ventajas de utilizar este lenguaje de marcado de texto ligero, también explico cómo es que lo utilizo día a día para ayudarme a llevar las notas de lo que voy aprendiendo sobre informática, el hecho de que que mis apuntes de estudio ya esten en formato markdown me reduce el esfuerzo cuando los quiero convertir a una publicación para mi blog en jekyll. Y si fuese poco jekyll me permite trabajar de manera offline con markdown e ir viendo exactamente como va a lucir mi publicación ya publicada sin mayor esfuerzo.

## No utiliza base de datos 
Jekyll a diferencia de wordpress no utiliza base de datos ya que todo el contenido es previamente generado desde nuestros archivos markdown que esten dentro de nuestra carpeta *_posts* a archivos html estaticos para ser adquiridos desde la carpeta *_site*. Lo anterior nos demuestra que jekyll no necesita hacer consultas a una base de datos para obtener las publicaciones de nuestro blog, lo que hace es obtener el archivo html dentro de la carpeta *_site*, esto lo hace veloz comparandolo con wordpress.

Otra ventaja de no tener base de datos para nuestro blog es que nos despreocupamos por inyecciones SQL u otros tipos de ataques a la base de datos de nuestro sitio, ya que simplemente no cuenta con una.

## Flexible, podemos agregar código javascript en las publicaciones
Jekyll es totalmente flexible, todo el código de nuestro blog puede ser modificado, incluso podemos agregar código javascript, crear nuestros propies themes y plugins para modificar el comportamiento de nuestro sitio, cosa que con wordpress.com en modo free no podemos lograr.

Si quisieramos por ejemplo agregar google analytics para ver las estadisticas de visitas en nuestro blog o implementar un buscador de publicaciones en jekyll podemos lograrlo.

## Usamos Git y es muy portable

Tareas como realizar backups, exportar, importar publicaciones y llevar el control de versiones del blog es sencillo, la curva de aprendizaje de git puede asustar a la gente no familiarizada con git pero una vez dominado es una belleza. El utilizar git para llevar nuestro blog nos ayuda a darle un seguimiento profesional a nuestro blog, podemos llevar el control de cambios de una manera muy precisa. Todos los archivos de nuestro blog podemos tenerlos online en el repo de github donde se ha desplegado y tambien de manera local haciendo un *git clone* desde cualquier lugar, ya que es muy comodo que nuestro blog sea un repositorio, algo que se puede lograr con wordpress pero no de manera tan sencilla por tener una base de datos, archivo config, mediafiles que se debe de llevar bien sincronizada con git.


## Caracteristicas de wordpress en las que me he basado para migrar a jekyll
Caractereisticas de Wordpress.com (sin hosting propio):
- Hosting en modo gratuito y premium (en modo gratuito no se pueden instalar plugins y no podemos meterle mano al código al mismo nivel que se puede lograr con jekyll).
- Para utilizar markdown necesitamos utilizar un plugin (es posible trabajarlo de manera offline desde la app o bien montando todo el entorno local con  base de datos, servidor web etc).
- Utiliza si o si base de datos.
- En el servicio wordpress.com modo gratuito no podemos agregar código javascript.
- Es posible usar git para wordpress en nuestro backup local (pero no tan sencillo como con jekyll, los que han usado git con wordpress para desarrollo en modo local saben de lo que hablo [WordPress-Git Red Flags](https://premium.wpmudev.org/blog/git-for-wordpress-development/?ptm=c&utm_expid=3606929-108.O6f5ypXuTg-XPCV9sY1yrw.2&utm_referrer=https%3A%2F%2Fwww.google.com.mx%2F)).

- El contenido (publicaciones) quedan dentro de una base de datos en el hosting de wordpress o en nuestro hosting privado.

## Pasos para la migración
Lo primero que tenemos que hacer para realizar la migración es 
En la terminal:
{% highlight bash linenos %}
$ gem install jekyll-import
$ gem install hpricot
$ gem install open_uri_redirections
{% endhighlight %}

{% highlight bash linenos %}
$ ruby -rubygems -e 'require "jekyll-import";
JekyllImport::Importers::WordpressDotCom.run({
"source" => "wordpress.xml",
"no_fetch_images" => false,
"assets_folder" => "assets"})'
{% endhighlight %}

### Resumen
Jekyll es una muy buena opción para todas las personas que quieran tener un blog gratuito, flexible, ligero y además vinculado con su cuenta de github.
