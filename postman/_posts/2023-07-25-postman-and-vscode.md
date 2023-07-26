---
layout: post
title: La espera ha terminado, Postman & VS Code
description: Con la extensión de Postman en Visual Studio Code, los desarrolladores pueden realizar pruebas y colaborar con eficiencia, lo que los ayuda a optimizar el flujo de trabajo al trabajar con APIs y servicios web.
image: /assets/img/blog/post-headers/postman/vscode-postman.jpg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [postman]
tags:
  - postman
keywords:
  - development
  
lang: es
---

## Introducción

Postman es una poderosa herramienta para probar y desarrollar APIs de forma eficiente, ahora bien, integrada como una extensión en Visual Studio Code, nos permite a los desarrolladores enviar solicitudes HTTP, analizar respuestas y colaborar con equipos de manera sencilla y organizada.

![image](/assets/img/blog/tutorials/postman-vs-code/000.jpg)

Y bueno, se que a lo mejor muchos no estaran familiarizamos con esto, por ello y para que podamos entender un poco mejor, comencemos por el inicio...

### ¿Qué es una extensión?

Una extensión es un componente que agrega funcionalidades adicionales al editor de código base. Estas extensiones están diseñadas para mejorar la experiencia del usuario y aumentar la productividad al trabajar con diferentes lenguajes de programación y tecnologías.

### Ahora bien, ¿qué es Postman?

Postman es una plataforma colaborativa y una herramienta para probar, desarrollar y documentar APIs (Interfaces de Programación de Aplicaciones). Es ampliamente utilizada por programadores para simplificar el proceso de trabajar con APIs y servicios web.

Con Postman, los usuarios pueden enviar solicitudes HTTP a diferentes endpoints de una API, ya sea para obtener datos, enviar información o realizar operaciones específicas. Permite probar estas solicitudes con diversas configuraciones, como agregar encabezados, parámetros, autenticación, y manejo de diferentes tipos de datos en los cuerpos de solicitud y respuesta.

## Extensión de Postman en Visual Studio Code

El 11 de Mayo se libero la poderosa extensión Postman en VS Code, con lo cual ahora podemos disfrutar de pruebas de API ultrarrápidas y colaboración contextual dentro de nuestro editor favorito.

Con la extensión de Postman en Visual Studio Code, los desarrolladores podemos realizar diversas tareas relacionadas con APIs directamente desde nuestro entorno de desarrollo. Algunas de las funcionalidades más destacadas incluyen:

- Enviar solicitudes HTTP: Permite enviar solicitudes HTTP a diferentes endpoints de APIs, como GET, POST, PUT, DELETE, etc., para probar su funcionamiento y obtener respuestas.

- Autocompletado de rutas y parámetros: Facilita la escritura de rutas y parámetros de solicitud al ofrecer sugerencias y completar automáticamente a medida que escribes.

- Resaltado de sintaxis: Proporciona un resaltado de sintaxis claro y legible para solicitudes y respuestas, lo que facilita la lectura y comprensión de los datos.

- Gestión de colecciones: Permite crear, importar y exportar colecciones de solicitudes, lo que ayuda a organizar y compartir pruebas con otros miembros del equipo.

- Variables de entorno: Permite definir variables de entorno para adaptar fácilmente las solicitudes a diferentes configuraciones, como entornos de desarrollo, pruebas o producción.

- Configuración de autenticación: Facilita la configuración de diferentes métodos de autenticación, como Basic Auth, OAuth, API Key, etc., para probar APIs protegidas.

- Vista previa de respuestas: Muestra una vista previa clara y estructurada de las respuestas recibidas de la API, lo que ayuda a verificar los datos obtenidos.

- Documentación de API: Permite generar automáticamente documentación interactiva para las APIs basada en las colecciones creadas, lo que facilita la comunicación y el conocimiento de las funcionalidades de la API.

- Automatización con scripts: Permite escribir y ejecutar scripts para realizar pruebas automatizadas y pre y post-acciones en las solicitudes.

- Colaboración en equipo: Facilita el trabajo en equipo al permitir compartir colecciones, comentarios y documentación relacionada con las APIs con otros miembros del equipo.

### Nota: 
Esta extensión se encuentra actualmente en su fase beta.

## Instalación

[![image](/assets/img/blog/tutorials/postman-vs-code/01.jpg)](https://marketplace.visualstudio.com/items?itemName=Postman.postman-for-vscode&mkt_tok=MDY3LVVNRC05OTEAAAGNLu5DfcW1MU6YicyvExPcNsydyZJij82VP2vPxdQQH1uUEwEW6Z3F6GRYwor7f0ju9Iwj3Em6-W1bI3JvvO-wFB0enw2268WG3g6PpEm0Ch4)

Para instalar Postman existen dos maneras: haciendo clic en el banner de arriba y al abrir la página web, dar clic en el botón de “Install”, o desde la barra lateral Extensiones en VS Code, buscando Postman.

![image](/assets/img/blog/tutorials/postman-vs-code/00.jpg)

Si se sigue el camino de la segunda opción, solo seleccionemos la extensión y posteriormente clic en el botón de “Install”.

![image](/assets/img/blog/tutorials/postman-vs-code/02.jpg)

## ¿Cómo funciona?

La verdad es que es muy sencillo su funcionamiento, una vez que se tenga Postman instalado en nuestro Visual Studio Code, solo deberemos de firmarnos, es decir, iniciar sesión con nuestra cuenta de Postman.

### Paso a Paso - Iniciar Sesión

Primero, abramos la extensión del Código VS, posteriormente seleccionemos Iniciar Sesión (Sign In) en la barra lateral. 

![image](/assets/img/blog/tutorials/postman-vs-code/04.jpg)

La extensión abrirá una nueva pantalla que le indicará que inicie sesión desde su navegador.

![image](/assets/img/blog/tutorials/postman-vs-code/05.jpg)

En su navegador, seleccione un equipo de Postman y luego inicie sesión en Postman. 

![image](/assets/img/blog/tutorials/postman-vs-code/06.jpg)

Después de iniciar sesión, nos preguntará si deseamos abrir VS Code, al indicarle que lo haga, podemos cerrar la pestaña del navegador.

![image](/assets/img/blog/tutorials/postman-vs-code/07.jpg)

Al regresar a Visual Studio Code, se visualizarán los espacios de trabajo del equipo en la extensión de Postman. Cuando hagamos esto podremos ver el historial de solicitudes de ese espacio de trabajo en la barra lateral. 

![image](/assets/img/blog/tutorials/postman-vs-code/08.jpg)

Para obtener más información sobre cómo iniciar sesión en Postman, consulte la [documentación de Postman](https://learning.postman.com/docs/getting-started/postman-account/#signing-in-to-postman).

#### Importante: Tengamos presente que se debe iniciar sesión en Postman para poder utilizar la extensión de VS Code.

Si no se tiene una cuenta de Postman, habrá que crear una para iniciar sesión y usar la extensión de VS Code:

- Abramos la extensión del Código VS.
- Seleccionemos 'Crear cuenta' en la barra lateral. 
- La extensión abrirá una nueva pantalla que le indicará que cree una cuenta desde el navegador.
- En susodicho, ingresemos la información requerida y luego seleccionemos 'Crear cuenta gratuita'.

Para obtener más información sobre cómo registrarse en Postman, consulte la [documentación de Postman](https://learning.postman.com/docs/getting-started/postman-account/#signing-up-for-a-postman-account).

## Conclusión

En este artículo, aprendimos sobre Postman, las funciones y cómo realizar una primera solicitud GET API usando Postman y sinceramente es una de las extensiones que no debe faltar en tu Visual Studio Code. 

Por último, si tienen alguna sugerencia o consulta sobre este artículo, por favor póngase en contacto conmigo.

¡Hasta la próxima!
