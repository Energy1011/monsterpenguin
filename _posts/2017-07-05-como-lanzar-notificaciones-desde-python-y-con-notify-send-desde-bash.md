---
layout: post
title: Cómo lanzar notificaciones desde python y con notify-send desde bash
date: 2017-07-05 14:11:46.000000000 -05:00
categories: [post, tutorial]
author: "Energy1011" 
tags: [python]
image: "logo-python.png"

---
Algunas veces necesitamos que nuestros scripts en GNU/Linux puedan generar notificaciones de escritorio, esto es muy útil cuando el proceso que se está realizando en nuestro script puede llevarnos un tiempo de espera prolongado o variable, así  que podríamos aprovechar ese tiempo perdido realizando otras labores con otros programas y recibir la notificación visual para luego regresar a nuestro script, y ahí es cuando es bastante interesante poder generar una notificación visual.

Generar una notificación es sencillo, en unos minutos buscando por internet rápidamente encontré la solución y comparto con ustedes los siguientes dos ejemplos en los lenguajes que en lo personal me parece que más comúnmente se puede requerir una notificación de este tipo (python y bash).

Generar una notificación con python:
{% highlight python linenos %}
import gi
gi.require_version('Notify', '0.7')
from gi.repository import Notify
Notify.init("test")
Notify.Notification.new("Hello friend, from python").show()
{% endhighlight %}

Este script en python hace uso de la [libnotify](https://developer.gnome.org/libnotify) del sistema, también existe un programa llamado **notify-send** que está escrito en lenguaje C, que nos permite enviarle al sistema las notificaciones que queremos mostrar; Para hacer uso de notifiy-send es necesario instalarlo primero en nuestro sistema:

{% highlight bash linenos %}
sudo apt-get install libnotify-bin
{% endhighlight %}

Ahora con nuestro notify-disponible en el sistema podemos crear una notificación desde bash de la siguiente manera:

{% highlight bash linenos %}
#!/bin/bash
notify-send "Hello Friend, from bash"";
{% endhighlight %}
¿ Muy sencillo, verdad ?

Quiero mencionar que he probado los dos ejemplos anteriores con i3wn (que no es un entorno de escritorio como tal, sino un gestor de ventanas) y me van de maravilla.
Para mayor información acerca del uso de notify-send podemos ver su manual:

{% highlight bash linenos %}
$ man notify-send
{% endhighlight %}
Enseguida dejo los enlaces y recursos de interés, por si desean indagar más en el tema :
- <https://wiki.archlinux.org/index.php/Desktop_notifications>
- <http://www.devdungeon.com/content/desktop-notifications-python-libnotify>
