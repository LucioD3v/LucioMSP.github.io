---
layout: post
title: Crea tu propia Fábrica de Reconocimiento de Imágenes con Amazon Rekognition
description: En este artículo aprenderemos a darle vision artificial a nuestra aplicación, en donde integraremos Amazon S3 para el almacenamiento, IAM Roles para la seguridad, AWS Lambda para la lógica Serverless y Amazon CloudWatch para el monitoreo en tiempo real.
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

Como programador sin duda alguna buscamos tener algun factor que nos haga ser mas competitivos y en tiempos de IA, la ventaja no está en quién programa el algoritmo más complejo, sino en quién sabe orquestar las herramientas que ya existen para resolver problemas reales. 

Es por ello que esta pequeña guía, veremos como integrar Amazon Rekognition en un flujo totalmente automatizado, es decir, nos olvidaremos de configurar GPUs o entrenar modelos por semanas; vamos a conectar piezas de ingeniería para que nuestras fotos(imágenes) se conviertan en datos accionables en milisegundos. El objetivo es simple: subir una foto a la nube y, automáticamente, la IA nos dice qué hay en ella.

Asi que si estás listo para pasar de la teoría a una arquitectura que escala a millones de imágenes por el precio de un café, sigue leyendo.

## De la Ciencia Ficción a tu Stack de Desarrollo 

La barrera de entrada para la IA ha caído. Lo que antes era un privilegio de laboratorios con presupuestos astronómicos, hoy es una pieza de LEGO en nuestro stack.  

- Ayer: Necesitabas PhDs, inversión masiva en GPUs y meses de entrenamiento para modelos que solían ser inalcanzables.  
- Hoy: Tenemos accesos a modelos pre-entrenados de clase mundial en milisegundos.
 
Es decir, ahora nuestro valor real está en la orquestación: conectar estas capacidades para resolver problemas de negocio con agilidad y escala. 

### La era Serverless

En el mundo del desarrollo moderno, existe una distinción fundamental que todo arquitecto debe comprender para dominar la nube:

El Mito: "No hay servidores".
La Realidad: Hay servidores, pero no son tu problema.

Al adoptar este enfoque, dejas de gestionar máquinas para centrarte en la orquestación de servicios.

Los beneficios son:
 - Escalabilidad automática: Tu sistema crece de forma fluida para procesar desde una hasta un millón de peticiones sin intervención manual.
 - Modelo de pago por uso: La infraestructura es eficiente financieramente; si nadie usa tu aplicación, el costo es de $0.
 - Foco total en el valor de negocio: Te olvidas por completo del parcheo de sistemas operativos y la gestión de parches para dedicar el 100% de tu tiempo a tu lógica.

## El "Dream Team" de AWS que usaremos

Para que esto funcione, necesitamos conectar varias piezas. Tal y como lo comente anteriormente, veamoslo como si armaramos una figura de LEGO:

1.  **Amazon S3:** Nuestro almacén. Aquí es donde caerán las fotos.
2.  **IAM Roles:** El guardia de seguridad. Le daremos a nuestra función los permisos justos para trabajar.
3.  **AWS Lambda:** El cerebro. Una función en Python que se activa solo cuando llega (cargat) una foto/imagen.
4.  **Amazon Rekognition:** El experto en visión. La IA que hace el trabajo pesado de análisis.
5.  **Amazon CloudWatch:** Nuestra bitácora. Aquí veremos los resultados que la IA nos devuelva.

### Arquitectura

Como bien lo han de saber, una buena solución no solamente se basa en elegir los servicios correctos, sino en cómo estos se orquestan para trabajar de forma armónica. A continuación, muestro el mapa de arquitectura nivel 100 que guía nuestra "fábrica" de reconocimiento: un flujo totalmente desacoplado y orientado a eventos que nos permite escalar sin intervención manual.

![image](/assets/img/blog/tutorials/aws-fabrica-ai/arquitectura_fabrica.png) 

## Paso 1: El Almacén de Datos (S3)

Y bueno, tal como lo podemos ver en la imagen anterior, lo primero que debemos de tener, es el lugar donde se guardaran/almacenaran las imágenes, para ello sigamos lo siguiente:

1. Entremos a la consola de AWS, naveguemos a S3 y demos clic en **Crear bucket**.
2. Elijamos un nombre único (yo usaré `fabric-ai-cloud-2026`). 
3. Dejemos las opciones por defecto y demos clic en **Crear bucket**.

![image](/assets/img/blog/tutorials/aws-fabrica-ai/paso1.jpg)

## Paso 2: Seguridad ante todo (IAM)

Lo siguiente segun lo indica la arquitectura es brindar los permisos necesarios para que nuestra Lambda pueda "leer" lo que se encuentra en nuestro S3 y asi poder llamar a la API de Rekognition.

1. En el servicio de **IAM**, creemos un nuevo **Role**.
2. Seleccionemos **Lambda** como el servicio que usará este rol.
3. Busquemos y agreguemos las siguientes políticas:
    * `AmazonS3ReadOnlyAccess`
    * `AmazonRekognitionReadOnlyAccess`
    * `AWSLambdaBasicExecutionRole` (para que pueda escribir logs).
4. Asignemosle un nombre claro, como `FabricRekognitionRole`.
5. Demos clic en **Crear rol**

![image](/assets/img/blog/tutorials/aws-fabrica-ai/paso2.jpg)

## Paso 3: El Cerebro (AWS Lambda)

Una vez creado lo anterior, procederemos a crear la Lambda, en donde ocurre la magia de la orquestación.

1. Vayamos a **Lambda** y demos clic en **Crear función**.
2. Asignemosle un nombre unico, en mi caso será `FabricRekognitionLambda`.
3. Elijamos **Python 3.14** como versión ejecutable (lenguaje en la que se escribirá la función).
4. En la sección de "Configuración adicional", habilitemos la opción de rol de ejecución personalizada y seleccionemos el rol que acabamos de crear en el paso anterior.
5. Demos clic en **Crear función**

![image](/assets/img/blog/tutorials/aws-fabrica-ai/paso3-1.jpg)

6. Una vez creada la función, peguemos el siguiente código que comparto a continuacion:

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
    
    print("--- RESULTADOS FABRIC-CLOUD ---")
    for label in response['Labels']:
        print(f"Detectado: {label['Name']} ({label['Confidence']:.2f}%)")
        
    return response

```
7. Por últmo para "guardar los cambios", hagamos clic en **Deploy**

![image](/assets/img/blog/tutorials/aws-fabrica-ai/paso3-2.jpg)

Y bueno, antes de avanzar, solo quiero compartir un poco sobre Amazon Rekognition, puesto que en el código anterior lo mandamos llamar. 
Este es un servicio de inteligencia artificial de AWS que permite analizar imágenes y videos para identificar objetos, rostros, texto, actividades y contenido inapropiado. Sus casos de uso van mas centrados para ambitos de seguridad, automatización y análisis visual, sin necesidad de desarrollar modelos desde cero. 

## Paso 4: Conectando los puntos (Trigger)

Ahora necesitamos que la función sepa cuándo actuar. Por ello...

1. Dentro de la configuración de la Lambda, hagamos clic en **+ Agregar desencadenador**.
2. Seleccionemos S3 y elijamos el bucket que creamos al inicio.
3. En tipo de evento, dejemos "Todos los eventos de creación de objetos".

![image](/assets/img/blog/tutorials/aws-fabrica-ai/paso4.jpg)

4. Demos clic en **Agregar**

![image](/assets/img/blog/tutorials/aws-fabrica-ai/paso4-1.jpg)

## Paso 5: ¡Hora de la verdad! (CloudWatch)

Llego el momento esperado, procedamos a subir cualquier imagen al bucket de S3. 

![image](/assets/img/blog/tutorials/aws-fabrica-ai/paso5.jpg)

Posteriormente se haya realizado esto, vayamos a la pestaña **Monitorear** en nuestra Lambda demos clic en **Ver registros de CloudWatch**.

![image](/assets/img/blog/tutorials/aws-fabrica-ai/paso5-1.jpg)

Busquemos el último stream de log y ¡ahí debe de aparecer! Se mostrará una lista de objetos que la IA detectó en milisegundos.

![image](/assets/img/blog/tutorials/aws-fabrica-ai/paso5-1.jpg)

---

### 🎤 **Sesión en Vivo:** 

Cabe destacar que este mismo contenido tuve el honor de brindarlo en el **AWS User Group Cúcuta** el pasado **30 de abril**. A continuación, comparto la grabación de la transmisión y el material utilizado en la sesión para que puedan seguir el taller a tu propio ritmo.

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
Por último, si estas interesado en aprender más sobre los servicios de AWS y te encuentras en la Ciudad de México, te invito a que asistas a los Meetups del User Group [Ajolotes en la Nube](https://www.meetup.com/es-ES/ajolotesenlanube/), en donde constantemente se brindan charlas técnicas y se dan a conocer más eventos de la comunidad de AWS.

## ¡Happy Coding! 

Más información:

- [Amazon S3](https://aws.amazon.com/es/s3/)
- [AWS Lambda](https://aws.amazon.com/es/pm/lambda/)
- [Amazon Rekognition](https://aws.amazon.com/es/pm/rekognition/)
- [Amazon CloudWatch](https://aws.amazon.com/es/cloudwatch/)
