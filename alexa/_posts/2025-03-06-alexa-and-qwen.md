---
layout: post
title:  Integrando Qwen de Alibaba Cloud en una Alexa Skill
image: /assets/img/blog/post-headers/alexa/alexa-qwen.png
description: >
  Aprende a integrar la API de Qwen de Alibaba Cloud en una Alexa Skill. En este tutorial aprenderás el paso a paso desde la configuración hasta la implementación, para que puedas aprovechar la IA en tu asistente de voz.
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [alexa]
tags:
  - alexa
  - alibaba
  - ai
keywords:
  - alexa
  - alibaba
  - cloud
  - model
  - ai
lang: es
---

Crear una Alexa Skill que se comunique con un modelo de IA como Qwen de Alibaba Cloud puede ser un gran reto para desarrollar asistentes conversacionales inteligentes. Es por ello que en este artículo, te enseñaré el paso a paso de cómo integrar la API de Qwen en una Alexa Skill desde la Alexa Developer Console.

Pero antes de comenzar, conozcamos un poco sobre Qwen:

## ¿Qué es Qwen?
Qwen AI es una herramienta de inteligencia artificial desarrollada por Alibaba que ofrece diversas capacidades, incluyendo la generación de texto, creación de imágenes y videos, así como la asistencia en programación. Lo mejor de todo es que muchas de sus funciones están disponibles de forma gratuita a través de Qwen Chat.

Aunado a lo anterior, Qwen ofrece una API para poder interactuar con esta y el día de hoy haremos uso de la misma.

### Prerrequisitos

Antes de comenzar, asegúrate de tener lo siguiente:

- Cuenta en Alibaba Cloud
- Cuenta en Amazon Developer Console

### Conociendo Qwen AI 

A continuación, te explico cómo puedes comenzar a usar Qwen AI sin costo alguno, solamente debes de seguir estos sencillos pasos:

- Abre tu navegador web favorito y navega al sitio de [Qwen Chat](https://chat.qwen.ai/).
- Aquí deberás de iniciar sesión, ya sea con tu correo electrónico o con tu cuenta de Google.
- Posterior a esto, selecciona la versión de Qwen que desees utilizar en el menú desplegable (algunas de las opciones son Qwen 2.5 Plus, Max, etc.).
Por último, en el Chatbox escribe tu consulta o petición y Qwen AI te responderá de inmediato.

![image](/assets/img/blog/tutorials/alexa-qwen/qwenImage00.png)

En mi caso, hice uso de Qwen 2.5 Max para crear una imagen, en donde el prompt fue "Amazon Alexa con la inteligencia artificial de Qwen de Alibaba Cloud" y el resultado fue el siguiente:

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage01.png)

Y bueno, ahora sí pasemos a lo que nos interesa.
## Crear una Alexa Skill que integre la API de Qwen AI

### Paso 1: Crear la API-Key de Alibaba Cloud Model Studio

Ya sabemos cómo funciona Qwen, lo primero que deberemos de hacer será conseguir la API que utilizaremos en nuestra Alexa Skill. Para ello realicemos lo siguiente:

** Navega al portal de [Alibaba Cloud](https://account.alibabacloud.com/) 

** Inicia sesión o crea tu cuenta en caso de que no cuentes todavía con una.

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage02.png)

** Una vez dentro, del lado superior derecho se encuentra la opción de **Model Studio**, misma que es fácil de reconocer puesto que está al lado de un rectángulo naranja con la leyenda "Free Trial".

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage03.png)

** Al hacer click, nos abrirá otra ventana en donde debemos de hacer click en el botón que dice "**Activate Now**".

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage04.png)

** Posteriormente en la nueva ventana, deberemos de iniciar sesión o crear una cuenta en caso de no contar con una. Acto seguido nos mostrará la consola de **Alibaba Cloud Model Studio**.

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage05.png)

** Ya estando aquí, nos dirigiremos a nuestro perfil (icono superior derecho), en donde al solo pasar el cursor nos desplegará un menú, aquí seleccionemos la opción de **API-KEY**

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage06.png)

** A continuación nos desplegará la siguiente vista:

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage07.png)

** Demos click en el botón **Create My API Key** y añadamos la información que nos solicita, el cual es el espacio de trabajo y una descripción, cabe destacar que esta última no es obligatoria:

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage08.png)

** Una vez creada, demos click en la acción de **View**, puesto que esta nos mostrará toda la API Key, copiémosla de momento, ya que más adelante la utilizaremos.

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage09.png)


### Paso 2: Crear la Alexa Skill en la Alexa Developer Console

Ahora toca acceder a la [Alexa Developer Console](https://developer.amazon.com/alexa/console/ask), en donde procederemos a generar una nueva Skill.

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage10.png)

- Ingresemos un nombre para nuestra Skill
- Seleccionemos la ubicación primaria

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage11.png)

- Escojamos el tipo de experiencia
- Elijamos el modelo
- Seleccionemos el servicio de aprovisionamiento
- Indiquemos la región

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage12.png)
![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage13.png)

- Por último seleccionemos la plantilla de la Skill a utilizar, en este caso usaremos la de **Start from Scratch**

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage14.png)

- Revisemos que todo esté en orden con respecto a lo previamente indicado y demos click en el botón de **Create Skill**

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage15.png)

- Esperemos unos minutos en lo que se genera la Skill.

### Paso 3: Construyendo la Skill
- Una vez creada, demos click en el botón de **Invocation Name**, puesto que al generarse por primera vez, no cuenta con el nombre con el cual el usuario lo podrá invocar.

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage16.png)

- Cambiemos el texto por el nombre con el cual queremos que se invoque nuestra Alexa Skill, en mi caso le puse: qwen cloud model

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage17.png)

- Salvemos nuestro cambio haciendo click en el botón de **Save**

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage18.png)

### Paso 3.1: Crea un Intent personalizado

- En la sección de **Intents** (que está dentro de Interaction Model), demos click en el botón de **+Add Intent** y configuremos un nuevo Intent llamado QwenIntent con una variable de entrada (Slot) llamada **userInput**

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage19.png)

- En los Sample Utterances agreguemos los siguientes ejemplos tomando en cuenta el Slot, mismo que hay setearlo como de tipo **AMAZON.SearchQuery**

    - Quisiera saber {userInput}
    - Dime {userInput}
    - Explícame {userInput}
    - Responde {userInput}
    - Quiero saber {userInput}

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage20.png)

- Nuevamente guardemos nuestros cambios haciendo click en el botón de **Save**

- Por último y como punto obligatorio debemos de construir la Skill (habilidad), para esto hagamos click en el botón **Build skill** que se encuentra en la parte superior derecha.

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage21.png)

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage22.png)

### Paso 3.2: Hora del Código

Lo siguiente que debemos de realizar, es navegar al Tab de **Code** en donde abriremos el archivo "index.js".

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage23.png)

Posteriormente agregaremos el controlador de la intención (Intent) previamente creada (**QwenIntent**), misma que interactuará con la API de Qwen de Alibaba Cloud. En otras palabras, implementa la siguiente lógica debajo del controlador de Lanzamiento de la Skill (LaunchRequestHandler**)

~~~bash

const QwenIntentHandler = {
    canHandle(handlerInput) {
        return Alexa.getRequestType(handlerInput.requestEnvelope) === "IntentRequest" &&
            Alexa.getIntentName(handlerInput.requestEnvelope) === "QwenIntent";
    },
    async handle(handlerInput) {
        const userInput = Alexa.getSlotValue(handlerInput.requestEnvelope, "userInput");
        const apiKey = "API Key"; // 🔴 Reemplázalo con tu API Key

        const requestData = JSON.stringify({
            model: "qwen-plus",
            input: {
                messages: [
                    { role: "system", content: "Eres un asistente útil y conversacional." },
                    { role: "user", content: userInput }
                ]
            }
        });

        const options = {
            hostname: "dashscope-intl.aliyuncs.com",
            path: "/api/v1/services/aigc/text-generation/generation",
            method: "POST",
            headers: {
                "Content-Type": "application/json",
                "Authorization": `Bearer ${apiKey}`,
                "Content-Length": Buffer.byteLength(requestData)
            }
        };
        
        return new Promise((resolve, reject) => {
            const req = https.request(options, (res) => {
                let responseData = "";

                res.on("data", (chunk) => {
                    responseData += chunk;
                });

                res.on("end", () => {
                    console.log("Respuesta completa de Qwen:", responseData); // Depuración

                    try {
                        const data = JSON.parse(responseData);

                        if (!data.output || !data.output.text) {
                            throw new Error("Respuesta inválida de la API.");
                        }

                        const botResponse = data.output.text + "¿Te gustó la respuesta?";

                        resolve(handlerInput.responseBuilder
                            .speak(botResponse)
                            .reprompt("¿Quieres preguntarme algo más?")
                            .getResponse());
                    } catch (error) {
                        console.error("Error al procesar la respuesta de Qwen:", error);
                        resolve(handlerInput.responseBuilder
                            .speak("Lo siento, hubo un problema al procesar tu solicitud.")
                            .getResponse());
                    }
                });
            });

            req.on("error", (error) => {
                console.error("Error en la solicitud HTTP:", error);
                resolve(handlerInput.responseBuilder
                    .speak("Lo siento, no pude conectarme con el servicio de Qwen.")
                    .getResponse());
            });

            req.write(requestData);
            req.end();
        });
    }
};

~~~

### Explicación del código:

#### Definición del controlador de intención (QwenIntentHandler):

**canHandle(handlerInput)**: Esta función determina si el controlador puede manejar la solicitud actual. Verifica si el tipo de solicitud es IntentRequest y si el nombre de la intención es QwenIntent.
**handle(handlerInput)**: Esta función maneja la solicitud cuando canHandle devuelve true.
Obtención del valor del slot:

**const userInput = Alexa.getSlotValue(handlerInput.requestEnvelope, "userInput");**: Obtiene el valor del slot userInput del requestEnvelope.

#### Configuración de la solicitud a la API de Qwen:

**const apiKey = "API Key";**: Define la clave de API (debe ser reemplazada por una clave válida).
**const requestData = JSON.stringify({...});**: Crea el cuerpo de la solicitud en formato JSON, incluyendo el modelo y los mensajes.

#### Opciones de la solicitud HTTPS:

**const options = {...};**: Define las opciones para la solicitud HTTPS, incluyendo el hostname, path, method, y headers.

#### Realización de la solicitud HTTPS:

**return new Promise((resolve, reject) => {...});**: Crea una promesa para manejar la solicitud asincrónica.
**const req = https.request(options, (res) => {...});**: Realiza la solicitud HTTPS con las opciones definidas.
**res.on("data", (chunk) => {...});**: Recibe los datos de la respuesta en fragmentos.
**res.on("end", () => {...});**: Procesa la respuesta completa cuando se recibe.
**req.on("error", (error) => {...});**: Maneja cualquier error que ocurra durante la solicitud.

#### Procesamiento de la respuesta de la API:

**const data = JSON.parse(responseData);**: Analiza la respuesta JSON.
**if (!data.output || !data.output.text) {...};**: Verifica si la respuesta es válida.
**const botResponse = data.output.text + "¿Te gustó la respuesta?";**: Construye la respuesta del bot.
**resolve(handlerInput.responseBuilder.speak(botResponse).reprompt("¿Quieres preguntarme algo más?").getResponse());**: Envía la respuesta al usuario.

#### Manejo de errores:

**catch (error) {...};**: Captura y maneja cualquier error durante el procesamiento de la respuesta.
**req.on("error", (error) => {...});**: Captura y maneja cualquier error durante la solicitud HTTPS.

En resumen, este controlador permite que la Alexa Skill envíe una solicitud a la API de Qwen, procese la respuesta y responda al usuario con el resultado generado por la API.

Para finalizar, añadamos el controlador creado en el **exports.handler**:

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage24.png)

Nota: No olvidemos guardar nuestros cambios y construir nuestra Skill.

### Paso 4: Probar la Skill en la Consola de Alexa

- Hagamos clic en la pestaña Test
- Lanza la Skill escribiendo el nombre que le diste en el "Invocation Name".
- Envía una pregunta y verifica la respuesta generada por Qwen

![image](/assets/img/blog/tutorials/alexa-qwen/01.png)

### Conclusión

Con esta integración, tu Alexa Skill ahora puede aprovechar el poder de la IA de Qwen para ofrecer respuestas inteligentes. Cabe señalar que puedes mejorarla agregando manejo de errores y otras funcionalidades.

¿Tienes dudas? ¡Déjalas en los comentarios! 🚀

### Más información: 

- [Repositorio](https://github.com/LucioD3v/Alexa-Skill-and-Qwen)
- [Qwen LLMs](https://www.alibabacloud.com/help/en/model-studio/developer-reference/what-is-qwen-llm)
- [Playground](https://bailian.console.alibabacloud.com/?spm=a2c63.p38356.0.0.67354be5zAZ730#/efm/model_experience_center/text)

## **¡Happy Coding!**

