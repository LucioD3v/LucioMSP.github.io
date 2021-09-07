---
layout: post
title: Fundamentos de ECS - Instantáneas (SnapShot)
description: Cuarto artículo sobre Elastic Compute Service (ECS) de Alibaba - Instantáneas (SnapShot).
image: /assets/img/blog/post-headers/alibaba/alibaba-header-snapshot.png
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [alibaba]
tags:
  - alibaba
  - snapshot
keywords:
  - alibaba
  - ecs
  - elastic
  - service
  - snapshot
  - cloud
  - instantáneas
lang: es
---

Hola amigos, sean bienvenidos a esta serie de artículos introductorios dedicados a Elastic Compute Service o ECS de Alibaba. En esta quinta entrega veremos ECS Snapshots o Instantáneas de ECS.

## ¿Qué es son las instantáneas de ECS (SnapShots)?

Las instantáneas son copias completas de solo lectura de los datos del disco en determinados momentos y estas se pueden utilizar para los siguientes escenarios:

### Copia de Seguridad y Recuperación ante Desastres: 
  puede crear una instantánea para un disco y luego usar la instantánea para crear otro disco para implementar la recuperación ante desastres geográficos o de zona.

### Clonación del Entorno: 
  puede utilizar una instantánea del disco del sistema para crear una imagen personalizada y, a continuación, utilizar la imagen personalizada para crear una instancia de ECS para clonar el entorno.

### Desarrollo de Datos: 
  las instantáneas pueden proporcionar datos de producción casi en tiempo real para aplicaciones como minería de datos, consultas de informes, desarrollo y pruebas.

### Tolerancia a Fallas Mejorada: 
  Puede revertir un disco a un punto anterior en el tiempo mediante el uso de una instantánea para reducir el riesgo de pérdida de datos causada por una ocurrencia inesperada. Puede crear instantáneas de forma regular para evitar pérdidas causadas por sucesos inesperados. 
  
  Estos sucesos inesperados pueden incluir, por ejemplo, escribir datos incorrectos en discos, eliminar datos accidentalmente de un disco, liberar instancias de ECS accidentalmente, errores de datos causados ​​por errores de aplicación y pérdida de datos debido a intentos de piratería.

![image](/assets/img/blog/tutorials/alibaba/articulos-ecs/SnapShot.png)

Además, puede crear una instantánea antes de realizar operaciones de alto riesgo, como cambiar sistemas operativos, actualizar aplicaciones y migrar datos comerciales.

En cualquiera de estos escenarios, los datos se pueden recuperar de una instantánea.

Las instantáneas se pueden crear de forma manual o automática mediante la creación de una política de instantáneas. Se pueden crear hasta 64 instantáneas por disco y cada instantánea es una copia incremental de la instantánea anterior. Cuando se alcanza el número máximo de instantáneas, se elimina la instantánea más antigua y se crea una nueva.

Sin embargo, las instantáneas no son gratuitas y se cobran en función del espacio de almacenamiento utilizado y la cantidad de tiempo que se guardan.
