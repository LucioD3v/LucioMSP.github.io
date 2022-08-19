---
layout: post
title: AWS anuncia el File Cache Service y otras ventajas de almacenamiento
description: AWS anuncia el servicio de caché de archivos y otras ventajas de almacenamiento
image: /assets/img/blog/post-headers/awsStorageService.png
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [aws]
tags:
  - aws
  - file
  - service
  - cache
keywords:
  - aws
  - cache
  - service
lang: es
---

¡Hola a tod@s!

Les traigo noticias sorprendentes sobre Amazon Web Services (AWS) y es que hace poco presentó varias actualizaciones de productos relacionadas con el almacenamiento en su reciente evento Storage Day, incluida una solución de nube híbrida llamada Amazon File Cache.

## Amazon File Cache

Programado para estar disponible de forma general más adelante en 2022, Amazon File Cache es un caché de alta velocidad que funciona con datos de archivos almacenados en múltiples fuentes, ya sea en las instalaciones o en la nube. Amazon File Cache es una "ubicación de almacenamiento temporal de alto rendimiento", según una publicación del [blog de esta semana](https://aws.amazon.com/blogs/aws/welcome-to-aws-storage-day-2022/) por el Senior Developer Advocate de AWS, Veliswa Boya.

Amazon File Cache "le permite hacer que conjuntos de datos dispersos estén disponibles para aplicaciones basadas en archivos en AWS con una vista unificada y a altas velocidades con latencias inferiores a un milisegundo y hasta cientos de GB/s de rendimiento", escribió Boya. "Amazon File Cache está diseñado para habilitar una amplia variedad de cargas de trabajo en la nube y flujos de trabajo híbridos, que van desde la representación y transcodificación de medios hasta la automatización del diseño electrónico (EDA) y el análisis de big data".

Otras noticias del evento Storage Day incluyen:

- La capacidad, ahora disponible, de excluir fácilmente volúmenes específicos cuando se utilizan instantáneas de Amazon EBS. "Ahora, puede elegir volúmenes específicos que desea excluir en el proceso de creación de instantáneas mediante una sola llamada a la API o mediante la consola de Amazon EC2, lo que genera un ahorro de costos significativo", escribió Boya.

- Compatibilidad con el protocolo Applicability Statement 2 (AS2) en el servicio AWS Transfer Family, lo que lo pone en línea con las normas de seguridad en las industrias financiera, de atención médica, ciencias de la vida, comercio minorista y seguros. Boya describió el servicio Transfer Family como una forma de "migrar, automatizar y monitorear sin problemas sus flujos de trabajo de transferencia de archivos hacia y desde Amazon S3 y Amazon Elastic File System (Amazon EFS) utilizando los protocolos SFTP, FTPS y FTP".

- El lanzamiento del Programa de entrega de AWS Transfer Family para socios que "ofrecen transferencia de archivos administrada (MFT) nativa de la nube y soluciones de intercambio de archivos de empresa a empresa (B2B) utilizando AWS Transfer Family".

Cabe destacar que el evento Storage Day 2022, que se transmitió en vivo en [Twitch](https://www.twitch.tv/videos/1557921433) el 10 de agosto, está disponible para verlo bajo demanda aquí.

Nota: Este artículo es una traducción no perfecta al español del blog [AWS Insider.NET](https://awsinsider.net/articles/2022/08/11/aws-file-cache-service.aspx)

## ¡Happy Coding! 