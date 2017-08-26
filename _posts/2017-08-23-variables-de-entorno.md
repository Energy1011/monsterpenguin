---
layout: post
title: 'Variables de entorno Bash en GNU/Linux (export, printenv, env y el archivo .bashrc)'
date: 2017-08-25 13:09:11.000000000 -06:00
type: post
published: true
status: publish
categories: [linux]
tags: [linux, bash]
meta:
author: "Energy1011"
image: "logo-bash-cube.png"
---
## Variables de entorno

Las variables del entorno, también conocidas como variables del sistema son valores almacenados en memoria de los que el sistema operativo puede hacer uso para múltiples tareas, en esta publicación hablaré de estas variables y cómo consultarlas y modificarlas desde la shell, además hablaré de comandos que tienen relación con este tema de las variables de entorno.

Las variables de entorno son un tema interesante y muy útil; Es común para los administradores de sistemas o programadores verse en la necesidad de cambiar por ejemplo la variable de entorno $PATH para apuntar a ejecutables, bibliotecas, frameworks, del sistema; Son necesarias cuando consultamos datos sobre la shell, cuando usamos compiladores, IDEs, instalando algun software, corriendo un script o intérprete, sin fin de cosas es donde podemos necesitarlas, es por ello que es importante al menos saber cómo consultarlas y definirlas.

En GNU/Linux y sistemas Unix-like con sintaxis [Bash](https://es.wikipedia.org/wiki/Bash) podemos modificar y consultar las variables de entorno de manera simple, la mayoría de las distribuciones GNU/Linux tienen bash como lenguaje para la shell por default, los sistemas MAC OS X también cuentan con bash como lenguaje en sus terminales y podemos usar el comando **echo** para ver las variables bash definidas:

```bash
$ echo $<presionamos la tecla tab>
```

Al presionar la tecla **\<tab\>** sirve para autocompletar palabras en la terminal, ella nos mostrará todas las variables de nuestro entorno auto-completando, y sabemos que en bash las variables comienzan con el signo **$**, es por ello que al auto-completar con **\<tab\>** veremos una lista más extensa de variables pero parecida a la siguiente:

(la siguiente lista es una lista reducida y específica de bash)
- $BASH_ALIASES    
- $BASH_ARGC       
- $BASH_ARGV       
- $BASH_CMDS       
- $BASH_COMMAND    
- $BASH_COMPLETION_COMPAT_DIR       
- $BASH_LINENO     
- $BASHOPTS        
- $BASHPID         
- $BASH_REMATCH    
- $BASH_SOURCE     
- $BASH_SUBSHELL   
- $BASH_VERSINFO   
- $BASH_VERSION (versión del bash)  


Posiblemente las variables más "populares" dentro de los sistemas Unix-like con y sin bash sean:
- $PATH (variable que tiene rutas a binarios, separadas por ':')
- $BASH (ruta al programa bash que interpreta órdenes y el lenguaje para la shell llamado bash)
- $DISPLAY (lista de las pantallas del servidor X)
- $EDITOR (el editor predeterminado: vim, emacs, nano, etc)
- $HISTFILE (ruta al archivo historial de comandos, normalmente: ~/.bash_history)
- $HISTSIZE (numero max de comandos del historial para el archivo definido en $HISTFILE)
- $HOME (la variable $HOME tiene la ruta a nuestra carpeta de usuario)
- $HOSTNAME (nombre de la máquina)
- $IGNOREEOF (número de veces que hay que pulsar ctrl+d para prevenir salir de la terminal por accidente, es recomendable IGNOREEOF=2 con esto es necesario pulsar ctrl+d dos veces para salir)
- $PATH (variable con rutas a binarios, en esta publicación hablo bastante sobre ella)
- $PS1 (variable que define como se muestra nuestro prompt, precisamente el carácter o los caracteres que se ven detrás del cursor en la línea de comandos, por default en bash es '$')
- $SHELL (el intérprete de comandos por default)

*Notemos que la mayoría de variables de entorno están definidas con letras mayúsculas por convención.*

Para ver el valor definido en una variable de entorno en particular, por ejemplo *$HOME* basta con hacer un **echo** de la siguiente manera:
```bash
$ echo $HOME
> /home/monsterpenguin
```

Podemos observar que definir y consultar variables es sencillo y aún más sencillo con el comando: **printenv** ya que nos permite ver **todas** las variables y sus valores rápidamente:

```bash
$ printenv
```
De la misma manera  el comando **env** puede mostrarnos las variables de entorno y también nos permite ejecutar un programa con variables de entorno modificadas (podría decirse en un enviroment controlado en cuanto a variables de entorno), esta publicación tiene un apartado explicando el uso de env con mayor detalle más adelante.

## La famosa variable $PATH
La variable de entorno $PATH existe en la mayoría de los sistemas operativos, su función es tener rutas donde se alojan los programas para que el usuario y otros comandos o programas los encuentren con facilidad, si no existiera esta variable de entorno para ejecutar el comando 'ls' por ejemplo, sería necesario escribir su ruta completa **'/bin/ls'** y el punto para ejecutarlo:
```bash
$ which ls
> /bin/ls
```
Con la variable $PATH nos aseguramos que en la variedad de sistemas existentes, esta variable tendrá las rutas importantes a los programas e intérpretes.

¿ Qué pasa con la variable $PATH ?  
La variable $PATH digamos que está definida de una manera "especial" y utiliza una notación con **':'** para separar rutas (lo explicaré enseguida) a diferencia de $HOME , y lo que almacena esta variable como mencione anteriormente son rutas a programas del sistema y además podemos hacer que apunte a una carpeta o varias carpetas donde tengamos nuestros propios programas, y esto sirve para que al escribir el nombre de alguno de nuestros programas en la terminal ella sepa donde encontrarlo y ejecutarlo.

$PATH por default tendrá una cadena (valor) algo parecido a esto:
```
$ echo $PATH
> /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```
En la cadena anterior tenemos varias rutas separadas por **':'** rutas a ejecutables dentro del directorio del usuario **'/usr/bin'** y del sistema **'/sbin/bin'** y si quisiéramos agregar otro directorio bastaría con definir la variable PATH agregando **'/ruta/a/mis/programas'** y concatenando la cadena actual del $PATH de la siguiente manera:

```bash
$ PATH=/ruta/a/mis/programas/:$PATH
$ export PATH
```

Con el comando anterior nuestra cadena (valor) de $PATH sería:
```
$ echo $PATH
> /ruta/a/mis/programas/:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

El orden en el que definimos las rutas dentro de $PATH **es importante**, ya que el sistema consulta las rutas de $PATH de izquierda a derecha y una vez que ha encontrado el binario/ejecutable dentro de un directorio, el sistema deja de buscar en los directorios que se encuentran más a la derecha de la cadena del $PATH. Supongamos que el sistema tiene el *programaX* dentro de */sbin/bin* y nosotros tenemos el mismo *programaX* dentro de */ruta/a/mis/programas/* y la variable $PATH fue definida así:
```bash
$ PATH=$PATH:/ruta/a/mis/programas/
$ export PATH
```

Entonces la cadena del $PATH sería:
```
$ echo $PATH
> /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/ruta/a/mis/programas/
```

Al escribir en la terminal:
```bash
$ programaX
```
El sistema buscará el **programaX** en las rutas del $PATH y si el sistema primero encuentra un programa con el nombre **programaX** especificado en las rutas del sistema, ese binario será la ejecutado y no el que se encuentre dentro de **'/ruta/a/mis/programas/'**, esto representaría un problema si las versiones del **programaX** fuesen distintas, en el tema sobre el comando **env** muestro un ejemplo de esto.

## El comando export
Quizá te preguntaste: ¿ para qué sirve **export PATH** ?  
El comando export se utiliza para exportar variables, cuando nosotros ejecutamos un programa todas las variables del entorno exportadas son heredadas a los procesos hijos y ellos pueden acceder a ellas.

Si nosotros definimos una nueva variable llamada FOO:
```bash
$ FOO="bar"
```
Y si no hacemos un **export FOO** los procesos hijos no podrán acceder al valor de FOO.

## El comando env
Si estamos hablando de variables de entorno también vale la pena hablar del comando **env**, este comando puede jugar un papel importante en el mundo de las variables de entorno, y para simplificarlo este comando hace dos cosas principalmente:
- Muestra las variables de entorno al igual que el comando **printenv** simplemente llamándolo sin opciones y argumentos:
```
$ env
```
- Ejecutar un comando o script añadiendo o eliminando variables de entorno. El siguiente comando muestra cómo se puede definir la variable $PATH para el nuevo entorno/contexto a generar con env
```bash
$ env PATH=/mi/nuevo/path /bin/bash
```
Para ejecutar por ejemplo una nueva shell ignorando las variables de entorno actuales y definiendo un PATH con una nueva ruta adicional:
```bash
$ env -i PATH=$PATH:/mi/ruta/adicional/ /bin/sh
```
La opción *-i* en el comando anterior nos permite ignorar las variables de entorno actuales pero aun así definir también $PATH, para más información ver el manual de env
```bash
$ man env
```  
Env a menudo es utilizado para asegurar que se lance el intérprete correcto para un script, el siguiente ejemplo lo encontré en stackoverflow y muestra cómo podemos asegurarnos de utilizar el intérprete correcto:

{% highlight bash linenos %}
$ /usr/local/bin/python -V
Python 2.6.4
$ /usr/bin/python -V
Python 2.5.1
$ cat my_script.py
#!/usr/bin/env python
import json
print "hello, json"
$ PATH=/usr/local/bin:/usr/bin
$ ./my_script.py
hello, json
$ PATH=/usr/bin:/usr/local/bin
$ ./my_script.py
Traceback (most recent call last):
  File "./my_script.py", line 2, in <module>
      import json
      ImportError: No module named json
```
{% endhighlight %}

Credito y fuente del ejemplo anterior [aquí](https://stackoverflow.com/questions/2429511/why-do-people-write-usr-bin-env-python-on-the-first-line-of-a-python-script)

El ejemplo anterior nos muestra que hay dos intérpretes de python (dos programas distintos en rutas distintas, con versiones distintas) y damos por hecho dos cosas:
- python 2.5 se encuentra en la ruta */usr/bin/*
- python 2.6 se encuentra en la ruta */usr/local/bin/*

Otro hecho importante y la moraleja de esto es que la primera línea de **my_script.py** "La apodada [Shebang #!](https://es.wikipedia.org/wiki/Shebang)" manda a llamar un interprete de python por medio de nuestro comando **env**, asegurando así que el intérprete a llamar será el que se encuentre primero en la variable $PATH del entorno actual, y al ser cambiado el orden de la definición del $PATH cambia el resultado de correr **my_scriopt.py** puesto que la versión 2.5 de python nos arroja un **ImportError** ya que esa versión en ese sistema no cuenta con el módulo *json* instalado y necesita ser instalado.

**Recuerda:** el orden del la definición de directorios en el $PATH es importante como en el caso anterior.

## El archivo .bashrc
El archivo .bashrc es un archivo que es ejecutado cuando iniciamos una sesión en bash, abriendo por ejemplo la terminal (los MACOSX también cuentan con un .bash_profile). Entonces la idea aquí con las variables de entorno y el .bashrc es definir variables del entorno como $PATH* en nuestro archivo de inicio **.bashrc**, esto quiere decir que: Cada vez que iniciemos un bash shell dentro del sistema y en el espacio del usuario, la variable $PATH tendrá un valor ya definido por default que el usuario quiera, con esto evitamos que tener que definir la variable $PATH de manera manual cada vez que abramos la terminal, para lograr esto solo hay que agregar las siguientes líneas a nuestro archivo bashrc:

El archivo **.bashrc** está oculto, es por ello que su nombre comienza con un punto '.' es la manera en que los sistemas Unix-like marcan/definen archivos ocultos; El archivo **.bashrc** lo encontramos dentro de la carpeta HOME de cada usuario que use bash como lenguaje shell para su sesión, los archivos ocultos que definen configuraciones específicas del usuario en distintas aplicaciones son llamados en conjunto [dotfiles](https://en.wikipedia.org/wiki/Dot-file).

En mi repo [dotfiles](https://github.com/Energy1011/dotfiles/blob/master/.bashrc) tengo además un par de scripts para instalar/respaldar mis dotfiles, sean libres de descargarlo, modificarlo y adaptarlo a su gusto.


Espero esta publicación les sea de utilidad, hasta la próxima.

