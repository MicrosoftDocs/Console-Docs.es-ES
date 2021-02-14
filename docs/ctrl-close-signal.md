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
ms.openlocfilehash: be237eac7649ad76615aea341a555a8a7af6445c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357895"
---
# <a name="ctrlclose-signal"></a>CTRL + cerrar señal

El sistema genera una señal CTRL + cerrar cuando el usuario cierra una consola. Todos los procesos conectados a la consola reciben la señal, con lo que cada proceso tiene la oportunidad de limpiar antes de la terminación. Cuando un proceso recibe esta señal, la función controladora puede realizar una de las siguientes acciones después de realizar las operaciones de limpieza:

- Llame a [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) para finalizar el proceso.
- Devuelve **false**. Si ninguna de las funciones de controlador registradas devuelve **true**, el controlador predeterminado finaliza el proceso.
- Devuelve **true**. En este caso, no se llama a ninguna otra función de controlador y finaliza el proceso.