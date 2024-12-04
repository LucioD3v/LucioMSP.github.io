---
layout: post
title: Principios Básicos - Amazon S3
description: En este artículo centrado a los principios basicos de AWS, aprenderemos sobre el servicio de almacenamiento de objetos mejor conocido como S3.
image: /assets/img/blog/post-headers/aws/amazons3.jpg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [aws]
tags:
  - storage
  - amazon s3
  - cloud
  - developer
keywords:
  - aws
  - amazon s3
  - storage
  - developer
lang: es
---

Amazon ofrece diversos servicios y uno de los más utilizados es el de depósito de objetos, mejor conocido como S3, mismo que puede alojar diversos tipos de archivos de los que usualemnte podriamos encontrar en cualquier equipo u ordenador. A continuacion exploraremos con mayor detalle sobre dicho servicio, por ende primero veamos que es exactamebte Amazon S3.

### ¿Qué es Amazon S3?
Amazon Simple Storate Service es el servicio de almacenamiento creado para recuperar cualquier volumen de datos desde cualquier ubicacion de manera segura, escalable y rentable, puesto que se encuentra en la nube.

### Funcionamiento
Amazon S3 organiza los datos en "buckets" o contenedores de almacenamiento en los que podemos ir añadiendo diferentes tipos de objetos de hasta 5 TB de tamaño que deseemos guardar, todo esto sin la necesidad de preocuparnos por el crecimiento de los "cubos" (si lo tradujeramos al español). Cabe destacar que los objetos pueden ser cualquier tipo de archivo, como imágenes, videos, documentos, etc. Y para poder acceder a los objetos que se almacenen en algun contenedor podemos hacerlo mediante una URL única.

### Video - Amazon S3
<iframe width="560" height="315" src="https://www.youtube.com/embed/zSXpnzAtrHA?si=XHCGGR-YD4TxAKuw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## [Tipos de Almacenamiento](https://aws.amazon.com/es/s3/storage-classes/?gclid=CjwKCAiAxqC6BhBcEiwAlXp459Yr0Eu932MEmP_o8t9OUewPbJFAF0quTm-lgpdRCAPf75WuCk7e5hoC5aUQAvD_BwE&trk=403e297f-6f7f-4dc0-9757-182e9e9f956c&sc_channel=ps&ef_id=CjwKCAiAxqC6BhBcEiwAlXp459Yr0Eu932MEmP_o8t9OUewPbJFAF0quTm-lgpdRCAPf75WuCk7e5hoC5aUQAvD_BwE:G:s&s_kwcid=AL!4422!3!646996315409!e!!g!!amazon%20s3!19636895691!149631417590)

Cabe destacar que Amazon S3 no es el único servicio de alojamiento de archivos que ofrece Amazon Web Services, sino que cuenta con los siguientes:

- De uso general: Amazon S3 Estándar (S3 Estándar)
- De acceso desconocido o modificado: Amazon S3 Intelligent-Tiering (S3 Intelligent-Tiering)
- De alto rendimiento: Amazon S3 Express One Zone
- De acceso poco frecuente: Amazon S3 One Zone-Infrequent Access (S3 One Zone-IA)
- De archivo: Glacier Instant Retrieval / Glacier Flexible Retrieval (antes, S3 Glacier) / Glacier Deep Archive
- S3 Outposts

### ¿Qué otras opciones ofrece Amazon S3?
Como ya se menciono anteriormente, S3 nos da la facilidad de almacenar todo tipo de archivos, pero lo que hay que tener presente de igual manera, es que nos brinda otras opciones, tales como:

* Alojamiento de Sitios Web
* Analisis de Big Data
* Integración con maquinas virtuales

### Ventajas
A continuacion se enlistan las principales ventajas de usar Amazon S3:

**Escalabilidad ilimitada**
Amazon S3 permite almacenar una cantidad practicamente ilimitada de datos, sin necesidad de gestionar infraestructura fisica.

**Alta durabilidad y disponibilidad**
Amazon S3 garantiza una durabilidad del 99.99999999% y una alta disponibilidad.

**Costos flexibles**
Ofrece múltiples clases de almacenamiento adaptadas a diferentes necesidades, tales como:
- S3 Standard para acceso frecuente
- S3 One Zone-IA para acceso poco frecuente
- S3 Glacier para archivo a largo plazo

**Seguridad Robusta**
S3 proporciona una variedad de características de seguridad:
- Autenticación y autorización
- Encriptación de datos
- Protección contra la eliminación accidental de objetos
- Protección contra la eliminación de objetos no autorizados

## Seguridad
Con respecto a la seguridad, Amazon S3 no lo pasa desapercibido, por ende nos brinda diferentes caracteristicas para proteger los datos almacenados en nuestros buckets:

- Amazon Macie: Macie proporciona automáticamente un inventario completo de buckets de S3 mediante el escaneo de buckets para identificar y categorizar los datos.

![image](/assets/img/blog/tutorials/aws-s3/amazonmacie.png) 

- Cifrado: Amazon S3 de manera automatica cifra todas las cargas de datos a cualquier bucket, admitiendo tanto cifrado del servidor como del cliente.

![image](/assets/img/blog/tutorials/aws-s3/amazoncifrado.png) 

- Identity and Access Management: De manera predeterminada, todos los recursos de Amazon S3 son privados, es decir, solo el propietario de los mismos y dueño de la cuenta de AWS con la que se genero, puede acceder a estos.

![image](/assets/img/blog/tutorials/aws-s3/amazonidentity.png) 

- AWS Trusted Advisor: Este nos permite inspeccionar el entorno de AWS y luego brindarnos recomendaciones cuando surgan oportunidades para solucionar déficits de seguridad.

![image](/assets/img/blog/tutorials/aws-s3/trustedadvisor.png) 

- AWS PrivateLink para S3: Mediante esta herramienta podemos tener acceso a S3 de forma directa como un punto de enlace privado dentro de la red virtual.

![image](/assets/img/blog/tutorials/aws-s3/privatelink.png) 

- Verificación de la Integridad de los datos: Contamos con 4 algoritmos de suma de comprobación compatibles (SHA-1, SHA-256, CRC32 o CRC32C) para verificar la integridadd de los datos de las solicitudes de carga y descarga.

![image](/assets/img/blog/tutorials/aws-s3/integridaddatos.png) 

### Resumen

En resumen, Amazon S3 es una solución de almacenamiento en la nube que destaca por su escalabilidad ilimitada, alta durabilidad y flexibilidad en los costos. Aunado a que brinda diversas clases de almacenamiento para optimizar recursos según las necesidades, garantiza la seguridad de los datos mediante cifrado y control de accesos, y facilita la integración con otros servicios de AWS así como con herramientas de terceros.

Sinceramente es una opción robusta y eficiente para quienes buscan soluciones avanzadas de gestión de datos en la nube.

----

Espero que hayas aprendido algo especial hoy. Si disfrutaste de este artículo, apoyame compartiendolo con tus amigos y si tienes alguna sugerencia o pensamiento para compartir conmigo, pasa a dejarlo en el cuadro de comentarios.

### P.D
Por último, si estas interesado en aprender más sobre Amazon S3 y te encuentras en la Ciudad de México, te invito a que asistas a los Meetups del User Group [Ajolotes en la Nube](https://www.meetup.com/es-ES/ajolotesenlanube/), en donde constantemente se brindan charlas técnicas y se dan a conocer mñas eventos de la comunidad de AWS. 

## ¡Happy Coding! 

Más información:

- [Amazon S3](https://aws.amazon.com/es/s3/)
- [Docs AWS Amazon S3](https://docs.aws.amazon.com/es_es/AmazonS3/latest/userguide/Welcome.html)
