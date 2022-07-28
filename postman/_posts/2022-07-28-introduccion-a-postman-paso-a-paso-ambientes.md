---
layout: post
title: Aprendiendo Postman paso a paso - Ambientes (Environments)
description:
image: /assets/img/blog/post-headers/postman.jpeg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [postman]
tags:
  - postman
keywords:
  - development
  
lang: es
---

Esta es una serie de artículos paso a paso, a continuación aprenderemos sobre las características de los Entornos o Ambientes (Environments) de Postman. Antes de aprender sobre esto, los invito a que lean los artículo anteriores de esta serie para una mejor comprensión:

- [Aprenda Postman paso a paso - Introducción (Día 1)](https://vicenteguzman.com/maui_net/net/2022-04-25-introduccion-a-postman/)
- [Aprenda Postman paso a paso - Encabezados Preestablecidos (Día 2)](https://vicenteguzman.com/postman/2022-04-27-aprendiendo-postman-paso-a-paso-encabezados-preestablecidos/)

Este artículo cubre los siguientes temas:

- Entornos
- Alcance variable
- Crear entornos y variables
- Acceder a las variables de entorno
- Establecer y obtener la variable de entorno del script

## Entornos
Los entornos no son más que el conjunto de variables definidas, las variables se almacenan en forma de pares clave-valor y se utilizan en la solicitud del cartero. Puede crear los entornos como Desarrollo, Puesta en escena, Producción, etc., y definir las variables.

Sintaxis - Para acceder a las variables de entorno.

~~~bash

" {{nombre de la variable}} "

~~~

Cabe señalar que hay un alcance definido para cada variable de entorno:

### Variable Local
Es la variable temporal utilizada para la solicitud o colección en particular, ya no está disponible una vez que se completa la solicitud. Se usa cuando desea anular el valor de las variables para una solicitud en particular.

### Variable Global
Nos permite acceder a los valores de las variables en todo el espacio de trabajo.

### Variable Ambiental o de Entorno
Nos permite acceder a los valores de las variables para diferentes entornos como dev, prod, stage, etc. A la vez, solo un entorno puede estar activo. Es más adecuado para el acceso basado en roles.

### Variable de Colección
Está disponible para las solicitudes de una colección, más adecuado para un solo entorno o un entorno independiente. No se modifica en el caso del medio ambiente.

### Variable de Datos
Proviene de archivos externos como CSV y JSON. Contiene los valores actuales para una solicitud en particular o la colección.

## Creando los Entornos y Variables

A continuación vamos a crear los entornos y las variables, para ello seguiremos los siguientes pasos:

Paso 1

Abra Postman, ya sea la versión web o la aplicación de escritorio y seleccione 'Entornos (Environments)' en el lado izquierdo como se muestra a continuación:

![image](/assets/img/blog/tutorials/postman-environments/Imagen1.png)

A ustedes les puede aparecer diferente, esto seria por que no tendrian entornos, es decir, estaria vacío.

Paso 2

Acto seguido, crearemos un entorno. Para eso, debemos hacer clic en el ícono más o en el enlace inferior que les aparezca 'Crear entorno':

![image](/assets/img/blog/tutorials/postman-environments/Imagen2.png)

Una vez que hacemos clic, se abre la pantalla para crear un entorno en la parte del lado derecho como se muestra a continuación:

![image](/assets/img/blog/tutorials/postman-environments/Imagen3.png)

Paso 3

En este paso, proporcionaremos los valores como se puede ver y hacemos clic en el botón Guardar al final:

![image](/assets/img/blog/tutorials/postman-environments/Imagen4.png)

- Variable: Es el valor utilizado en las solicitudes del cartero.
- Tipo: contiene dos valores predeterminado y secreto. 
El tipo secreto se utiliza para almacenar los datos confidenciales en él y mantiene sus valores enmascarados en la pantalla.
- Valor inicial: este valor se sincroniza cuando trabaja con el equipo en el espacio de trabajo.
- Valor actual: este valor se usa cuando enviamos la solicitud y no está sincronizado. 
Si no hemos fijado el valor actual, automáticamente toma el valor inicial como actual.
- Persist All - reemplaza todos los valores iniciales con valores actuales.
- Restablecer todo: reemplaza todos los valores actuales con los valores iniciales.

![image](/assets/img/blog/tutorials/postman-environments/Imagen5.png)

En la captura de pantalla anterior, cuando hacemos clic en los tres puntos superiores, muestra la opción Establecer como entorno activo, Exportar, Duplicar, Eliminar, etc.

Paso 4

Pasenos a crer dos entornos más, el de Prod y el de Stagging. Una vez realizado lo anterior, podremos ver los susodichos en dos lugares, primero en la pestaña Entornos del lado izquierdo y en el menú desplegable superior del lado derecho. Acto seguido, configuremos el entorno predeterminado como 'Dev', tal y como se puede a continuación:

![image](/assets/img/blog/tutorials/postman-environments/Imagen6.png)

### Acceder a las variables de entorno

Ahora veamos cómo podemos acceder a esas variables de entorno en la solicitud como se indica a continuación:

Paso 1

Hagamos clic en el ícono "+" para crear una solicitud:

![image](/assets/img/blog/tutorials/postman-environments/Imagen7.png)

Paso 2

Esto lo que hará, es que nos abrirá la página de solicitud de creación en el lado derecho, aqui proporcionemos los siguientes datos:

![image](/assets/img/blog/tutorials/postman-environments/Imagen8.png)

En la captura de pantalla anterior, podemos ver la URL que hemos utilizado para la solicitud GET como '{{base_url}}/users/jsgund'. Aquí '{{base_url}}' significa la variable de entorno y cuando hacemos clic en enviar, reemplazará la variable con el valor real como 'https://api.github.com'. En el menú desplegable superior del lado derecho, puede ver el entorno seleccionado para esta solicitud como 'Dev'.

Paso 3

A continuación, si deseas verificar las variables de entorno para 'Dev', hagamos clic en el icono del ojo del lado derecho para ver las variables como se muestra arriba:

![image](/assets/img/blog/tutorials/postman-environments/Imagen9.png)

O simplemente pasemos el mouse sobre la variable de entorno '{{base_url}}', para poder obtener los detalles sobre esa variable:


![image](/assets/img/blog/tutorials/postman-environments/Imagen10.png)

Paso 4

Ahora, simplemente hagamos clic en el botón Enviar (Send) y veamos el resultado:

![image](/assets/img/blog/tutorials/postman-environments/Imagen11.png)

Como pudimos observar, las variables de entorno son fáciles de usar y actualizar en un solo lugar, mismo que usará el valor actualizado para ese entorno.

## Establecer y Obtener la variable de entorno del script

También hay otra forma de configurar o crear la variable de entorno en el script 'Requisito previo (Pre-req)' y 'Prueba (Test)':

La sintaxis para Set sería:

~~~bash

pm.environment.set("base_url", "https://api.github.com");

~~~

La sintaxis para Get:

~~~bash

pm.entorno.get("variable_clave");

~~~

En el código anterior, podemos ver el objeto 'pm', al usar este se puede acceder y manipular las variables en Postman usando la API 'pm'.

## Conclusión

En este artículo, aprendimos sobre el entorno y las variables, el alcance de las variables y la creación y el uso en la solicitud. Si tiene alguna sugerencia o consulta sobre este artículo, por favor póngase en contacto conmigo.

Estén atentos para aprender cosas nuevas sobre Postman.

¡Hasta la próxima!