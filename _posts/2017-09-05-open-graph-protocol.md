---
layout: post
title: 'Open graph protocol'
date: 2017-09-05 02:30:00 -06:00
type: post
published: true 
status: publish
categories: [web, blog]
tags: [html, protocol]
meta:
author: "Energy1011"
image: "logo-open-graph-protocol.png"

---

En esta ocasión quiero hablarles del Open Graph Protocol, abreviado simplemente como OG u OGP, este protocolo nos permite ofrecer información adicional al compartir contenido como web/enlaces en chats o en redes sociales que implementen este protocolo. OG esta basado en [RDFa](https://es.wikipedia.org/wiki/RDFa) y es por eso que hace uso de las [meta tag HTML](https://es.wikipedia.org/wiki/Etiqueta_meta) con (meta tags) me refiero a las etiquetas HTML que van dentro del encabezado, como la siguiente:
```html
<head>
 <meta property="og:image" content="http://una-direccion-de-ejemplo.com/mi-imagen-principal.png">
</head>
``` 
Como podemos observar en la meta tag anterior el atributo **property** tiene una notación haciendo referencia al protocolo OG con **'og:image'**. La meta tag del ejemplo anterior indica que la imagen principal para el preview es: mi-imagen-principal.png y es la que será mostrada en el preview al compartir en cualquier medio social que sorporte e implemente el OG.

OG nos permite mostrar previews como estos:
[imagen]

Las meta tag con OG ofrecen datos extra a servicios y aplicaciones de manera "oculta" (detras de bambalinas) dentro del código de una pagina web, estos datos en conjunto son información llamada o reconocida como **Social Object**.

Si alguna vez te preguntaste cómo servicios como facebook, twitter, g+, [telegram](https://es.wikipedia.org/wiki/Telegram_Messenger), etc, generan una vista previa del contenido, la respuesta es que **lo hacen por medio de OG**, y toda esta información es tratada como un objeto social. __**Personalmente no estoy de acuerdo con las redes sociales cerradas y [aquí](redes) hablo al respecto**__. Hay que tomar en cuenta que protocolo OG es implementado en multitud de servicios no solos las redes cerradas y vale la pena saber como funciona.

Las etiquetas de un objeto social OG basicas son 4:  
- **og:title** Titulo del enlace o publicación a mostrar en el preview.
- **og:type** El tipo de objeto compartido, puede ser: website, article, book, profile.
- **og:description** Texto que se toma de la publicación para describir su contenido, regularme son las primeras palabras del primer parrafo del contenido del enlace.
- **og:image** Imagen principal a mostrar en el preview, comunmente la imagen de encabezado de un artículo o logo de la página.

Existen otros atributos/tags que el OG toma en cuenta y podemos obtener más información [aquí](http://ogp.me/).
En el caso de twitter maneja una notación no estandar y única para su servicio, info [aquí](https://dev.twitter.com/cards/getting-started).

## OG en Jekyll
Ahora que he migrado mi blog a jekyll, me di cuenta que el template en el que me base no tenia una construcción completa de estas meta tags con OG y al parecer muchos repos que sirven para iniciar un blog con jekyll no tienen el código completo necesario para generar las meta tags compatibles con OG, y entonces noté que mis publicaciones en los distintos medios sociales, libres y no libres implementan este protocolo y los previews de mis publicaciones no eran mostrados correctamente y estaban incompletos, pueden revisar como es que he generado estas meta tags para mi blog [aquí](https://github.com/Energy1011/monsterpenguin/blob/master/_includes/head.html), es html con [liquid](https://shopify.github.io/liquid/).

Las meta tags para twitter tendrían que verse algo parecido a esto:
```html
<meta name="twitter:card" content="summary" />
<meta name="twitter:site" content="@flickr" />
<meta name="twitter:title" content="Small Island Developing States Photo Submission" />
<meta name="twitter:description" content="View the album on Flickr." />
<meta name="twitter:image" content="https://farm6.staticflickr.com/5510/14338202952_93595258ff_z.jpg" />

```
El atributo content tiene que ser propio del sitio.

Hay herramientas como [twitter validator](https://cards-dev.twitter.com/validator) para validar como se previsualizaran las OG, ellos al preview la llaman card. Facebook cuenta con validador similar, en lo personal prefiero verificar los previews con el cliente desktop de telegram.

Por ultimo puedes revisar el código fuente de esta página y ver el resultado final de las meta tags con OG. 

Meta tag generadas por esta publicación, puedes verificarlo viendo su código fuente:
```html
<meta content="Monster Penguin" property="og:site_name">
<meta content="Open graph protocol" property="og:title">
<meta content="article" property="og:type">
<meta property="og:description" content="En esta ocasión quiero hablarles del Open Graph Protocol, abreviado simplemente como OG u OGP, este protocolo nos permite ofrecer información adicional al co...">
<meta property="og:image" content="https://energy1011.github.io/monsterpenguin/assets/logo-open-graph-protocol.png">
<meta content="https://energy1011.github.io/linux/2017/09/05/open-graph-protocol.html" property="og:url">
```

Espero esta información sea útil, hasta la próxima.
