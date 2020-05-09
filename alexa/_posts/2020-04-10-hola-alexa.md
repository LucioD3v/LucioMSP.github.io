---
layout: post
title: ¡Hola Alexa!
image: /assets/img/blog/post-headers/amazon-alexa-ciegos.jpg
description: >
 Artículo donde se detalla todo sobre Alexa, el asistente virtual de Amazon.
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [alexa]
tags:
  - alexa
keywords:
  - alexa
  - skill
lang: es
---

El mundo del desarrollo abarca diferentes vertientes, el principal y pionero en todo es la web, el secundario se dirige a las aplicaciones móviles y hoy en día ha emergido otro, el cual se basa en la voz, es decir, dejar de lado una petición por texto para obtener una respuesta de igual índole.

Donde podemos encontrar este último, es en los asistentes de voz, los cuales están cada vez más presentes en nuestras vidas. Ya no solo en nuestros teléfonos móviles, sino en distintos dispositivos, tales como por ejemplo el  Google Home o Amazon Echo, ambos con distintas variantes.

Y así como hace algunos años se abrió un nuevo mundo de oportunidades para los programadores cuando llegaron las interfaces táctiles con los dispositivos móviles, ahora es el momento para que los desarrolladores se centren en las interfaces de voz. Por ello, en este artículo nos vamos a centrar en el asistente de voz creado por Amazon: Alexa. Comencemos por saber...
## ¿Quién o qué es Alexa?

Alexa es el servicio de voz de Amazon basado en la nube que alimenta la familia de dispositivos Echo, así como la aplicación complementaria de los smartphones Android y iOS. Desde el primer momento, nosotros como usuarios podemos darle a Alexa una serie de comandos de voz, como crear una lista de tareas, configurar la alarma (una de las que más utilizo), reproducir una canción o solicitar las noticias. Las tareas que Alexa realiza a petición del usuario se denominan “Alexa Skills”.
## ¿Qué es una Skill (habilidad) de Alexa?

Esencialmente es una aplicación Alexa basada en la voz. Alexa viene integrada ya con un gran número de habilidades, pero nosotros como desarrolladores podemos generar nuevas habilidades personalizadas, usando el Alexa Skill Kit (ASK) y posteriormente publicarlas en el Alexa App Store y utilizarlas desde cualquier dispositivo que incorpore Alexa. El ASK, es una colección de APIs y herramientas, maneja el trabajo duro relacionado con las interfaces de voz, incluyendo el reconocimiento de voz, la codificación de texto a voz y el procesamiento del lenguaje natural. ASK nos facilita a los programadores a desarrollar habilidades de forma rápida y sencilla.

Si ya tengo tu atención, déjame decirte que hoy ya puedes desarrollar alguna Skill para Alexa en español en los siguientes lenguajes de programación:

- Alexa Skills Kit SDK for Python 
- Alexa Skills Kit SDK v2 for Java
- Alexa Skills Kit SDK v2 for Node.js (Mi favorito)

## ¿Cómo funciona la comunicación dentro del Alexa Skill?

Los Skills de Alexa constan de dos componentes principales: Skill Interface y el Skill Service.

La interfaz de habilidades (Skill Interface) procesa las peticiones de voz del usuario y luego las mapea a intenciones dentro del modelo de interacción. Los intentos son acciones que cumplen con las peticiones habladas del usuario. Cada intención tiene al menos una expresión, una palabra, frase u oración predefinida que el usuario puede decir para invocar la intención. Si se detecta una intención específica, la interfaz de habilidades crea un evento codificado en JSON, que se transmite al servicio de habilidades.

El servicio de habilidades (Skill Service) determina qué acciones tomar en respuesta al evento codificado JSON recibido de la interfaz de habilidades. Al tomar una decisión, el servicio de habilidades devuelve una respuesta codificada JSON a la interfaz de habilidades para su posterior procesamiento. Después de procesar, la respuesta de voz se envía de vuelta al usuario a través del Echo Machine.

![image](/assets/img/blog/tutorials/alexa-hola/alexa-componentes-principales.png)

## ¿Cómo invoco alguna habilidad (Skill) desarrollada para Alexa?

En inglés, el método usual para invocar una Skill comienza con el uso de la palabra “open” y va seguido del nombre de la Skill. En español seria su traducción, un ejemplo de un nombre práctico, inteligente y memorable es el de la Skill Ayudante de Santa, entonces la invocación de susodicha seria:

“Alexa, abre Curiosidades de México".
## Ahora bien, ¿qué necesitamos para desarrollar una Skill para Alexa?

Para comenzar en este mundo solo requerimos:

- Una cuenta en Amazon Developer: [https://developer.amazon.com/](https://developer.amazon.com/)
- Una cuenta en AWS: [https://aws.amazon.com/](https://aws.amazon.com/) (obligatorio contar con una tarjeta de crédito).
- Un dispositivo de [Amazon Echo](https://www.amazon.es/s?k=alexa+echos&__mk_es_ES=%C3%85M%C3%85%C5%BD%C3%95%C3%91&ref=nb_sb_noss_2) (Opcional)

## Resumen

En esta ocasión hemos abordado las características principales de Amazon Alexa, en el próximo artículo brindare un tutorial paso a paso de cómo generar nuestra primera Skill para Alexa en español.

Y bueno, esto es todo, espero que te unas a la comunidad de desarrolladores de voz y generes Skills impresionantes. Recuerda además que si tienes alguna inquietud o pregunta, no dudes en ponerte en contacto conmigo o poner un comentario a continuación.

Más información:  [Amazon Developer](https://developer.amazon.com/es/) | [Alexa Skills Kit](https://marketplace.visualstudio.com/items?itemName=ask-toolkit.alexa-skills-kit-toolkit)

