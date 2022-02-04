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

Sinceramente una de las principales razones por las que ASP.NET Core es el framework favorito de muchos, es el rendimiento. Puesto que nos brinda a los desarrolladores una base estable para crear aplicaciones basadas en web. Cabe mencionar que es crucial revisar nuestras aplicaciones regularmente para cumplir con las expectativas y es por ello que, en este artículo se trataran algunos consejos esenciales para mejorar la velocidad y el rendimiento para las aplicaciones ASP.NET Core.

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
- En lugar de realizar varias conexiones a su servidor obteniendo los datos en tan solo una o varias llamadas
- Cree un caché que almacenará datos sin cambios
- No acceda a los datos antes de tiempo si no es necesario. Esto mejora la carga en la aplicación y puede ser lento

### 4. Optimizar código personalizado

La optimización del código y la lógica empresarial ayuda a mejorar el rendimiento de las aplicaciones, por lo tanto esto es lo que podriamos realizar:

- Crear un registro y autenticación personalizados o algún controlador personalizado que se ejecute cada vez que se solicite.
- No ejecutar procedimientos personalizados de ejecución prolongada en la capa lógica o el middleware. Ya que bloqueará la solicitud del servidor y aumentará el tiempo para obtener los datos de la aplicación. En su lugar, podemos optimizar el software en el lado del cliente o del servidor.
- Complete de forma asincrónica tareas de ejecución prolongada para asegurarse de que otras tareas no se vean afectadas.
- La comunicación cliente-servidor en tiempo real es SignalR que funciona de forma asíncrona.

### 5. Usar middleware de almacenamiento en caché de respuestas

Cree código rápido mediante el uso de elementos de Middleware que puedan optimizar las rutas de código de uso frecuente. Almacene las respuestas y sírvalas desde el caché. Se recomienda emplear herramientas para perfilar el rendimiento como PerfView para encontrar rutas de código activas.

### 6. Minimice las asignaciones de objetos grandes

Aunque el recolector de basura (garbage) de .Net Core está a cargo de todas las asignaciones y las liberaciones de memoria por cuenta propia dentro de la aplicación ASP.NET Core. La limpieza de objetos a los que no se ha hecho referencia requiere tiempo del CPU. Por lo tanto, nosotros como desarrolladores debemos evitar colocar objetos no deseados en rutas de código activo. La recolección de basura puede ser costosa y acumular enormes generaciones como generación. Eso requiere una suspensión indefinida del rendimiento de la aplicación para borrarlo. Una asignación y limpieza frecuente podría ralentizar el rendimiento de la aplicación.

### Consejos:

- Almacenar en caché objetos más grandes porque ayuda a evitar asignaciones costosas.
- Utilice un grupo de arreglos para mantener arreglos masivos.
- No asigne objetos grandes a rutas de código activo.

### 7. Usa la serialización JSON

.NET Core 3.0 utiliza System.Text.Json para realizar la serialización JSON. Esto significa que puede escribir y leer JSON de forma asíncrona. sin esperar a que se completen las otras tareas. Utilice JSON ya que puede mejorar el rendimiento de la aplicación más que Newtonsoft.Json. El espacio de nombres Json ofrece alto rendimiento y baja asignación y capacidades compatibles. Ese objeto en la serialización de texto JSON y el proceso de deserialización del texto JSON en objetos.

### 8. Usa la compresión de respuesta

La compresión del tamaño del archivo es un factor diferente que puede mejorar el rendimiento. La compresión de respuesta reduce el tamaño del archivo en ASP.NET Core puesto que está disponible como un componente de middleware. Cabe señalar que la mayoría de las respuestas no están comprimidas de forma nativa. Este suele ser el caso con CSS, JavaScript, HTML, XML y JSON.

* Importante:

- No comprima archivos de menos de 150 a 1000 bytes.
- No comprima archivos comprimidos de forma nativa como imágenes PNG.

### 9. Minimiza las excepciones

El proceso de lanzar y capturar excepciones puede ser más lento que otros patrones de código. Por lo tanto, no deben usarse con poca frecuencia y no deben usarse para regular el flujo normal de programas.

### Tips:

- Lanzar o capturar excepciones por imprevisibilidad o circunstancias inusuales.
- Cree lógica de código para identificar y tratar situaciones que pueden causar excepciones.

Se pueden utilizar herramientas de diagnóstico de aplicaciones como Application Insights para identificar errores comunes en las aplicaciones y ver cómo funcionan.

## Consejos para mejorar el rendimiento

* Preferir ReadFormAsync sobre el formulario de solicitud
* No almacene IHttpContextAccessor.HttpContext en un campo
* No abra HttpContext a través de varios subprocesos, ya que no es seguro y puede causar un comportamiento indefinido, tels como bloqueos o corrupción de datos.
* No registre los servicios que se inyectan en los controladores a través de subprocesos en segundo plano.
* No modifique los encabezados ni el código de estado después de que se haya iniciado el cuerpo de la respuesta HTTP, porque ASP.NET Core no almacena en búfer el cuerpo de la respuesta HTTP.

## 10. Mejoras del lado del cliente

- Agrupación y Minificación

Optimice su contenido antes de cargarlo usando minificación. Asi mismo asegúrese de reducir el código y cargar todos los activos del lado del cliente. Una vez que haya reducido los archivos, júntelos para que se carguen más rápido. Al igual que con el archivo zip. Luego comprímalo y hagalo zip.

- Cargar JavaScript al final

Asegúrese de cargar los archivos JavaScript en último lugar. Con este método, su sitio web se completará en poco tiempo, además cuando se ejecuta JavaScript, los elementos DOM ya están allí. Por lo tanto, su aplicación se puede ser más rápida.

- Reducción de Imágenes

Las imágenes grandes requieren mucho esfuerzo para cargar. En cambio, puede reducir las imágenes con herramientas de compresión para reducir la velocidad de carga.

- Uso de CDN

Si está utilizando bibliotecas de terceros para CSS y JavaScript que viene con una versión de CDN. Debe intentar usar la ruta de su archivo CDN en lugar de descargar los archivos de la biblioteca. CDN tiene múltiples servidores en diferentes zonas. Si está utilizando un sitio dentro de una sola región, descargará el archivo CDN a través del servidor. Al acceder al sitio, que es más rápido que cargar automáticamente el archivo de biblioteca grande.

--------------------------------------------------------------------------------------

Artículo Original: [hireaspnet.medium.com](https://hireaspnet.medium.com/10-best-practices-to-improve-asp-net-core-performance-f600e041a87b) 
