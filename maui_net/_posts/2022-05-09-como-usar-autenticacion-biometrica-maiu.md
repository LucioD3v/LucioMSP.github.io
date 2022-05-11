---
layout: post
title: Implementando la autenticación biométrica en .NET MAUI
description: En este artículo mostraré que tan fácilmente es agregar la autenticación biométrica en .NET MAUI
image: /assets/img/blog/post-headers/maui/Integrate-biometric.png
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
  - biométrica
  - autenticación
lang: es
---

Sin duda alguna la autenticación biométrica se ha convertido cada vez más en una parte integral de las aplicaciones móviles para garantizar que el usuario sea el propietario legítimo del dispositivo que está utilizando. Existen dos maneras de poder autenticarse, unas es a través de Face ID (iOS) y la otra mediante huella digital (Android / iOS), en este caso, en nuestra aplicación .NET MAUI.

El día de hoy veremos como integrar la autenticación biométrica en un proyecto .NET MAUI, asi que comencemos.

### Cómo utilizarlo

Lo primero que se debe de hacer es instalar el complemento mediante el administrador de paquetes en el proyecto de .NET MAUI:

En el proyecto .NET MAUI, instale el paquete NuGet [Plugin.Fingerprint](https://github.com/smstuebe/xamarin-fingerprint). Necesitará la versión 3.0.0-beta.1, que actualmente se encuentra en versión preliminar, así que recuerde marcar "Incluir Versión Preliminar":

![image](/assets/img/blog/tutorials/maui-biometrics/01.png)

### Implementación - Android

Ahora lo que se debe de hacer es establecer la versión del SDK de destino. La versión del SDK de destino debe ser >= 6.0. Por mi parte y si es posible, recomiendo usar siempre la última versión estable del SDK. Puede establecer la versión del SDK de destino en las propiedades del proyecto de Android.

#### Instalar la migración de Android X

Desde la versión 2, el plugin antes mencionado usa Android X. Por ende se debe instalar Xamarin.AndroidX.Migration en nuestro proyecto de Android.

### Solicita el permiso en AndroidManifest.xml

Acto seguido, deberemos de agregar el permiso en el archivo AndroidManifest.xml

~~~bash

<uses-permission android:name="android.permission.USE_FINGERPRINT" />

~~~

![image](/assets/img/blog/tutorials/maui-biometrics/02.png)

Ya para terminar en Android, en el archivo MainActivity.cs añadamos el using correspondiente: 

~~~bash

using Plugin.Fingerprint;

~~~

Posteriormente en el mismo archivo, añadamos el método OnCreate(), en el cual recordemos se ejecuta la lógica de arranque básica de la aplicación que debe ocurrir una sola vez en toda la vida de la actividad. Aqui agregaremos la siguiente linea de código:

~~~bash

CrossFingerprint.SetCurrentActivityResolver(() => this);

~~~

Nuestro archivo quedará de la siguiente manera:

![image](/assets/img/blog/tutorials/maui-biometrics/img02.png)

### Implementación - iOS

En iOS es mas sencillo, solo se debe de agregar el "NSFaceIDUsageDescription" al archivo Info.plist para describir la razón por la que nuestra aplicación usara Face ID. ([ver Documentación](https://developer.apple.com/library/content/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html#//apple_ref/doc/uid/TP40009251-SW75)). De lo contrario, la aplicación se bloqueará cuando inicie una autenticación de Face ID en iOS 11.3+.

~~~bash

<key>NSFaceIDUsageDescription</key>
<string>Need your face to unlock magic things</string>

~~~

Nota: Si tienen alguna duda de como implementar esto, les recomiendo que sigan la guía en GitHub para saber mas sobre cómo configurarlo para su proyecto .NET MAUI. Cabe mencionar que la guía se encuentra actualmente en la rama de soporte de maui, po  r lo que si el enlace no funciona, ya se ha fusionado y puede usar el enlace proporcionado anteriormente.

Ya por último y antes de irnos a modificar nuestro XAML y añadir la funcionalidad principal, en el archivo MauiProgram.cs deberemos de agregar las siguiente lineas:

~~~bash

    builder.Services.AddSingleton<MainPage>();
		builder.Services.AddSingleton(typeof(IFingerprint), CrossFingerprint.Current);

~~~

Quedando de la siguiente manera:

![image](/assets/img/blog/tutorials/maui-biometrics/img021.png)

### XAML

A continuación agreguemos un botón con un controlador de clic (o modifiquemos el que nos creó la solución si el proyecto es nuevo):

~~~bash

<Button 
                Text="Authenticate"
                FontAttributes="Bold"
                SemanticProperties.Hint="Click to authenticate with your fingerprint"
                Clicked="OnBiometricClicked"
                HorizontalOptions="Center" />

~~~

![image](/assets/img/blog/tutorials/maui-biometrics/03.png)

A continuación debemos de añadir el using correspondiente:

~~~bash

using Plugin.Fingerprint.Abstractions;

~~~

Posteriormente 

~~~bash

private readonly IFingerprint fingerprint;

~~~

~~~bash

this.fingerprint = fingerprint;

~~~

![image](/assets/img/blog/tutorials/maui-biometrics/05.png)


Ahora, dentro del controlador de eventos "OnBiometricClicked", en el código subyacente añadamos el siguiente código, el cual cuando haga clic en el botón, se le pedirá que se autentique mediante huella digital:

~~~bash

private async void OnBiometricClicked(object sender, EventArgs e)
	{
		var request = new AuthenticationRequestConfiguration("Validate that you have fingers", "Because without them you will not be able to access");
		var result = await fingerprint.AuthenticateAsync(request);
		if (result.Authenticated)
		{
			await DisplayAlert("Authenticate!", "Access Granted", "OK");
		}
		else
		{
			await DisplayAlert("Unauthenticated", "Access Denied", "OK");
		}
	}

~~~

![image](/assets/img/blog/tutorials/maui-biometrics/04.png)

## Resultado / Salida

| Android |

![image](/assets/img/blog/tutorials/maui-biometrics/06.png)

![image](/assets/img/blog/tutorials/maui-biometrics/07.png)

| iOS |

![image](/assets/img/blog/tutorials/maui-biometrics/08.png)

![image](/assets/img/blog/tutorials/maui-biometrics/09.png)


Como siempre, a continuación proporciono un ejemplo de código en mi [GitHub](https://github.com/LucioMSP/biometricMAUI), mismo que puedes consultar si lo deseas.

## Conclusión

Espero que este pequeño artículo te haya brindado suficiente información para aplicar dicho control en tus aplicaciones .NET MAUI y ver los resultados tanto en Android como en iOS. 

Aprovecho el espacio para invitarte a dejar un comentario si deseas que dé más detalles sobre cualquier cosa dentro de este artículo.

Más información:

- GitHub Xamarin-Fingerprint: [https://github.com/smstuebe/xamarin-fingerprint/tree/maui-support](https://github.com/smstuebe/xamarin-fingerprint/tree/maui-support)

## ¡Happy Coding!