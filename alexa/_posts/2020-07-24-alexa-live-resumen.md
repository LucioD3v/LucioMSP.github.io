---
layout: post
title:  Alexa Live - Resumen [31 Nuevas Características de Desarrollo]
image: /assets/img/blog/post-headers/amazon-alexa-live.jpg
description: >
  Entrada dedicada a conocer las nuevas características que Alexa dio a conocer en su pasado evento Alexa Live 2020.
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
  - desarrollo
  - development
lang: es
---

El pasado miércoles 22 de Julio, Amazon llevó a cabo su evento denonimado "Alexa Live", el cual se centra en los desarrolladores y aquí, presentó 31 nuevas características que ayudaran a obtener experiencias más naturales y que nos permitirán como programadores a aumentar la participación de los usuarios con el asistente virtual.

Como era de esperar, algunos de estos son relativamente menores, pero algunos cambian significativamente la experiencia de Alexa para los más de 700,000 desarrolladores que hemos desarrollado Skills para la plataforma hasta ahora.

## Características

# Alexa Conversations

Este es un nuevo gestor de diálogos que facilitará y simplificará el trabajo de los desarrolladores, puesto que para mejorar la comprensión del lenguaje natural en Alexa, tanto en sentencias, como en palabras individuales, Amazon adoptará redes neuronales profundas, por ende se aplicará el aprendizaje profundo.

Sinceramente no era una sorpresa que uno de los aspectos más destacados haya sido este, puesto que desde que la compañía lo mostró por primera vez en su evento [re: Mars](https://techcrunch.com/tag/remars-2019/) el año pasado, la mayoria de nosotros lo esperabamos con ansias, y es que imaginense, el poder facilitarle a los usuarios una conversación más natural con sus dispositivos Alexa, es algo inclreible.

"Alexa Conversations promete ser un gran avance para los desarrolladores y creará nuevas experiencias excelentes para los clientes", dijo Steven Arkonovich, fundador de Philosophical Creations.

# Alexa for Apps

Sinceramente y desde un punto de vista personal, esta nueva característica me llamo mucho la atención, esto por que la idea aquí es permitir que los desarrolladores móviles (me incluyo) lleven a los usuarios de las Skill en Alexa a sus aplicaciones móviles. 

Por ejemplo, para Twitter, esto podría significar decir algo como: "Alexa, pídele a Twitter que busque #AmazonLive", y la Skill de Twitter podría abrir la aplicación móvil.

Nota: Esta característica se encuentra de momento en vista previa.

# Skill Resumptions

Otra interesante característica nueva que se presentó, es la "Reanudación de Skills", la cual permite a un usuario volver a una habilidad pasada después de realizar una pausa larga o haber terminado otra tarea con Alexa.

Basicamente esta característica nos permite como desarrolladores tener nuestras Skills en segundo plano y luego proporcionar actualizaciones según sea necesario. Eso es útil para una aplicación de viaje compartido, por ejemplo, que luego puede proporcionar a los usuarios actualizaciones sobre cuándo llegará su automóvil. Este tipo de notificaciones proactivas son algo con lo que todas las plataformas de asistente están comenzando a experimentar, aunque la mayoría de los usuarios probablemente solo hayan visto algunas de ellas en su uso diario hasta ahora.

Lo malo, es que de momento solo se encuentra disponible en versión preliminar para el idioma inglés de EE.UU.

# Quick Links for Alexa & NFI

Uno de los mayores problemas que se tiene actualmente es que los usuarios puedan encontrar o descubrir nuestras Skills, el cual no solo presenta la empresa Amazon, sino que es un problema que existe en todas las plataformas de voz y es probablemente una de las razones por las cuales la mayoría de las personas solo usan una fracción de las Skills actualmente disponibles para ellos.

Lo bueno es que el equipo de desarrollo ya analizo esto y lanzo dos nuevas características que nos ayudaran a que nuestras habilidades lleguen a los usuarios.

La primera de estas es la versión beta de Quick Links for Alexa, la cual nos permite crear enlaces desde nuestras aplicaciones móviles, sitios web o anuncios a una nueva interfaz de usuario.

Nota: De momento solo se encuentra en versión beta para los idiomas inglés y español de EE.UU.

La segunda característica nueva es el kit de herramientas de interacciones sin nombre (Name-Free Interactions / NFI), la cual nos permite proporcionar señales adicionales que Alexa puede tener en cuenta al lanzar nuestra Skill. Con el kit de herramientas, podemos configurar hasta cinco frases de inicio sugeridas. Por ejemplo, para una habilidad de planificación de viajes, una de estas frases puede ser: "Alexa, ayúdame a planificar mi viaje". También podemos indicar intenciones específicas en nuestras Skills, esto para que Alexa las considere. 

El kit de herramientas de NFI también proporciona un panel de invocación que muestra las rutas que utilizan los clientes para invocar nuestras Skills. Si bien los resultados serán diferentes para cada habilidad, algunos de los primeros en adoptar el kit de herramientas NFI vieron un aumento de hasta un 15% en los diálogos.

Nota: esta característica tambien se encuentra en su versión preliminar.

# Alexa Web API for Games

También introdujeron la API Web para Juegos, la cual permitirá a los programadores de habilidades crear experiencias controladas por voz para algunos dispositivos Fire TV y Echo Show, utilizando tecnologías como HTML5, WebGL y Web Audio. 

# APL for Audio

Creo que esta característica fue una de las mejores, puesto que se agrego el APl para audio, el cual proporciona herramientas para mezclar voz, efectos de sonido y música en tiempo de ejecución; Con APL para audio, podemos ofrecer experiencias de audio emocionantes e inmersivas, sin el tiempo, el esfuerzo y el costo necesarios para la premezcla. Audible, Creativity Inc, Doppio Games, Krogoor Entertainment Studio, Stoked Skills y Volley ya están usando esta nueva APL característica. De momento se encuentra en su fase beta.

Asi mismo, la actualización a APL 1.4, que ahora agrega cuadros de texto editables, controles de interfaz de usuario para que podamos simplemente arrastrar y soltar. Y algo muy bueno que llega junto a esta mejora, es la de poder navegar hacia atrás. Aunado a lo anterior, APL 1.4 permite incluir animación y gráficos vectoriales.

## Alexa Live On-Demand

Si ter perdiste las sesiones del evento, no te preocupes puesto que las puedes revivir en el [Alexa Live On-Demand](https://build.amazonalexadev.com/Alexa-Live-on-Demand-1.html?aliId=eyJpIjoiZ1BkYzF6NmYwQzlnQlpBZCIsInQiOiJueEI0cXNRUkFaOHFTUndtaEZxTnlnPT0ifQ%253D%253D).

![image](/assets/img/blog/tutorials/alexa-live-resumen/alexaliveOnDemand.png)

## Conclusión

No cabe duda que Amazon ha trabajado arduamente en todas y cada una de las 31 características anunciadas durante la presentación del Alexa Live, incluidas las actualizaciones de ASK SDK y herramientas, creo que tenemos mucho que leer y experimentar para poder mejorar nuestras Skills existentes.

Y bueno, esto es todo, espero que te haya inspirado y que te unas a nosotros en el desarrollo de voz. Recuerda que si tienes alguna inquietud o pregunta, no dudes en ponerte en contacto conmigo o poner un comentario a continuación.

Más información: [Alexa Skill Kit Blog](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2020/07/31-new-features-to-unlock-more-natural-and-immersive-alexa-experiences)

¡Happy Coding!