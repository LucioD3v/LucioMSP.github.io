---
layout: post
title: Fundamentos de ECS - Grupos de Seguridad (Security Groups)
description: Sexta entrega sobre Elastic Compute Service (ECS) de Alibaba - Grupos de Seguridad (Security Groups).
image: /assets/img/blog/post-headers/alibaba/alibaba-cloud.jpg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [alibaba]
tags:
  - alibaba
  - security
  - groups
  - seguridad
keywords:
  - alibaba
  - ecs
  - elastic
  - service
  - security
  - cloud
  - seguridad
lang: es
---

Hola amigos, sean bienvenidos a esta serie de artículos introductorios dedicados a Elastic Compute Service o ECS de Alibaba. En esta sexta entrega veremos grupos de seguridad (Security Groups) de ECS.

## ¿Qué es son los grupos de seguridad de ECS?
Los grupos de seguridad actúan como cortafuegos virtuales que proporcionan inspección completa de paquetes y filtrado de paquetes del protocolo de red, el puerto y el tráfico IP de origen para permitir o denegar el acceso. 

Cabe destacar que podemos configurar reglas de grupo de seguridad para controlar el tráfico entrante y saliente de las instancias de ECS en el grupo.

Hay 2 clasificaciones de grupos de seguridad: Básico y Avanzado. 

- Los grupos de seguridad básica admiten hasta 2000 direcciones IP privadas, las reglas de entrada y salida se pueden configurar para permitir o denegar el acceso a Internet o intranet a las instancias de ECS en grupos de seguridad básica. 

- Los grupos de seguridad avanzada son un nuevo tipo de grupo de seguridad. En comparación con un grupo de seguridad básico, un grupo de seguridad avanzado puede contener un número ilimitado de direcciones IP privadas. Solo puede configurar reglas de permiso para el tráfico entrante y saliente, ya que todo el tráfico no permitido está denegado de forma predeterminada.

## Características
Los grupos de seguridad tienen las siguientes características: 

** Debe especificar un grupo de seguridad cuando crea una instancia de ECS. 

** Cada instancia de ECS debe pertenecer al menos a un grupo de seguridad, pero se puede agregar a varios grupos de seguridad al mismo tiempo. 

** Las instancias de ECS no pueden pertenecer a grupos de seguridad básicos y avanzados al mismo tiempo. 

** Las instancias de ECS en el mismo grupo de seguridad pueden comunicarse entre sí a través de la red interna.

** Las instancias de ECS en diferentes grupos de seguridad están aisladas entre sí.

** Se pueden agregar reglas de grupo de seguridad para autorizar el acceso mutuo entre dos grupos de seguridad. 

** Se pueden configurar reglas de grupo de seguridad solo para grupos de seguridad básicos, para autorizar el acceso mutuo entre dos grupos de seguridad.

## Grupo de Seguridad Predeterminado
cuando crea una instancia de ECS en una región a través de la consola de ECS, se crea un grupo de seguridad predeterminado si no se ha creado ningún otro grupo de seguridad en la cuenta actual en esta región. El grupo de seguridad predeterminado es un grupo de seguridad básico y tiene el mismo tipo de red que la instancia de ECS.
