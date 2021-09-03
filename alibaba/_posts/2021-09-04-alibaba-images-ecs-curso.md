---
layout: post
title: Fundamentos de ECS - Imagenes
description: Tercer artículo sobre Elastic Compute Service (ECS) de Alibaba - Imagenes. 
image: /assets/img/blog/post-headers/alibaba/second-article-ecs-header.jpeg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [alibaba]
tags:
  - alibaba
  - images
keywords:
  - alibaba
  - ecs
  - elastic
  - service
  - images
  - cloud
lang: es
---

Hola amigos, sean bienvenidos a esta serie de artículos introductorios dedicados a Elastic Compute Service o ECS de Alibaba. En esta tercera sección veremos ECS Images.

## ¿Qué son las imagenes de ECS?

Las imágenes son una plantilla de un entorno de ejecución para una instancia de ECS. Existen 4 tipos principales.

### Imágenes Públicas del Sistema (Public System Images)
 Las imágenes públicas con licencia de Alibaba Cloud son muy seguras y estables. Estas imágenes públicas incluyen la mayoría de los sistemas Windows Server y Linux convencionales. 
 
 Estas imágenes solo incluyen entornos de sistema estándar y puede aplicar su propia personalización y configuraciones basadas en estas imágenes.

### Imágenes de Marketplace (Marketplace Images) 
Las imágenes de Alibaba Cloud Marketplace se clasifican en los 2 tipos siguientes:

- Imágenes proporcionadas por Alibaba Cloud
- Imágenes proporcionadas por Proveedores de Software Independientes y con licencia de Alibaba Cloud Marketplace. 

Una imagen de Alibaba Cloud Marketplace contiene un sistema operativo y software preinstalado. 

El proveedor de software independiente (ISV - Independent Software Vendors) y Alibaba Cloud prueban y verifican el sistema operativo y el software preinstalado para garantizar que las imágenes sean seguras de usar. Estos son adecuados para la creación de sitios web, el desarrollo de aplicaciones y otros escenarios de uso personalizados.

### Imagen Personalizada (Custom Images)
Las imágenes personalizadas se crean a partir de instancias o instantáneas del sistema, o se importan desde su dispositivo local. Solo el creador de una imagen personalizada puede usar, compartir, copiar y eliminar la imagen. 

Estas imágenes personalizadas se pueden utilizar para crear más instancias, lo que le ahorrará el esfuerzo de crear un nuevo sistema desde cero.

### Imagen Compartida (Shared Images)
Una imagen compartida es una imagen personalizada que se ha compartido con otros usuarios o cuentas. 

Cabe mencionar que Alibaba Cloud no puede garantizar la seguridad e integridad de las imágenes compartidas con usted o con cualquier otro usuario, por lo que si hace uso de esta imagen, la usa bajo su propio riesgo y discreción.