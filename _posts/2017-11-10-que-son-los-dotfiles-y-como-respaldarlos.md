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

Hace poco más un mes que no escribía en el blog, pero aquí estoy de regreso con un tema básico para cualquier *nix user, los llamados Dotfiles (archivos de configuración ocultos).

### ¿ Qué son los dotfiles ?

En sistemas unix-like, refiriéndonos a los sistemas basados en unix, digamos: GNU/Linux, MAC OS X, FreeBSD, etc. Sistemas en los que si bien recordamos, los archivos ocultos son definidos e identificados fácilmente por comenzar con un punto (.) 'dot' en inglés, por ello en primera instancia ya sabemos que los dotfiles son archivos ocultos en nuestro sistema.

### ¿ Dónde encuentro estos archivos y para qué sirven ?

Es común que ciertos programas hagan uso de archivos dotfiles creandolos y poniéndolos en algunas rutas del sistema para contener configuraciones.

Por mencionar algunos dotfiles célebres (.bashrc en Mac OS X llamado: .bash_profile, .gitignore, .vimrc) este último por ejemplo, tenemos que Vim (mi editor favorito para programar) crea y usa un archivo dotfile llamado .vimrc por default para guardar algunas configuraciones que el usuario puede modificar y agregar nuevas. Los nombres y rutas de los archivos dotfiles pueden variar y ser modificados en los programas que hacen uso de ellos, aun así es importante mencionar que muchos archivos dotfiles tienen el posfijo 'rc' o 'config'.

El archivo .vimrc podemos encontrarlo en el directorio home del usuario ~/.vimrc en el que '~/' tilde-virgulilla-de-eñe y diagonal se refieren al directorio principal del usuario y .vimrc al archivo dotfile en sí.

Dentro del archivo dotfile de vim -también llamado archivo de configuración- podemos encontrar algo parecido a esto:
```vim
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
```

### ¿ El contenido de los dotfiles tienen el mismo 'lenguaje' universal y/o estructura ?
No, el contenido de estos archivos, puede variar entre programas, es decir, cada programa define la sintaxis y cómo leer estos archivos, pero de eso no hay que preocuparnos, si siempre tenemos en mente que los archivos dotfiles a manera genérica/universal buscan definir configuraciones y variables. Por ejemplo, añadiendo la siguiente línea al archivo .vimrc hacemos que vim siempre nos muestre los números de línea de un archivo dentro del editor:

```vim
set number
```

o también con :

```vim
set nu
```
Me encanta hablar de vim, pero seguir hablando más de vim y su archivo .vimrc va más allá del propósito principal de este post. Les prometo realizar una serie de tutoriales y screencast sobre vim para todos los interesados en el tema.

Como dije, no hay que preocuparnos, la mayoría de programas que hacen hacen uso de los dotfiles tienen documentación disponible que explica cómo modificarlos y definir configuraciones.

### Respaldando e "instalando" tus dotfiles
Los dotfiles pueden contener muchas configuración específicas del usuario, es por ello que regularmente estos se guardan debajo de la carpeta home del usuario, la cantidad de dotfiles dependerá de la cantidad de programas que el usuario tenga y que estos programas por supuesto implementen estos archivos, en lo personal me doy a la tarea de respaldar los siguientes:

- bash (~/.bashrc bash shell)
- i3wm (~/.i3/config window manager)
- vim (~/.vimrc editor de texto y código)
- tmux (terminal multiplexer)
- vimfx (un legacy plugin de firefox para navegar en modo vim)

Para tener nuestros dotfiles resguardados y disponibles en cualquier momento y en cualquier sistema, alguien tuvo la brillante idea de crear un repositorio con todos ello en su propio github; Utilizando git entonces podemos guardar las versiones y tener estos archivos disponibles para clonarlos como cualquier otro repo e instalarlos en cualquier sistema, y así evitarnos que tener que crearlos y modificarlos manualmente.

### Mi repo dotfile
La idea de respaldar e instalar los dotfiles me pareció excelente y de inmediato quise crear mi propio repo y programé dos scripts en bash: uno para crear un backup y otro para instalarlos (copiarlos) de manera automática en sus respectivos directorios; [Aquí mi dotfile repo ](https://github.com/Energy1011/dotfiles), lo mejor de esto es que cualquier persona puede ver estos repos y tomar todas las configuraciones de cada dotfile. Siéntete libre de clonar mi repo y modificarlo a tu gusto :)


El script que he creado para respaldo, en el que el script pregunta al usuario que dotfiles respaldar:
[backup.sh](https://github.com/Energy1011/dotfiles/blob/master/backup.sh)

Para instalar mis dotfiles he creado este otro script que va preguntando al usuario que instalar y que no:
[install.sh](https://github.com/Energy1011/dotfiles/blob/master/install.sh)

Te animo a modificar los scripts a tus necesidades o colaborar con un pull request si lo deseas.

### Recapitulando esta publicación
- Los archivos dotfiles son archivos de configuración ocultos utilizados por distintos programas.
- En los sistemas operativos unix-like los archivos son nombrados y comienzan con un (.) 'dot' en inglés.
- Estos archivos pueden ser respaldados en repos de github para tenerlos disponibles y hacer uso de ellos desde cualquier sistema.
- Visita/Clona y basate en otros repositorios con archivos dotfiles para mejorar los tuyos.

Espero esta información sea útil, hasta la próxima.

