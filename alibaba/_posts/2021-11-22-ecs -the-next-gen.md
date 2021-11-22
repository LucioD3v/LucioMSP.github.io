---
layout: post
title: ECC - la nueva generación (Gen 7)
description: El servidor en la nube Elastic Compute Service (ECS) es un servicio básico de computación en la nube proporcionado por Alibaba Cloud.
image: /assets/img/blog/post-headers/alibaba/ecsGen7.png
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [alibaba]
tags:
  - alibaba
  - ecs
keywords:
  - alibaba
  - gen7
  - ecs
lang: es
---

Si han estado prestando atención a la consola (o al servicio de noticias en alibabacloud.com), es posible que hayan notado que han lanzado nuevas instancias de séptima generación de ECS. Esta actualización aporta nueva potencia y capacidades al servicio ECS, más allá de las principales mejoras aportadas por la generación 6.

Pero..., ¿qué significa realmente la Generación 7 en términos de características y rendimiento? Vayamos a ver:

## ¿Qué tiene de especial Gen 7?

### 1. Nuevos Procesadores

Las nuevas instancias Gen 7 funcionan con chips Intel Ice Lake, que superan a los chips de servidor Intel anteriores en aproximadamente un 30% para muchas tareas.

Esto también significa un mejor soporte para las operaciones de cifrado y transcodificación de medios, lo que significa que las máquinas virtuales ECS que se ejecutan en la parte superior del hardware Gen 7 pueden realizar el procesamiento de audio y video de manera más eficiente.

La velocidad máxima de reloj también se ha aumentado de 3,2 Ghz (Gen 6) a 3,5 Ghz, para aquellos usuarios que ejecutan aplicaciones urgentes. Si necesita velocidades de reloj aún más altas que eso, consulte la clase de instancia hfg7 basada en Cooper Lake, que tiene una frecuencia turbo de todos los núcleos de hasta 3.8 Ghz.

2. Mejor rendimiento de la red

Las instancias Gen 7 vienen con dos interfaces de red de 50 Gigabit, lo que permite un rendimiento de paquetes de hasta 24 millones de paquetes por segundo y un rendimiento de red de hasta 64 Gbit/s (para los tipos de instancias de ECS más grandes, como 32xlarge).

3. Computación confiable

Las instancias de la séptima generación son compatibles con SGX (Software Guard Extensions) 2.0 de Intel, lo que significa que puede crear enclaves protegidos para los datos en la memoria.

Aunque esto ya estaba disponible en las instancias Gen 6, las instancias Gen 7 también vienen equipadas con chips TPM (Trusted Platform Module), lo que permite una seguridad general aún más sólida y un entorno de arranque a prueba de manipulaciones.

4. Almacenamiento más rápido

Las nuevas instancias Gen 7 utilizan la tecnología Enhanced SSD (ESSD) de Alibaba Cloud, lo que permite un rendimiento de almacenamiento de hasta 32 Gbit / sy 600.000 IOPS. Esta es una mejora significativa con respecto a instancias anteriores: hasta aproximadamente 3 veces más rápido, de hecho.

## ¿Qué configuraciones de hardware están disponibles?

Hay tres:

- g7: de uso general (CPU: relación de memoria de 1:4)
- c7: Computación optimizada (CPU: relación de memoria de 1:2)
- r7: memoria optimizada (CPU: relación de memoria de 1:8)

¿Qué tan grandes se vuelven?

La instancia de g7 más grande es ecs.g7.32xlarge, que ofrece:

- 128 núcleos de CPU
- 512 GB de RAM
- Ancho de banda de red de 64 Gbit/s
- Rendimiento del disco hasta 600.000 IOPS (32 Gbps)
- Rendimiento de red de hasta 24 millones de PPS

La instancia c7 más grande es ecs.c7.32xlarge, que ofrece:

- 128 núcleos de CPU
- 256 GB de RAM
- Ancho de banda de red de 64 Gbit/s
- Rendimiento del disco hasta 600.000 IOPS (32 Gbps)
- Rendimiento de red de hasta 24 millones de PPS

La instancia de r7 más grande es ecs.r7.32xlarge, que ofrece:

- 128 núcleos de CPU
- 1024 GB de RAM
- Ancho de banda de red de 64 Gbit/s
- Rendimiento del disco hasta 600.000 IOPS (32 Gbps)
- Rendimiento de red de hasta 24 millones de PPS

¿Qué aplicaciones se benefician?
Realmente cualquier aplicación se beneficiará de un mejor hardware, pero en particular estas aplicaciones pesadas de CPU, disco y red se benefician más:

Aplicaciones blockchain
Aplicaciones de base de datos
Codificación/decodificación/transcodificación de video y audio

### ¡Oye, no puedo encontrar Gen 7 en mi región!

¡El hardware aún se está implementando! Si aún no ve instancias Gen 7 disponibles en su región, es probable que el hardware aún se esté instalando y probando.

Si realmente tiene prisa por tener en sus manos este nuevo hardware, mire a su alrededor en las regiones vecinas. Por ejemplo, si descubrió que la región de Singapur carecía de Gen 7, también podría buscar en regiones vecinas como Indonesia o Malasia.

Si creen que esta publicación fue demasiado corta, los invitamos a que consulten la página de [ECS Generation 7](https://www.alibabacloud.com/ecs-gen7?spm=a2c65.11461447.0.0.366158d09OjLEs) para obtener más detalles. 



