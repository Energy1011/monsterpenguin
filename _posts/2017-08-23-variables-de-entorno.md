---
layout: post
title: 'Variables de entorno Bash en GNU/Linux'
date: 2017-08-24 13:09:11.000000000 -06:00
type: post
published: false 
status: publish
categories: [linux]
tags: [linux, bash]
meta:
author: "Energy1011"
image: ""
---
## Variables de entorno

Las variables del entorno, también conocidas como variables del sistema son valores almacenados en memoria de los que el sistema operativo puede hacer uso para multiples tareas.  

Es cómun para los administradores de sistemas o programadores en algun momento toparse con la necesidad de cambiar por ejemplo la variable de entorno PATH para apuntar a ejecutables o bibliotecas del sistema. Es por ello que es importante comprender las variables de entorno y saber definirlas o consultarlas.

En GNU/Linux y sistemas Unix-Like podemos modificar y consultar las variables de entorno de manera muy similar, lo primero sería saber como consultar con que variables cuenta nuestro entorno:

En sistemas unix-like con bash (la mayoria de las distribuciones GNU/Linux tienen bash como lenguaje para la shell por default) podemos usar el comando echo:
```bash 
echo $<presionamos la tecla tab>
```

Al presionar la tecla **\<tab\>** sirve para acompletar palabras en la terminal, ella nos mostrara todas las variables de nuestro entorno, en Bash, las variables comienzan con el signo '$', es por ello que al autocompletar con **\<tab\>** veremos una lista de variables parecida a la siguiente:

$BASH            
$BASH_ALIASES    
$BASH_ARGC       
$BASH_ARGV       
$BASH_CMDS       
$BASH_COMMAND    
$BASH_COMPLETION_COMPAT_DIR       
$BASH_LINENO     
$BASHOPTS        
$BASHPID         
$BASH_REMATCH    
$BASH_SOURCE     
$BASH_SUBSHELL   
$BASH_VERSINFO   
$BASH_VERSION (version del bash)  
$HOME (variable que apunta a la carpeta principal del usuario)  
$PATH (variable con rutas a binarios)  
$HISTFILE ( archivo donde se guarda el historial de comandos )  

*Notemos que la mayoría de variables de entorno estan definidas con letras mayusculas por convención.*

Para ver el valor definido en una variable de entorno por ejemplo $HOME basta con hacer un echo de la siguiente manera:
```bash
echo $HOME
```
La variable $HOME siempre almacena la ruta a nuestra carpeta de usuario; Podemos observar que definir y consultar variables es sencillo.


## La variable $PATH
¿ Qué pasa con la variable $PATH ? la variable $PATH esta definida, digamos de una manera "especial" a diferencia de $HOME, y lo que almacena esta variable como mencione anteriormente son rutas a binarios del sistema y podemos hacer que apunte a una carpeta o varias carpetas donde tengamos nuestros programas, y esto sirve para que al escribir el nombre de alguno de nuestros programas en la terminal ella sepa donde encontrarlo y ejecutarlo.

Esta variable por default tendra una cadena (valor) algo parecido a esto:
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```
En la cadena anterior tenemos varias rutas separadas por ':', entre ellas rutas a binarios dentro del directorio del usuario '/usr/bin' y del sistema '/sbin/bin' si quisieramos agregar otro directorio bastaría con definir la variable PATH agregando '/ruta/a/mis/programas' y concatenando la cadena actual del $PATH de la siguiente manera:

```bash
PATH=/ruta/a/mis/programas/:$PATH
export PATH
```

Con el comando anterior nuestra cadena (valor) de $PATH sería:
```
/ruta/a/mis/programas/:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

El orden en la que definimos las rutas dentro de $PATH importan, ya que el sistema consulta las rutas de $PATH de izquierda a derecha y una vez que ha encontrado el binario dentro de un directrio , el sistema deja de buscar en los directorios que se encuentran más a la derecha de la cadena del $PATH. Supongamos que el sistema tiene el comandoX dentro de /sbin/bin y nosotros tenemos el mismo comandoX dentro de /ruta/a/mis/programas/ y la variable $PATH fue definida así:
```bash
PATH=$PATH:/ruta/a/mis/programas/
export PATH
```

Entonces la cadena del $PATH sería:
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/ruta/a/mis/programas/
```

Al escribir en la terminal:
```bash
comandoX
```
El sistema buscará el comandoX en las rutas del $PATH y si el sistema primero encuentra un programa con el nombre especificado en las rutas del sistema, esa versión será la ejecutada y no la que se encuentre dentro de '/ruta/a/mis/programas/' 

## El comando export
Quiza te pregustante para que sirve 'export PATH' El comando export se utiliza para exportar variables. Cuando nosotros ejecutamos un programa todas las variables del entorno exportadas son heredadas a los procesos hijos y ellos pueden acceder a ellas.

Si nosotros definimos una nueva variable llamada FOO:
```bash
FOO="bar"
```
Y si no hacemos un export FOO los procesos hijos no podrán acceder a su valor "bar"


## El archivo .bashrc

Por ultimo podemos definir un valor de cualquier variable del entorno como PATH en nuestro archivo de inicio **.bashrc**, esto quiere decir que para que cada vez que iniciemos la sesión de usuario dentro de sistemam, la variable PATH tendrá un valor ya definido por default, con esto evitamos que tener que definir la variable $PATH de manera manual, cada que la necesitemos:

El archivo .bashrc está oculto, es por ello que su nombre comienza con un punto '.' es la manera en que los sistemas unix-like reconoce archivos ocultos; El archivo .bashrc lo encontramos dentro de la carpeta HOME de cada usuario que use bash como lenguaje shell para su sesión. 
