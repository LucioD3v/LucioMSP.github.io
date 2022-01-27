---
layout: post
title: What’s New in .NET 6
description: In this article we will see the news that the arrival of .NET 6 brings
image: /assets/img/blog/post-headers/maui/xamarin-forms-maui.jpg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [maui]
tags:
  - net
keywords:
  - net
  - development
  
lang: en
---

![image](/assets/img/blog/tutorials/whatsnewNET6/logoNET.png)

5 years ago (to be more precise, on June 27, 2016), Microsoft released one of the most anticipated news by many and questioned by others. And it was announcing its move to Open Source with the .NET Framework launching .NET Core 1.

Subsequently, Microsoft released .NET Core 3.1 as a stable and LTS version for use in applications in production environments. In November of last year the version of .NET Core was released under the name .NET 5.0.

Microsoft named this version .NET 5.0 instead of .NET Core 4.0 for two simple reasons:

- Avoid confusion with .NET Framework 4.x.
- The .NET project is the future of the platform.

So the word "Core" would be no longer used to simplify the name. Although in the Microsoft Development blog, they tell us that if we want we can continue calling it .NET Core.

With this and to be honest, I believe that Microsoft seeks every day to facilitate software programming in Windows, improving its .NET framework, which is one of the most important components in its operating system. And it is that if we remember, a few months after the arrival of version 5.0 of .NET, Microsoft announced the arrival of the first 'preview' of .NET 6.0, where the releases that Microsoft has made this year, we indicates that we are getting closer and closer to a definitive version (intended to unify the .NET Framework and .NET Core platforms).

## NET 5 

As we already know, the .NET 5.0 version has much more application and platform support than .NET Core, and the .NET Framework also has great improvements compared to .NET Core 3.1 in terms of security, performance, and stability.

Over the past year many people argued that .NET 5 was Microsoft's last step in its quest to rebuild .NET as a cross-platform open source project. However, .NET 5 is the first step in a new Microsoft release scheme. For the near future, Microsoft promises a new version of .NET annually, which will be released every November, as we can see below:

![image](/assets/img/blog/tutorials/whatsnewNET6/netSchedule.png)

.NET release schedule

Image from: [visualstudiomagazine](https://visualstudiomagazine.com/articles/2019/06/12/net-core-3-preview-6.aspx) 

## .NET 6

With the arrival of .NET 6 in preview, we can see impressive features and improvements over its predecessor (.NET 5). And it is that in this new installment new features that were not present in .NET 5 are focused, such as a next generation "Xamarin". Which reduces the barriers between desktop and native mobile development, also includes improvements in the cloud, which means better integration of the Windows user interface SDKs.
Month by month Microsoft has been taking previews with the new changes and updates. These previews are being discussed from now until the launch of its manufacture, which will be supported for 3 years.

As I mentioned before, Microsoft comes with a lot of traction with a very ambitious plan on changes, challenges and new features with the current development of .NET 6. For this reason in this article we will focus on some of the new features that are ahead of us. in .NET 6 Preview.

## .NET Multi-Platform App UI (MAUI)

![image](/assets/img/blog/tutorials/whatsnewNET6/netMAUI.png)

Image from: [devblogs](https://devblogs.microsoft.com/dotnet/announcing-net-maui-preview-4/) 

For those who did not know, Xamarin.Forms is an open source cross-platform framework for creating mobile applications on iOS, Android and Windows with .NET from a single code base which is shared. It was originally developed by the Mono project engineers and Microsoft acquired it in February 2016.

Xamarin.Forms is a Model-View-ViewModel (MVVM) development platform, which has built-in pages, mobile app layouts, and controls that allow us to create apps with a single, highly extensible API. In addition, it allows us to subclass and customize controls, layouts, pages and cells to make our application perfect.

.NET 6 uses the .NET cross-platform application user interface. It is a modern user interface toolkit based on Xamarin. But it has improvements and new features as part of the .NET 6 unification. It gives us the ability to create applications that can be deployed on multiple devices using a single project and a single code base with minimal overhead.

By using the .NET cross-platform application user interface, we developers can deliver consistent application experiences across multiple platforms and devices. Mobile and desktop apps can use a single shared code base to target Android, iOS, macOS, and Windows operating systems.

The mobile cross-platform and cross-platform support of .NET 6 integrates and extends the Xamarin.Forms toolkit. It also extends the Xamarin.Essentials libraries to enhance cross-platform user interface controls. With MAUI, we can use various device capabilities. This includes device sensors, photos, contacts, authentication, and secure storage.

Building applications with .NET 6 is a breeze, as it comes with sample mobile projects and installation instructions. It also includes a new C # Hot Reload feature and XAML support which allows for a more streamlined development experience. Changes and improvements in MAUI are focused on improving application performance, user experience, control, and increasing development speed. Using UI plugins like ComponetOne in MAUI applications will speed up the development process. It will also improve the user experience of the application in addition to what the .NET MAUI already has.

## Blazor Desktop

![image](/assets/img/blog/tutorials/whatsnewNET6/blazorDesktop.png)

Blazor has become a very smart way to build .NET web applications. This is due to its fluidity and ease of integration with user interface libraries such as ComponentOne. This makes the application development life cycle more efficient.

Blazor support for .NET was the first on the server. Then it was in the browser with WebAssembly. Now, .NET 6 allows writing desktop applications in Blazor. Blazor Desktop allows you to create hybrid client applications, combining the native and web user interface in a native client application. Blazor Desktop is targeted at web developers who want to deliver rich, offline client experiences to application users. These experiences can also be enhanced by using user interface libraries like ComponentOne.

The .NET 6 team emphasized that they initially built Blazor Desktop for .NET applications. But there is no technical reason why Blazor can be used in a desktop application built with another application stack. For example, we could use Swift.

Blazor Desktop sits on top of the new .NET application UI with cross-platform support. It builds on that UI stack for a native app container and native controls with excellent performance.

## WPF support in Arm64

Windows Presentation Foundation (WPF) is a resolution independent user interface framework. It uses a vector-based rendering engine built to take advantage of modern graphics hardware.

Provides a complete set of application development features: Extensible Application Markup Language (XAML), data binding, 2D and 3D graphics, animation, templates, documents, media, text, and typography. WPF is part of .NET, so we can easily incorporate it with other .NET API elements.

In .NET 6, Arm64 is very important due to its significant performance improvements compared to .NET 5. Support for Windows Forms and Windows Presentation Framework (WFP) are also introduced and are out of the box.

## Performance improvements

We can also anticipate performance improvements for .NET 6. According to the official Microsoft blog, Microsoft is starting a new project called Rapid Internal Loop. The first part of the project is to make the build run significantly faster with a set of performance-related projects.

The second part is creating new systems that will allow you to skip the construction phase entirely. Microsoft stated that they envisioned implementing the innovation from the Xamarin team with the XAML Hot Reload feature to become a general .NET feature.

## Summary:

As you can understand, the .NET 6 framework is not going to be a final version, but a transition to achieve the goal that Microsoft has in mind of creating a universal development platform for Windows. With the arrival of .NET 7 it is believed that this goal will be achieved. And well, in the coming months we will be able to have more information about this final version.

Important Data: With the arrival of .NET 6, the C # language will reach its version 10.0

Undoubtedly .NET 6 Preview is a little breath of fresh air about what is new that the Microsoft .NET development team brings us and the safest thing (I think) that the following versions will come with many more features and improvements.

If you want to try the preview, it can be downloaded from: dotnet.microsoft.com

¡Happy Coding!
