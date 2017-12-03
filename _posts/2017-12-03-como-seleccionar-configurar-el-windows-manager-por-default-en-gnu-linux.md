---
layout: post
title: "Cómo seleccionar el windows manager por default para tu GNU/Linux"
date: 2017-12-03 09:36:53 -06:00
type: post
published: true
status: publish
categories: [i3,awesome,window manager,gnu,linux]
tags: [i3,awesome,window manager,gnu linux]
author: "Energy1011"
image: "window-manager.png"
---

## ¿ Qué es un window manager ?
Los window manager (gestores de ventanas) son una parte fundamental en los sistemas para la implementación de cualquier GUI con múltiples ventanas, ya que se encargan a manera general, de organizar y decorar las ventanas, en GNU/Linux tenemos la posibilidad de cambiar el gestor de ventanas que más nos guste, esta es solo una de la multitud de ventajas de GNU/Linux; En comparación de otros sistemas operativos por ejemplo: (windows, mac osx) que tienen un gestor de ventanas instalado por default y olvidate de tener la libertad de cambiarlo, algo que se logra con facilidad en GNU/Linux.

En el siguiente enlace tenemos un [listado de 21 gestores de ventanas para GNU/Linux](https://www.emezeta.com/articulos/21-gestores-ventanas-gnu-linux).

En lo personal mi gestor de ventanas favorito es [i3-wm](https://i3wm.org/) y puede ser instalado y ejecutado de manera independiente al [Desktop enviroment](https://es.wikipedia.org/wiki/Entorno_de_escritorio), con esto me refiero a que con solo i3-wm podemos usar nuestro sistema GNU/Linux sin necesidad de cargar en memoria y correr un __Desktop enviroment (completo)__. Brevemente menciono solo algunas de las ventajas de i3-wm :

- Es ligero
- Se instala con un solo comando:
```bash
$ apt install i3
 ```
- Es independiente al desktop enviroment, esto ahorra bastante memoria RAM.
- Veloz, es un gestor de ventanas orientado a utilizar el mouse lo menos posible.

Estas son solo algunas de las ventajas que tiene [i3-wm](https://i3wm.org/), y en su [sitio oficial](https://i3wm.org/) podemos obtener toda la información

## Cómo seleccionar el window manager por default
Para lograr cambiar el window manager por default basta correr el siguiente comando en la terminal:
```bash
$ sudo update-alternatives --config x-window-manager
```

Al lanzar el comando anterior obtendremos la lista de window managers instalados y disponibles en nuestro sistema:
```
There are 3 choices for the alternative x-window-manager (providing /usr/bin/x-window-manager).

  Selection    Path              Priority   Status
------------------------------------------------------------
  0            /usr/bin/mutter    60        auto mode
  1            /usr/bin/awesome   20        manual mode
* 2            /usr/bin/i3        20        manual mode
  3            /usr/bin/mutter    60        manual mode

Press <enter> to keep the current choice[*], or type selection number:
```

Para finalizar solo hace falta teclear el número de 'Selection' del window manager a definir por default, que en mi caso es i3 en la opción 2. De esta manera tan sencilla podemos seleccionar el window manager por default, espero está información sea útil, hasta la próxima.

