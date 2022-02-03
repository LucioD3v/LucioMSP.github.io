---
layout: post
title: Top 10 - Mejores prácticas para ASP.NET Core
description: En este artículo conoceremos el top 10 de las mejores prácticas para mejorar el rendimiento de ASP.Net Core
image: /assets/img/blog/post-headers/aspNetCore.jpeg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [net]
tags:
  - asp
  - net
keywords:
  - asp
  - net
  - development
  
lang: es
---

Sinceramente una de las principales razones por las que ASP.NET Core es el framework favorito de muchos, es el rendimiento. Puesto que nos brinda a los desarrolladores una base estable para crear aplicaciones basadas en web. Cabe mencionar que es crucial revisar nuestras aplicaciones regularmente para cumplir con las expectativas y es por ello, que en este artículo se trataran algunos consejos esenciales para mejorar la velocidad y el rendimiento para las aplicaciones ASP.NET Core.

## Usa la última versión

¿Por qué hacer esto? Bueno, cada versión viene con las capacidades más recientes y avanzadas, por ende un rendimiento más rápido.
Al desarrollar aplicaciones con ASP.NET Core debemos de asegurarnos de utilizar la versión más reciente dado que Microsoft mejora constantemente su rendimiento en la versión más reciente con respecto a la versión anterior.

### 1. Evite el bloqueo de llamadas

Es importante diseñar su aplicación ASP.NET Core para ejecutar varios procesos a la vez. Puede lograr esto mediante el uso de una API asíncrona, ya que esta puede manejar miles de solicitudes y no depende de que se bloqueen las llamadas. En lugar de esperar a que finalice un trabajo asíncrono, comenzará a trabajar en un subproceso diferente.

El problema en las aplicaciones ASP.NET Core es bloquear la ejecución asíncrona a través de llamadas a Task. El subproceso se bloquea hasta que se completa la tarea y espera a que se complete. Ejecutar desde ASP.NET Core que ya este ejecutando subprocesos dentro del grupo de subprocesos estándar dará como resultado una programación de grupo de subprocesos innecesaria. En su lugar, podemos crear rutas de código activo que sean síncronas y llamen a E/S, acceso a datos. Aunado a patrones de API que se ejecutan durante largos períodos para ejecutar operaciones de forma asíncrona, con la finalidad de que puedan llevarse a cabo sin afectar a otros procesos.

### 2. Usar caché

Si busca mejorar el rendimiento de su aplicación, el método mejor conocido es el de reducir la cantidad de solicitudes realizadas al servidor cada vez. Funciona: se realiza una llamada al servidor y se guarda la respuesta, por lo tanto, la próxima vez que se realice una llamada para obtener la misma respuesta, en lugar de solicitar la ayuda del servidor esta información se compara con los datos almacenados. Y cuando se determina que es compatible, se lee de la base de datos en lugar de llamar al servidor.

Así es como el almacenamiento en caché puede ahorrar tiempo y mejorar el rendimiento general, reduciendo las llamadas al servidor con frecuencia. Es posible realizar el almacenamiento en caché del lado del servidor o del lado del cliente del lado del servidor, ya que ASP.NET Core nos permite diferentes tipos de almacenamiento en caché, incluido el almacenamiento en caché en la memoria de almacenamiento en caché de respuestas. Y también almacenamiento en caché de respuestas, almacenamiento en caché distribuido y más.

Por lo tanto la recomendación en este punto es: ¡siempre asegúrese de usar el caché para mejorar el rendimiento! 

### 3. Optimice el acceso a los datos

Para mejorar el rendimiento del software, necesitamos mejorar la eficiencia de la lógica de acceso a los datos. Dado que los datos se eliminan directamente de las bases de datos, recuperar cada vez lleva tiempo. Aquí hay algunos métodos que pueden aumentar el rendimiento de su aplicación.

- Reducir el número de llamadas HTTP
- En lugar de realizar varias conexiones a su servidor obteniendo los datos en tan solo una o varias llamadas.
- Cree un caché que almacenará datos sin cambios.
- No acceda a los datos antes de tiempo si no es necesario. Esto mejora la carga en la aplicación y puede ser lento.

Artículo Original: [hireaspnet.medium.com](https://hireaspnet.medium.com/10-best-practices-to-improve-asp-net-core-performance-f600e041a87b) 

