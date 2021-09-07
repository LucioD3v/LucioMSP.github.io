---
layout: post
title: Fundamentos de ECS - Almacenamiento
description: Cuarto artículo sobre Elastic Compute Service (ECS) de Alibaba - Almacenamiento. 
image: /assets/img/blog/post-headers/alibaba/alibaba-storage.jpg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [alibaba]
tags:
  - alibaba
  - storage
keywords:
  - alibaba
  - ecs
  - elastic
  - service
  - store
  - cloud
  - almacenamiento
lang: es
---

Hola amigos, sean bienvenidos a esta serie de artículos introductorios dedicados a Elastic Compute Service o ECS de Alibaba. En esta cuarta entrega veremos ECS Storage y bueno, antes de comenzar con la ECS Storage, conozcamos primero que es Block Storage.

## Block Storage

Es un servicio de almacenamiento en bloque de alto rendimiento y baja latencia. Admite operaciones de lectura y escritura secuenciales o aleatorias. El almacenamiento en bloque es similar a un disco físico, puede formatear un dispositivo de almacenamiento en bloque y crear un sistema de archivos en él para satisfacer las necesidades de almacenamiento de datos de su empresa.

## Por otro lado...

ECS Storage proporciona discos en la nube basados ​​en arquitectura para los discos de su sistema operativo y los discos de datos.

Los discos en la nube (Cloud Disks) se basan en el sistema de archivos distribuidos de Apsara llamado "Pangu", los cuales almacenan tres copias redundantes en diferentes servidores físicos bajo diferentes conmutadores en el centro de datos. Esto proporciona una alta confiabilidad de los datos en caso de falla.

Actualmente, existen 3 tipos de disco en la nube:

- Ultra Disk: discos en la nube con alta rentabilidad, rendimiento de IOPS aleatorio medio y alta confiabilidad de los datos.
- SSD Estándar: discos de alto rendimiento que cuentan con un rendimiento de IOPS aleatorio alto y constante y una alta confiabilidad de los datos.
- SSD Mejorado (Enhanced SSD (ESSD)): los ESSD son discos de rendimiento ultra alto basados ​​en la arquitectura de almacenamiento de bloques distribuidos de próxima generación. Cada ESSD puede entregar hasta 1 millón de IOPS aleatorias y tiene baja latencia.

Las 2 funciones de Cloud Disks son las siguientes:
### Como disco del sistema

De forma predeterminada, el disco del sistema tiene el mismo ciclo de vida que la instancia de ECS en la que está montado y se libera junto con la instancia de ECS. (Esta función de liberación automática se puede cambiar). No se permite el acceso compartido a los discos del sistema. Los tamaños de disco del sistema pueden ser de 20 GB y 500 GB. Esto depende del sistema operativo que se esté aprovisionando. 

Los sistemas Linux y FreeBSD tienen un valor predeterminado de 20 GB. Los sistemas CoreOS tienen un valor predeterminado de 30 GB. Y los sistemas Windows predeterminados a 40 GB.
### Como discos de datos

Los discos de datos se pueden crear por separado o al mismo tiempo que una instancia de ECS. Los discos de datos creados al mismo tiempo que las instancias de ECS tienen el mismo ciclo de vida que la instancia correspondiente y se publican junto con la instancia de forma predeterminada. Y nuevamente, esta función de liberación automática se puede cambiar. Los discos de datos creados por separado se pueden liberar por separado o al mismo tiempo que la instancia de ECS correspondiente. 

Y al igual que el disco del sistema, el acceso compartido a un disco de datos no está permitido. Los tamaños de los discos de datos pueden oscilar entre 20 GB y 32 TB y se pueden conectar hasta 16 discos de datos a una única instancia de ECS. 

Los discos de nube se pueden montar en cualquier instancia de la misma zona, pero no se pueden montar en instancias de distintas zonas.

![image](/assets/img/blog/tutorials/alibaba/articulos-ecs/storage-zones.pngg)
