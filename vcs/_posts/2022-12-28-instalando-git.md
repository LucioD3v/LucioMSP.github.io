---
layout: post
title: Instalación de Git
description: En este artículo conoceremos las diferentes manera de instalar Git.
image: /assets/img/blog/post-headers/vcs/gitInstall.jpg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [vcs]
tags:
  - git
  - github
  - 14díasdeGit
keywords:
  - github
  - git
  - vcs
  - 14díasdeGit
lang: es
---

Y bueno, hasta ahora en lo que va de los 14 días de viaje de aprendizaje de Git, hemos visto y profundizado en:

- [¿Qué es el control de versiones?](https://vicenteguzman.com/vcs/2022-11-02-que-es-vcs/)
- [¿Qué es Git?](https://vicenteguzman.com/vcs/2022-11-03-que-es-git/)

Ahora es el momento de ponerse manos a la obra con Git e instalar la herramienta en nuestros equipos (computadoras).

## Instalar Git en Windows

Git es una herramienta que se puede instalar en cualquier sistema operativo, ya sea macOS, Windows o Linux. A continuación nos centraremos en los métodos de instalación de Windows.

- Lo primero que debemos de hacer es dirigirnos a [https://git-scm.com/downloads](https://git-scm.com/downloads) y descargar la última versión del cliente.
- Una vez que se haya descargado el archivo correcto, hacemos doble clic en él para iniciar la instalación.

Cabe señalar que la instalación se realiza a través de un asistente, por lo cual se nos harán algunas preguntas básicas:

- Aceptar la licencia
- Ubicación de instalación

### Componentes
Y luego se nos preguntará qué componentes podemos instalar. Los valores predeterminados generalmente están bien para comenzar con Git. Es posible que desee seleccionar la opción para instalar un icono en su escritorio y configurarlo para buscar actualizaciones diariamente, tal y como podemos ver a continuación:

![image](/assets/img/blog/tutorials/install-git/01.jpg)

El otro componente opcional que quizás desee considerar es "Agregar un perfil de Git Bash a la terminal de Windows". Esto puede ser útil más adelante, especialmente si planea usar Visual Studio Code u otro editor que tenga una ventana de terminal integrada.

Carpeta del menú Inicio
Puede dejar la siguiente pantalla en su configuración predeterminada.

Editor predeterminado
Cuando llega a elegir el editor predeterminado utilizado por Git, tiene la opción de seleccionar de una lista de editores. El valor predeterminado es Vim, sin embargo, sugeriría elegir uno con el que esté más familiarizado.

Nombre inicial de la sucursal
Cuando crea un nuevo repositorio, por defecto, Git llamará a esa primera rama "maestro". Puede confirmarlo para que use otro nombre. Recomiendo configurar esto en "principal".

![image](/assets/img/blog/tutorials/install-git/02.jpg)

entorno de RUTA
Cuando usa una herramienta dentro de la línea de comando sin especificar la ruta de ubicación completa, debe configurarla para que Windows sepa dónde está la herramienta. Recomiendo usar la opción predeterminada aquí para configurar los ajustes de la RUTA.

Ejecutable SSH
Prefiero dejar esta opción como está eligiendo OpenSSH.

Convenciones de final de línea
Nuevamente les dejo esto por defecto.

Emulador de terminal para Git Bash
Esta es otra configuración que es mejor dejar en la opción MinTTY predeterminada. Es la opción más moderna.

Comportamiento predeterminado
Es mejor dejar esta opción en "Predeterminado (avance rápido o fusión)". La mayoría de los tutoriales que seguirá asumirán que está utilizando esta configuración. Y hasta que te familiarices con Git y su funcionamiento, es la mejor opción.

Ayudante de credenciales Git
Cuando se trabaja con repositorios Git externos, se recomienda utilizar la autenticación HTTPS multifactor. Es mejor dejar la opción predeterminada utilizando el Git Credential Manager integrado.

Opciones adicionales
Lo mejor es ir con los valores predeterminados aquí, a menos que tenga alguna otra necesidad de configurarlos.

Opciones experimentales
Tiendo a no instalar ninguna opción experimental, pero de nuevo, si tienes una necesidad o quieres probarlas, eso es algo que debes decidir.

El proceso de instalación debería comenzar ahora.

![image](/assets/img/blog/tutorials/install-git/03.jpg)

## Instalar Git con el Administrador de paquetes de Windows

Windows Package Manager (winget) es un administrador de paquetes de código abierto desarrollado y creado por Microsoft. Puede ayudarlo a instalar, administrar y actualizar el software en sus escritorios de Windows.

Si tiene instalado el Administrador de paquetes de Windows en su máquina, puede usar el siguiente comando para instalar Git:

```bash

winget install git.git

```
## Instalar Git con Chocolatey
Chocolatey es un administrador de paquetes de código abierto que puede ayudarlo a instalar, administrar y actualizar el software en sus servidores y escritorios de Windows.

Si tiene Chocolatey instalado en su máquina y es su administrador de paquetes preferido, puede usar el siguiente comando para instalar Git:

```bash

choco install git

```

Configurar Git para su uso
Antes de comenzar a usar Git, hay algunas cosas que debemos configurar. Establecer su nombre y su dirección de correo electrónico es el primer paso. Esta información se utiliza para registrar cualquier cambio que realice en los repositorios de Git.

Abra una herramienta de línea de comando y escriba lo siguiente:

```bash

git config --global user.name "Your Name"
git config --global user.email “you@example.com”

```

## 14 días de Git
En el siguiente artículo de 14 días de Git, comenzaremos a usar Git y familiarizarnos con los comandos básicos.¡Asegúrate de suscribirte y unirte para seguir en el camino del aprendizaje!

Recuerda que puedes seguirlo aquí: [https://github.com/LucioMSP/14-dias-de-Git](https://github.com/LucioMSP/14-dias-de-Git)

## ¡Happy Coding!

### Nota:
Este artículo es una traducción al español no 100% fiel a [Techielass por Sarah Lean](https://www.techielass.com/installing-git/)