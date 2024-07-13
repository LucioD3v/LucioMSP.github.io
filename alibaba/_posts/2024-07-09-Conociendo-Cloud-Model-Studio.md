---
layout: post
title: Conociendo Alibaba Cloud Model Studio
description:
  La plataforma integral de IA generativa de Alibaba Cloud está diseñada para ayudarnos a crear aplicaciones inteligentes que realmente comprendan nuestro negocio. Basada en Qwen y otros modelos populares de IA, Alibaba Cloud ha liberado un nuevo producto denominado "Model Studio", el cual nos ofrece una solución poderosa y versátil que se adapta a nuestras necesidades específicas.
image: /assets/img/blog/post-headers/alibaba/modelStudio.jpeg
comments: true
author: lucio
kate: hl markdown;
categories: [alibaba]
tags:
  - alibaba
  - cloud
  - model
  - studio
keywords:
  - alibaba
  - cloud
  - model
  - studio
lang: es
---

## ¿Qué es Alibaba Cloud Model Studio?

Alibaba Cloud Model Studio es una plataforma integral diseñada específicamente para el desarrollo de IA generativa. Con fácil acceso a los modelos básicos (FM) líderes en la industria, incluidas las series Qwen-Max, Qwen-Plus, Qwen-Turbo y Qwen 2, puede personalizar estos modelos con los datos de su empresa configurando una generación de recuperación aumentada (RAG) arquitectura con un solo clic, cree agentes de IA en unos pocos pasos simples y desarrolle aplicaciones de IA generativa (GenAI) que comprendan su negocio sin preocuparse por la infraestructura subyacente y la potencia informática, todo en una red de nube aislada que mitiga los riesgos de privacidad.

Dicho de otra manera, AC Model Studio permite a los desarrolladores y empresas construir, entrenar, y desplegar modelos de inteligencia artificial (IA) y aprendizaje automático (ML) de manera eficiente.

## Características principales:

**1. Capability-Enhanced FMs**: Permite impulsar nuestras aplicaciones con capacidades mejoradas de modelos de IA, como preguntas y respuestas, escritura, NL2SQL, etc., de la serie Tongyi de Alibaba Cloud, que incluye Tongyi Qwen, Tongyi Wanxiang y la serie de modelos Qwen de código abierto.
**2. Built-In Model Inference and Evaluation Workflows**: Nos permite acelerar los flujos de trabajo de desarrollo de modelos con herramientas integrales diseñadas para admitir SFT y LoRA, compresión de modelos integrada y aceleración de inferencia, evaluación de modelos multidimensionales en plantillas visualizadas e implementación de modelos con un solo clic.
**3. Simplified GenAI Application Development**: Nos permite agilizar el desarrollo de aplicaciones de IA generativa con flujos de trabajo prediseñados en lienzo visualizado, orquestación altamente personalizable, ingeniería de avisos basada en plantillas y un amplio conjunto de API para una fácil integración con su sistema empresarial.
**4. Comprehensive Security Measures**: Nos permite proteger los datos de la empresa en almacenamiento y transmisión completando el desarrollo de modelos y aplicaciones en su red dedicada de Nube Privada Virtual (VPC) y accediendo a los datos con PrivateLink, aplicando una gobernanza de contenido personalizable a las indicaciones y el contenido, y combinando principios de IA responsable con herramientas para la responsabilidad humana.

## ¿Cómo funciona?

- **API y SDKs**: Integre capacidades de FM en sus sistemas y aplicaciones empresariales con API diseñadas específicamente, que están encapsuladas en SDK que admiten lenguajes de programación convencionales.
- **Herramientas del Agente**: Cree agentes de IA en pasos simples con un amplio conjunto de complementos, servicios de orquestación de aplicaciones visualizados, así como plantillas y herramientas de optimización para una ingeniería rápida.
- **API Asistente**: Apoye el desarrollo de agentes con complementos diseñados específicamente y un amplio conjunto de API.
- **Desarrollo de modelos con conjunto de herramientas**: Administre conjuntos de datos, personalice el ajuste de FM con parámetros ajustables, evalúe FM con alta eficiencia e implemente FM como servicios con un solo clic, en una red VPC aislada para proteger los datos de su empresa.
- **Galería de Modelos**: Elija entre una variedad de FM líderes, incluidas las series de modelos Tongyi Qwen, Tongyi Wanxiang y Qwen de código abierto de Alibaba Cloud.

![image](/assets/img/blog/tutorials/alibaba/howWorksModelStudio.png)

## Precios y Especificaciones
Todas las opciones son gratuitas hasta el 15 de Julio del 2024.

![image](/assets/img/blog/tutorials/alibaba/priceModelStudio.png)

## Primer Acercamiento - Paso a Paso

1. Inicia sesión en la consola de [Alibaba Cloud Model Studio](https://bailian.console.alibabacloud.com/?spm=a3c0i.29328889.1985584540.1.29722d2fKhpF0I)

![image](/assets/img/blog/tutorials/alibaba/modelstudio_demo/01.png)

2. Aceptemos los Terminos del Servicio

![image](/assets/img/blog/tutorials/alibaba/modelstudio_demo/02.png)

3. En la pagina de inicio (HomaPage) podremos visualizar el cuadro de texto donde ingresaremos nuestras indicaciones o mejor conocidos como "prompts"

![image](/assets/img/blog/tutorials/alibaba/modelstudio_demo/03.png)

4. Tal y como podemos observar, podemos elegir el modelo con el que queramos chatear, como Qwen-Max, Qwen-Plus, Qwen-Turbo y Qwen1.5-32B-Chat.

![image](/assets/img/blog/tutorials/alibaba/modelstudio_demo/04.png)

5. Interactuemos entonces, en mi caso ingrese el siguiente prompt: "Eres un autor de canciones mexicanas, escribe una canción de banda que hable de amor y se base en una historia real"

![image](/assets/img/blog/tutorials/alibaba/modelstudio_demo/06.png)

Nota: Al dar clic en el boton de **"Activate"** nos aparecera una ventana emergente cuestionando que deseamos continuar usando el servicio de Alibaba Cloud Model Studio, para esto simplemente marquemos el checkbox y demos en el botón de **"Confirm Activation"**:

![image](/assets/img/blog/tutorials/alibaba/modelstudio_demo/05.png)

Como podemos apreciar a continuacion, al parecer el modelo no trabaja o no detecta el lenguaje del Español:

![image](/assets/img/blog/tutorials/alibaba/modelstudio_demo/07.png)

Intentemos de nuevo pero esta vez en Ingles:

![image](/assets/img/blog/tutorials/alibaba/modelstudio_demo/08.png)

**Nota**: La imagen que les muestro anteriormente es en el momento justo donde se encontraba generando la respuesta, pero acto seguido mostro el siguiente error:

![image](/assets/img/blog/tutorials/alibaba/modelstudio_demo/081.png)

Y bueno, parece que solo funciona para algunos idiomas tales Inglés, Japonés, Chino y Coreano (son los que probe). Desde mi punto de vista creo que esta muy bien, solo es cuestion de tiempo para que acepte otros idiomas.

![image](/assets/img/blog/tutorials/alibaba/modelstudio_demo/09.png)


## Conclusión
En resumen, Alibaba Cloud Model Studio es una poderosa herramienta que democratiza el desarrollo de la IA, permitiendo a las empresas innovar rápidamente y aprovechar el poder del aprendizaje automático sin barreras de entrada significativas.

## En el siguiente capítulo...
En el siguiente articulo veremos como obtener una API Key y como integrarlo en un desarrollo, ya veremos si lo haceoms desde .NET o con Amazon Alexa, no se lo pierdan.

Más información: [Alibaba Cloud Model Studio](https://www.alibabacloud.com/en/product/modelstudio?_p_lc=1)

¡Hasta la próxima!