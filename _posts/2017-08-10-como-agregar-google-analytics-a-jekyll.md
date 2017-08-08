---
layout: post
title: Cómo agregar google analytics a jekyll
date: 2017-08-10 14:01:35 -06:00
type: post
published: false 
categories: git
tags: git
author: "Energy1011" 
image: "logo-analytics.png"
---

## Pasos para implementar google analytics en jekyll
Google analytics es un servicio de google que nos permite verificar el trafico de cualquier web, en este caso haremos seguimiento de nuestro blog en jekyll, no solo de una pagina sino de cualquiera de las paginas de nuestro blog. Jekyll no cuenta con un mecanismo built-in o por default para darnos información acerca de los visitantes de nuestro blog, es por ello que este pequeño tutorial pretendo mostrar los pasos para implementar google analytics dentro de jekyll.


### Paso 1: Crear una cuenta
Lo primero que tenemos que hacer es crear una cuenta de google analytics y dar de alta nuestro sitio dentro del panel de control de google analytics.

En la siguiente dirección podemos crear una cuenta y acceder al panel de control del servicio
<https://www.google.com/intl/es/analytics/> .

Dentro de nuestra cuenta de analytics vamos al apartado de crear cuenta (de siguimiento a un sitio web) y llenamos el formulario:

![Google analytics crear cuenta de seguimiento](/monsterpenguin/assets/ga-crear-cuenta.jpg)

Cuando hemos terminado de llenar el formulario, analytics nos va a dar un código en javascript como el siguiente:

![Google analytics código de seguimiento](/monsterpenguin/assets/ga-script-seguimiento.jpg)

### Paso 2: Agregar el script se seguimiento a nuestro jekyll

Vamos a crear un archivo nuevo **analytics.html** en nuestro jekyll en **\_includes/analytics.html** en este archivo **analytics.html** agregaremos todo el código que está dentro de la etiqueta \<script\> que google analytics nos ha generado al crear la cuenta de seguimiento.

El contenido del archivo analytics.html que acabamos de crear sería algo similar a esto:

```html
<script>
(function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
(i[r].q=i[r].q||[]).push(arguments)
},i[r].l=1*new Date();a=s.createElement(o),
m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
})(window,document,'script','//www.google-analytics.com/analytics.js','ga');
ga('create', 'UA-XXXXXXXX-X', 'auto');
ga('send', 'pageview');
</script>
```
Donde **UA-XXXXXXXX-X** es tu ID de seguimiento.

### Paso 3: Incluir el archivo analytics.html en nuestro layout
Para que google analytics pueda dar seguimiento a todas nuestras paginas de nuestro blog vamos a necesitar incluir nuestro archivo analytics.html en _layouts/default.html ya que el archivo default.html es cargado en todas nuestras paginas de manera automatica.

Para incluir un archivo con etiquetas liquid en jekyll para incluir un archivo basta con la siguiente linea de código:
```liquid
{{ "{% include archivo-a-incluir.html " }}%}
```
El archivo _layouts/default.html de lucir algo parecido a lo siguiente
```liquid
<body>
	...
	...
	{{ "{% if jekyll.environment == 'production' " }}%}
		{{ "{% include analytics.html " }}%}
	{{ "{% endif "}}%}
</body>
</html>
```

Con las 3 lineas de liquid anteriores vamos a comprobar si jekyll se encuentra en modo production, si esto es verdad entonces se va a incluir el archivo analytics.html de caso contrario no tendremos el código incluido, esto se hace para evitar que google analytics nos realice un seguimiento en modo desarrollo o cuando estamos escribiendo una publicación en modo local.

la variable de entorno que jekyll verifica en este caso es JEKYLL_ENV, si queremos poner a jekyll en modo production bastaria desde nuestra terminal darle el valor "production" de la siguiente manera

```bash 
$ JEKYLL_ENV=production 
``` 
### Paso 4: Realizar un build
Finalmente para que los pasos anteriores surtan efecto hay que realizar un
```bash 
$ jekyll build
```
Con el comando anterior jekyll va a generar todo el contenido estatico de nuestro blog con google analytics funcionando; Analytics alguna veces tiene una demora para mostrar los datos, en mi caso tuve que esperar aprox 12 horas para notar las visitas a mi blog. Hasta aquí con este tutorial, hasta la proxima.
