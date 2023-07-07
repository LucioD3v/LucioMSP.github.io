---
layout: post
title: Conociendo AWS CodeWhisperer
description: En este artículo conoceremos de manera general el Github Copilot gratuito de AWS, mejor conocido como CodeWhisperer.
image: /assets/img/blog/post-headers/aws/amazon-codeWhisperer.jpg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [aws]
tags:
  - aws
  - codewhisperer
  - github
keywords:
  - aws
  - codewhisperer
  - github
  - copilot
lang: es
---

CodeWhisperer es la nueva herramienta de Amazon que permite construir diversos códigos guiándose por los comentarios de los desarrolladores.

## ¿Qué es CodeWhisperer?
CodeWhisperer es una herramienta para auxiliar a los programadores a través del autocompletado del código. Al igual que Copilot, cuenta con una IA que ha sido nutrida por diversos códigos y comentarios, por lo cual sugiere la integración de funciones basándose en los caracteres del código escrito. Además, examina el código en tiempo real y permite buscar vulnerabilidades.

Una de las particularidades de CodeWhisperer es que detecta el estilo personal de codificación de cada desarrollador, lo que lo hace de gran ayuda para los desarrolladores.

A diferencia de Copilot, CodeWhisperer está alimentado únicamente por códigos enteramente públicos. Por lo cual, resalta los fragmentos de código que son bastante similares a las referencias de la IA y tienen licencia, de esta manera, los usuarios pueden decidir si quieren integrar dicho fragmento o prefieren quitarlo. Con esto, se evitan los problemas legales.

CodeWhisperer busca que sus usuarios utilicen la inteligencia artificial responsablemente y generen aplicaciones correctas y seguras. Por el momento, es una extensión de AWS Toolkit es compatible con Java, JavaScript y Python

## ¿Cómo funciona?
Esta herramienta se nutre del aprendizaje continuo, por lo cual genera recomendaciones basadas en los comentarios, sean del lenguaje natural o del lenguaje de codificación. Amazon describe el funcionamiento en 4 pasos:

1- El desarrollador escribe el código.

2- El código se envía a CodeWhisperer.

3- Amazon CodeWhisperer usa todo el conocimiento que tiene para generar las recomendaciones para el desarrollo. Estas sugerencias suelen ser totalmente nuevas (aunque puede ocurrir que el código sea similar a otro ya registrado). De igual forma, evalúa otras áreas de oportunidad:

Escaneo de seguridad
Rastrea las referencias
Previene los sesgos
4- Envía el código de vuelta con las recomendaciones y señalizaciones.

A grandes rasgos, la escritura y análisis del código ocurren de manera simultánea, y puede ensamblarse usando servicios en la nube, así como las bibliotecas correctas para la funcionalidad.

Casos de uso 
Algunos de los usos de esta tecnología son:

Desarrollo de aplicaciones de última generación.
Proyectos que busquen acelerar el desarrollo del frontend y el backend.
Es posible usar CodeWhisperer para entrenar los modelos de machine learning.
Permite construir aplicaciones con los servicios AWS.
Si bien, muchos de estos son parte de otras plataformas, Amazon lo potencializo con las varias ventajas. Entre estas destacan:

 
Genera funciones enteras y bloques de código lógicos
Facilita el uso de los diversos servicios de AWS.
En el caso de tener un código ya registrado, proporciona la información del repositorio y la licencia.
Se automatizan las pruebas.
CodeWhisperer de Amazon no es solamente una “copia” de GitHub Copilot, pues ofrece un mejor seguimiento de la escritura individual de cualquier desarrollador, así como el reconocimiento de cualquier código que tenga una licencia.

Además de esto, las mentes detrás de CodeWhisperer desean que sea una herramienta usada de manera adecuada, logrando así, proyectos funcionales y éticos.


Gracias por leer mi artículo hasta el final. Espero que hayas aprendido algo especial hoy. Si disfrutó de este artículo, compártalo con sus amigos y si tiene sugerencias o pensamientos para compartir conmigo, escríbalos en el cuadro de comentarios.


## ¡Happy Coding! 

Más Información:

- Amazon CodeWhispererer- https://aws.amazon.com/es/codewhisperer/
- Amazon CodeWhisperer el asistente de programación de Amazon - https://www.adictosaltrabajo.com/2023/05/24/amazon-codewhisperer-el-asistente-de-programacion-de-amazon/
- Introducing Amazon CodeWhisperer, the ML-powered coding companion -  https://aws.amazon.com/es/blogs/machine-learning/introducing-amazon-codewhisperer-the-ml-powered-coding-companion/

