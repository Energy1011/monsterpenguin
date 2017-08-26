---
layout: post
title: 'Mpsyst - youtube en la terminal'
date: 2017-08-26 00:00:07.000000000 -06:00
type: post
published: true
status: publish
categories: [linux]
tags: [linux, bash, terminal, youtube, music]
meta:
author: "Energy1011"
image: "screen-mpsyt.png"

---

En lo personal encuentro mayor comodidad, simpleza y velocidad el realizar varias tareas en la terminal que se realizan habitualmente con programas con interfaz gráfica [GUI](https://es.wikipedia.org/wiki/Interfaz_gr%C3%A1fica_de_usuario), muchos usuarios piensan que usar la terminal no es para ellos porque creen que la terminal es complicada de aprender, este punto puede llegar a ser muy subjetivo, y solo diré que:

> Si te predispones a que algo es difícil de aprender o lograr, porque nunca lo haz hecho o porque es diferente a lo que estás acostumbrado a hacer, eso es lo que será: **difícil para ti**.

Una vez que se le agarra un poco el hilo a la terminal, la línea de comandos es fabulosa, poderosa y jamás querrás apartarte de ella, jaja ya sé: suena romántico, muchos me entenderán; Tareas como copiar-borrar-mover archivos o carpetas desde la terminal puede llegar a parecer trivial para muchos que ya se mueven en la terminal como peces en el agua, pero realizar conexiones ssh, abrir tu editor favorito dentro de la terminal como vim y programar en tus lenguajes favoritos, instalar programas adicionales o plugins, lanzar scripts, controlar servicios y daemons, dominar el lenguaje y sintaxis de bash, ksh, csh, tener a disposición y saber usar infinidad de comandos que cumplen la [Filosofía Unix](https://en.wikipedia.org/wiki/Unix_philosophy) comunicandose entre si por medio de pipes, son cosas que por supuesto no llegan a ser triviales para la mayoría, estas son tareas que con practica se vuelven más sencillas pero requiere su tiempo y esfuerzo aprenderlas, pero qué hay de aquellas otras cosas que hacemos sin esfuerzo alguno como puede ser **reproducir música**, esta tarea no es algo que no podamos lograr dentro de la terminal con menor esfuerzo y algunas ventajas (como dije la terminal es poderosa y nos llega a facilitar las tareas menos inesperadas, las que creiamos que solo con programas con GUI se podían hacer), es por eso que después de esta introducción honorífica a la terminal, en esta ocasión quiero hablarles acerca de este programa mps-youtube (conocido también como mpsyt) un programa que nos va a permitir escuchar y descargar el audio de videos de youtube, incluso abrir el video con un reproductor, todo esto desde la terminal:

Las características de mps-youtube son:
- Búsqueda y reproducción de audio/video de youtube
- Búsqueda de canciones de álbumes por título del álbum
- Búsqueda e importación de playlist de youtube
- Crear y guardar playlist locales
- Descargar audio/video
- Conversión a mp3 y otros formatos (requiere ffmpeg y avconv)
- Ver los comentarios del video
- Funciona con Python 3.x
- Funciona con Windows, Linux and Mac OS X
- Requiere mplayer o mpv

Una característica importante que no mencionan "creo imaginarme el por qué" y que he notado es que al escuchar la música desde mps-youtube no pasan los anuncios molestos, pero shhh ;)

Hay que mencionar que este programa está basado en [mps](https://github.com/np1/mps) un programa para la terminal para stream y descarga de videos, en cambio mps-youtube es especializado para youtube utiliza el servicio de youtube como fuente directa.

Mps-youtube se instala con un solo comando y en su repo oficial nos indican cómo instalarlo de la siguiente manera:
```bash
$ sudo pip3 install mps-youtube
```

Una vez instalado lo lanzamos con:
```bash
$ mpsty
```
Para finalizar dejaré la sección help y algunos controles (shortcuts) para movernos dentro del programa.  

Al entrar en modo prompt o consola:  
  Help Topics  

  Enter help \<topic\> for specific help:  
  - basic      : Basics  
  - search     : Searching and Retrieving  
  - edit       : Editing / Manipulating Results  
  - download   : Downloading and Playback  
  - dl-command : Downloading Using External Application  
  - encode     : Encoding to MP3 and other formats  
  - playlists  : Using Local Playlists  
  - history    : Accessing Local History  
  - invoke     : Invocation Parameters  
  - config     : Configuration Options  
  - tips       : Advanced Tips  
  - new        : New Features  

En modo reproducción  
    [<] Track anterior  
    [>] Track siguiente  
    [9] y [0] Subir y bajar volumen  
    [q] retroceder (salir o volver al menú anterior)   
    [↓] [↑] Retroceder track y avanzar track  
    [space] pause

Internamente tengo entendido que mps-youtube utiliza youtube-dl y la gente de mps-youtube recomienda tenerlo instalado, youtube-dl es otra herramienta interesante de la cual muy probablemente hablaré en otra ocasión, hasta la próxima...
