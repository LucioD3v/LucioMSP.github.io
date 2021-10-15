---
layout: post
title: Correción de pantalla blanca en Android al usar NavigationPage (Xamarin.Forms)
description: Conoce todo sobre .NET MAUI, la evolución de Xamarin.Forms. - Primer articulo -
image: /assets/img/blog/post-headers/xamarin/xamarinBanner.jpg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [maui]
tags:
  - maui
  - net
keywords:
  - maui
  - net
lang: es
---

Si experimenta una pantalla en blanco al presionar Navegación o Pila modal en Android, siga leyendo.

No estoy seguro de si esto es un error en Xamarin Forms o no, pero supongo que lo es, porque solo se presenta en ciertos escenarios, y no siempre.

## ¿Qué está pasando, cómo nota este error?
Tienes una NavigationPage. Está enviando una nueva página a la pila de navegación y la página no se está procesando, solo se muestra una pantalla en blanco.

Si está rotando el dispositivo, la página se está renderizando bien.

Mi entorno es:
Xamarin.Forms: 4.8 up to 5.0
Device: Samsung Galaxy A12
Visual Studio 2019 Professional with Xamarin.Android SDK 11.4.0.5

## Solución
Siempre invoque los métodos de INavigation en el subproceso principal de la aplicación. Los cambios en la interfaz de usuario deben ir siempre en el hilo de la interfaz de usuario de la aplicación.

Cree una clase que envuelva la INavigation presentada por sus Vistas. Es útil almacenar una referencia en esta clase a la instancia de INavigation de la página principal actual de las aplicaciones, así que intente crear su código para suministrar la instancia de INavigation real cada vez que esta clase cuando la página principal de la aplicación esté configurada.

~~~bash

public class NavigationDispatcher : INavigation
{
    private INavigation _navigation;
 
    public IReadOnlyList<Page> ModalStack => _navigation?.ModalStack;
 
    public IReadOnlyList<Page> NavigationStack => _navigation?.NavigationStack;
 
    private void SetNavigation(INavigation navigation)
    {
        _navigation = navigation;
    }
 
    public void InsertPageBefore(Page page, Page before)
    {
        _ = Xamarin.Essentials.MainThread.InvokeOnMainThreadAsync(() =>
          {
              _navigation.InsertPageBefore(page, before);
          });
    }
 
    public Task<Page> PopAsync()
    {
        return Xamarin.Essentials.MainThread.InvokeOnMainThreadAsync(async () =>
        {
            return await _navigation.PopAsync();
        });
    }
 
    public Task<Page> PopAsync(bool animated)
    {
        return Xamarin.Essentials.MainThread.InvokeOnMainThreadAsync(async () =>
        {
            return await _navigation.PopAsync(animated);
        });
    }
 
    public Task<Page> PopModalAsync()
    {
        return Xamarin.Essentials.MainThread.InvokeOnMainThreadAsync(async () =>
        {
            return await _navigation.PopModalAsync();
        });
    }
 
    public Task<Page> PopModalAsync(bool animated)
    {
        return Xamarin.Essentials.MainThread.InvokeOnMainThreadAsync(async () =>
        {
            return await _navigation.PopModalAsync(animated);
        });
    }
 
    public Task PopToRootAsync()
    {
        return Xamarin.Essentials.MainThread.InvokeOnMainThreadAsync(async () =>
        {
            await _navigation.PopToRootAsync();
        });
    }
 
    public Task PopToRootAsync(bool animated)
    {
        return Xamarin.Essentials.MainThread.InvokeOnMainThreadAsync(async () =>
        {
            await _navigation.PopToRootAsync(animated);
        });
    }
 
    public Task PushAsync(Page page)
    {
        return Xamarin.Essentials.MainThread.InvokeOnMainThreadAsync(async () =>
        {
            await _navigation.PushAsync(page);
        });
    }
 
    public Task PushAsync(Page page, bool animated)
    {
        return Xamarin.Essentials.MainThread.InvokeOnMainThreadAsync(async () =>
        {
            await _navigation.PushAsync(page, animated);
        });
    }
 
    public Task PushModalAsync(Page page)
    {
        return Xamarin.Essentials.MainThread.InvokeOnMainThreadAsync(async () =>
        {
            await _navigation.PushModalAsync(page);
        });
    }
 
    public Task PushModalAsync(Page page, bool animated)
    {
        return Xamarin.Essentials.MainThread.InvokeOnMainThreadAsync(async () =>
        {
            await _navigation.PushModalAsync(page, animated);
        });
    }
 
    public void RemovePage(Page page)
    {
        _ = Xamarin.Essentials.MainThread.InvokeOnMainThreadAsync(() =>
          {
              _navigation.RemovePage(page);
          });
    }
}

~~~

## Observaciones
Considere una verificación del hilo actual en el cuerpo de los métodos.
Si se están ejecutando en el hilo principal, no necesitará volver a cambiar al hilo principal.
