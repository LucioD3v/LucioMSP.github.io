---
layout: post
title: Implementando un Calendario Horizontal en Xamarin.Forms
description: En este artículo mostraré que tan fácilmente es agregar un control de calendario de manera horizontal a nuestras aplicaciones de Xamarin.Forms
image: /assets/img/blog/tutorials/xamarin-horizontal-calendar/img01.png
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

Horizontal Calendar Control es un complemento multiplataforma para Xamarin.Forms que nos permite mostrar un calendario de una sola fila en nuestras aplicaciones.

![image](/assets/img/blog/tutorials/xamarin-horizontal-calendar/img01.png)

### Cómo utilizarlo

Lo primero que se debe de hacer es instalar el complemento mediante el administrador de paquetes solamente en el proyecto de Xamarin.Forms:

![image](/assets/img/blog/tutorials/xamarin-horizontal-calendar/img02.png)

Ya si se quiere hacer mediante la consola del Package Manager:

Install-Package HorizontalCalendarControl -Version 1.0.2

![image](/assets/img/blog/tutorials/xamarin-horizontal-calendar/img03.png)

### Ejemplo de implementación

Ahora lo que se debe de hacer es escribir (agregar) el espacio de nombres (namespace) en la vista que vayamos a utilizar el control:

~~~bash

xmlns:views="clr-namespace:HorizontalCalendar.Views;assembly=HorizontalCalendar"

~~~

Posteriomente habrá  que escribir el siguiente código en la página XAML donde lo vayamos a ocupar:

~~~bash

  <StackLayout >
      <views:HorizontalCalendarControl  x:Name="calendarControl" />
  </StackLayout>

~~~

## Personalización de la Interfaz de Usuario (UI)

### Propiedades

- HeaderBackgroundColor: se utiliza para establecer el color de fondo del encabezado.
- HeaderTextColor: se utiliza para establecer el color del texto del encabezado.
- LeftRightArrowColor: se utiliza para establecer el color de la flecha izquierda y derecha.
- SelectedDateTextColor: se utiliza para establecer el color del texto de la fecha seleccionada.
- SelectedDateBackGroundColor: se utiliza para establecer el color de fondo del texto de la fecha seleccionada.

~~~bash

  <views:HorizontalCalendarControl 
      HeaderBackgroundColor="LightBlue"
      HeaderTextColor="Black"
      SelectedDateTextColor="LightBlue" 
      SelectedDateBackGroundColor="Black" 
      LeftRightArrowColor="Black"   />

~~~

### Cómo mostrar la fecha seleccionada
Para poder obtener la fecha seleccionada, deberemos de escribir el siguiente código:

~~~bash

  <Label Text="{Binding Source={x:Reference calendarControl},Path=SelectedDate}" />
  <views:HorizontalCalendarControl  x:Name="calendarControl"/>

~~~

### Cómo obtener la fecha seleccionada

Para obtener la fecha seleccionada deberemos de usar este comando: SelectedDateCommand

### XAML

~~~bash

<views:HorizontalCalendarControl SelectedDateCommand="{Binding SelectedDateCommand}" x:Name="calendarControl"  />

~~~

### Code Behind (Código)

~~~bash

private DateTime _selectedDate;
public DateTime SelectedDate
{
   get => _selectedDate;
   set => SetProperty(ref _selectedDate, value);
}
 
public ICommand SelectedDateCommand => new Command<DateTime>((selectedDate) =>
{
     SelectedDate = selectedDate; 
});

~~~

Y listo, ¡eso es todo! Ahora ya podemos hacer uso del Horizontal Calendar Control.

## Resultado / Salida

| Android |

![image](/assets/img/blog/tutorials/xamarin-horizontal-calendar/img04.png)

| iOS |

![image](/assets/img/blog/tutorials/xamarin-horizontal-calendar/img05.png)

## Conclusión

Espero que este pequeño artículo te haya brindado suficiente información para aplicar dicho control em tus aplicaciones de Xamarin.Forms y ver los resultados tanto en Android como en iOS. 

Aprovecho el espacio para invitarte a dejar un comentario si deseas que dé más detalles sobre cualquier cosa dentro de este artículo.

Más información:

- NuGet: [https://www.nuget.org/packages/HorizontalCalendarControl/1.0.2](https://www.nuget.org/packages/HorizontalCalendarControl/1.0.2)

## ¡Happy Coding!