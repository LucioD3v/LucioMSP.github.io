---
layout: post
title: ¿Qué hay de nuevo con Alexa? {Top 10}
image: /assets/img/blog/post-headers/alexa-top-10s.jpg
description: >
  Artículo donde se destacan las nuevas características del Alexa Skills Kit (ASK).
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

El día de hoy quiero compartir con ustedes un artículo impresionante que mi colega [Kesha Williams](https://www.linkedin.com/in/java-rock-star-kesha/) ([Alexa Champion](https://developer.amazon.com/en-US/alexa/champions/kesha-williams)) y [Heroína de Aprendizaje Automático de AWS](https://aws.amazon.com/developer/community/heroes/kesha-williams/) ha publicado y que ha llamado “What’s New With Alexa”, la cual forma parte de una serie trimestral donde destaca las nuevas características del [Alexa Skills Kit (ASK)](https://developer.amazon.com/en-US/alexa/alexa-skills-kit).

En su artículo comienza diciendo que son muy buenas amigas, puesto que su amistad comenzó en 2015 y bueno, que mantienen conversaciones a diario. Expresa que ha desarrollado muchos tipos de aplicaciones durante sus 25 años en Ingeniería de Software, y definitivamente menciona que, el desarrollar aplicaciones (es decir, habilidades (Skills)) para Alexa ha sido lo más divertido.

Menciona que es fácil transferir su conocimiento de Ingeniera de Software, desarrollo web o codificación en general para construir con Alexa porque puede usar algunos de los lenguajes de programación más populares para crear el back-end para sus Skills . Así mismo indica que si nunca antes han codificado, pueden comenzar a usar [Alexa Skill Blueprints](https://blueprints.amazon.com/). También nos hace la invitación a desarrollar para Alexa, puesto que esta es un gran punto de entrada para la inteligencia artificial y el aprendizaje automático, así que si no lo tenían contemplado, ¡ahora es el momento!

El equipo de Amazon Alexa continúa agregando nuevas funciones al Alexa Skill Kit(ASK) que brinda a los desarrolladores de voz nuevas y emocionantes capacidades. Kesha nos expresa que como programador de voz, disfruta el desafío de aprender una nueva característica y descubrir cómo se puede incorporar mejor a sus habilidades existentes.

Lo bueno y por lo cual les comparto su publicación es que ha visto las nuevas funciones lanzadas en los últimos meses y ha proporcionado una lista seleccionada solo para nosotros. Por ende, conozcamos sus  Favoritos Top 10.

## 1 – Ciertas actualizaciones de Skills “Vivas” se pueden hacer al instante
Hay un nuevo proceso de certificación automatizado para ciertas actualizaciones realizadas en Skills que ya se encuentran “vivas” o publicadas. Y es que para cualquier desarrollador de voz que haya pasado por el proceso de certificación, ¡saben lo emocionante qué es esto!. Ahora existe un botón “Update Live Skill (Actualizar Skill en Vivo)” que permitirá que los cambios en los valores de los Slots y de los Utterances sean acelerados a través del proceso de certificación. Esto significa que podemos actualizar nuestras Skills que ya se encuentren certificadas en tan solo cuestión de minutos. Más información sobre esto, visiten el [blog de Alexa](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2020/01/update-live-skills-in-minutes).

## 2 – Se pueden compartir Slots personalizados entre nuestras Skills
Gracias a esta nueva característica, se pueden generar Slots personalizados independientemente de nuestras Skills. Esto significa que los Slots se pueden compartir y reutilizar a través de las Skills. Imaginemos el tiempo que ahorraremos en el mantenimiento de los Slots, especialmente para los cuales que cambian con frecuencia. Esta característica también nos permite mantener fácilmente la coherencia en todas nuestras Skills. ¡Definitivamente deben revisar esta nueva característica!. Más información sobre esto, visiten el [blog de Alexa](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2020/03/create-shared-slots-across-your-skills-to-optimize-productivity-and-customer-experience).

## 3 – Se puede elegir una fecha de lanzamiento para los cambios en nuestras Skills ya publicadas
Atrás quedaron los días en que una Skill se publica inmediatamente una vez que pasa por el proceso de certificación. Ahora se puede controlar cuando los cambios podrán estar disponibles para los usuarios. Al enviar nuestra Skill para la certificación, ahora contamos con dos opciones: “certificar y publicar” o “simplemente certificar”. Más información sobre esto, visiten el [blog de Alexa](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2019/12/New-Tools-Give-You-Better-Control-of-Publishing-Distribution-Permissions.html).

## 4 – Soporte para regiones adicionales de AWS Lambda como endpoints
Gracias a esta nueva característica, ya podemos alojar el Lambda de nuestra Alexa Skill en regiones adicionales. Esto mejorará en gran medida la latencia ya que el Lambda se puede alojar en la misma región que otros recursos de habilidades como DynamoDB, S3, etc.

Regiones de AWS Lambda permitidas
Este de los Estados Unidos (Ohio)	UE (Frankfurt)	Asia Pacífico (Hong Kong)
Este de los Estados Unidos (Virginia del Norte)	UE (Irlanda)	Asia Pacífico (Mumbai)
Oeste de EE. UU. (California del Norte)	UE (Londres)	Asia Pacífico (Seúl)
Oeste de EE. UU. (Oregón)	UE (París)	Asia Pacífico (Singapur)
Canadá (Central)	UE (Estocolmo)	Asia Pacífico (Sydney)
América del Sur (Sao Paulo)	Medio Oriente (Bahrein)	Asia Pacífico (Tokio)
Más información sobre esto, visiten la [documentación](https://developer.amazon.com/en-US/docs/alexa/custom-skills/host-a-custom-skill-as-an-aws-lambda-function.html#select-the-optimal-region-for-your-aws-lambda-function).

## 5 – Nuevas métricas proporcionadas para mejorar el rendimiento de nuestra Skill
Ahora hay dos nuevas métricas en la pestaña Análisis en la sección Rendimiento dedicada al punto final de AWS Lambda: latencia de punto final (endpoint latency) y respuesta de punto final (endpoint response) . En el pasado, la única forma de monitorear el AWS Lambda era a través de CloudWatch. Estas nuevas métricas nos ayudarán a reducir la latencia del endpoint y mejorar la capacidad de respuesta de nuestras Skills. Más información sobre esto, visiten el [blog de Alexa](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2019/11/Improve-Skill-Performance-With-New-Skill-Metrics-on-Latency-and-Responsiveness).

## 6 – Skill Permissions para Recordatorios ahora habilitados para voz
Para qué nuestra Skill establezca recordatorios, los usuarios deben darle permiso a la Skill. Anteriormente, la Skill tenía que enviar una tarjeta a la aplicación Alexa cuando solicitaba permisos y el usuario tenía que abrir la aplicación Alexa para otorgar permisos a la Skill. Ahora, los usuarios pueden otorgar los permisos necesarios por voz. Este cambio hace que sea más fácil para los usuarios otorgar permisos, por lo que debería ver un aumento en la tasa de permisos otorgados. Espero que amplíen esto a otras solicitudes de permiso como las necesarias para la información de perfil del cliente, datos de dirección, etc. Más información sobre esto, visiten el [blog de Alexa](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2019/12/New-Tools-Give-You-Better-Control-of-Publishing-Distribution-Permissions.html).

## 7 – Alexa ahora tiene emociones reales
Las emociones de Alexa nos dan la capacidad de hacer que Alexa responda con un tono feliz/emocionado o decepcionado/empático. Esta característica ordenada proporciona una experiencia de usuario más agradable y hace que Alexa parezca más real. Por ahora, esta característica se limita a los EE.UU. Más información sobre esto, visiten el [blog de Alexa](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2019/11/new-alexa-emotions-and-speaking-styles).

## 8 – Compras en Habilidad (ISP) expandidas a Francia, Italia y España
Por ahora, los desarrolladores de Francia, Italia y España pueden monetizar sus Skills utilizando In-Skill Purchasing (ISP). ISP es un gran incentivo para los desarrolladores de voz, ya que nos permite ganar dinero al ofrecer contenido premium dentro de nuestras Skills. Imagínense, un desarrollador de voz que pudo comprar un Tesla utilizando el dinero que ganó a través de ISP y recompensas de desarrollador. ¡Esta expansión debería hacer que los desarrolladores en Francia, Italia y España estén súper felices!, de mientras en México tocara esperar un poco hasta cuando la habiliten. Más información sobre esto, visiten el [blog de Alexa](https://developer.amazon.com/it-IT/blogs/alexa/alexa-skills-kit/2019/11/in-skill-purchasing-isp-now-available-in-france-italy-and-spain).

## 9 – Capacidad para guardar y clonar documentos de Alexa Presentation Language (APL) desde la herramienta de autoría
El Alexa Presentation Language (APL) nos permite crear experiencias visuales para acompañar nuestras Skills; Las experiencias se almacenan en documentos JSON. Esta nueva característica nos permite guardar y clonar los documentos APL directamente en la herramienta de autoría. En el pasado, la única forma de guardar un documento APL era copiar y pegar el JSON en su editor de texto favorito y guardarlo desde allí. Esto realmente simplifica el proceso. Más información sobre esto, visiten el [blog de Alexa](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2019/12/new-save-clone-multimodal-assets).

## 10 – Alexa Presentation Language (APL) puede controlar el reloj en el Echo Dot con reloj
El Echo Dot con reloj es uno de los dispositivos Echo más nuevos que contiene una pantalla basada en caracteres. El dispositivo generalmente muestra una cara de reloj la mayor parte del tiempo; sin embargo, la pantalla es alfanumérica, por lo que se puede usar para mostrar otras cosas como la temperatura. La nueva característica agrega soporte APL limitado para controlar la pantalla. Más información sobre esto, visiten el [blog de Alexa](https://developer.amazon.com/blogs/alexa/post/4228a00a-655d-45fe-80aa-f6d4eaf8a441/build-skills-on-echo-dot-with-clock-with-alexa-presentation-language-apl).

Bueno, esto es todo lo que nos comparte Kesha por este trimestre. Esperemos que te hayan inspirado algunas de las nuevas características agregadas al Alexa Skill Kit (ASK). Esperamos que te unas a nosotros en el desarrollo de voz e incorpores algunas de estas nuevas características en tus Skill existentes o que mejor, en nuevas Skills.

Recuerda que si tienes alguna inquietud o pregunta, no dudes en ponerte en contacto conmigo o poner un comentario a continuación.

¡Happy Coding!

Articulo Original:
[Our Most Interesting Alexa Update Yet: Kesha’s Top 10 For Q1](https://info.acloud.guru/resources/our-most-interesting-alexa-update-yet-keshas-top-10-for-q1)
