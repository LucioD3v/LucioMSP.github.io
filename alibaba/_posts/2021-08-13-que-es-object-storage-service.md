---
layout: post
title: ¿Qué es OSS (Object Storage Service)? - Alibaba Cloud 
description: Conoce a detalle que es el servicio de almacenamiento de objetos (OSS) de Alibaba Cloud
image: /assets/img/blog/post-headers/alibaba/oss.png
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [alibaba]
tags:
  - alibaba
  - oss
  - object
  - storage
  - service
keywords:
  - alibaba
  - oss
  - object
  - service
lang: es
---

Antes de hablar sobre qué es OSS, primero veamos una breve descripción general de los dos tipos principales de almacenamiento tradicional disponibles en Alibaba Cloud. Estos son el almacenamiento de archivos (File Storage) y el almacenamiento en bloque (Block Storage). 

# Almacenamiento de Archivos (File Storage)

También conocido como almacenamiento en red, se basa en un sistema de archivos compartidos. Este tipo de almacenamiento brinda a varios clientes la capacidad de acceder a los mismos datos compartidos a través de una red. La interfaz para esto generalmente está en el lado del cliente. Los dos protocolos más populares para acceder a este tipo de almacenamiento son NFS y SMB.

# Almacenamiento en Bloque (Block Storage). 

El almacenamiento en bloque es un servicio de almacenamiento en bloque de alto rendimiento y baja latencia para las máquinas virtuales Alibaba Cloud ECS. Y admite operaciones de lectura y escritura aleatorias o secuenciales. El almacenamiento en bloque es similar a un disco físico. Puede formatear un dispositivo de almacenamiento en bloque y crear un sistema de archivos en él para satisfacer las necesidades de almacenamiento de datos de su empresa. Los servicios de almacenamiento de archivos y bloques son servicios de datos estructurados y su precio se basa en el usuario final definido en la capacidad requerida. En otras palabras, paga por lo que proporciona.

# Entonces.... ¿qué es OSS? 

El servicio de almacenamiento de objetos (Object Storage Service u OSS) es un servicio que le permite almacenar, realizar copias de seguridad y archivar cualquier cantidad de datos no estructurados, como imágenes, videos, documentos en la nube. A diferencia de un servicio de archivos estructurado, donde navegaría a un archivo a través de su estructura de directorio, los archivos en OSS se cargan en un contenedor y cada archivo tiene su propia dirección única para acceder a él.

OSS es una solución de almacenamiento en la nube rentable, altamente segura, fácilmente escalable y altamente confiable. Con OSS, puede almacenar y recuperar cualquier tipo de datos en cualquier momento y desde cualquier lugar. Puede utilizar las operaciones de API y los SDK proporcionados por la nube de Alibaba o las herramientas de migración de OSS para transferir cantidades masivas de datos hacia o desde el OSS de Alibaba Cloud.

# ¿Cuáles son las ventajas sobre el uso de los servicios de almacenamiento tradicionales? 

El primero es la confiabilidad. OSS ofrece hasta un 99,995% de disponibilidad de servicio para proteger contra interrupciones del servicio y hasta 12 nueves de durabilidad de datos para mantener sus datos seguros. Ofrece escalado automático sin afectar los servicios externos. También ofrece una copia de seguridad de datos redundante automática. Y con la replicación entre regiones opcional, puede admitir la conmutación por error automática. Entonces redundancia.

Hay dos tipos de redundancia disponibles en OSS: 

- Almacenamiento Redundante Local (Local Redundant Storage, conocido como LRS)
- Almacenamiento Redundante de Zona (Zone Redundant Storage, conocido como ZRS)

LRS almacena los datos de cada objeto en varios dispositivos en la misma región, lo que garantiza la durabilidad y disponibilidad de los datos en caso de falla del hardware. ZRS distribuye los datos del usuario en tres zonas dentro de la misma región. Incluso si una zona deja de estar disponible, sus datos seguirán siendo accesibles. La integridad de los datos se verifica periódicamente para descubrir daños en los datos causados ​​por factores como fallas de hardware. OSS reconstruye y repara datos dañados utilizando datos redundantes.

# Seguridad. 

OSS proporciona seguridad multinivel de nivel empresarial y protección contra ataques de denegación de servicio. Es compatible con el aislamiento de recursos de múltiples usuarios y la recuperación remota de desastres. También proporciona autorización de autenticación, dirección IP, listas negras y listas blancas y funciones de administración de acceso a recursos o cuentas RAM. Y proporciona un registro completo para ayudar a rastrear el acceso malicioso.

# Costos. 

OSS cobra tarifas basadas en el uso real. Las tarifas incurridas dentro de una hora se facturan en la próxima hora. Las tarifas se calculan en función de la fórmula: las tarifas equivalen al uso real multiplicado por el precio unitario. Y el término uso real se basa en el volumen de almacenamiento utilizado, la cantidad de datos transferidos y la cantidad de solicitudes de API realizadas. No hay costos iniciales y la carga de datos en OSS es gratuita. Es fácil de usar.

OSS proporciona una interfaz API de descanso estándar, una amplia gama de herramientas de cliente SDK y una consola basada en web. Puede cargar, descargar, recuperar y administrar fácilmente cantidades masivas de datos para sitios web y aplicaciones de la misma manera que para archivos normales en Windows. No hay límite en la cantidad de archivos. Los tamaños de archivo pueden ser desde un bocado hasta un tamaño máximo de 48,8 terabytes para un solo archivo. Sin embargo, el tamaño máximo depende del método que se utilice para cargar. Y a diferencia del almacenamiento de hardware tradicional, OSS le permite escalar o expandir fácilmente su espacio de almacenamiento según sea necesario.

Es compatible con la carga y descarga en tiempo real, lo que es adecuado para escenarios comerciales. Por ejemplo, cuando necesite leer y escribir videos y otros archivos grandes simultáneamente. Y ofrece gestión del ciclo de vida. Puede eliminar datos vencidos por lotes o transferir los datos a servicios de archivo de menor costo. Algunas de las otras ventajas incluyen el procesamiento de imágenes, que admite conversión de formato, miniaturas, recorte, marcas de agua, escalado y otras operaciones. Transcodificación de audio y video, que proporciona capacidades de transcodificación de audio / video en paralelo de alta calidad y alta velocidad para archivos de audio / video almacenados en OSS. Y la red de entrega de contenido de Alibaba se puede utilizar para acelerar la entrega de contenido almacenado en OSS.