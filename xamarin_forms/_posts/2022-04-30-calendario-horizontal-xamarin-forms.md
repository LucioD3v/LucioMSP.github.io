---
layout: post
title: Implementando un Calendario Horizontal en Xamarin.Forms
description: En este artículo mostraré que tan fácilmente es agregar un control de calendario de manera horizontal a nuestras aplicaciones de Xamarin.Forms
image: /assets/img/blog/post-headers/xamarin/shadow.png
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [xamarin.forms]
tags:
  - calendario
  - calendar
  - control
  - xamarin
keywords:
  - ios
  - android
  - xamarin
  - maui
  
lang: es
---

Horizontal Calendar Control: es un complemento multiplataforma para Xamarin.Forms que le permite mostrar un calendario de una sola fila en su aplicación.

![image](/assets/img/blog/tutorials/xamarin-horizontal-calendar/img01.png)


### Cómo utilizarlo

Lo primero que se debe de hacer es instalar el complemente mediante el administrador de paquetes:

IMAGEN

### Package Manager

![image](/assets/img/blog/tutorials/xamarin-horizontal-calendar/img00.png)


### Ejemplo de implementación

Espacio de Nombres (Namespace):

~~~bash

xmlns:views="clr-namespace:HorizontalCalendar.Views;assembly=HorizontalCalendar"

~~~

Escriba el siguiente código en su página XAML.

~~~bash

 <views:HorizontalCalendarControl LeftRightArrowColor="White"   />

~~~

### Personalización de la interfaz de usuario

Propiedad de personalización de la interfaz de usuario
HeaderBackgroundColor: se utiliza para establecer el color de fondo del encabezado.
HeaderTextColor: se utiliza para establecer el color del texto del encabezado.
LeftRightArrowColor: se utiliza para establecer el color de la flecha izquierda y derecha.
SelectedDateTextColor: se utiliza para establecer el color del texto de la fecha seleccionada.
SelectedDateBackGroundColor: se utiliza para establecer el color de fondo del texto de la fecha seleccionada.


Cómo mostrar la fecha seleccionada
Escriba el siguiente código para obtener la fecha seleccionada.

Y listo, ¡eso es todo! Ahora ya podemos hacer uso del Horizontal Control.


## Resultado / Salida

| iOS |

![image](/assets/img/blog/tutorials/xamarin_sombras/resultadoAntes.png)

| Android |

![image](/assets/img/blog/tutorials/xamarin_sombras/resultadoDespues.png)

¡Felicidades! Ahora ya sabes cómo usar el control de Horizontal Calendar.

## Conclusión

Espero que este pequeño artículo te haya brindado suficiente información para aplicar dicho control em tus aplicaciones de Xamarin.Forms y ver los resultados tanto en Android como en iOS. 

Aprovecho el espacio para invitarte a dejar un comentario si deseas que dé más detalles sobre cualquier cosa dentro de este artículo.

Más información: 

- NuGet: [https://www.nuget.org/packages/HorizontalCalendarControl/1.0.2](https://www.nuget.org/packages/HorizontalCalendarControl/1.0.2)

## Happy Coding!