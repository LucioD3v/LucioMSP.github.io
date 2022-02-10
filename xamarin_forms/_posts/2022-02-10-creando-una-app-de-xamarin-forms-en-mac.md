---
layout: post
title: Creando mi primera aplicación de Xamarin.Forms en Mac
description: Este artículo realizaremos (crearemos) nuestra primera aplicación de Xamarin.Forms utilizando MacOS
image: /assets/img/blog/post-headers/xamarin/xamarinForMac.png
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [xamarin.forms]
tags:
  - xamarin
  - xamarin.forms
keywords:
  - ios
  - android
  - xamarin
  - maui
lang: es
---

## Introducción
En este pequeño artículo, explicaré el cómo crear un proyecto Xamarin.Forms de muestra y ejecutar la aplicación Android/iOS en Visual Studio 2019 para Mac.

La verdad es algo muy sencillo, por ello realizaremos esto en tan solo 6 pasos, los cuales son los siguientes:

### Nota:
Cabe destacar que no se verá o tocará como instalar Visual Studio for Mac, ya que esto es muy sencillo de realizar.

## Paso 1

Abramos Visual Studio 2019 en nuestra máquina Mac y en la parte derecha tendremos dos opciones que son: Abrir y Nuevo. Cabe mencionar que podemos hacer clic en la opción Abrir para abrir un proyecto ya existente de Xamarin y en la opción Nuevo para crear un proyecto desde cero, la cual será la opción que elegiremos.

![image](/assets/img/blog/tutorials/creandoAppXamarinFormsMac/paso1.png)


## Paso 2

Después de hacer clic en la opción de Nuevo, VS navegará a la siguiente pantalla, en donde del lado izquierdo, podremos observar varias secciones, pero nosotros nos centraremos en la sección de Multiplataforma, posteriormente deberemos de seleccionar y hacer clic en Aplicación -> Aplicación en blanco -> Siguiente.

![image](/assets/img/blog/tutorials/creandoAppXamarinFormsMac/paso2.png)


## Paso 3

Después de hacer clic en el botón de Siguiente, VS navegará a la siguiente pantalla, en donde deberemos de configurar el nombre de nuestra aplicación en blanco, asi mismo deberemos de cubrir la organización identificada y posteriormente hacer clic en el botón Siguiente.

![image](/assets/img/blog/tutorials/creandoAppXamarinFormsMac/paso3.png)

Cabe destacar que podemos deshabilitar cualquier opcion de SO y por ende no se creará la aplicación de dicha plataforma, pero no lo recomiendo, ya que la idea de Xamarin.Forms es que podamos crear un proyecto y lanzarla para Android como para iOS, por ello es que vienen seleccionados ambos por default.

## Paso 4
Después de hacer clic en el botón Siguiente, VS navegará a la siguiente pantalla, en donde deberemos de configurar la ruta de donde queremos que se genere el proyecto (podemos dejar la ruta predefinida si queremos) y podemos de igual manera marcar la casilla  de Control de Versiones si lo situaremos en algun repositorio y si este proyecto sera compartido con otros desarrolladores. Posteriormente hagamos clic en el botón Crear.

![image](/assets/img/blog/tutorials/creandoAppXamarinFormsMac/paso4.png)

## Paso 5

Después de hacer clic en el botón Crear, VS navegará a la siguiente pantalla, en donde veremos ya como tal el proyecto de Xamarin.Forms creado, junto con la biblioteca de clases PCL-Portable (XamVG), XamVG.Android y XamVG.iOS

![image](/assets/img/blog/tutorials/creandoAppXamarinFormsMac/paso5.png)

## Paso 6

Ya por último podemos seleccionar el modo de depuración en Android o iOS y configurar el proyecto que deseemos ejecutar, cabe mencionar que del SO seleccionado podremos ver las diferentes opciones con las que contamos, ya sea a través de dispositivos fisicos o simuladores.

![image](/assets/img/blog/tutorials/creandoAppXamarinFormsMac/paso6Android.png)


![image](/assets/img/blog/tutorials/creandoAppXamarinFormsMac/paso6iOS.png)

## Resultado / Salida

### iOS

![image](/assets/img/blog/tutorials/creandoAppXamarinFormsMac/resultadoiOS.png)

### Android


![image](/assets/img/blog/tutorials/creandoAppXamarinFormsMac/resultadoAndroid.png)

## Conclusión

Espero que este pequeño artículo te haya brindado suficiente información para crear un proyecto Xamarin y ejecutar la aplicación tanto en Android como en iOS. 

Aprovecho el espacio para invitarte a dejar un comentario si deseas que dé más detalles sobre cualquier cosa dentro de este artículo.

## Happy Coding