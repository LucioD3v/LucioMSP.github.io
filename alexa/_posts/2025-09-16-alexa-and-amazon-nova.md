---
layout: post
title:  Integrando Amazon Nova Lite en una Alexa Skill
image: /assets/img/blog/post-headers/alexa/nova-lite.png
description: >
  Amazon Nova Lite es un modelo multimodal de muy bajo costo que es increíblemente rápido para procesar entradas de imágenes, video y texto para generar salidas de texto que esta disponible a través de Amazon Bedrock. En este tutorial aprenderemos a integrarlo en una Alexa Skill para poder generar respuestas más dinámicas, creativas y relevantes para tus usuarios.
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [alexa]
tags:
  - alexa
  - aws
  - bedrock
keywords:
  - alexa
  - aws
  - cloud
  - nova
  - ai
lang: es
---

Desarrollar una Alexa Skill que se conecte con un modelo de inteligencia artificial como AWS Nova Lite representa una excelente oportunidad —y también un reto— para crear asistentes conversacionales verdaderamente inteligentes. En este artículo, te guiaré paso a paso en el proceso de integración del Modelo Fundacional "Nova Lite" en una Alexa Skill, utilizando la Alexa Developer y la AWS Console.

Pero antes de comenzar, conozcamos un poco sobre Nova Lite:

## ¿Qué es Nova Lite?

Amazon Nova Lite es uno de los modelos de IA de la familia de Amazon Nova. Su principal caracteristica es que al ser un modelo mutimodal puede procesar y entender diferentes tipos de datos a la vez, como texto, imagenes y videos. Lo cual lo hace muy versatil para diferentes aplicaciones.

### Prerrequisitos

Antes de comenzar, asegúrate de tener lo siguiente:

- Cuenta en Alexa Developer Console
- Cuenta en Amazon Management Console

### Paso 1: Crear la Alexa Skill

Vayamos a la [Alexa Developer Console](https://developer.amazon.com/alexa/console/ask), en donde procederemos a generar una nueva Skill donde clic en el boton **"Crear skill"**:

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/01.png)

Ingresemos un nombre para nuestra Skill e indiquemos la ubicación primaria:

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/02.png)

Posteriormente:

- Escojamos el tipo de experiencia
- Indiquemos el modelo
- Seleccionemos el servicio de aprovisionamiento

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/03.png)

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/04.png)

Por último seleccionemos la plantilla a utilizar, en este caso usaremos la de **Start from Scratch**.

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/05.png)

Revisemos que todo esté en orden con respecto a lo previamente indicado y demos click en el botón de **Create Skill**

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/06.png)

Esperemos unos minutos en lo que se genera la Skill.

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/07.png)

### Paso 2: Construyendo la Skill

Una vez creada, demos click en el botón de **Invocation Name**, puesto que al generarse por primera vez, no cuenta con el nombre con el cual el usuario la podrá invocar.

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/08.png)

Cambiemos el texto por el nombre con el cual queremos que se invoque nuestra Alexa Skill, en mi caso le puse: **terra nova**

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/09.png)

Salvemos nuestro cambio haciendo click en el botón de **Save**

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/10.png)

### Paso 3: Crea un Intent personalizado

En la sección de **Intents** (que está dentro de Interaction Model), demos click en el botón de **+Add Intent**

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/11.png)

Acto seguido configuremos un nuevo Intent llamado **GenerarTextoNova**

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/12.png)

En los Sample Utterances añadamos algunas expresiones de ejemplo que los usuarios podrian decir para activar esta intención. Asegurate de crear un Slot, el cual pueden nombrarlo como gusten, en mi caso lo llamare  **consulta** y por último hay que setearlo como de tipo **AMAZON.SearchQuery**

    - Quisiera saber {consulta}
    - Genera texto sobre {consulta}
    - Cuéntame algo sobre {consulta}
    - Dime {consulta}
    - Explícame {consulta}
    - Qué sabes de {consulta}
    - Responde {consulta}
    - Quiero saber {consulta}

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/13.png)

Nuevamente guardemos nuestros cambios haciendo click en el botón de **Save**

Por último y como punto obligatorio debemos de construir la Skill (habilidad), para esto hagamos click en el botón **Build skill** que se encuentra en la parte superior derecha.

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/14.png)

### Paso 4: Hora del Código

Lo siguiente que debemos de realizar, es configurar una función de AWS Lambda, para ello deberemos de navegar a la consola de 
[Amazon Management Console](https://console.aws.amazon.com/) y seleccionar Lambda o buscarlo si es que no se tiene como visitado recientemente.

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/15.png)

Una vez dentro, si no tenemos ninguna función creada previamente, se nos mostrará de la siguiente manera, en donde haremos clic en **Crear una función**:

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/16.png)

En la siguiente vista, seleccionemos **Crear desde cero** e ingresemos los siguientes datos:
- Nombre: alexaNovaBackend
- Tiempo de ejecución: Python 3.13
- Arquitectura: x86_64
- Permisos: Creación de un nuevo rol con permisos básicos de Lambda

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/17.png)

Hagamos clic en el botón de **Crear una función**.

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/18.png)

Una vez creada, nos encontraremos en la vista de edición de la función Lambda.

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/19.png)

## - Integración con Boto3 en Lambda -

Posteriormente desplacémonos a la pestaña **Código fuente** que se encuentra en la parte inferior y reemplacemos el código existente con el siguiente:

~~~bash

import json
import boto3

bedrock = boto3.client('bedrock-runtime', region_name="us-east-1")

def lambda_handler(event, context):
    try:
        intent_name = event['request']['intent']['name']

        if intent_name == 'GenerarTextoNova':
            prompt = event['request']['intent']['slots']['consulta']['value']
            response = invoke_titan_text(prompt)
            speech_text = response
        else:
            speech_text = "Lo siento, no entiendo esa solicitud."

        return {
            'version': '1.0',
            'response': {
                'outputSpeech': {
                    'type': 'PlainText',
                    'text': speech_text
                },
                'shouldEndSession': True
            }
        }
    except Exception as e:
        print(f"Error: {e}")
        return {
            'version': '1.0',
            'response': {
                'outputSpeech': {
                    'type': 'PlainText',
                    'text': "Lo siento, hubo un problema al procesar tu solicitud."
                },
                'shouldEndSession': True
            }
        }

def invoke_titan_text(prompt):
    model_id = 'amazon.titan-text-lite-v1'
    accept = 'application/json'
    content_type = 'application/json'

    body = json.dumps({
        "inputText": prompt,
        "textGenerationConfig": {
            "maxTokenCount": 200,
            "temperature": 0.7,
            "topP": 0.9
        }
    })

    response = bedrock.invoke_model(
        body=body,
        modelId=model_id,
        accept=accept,
        contentType=content_type
    )

    response_body = json.loads(response['body'].read())
    generated_text = "Nova Lite responde: " + response_body['results'][0]['outputText']

    return generated_text

~~~

A grandes rasgos lo que hace este código de Python es que la función Lambda interactue con Amazon Bedrock.

**Nota:** el código de igual manera se encuentra en el siguiente [Gist](https://gist.github.com/LucioD3v/dae03b3ef42f19125cfa073097a2f8c3)

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/20.png)

Por último, hagamos clic en **"Deploy (Desplegar)"**

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/21.png)

## Paso 5: Conecta la Skill con la Lambda

Para que la función Lambda pueda comunicarse con la Alexa Skill, lo que debemos de hacer primero será copiar el ARN (Amazon Resource Name) de la función y pégarlo en el campo correspondiente en la Consola de Alexa.

~~~bash

arn:aws:lambda:us-east-1:842676015954:function:alexaNovaBackend

~~~

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/22.png)

En la consola de Alexa, vayamos a la seccion de "Endpoint" en la Skill y borremos lo que se encuentra en **Default Region**

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/23.png)

Para poder pegar el ARN del paso anterior:

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/24.png)

Que no se nos olvide guardar los cambios haciendo click en el boton **Save**

## Paso 6: Configurar el trigger de Alexa Skills Kit:

Nuevamente en la vista de nuestra función Lambda, hagamos clic en **+ Agregar desencadenador**

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/25.png)

En la nueva vista, del dropdown seleccionemos **Alexa**

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/26.png)

Acto seguido, dejemos seleccionado el producto de Alexa que viene por default (Kit de habilidades de Alexa) y en la sección de **Verificación del ID de la habilidad** peguemos el ID de nuestra Alexa Skill (lo encuentras en la consola de desarrolladores de Alexa).

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/27.png)

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/28.png)

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/29.png)

Finalmente, hagamos clic en **Agregar**.

## Paso 7: Añadiendo Permisos 

Nuevamente en nuestra función Lambda, ahora vayamos a la pestaña de **Configuración** y seleccionemos la opción de Permisos, puesto que aqui configuraremos los consentimientos necesarios:

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/30.png)

Aqui, lo que haremos sera buscar el rol de IAM asociado a la función Lambda (generalmente tiene un nombre similar al de la función). Una vez localizado, hagamos clic en el nombre del rol.

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/31.png)

Nos abrira una nueva ventana en nuestro navegador, ubiquemos **Agregar permisos** y del dropdown eligamos **Crear política insertada**

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/32.png)

En el **Editor de políticas** seleccionamos JSON y peguemos la siguiente política:

~~~bash
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "bedrock:InvokeModel"
            ],
            "Resource": "arn:aws:bedrock:<REGION>::foundation-model/amazon.titan-text-lite-v1"
        },
        {
            "Effect": "Allow",
            "Action": [
                "logs:CreateLogGroup",
                "logs:CreateLogStream",
                "logs:PutLogEvents"
            ],
            "Resource": "arn:aws:logs:REGION:ACCOUNT_ID:log-group:/aws/lambda/YOUR_LAMBDA_FUNCTION_NAME:*"
        }
    ]
}
~~~
**Importante:** Asegurate de reemplazar <REGION> con la región de AWS donde estás trabajando.

La region trabajada en este ejemplo es: us-east-1

~~~bash
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Effect": "Allow",
			"Action": "bedrock:InvokeModel",
			"Resource": "arn:aws:bedrock:us-east-1::foundation-model/amazon.titan-text-lite-v1"
		},
		{
			"Effect": "Allow",
			"Action": [
				"logs:CreateLogGroup",
				"logs:CreateLogStream",
				"logs:PutLogEvents"
			],
			"Resource": "arn:aws:logs:*:*:*"
		}
	]
}
~~~

***Nota:*** En este ejemplo, estamos utilizando **"amazon.titan-text-lite-v1"**, que es parte de la familia de modelos Titan Text Lite ofrecidos a través de Bedrock. Si requieres hacer uso de otro FM como "Nova Micro" asegúrate de actualizar el "Resource" en la política de IAM. Para esto, consulta la documentación de Amazon Bedrock para obtener el ARN exacto del modelo Nova que necesites cuando esté disponible.

Hagamos clic en "Siguiente".

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/33.png)

Posteriormente en la nueva ventana denominada **Revisar y Crear**, tocara asigarle un nombre a la política 
(ej. BedrockAlexaNovaPolicy) y haz clic en "Crear política".

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/34.png)

### Paso 7: Configurar el Tiempo de espera

Ya por último, en la función Lambda, seleccionemos la pestaña de **Configuración**, y si hacemos clic en "Configuración general" podremos observar que el tiempo de espera es de 3 segundos:

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/35.png)

Pasemos a modificar esto, por ende hagamos clic en **Editar** y cambiemos el tiempo de espera a 10 segundos, posteriormente hagamos clic en **Guardar**.

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/36.png)

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/37.png)

### Paso 8: Probar la Skill en la Consola de Alexa

- Hagamos clic en la pestaña Test

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/38.png)

- Activemos el entorno de pruebas seleccionando "Development"

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/39.png)

- Lanza la Skill escribiendo el nombre que le diste en el **Invocation Name**, en mi caso seria **terra nova** y sumale un ejemplo de frase que haga que ingrese a nuestro **Intent**, por ejemplo:

**Abre terra nova y genera texto sobre los power rangers**

- Esperemos unos segundos y deberiamos de ver la respuesta generada por Nova Lite:

![image](/assets/img/blog/tutorials/nova-lite-alexa-skill/40.png)

Y ¡listo!, hemos logrado integrar Amazon Nova Lite en una Alexa Skill.

### Conclusión
Integrar Amazon Nova Lite en una Alexa Skill puede transformar la experiencia del usuario al proporcionar respuestas más inteligentes y contextuales. Con los pasos descritos en este tutorial, ahora tienes las herramientas necesarias para comenzar a experimentar con esta poderosa combinación de tecnologías.

¿Tienes dudas? ¡Déjalas en los comentarios! 🚀

## ¿Lo quieres ver en video?

Aqui les dejo la grabacion de mi participacion al lado de mi colega Uriel Arellano en el AWS Community Day de Bolivia:

<iframe width="560" height="315" src="https://www.youtube.com/embed/CneHRDE7EMw?si=5XD97dkrRY7LiEVI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### Más información: 

- [AWS Nova Lite](https://www.alibabacloud.com/help/en/model-studio/developer-reference/what-is-qwen-llm)

### Recursos: 

- [Gits - Lambda Function](https://gist.github.com/LucioD3v/dae03b3ef42f19125cfa073097a2f8c3)
- [Gits - Politica](https://gist.github.com/LucioD3v/4c79dcb5f9f6025996844e907caed481)

## **¡Happy Coding!**

