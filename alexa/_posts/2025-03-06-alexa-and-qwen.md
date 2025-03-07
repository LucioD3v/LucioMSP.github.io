---
layout: post
title:  Integrando Qwen de Alibaba Cloud en una Alexa Skill
image: /assets/img/blog/post-headers/alexa/alexa-qwen.png
description: >
  Aprende a integrar la API de Qwen de Alibaba Cloud en una Alexa Skill. En este tutorial aprenDerás el paso a paso desde la configuración hasta la implementación, para que puedas aprovechar la IA en tu asistente de voz.
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

### Introducción

Crear una Alexa Skill que se comunique con un modelo de IA como Qwen de Alibaba Cloud puede ser un gran reto para desarrollar asistentes conversacionales inteligentes. Es por ello que en este artículo, te enseñare el paso a paso de cómo integrar la API de Qwen en una Alexa Skill desde la Alexa Developer Console.

Pero antes de comenzar, conozcamos un poco sobre Qwen:

## ¿Qué es Qwen?
Qwen es un modelo de IA de Alibaba Cloud que ofrece una API para interactuar con él.

Prerrequisitos

Antes de comenzar, asegúrate de tener lo siguiente:

- Cuenta en Alibaba Cloud
- Cuenta en Amazon Developer Console


#### Paso 1: Crear la Alexa Skill en la Alexa Developer Console

Accede a Alexa Developer Console

Crea una nueva Skill personalizada

![image](/assets/img/blog/tutorials/alexa-qwen/Image1.jpg)

Configura un Intent llamado QwenIntent con una variable de entrada (slot) llamada userInput

#### Paso 2: Configurar el Proyecto Node.js

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

#### Paso 4: Probar la Skill en la Consola de Alexa

- Hagamos click en la pestaña Test
- Lanza la Skill escribiendo el nombre que le diste en el "Invocation Name".
- Envía una pregunta y verifica la respuesta generada por Qwen

### Conclusión

Con esta integración, tu Skill de Alexa ahora puede aprovechar el poder de la IA de Qwen para ofrecer respuestas inteligentes. Puedes mejorarla agregando manejo de errores y más funcionalidades.

¿Tienes dudas? ¡Déjalas en los comentarios! 🚀

### Más información: 

- [Qwen LLMs](https://www.alibabacloud.com/help/en/model-studio/developer-reference/what-is-qwen-llm)
- [Playground](https://bailian.console.alibabacloud.com/?spm=a2c63.p38356.0.0.67354be5zAZ730#/efm/model_experience_center/text)´


¡Happy coding!

