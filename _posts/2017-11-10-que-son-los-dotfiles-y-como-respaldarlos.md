---
layout: post
title: 'Qué son los dotfiles y cómo respaldarlos'
date: 2017-11-10 02:00:00 -06:00
type: post
published: false 
status: publish
categories: [linux, unix, blog]
tags: [dotfiles, unix]
meta:
author: "Energy1011"
image: ""

---

Hace poco más un mes que no escribia en el blog, pero aquí estoy de regreso con un tema básico para cualquier *nix user, los llamados Dotfiles (archivos de configuración ocultos). 

### ¿ Qué son los dotfiles ?

En sistemas unix-like, refiriendonos a los sistemas basados en unix, digamos: GNU/Linux, MAC OSX, FreeBSD, etc. Sistemas en los que si recordamos los archivos ocultos son definidos e identificados facilmente por comenzar con un punto (.) 'dot' en inglés, por ello en primera instancia ya sabemos que los dotfiles son archivos ocultos en nuestro sistema.

### ¿ Donde encuentro estos archivos y para que sirven ?

Es común que ciertos programas hagan uso de archivos dotfiles creandolos y poniendolos en algunas rutas del sistema para contener configuraciones.

Por mencionar un celebre dotfile tenemos que Vim (mi editor favorito para programar) crea y usa un archivo dotfile .vimrc por default para guardar algunas configuraciones que el usuario puede modificar y definir nuevas configuraciones e infinidad de cosas, los nombres y rutas de los archivos dotfiles pueden variar y ser modificados en los programas que hacen uso de ellos, aun así es importante mencionar que muchos archivos dotfiles tienen el posfijo 'rc' o 'config'.

El archivo .vimrc podemos encontrarlo en el directorio home del usuario ~/.vimrc en el que '~/' tilde-virgulilla-de-eñe y diagonal se refieren al directorio principal del usuario y .vimrc al archivo dotfile en si.

Dentro del archivo dotfile de vim podemos encontrar algo parecido a esto: 
"""vim
" URL: http://vim.wikia.com/wiki/Example_vimrc
" Authors: http://vim.wikia.com/wiki/Vim_on_Freenode
" Description: A minimal, but feature rich, example .vimrc. If you are a
"              newbie, basing your first .vimrc on this file is a good choice.
"              If you're a more advanced user, building your own .vimrc based
"              on this file is still a good idea.

"------------------------------------------------------------
" Features
"
" These options and commands enable some very useful features in Vim, that
" no user should have to live without.

" Set 'nocompatible' to ward off unexpected things that your distro might
" have made, as well as sanely reset options when re-sourcing .vimrc
set nocompatible

" Attempt to determine the type of a file based on its name and possibly its
" contents. Use this to allow intelligent auto-indenting for each filetype,
" and for plugins that are filetype specific.
filetype indent plugin on

" Enable syntax highlighting
syntax on
"""


### ¿ El contenido de los dotfiles tienen el mismo 'lenguaje' universal y/o estructura ?
No, el contenido de estos archivos, puede variar entre programas, es decir, cada programa define la sintaxis y como leer estos archivos, pero de eso no hay que preocuparnos, si siempre tenemos en mente que los archivos dotfiles a manera generica/universal buscan definir configuraciones y variables. Por ejemplo, añadiendo la siguiente linea al archivo .vimrc hacemos que vim siempre nos muestre los numeros de línea de un archivo dentro del editor:

"""vim
set number
"""

o también con :

"""vim
set nu
"""
Me encanta hablar de vim y mostrar el power que tiene oculto, pero seguir hablando más de vim y su archivo .vimrc va más allá del proposito pricipal de este post. Les prometo realizar una serie de tutoriales y screeencast sobre vim para todos los interesados en el tema.

Como dije, no hay que preocuparnos, la mayoria de programas que hacen hacen uso de los dotfiles tienen documentación disponible para explicarlos.

### Respaldando e "instalando" tus dotfiles
Los dotfiles pueden contener muchas configuración muy especificas del usuario, la cantidad de dotfiles dependera de la cantidad de programas que el usuario tenga y que estos programas por supuesto implementen estos archivos, en lo personal me preocupo por respaldar dotfiles de los siguientes programas:

bash (~/.bashrc bash shell)
i3wm (~/.i3/config window manager)
vim (~/.vimrc editor de texto y código)
tmux (terminal multiplexer)
vimfx (un legacy plugin de firefox para navegar en modo vim)

### Recapitulando
- Los archivos dotfiles son archivos de configuración ocultos utilizados por distintos programas.
- En los sistemas operativos unix-like los archivos son nombrados y comienzan con un (.) 'dot' en inglés.
- Estos archivos pueden ser respaldados en repos de github para tenerlos disponibles y hacer uso de ellos desde cualquier sistema.

Espero esta información sea útil, hasta la próxima.
