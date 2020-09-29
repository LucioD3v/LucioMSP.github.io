---
layout: post
title: Modelos de alojamiento en Blazor
description:
  Conociendo a detalle los modelos de ajolamiento en Blazor
image: /assets/img/blog/post-headers/blazorModels.png
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [blazor]
tags:
  - blazor
keywords:
  - blazor
lang: es
---

## Introducción

Blazor actualmente tiene dos modelos de alojamiento, Blazor del lado del Servidor y Web Assembly. El alojamiento del lado del servidor se lanzó en septiembre del 2019 y Web Assembly se lanzó oficialmente en mayo del 2020.

## Blazor Web Assembly

![image](/assets/img/blog/tutorials/blazor-hosting-models/BlazorWebAssembly.png)

# Pros

Web Assembly se ejecuta en el cliente, dentro del navegador, por lo que se puede implementar como archivos estáticos. A pesar de esto, las aplicaciones Blazor Wasm no se ejecutarán directamente desde el sistema de archivos local debido a las restricciones de seguridad del navegador.

Blazor Wasm puede funcionar sin conexión, es decir, cuando se pierda la conexión de red al servidor, la aplicación cliente puede seguir funcionando pero obviamente, no podrá comunicarse con el servidor para recuperar nuevos datos.

También puede ejecutarse fácilmente como una aplicación web progresiva, lo que significa que el cliente puede elegir instalar nuestra aplicación en su dispositivo y ejecutarla cuando lo desee sin ningún acceso a la red.

Con el código ejecutándose en la máquina del cliente, significa que la carga del servidor se reduce significativamente.

# Contras

El archivo blazor.webassembly.js inicia la aplicación cliente. Descarga todos los ensamblados DLL .NET necesarios, lo que hace que el tiempo de inicio de la aplicación sea más lento que en el lado del servidor.

Mono Framework interpreta .NET Intermediate Language, por lo que es más lento que ejecutar Blazor en el lado del servidor. La compilación con anticipación (AOT) está prevista para una versión futura.

Blazor Wasm aún no admite más de un hilo, por lo que todo el procesamiento se produce en el hilo de la interfaz de usuario, aunque las llamadas a servidores / JavaScript, etc. ocurren de forma asíncrona, por lo que no bloquea la capacidad de respuesta de la interfaz de usuario.

Además, Blazor Wasm solo funciona en los navegadores más nuevos y no es compatible con los motores de búsqueda (a menos que habilitemos la representación previa del lado del servidor).

## Blazor Web Assembly

![image](/assets/img/blog/tutorials/blazor-hosting-models/BlazorServerSide.png)

# Pros

El lado del servidor de Blazor procesa previamente el contenido HTML antes de enviarlo al navegador del cliente. Esto hace que sea compatible con los motores de búsqueda y no hay un tiempo de inicio perceptible.

Las aplicaciones del lado del servidor de Blazor funcionarán en navegadores más antiguos, ya que no hay requisitos para Web Assembly, solo HTML y JavaScript. A medida que el código se ejecuta en el servidor, también es posible depurar nuestro código .NET en Visual Studio.

# Contras

El lado del servidor de Blazor configura una sesión en memoria para el cliente actual y usa SignalR para comunicarse entre el .NET que se ejecuta en el servidor y el navegador del cliente. Todo el uso de memoria y CPU tiene un costo para el servidor, para todos los usuarios. También significa que el cliente está vinculado al servidor que lo sirvió por primera vez, por lo que no funciona con el equilibrio de carga.

Una vez que la página inicial se ha renderizado y enviado al navegador, el archivo blazor.server.js se conecta a cualquier evento de interacción del usuario relevante en el navegador para que pueda mediar entre el usuario y el servidor. Por ejemplo, si un elemento renderizado tiene registrado un evento @onclick, blazor.server.js se conectará a su evento de clic de JavaScript y luego usará su conexión SignalR para enviar ese evento al servidor y ejecutar el código .NET relevante.

Una vez finalizado el código .NET, Blazor volverá a representar los componentes en la página y luego enviará un paquete delta de HTML al navegador del cliente para que pueda actualizar su visualización sin tener que volver a cargar toda la página.
