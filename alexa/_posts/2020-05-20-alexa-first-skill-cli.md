---
layout: post
title: Guia - Creando mi primera Alexa Skill mediante ASK CLI 
image: /assets/img/blog/post-headers/alex-skills-banner.jpg
description: >
 Tutorial de cómo puedes desarrollar tu primera Skill mediante ASK CLI.
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
  - cli
lang: es
---

El día de hoy les voy a compartir el cómo pueden desarrollar su propia Skill mediante ASK CLI.

Recordemos que aunque no tengais un Amazon Echo, podeis usar el simulador que te ofrece Amazon para hacer las pruebas.

Pasos para desarrollar una Skill en Alexa
Esto es lo que hariamos
1.- Crear una cuenta en AWS
2.- Crear una cuenta de desarollador
3.- Instalación del ask-cli y configuración con AWS
4.- Crear nuevo proyecto y explicación de la estructura.
5.- Picar código
6.- ask deploy
7.- Testing y a certificación!

# 1. Crear una cuenta en AWS
Lo primero que tenemos que hacer es abrirnos una cuenta en Amazon Web Services (AWS), esto lo necesitaremos para usar la herramienta Lambda que nos permitirá incluir alli el código del backend de nuestra Skill. Usar Lambda es totalmente gratuito a menos que superemos las 1.000.000 peticiones al mes.

Para abrir una cuenta en AWS simplemente tenemos que ir a Amazon y seguir los pasos. Te pedirá los datos de la tarjeta, pero eso es simplemente para la verificación de la cuenta.

Cuando hayamos abierto una cuenta en AWS, empezará a contar un año de pruebas de otros servicios como por ejemplo EC2, que podrías usarlo para otras cosas 🙂

# 2. Crear una cuenta de desarollador
Una vez abierto una cuenta en AWS, tenemos que abrir una cuenta de desarrollador en amazon, lo puedes hacer en el siguiente enlace: developer.amazon.com

Estando logueado, veremos un panel para poder crear skills, alli nosotros NO le vamos a dar, ya que vamos a usar el ASK-CLI para hacer deploy de nuestro codigo de la Skill.

# 3. ASK-CLI
Para instalar ask-cli necesitamos tener instalado node, podemos comprobarlo ejecutando



![image](/assets/img/blog/skills-logos/consejosdelAbuelo.png)



Y bueno, esto es todo, espero que te unas a la comunidad de desarrolladores de voz y generes Skills impresionantes. Recuerda además que si tienes alguna inquietud o pregunta, no dudes en ponerte en contacto conmigo o poner un comentario a continuación.