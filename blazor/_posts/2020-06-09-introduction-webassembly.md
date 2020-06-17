---
layout: post
title: Introducción a WebAssembly
description: >
  Conociendo a detalle WebAssembly
image: /assets/img/blog/post-headers/web_assembly.png
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [blazor]
tags:
  - blazor
keywords:
  - blazor
  - webassembly
lang: es
---

## Introducción

Hoy en día las aplicaciones que se ejecutan en navegadores, en lugar de ir instaladas en equipos de computo son cada vez más y muy completas. Un ejemplo de estas, son los programas de oficina como Microsoft 365 o Google Docs, que siempre presentan funciones nuevas y por ende requieren más recursos. Este tipo de aplicaciones web se ofrecen a menudo en JavaScript, pero cada vez más desarrolladores apuestan por WebAssembly: un nuevo planteamiento con resultados sorprendentes.

## ¿Qué es WebAssembly?

Si buscamos una descripción corta, sería que es un standard abierto que permite la ejecución de código binario en la Web, proporcionando un nivel de rendimiento superior al rendimiento ofrecido por un lenguaje interpretado como JavaScript.

Si no quedo muy entendido,  conozcamos su definición oficial.

## Definición Oficial

El sitio web oficial de WebAssembly ([Sitio Oficial de WebAssembly](https://webassembly.org/)) indica que:

Wasm es un formato de instrucciones binario para una máquina virtual basada en una pila (stack). Wasm esta diseñado como un destino portátil para la compilación de lenguajes de alto nivel como C/ C++/ Rust, permitiendo la implementación en la web para aplicaciones de cliente y servidor.

![image](/assets/img/blog/tutorials/blazor-webassembly/webassembly_binary.png)

## ¿Entonces...?

Sinceramente creo que esta definición no es muy fácil de comprender en un inicio, trataré de explicarlo no tan literalmente. Para mi Wasm es dar la posibilidad de que la web pueda ejecutar más de un lenguaje de programación, como lo son C++ y RUST a través de un proceso de ensamblaje, con este proceso mejoraremos el performance o la velocidad de nuestras aplicaciones y tenemos un sin fin de nuevas mejoras e innovación que podemos realizar en la web.

Y es que antes, los desarrolladores web podían crear aplicaciones en Internet, pero para ello había que recurrir a JavaScript, y para quienes lo han utilizado, sabemos que JavaScript es relativamente lento y, en determinados escenarios, se ve limitado. Por eso, el World Wide Web Consortium (W3C) ha impulsado este nuevo método. Sin embargo, para que Wasm pueda funcionar, el navegador debe ser compatible con este lenguaje. Por este motivo, Mozilla (Firefox), Microsoft (Edge), Apple (Safari) y Google (Chrome) han participado en el desarrollo.

En todas las versiones de navegador actuales de estos proveedores se pueden ejecutar aplicaciones en WebAssembly.

Actualmente, WebAssembly presenta un único inconveniente: se difunde con mucha lentitud. Los desarrolladores web están acostumbrados al trabajo con JavaScript y no hay planes para desbancarlo. La dirección del proyecto da una gran importancia a que en la comunicación Wasm se presente como una opción complementaria de JavaScript. Pero, gracias a la compatibilidad con los grandes proveedores de navegadores y el W3C, la difusión está comenzando a despegar. Esto también se debe a que los visitantes de las páginas web no tienen que realizar ningún paso por su cuenta: las aplicaciones web en WebAssembly se cargan de manera tan sencilla como el código en JavaScript, solo que más rápido.

## Ventajas de WebAssembly

* Alto rendimiento
* Estándar web abierto de W3C
* Sin limitaciones para el usuario
* Posibilidad de uso de realidad virtual en navegadores
* Compatible con todos los proveedores de navegadores
* No se requiere ningún lenguaje de programación nuevo
* Uso de C, C++ o Rust para la programación de aplicaciones web
* Tamaños de archivo reducido (perfecto para la navegación móvil)


Entonces, no hay pretextos o motivos para que los desarrolladores no empiecen a estudiar WebAssembly con más detenimiento.

Nota: Si quieres experimentar con WebAssembly por primera vez, puedes hacerlo en el [WebAssembly Studio](https://webassembly.studio/). Aquí hay disponible un entorno de desarrollo online para Wasm.
