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
Qwen AI es una herramienta de inteligencia artificial desarrollada por Alibaba que ofrece diversas capacidades, incluyendo la generación de texto, creación de imágenes y videos, asi como la asistencia en programación. Lo mejor de todo es que muchas de sus funciones están disponibles de forma gratuita a través de Qwen Chat. 

Aunado a lo anterior, Qwen ofrece una API para poder interactuar con esta y el dia de hoy haremos uso de la misma.

### Prerrequisitos

Antes de comenzar, asegúrate de tener lo siguiente:

- Cuenta en Alibaba Cloud
- Cuenta en Amazon Developer Console

### Conociendo Qwen AI 

A continuación, te explico cómo puedes comenzar a usar Qwen AI sin costo alguno, solamente debes de seguir estos sencillos pasos:

- Abre tu navegador web favorito y navega al sitio de [Qwen Chat](https://chat.qwen.ai/).
- Aqui deberas de iniciar sesión, ya sea con tu correo electrónico o con tu cuenta de Google.
- Posterior a esto, selecciona la versión de Qwen que desees utilizar en el menú desplegable (algunas de las opciones son Qwen 2.5 Plus, Max, etc.).
Por ultimo, en el Chatbox escribe tu consulta o petición y Qwen AI te responderá de inmediato.

![image](/assets/img/blog/tutorials/alexa-qwen/qwenImage00.png)

En mi caso, hice uso de Qwen 2.5 Max para crear una imagen, en donde el prompt fue "Amazon Alexa con la inteligencia artificial de Qwen de Alibaba Cloud" y el resultado fue el siguiente:

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage01.png)

Y bueno, ahora si pasemos a lo que nos interesa.
## Crear una Alexa Skill que integre la API de Qwen AI

### Paso 1: Crear la API-Key de Alibaba Cloud Model Studio

Ya sabemos como funciona Qwen, lo primero que deberemos de hacer será conseguir la API que utilizaremos en nuestra Alexa Skill. Para ello realicemos lo siguiente:

** Navega al portal de [Alibaba Cloud](https://account.alibabacloud.com/) 

** Inicia sesión o crea tu cuenta en caso de que no cuentes todavia con una.

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage02.png)

** Una vez dentro, del lado superior derecho se encuentra la opcion de **Model Studio**, misma que es facil de reconocer puesto que esta al lado de un rectangulo naranja con la leyenda "Free Trial".

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage03.png)

** Al hacer click, nos abrira otra ventana en donde debemos de hacer click en el boton que dice "**Activate Now**".

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage04.png)

** Posteriormente en la nueva ventana, deberemos de iniciar sesión o crear una cuenta en caso de no contar con una. Acto seguido nos mostrará la consola de **Alibaba Cloud Model Studio**.

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage05.png)

** Ya estando aqui, nos dirigiremos a nuestro perfil (icono superior derecho), en donde al solo pasar el cursor nos desplegara un menu, aqui seleccionemos la opcion de **API-KEY**

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage06.png)

** A continuacion nos desplegara la siguiente vista:

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage07.png)

** Demos click en el boton **Create My API Key** y añadamos la informacion que nos solicita, el cual es el espacio de trabajo y una descripcion, cabe destacar que esta ultima no es obligatoria:

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage08.png)

Una vez creada, demos click en la accion de **View**, puesto que esta nos mostrara toda la API Key, copiemosla de momento, ya que mas adelante la utilizaremos.

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage09.png)


### Paso 2: Crear la Alexa Skill en la Alexa Developer Console

** Ahora toca acceder a la [Alexa Developer Console](https://developer.amazon.com/alexa/console/ask), en donde procederemos a generar una nueva Skill.

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage10.png)

- Ingresemos un nombre para nuestra Skill
- Seleccionemos la ubicacion primaria

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage11.png)

- Escogamos el tipo de experiencia
- Eligamos el modelo
- Seleccionemos el servicio de aprovisionamiento
- Indiquemos la region

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage12.png)
![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage13.png)

- Por ultimo seleccionemos la plantilla de la Skill a utilizar, en este caso usaremos la de **Start from Scratch**

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage14.png)

- Revisemos que todo este en orden con respecto a lo previamente indicado y demos click en el boton de **Create Skill**

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage15.png)

- Esperemos unos minutos en lo que se genera la Skill.

### Paso 3.1: Construyendo la Skill
- Una vez creada, demos click en el boton de **Invocation Name**, puesto que al generarse por primera vez, no cuenta con el nombre con el cual el usuario lo podra invocar.

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage16.png)

- Cambiemos el texto por el nombre con el cual queremos que se invoque nuestra Alexa Skill, en mi caso le puse: qwen cloud model

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage17.png)

- Salvemos nuestro cambio haciendo click en el boton de **Save**

![image](/assets/img/blog/tutorials/alexa-qwen/qwenimage18.png)

### Paso 3.2: Crea un Intent personalizado

- En la sección de **Intents**, demos click en el boton de **Add Intent** y configuremos un nuevo Intent llamado QwenIntent con una variable de entrada (Slot) llamada userInput

### Paso 3.3: 

### Paso 4:

Implementa la siguiente lógica en el archivo index.js con el siguiente código:

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

                        const botResponse = data.output.text + "¿Te gusto la respuesta?...";

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

### Paso 5: Probar la Skill en la Consola de Alexa

- Hagamos click en la pestaña Test
- Lanza la Skill escribiendo el nombre que le diste en el "Invocation Name".
- Envía una pregunta y verifica la respuesta generada por Qwen

![image](/assets/img/blog/tutorials/alexa-qwen/Image1.jpg)

### Conclusión

Con esta integración, tu Alexa Skill ahora puede aprovechar el poder de la IA de Qwen para ofrecer respuestas inteligentes. Cabe señalar que puedes mejorarla agregando manejo de errores y otras funcionalidades.

¿Tienes dudas? ¡Déjalas en los comentarios! 🚀

### Más información: 

- [Repositorio](https://github.com/LucioD3v/Alexa-Skill-and-Qwen)
- [Qwen LLMs](https://www.alibabacloud.com/help/en/model-studio/developer-reference/what-is-qwen-llm)
- [Playground](https://bailian.console.alibabacloud.com/?spm=a2c63.p38356.0.0.67354be5zAZ730#/efm/model_experience_center/text)´


## **¡Happy Coding!**

