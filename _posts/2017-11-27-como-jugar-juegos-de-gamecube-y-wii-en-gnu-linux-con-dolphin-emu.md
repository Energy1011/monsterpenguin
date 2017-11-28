---
layout: post
title: "Cómo jugar juegos de Gamecube y Wii en GNU/Linux con Dolphin-emu"
date: 2017-11-27 14:11:30 -06:00
type: post
published: true
status: publish
categories: [games, linux, tutorial]
tags: [gamecube, wii, linux, emulator, screeencast]
author: "Energy1011"
image: "logo-dolphin-emu.png"
---
El siguiente post cuenta con un screencast (video tutorial):
<iframe width="560" height="315" src="https://www.youtube.com/embed/b24uxWMa0g4" frameborder="0" gesture="media" allowfullscreen></iframe>

Este post lo he podido elaborar gracias a un amigo, que me ha animado y despertado nuevamente la curiosidad de emular juegos en GNU/Linux y me ha compartido la lista de comandos y dependencias necesarias para la instalación de dos emuladores: __Dolphin y PPSSPP__, en este post pretendo compartir y guardar los pasos a seguir para la instalación de __Dolphin__.

*El emulador para juegos de __PSP__ llamado __PPSSPP__ lo dejaré para el próximo post.*

Para los que piensan a estas alturas que GNU/Linux es aburrido o que es un sistema donde no se puede jugar, adivinen que... este post demuestra lo contrario, ya que una vez instalado Dolphin-emu podremos disfrutar de juegos de GameCube y Wii en nuestra computadora :)

Para los que no conocen Dolphin, este es un emulador open-source para Nintendo GameCube y Wii (además tenemos compatibilidad con [VC](https://wiki.dolphin-emu.org/index.php?title=Virtual_Console) en la [Dolphin Wiki](https://wiki.dolphin-emu.org/index.php?title=Main_Page) podemos ver la __Compability list__ en el menú izq).
Dolphin puede ser instalado en Android, Linux, Mac OS X y Windows. Dolphin fue el primer emulador en arrancar juegos de GameCube y Wii, teniendo ahora gran compatibilidad con la mayoría de títulos de estas dos consolas. Con una gran comunidad de desarrolladores y usuarios alrededor del mundo Dolphin continúa ganando compatibilidad, performance y nuevas funcionalidades, al día de hoy Dolphin-Emu se encuentra en su versión 5.

<div style="position:relative;height:0;padding-bottom:56.25%"><iframe src="https://www.youtube.com/embed/KS7Fl30JZcA?ecver=2" width="640" height="360" frameborder="0" gesture="media" style="position:absolute;width:100%;height:100%;left:0" allowfullscreen></iframe></div>

Antes de comenzar con la instalación, les recuerdo que podemos apoyarnos e instalar Dolphin siguiendo las [instrucciones](https://wiki.dolphin-emu.org/index.php?title=Installing_Dolphin) y la descarga del sitio oficial en su sección de descargas [aquí](https://es.dolphin-emu.org/download/). El método que mostraré a continuación es por medio de un script que descarga y compila el código fuente en su última versión estable.

## __Paso 1:__ Instalando las dependencias de Dolphin
Para distribuciones basadas en Debian, lo primero que haremos será instalar las dependencias de Dolphin con __apt install__ para tener dolphin funcionando en nuestro sistema:
```bash
$ apt install pkg-config gcc libwxbase3.0-dev libwxgtk3.0-dev libgtk2.0-dev libxext-dev libreadline-dev libgl1-mesa-dev libevdev-dev libudev-dev cmake qtbase5-private-dev
```

La instalación para usuarios de Ubuntu es simple y en la guia oficial cuentan con un PPA para la instalación con los siguientes comandos:
```bash
$ sudo apt-add-repository ppa:dolphin-emu/ppa
$ sudo apt update
$ sudo apt install dolphin-emu
```

## __Paso 2:__ Descargar y ejecutar el script de instalación
Para instalar Dolphin desde el código fuente, tenemos un script que lo que hace es descargar el código fuente del repo oficial de Dolphin, compilarlo e instalarlo, este script lo he colgado en mi Github, entonces hacemos lo siguiente:

*Clonamos el script que comenzará a descargar, compilar e instalar Dolphin*
```bash
$ git clone https://github.com/Energy1011/dolphin-emu-installer-sh.git
```

*Entramos a la carpeta del repo clonado y damos permisos al script de ejecución*
```bash
$ cd dolphin-emu-installer-sh && chmod +x dolphin-installer.sh
```

*Ejecutamos el script instalador*
```bash
$ ./dolphin-installer.sh
```

Ahora solo esperamos que el script descargue, compile e instale Dolphin, el tiempo de espera puede variar entre computadoras en la descarga y el proceso de compilación suele tardar, pero una vez finalizado tendremos nuestro Dolphin funcionando y listo para correr los ROMS.

## ¿ Dolphin soporta controles ?
Claro que se pueden usar controles usb y bluetooth, incluso he conectado controles de PSP3 a GNU/Linux en otros emuladores, mi amigo también acaba de enlazar su nuevo control de nintendo switch a su pc con emuladores, pronto haré un tutorial sobre controles.

## ¿ Donde descargamos ROMS ?
Los Roms e ISOs son las imágenes de juegos que podemos descargar y correr en nuestros emuladores, haría falta hacer una búsqueda en tu motor de búsqueda favorito para encontrar diferentes sitios de descarga de juegos, por ejemplo: [https://www.emuparadise.me/](https://www.emuparadise.me/)

## Recomendaciones y aclaraciones
Este es un método de instalar Dolphin, existen desde luego otras maneras, de hecho este método lo he realizado sobre una distribución Kali, que si bien funciona, esta no pretende ser una distribución en la que se suelen correr emuladores para juegos por el tema del __root user__ por default y es necesario y recomendado crear un usuario estándar, pero aun así se demuestra la versatilidad de GNU/Linux como sistema.

Para usuarios de otros sistemas como Windows y Mac tienen los compilados en el sitio oficial en el apartado de descargas de esa página.

Y para los usuarios de otras distros como Arch, Ubuntu, Fedora pueden visitar el siguiente [enlace](https://wiki.dolphin-emu.org/index.php?title=Installing_Dolphin) con la guia oficial de instalación de Dolphin.

Finalmente, espero que disfruten jugar videojuegos por medio de emuladores tanto como yo en su sistema favorito; Antes de terminar el post quiero agradecer a todos los desarrolladores y usuarios que hacen que estos emuladores funcionen, dandonos tantas horas de diversión, incluso de tambien hasta felicidad/nostalgia en el caso de los juegos retros corriendo en nuestros ordenadores, hasta la próxima.


