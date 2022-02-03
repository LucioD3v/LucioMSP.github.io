---
layout: post
title: Top 10 - Mejores prácticas para ASP.NET Core
description: En este artículo conoceremos el top 10 de las mejores prácticas para mejorar el rendimiento de ASP.Net Core
image: /assets/img/blog/post-headers/aspNetCore.jpeg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [asp][net]
tags:
  - asp
  - net
keywords:
  - asp
  - net
  - development
  
lang: es
---

Sinceramnente una de las principales razones por las que ASP.NET Core es el framework favorito de muchos, es el rendimiento. Puesto que nos brinda a los desarrolladores una base estable para crear aplicaciones basadas en web. Cabe mencionar que es crucial revisar nuestras aplicaciones regularmente para cumplir con las expectativas y es por ello, que en este artículo se trataran algunos consejos esenciales para mejorar la velocidad y el rendimiento para las aplicaciones ASP.NET Core.

## Usa la última versión

Cada versión viene con las capacidades más recientes y avanzadas y un rendimiento más rápido.
Al desarrollar aplicaciones con ASP.NET Core. Asegúrese de utilizar la versión más reciente de ASP.NET Core. Dado que Microsoft mejora constantemente su rendimiento en la versión más reciente con respecto a la versión anterior.

### 1. Evite el bloqueo de llamadas

Es importante diseñar su aplicación ASP.NET Core para ejecutar varios procesos a la vez. Puede lograr esto mediante el uso de una API asíncrona. Eso puede manejar miles de solicitudes y no depende de que se bloqueen las llamadas. En lugar de esperar a que finalice un trabajo asíncrono, comenzará a trabajar en un subproceso diferente.
El problema en las aplicaciones ASP.NET Core es bloquear la ejecución asíncrona a través de llamadas a Task. El subproceso se bloquea hasta que se completa la tarea y espera a que se complete. Ejecutar ya que ASP.NET Core ya está ejecutando subprocesos dentro del grupo de subprocesos estándar. Ejecutar dará como resultado una programación de grupo de subprocesos innecesaria.
En su lugar, cree rutas de código activo que sean síncronas y llamen a E/S, acceso a datos. Y patrones de API que se ejecutan durante largos períodos para ejecutar operaciones de forma asíncrona. Para que puedan llevarse a cabo sin afectar a otros procesos.
Asegurarse de que los aspectos técnicos estén en su lugar para una aplicación en ejecución puede ser difícil. Contamos con expertos en el campo que podrían convertirse en su equipo extendido, capaces de manejar sus proyectos. Si está buscando crear la aplicación desde cero o modificar su aplicación existente.

### 2. Usar caché
Si buscas mejorar el rendimiento de tu aplicación. El método bien conocido es reducir la cantidad de solicitudes realizadas al servidor cada vez. Funciona: se realiza una llamada al servidor y se guarda la respuesta. La próxima vez que se realice una llamada para obtener la misma respuesta, en lugar de solicitar la ayuda del servidor. Esta información se compara con los datos almacenados. Y cuando se determina que es compatible, se lee de la base de datos en lugar de llamar al servidor.
Así es como el almacenamiento en caché puede ahorrar tiempo y mejorar el rendimiento general. Reducir las llamadas al servidor con frecuencia. Es posible realizar el almacenamiento en caché del lado del servidor o del lado del cliente del lado del servidor. ASP.NET Core permite diferentes tipos de almacenamiento en caché, incluido el almacenamiento en caché en la memoria Almacenamiento en caché de respuestas. Y también almacenamiento en caché de respuestas, almacenamiento en caché distribuido y más.
¡Siempre asegúrese de usarlo para mejorar el rendimiento! 
Más información sobre este texto de origen


Artículo Original: [hireaspnet.medium.com](https://hireaspnet.medium.com/10-best-practices-to-improve-asp-net-core-performance-f600e041a87b) 


