---
layout: post
title: 10 consejos para mejorar tu código en C#
description: En este artículo veremos 10 consejos para mejorar o entender y tener un código más limpio en C#
image: /assets/img/blog/post-headers/csharp/csharp.png
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [maui]
tags:
  - maui
  - net
  - apk
  - android
keywords:
  - csharp
  - net
  - code
lang: es
---

Escribir código limpio, conciso y legible es una habilidad esencial para cualquier desarrollador de C#. El código limpio es más fácil de entender, mantener y depurar. También es más probable que sea correcto y eficiente.

Aquí hay 10 consejos para escribir mejor código C#:


1. Utilice tipos inmutables y de solo lectura siempre que sea posible.
Es menos probable que los tipos de solo lectura e inmutables se modifiquen accidentalmente, lo que puede provocar errores.

~~~bash

// readonly and immutable types
readonly struct Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y)
    {
        X = x;
        Y = y;
    }
}

~~~

![image](/assets/img/blog/tutorials/maui-biometrics/02.png)

Espero que este pequeño artículo te haya brindado suficiente información para aplicar dicho control en sus aplicaciones .NET MAUI y ver los resultados esperados.

Aprovecho el espacio para invitarte a dejar un comentario si deseas que dé más detalles sobre cualquier cosa dentro de este artículo.

Recuerda que puedes encontrar una pequeña aplicación de muestra en mi repositorio de GitHub. Y no se olvide de buscar publicaciones existentes y otras publicaciones de julio de UI en todo el atractivo visual de .NET MAUI.

Más información:

- Articulo original por [Mark´s Blog (versión en Ingles)](https://mallibone.com/post/dotnetmaui-countdown-button)

- GitHub Xamarin-Fingerprint: [https://github.com/smstuebe/xamarin-fingerprint/tree/maui-support](https://github.com/smstuebe/xamarin-fingerprint/tree/maui-support)

## ¡Happy Coding!