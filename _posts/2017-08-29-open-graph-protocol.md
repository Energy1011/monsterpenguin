---
layout: post
title: 'Open graph protocol'
date: 2017-08-27 01:00:07 -06:00
type: post
published: false 
status: publish
categories: [linux]
tags: [linux, bash, apt]
meta:
author: "Energy1011"
image: "logo-open-graph-protocol.png"

---

En esta ocasión quiero hablarles del Open Graph Protocol abreviado simplemente como OG u OGP, este protocolo nos permite ofrecer información adicional al compartir contenido como web/enlaces en chats o en redes sociales, que implementen este protocolo. OG esta basado en [RDFa](https://es.wikipedia.org/wiki/RDFa) y es por eso que hace uso de las [meta tag HTML](https://es.wikipedia.org/wiki/Etiqueta_meta) con (meta tags) me refiero a las etiquetas HTML que van dentro del encabezado, como la siguiente:
```html
<head>
 <meta property="og:image" content="http://una-direccion-de-ejemplo.com/mi-imagen-principal.png">
</head>
``` 
Como podemos observar en la meta tag anterior el atributo **property** tiene una notación haciendo referencia al protocolo OG con **'og:image'**. La meta tag del ejemplo anterior indica que la imagen principal para el preview es: mi-imagen-principal.png y es la que será mostrada en el preview al compartir en cualquier medio social que sorporte e implemente el OG.

OG nos permite mostrar previews como estos:
[imagen]

Las meta tag con OG ofrecen datos extra a servicios y aplicaciones de manera "oculta" (detras de bambalinas) dentro del código de una pagina web, estos datos en conjunto son información llamada o reconocida como **Social Object**.

Si alguna vez te preguntaste cómo servicios como facebook, twitter, g+, [telegram](https://es.wikipedia.org/wiki/Telegram_Messenger), etc, generan una vista previa del contenido, pues lo hacen por medio de OG, y toda esta información es tratada como un objeto social. __**Personalmente no estoy de acuerdo con las redes sociales cerradas y [aquí](redes) hablo al respecto**__. Hay que tomar en cuenta que protocolo OG es implementado en multitud de servicios no solos las redes cerradas y vale la pena saber como funciona.

Las etiquetas de un objeto social OG basicas son 4:  
- **og:title** Titulo del enlace o publicación a mostrar en el preview.
- **og:type** El tipo de objeto compartido)
- **og:description** Texto que se toma de la publicación, para describir su contenido, este pueden ser las primeras palabras del primer parrafo del contenido del enlace.
- **og:image** Imagen principal a mostrar en el preview, comunmente la imagen de encabezado de un artitulo o logo de la pagina.

Existen otros atributos/tags que el OG toma en cuenta y podemos obtener más información [aquí](http://ogp.me/).
En el caso de twitter maneja una notación no estandar y única para su servicio, info [aquí]().

## OG en Jekyll
Ahora que he migrado mi blog a jekyll, me di cuenta que el template en el que me base no tenia una construcción de estas meta tags con OG y al parecer muchos repos que sirven para iniciar un blog con jekyll no tienen el código completo necesario para generar estás meta tags compatibles con OG, y entonces noté que mis publicaciones en los distintos medios sociales, libres y no libres implementan este protocolo y los previews de mis publicaciones no eran mostrados correctamente y estaban incompletos, pueden revisar como es que he generado estas meta tags para mi blog [aquí](https://github.com/Energy1011/monsterpenguin/blob/master/_includes/head.html), es html con [liquid](https://shopify.github.io/liquid/).

Twitter cuenta con su propio manejo con etiquetas, ejemplo:
```html
<meta name="twitter:card" content="summary" />
<meta name="twitter:site" content="@flickr" />
<meta name="twitter:title" content="Small Island Developing States Photo Submission" />
<meta name="twitter:description" content="View the album on Flickr." />
<meta name="twitter:image" content="https://farm6.staticflickr.com/5510/14338202952_93595258ff_z.jpg" />

```
Hay herramientas como [Twitter validator](https://cards-dev.twitter.com/validator) para validar como se previsualizaran las OG, ellos al preview la llaman card. Facebook cuenta con validador similar, en lo personal prefiero verificar los previews con el cliente desktop de Telegram (siempre tendre preferencia por lo que me ofrezca más libertad y se apague lo más posible a la filosofía de software libre).

Por ultimo puedes revisar el código fuente de esta pagina y ver el resultado final de las meta tags con OG. 

Meta tag generadas por esta publicación:
```html
**code**
```
Espero esta información sea útil, hasta la próxima.
