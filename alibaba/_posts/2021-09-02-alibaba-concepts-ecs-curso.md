---
layout: post
title: Fundamentos de (Elastic Compute Service) - Conceptos
description: Segundo artículo sobre el Elastic Compute Service de Alibaba, o ECS, uno de los servicios más comunes dentro de la plataforma Alibaba.
image: /assets/img/blog/post-headers/alibaba/second-article-ecs-header.jpeg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [alibaba]
tags:
  - alibaba
  - compute
keywords:
  - alibaba
  - ecs
  - elastic
  - service
  - concepts
  - cloud
lang: es
---

Hola amigos, sean bienvenidos a esta serie de artículos introductorios dedicados a Elastic Compute Service o ECS de Alibaba. La primera sección que veremos son los conceptos de ECS.

# Conceptos de Elastic Compute Service (ECS)

 Entonces, ¿qué es ECS? Elastic Compute Service (ECS) es un servicio informático con capacidad de procesamiento flexible. Es una solución de nivel IaaS de alto rendimiento, estable, confiable y escalable que se utiliza para implementar servidores virtuales conocidos como instancias. IaaS o Infraestructura como Servicio es un concepto en el que Alibaba proporciona y administra la virtualización, los servidores, el almacenamiento y las redes. Y así, nosotros como clientes, podemos seleccionar el sistema operativo, instalar aplicaciones y administrar nuestros datos.

En el siguiente diagrama, se pueden ver las diferentes responsabilidades cuando se aprovisiona un servidor en las instalaciones y cuando se aprovisiona un servidor dentro de Alibaba Cloud ECS. Las instancias pueden implementar y administrar fácilmente aplicaciones con mejor estabilidad y seguridad, en comparación con los servidores físicos en las instalaciones.

![image](/assets/img/blog/tutorials/alibaba/articulos-ecs/on-premise-vs-alibaba.png)

Las instancias de ECS proporcionan una capacidad informática redimensionable en la nube. Están diseñados para facilitar la informática a gran escala y es que se pueden crear instancias con una variedad de sistemas operativos. Alibaba es compatible con la mayoría de los sistemas principales de Linux y Microsoft Windows Server, aunado a que se pueden ejecutar tantas instancias como se desee.

# ¿Por qué utilizar ECS? 

A diferencia del aprovisionamiento de máquinas en las instalaciones, no tiene que comprar ningún hardware por adelantado. Las instancias en la nube de Alibaba se entregan en minutos, lo que permite una implementación rápida con poco o ningún tiempo de espera. Puede escalar y eliminar recursos en función de las necesidades comerciales reales. Las instancias de ECS proporcionan una gran cantidad de soluciones de seguridad integradas, como firewalls virtuales, aislamiento de red interno, acceso a IP pública, protección antivirus y contra ataques de denegación de servicio.

Elastic Compute Service se proporciona a través de una capa de virtualización que se proporciona en los centros de datos de todo el mundo. Los centros de datos contienen miles de racks y aquí es donde se encuentra la tecnología de virtualización. Alibaba utiliza la virtualización XEN y KVM para aprovisionar sus instancias ECS. Estas instancias, a su vez, se ejecutan sobre la plataforma informática X-Dragon y el sistema de archivos distribuido de Apsara llamado Pangu, que proporciona el sistema de almacenamiento.

ECS comprende los siguientes componentes principales:

- Instancia: un entorno informático virtual que incluye componentes informáticos básicos como CPU, memoria, ancho de banda de red y discos.

- Imagen: proporciona el sistema operativo, los datos iniciales de la aplicación y el software preinstalado para las instancias.

- Almacenamiento en bloque: un dispositivo de almacenamiento en bloque basado en el Servicio de almacenamiento de objetos (OSS) que presenta discos distribuidos en la nube de alto rendimiento y baja latencia.

- Grupos de seguridad: los utiliza un grupo lógico de instancias ubicadas en la misma región que tienen los mismos requisitos de seguridad y requieren acceso entre sí.

- Red: una red de nube privada lógicamente aislada. Las regiones son ubicaciones físicas con uno o más centros de datos distribuidos por todo el mundo para reducir la latencia de la red. 

La región es donde Alibaba Cloud Services lanzará la instancia que cree. Elija una región para optimizar la latencia, minimizar el costo o abordar los requisitos reglamentarios. Hay regiones específicas en China continental y otras regiones internacionales disponibles. Para la lista actual de regiones alrededor del mundo, se proporciona un enlace en la pestaña de transcripción. Tener varias regiones en todo el mundo significa que puede aprovisionar servidores más cerca de sus usuarios. 

Las zonas se refieren a centros de datos físicos dentro de una región que tienen fuentes de alimentación y redes independientes. Los usuarios pueden separar las instancias de ECS en diferentes zonas de una región para facilitar, por ejemplo, la "alta disponibilidad". Las instancias de ECS creadas en una sola región tendrán conectividad de red de intranet privada de baja latencia con otras zonas de la misma región. Sin embargo, las instancias de ECS creadas en diferentes regiones, de forma predeterminada, no tendrán conectividad de red privada. Sin embargo, la latencia de la red para instancias dentro de la misma zona es menor que cuando se comunican entre zonas en la misma región.

[Más Información](https://www.alibabacloud.com/help/doc-detail/123712.htm?spm=a2c63.p38356.b99.10.7f951d600WKWd5)