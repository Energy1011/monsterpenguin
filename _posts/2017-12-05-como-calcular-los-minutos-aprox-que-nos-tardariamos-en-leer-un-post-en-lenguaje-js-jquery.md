---
layout: post
title: "Cómo calcular los minutos aprox que nos tardariamos en leer un post, código en js y jquery"
date: 2017-12-05 11:13:20 -06:00
type: post
published: true
status: publish
categories: [tutorial]
tags: [javascript]
author: "Energy1011"
image: "time-death.png"
---

El tiempo, un tema complicado de abordar filosóficamente hablando, el tiempo como recurso utilizable me parece que es mayormente y mayoritariamente importante para los seres orgánicos con raciocinio en estos días, y con esto recuerdo la frase que dice: __el tiempo vale oro__, o dicho de otra manera __el tiempo vale vida__.

Reflexionando sobre el tiempo, quise hacer un código sencillo, _nada de código extremadamente preciso_, pero sirve para aproximar el tiempo que te tardarías en leer un post en este blog, __debajo del título de este post tendrías que poder ver ahora mismo el calculo aprox en minutos que te tardarías en leer este post__.

El código que hice es el siguiente y te lo comparto:

```javascript
<script>
    // Calculate WPM inside <p> and <code> elements
    function calculate_wpm(){
        words = '';
        $('.post-content p').each(function(i){
            words += $(this).text();
        });
        $('code').each(function(i){
            words += $(this).text();
        });
        msg = "Este post te llevará aprox "+ (words.split(" ").length/155).toFixed(0) + " minutos de lectura a 155 PPM.";
        $('#time-to-read').append(msg);
    }
// On document ready
$(document).ready(function(){
    calculate_wpm();
});

</script>
```

El código anterior es simple, cuando la página ha cargado el DOM y está listo __$(document).ready__ llamo a la función para calcular WPM (Words per minute) que lo que hace es inicializar un string vacío, donde se concatenan posteriormente todo el contenido (texto) de los párrafos y los bloques de código que son hijos de la clase css post-content, para que con todas las palabras dentro de __words__ concatenadas hacer un split por espacios para sacar el length y saber cuántas palabras existen para poder hacer la aproximación.

Lo único que faltaría con el código anterior es agregar el elemento con el ID #time-to-read en el lugar del HTML donde queremos mostrar el mensaje, indicándonos el tiempo que tardaremos si leemos a una velocidad promedio de 155 PPM.
```html
<p><span id="#time-to-read"></span></p>
```

He tomado como referencia 155 PPM, ya que según estudios realizados es una velocidad promedio para un joven que ha sobrepasado la educación primaria, puedes copiar y ajustar el código a tu gusto.

El código para que funcione en este blog, lo he incluido en el archivo __layouts/post.html__

Para despedirme en esta ocasión... como un compañero decía a manera de broma: __No les robo más mi tiempo__, jaja , hasta la proxima.

