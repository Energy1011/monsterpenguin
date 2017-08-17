---
layout: post
title: Cómo agregar Google Analytics a Jekyll
description: "Pasos para implementar google analytics en jekyll"
date: 2017-08-10 14:01:35 -06:00
type: post
published: true
categories: jekyll 
tags: jekyll 
author: "Energy1011"
image: "logo-g-analytics.png"

---

## Pasos para implementar google analytics en jekyll

Google analytics es un servicio de google que nos permite verificar el tráfico de cualquier web, en este caso haremos seguimiento de un  blog en jekyll, no solo de una página sino de cualquiera de las páginas del blog. Jekyll no cuenta con un mecanismo built-in o por default para darnos información acerca de los visitantes de nuestro blog, es por ello que este pequeño tutorial pretendo mostrar los pasos para implementar google analytics dentro de jekyll.

Los pasos que se muestran a continuación son básicamente lo mismo que se realiza en cualquier otro sitio para incluir google analytics, la esencia es obtener código javascript generado por google con un ID desde el panel de administración de google analytics e incluirlo en nuestro sitio; De esta manera google puede dar seguimiento a nuestro sitio, con un código javascript que envía reportes a google de los visitantes.

### Paso 1: Crear una cuenta
Lo primero es crear una cuenta de google analytics y dar de alta nuestro sitio dentro del panel de control de google analytics.

En la siguiente dirección podemos crear una cuenta y acceder al panel de control del servicio de analytics
<https://www.google.com/intl/es/analytics/> .

Dentro de nuestra cuenta de analytics vamos al apartado de crear cuenta (de seguimiento a un sitio web) y llenamos el formulario:

![Google analytics crear cuenta de seguimiento](/monsterpenguin/assets/ga-crear-cuenta.jpg)

Cuando hemos terminado de llenar el formulario, analytics nos va a dar un código javascript como se ve en la siguiente imagen:

![Google analytics código de seguimiento](/monsterpenguin/assets/ga-script-seguimiento.jpg)

### Paso 2: Agregar el script de seguimiento a nuestro jekyll

Vamos a crear un archivo nuevo **analytics.html** en nuestro jekyll y lo ubicamos en **\_includes/analytics.html** en este archivo **analytics.html** agregaremos todo el código que está dentro de la etiqueta \<script\> que google analytics nos ha generado al crear la cuenta de seguimiento.

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
Para que google analytics pueda dar seguimiento a todas nuestras páginas de nuestro blog vamos a necesitar incluir nuestro archivo **analytics.html** en **_layouts/default.html** ya que el archivo **default.html** es cargado en todas nuestras páginas de manera automática.

Para incluir el código que tenemos en **analytics.html** a jekyll basta con la siguiente línea de código de liquid (que es el lenguaje de templates que jekyll utiliza por default):
```liquid
{{ "{% include archivo-a-incluir.html " }}%}
```

El archivo **_layouts/default.html** debe lucir algo parecido a lo siguiente
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

Con las 3 líneas de liquid anteriores vamos a comprobar si jekyll se encuentra en modo production, si esto es verdad entonces se va a incluir el archivo **analytics.html** de caso contrario el código dentro de **analytics.html** no es incluido, esto lo hacemos  para evitar que google analytics nos realice un seguimiento en modo desarrollo o cuando estamos escribiendo una publicación en modo local.


```bash
$ JEKYLL_ENV=production
```

### Paso 4: Realizar un build
Finalmente para que los pasos anteriores funcionen hay que realizar un **build**
```bash
$ jekyll build
```
Con el comando anterior jekyll va a generar todo el contenido estático de nuestro blog con google analytics funcionando;

**Nota importante:** Analytics algunas veces tiene una demora para mostrar los resultados de los visitantes, en mi caso tuve que esperar aprox 12 horas para notar las visitas a mi blog (incluso con el visor en tiempo real empezó a funcionar después de 12 horas). Espero este pequeño tutorial les sea de utilidad, hasta la próxima.
