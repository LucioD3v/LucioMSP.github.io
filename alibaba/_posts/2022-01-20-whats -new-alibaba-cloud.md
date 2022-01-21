---
layout: post
title: ¿Qué hay de nuevo en la nube de Alibaba?
description: Vea las novedades de Alibaba Cloud de esta semana que nos trae el equipo de Alibaba Cloud Academy. ¡Uno de los nuevos servicios podría sorprenderte!
image: /assets/img/blog/post-headers/alibaba/alibabaNewsJan2022.jpeg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [alibaba]
tags:
  - alibaba
  - polardb
  - rds
  - ecs
  - function compute
keywords:
  - alibaba
  - polardb
  - rds
  - ecs
  - function compute
lang: es
---

Esta semana echamos un vistazo rápido a las novedades en el mundo de Alibaba Cloud.
# Novedades: 

## Bases de Datos

### PolarDB

La [función de proxy](https://www.alibabacloud.com/help/en/doc-detail/173396.html?spm=a2c65.11461447.0.0.c51077dccYyf5F) de la base de datos PolarProxy se convertirá en una función paga, incluida en la edición Enterprise de PolarDB. El clúster de base de datos de archivo de PolarDB ahora es compatible con MySQL 8.0.

### RDS

- RDS (MySQL) ahora admite el cambio de zona de disponibilidad con un solo clic (dentro de una sola región, por supuesto). ¡Todo el proceso de migración se maneja automáticamente! 
- RDS (PostgreSQL) ahora es compatible con PostgreSQL 14.1.
- RDS (SQL Server) ha agregado soporte para algunas versiones adicionales de SQL Server: ediciones básicas para 2016EE, 2016SE, 2017SE, 2019SE, 2017 Web y 2019 Web.

### Otras actualizaciones de la base de datos

- AnalyticDB para PostgreSQL ha lanzado una edición sin servidor. Como se trata de una versión anticipada, debe enviar un [ticket de soporte](https://workorder-intl.console.aliyun.com/?spm=a2c65.11461447.0.0.c51077dccYyf5F#/ticket/list) para habilitar esta función.
- La herramienta de migración de datos DTS ahora es compatible con Microsoft SQL Server 2019.

## Novedades: Informática

### ECS

- Se han agregado dos nuevos tipos de instancias ECS equipados con AMD de séptima generación, en particular ebmg7a y ebmr7a, que son instancias Bare Metal de séptima generación con procesadores AMD. Estas instancias basadas en AMD ofrecen una excelente relación precio/rendimiento y admiten grandes cantidades de memoria... en el caso de ebmr7a, ¡hasta 256 núcleos de vCPU y 2048 GB de memoria!

- Ya está disponible un nuevo tipo de instancia Bare Metal equipada con GPU, la ebmgn7e, que utiliza GPU NVIDIA A100 SXM4 de 80 GB con compatibilidad con NVSwitch y ofrece hasta 312 TFLOPS en TensorFloat-32.

### Function Compute

Una herramienta completamente nueva, [Serverless Devs](https://www.alibabacloud.com/help/en/doc-detail/195473.htm?spm=a2c65.11461447.0.0.c51077dccYyf5F), ahora reemplaza a la divertida herramienta de línea de comandos como la forma recomendada de implementar y administrar aplicaciones sin servidor.

La herramienta es demasiado grande para cubrirla en detalle en la publicación de blog de esta semana, pero eche un vistazo a la documentación de Serverless Devs (enlace en el párrafo anterior), o consulte [esta publicación de blog](https://community.alibabacloud.com/blog/598366?spm=a2c65.11461447.0.0.c51077dccYyf5F) donde uso Serverless Devs para implementar un tiempo de ejecución de contenedor personalizado.

### Compute Nest

Un servicio completamente nuevo, [Compute Nest](https://www.alibabacloud.com/help/en/doc-detail/290066.html?spm=a2c65.11461447.0.0.c51077dccYyf5F), ya está disponible.

Compute Nest es un servicio PaaS que proporciona una plataforma de gestión centralizada para proveedores de servicios.

Esencialmente, es una herramienta para ayudarlo a construir e implementar sus propios servicios en la nube sobre Alibaba Cloud. Si es un proveedor de software independiente (ISV), un proveedor de servicios de TI, un proveedor de servicios de entrega (implementación) o un proveedor de O&M, puede usar Compute Nest para crear e implementar servicios en Alibaba Cloud, que luego puede poner a disposición de sus usuarios finales. .

Consulte la documentación para obtener más detalles.

### Server Migration Center (Centro de migración del servidor)

- La herramienta de migración go2aliyun de Server Migration Center [ahora admite migraciones de servidor ARM64](https://www.alibabacloud.com/help/en/doc-detail/122992.htm?spm=a2c65.11461447.0.0.c51077dccYyf5F).

## Novedades: Contenedores

### Servicio de contenedores para Kubernetes (ACK)

- Se agregó una [función de análisis de costos de clúster](https://www.alibabacloud.com/help/en/doc-detail/215497.htm?spm=a2c65.11461447.0.0.c51077dccYyf5F), que le permite crear paneles para comprender mejor sus gastos de ACK. ¡Se ve bastante bien!

![image](/assets/img/blog/tutorials/alibaba/whatsNewAlibaba/containerService.png)

### Registro de contenedores en la nube de Alibaba (ACR)

- Ahora puede sincronizar manualmente las imágenes de los contenedores, así como reintentar manualmente las tareas de sincronización fallidas. Esto funciona tanto para la [sincronización dentro de una sola región](https://www.alibabacloud.com/help/en/doc-detail/147064.htm?spm=a2c65.11461447.0.0.c51077dccYyf5F) como para la [sincronización entre regiones](https://www.alibabacloud.com/help/en/doc-detail/305586.htm?spm=a2c65.11461447.0.0.c51077dccYyf5F).

## Novedades: Seguridad

### ActionTrail

- ActionTrail ha agregado una función de [Insight Events](https://www.alibabacloud.com/help/en/doc-detail/289019.htm?spm=a2c65.11461447.0.0.c51077dccYyf5F) para ayudar a los usuarios a identificar automáticamente operaciones inusuales. Esta es una gran ayuda para descubrir configuraciones erróneas y errores temprano.

### Bastion Host
- El servicio [Bastion Host](https://www.alibabacloud.com/help/en/doc-detail/52922.html?spm=a2c65.11461447.0.0.c51077dccYyf5F) ahora le permite crear reglas de autorización de tiempo limitado para los usuarios, permitiéndoles acceso temporal a una o más instancias de ECS detrás de la instancia de Bastion Host.

- Ahora puede importar y exportar configuraciones de Bastion Host, lo que le permite transferir todos sus datos de configuración existentes de un Bastion Host a otro.

### Big Data e IA
-------------------------------------------------------------

### QuickBI

QuickBI ahora ha agregado soporte para una amplia gama de bases de datos autoconstruidas. 

Los siguientes ahora son compatibles como fuentes de datos en QuickBI 3.12.2:

- Copo de nieve
- Impala
- Kylin

Ahora puede exportar tablas y gráficos como imágenes y archivos PDF, además del formato Excel.
También puede exportar informes directamente a OSS.

### PAI (Plataforma para IA)

Se han agregado [modelos ASR](https://www.alibabacloud.com/help/en/doc-detail/196904.htm?spm=a2c65.11461447.0.0.c51077dccYyf5F) actualizados para hablar en chino e inglés a Model Hub. Esto le permite entrenar más fácilmente sistemas automáticos de reconocimiento de voz de alta precisión.

### Redes
-----------------------------------------------------------------------

### Nube Privada Virtual (VPC)

Técnicamente, estas funciones no son tan nuevas (la mayoría se lanzaron a mediados de 2021), pero siguen siendo importantes. Estas son cuatro adiciones importantes al servicio de VPC que todo el mundo debería conocer:

1. - Los [conjuntos de opciones de DHCP](https://www.alibabacloud.com/help/en/doc-detail/174112.htm?spm=a2c65.11461447.0.0.c51077dccYyf5F) le permiten personalizar DHCP dentro de su VPC. Esto le permite pasar automáticamente la información del servidor DNS a las nuevas instancias de ECS tan pronto como se conecten, o establecer nombres de dominio personalizados para sus instancias de ECS.

2. - La [duplicación de tráfico](https://www.alibabacloud.com/help/en/doc-detail/207513.htm?spm=a2c65.11461447.0.0.c51077dccYyf5F) le permite reenviar el tráfico destinado a una ENI (interfaz de red elástica) a un equilibrador de carga o una ENI secundaria, lo cual es ideal para la detección, el registro y la supervisión de amenazas, o simplemente para la resolución de problemas antiguos.

3. - Las VPC ahora son compatibles con las [ACL de red (NACL)](https://www.alibabacloud.com/help/en/doc-detail/116626.htm?spm=a2c65.11461447.0.0.c51077dccYyf5F), lo que le permite un control más detallado sobre cómo se pueden comunicar los ENI y los VSwitches. Esto le permite hacer cosas como crear una "subred privada" (VSwitch) que no puede comunicarse con Internet.

4. - El [uso compartido de VPC](https://www.alibabacloud.com/help/en/doc-detail/160633.htm?spm=a2c65.11461447.0.0.c51077dccYyf5F) le permite hacer algo realmente genial: con el uso compartido de VPC, puede permitir que varias cuentas de Alibaba Cloud creen recursos dentro de una sola VPC. Esto significa que más de una cuenta puede crear bases de datos de RDS, instancias de ECS o balanceadores de carga dentro de una sola VPC compartida. Esto ayuda a evitar la necesidad de configurar la interconexión de VPC mediante CEN.

### VPN Gateway (Puerta de enlace VPN)

VPN Gateway ahora ha agregado soporte para BGP Dynamic Routing. Aprende más [aquí](https://www.alibabacloud.com/help/en/doc-detail/170235.html?spm=a2c65.11461447.0.0.c51077dccYyf5F).

-----------------------------------------

## Cosas Inusuales

¿Sabía que Alibaba Cloud tiene un servicio para extraer datos de futuros y bolsas de valores? Si, existe en realidad y se llama [CloudQuotation](https://www.alibabacloud.com/help/en/doc-detail/147299.html?spm=a2c65.11461447.0.0.c51077dccYyf5F). Puedes encontrarlo en la consola [aquí](https://assetservice.console.aliyun.com/commodity?spm=a2c65.11461447.0.0.c51077dccYyf5F).

Es costoso, pero si está creando una aplicación financiera y necesita acceso a datos de mercado actualizados, CloudQuotation es un buen lugar para comenzar.

Blog Post Original: [alibabacloud.com](https://www.alibabacloud.com/blog/598490)


