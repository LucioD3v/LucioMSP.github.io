---
layout: post
title: Añadiendo el efecto de sombra a una aplicación de Xamarin.Forms
description: En este artículo mostraré que tan fácilmente es agregar sombras a nuestras aplicaciones de Xamarin.Forms sin utilizar Frames.
image: /assets/img/blog/post-headers/xamarin/shadow.png
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [xamarin.forms]
tags:
  - shadow
  - effects
  - sombras
  - toolkit
  - xamarin
keywords:
  - ios
  - android
  - xamarin
  - maui
  
lang: es
---

En este artículo mostraré que tan fácilmente se pueden agregar sombras a nuestras aplicaciones de Xamarin.Forms, esto sin hacer uso de Frames y lo mejor, que se vera en menos de dos minutos.

## Paso 1

En primer lugar, instalemos el paquete nuget Xamarin.CommunityToolkit a todos nuestros proyectos de Xamarin.Forms (incluidos los específicos de la plataforma iOS, Android, UWP, etc).

![image](/assets/img/blog/tutorials/xamarin_sombras/paso1.png)

## Paso 2

Ahora naveguemos a cualquier archivo XAML en la que deseemos agregar sombra, posteriormente agreguemos el siguiente espacio de nombres (también puede ser un archivo C#, pero en este ejemplo, me centrare en XAML).

~~~bash

xmlns:xct="http://xamarin.com/schemas/2020/toolkit"

~~~

Y listo, ¡eso es todo! Ahora ya podemos hacer uso del ShadowEffect.

Ahora solo tocar usar las propiedades adjuntas de ShadowEffect para controlar la sombra, por ejemplo:

~~~bash

<StackLayout
    xct:ShadowEffect.Color="Red"
    xct:ShadowEffect.OffsetY="5"
    xct:ShadowEffect.Radius="10">

~~~


![image](/assets/img/blog/tutorials/xamarin_sombras/code.png)


## Resultado / Salida

| Antes |

![image](/assets/img/blog/tutorials/xamarin_sombras/resultadoAntes.png)

| Despues |

![image](/assets/img/blog/tutorials/xamarin_sombras/resultadoDespues.png)


Las propiedades Color, Opacidad, Radio, OffsetX, OffsetY están disponibles para que ajuste la sombra según lo requiera su diseño.

La buena noticia es que este efecto se puede aplicar a cualquier vista de Xamarin.Forms (no solo a los diseños). Para que podamos agregar sombras tanto a etiquetas (labels), botones y  vistas personalizadas.

¡Felicidades! Ahora ya sabes cómo usar los efectos de sombra de Xamarin.CommunityToolkit

## Conclusión

Espero que este pequeño artículo te haya brindado suficiente información para aplicar sombras em tus aplicaciones de Xamarin.Forms y ver los resultados tanto en Android como en iOS. 

Aprovecho el espacio para invitarte a dejar un comentario si deseas que dé más detalles sobre cualquier cosa dentro de este artículo.

## Happy Coding