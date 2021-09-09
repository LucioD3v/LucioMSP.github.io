---
layout: post
title: Fundamentos de ECS - Redes (Networking)
description: Séptimo artículo sobre Elastic Compute Service (ECS) de Alibaba - Redes (Networking).
image: /assets/img/blog/post-headers/alibaba/VPC.jpg
noindex: true
comments: true
author: lucio
kate: hl markdown;
categories: [alibaba]
tags:
  - alibaba
  - networking
  - redes
keywords:
  - alibaba
  - ecs
  - elastic
  - service
  - cloud
  - networking
lang: es
---

Hola amigos, sean bienvenidos a esta serie de artículos introductorios dedicados a Elastic Compute Service o ECS de Alibaba. En esta séptima y última entrega veremos ECS Networking o Redes de ECS.

![image](/assets/img/blog/tutorials/alibaba/articulos-ecs/alibaba-networking.jpg)

La nube privada virtual (Virtual Private Cloud - VPC) es una red virtual aislada lógicamente, la cual proporciona aislamiento a nivel de VLAN y bloquea las comunicaciones de la red externa; es un requisito al aprovisionar una instancia de ECS.

VPC ofrece dos funciones principales, los usuarios pueden personalizar su propia topología de red, asignar rangos de direcciones IP privadas, asignar segmentos de red y configurar VSwitches.

Los clientes pueden integrar centros de datos existentes a través de una línea dedicada (Express Connect) o una puerta de enlace VPN para formar una nube híbrida.

Una red privada virtual se compone de dos componentes principales: 

- Un enrutador virtual (VRouter) 
- Uno o más conmutadores virtuales (VSwitch).

Un VSwitch es un dispositivo de red básico de una red de VPC y se usa para conectar diferentes instancias de ECS juntas en una subred. Una VPC puede tener un máximo de 24 VSwitches.

Un VRouter es un concentrador que conecta todos los VSwitches en la VPC y sirve como un dispositivo de puerta de enlace que puede conectarse a otras redes.

![image](/assets/img/blog/tutorials/alibaba/articulos-ecs/VPC-Networking.png)

En el diagrama, puede ver la zona 1 y la zona 2 representadas en la región de Mumbai en Asia. Como podemos ver, en la zona 1 contamos que la VM 1 y la VM 2 están conectadas a un vSwitch, y en la zona 2, la VM 3 está conectada a un VSwitch. Pero ambos VSwitches están dentro de la VPC que se ha creado, por lo tanto, VM1, VM2 y VM3 pueden comunicarse entre sí, independientemente del hecho de que estén en zonas diferentes; están en la misma red de nube privada virtual.

## Virtual Private Network

A cada instancia de ECS conectada a VPC se le asigna una dirección IP privada cuando se crea. Esa dirección está determinada por la VPC y el bloque CIDR del vSwitch al que está conectada la instancia.

Se puede utilizar una dirección IP privada en los siguientes escenarios:

- Balanceo de carga
- Comunicación entre instancias de ECS dentro de una intranet
- Comunicación entre una instancia de ECS y otros productos en la nube (como OSS y RDS) o dentro de una intranet.

Las instancias de ECS admiten dos tipos de direcciones IP públicas:

** El primero es NATPublicIP, que se asigna a una instancia ECS conectada a VPC. Este tipo de dirección solo se puede liberar y no se puede desvincular de la instancia. 
** El segundo es la dirección IP elástica (EIP). Una dirección IP elástica (EIP) es una dirección IP pública independiente que puede comprar y usar. Los EIP se pueden asociar a diferentes instancias de ECS que residen dentro de las VPC a lo largo del tiempo para permitir el acceso público a las instancias de ECS.

Sus casos de uso son:

Si no desea conservar la dirección IP pública cuando se libera la instancia, puede usar una dirección NatPublicIP
Si desea mantener una dirección IP pública y asociarla a cualquiera de sus instancias ECS conectadas a VPC en la misma región, debe usar la dirección EIP.
