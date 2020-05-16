---
layout: post
title: Conceptos Generales [Construyendo mi Alexa Skill]
image: /assets/img/blog/post-headers/alexa-header-primera-skill.jpg
description: >
 Tutorial donde se detalla paso a paso como desarrollar nuestra primera Alexa Skill desde la consola de Amazon Alexa.
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

En mi artículo anterior ([Hola Alexa](https://luciomsp.github.io/alexa/2020-04-10-hola-alexa/)) vimos una introducción sobre el servicio de voz de Amazon y las "habilidades" (aplicaciones) que se le pueden integrar, estas mejormente conocidas como Skills.

Si bien ya sabemos que podemos hacer que Alexa pueda ejecutar cualquier tipo de tarea a través de comandos de voz, hay que saber como es que funciona dicho proceso.

Para poder desarrollar una Skill es necesario el Alexa Skill Kit, ([el cual vimos detalladamente en una publicación previa](https://luciomsp.github.io/alexa/2020-04-20-alexa-skill-kit/)) recordemos que es una colección de APIs y herramientas, que incluye el reconocimiento de voz, la codificación de texto a voz y el procesamiento del lenguaje natural.
## Ahora bien, ¿cómo está compuesto una Alexa Skill?

Las Alexa Skills constan de dos componentes principales: Skill Interface y el Skill Service.

Es decir, una parte cliente y una parte servidora. La primera es la responsable de definir el modelo de interacción (Interaction Model) con el usuario. Este modelo está compuesto de varias partes que veremos más adelante. Para la parte server vamos a usar AWS Lambda que, de igual manera veremos en publicaciones futuras.

En este artículo nos centraremos en generar la Skill Interface, esto usando la [Alexa Developer Console](https://developer.amazon.com/alexa/console/ask). Una vez que accedemos con nuestra cuenta podemos iniciar a crear nuestras skills. 

![image](/assets/img/blog/tutorials/alexa-construyendo-mi-alexa-skill/Image1.jpg)

Si ya hemos generado una que otra, podremos ver el listado de estas con cierta información, así como con acciones directas sobre algunas secciones, como las analíticas o el poder editar la misma, esconderla o eliminarla. Cabe mencionar que cuando publiquemos una skill, esta aparecerá por partida doble, pero con distinto estado, la de desarrollo (In Development) y la que está publicada (Live), en la “tienda de Alexa Skills” de Amazon.

![image](/assets/img/blog/tutorials/alexa-construyendo-mi-alexa-skill/Image2.png)
 
## Creación de una cuenta de desarrollador Amazon
Antes de ponernos manos a la obra necesitamos tener una cuenta de desarrollador de Amazon. La podemos hacer desde la [web oficial de Alexa](https://developer.amazon.com/alexa) y nos permitirá acceder al conjunto de servicios que ofrece Amazon a los desarrolladores. En nuestro caso, ingresaremos tanto a la [Alexa Developer Console](https://developer.amazon.com/alexa/console/ask) como a los [servicios AWS](https://aws.amazon.com/).

![image](/assets/img/blog/tutorials/alexa-construyendo-mi-alexa-skill/Image3.png)

## Creando la Alexa Skill
Al comenzar a crear nuestra skill se nos solicitan cuatro cosas: el nombre, idioma, el modelo y el método para alojar nuestro backend.

- Skill Name
El nombre de la skill y el nombre de invocación (que normalmente son el mismo), es la manera en que le diremos a Alexa que queremos usar determinada skill), en este caso será “Deseos de Navidad”.

Nota: el nombre de invocación puede ser editado posteriormente.

- Default language
Es el idioma en el que desplegaremos nuestra Skill, es decir, en el que la desarrollaremos y que posteriormente será invocada a tráves del mismo lenguage.

Nota: Cabe destacar que se pueden agregar más idiomas a nuestra habilidad después de la creación.

- Model
Los modelos preconstruidos son modelos de interacción que contienen un paquete de intenciones y expresiones que puede agregar a su habilidad.

Nota: Podemos diseñar nuestro propio modelo personalizado o utilizar un prefabricado.

- Method
Este sirve para aprovisionar nuestros propios recursos de back-end o puede hacer que Alexa los aloje por nosotros. Si decidimos que Alexa aloje nuestra habilidad, tendremos acceso al editor de código, que nos permitirá implementar código directamente en AWS Lambda desde la consola de desarrollador.

Importante: Los modelos disponibles dependen del idioma por defecto que seleccionemos. El idioma que seleccionaremos en este ejemplo será el de “Spanish (MX)”, el modelo que elegiremos para este tutorial será “Custom“ (ya que nos permitirá tener todo el control sobre la experiencia del usuario) y el método será "Alexa-Hosted (Node.js)". Una vez generado, se nos mostrará una ventana que nos dará acceso a todo lo necesario para el desarrollo de la skill.

![image](/assets/img/blog/tutorials/alexa-construyendo-mi-alexa-skill/Image4.png)

Puedes consultar los distintos tipos [aquí](https://developer.amazon.com/en-US/docs/alexa/ask-overviews/understanding-the-different-types-of-skills.html).

Luego daremos click en “Create skill”

Posteriormente se nos mostrará otra ventana donde deberemos de seleccionar una plantilla para agregar a nuestra habilidad, para este tutoríal elijamos la plantilla "Hello World Skill", la cual contiene un modelo de interacción y un código de fondo que funcionan juntos desde el principio.

![image](/assets/img/blog/tutorials/alexa-construyendo-mi-alexa-skill/Image5.png)

Una vez creado pasaremos a una ventana con diferentes pestañas. La pestaña de “build” será la que nos ofrece toda la funcionalidad necesaria para crear el modelo interactivo. La definición de este modelo no es más que generar un fichero JSON con una estructura concreta. Tendremos acceso a ese fichero si queremos, por ejemplo, versionarlo o crear otra skill partiendo de un modelo ya existente.

Siguiendo el “Skill builder checklist” del lado derecho completaremos de manera rápida lo mínimo necesario para tener la skill lista. Para esto, enfoquémonos en el lado izquierdo, aquí existen dos partes básicas pero relevantes: el interaction model del skill y el endpoint, el que indica el server que gestionará las peticiones al skill.

![image](/assets/img/blog/tutorials/alexa-construyendo-mi-alexa-skill/Image6.png)

Recordemos, en este articulo trabajaremos solo en la primera parte, así como de todos sus descendientes.

## Interaction Model

El interaction model consta de 4 partes, pero dos “obligatorias”:

- El nombre de invocación de la Skill.
- El conjunto de Intents (acciones) que deben corresponder con las peticiones de los clientes.

## Nombre de Invocación

Este es de suma importancia, puesto que es el cual el usuario use para comenzar a interactuar con nuestra skill y aunque parezca sencillo, debe cumplir una serie de requisitos. Por eso antes de querer tirar código se recomienda demasiado el hacer una buena elección del nombre del skill que se quiere desarrollar, debido a que referente a esto es que el usuario podrá invocarlo, el cual como sabemos ejecuta un intent de una sola vez, por ejemplo, “Alexa, abre deseos de navidad".

![image](/assets/img/blog/tutorials/alexa-construyendo-mi-alexa-skill/Image7.png)

## Intents

Un intent es en pocas palabras "lo que el usuario quiere que haga la skill cuando se activa por una determinada petición". Ejemplo: dime un deseo de navidad.

Si nos adentramos más detalladamente, un intent está compuesto de dos partes: los utterances (sentencias) que van a servir para invocarlo y los slots (argumentos) que puede tener, estos últimos son opcionales.

![image](/assets/img/blog/tutorials/alexa-construyendo-mi-alexa-skill/Image8.png)

A tener en cuenta:

- Un mismo intent no puede contener dos utterances repetidos.
- Los utterance los usa Alexa para inferir que intent corresponde a lo que desea hacer el usuario.

Nota: Cuando se manda a revisión, el proceso de certificación es una de las cosas que validan, en caso de tener errores, nos harán saber a través de un correo y tendremos que corregirlo (experiencia propia).

## Intents obligatorios

Al crear un nuevo skill, este conlleva 4 Intents obligatorios y predefinidos ya por Alexa, los cuales hay que considerar puesto que son de suma importancia, estos se encuentran debajo de “Built-in Intents“.

La verdad es fácil de comprender, debido a que no cuentan con slots, estos se pueden interpretar de la siguiente manera:

- CancelIntent – se usa para cancelar alguna interacción en proceso
- HelpIntent – es utilizado para solicitar ayuda al skill en proceso
- StopIntent – normalmente se centra en detener por completo el skill
- NavigateHomeIntent – este se podría entender como un “regresa al inicio”

Para cada uno de estos, es necesario declararle un/os utterances para su invocación.

![image](/assets/img/blog/tutorials/alexa-construyendo-mi-alexa-skill/Image9.png)

Nota: El intent que se genero por defecto (HelloWorldIntent) podemos personalizarlo, es decir, cambiar su nombre y sus utterances, pero para este caso lo eliminaremos.

## Custom Intents

Estos intents serán los que definan realmente los casos de uso que queremos cubrir en nuestro skill. Para este ejemplo solo se necesita uno: solicitar los deseos de navidad.

![image](/assets/img/blog/tutorials/alexa-construyendo-mi-alexa-skill/Image10.png)

Al crear un intent tenemos la opción de hacer uso uno existente de la librería de Alexa, como los built-in intent que eran obligatorios, o uno custom. Para este tutorial no hay uno existente que nos sirva.

El nombre del intent debe ser explicativo de la acción correspondiente que se quiere cubrir. Llamémosle “DeseoIntent“, el cual servirá para cubrir la petición de las frases. Una vez creado, lo único que tenemos que añadir son los utterance para ser invocado.

![image](/assets/img/blog/tutorials/alexa-construyendo-mi-alexa-skill/Image11.png)

Hay que pensar bien los utterances para el intent que se agregaran, puesto que entre más se añadan mejor será la identificación. [Aquí](https://developer.amazon.com/en-US/docs/alexa/custom-skills/best-practices-for-sample-utterances-and-custom-slot-type-values.html) les dejo una guía de buenas prácticas por idioma.

## Build Model

En la parte superior se encuentra el botón que nos permitirá construir nuestro modelo, presionémoslo. Cabe destacar que el modelo que se genera es un JSON con toda la información que hemos ido construyendo con la consola. Susodicho se puede modificar una vez generado.

![image](/assets/img/blog/tutorials/alexa-construyendo-mi-alexa-skill/Image12.png)

De momento es todo en esta primera entrega, en el siguiente artiículo veremos la parte lógica, es decir, la programación de nuesra Skill y realizaremos pruebas para corroborar su funcionamiento.

## Resumen

La [Alexa Developer Console](https://developer.amazon.com/alexa/console/ask) es el sitio principal a la hora de desarrollar una skill para Alexa. Ya que esta nos va a permitir cubrir gran parte del ciclo de desarrollo, pruebas, distribución, certificación y metrícas.


Más información:  [Amazon Developer](https://developer.amazon.com/es/) | [Alexa Skills Kit](https://marketplace.visualstudio.com/items?itemName=ask-toolkit.alexa-skills-kit-toolkit)

Si estas interesado en saber más sobre el desarrollo de Alexa Skills, puedes unirte a la comunidad de desarrolladores de voz en México, comunidad que lleva por nombre [vox: Ninja Alexa](https://www.facebook.com/groups/voxAlexaSkills). 

Recuerda además que si tienes alguna inquietud o pregunta, no dudes en ponerte en contacto conmigo o poner un comentario a continuación.


