---
layout: post
title: Correción de pantalla blanca en Android al usar NavigationPage (Xamarin.Forms)
description: 
image: /assets/img/blog/post-headers/xamarin/xamarinBanner.jpg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [xamarin.forms]
tags:
  - xamarin
  - xamarin.forms
keywords:
  - maui
  - net
lang: es
---

Este artículo es una traducción al español del blog de banditoth (con un toque personal), en donde se demuestra como corregir el problema reportado en el GitHub de [Xamarin.Forms](https://github.com/xamarin/Xamarin.Forms/issues/11993).

---------------------------------------------------------------------

## Escenario

Si te encuentras experimentando con una pantalla en blanco al presionar Navigation o un Modal Stack en Android, sigue leyendo, ya que este artículo te ayudará a resolverlo.

La verdad no estoy seguro de si esto es un error en Xamarin.Forms o no, pero supongo que lo es, porque solo se presenta en ciertos escenarios, y no siempre.

## ¿Qué está pasando, cómo nota este error?
Tienes una NavigationPage, la cúal está enviando una nueva página a la pila de navegación y la página no se está procesando, solo se muestra una pantalla en blanco. Ahora bien, si rotas el dispositivo, la página se renderizará correctamente.

Mi entorno es:
Xamarin.Forms: 4.8 hasta 5.0
Dispositivo: Samsung Galaxy A12 (probado igual en un Samsuns S20+)
Visual Studio 2019 Professional con Xamarin.Android SDK 11.4.0.5

## Solución
Siempre se deben de invocar los métodos de INavigation en el subproceso principal de la aplicación, ya que los cambios en la interfaz de usuario deben ir siempre en el hilo de la interfaz de usuario de la aplicación.

Para esto, solo se debe de crear una clase que envuelva la INavigation presentada por sus Vistas. Es útil almacenar una referencia en esta clase a la instancia de INavigation de la página principal actual de las aplicaciones, así que intente crear su código para suministrar la instancia de INavigation cada vez a esta clase cuando la página principal de la aplicación esté configurada.

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
Considere realizar una verificación del hilo actual en el cuerpo de los métodos, puesto que si se están ejecutando en el hilo principal, no se necesitará volver a cambiar al hilo principal.

Post Original: [banditoth.hu](https://www.banditoth.hu/2021/10/06/xamarin-forms-white-screen-between-page-push-and-pop-solved/)