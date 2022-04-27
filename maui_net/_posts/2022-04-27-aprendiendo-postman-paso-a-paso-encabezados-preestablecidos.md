---
layout: post
title: Aprendiendo Postman paso a paso - encabezados preestablecidos
description:
image: /assets/img/blog/post-headers/postman.jpeg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [net]
tags:
  - net
  - c#
keywords:
  - net
  - c#
  - development
  
lang: es
---

Esta es una serie de artículos paso a paso, a continuación aprenderemos sobre las características de los encabezados preestablecidos de Postman. Antes de aprender sobre los encabezados preestablecidos, los invito a que lean el artículo anterior de esta serie para una mejor comprensión:

[Aprenda Postman paso a paso - Introducción (Día 1)](https://vicenteguzman.com/maui_net/net/2022-04-25-introduccion-a-postman/)

Este artículo cubre los siguientes temas:

- Encabezados preestablecidos
- Adición de encabezados preestablecidos
- Uso de encabezados preestablecidos

## Encabezados preestablecidos
Cuando desea interactuar con una API, se requieren algunos encabezados cada vez que realiza una solicitud. Los encabezados incluyen nombre de usuario, contraseña, clave de API, autorización, etc., pero cuando trabaja con la aplicación, se configura automáticamente y envía la solicitud. En caso de acceder directamente a la API, debe pasar esos encabezados cada vez que necesite realizar una solicitud.

En cartero, cuando realiza una nueva solicitud, debe completar todos los encabezados nuevamente, para ahorrar tiempo. Preestablecidos o Encabezados preestablecidos entran en escena para preservar la configuración de los encabezados para usar en futuras solicitudes.

![image](/assets/img/blog/tutorials/intro-postman/01.png)

Los ajustes preestablecidos se encuentran debajo de la sección de encabezados cuando solicita la captura de pantalla anterior.

### Adición de encabezados preestablecidos
Veamos cómo agregar los encabezados preestablecidos, siguiendo los pasos a continuación:

Paso 1

Abra el cartero, cree una nueva solicitud y haga clic en los encabezados, seleccione el valor 'Administrar ajustes preestablecidos' del menú desplegable 'Preajustes' como se muestra a continuación:

![image](/assets/img/blog/tutorials/intro-postman/04.png)

Paso 2

Una vez que haga clic en 'Administrar ajustes preestablecidos', se abrirá la ventana emergente como se muestra a continuación:

![image](/assets/img/blog/tutorials/intro-postman/05.png)

En esta ventana emergente, puede administrar su grupo de encabezados preestablecidos, como agregar, actualizar o eliminar el grupo. El grupo contiene los pares clave-valor del encabezado.

Paso 3

A continuación, haga clic en el botón 'Agregar' y se abre otra ventana emergente para crear el grupo de encabezado preestablecido como se muestra a continuación:

![image](/assets/img/blog/tutorials/intro-postman/05.png)

Contiene el nombre del encabezado preestablecido, la clave, el valor, la descripción que se debe completar y la funcionalidad de edición masiva.

Paso 4

A continuación, complete los detalles requeridos para el grupo de encabezados preestablecidos y haga clic en el botón 'Agregar' como se muestra a continuación:

![image](/assets/img/blog/tutorials/intro-postman/05.png)

Paso 5

Una vez que hizo clic en el botón 'Agregar', agrega ese grupo y verá la lista de grupos a continuación:

![image](/assets/img/blog/tutorials/intro-postman/05.png)

En la ventana emergente después del botón 'Agregar', verá el grupo 'GET-Headers' agregado recientemente. Aquí puede administrar los grupos como 'Agregar', 'Actualizar' y 'Eliminar'.

Para la funcionalidad de actualización, simplemente haga clic en el nombre del grupo y verá una ventana emergente como la siguiente:

![image](/assets/img/blog/tutorials/intro-postman/05.png)


Para la funcionalidad de eliminación, simplemente haga clic en el icono de eliminación y le dará un mensaje de advertencia antes de eliminar ese grupo como se muestra a continuación:

![image](/assets/img/blog/tutorials/intro-postman/05.png)


Espero que comprenda cómo agregar o administrar el grupo de encabezado preestablecido.

Uso de encabezados preestablecidos
En la sección anterior, aprendimos cómo agregar el grupo preestablecido, veamos cómo usarlo en la solicitud de la siguiente manera:

Paso 1

Cree una nueva solicitud, vaya a la pestaña de encabezados y haga clic en el menú desplegable 'Preajustes' como se muestra a continuación:

![image](/assets/img/blog/tutorials/intro-postman/05.png)

En la captura de pantalla anterior, puede ver que el grupo agregado recientemente está junto a 'Administrar ajustes preestablecidos', que es 'GET-Headers'.

Paso 2

A continuación, haga clic en el grupo agregado recientemente que es 'GET-Headers' y se agrega a los encabezados de la siguiente manera:

![image](/assets/img/blog/tutorials/intro-postman/05.png)

En la pestaña de encabezados, puede ver los encabezados agregados 'API-Key' y 'User-Name' del grupo que hemos creado, que es 'GET-Headers'. No es que lo hayamos seleccionado de los ajustes preestablecidos, por lo que no es editable, podemos actualizar ese valor aquí.

## Conclusión

En este artículo, aprendimos sobre ajustes preestablecidos, encabezados y cómo agregarlos y usarlos en una solicitud. Si tiene alguna sugerencia o consulta sobre este artículo, por favor póngase en contacto conmigo.

Estén atentos para aprender cosas nuevas sobre Postman…....

