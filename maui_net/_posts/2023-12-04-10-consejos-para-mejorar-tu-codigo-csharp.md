---
layout: post
title: 10 consejos para mejorar tu código en C#
description: En este artículo veremos 10 ejemplos de buenas prácticas para escribir código en C#
image: /assets/img/blog/post-headers/csharp/csharp.png
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [maui]
tags:
  - csharp
  - código
keywords:
  - csharp
  - net
  - code
lang: es
---

Sin duda alguna como programador el tirar (escribir) código limpio, conciso y legible es una habilidad esencial que requiere cualquier desarrollador, ya sea de C# o no. Cabe destacar que si uno cuenta con un código limpio, este es más fácil de entender, mantener y depurar. Es por ello que a continuación les quiero compartir 10 consejos para escribir de una mejor manera código en C#:


## 1. Nombres Descriptivos:
Utiliza nombres descriptivos para variables, métodos y clases para mejorar la legibilidad.

~~~bash

// Incorrecto
int x = 5;

// Correcto
int edadUsuario = 5;

~~~

## 2. Uso de Propiedades:
Utiliza propiedades en lugar de campos públicos para controlar el acceso y posibilitar futuras modificaciones.

~~~bash

// Incorrecto
public int edad;

// Correcto
public int Edad { get; set; }


~~~

## 3. Manejo de Excepciones:
Gestiona las excepciones de manera adecuada para mejorar la robustez del código.


~~~bash

// Incorrecto
try
{
    // Código propenso a excepciones
}
catch (Exception ex)
{
    // Manejo genérico de excepciones
}

// Correcto
try
{
    // Código propenso a excepciones
}
catch (SpecificException ex)
{
    // Manejo específico de excepciones
}


~~~

## 4. Uso de 'var' de manera Moderada:
Utiliza var con moderación y preferiblemente en casos donde el tipo es obvio.

~~~bash

// Incorrecto
List<string> nombres = new List<string>();

// Correcto
var nombres = new List<string>();

~~~

## 5. Implementación de IDisposable:
Implementa la interfaz IDisposable para liberar recursos no administrados.

~~~bash

public class MiClase : IDisposable
{
    private bool disposed = false;

    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    protected virtual void Dispose(bool disposing)
    {
        if (!disposed)
        {
            if (disposing)
            {
                // Liberar recursos administrados
            }

            // Liberar recursos no administrados

            disposed = true;
        }
    }

    ~MiClase()
    {
        Dispose(false);
    }
}

~~~

## 6. Uso de Expresiones Lambda:
Utiliza expresiones lambda para mejorar la concisión del código.

~~~bash

// Incorrecto
lista.Where(delegate(int x) { return x > 5; });

// Correcto
lista.Where(x => x > 5);

~~~

## 7. Uso de Clases Estáticas:
Utiliza clases estáticas para métodos que no dependan del estado de una instancia.

~~~bash

// Incorrecto
public class Utilidades
{
    public int Sumar(int a, int b)
    {
        return a + b;
    }
}

// Correcto
public static class Utilidades
{
    public static int Sumar(int a, int b)
    {
        return a + b;
    }
}

~~~

## 8. Documentación XML:
Agrega documentación XML para explicar la funcionalidad de tus clases y métodos.

~~~bash

/// <summary>
/// Clase que representa a un usuario.
/// </summary>
public class Usuario
{
    /// <summary>
    /// Obtiene o establece el nombre del usuario.
    /// </summary>
    public string Nombre { get; set; }
}

~~~

## 9. Uso de 'readonly':
Utiliza la palabra clave readonly para campos que no deben ser modificados después de la inicialización.

~~~bash

public class MiClase
{
    private readonly int valorInicial = 10;

    public int ObtenerValor()
    {
        return valorInicial;
    }
}

~~~

## 10. Evitar Métodos Largos:
Divide métodos largos en funciones más pequeñas para mejorar la claridad y mantenibilidad del código.

~~~bash

// Incorrecto
public void ProcesarDatos()
{
    // Código extenso y difícil de entender
}

// Correcto
public void ProcesarDatos()
{
    ProcesarParte1();
    ProcesarParte2();
    // ...
}

private void ProcesarParte1()
{
    // Código específico de la parte 1
}

private void ProcesarParte2()
{
    // Código específico de la parte 2
}

~~~

Estos ejemplos representan solo algunas de las muchas prácticas recomendadas al escribir código en C#. Adaptarlas a las necesidades específicas de nuestros proyectos puede mejorar aún más la calidad y mantenibilidad del código.

Espero que este pequeño artículo te haya brindado suficiente información para aplicar dichas mejoras en nuestras aplicaciones desarroladas en C#.

Aprovecho el espacio para invitarte a dejar un comentario si deseas que dé más detalles sobre cualquier cosa dentro de este artículo.


## ¡Happy Coding!