---
layout: post
title: 'Qué son los dotfiles y cómo respaldarlos'
date: 2017-11-10 02:00:00 -06:00
type: post
published: true
status: publish
categories: [linux, unix, blog]
tags: [dotfiles, unix]
meta:
author: "Energy1011"
image: "logo-dotfiles.png"

---

Hace poco más un mes que no escribía en el blog, pero aquí estoy de regreso con un tema básico para cualquier *nix-user, los llamados __Dotfiles__ (archivos de configuración ocultos).

### ¿ Qué son los dotfiles ?

En sistemas unix-like, refiriéndonos a los sistemas basados en unix, digamos: GNU/Linux, MAC OS X, FreeBSD, etc. Sistemas en los que si bien recordamos, los archivos ocultos son definidos e identificados fácilmente por comenzar con un punto (.) 'dot' en inglés, por ello en primera instancia ya sabemos que los dotfiles son archivos ocultos en nuestro sistema.

### ¿ Dónde encuentro estos archivos y para qué sirven ?

Es común que ciertos programas hagan uso de archivos dotfiles creandolos y poniéndolos en algunas rutas del sistema para contener configuraciones.

Por mencionar algunos dotfiles célebres (.bashrc en Mac OS X llamado: .bash_profile, .gitignore, .vimrc) este último por ejemplo, tenemos que Vim (mi editor favorito) crea y usa un archivo dotfile llamado __.vimrc__ por default para guardar algunas configuraciones que el usuario puede modificar y agregar nuevas. Los nombres y rutas de los archivos dotfile pueden variar y ser modificados en los programas que hacen uso de ellos, aun así es importante mencionar que muchos archivos dotfile tienen el posfijo 'rc' o 'config'.

El archivo __.vimrc__ podemos encontrarlo en el directorio home del usuario __~/.vimrc__ en el que __'~/'__ tilde-virgulilla-de-eñe y diagonal se refieren al directorio principal del usuario y __.vimrc__ al archivo dotfile en sí.

Dentro del archivo dotfile de vim __también llamado archivo de configuración de vim__ podemos encontrar algo parecido a esto:
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
No, el contenido de estos archivos, puede variar entre programas, es decir, cada programa define la sintaxis y cómo leer estos archivos, pero de eso no hay que preocuparnos, si siempre tenemos en mente que los archivos dotfiles a manera genérica/universal buscan definir configuraciones y variables. Por ejemplo, añadiendo la siguiente línea al archivo __.vimrc__ hacemos que vim siempre nos muestre los números de línea de un archivo dentro del editor:

```vim
set number
```

o también con :

```vim
set nu
```
Me encanta hablar de vim, pero seguir hablando más de vim y su archivo .vimrc va más allá del propósito principal de este post. Les prometo realizar una serie de tutoriales y screencast sobre vim para todos los interesados en el tema.

Como dije, no hay que preocuparnos, si leemos el apartado de __Description__ del archivo .vimrc anterior, dice:
```vim
" Description: A minimal, but feature rich, example .vimrc. If you are a
"              newbie, basing your first .vimrc on this file is a good choice.
"              If you're a more advanced user, building your own .vimrc based
"              on this file is still a good idea.
```
> Que es buena idea basarse en ese archivo de configuración para los usuarios novatos y aun así para los más avanzados también sigue siendo buena idea

__Pienso que esta pequeña descripción en el fondo promueve y nos invita a la filosofía libre de compartir__, para así usar y basarnos en archivos dotfiles que otras personas ya han elaborado. Para aprender a modificar dotfiles no solo compartimos sino que también la mayoría de programas que hacen uso de los dotfiles tienen documentación disponible que explica cómo modificarlos y definir configuraciones.

### Respaldando e "instalando" tus dotfiles
Los dotfiles pueden contener muchas configuraciones específicas del usuario, es por ello que regularmente estos se guardan debajo de la carpeta home del usuario, la cantidad de dotfiles dependerá de la cantidad de programas que el usuario tenga y que estos programas por supuesto implementen este tipo de archivos; En lo personal me doy a la tarea de respaldar los siguientes dotfiles:

- bash (~/.bashrc bash shell)
- i3wm (~/.i3/config window manager)
- vim (~/.vimrc editor de texto y código)
- tmux (terminal multiplexer)
- vimfx (un legacy plugin de firefox para navegar en modo vim)

Para tener nuestros dotfiles resguardados y disponibles en cualquier momento y en cualquier sistema, __alguien tuvo la brillante idea un día de crear un repositorio__ y llevarlo con un CVS como lo es __git__; Utilizando git entonces podemos guardar las versiones  de nuestros dotfiles y tener estos archivos disponibles para clonarlos como cualquier otro repo e instalarlos en cualquier sistema.

__Una guía no-oficial de Github explica y recomienda la creación de repositorios dotfiles [aquí](https://dotfiles.github.io/)__

### Mi Repo Dotfile
Como anteriormente mencioné, compartir configuraciones de dotfiles es bueno, ya que puede beneficiarnos a todos. La idea de respaldar e instalar los dotfiles me pareció excelente y de inmediato quise crear mi propio repo y programé dos scripts en bash: __Uno para crear backups__ y otro __para instalarlos (copiarlos)__ de manera automática en sus respectivos directorios; [Aquí mi dotfile repo](https://github.com/Energy1011/dotfiles)
__Siéntete libre de clonar mi repo y modificarlo a tu gusto :)__

__Mi repo dotfiles contiene lo siguiente:__

- El script que he creado para respaldo, en el que el script pregunta al usuario que dotfiles respaldar:
[backup.sh](https://github.com/Energy1011/dotfiles/blob/master/backup.sh)

- Para instalar mis dotfiles he creado este otro script que va preguntando al usuario que instalar y que no:
[install.sh](https://github.com/Energy1011/dotfiles/blob/master/install.sh)

- Y por supuesto: archivos dotfile

Te invito a modificar mis scripts a tus necesidades o colaborar con un pull request si lo deseas, (por lo pronto un amigo me ha recomendado agregarle a los scripts una opción de (yes to all) para las preguntas de instalación y de respaldo).

### Recapitulando esta publicación
- En los sistemas operativos unix-like los archivos son nombrados y comienzan con un (.) 'dot' en inglés.
- Los archivos dotfiles son archivos de configuración ocultos utilizados por distintos programas.
- Estos archivos pueden ser respaldados en repos de git para tenerlos disponibles y hacer uso de ellos desde cualquier sistema.
- Es buena idea aprender/clonar/crear repos dotfiles, más que nada basarte en otros repositorios para mejorar tus dotfiles.


A manera general he explicado los dotfiles en esta publicación y espero esta información sea útil, hasta la próxima.
