---
title: Controladores de control de consola
description: Cada proceso de consola tiene su propia lista de funciones de controlador de control a las que llama el sistema cuando el proceso recibe una señal CTRL + C, CTRL + INTER o CTRL + cerrar.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_control\_handlers'
- base.console\_control\_handlers
- consoles.console\_control\_handlers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6480e8ee-d228-4c07-99df-de1e0c3ca250
ms.openlocfilehash: b3fa6f3e842d1757b90ff03c30a343ad12964882
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060873"
---
# <a name="console-control-handlers"></a>Controladores de control de consola


Cada proceso de consola tiene su propia lista de funciones de controlador de control a las que llama el sistema cuando el proceso recibe una señal [Ctrl + C](ctrl-c-and-ctrl-break-signals.md), [Ctrl + Inter](ctrl-c-and-ctrl-break-signals.md)o [Ctrl + cerrar](ctrl-close-signal.md) . Inicialmente, la lista de controladores de control para cada proceso contiene solo una función de controlador predeterminada que llama a la función [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) . Un proceso de consola puede Agregar o quitar funciones [**HandlerRoutine**](handlerroutine.md) adicionales mediante una llamada a la función [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) . Esta función no afecta a las listas de controladores de control para otros procesos. Cuando un proceso de consola recibe cualquiera de las señales de control, llama a las funciones de controlador en una última base de registro, que se llama primero, hasta que uno de los controladores devuelve **true**. Si ninguno de los controladores devuelve **true**, se llama al controlador predeterminado.

El parámetro *dwCtrlType* de la función identifica qué señal de control se ha recibido y el valor devuelto indica si se ha controlado la señal.

Para obtener un ejemplo de una función de controlador de control, vea [registrar una función de controlador de control](registering-a-control-handler-function.md).

 

 




