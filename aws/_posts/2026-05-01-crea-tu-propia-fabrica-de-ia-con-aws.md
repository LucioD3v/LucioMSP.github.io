---
layout: post
title: Crea tu propia Fábrica de Reconocimiento de Imágenes con Amazon Rekognition
description: En este artículo aprenderemos a darle vision artificial a nuestra aplicacion, en donde integraremos Amazon S3 para el almacenamiento, IAM Roles para la seguridad, AWS Lambda para la lógica Serverless y Amazon CloudWatch para el monitoreo en tiempo real.
image: /assets/img/blog/post-headers/aws/bannerFabricaIA.png
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [aws]
tags:
  - ia
  - amazon s3
  - cloud
  - developer
keywords:
  - aws
  - amazon s3
  - lambda
  - serverless
lang: es
---

Como programador sin duda alguna buscamos tener algun factor que nos haga ser mas competitivos y en tiempos de IA, la ventaja no está en quién programa el algoritmo de más complejo, sino en quién sabe orquestar las herramientas que ya existen para resolver problemas reales hoy. 

Es por ello que este pequeña guía, veremos como integrar Amazon Rekognition en un flujo totalmente automatizado, es decir, nos olvidaremos de configurar GPUs o entrenar modelos por semanas; vamos a conectar piezas de ingeniería para que nuestras fotos(imagenes) se conviertan en datos accionables en milisegundos. El objetivo es simple: subes una foto a la nube y, automáticamente, la IA nos dice qué hay en ella.

Asi que si estás listo para pasar de la teoría a una arquitectura que escala a millones de imágenes por el precio de un café, sigue leyendo.

## El "Dream Team" de AWS que usaremos

Para que esto funcione, necesitamos conectar varias piezas. Piénsenlo como si armaramos una figura de LEGO:

1.  **Amazon S3:** Nuestro almacén. Aquí es donde caerán las fotos.
2.  **IAM Roles:** El guardia de seguridad. Le daremos a nuestra función los permisos justos para trabajar.
3.  **AWS Lambda:** El cerebro. Una función en Python que se activa solo cuando llega (cargat) una foto/imagen.
4.  **Amazon Rekognition:** El experto en visión. La IA que hace el trabajo pesado de análisis.
5.  **Amazon CloudWatch:** Nuestra bitácora. Aquí veremos los resultados que la IA nos devuelva.

---

## Paso 1: El Almacén de Datos (S3)

Lo primero es tener un lugar donde guardar las imágenes.

1. Entren a la consola de S3 y den clic en **Create bucket**.
2. Elijan un nombre único (yo usaré `cucuta-cloud-demo-2026`). 
3. Dejen las opciones por defecto y denle a **Create**.

> ![CAPTURA: Pantalla de creación de Bucket en S3 con el nombre resaltado]

---

## Paso 2: Seguridad ante todo (IAM)

Nuestra Lambda necesita permiso para leer de S3 y para llamar a la API de Rekognition.

1. En el servicio de **IAM**, creen un nuevo **Role**.
2. Seleccionen **Lambda** como el servicio que usará este rol.
3. Busquen y agreguen estas políticas:
    * `AmazonS3ReadOnlyAccess`
    * `AmazonRekognitionReadOnlyAccess`
    * `AWSLambdaBasicExecutionRole` (para que pueda escribir logs).
4. Pónganle un nombre claro, como `LambdaRekognitionRoleCucuta`.

> ![CAPTURA: Lista de políticas adjuntas al Rol en la consola de IAM]

---

## Paso 3: El Cerebro (AWS Lambda)

Aquí es donde ocurre la magia de la orquestación.

1. Vayan a **Lambda** y den clic en **Create function**.
2. Elijan **Python 3.12** como lenguaje.
3. En la sección de permisos, seleccionen el Rol que acabamos de crear en el paso anterior.
4. Una vez creada la función, peguen el código que les compartí en el Gist.

```python
import boto3
import json

def lambda_handler(event, context):
    rekognition = boto3.client('rekognition')
    
    # Obtenemos el bucket y el nombre del archivo del evento
    bucket = event['Records'][0]['s3']['bucket']['name']
    key = event['Records'][0]['s3']['object']['key']
    
    print(f"Analizando imagen: {key} en el bucket: {bucket}")
    
    # Llamamos a Rekognition
    response = rekognition.detect_labels(
        Image={'S3Object': {'Bucket': bucket, 'Name': key}},
        MaxLabels=5,
        MinConfidence=80
    )
    
    print("--- RESULTADOS CÚCUTA-CLOUD ---")
    for label in response['Labels']:
        print(f"Detectado: {label['Name']} ({label['Confidence']:.2f}%)")
        
    return response

```

![CAPTURA: Editor de código de Lambda con el código pegado y el botón Deploy resaltado]

Paso 4: Conectando los puntos (Trigger)
Necesitamos que la función sepa cuándo actuar.

Dentro de la configuración de la Lambda, den clic en Add trigger.

Seleccionen S3 y elijan el bucket que crearon al inicio.

En tipo de evento, dejen All object create events.

![CAPTURA: Diagrama de la función Lambda mostrando el trigger de S3 conectado a la izquierda]

Paso 5: ¡Hora de la verdad! (CloudWatch)
Ahora, suban cualquier imagen a su bucket de S3. Una vez subida:

Vayan a la pestaña Monitor en su Lambda.

Den clic en View CloudWatch logs.

Busquen el último stream de log y ¡ahí lo tienen! Verán la lista de objetos que la IA detectó en milisegundos.

![CAPTURA: Logs de CloudWatch mostrando las etiquetas detectadas por la IA]

---

### 🎤 **Sesión en Vivo:** 

Cabe destacar que este mismo contenido tuve el honor de brindarlo en el **AWS User Group Cúcuta** el pasado **30 de abril**. A continuación, comparto la grabación de la transmisión y el material utilizado en la sesión para que puedas seguir el taller a tu propio ritmo.

![image](/assets/img/blog/tutorials/aws-fabrica-ai/MeetupCucutaVicente.jpg) 

[AWS UG Cúcuta - Meetup](https://www.meetup.com/aws-ug-cucuta/events/314444754/)

### Video - Sesión para AWS UG Cúcuta

<iframe width="560" height="315" src="https://www.youtube.com/embed/KnLqAqz_zwY?si=jfyxCyuBE-FUltQ_" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### Material - PPT

<iframe src="https://www.slideshare.net/slideshow/embed_code/key/3sDsB9yLNKNmHX?hostedIn=slideshare&page=upload" width="476" height="400" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe>

### Conclusión
Como pudimos observar, el construir soluciones inteligentes hoy en día es más una cuestión de arquitectura y conexión de servicios que de programación compleja. Esta misma estructura que acabamos de montar es capaz de escalar de 1 a un millón de imágenes sin que tengamos que preocuparnos por la infraestructura.

Espero que esta guía les haya servido para visualizar como implemetarlo en sus propios proyectos. 
Ya por último, si tienen dudas o logran implementar algo loco con esto, ¡etiquétenme y cuéntenme! 

¡A seguir construyendo en la nube!

### P.D
Por último, si estas interesado en aprender más sobre los servicios de AWS y te encuentras en la Ciudad de México, te invito a que asistas a los Meetups del User Group [Ajolotes en la Nube](https://www.meetup.com/es-ES/ajolotesenlanube/), en donde constantemente se brindan charlas técnicas y se dan a conocer mñas eventos de la comunidad de AWS.

## ¡Happy Coding! 

Más información:

- [Amazon S3](https://aws.amazon.com/es/s3/)
- [AWS Lambda](https://aws.amazon.com/es/pm/lambda/)
- [Amazon Rekognition](https://aws.amazon.com/es/pm/rekognition/)
- [Amazon CloudWatch](https://aws.amazon.com/es/cloudwatch/)
