---
layout: post
title: Aprendiendo a codificar y decodificar Base64 en C#
description:
image: /assets/img/blog/post-headers/b64-fb.png
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [maui]
tags:
  - net
  - c#
keywords:
  - net
  - c#
  - development
  
lang: es
---

## Codificación Base64
Base64 es un método de codificación en el que cualquier archivo de datos/imágenes/audio se puede convertir en datos binarios. Y los datos convertidos pueden pasar por la red sin ninguna pérdida de datos/imagen/audio.

A continuación veremos como hacer esto en C#

### Codificación de Base64 en C#

~~~bash

var plainTextBytes = System.Text.Encoding.UTF8.GetBytes("SampleTest");
Console.WriteLine(System.Convert.ToBase64String(plainTextBytes));

~~~

## Decodificación Base64
Este método es el reverso de la codificación base64, cuando se recibe en el otro extremo, a través de la red. Decodificarlo y procesar archivos de datos/imagen/audio para el próximo requisito específico, veamos dicho proceso en C#.

### Decodificación de Base64 en C#

~~~bash

var base64EncodedBytes = System.Convert.FromBase64String(System.Convert.ToBase64String(plainTextBytes));
Console.WriteLine(System.Text.Encoding.UTF8.GetString(base64EncodedBytes));

~~~

### Happy Coding!
