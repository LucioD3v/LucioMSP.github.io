---
layout: post
title: Primeros pasos con Microsoft .NET MAUI
description: Conoce todo sobre .NET MAUI, la evolución de Xamarin.Forms. - Primer articulo -
image: /assets/img/blog/post-headers/maui/maui01.png
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [maui]
tags:
  - maui
  - net
keywords:
  - maui
  - net
lang: es
---

Como ya muchos sabemos, la interfaz de usuario de la aplicación multiplataforma .NET (.NET Multi-platform App UI (.NET MAUI)) es la evolución del kit de herramientas de Xamarin.Forms. Teniendo en cuenta la productividad del desarrollador, MAUI simplifica la estructura del proyecto en un solo proyecto para apuntar a múltiples plataformas (Android, iOS, macOS y Windows).

-------------------------------------------------------------------------------

En esta serie de artículos, exploraremos MAUI y aprenderemos a crear nuestra ya famosisima primera aplicación de "Hola Mundo".

A continuación dejo los temas que veremos y que nos permitirán conocer más sobre .NET MAUI:

- ¿Qué es .NET MAUI, para quién es, cómo funciona?
- Ventajas de MAUI sobre otros marcos multiplataforma (frameworks)
- Instalación de requisitos previos para el desarrollo multiplataforma con MAUI
- Instalación de MAUI
- Creación de una aplicación usando .NET MAUI 
- Corrección a problemas

---------------------------------------------------------

#### Importante -> Requerimientos Técnicos

Este artículo está dirigido principalmente a desarrolladores de .NET con cierta experiencia con Xamarin y .NET.

Para la aplicación que se va a desarrollar, se requiere un entorno de desarrollo de Windows 10, debido a que la compatibilidad de Visual Studio para Mac con .NET MAUI está prevista para una versión futura.

Idealmente, se debería contar con un dispositivo macOS con Xamarin.iOS y Xcode instalado conectado a su entorno de Windows 10. Esto por que se necesitará compilar y usar el simulador de iOS. Con esta configuración, es decir, Windows y Mac, podemos probar la aplicación de tareas en múltiples plataformas (Android, iOS, macOS y Windows).
### Nota: 

Actualmente, Visual Studio 2022 solo puede implementar aplicaciones de .NET MAUI iOS en el simulador de iOS, y no en dispositivos físicos.

## ¿Qué es .NET MAUI, para quién es, cómo funciona?
.NET MAUI es un framework multiplataforma para crear aplicaciones nativas de escritorio y móviles con C# y XAML. Funciona como una capa de abstracción que gestiona la comunicación de código compartido con plataformas subyacentes como Android, iOS, macOS y Windows.

.NET MAUI nos permite crear una interfaz de usuario nativa en cada plataforma y escribir lógica de negocios en C# que se comparte entre plataformas. Está construido sobre .NET, lo que significa que maneja tareas como la asignación de memoria, la recolección de basura (garbage collection) y la interoperabilidad con las plataformas Android, iOS, macOS y Windows.

.NET MAUI es para desarrolladores que desean escribir aplicaciones multiplataforma usando C# desde una única base de código compartida en Visual Studio.

Si han utilizado anteriormente Xamarin.Forms para crear interfaces de usuario multiplataforma, notarán muchas similitudes con .NET MAUI. De hecho, .NET MAUI es la evolución de Xamarin.Forms. Sin embargo, simplifica la estructura del proyecto en un solo proyecto para apuntar a múltiples plataformas, algo que en Xamarin.Forms no tiene, por el contrario cuenta con un proyecto para cada plataforma de destino y otro proyecto para una base de código compartido:

|Xamarin.Forms|
![image](/assets/img/blog/tutorials/maui-primeros-pasos/App_Xamarin.jpeg)

|.NET MAUI|

![image](/assets/img/blog/tutorials/maui-primeros-pasos/App_MAUI.jpeg)

Figura 1 – Comparación de la estructura de una solución entre Xamarin.Forms (izquierda) y .NET MAUI (derecha)

Además de lo anterior, .NET MAUI nos permite agregar recursos como imágenes, fuentes o formularios de traducción una sola vez, ya que como solo se cuenta con un solo proyecto, no se tiene la necesidad de hacerlo para cada plataforma por separado. En comparación, al usar Xamarin.Forms, debemos agregar cada recurso a cada plataforma por separado. Esto agrega trabajo adicional para nosotros los desarrolladores y claro esta, tambien para el equipo. 

|Xamarin.Forms|
![image](/assets/img/blog/tutorials/maui-primeros-pasos/XF01.png)

|.NET MAUI|

![image](/assets/img/blog/tutorials/maui-primeros-pasos/MAUI01.png)

Figura 2 - Agregando imagenes en Xamarin.Forms y en .NET MAUI

Sin embargo, .NET MAUI todavía nos permite trabajar con las APIs nativas del sistema operativo subyacente. En la carpeta Plataformas, se pueden agregar archivos de código fuente para un sistema operativo específico y acceder a las API nativas:

|.NET MAUI|

![image](/assets/img/blog/tutorials/maui-primeros-pasos/MAUI02.png)

Figura 3 - Carpeta Platforms

Y bueno, eso es todo por el momento, en el siguiente artículo conoceremos cuales son las ventajas de MAUI sobre otros marcos multiplataforma (frameworks).

¡Hasta la próxima!