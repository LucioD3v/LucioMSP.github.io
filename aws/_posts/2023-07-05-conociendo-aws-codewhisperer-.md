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

Antes de comenzar, tengamos en cuenta que GitHub Copilot ha tenido gran aceptación en el mercado, por ello es que grandes empresas han comenzado a buscar otras alternativas para poder albergar sus códigos. Tomando esto en consideración, Amazon tomo la delantera y opto por lanzar CodeWhisperer, misma que se puede resumir como la nueva herramienta que permite construir diversos códigos guiándose por los comentarios de los desarrolladores.

## ¿Qué es CodeWhisperer?
CodeWhisperer es una herramienta para apoyar los programadores a través del autocompletado del código. Es decir, nos ayuda a hacer pair programming basado en IA que generá sugerencias de código en tiempo real en nuestro IDE para ayudarnos a crear software. Al igual que Copilot y como ya lo mencioné, cuenta con una Inteligencia Artificial que ha sido nutrida por diversos códigos y comentarios, por lo cual sugiere la integración de funciones basándose en los caracteres del código escrito. Además de examinar el código en tiempo real nos permite buscar vulnerabilidades.

Una de las particularidades de CodeWhisperer es que detecta el estilo personal de codificación de cada desarrollador, lo que lo hace de gran ayuda para los desarrolladores.

A diferencia de Copilot, CodeWhisperer está alimentado únicamente por códigos enteramente públicos. Por lo cual, resalta los fragmentos de código que son bastante similares a las referencias de la IA y tienen licencia, de esta manera, los usuarios pueden decidir si quieren integrar dicho fragmento o prefieren quitarlo. Con esto, se evitan los problemas legales.

CodeWhisperer es una extensión de AWS Toolkit y es compatible con Java, JavaScript y Python:

![image](/assets/img/blog/tutorials/aws-codewhisperer/vscode.jpeg)

### Nota Importante: 
CodeWhisperer Individual es gratuito, solo se requiere un inicio de sesión con AWS Builder.

## ¿Cómo funciona?
Conforme se vaya programando (tirando/escribiendo código), CodeWhisperer analiza los comentarios en inglés y código circundante para ayudar en el proceso de escritura de código. Utiliza un gran modelo de lenguaje (LLM) entrenado con una gran cantidad de código fuente, incluyendo código de Amazon y de código abierto. Al escribir código, CodeWhisperer sugiere fragmentos de código directamente en el editor, lo que acelera el proceso de creación de código.

Las sugerencias de CodeWhisperer están diseñadas para completar la tarea en cuestión. Puede aceptar rápidamente la sugerencia principal presionando la tecla de tabulación. También puede explorar más sugerencias utilizando las teclas de flecha o continuar escribiendo su propio código.

Es importante tener en cuenta que siempre se deben revisar las sugerencias antes de aceptarlas. Es posible que sea necesario realizar modificaciones para garantizar que funcionen según lo esperado.

### Video: AWS CodeWhisperer, el GitHub Copilot Gratuito de AWS

<iframe width="560" height="315" src="https://www.youtube.com/embed/fy5UUQ0aeq0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Resumen
AWS CodeWhisperer no es solamente una “copia” de GitHub Copilot, ya que ofrece un mejor seguimiento de la escritura individual de cualquier programador. Aunado a esto, las mentes detrás de CodeWhisperer desean que sea una herramienta usada de manera adecuada, logrando así, proyectos funcionales y éticos.

Espero que hayas aprendido algo especial hoy. Si disfrutaste de este artículo, apoyame compartiendolo con tus amigos y si tienes alguna sugerencia o pensamiento para compartir conmigo, pasa a dejarlo en el cuadro de comentarios.

## ¡Happy Coding! 

Más información:

- [Amazon CodeWhispererer](https://aws.amazon.com/es/codewhisperer/) 
- [Amazon CodeWhisperer el asistente de programación de Amazon](https://www.adictosaltrabajo.com/2023/05/24/amazon-codewhisperer-el-asistente-de-programacion-de-amazon/)
- [Introducing Amazon CodeWhisperer, the ML-powered coding companion](https://aws.amazon.com/es/blogs/machine-learning/introducing-amazon-codewhisperer-the-ml-powered-coding-companion/)

