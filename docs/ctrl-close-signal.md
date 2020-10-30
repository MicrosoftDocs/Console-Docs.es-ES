---
title: CTRL + cerrar señal
description: El sistema genera una señal CTRL + cerrar cuando el usuario cierra una consola.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_ctrl\_close\_signal'
- base.ctrl\_close\_signal
- consoles.ctrl\_close\_signal
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a327dd55-3250-40ee-b1c4-6ba3b80984a8
ms.openlocfilehash: d3775bf0b8536fc531905ee6665a1e2c294d0a68
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038233"
---
# <a name="ctrlclose-signal"></a>CTRL + cerrar señal

El sistema genera una señal CTRL + cerrar cuando el usuario cierra una consola. Todos los procesos conectados a la consola reciben la señal, con lo que cada proceso tiene la oportunidad de limpiar antes de la terminación. Cuando un proceso recibe esta señal, la función controladora puede realizar una de las siguientes acciones después de realizar las operaciones de limpieza:

- Llame a [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) para finalizar el proceso.
- Devuelve **false** . Si ninguna de las funciones de controlador registradas devuelve **true** , el controlador predeterminado finaliza el proceso.
- Devuelve **true** . En este caso, no se llama a ninguna otra función de controlador y finaliza el proceso.
