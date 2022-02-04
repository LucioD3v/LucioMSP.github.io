---
layout: post
title: Como prevenir el modo oscuro en Xamarin.Forms
description: Este artículo veremos como forzar el modo blanco o light en una aplicación desarrollada en Xamarin.Forms
image: /assets/img/blog/post-headers/xamarin/lightModeXF.png
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

Este artículo es una traducción al español del blog de [banditoth](https://www.banditoth.hu/2022/02/04/xamarin-forms-prevent-dark-mode-on-ios-android/) (con un toque personal), en donde se demuestra como forzar el modo blanco o light en una aplicación desarrollada en Xamarin.Forms

---------------------------------------------------------------------

## Solución para iOS

Abramos nuestro archivo info.plist y agreguemos la siguiente clave:

~~~bash

<key>UIUserInterfaceStyle</key> 
<string>Light</string>

~~~

## Solución para Android

Para que se realice lo mismo pero en Android, deberemos de poner este código en el MainAcitivity.cs

~~~bash

AppCompatDelegate.DefaultNightMode = AppCompatDelegate.ModeNightNo;

~~~

Recordemos guardar los cambios y si es necesario recompilar para que los cambios se implementen en las aplicaciones.

## Observaciones
Consideren el realizar varias pruebas previas antes de subir cambios a su repositorio o generar versión para publicar en las respectivas tiendas de los sistemas operativos móviles.

# Happy Coding