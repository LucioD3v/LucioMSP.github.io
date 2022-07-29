---
layout: post
title: ¿Qué es Blazor WASM?
description:
  En este tutorial conoceremos los conceptos de WebAssembly como parte integral de Blazor WASM y explora qué es Blazor WASM, cómo funciona, los problemas que resuelve, sus características y el tipo de aplicaciones para las que es adecuado.
image: /assets/img/blog/post-headers/blazor/blazorWASM.jpg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [blazor]
tags:
  - blazor
  - wasm
  - webassembly
keywords:
  - blazor
lang: es
---

# ¿Qué es Blazor WASM?

Como ya hemos visto o como ya sabemos, Blazor WASM (o Blazor WebAssembly) es un marco (framework)) de aplicación web de una sola página que nos permite crear aplicaciones web de una sola página. Construido como parte del ecosistema .NET Core, Blazor usa C# para generar contenido dinámico para una rica experiencia del cliente.

## ¿Cómo funciona Blazor WASM?
Tradicionalmente, todas las páginas web están estructuradas con HTML, diseñadas con CSS y usan Javascript para introducir una interactividad dinámica. C# como lenguaje no se creó para ejecutarse de forma nativa en los navegadores. Sin embargo, con la presencia de WebAssembly, el navegador ahora puede alojar el tiempo de ejecución de dotnet, lo que hace posible ejecutar y ejecutar código C#.

## ¿Cuál es el problema con Javascript en el navegador?
Si bien es cierto que Javascript es el idioma nativo de los navegadores web y puede ejecutarse en el frontend y backend. Pero, ¿es realmente necesario ejecutar C# en el navegador?

A continuación se destacan los beneficios de ejecutar C# en el navegador:

### Habilitación de Pila Completa (Full Stack)
El ecosistema dotnet core proporciona una de las implementaciones del lado del servidor más seguras y resistentes. Ocupa un lugar destacado entre los marcos de back-end más populares con su implementación de ASP.NET.

Al extender el tiempo de ejecución de .NET al navegador, Microsoft habilitó una verdadera experiencia de pila completa para permitir que los equipos usen el mismo conocimiento y bibliotecas de clases con las que están familiarizados del lenguaje C# en ambas pilas.

### Integración más fácil
En el desarrollo web, hay desarrolladores que se enfocan en el lado del cliente o en el lado del servidor. Si bien las clases de código no necesitan conocer los detalles de implementación de otras clases, los desarrolladores del lado del cliente necesitan conocimientos sobre la implementación del lado del servidor, y esto a veces puede resultar difícil al usar dos idiomas, especialmente cuando uno está fuertemente tipado y el otro no. .

Al usar Blazor WASM, el lado del cliente y el lado del servidor pueden compartir una base de código común en el mismo idioma, que se puede integrar fácilmente entre sí. Los desarrolladores del lado del cliente comprenderán la lógica del lado del servidor y cómo integrarla e implementarla sin problemas.

### Costos de desarrollo reducidos
Los lenguajes de programación tardan años en aprenderse y dominarse. Como los desarrolladores no son baratos, encontrar y pagar a los desarrolladores es una decisión estratégica para los equipos pequeños. Contar con un equipo de desarrolladores capacitados que puedan alternar entre las aplicaciones del lado del cliente y del servidor sin perder la comprensión de ambos lados mejora la colaboración, lo cual es vital para los equipos pequeños.

### Reutilización de código mejorada
El principio DRY es una de las formas más sencillas de prevenir y reducir los olores de código y el código espagueti. Al no tener que volver a escribir código nuevo, se reduce el acoplamiento y los cambios futuros no afectan a otras partes del código base.

Se pueden compartir y consumir bibliotecas .NET completas en Blazor WASM. Hacer uso de la lógica, la funcionalidad y las capacidades existentes permite a los desarrolladores centrarse en innovar más, ya que no están obligados a reinventar la rueda.

## Características de Blazor WASM
Blazor WASM tiene un conjunto único de características que lo convierten en una opción convincente para el desarrollo del lado del cliente.

### Componentes reutilizables
Con Blazor, puede crear componentes para usarlos en su aplicación. Los componentes son bloques de construcción para una interfaz de usuario, como formularios, tarjetas, tablas, cuadrículas y muchos más.

Estos componentes se pueden definir una vez y llamar varias veces. En esencia, los componentes son un grupo de elementos HTML que especifican la estructura de un sitio.

~~~bash

<Dropdown>
    <DropdownToggle Color="Color.Primary">
        Dropdown
    </DropdownToggle>
    <DropdownMenu>
        <DropdownItem>Action</DropdownItem>
        <DropdownDivider />
        <DropdownItem>Another Action</DropdownItem>
    </DropdownMenu>
</Dropdown>

~~~

Lo anterior es un componente de menú desplegable con Blazorise. Esto hace que el desarrollo sea más fácil y rápido y se puede llamar en cualquier momento que desee crear un menú desplegable, sin tener que escribir mucho código.

### Hot Reload
La recarga activa hace que el navegador se actualice automáticamente cuando se realizan cambios en el código base. Esto ayuda a mejorar la productividad de los desarrolladores, ya que necesitan reiniciar la aplicación para ver los efectos de esos cambios.

### Rendimiento rápido
Blazor WASM en la primera carga tarda un tiempo, ya que se debe descargar el entorno de tiempo de ejecución y otras dependencias. Luego, Blazor WASM se basa en el tiempo de ejecución descargado para ejecutarse a velocidades casi nativas en el navegador, lo que hace que las aplicaciones sean más rápidas.

## ¿Qué se puede construir con Blazor?
Esta sección destaca algunos de los mejores casos de uso para Blazor

## Aplicación Web Progresiva
Una aplicación web progresiva es una aplicación que se puede instalar y ejecutar como una aplicación nativa. La creación de PWA ayuda a los equipos a proporcionar experiencias móviles y de escritorio nativas para sus aplicaciones sin crearlas específicamente para esos entornos.

Para equipos pequeños, Blazor puede ser una forma de ahorrar costos sin sacrificar el rendimiento y la entrega.

### Aplicaciones de una sola página
Una aplicación de página única (SPA) es una aplicación web o sitio web que interactúa con el usuario al reescribir dinámicamente la página web actual con nuevos datos del servidor web, en lugar del método predeterminado de un navegador web que carga páginas nuevas completas.

En Blazor WebAssembly, cuando el cliente realiza una solicitud, se presenta como un poco de HTML, CSS y JavaScript, como todas las demás aplicaciones web. El archivo blazor.webassembly.js arranca la aplicación y comienza a cargar archivos binarios .NET que se pueden ver en la pestaña Red del navegador.

### Aplicaciones fuera de línea
Debido a que Blazor WASM descarga el tiempo de ejecución y las dependencias al inicio, la mayor parte de la representación se realiza en el lado del cliente. Como resultado, puede funcionar bien en escenarios donde no hay Internet o una conexión limitada.

## Desacreditando conceptos erróneos comunes
Al igual que todos los demás marcos de SPA, Blazor WASM tiene sus deficiencias. Aquí hay algunos para tomar nota

### Enorme carga útil y tamaño inicial lento
Las aplicaciones Blazor WASM pueden crecer rápidamente debido a los tiempos de ejecución necesarios para ejecutar C# en el navegador. Este gran tamaño puede hacer que el inicio inicial sea lento, y esto puede afectar una mala conexión a Internet. Afortunadamente, esto solo sucede una vez, por lo que las cargas subsiguientes son más rápidas y más pequeñas, ya que la mayor parte del trabajo pesado ya se ha realizado.

### No más JavaScript
El objetivo de Blazor WASM es permitir que C# se ejecute en el navegador, pero eso no significa que no necesitará javascript en absoluto. Blazor WASM no puede interactuar directamente con el DOM ni tener acceso a las API del navegador y, como resultado, es necesario llamarlas mediante javascript, en un proceso llamado Javascript Interop. Dado que Javascript es el idioma nativo de los navegadores, será necesario para acceder a las funcionalidades basadas en el navegador y

## Conclusión
En este artículo, vimos como es que Blazor ayuda a los equipos a crear interfaces de interfaz de usuario enriquecidas. Si tiene alguna sugerencia o consulta sobre este artículo, por favor póngase en contacto conmigo.

Aprovecho el espacio para invitarte a dejar un comentario si deseas que dé más detalles sobre cualquier cosa dentro de este artículo.

Más información:

- [Web Apps Blazor](https://dotnet.microsoft.com/en-us/apps/aspnet/web-apps/blazor)
- [Host and deploy ASP.NET Core Blazor WebAssembly](https://docs.microsoft.com/en-us/aspnet/core/blazor/host-and-deploy/webassembly?view=aspnetcore-6.0)

 ¡Hasta la próxima!