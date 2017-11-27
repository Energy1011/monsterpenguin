---
layout: post
title: "Script para crear post en jekyll"
date: 2017-11-26 19:44:48 -06:00
type: post
published: true
status: publish
categories: [jekyll, scripts]
tags: [jekyll, create post, scripts]
author: "Energy1011"
image: "screen-jekyll-tool-1.png"
---

En esta ocasión les traigo un pequeño aporte, __un [script](https://github.com/Energy1011/jekyll-tool-sh) para inicializar posts en [Jekyll](https://jekyllrb.com/)__, los programadores tenemos la costumbre de tratar de automatizar todo, esta no es la excepción y me ha parecido buena idea crear un script para esta tarea. Quiero extender el script con otras funcionalidades, pero por el momento ayudará a inicializar los posts de manera más "interactiva". Aunque no lo parezca con este tipo de scripts podemos ahorrarnos bastante tiempo de post en post.

> El tiempo es el recurso más valioso.

Si bien sabemos, para crear un nuevo post en jekyll es necesario crear un archivo con un nombre como el siguiente:
```
_post/2017-11-26-título-de-mi-post.md
```
En el que el archivo tiene que empezar con una fecha en el formato: __año-mes-día__, seguido del título del post en formato markdown. Bien, este archivo debe de estar dentro de la carpeta __post__ esto es necesario para que jekyll lo reconozca como un post y genere el HTML estático dentro de __site__ cuando lanzamos el comando:
```bash
$ jekyll serve
```
Al crear este archivo su primer contenido de cabecera [Front Matter](https://jekyllrb.com/docs/frontmatter/), tiene que ser algo parecido a lo siguiente en formato YAML:
```YAML
---
layout: post
title: "Script para crear post en jekyll"
date: 2017-11-26 19:44:48 -06:00
type: post
published: true
status: publish
categories: [jekyll, scripts]
tags: [jekyll, create post, scripts]
author: "Energy1011"
image: "screen-jekyll-tool-1.png"
---
```
Este Front Matter YAML lo he generado desde mi script que he llamado __[jekyll-tool-sh](https://github.com/Energy1011/jekyll-tool-sh)__ (No me rompí la cabeza pensando en un nombre xD) este script que he realizado lo comparto con todos ustedes en mi [github aquí](https://github.com/Energy1011/jekyll-tool-sh), su función principal por ahora es ahorrarnos el tiempo de copiar el front matter de otros post para después editarlo y lo más importante es que nos lleva de manera interactiva a crearlo como se muestra a continuación:


![Jekyll-tool screenshot 1](/monsterpenguin/assets/screen-jekyll-tool-1.png)

El script se encarga de crear el archivo para el post, nombrandolo con el formato correcto, y para lanzar el script basta con lanzar el siguiente comando:
```bash
$./jekyll-tool -c "título de mi post"
```

La opción '-c' le dice al script que tiene que crear un nuevo post, cuando el script se corre por primera vez nos preguntará datos como:
- Author
- Path completo de nuestra carpeta __post__ para que el script sepa donde inicializarlo.

Los datos anteriores se guardan en un archivo de configuración como un [.dotfile]() localizado en __~/.jekyll-tool__. 

La opción _-h_ nos muestra información sobre el _usage_.

El script desde luego tiene licencia GPL, sugerencias de cambios o nuevas funcionalidades y pull request son bien recibidos, ya que el script está muy simple, por el momento este es mi pequeño aporte para todos ustedes, hasta la próxima.

