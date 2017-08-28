---
layout: post
title: 'Liberando espacio con apt'
date: 2017-08-27 01:00:07 -06:00
type: post
published: true
status: publish
categories: [linux]
tags: [linux, bash, apt]
meta:
author: "Energy1011"
image: "logo-apt-moo.png"

---

## Introducción
APT (Advanced Packaging Tool) Herramienta Avanzada de Empaquetado es un sistema gestor de paquetes creado por el proyecto Debian. Esta herramienta se encarga de facilitarle al usuario las tareas de instalación y eliminación de programas en los sistemas GNU/Linux (distribuciones derivadas de Debian).

Esta herramienta se compone de dos programas principalmente:
**apt-get** y **apt-cache**, para estos programas podemos encontrar programas frontend, me refiero a programas con una interfaz gráfica que facilita el uso de apt como es Aptitude, Synaptic, Adept, Ubuntu Software Center, etc.

Apt instala paquetes .deb para los sistemas debian y distribuciones derivadas, instalar un programa con esta herramienta es tan sencillo como escribir:
```bash
$ apt-get install <nombre_del_programa>
```
Donde **\<nombre_del_programa\>** lo sustituimos por el nombre del programa que deseamos instalar.

Si queremos por ejemplo instalar GIMP, un programa para la manipulación de imágenes, se haría de la siguiente manera:
```bash
$ apt-get install gimp
```
Sencillo ¿cierto?.

## Comprobando el espacio utilizado
Los archivos .deb que apt-get descarga de los repositorios, son almacenados en nuestra máquina antes de comenzar el proceso de instalación, y a veces hace falta hacer limpieza de estos archivos (ojo, al realizar los siguientes 3 pasos para liberar espacio, liberaremos espacio sin **desinstalar** programas, solo borraremos los instaladores, caché de .deb almacenados localmente); Los archivos son almacenados en la siguiente ruta cuando van a ser instalados **/var/cache/apt/archives** podemos ver cuánto espacio están utilizando estos archivos en nuestro disco con:

```bash
$ du -hs /var/cache/apt/archives
```
**du** es un comando que nos permite ver el Disk Usage (espacio utilizado en disco).
## 3 Pasos para liberar espacio
```bash
$ sudo apt-get autoclean
$ sudo apt-get clean
$ sudo apt-get autoremove
```

### Explicación de los 3 comandos anteriores
1- Para liberar el espacio primero haremos un **autoclean**, esta opción borra todo el caché de los paquetes .deb de paquetes de versiones anteriores y de los programas que ya han sido instalados en nuestro sistema:
```bash
$ sudo apt-get autoclean
```
2- El siguiente comando con la opción **clean** borra todos los paquetes .deb, si queremos instalar de nuevo un programa el archivo .deb necesitará ser descargado nuevamente de los repos:

```bash
$ sudo apt-get clean
```
3- Por último el siguiente comando con la opción **autoremove** borra todos los paquetes dependencias de otros programas:
```bash
$ sudo apt-get autoremove
```
## Comprobando el espacio libre nuevamente
Ahora que hemos liberado el espacio, podemos comprobar nuevamente el tamaño de la carpeta que apt usa para almacenar todos los archivos como caché:

```bash
$ du -hs /var/cache/apt/archives
```

NOTA: la imagen de esta publicación es una vaca, sí una vaca en arte ASCII que podemos ver lanzando el comando:
```bash
$ apt-get moo
```
Es un [Easter Egg virtual](https://es.wikipedia.org/wiki/Huevo_de_pascua_(virtual)) que los desarrolladores de apt han incluido en el programa.

A nadie le cae mal liberar espacio en disco de vez en cuando, hasta aquí con este pequeño tutorial, hasta la próxima.

