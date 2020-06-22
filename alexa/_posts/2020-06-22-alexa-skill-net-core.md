---
layout: post
title: Alexa Skill con .Net Core & AWS Lambda
image: /assets/img/blog/post-headers/alexa-skill-net-core-header.png
description: >
 Tutorial de cómo desarrollar una Alexa Skill con .NET Core y AWS Lambda desde Visual Studio
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
  - .net
  - aws
  - visualstudio
lang: es
---

Las Skills de Alexa se pueden desarrollar utilizando las Lambda Functions de AWS o usando un servidor REST.Lambda Function es la implementación de Amazon de funciones serverless disponibles en AWS.Amazon recomienda usar las Lambda functions a pesar de que no sean fáciles de debuggear.Si bien puedes loggear en CloudWatch, no puedes poner un breakpoint y revisor el código.

Esto hace que debuggear una request que nos envía Alexa sea un completo desafío.Este post explica una solución simple pero útil: levantar un proyecto Web API para debug local y un proyecto de función Lambda para luego poder desplegar en AWS.Ambos proyectos ejecutarán el mismo código escrito en C#.

# Requisitos

Entonces, ya sabemos que las aplicaciones para Alexa se llaman habilidades, en esta ocasión vamos a construir una skill muy sencilla que le pida al usuario que adivine un número aleatorio entre 1 y 10. Para seguir, necesitaremos:

- .NET Core 2.1 SDK
- Una cuenta de desarrollador de Amazon (requerida para Alexa Development).
- Una cuenta de Amazon Web Services (nos mantendremos dentro del uso de nivel gratuito)
- Visual Studio 2019 (se puede hacer esto con Visual Studio Code, pero sus pasos diferirán un poco) 

# Alexa Developer Console

Una vez que contemos con la cuenta de desarrollador de Amazon, deberemos de dirigirnos a la consola de desarrollador de Alexa. Posteriromente deberemos de crear una nueva skill, asígnarle un nombre (Number Game).

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step01.png)

Despúes seleccionar 'Habilidad Personalizada' (Custom), puesto que no queremos un modelo prefabricado para este proyecto. 

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step02.png)

Y para los recursos de back-end de la habilidad, seleccione 'Aprovisione el Suyo' (Provision your own), ya que vamos a crear un Lambda Function y se lo atribuiremos a nuestra habilidad.

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step03.png)

Posteriormente deberemos seleccionar una plantilla, para nuestro ejemplo, elijamos la primera opcion: Start from scratch

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step04.png)

Una vez que creamos la Skill, deberíamos ver el panel de desarrollo principal. No estaremos escribiendo código en esta consola, pero crearemos el modelo de interacción para nuestra Alexa Skill. Este modelo define las instrucciones de voz que permiten a los usuarios conversar con la Skill.

Vamos a seguir la lista de verificación en el lado derecho de la consola para desarrollar nuestra Skill. El primer paso es configurar un nombre de invocación. Esta es la frase que hablará un usuario para iniciar nuestra aplicación; por ejemplo, "Alexa, abre curiosidades de Mexico". Los usuarios también pueden combinar el nombre de invocación con un comando, como "Alexa, dime un dato curioso de méxico" para obtener la información. 

Invocation Name: number games

En este ejemplo, usaremos "Alexa, open number games".

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step05.png)

Para definir la interfaz de voz para nuestra skill, deberemos asignarle una entrada hablada a las intenciones de nuestros controladores de servicio que se procesan de fondo. En nuestro juego de ejemplo, queremos proporcionar un comando para que el usuario inicie un nuevo juego. Entonces el usuario puede decir "nuevo juego", "jugar un juego", "iniciar un juego" o muchas otras variaciones de esto. 

Cada una de esas frases se llama uterrances. Independientemente de la redacción exacta, es importante saber que se desea activar la misma funcionalidad. Entonces dereremos generar una intención y asociar todas las expresiones de muestra que deseamos que active esta intención. 

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step06.png)

En el panel de control de Alexa Developer, hacemos clic en el elemento dos de la lista de verificación y generaremos una intención personalizada. Nómbremoslo NewGameIntent y luego agregue los enunciados de muestra (invente los suyos o use los del párrafo anterior). Esta es una intención muy básica porque no permitimos ninguna variable en la respuesta del usuario; tiene que coincidir exactamente con uno de nuestros enunciados.

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step07.png)

Luego, deberemos de crear otro Intent, llamado "AnswerIntent", esta manejara el intento del usuario de adivinar el número. 

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step08.png)

En este caso, lo que queremos es que usuario pueda brindar diversas opciones, por ende al igual que el Intent previo, deberemos de agregar algunas expresiones de muestra para manejar la entrada del usuario; Esto como vimos anteriormente se logra fácilmente, pero ¿cómo manejamos el número de conjeturas? Para esto existen los Slots: esta es una palabra o frase que representa información variable. Por ejemplo, un nombre, una ubicación geográfica, una fecha o, en nuestro caso, un número.

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step09.png)

Un enunciado con un slot utiliza llaves: "¿Es {número}?" - El espacio "número", debe estar definido, por lo que utilizamos AMAZON.NUMBER como nuestro tipo de Slots

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step10.png)

Cuando hayamos terminado, seleccionemos "Construir Modelo" para aplicar todos los cambios que hayamos realizado a la versión de desarrollo de nuestra Skill. 

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step11.png) - ![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step12.png) - ![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step13.png)

Además, si nos desplazamos hacia abajo más allá de la seccion de Intents y Slots, en el menú del lado izquierdo de la Consola, veremos la opcion de Editor JSON. Si hacemos clic, veremos el JSON que representa la interfaz de usuario de voz que hayamos definido (desde elnombre de invocación, los Intents, Utterances y Slots, etc).

# Visual Studio 2019

Ahora que hemos creado el modelo para manejar a un usuario que habla con Alexa, nos toca escribir el código del back-end de nuestra Skill.

Cabe recordar que puede ser una API escrita en cualquier idioma y alojada en cualquier lugar, pero Amazon recomienda Lambda (la versión AWS de Function as a Service). En resumen, Lambda nos permite ejecutar código sin preocuparnos por servidores u otra infraestructura (computación sin servidor). Otra razón para usar Lambda es que para muchos casos de uso, es prácticamente gratis (hasta para 1 millón de solicitudes por mes).

Una excelente manera de compilar e implementar funciones de Lambda es usar Visual Studio 2019 junto con AWS ToolKit for Visual Studio. Entonces para esto debimos de haber instalado el kit de herramientas de AWS,  para posteriormente iniciar Visual Studio y crear un nuevo proyecto de AWS Lambda en .NET Core (puede ser con pruebas o sin ellas, en esta ocasion  no cubriré las pruebas unitarias)

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step14.png)

# Alexa.NET

[Tim Heuer](https://www.timheuer.com/blog) creó un paquete increíble llamado Alexa.NET que envuelve muchas de las funciones de Alexa en una sola biblioteca de C# .Net Core. 

Entonces para nuestro ejemplo, abramos el administrador de dependencias NuGet del Proyecto, busquemos e instalemos este paquete.Yo instale la version versión 1.13.2.

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step15.png)

## ¿Qué es Alexa.NET?

Es una librería auxiliar para trabajar con requests/responses de Skills de Alexa en C#. El objetivo de esta librería es que el trabajar con la API de Alexa sea más natural para un desarrollador de C# que utiliza un modelo de objetos fuertemente tipado.

Podemos encontrar toda la documentación en su repositorio GitHub oficial: [https://github.com/timheuer/alexa-skills-dotnet](https://github.com/timheuer/alexa-skills-dotnet)

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step16.png)

# Functions.cs

Si le echamos un vistazo al archivo Function.cs, encontraremos el punto de entrada para nuestra función Lambda. La plantilla que Visual Studio crea para nosotros incluye una función muy simple, y si deseamos practicar, podemos publicarla en Lambda y luego probarla. 

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step17.png)

Pero nos mantendremos enfocados en Alexa y reemplazaremos todo el código de este archivo con el fragmento a continuación: [https://gist.github.com/LucioMSP](https://gist.github.com/LucioMSP/090b49385d2cbeef6cf4e00bbdd4c0df#file-function-cs-v2)


<script src="https://gist.github.com/LucioMSP/090b49385d2cbeef6cf4e00bbdd4c0df.js"></script>

Como ya lo mencionamos anteriormente, este código es una simple Alexa Skill que le pide al usuario que adivine un número entre uno y diez.

FunctionHandler es nuestro punto de entrada; toma entrada en forma de una solicitud de habilidad y devuelve una SkillResponse.

Si se trata de una solicitud de lanzamiento, un usuario acaba de activar nuestra habilidad diciendo el nombre de invocación. Si hemos recibido una IntentRequest (línea 39), Alexa ha comparado el comando del usuario con un enunciado de muestra y su intención asociada. En ese caso, activamos el nombre de la intención y activamos nuestra funcionalidad deseada.

Independientemente del tipo de solicitud que recibamos, creamos nuestra respuesta utilizando métodos estáticos de la clase ResponseBuilder. Nuestra respuesta consta de algunas partes, la pieza más obvia es la respuesta de texto que queremos que Alexa hable con nuestro usuario. También tenemos que determinar si mantener abierta la sesión actual o finalizarla. En la mayoría de los casos, deseará que su habilidad continúe atrayendo al usuario solicitando más información o explorando otra parte de la habilidad. Use ResponseBuilder.Ask () para mantener la sesión abierta y esperar otra respuesta del usuario. ResponseBuilder.Tell () dirá la respuesta y luego finalizará inmediatamente la sesión (cerrando efectivamente su aplicación).

ResponseBuilder.Ask () también requiere que pase un objeto Reprompt; Esta es solo una cadena que Alexa hablará si el usuario no responde a su mensaje original. Si su respuesta original fue interminable ("el juego terminó, lo completó en siete intentos, esa es una nueva puntuación alta, ¿quiere volver a jugar?"), Tener un Reprompt corto (como "¿jugar de nuevo?" O "¿Qué sigue?" A menudo es mejor que repetir el mensaje original.

Mientras un usuario avanza y retrocede con su habilidad a través de Alexa, querrá realizar un seguimiento de dónde se encuentra en la conversación. Ahí es donde entra en juego el objeto Sesión. Desde el momento en que alguien lanza su habilidad hasta que la habilidad se termina (al decir "detener" u otra frase que desencadena un final), el objeto de sesión conservará los datos que su habilidad puede referenciar mientras maneja los intentos. Sin embargo, cada vez que un usuario inicia su habilidad, se crea una nueva sesión. Si desea almacenar datos entre sesiones, deberá utilizar un almacén de datos más persistente como DynamoDB.

Los atributos de sesión se almacenan en un diccionario al que puede hacer referencia a través de SkillRequest.Session.Attributes; puede leer y escribir en este objeto (consulte las líneas 54 y 69). Un caso de uso de muestra es cuando le hace al usuario una pregunta de sí o no, y su respuesta es manejada por un YesIntent o NoIntent genérico. Tendrás que recordar qué fue lo que preguntaste o la conversación no irá a ningún lado. En nuestro código de muestra, almacenamos la cantidad de conjeturas y la respuesta que buscamos utilizando los atributos de la sesión, y modificamos nuestra respuesta en función de si la conjetura del usuario coincide con nuestro número mágico.
# Publish to AWS Lambda

Ahora necesitamos llevar nuestro código a la nube. Para este paso, deberemos de contar con nuestras credenciales de AWS configuradas en la máquina local; Visual Studio puede recogerlos automáticamente si ya se configuró un usuario a través de la CLI de AWS. De lo contrario, deberemos de hacer esto en otro momento, ya que no lo veremos a continuacion.

En Visual Studio, hacemos clic con el botón derecho en el proyecto en el Explorador de soluciones y seleccionamos Publicar en AWS Lambda. 

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step18.png)

Asegúremosnos de seleccionar el perfil deseado y la región de AWS, despues solo completemos el nombre de la función tal como deseamos que aparezca en AWS Lambda.

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step19.png)

Damos en Continuar o Next.

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step20.png)

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step21.png)

Después de hacer clic en Cargar, si todo va bien, podemos ir al panel de Lambda en la consola de administración de AWS y ver nuestra nueva función

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step22.png)

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step23.png)

# Desencadenador

Una vez en la funciön, y para permitir que Alexa invoque la función Lambda, deberemos agregar un desencadenador a la configuración de esta misma. 

Entonces en la vista del diseñador de la función, hacemos clic en el botón "Añadir desencadenador" 

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step24.png)

Y elegimos el kit de habilidades de Alexa (Alexa Skills Kit) como desencadenador.

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step25.png)

Amazon recomienda habilitar la verificación de ID de habilidad, para garantizar que solo su habilidad específica (o habilidades, puede agregar más de un disparador del Kit de habilidades de Alexa) pueda invocar su función Lambda. Puede encontrar el ID de su habilidad en la página principal de la Consola de desarrollador de Alexa. (View Skill ID)

# Prueba End to End

Nuestro último paso de configuración es conectar la Alexa Skill al EndPoint (punto final) Lambda. Seleccionemos ”EndPoint" en el menú de la izquierda en el panel de Alexa y modifiquemos el ARN de AWS Lambda para que la región predeterminada apunte a nuestro Lambda. Encontraremos el ARN de nuestra Lambda en la esquina superior derecha de la pantalla cuando veamos nuestra función en el panel de AWS.

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step26.png)

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step27.png)

Ahora finalmente podemos probar esto. Para realizarlo, vayamos a la consola de Alexa, aunque también podemos probar en un dispositivo, siempre que el dispositivo esté utilizando la misma cuenta de Amazon que su cuenta de desarrollador de Alexa. Hagamos clic en la pestaña "Prueba" (Test) cerca de la parte superior de la pantalla. Posteriormente escribamos (o hablemos) el comando de invocación para lanzar nuestra skill (”open number games"). Esperemos a que la Skill responda, y luego podremos ver la solicitud y respuesta JSON. Posteriormente podemos continuar conversando con nuestra Skill para probar cualquier cantidad de escenarios.

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step28.png)

Y bueno, eso es todo, ya tenemos una habilidad funcional de Alexa creada desde Visual Studio.

# Alexa Skill == Errores

Si nuestra Skill no se comporta como esperamos, o si vemos que "hubo un problema con la respuesta de la Skill solicitada", deberemos profundizar en los registros producidos por la función Lambda para rastrear el error.

![image](/assets/img/blog/tutorials/alexa-skill-net-core/Step29.png)

Para encontrar los registros de cualquier habilidad, deberemos de navegar a Cloudwatch en la consola de administración de AWS. Seleccionar "Grupos de Registro" en el menú de navegación de la izquierda, y aqui deberiamos ver una entrada con el nombre de la función Lambda. Despues deberemos hacer clic en esa entrada y ver una lista de secuencias de registro, ordenadas por las modificaciones más recientes. 

Por ultimo deberemos añadir un registro adicional a la función para rastrear errores u obtener información sobre cómo se comporta su aplicación.

------------------------------------------------------------------------------------------------------------------------------

Si estas interesado en saber más sobre el desarrollo de Alexa Skills, puedes unirte a la comunidad de desarrolladores de voz en México, comunidad que lleva por nombre [vox: Ninja Alexa](https://www.facebook.com/groups/voxAlexaSkills).

Recuerda además que si tienes alguna inquietud o pregunta, no dudes en ponerte en contacto conmigo o poner un comentario a continuación.

