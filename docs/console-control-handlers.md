---
title: Identificadores de control de la consola
description: Cada proceso de consola tiene su propia lista de funciones de controlador de control a las que llama el sistema cuando el proceso recibe una señal CTRL + C, CTRL + INTER o CTRL + cerrar.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_control\_handlers'
- base.console\_control\_handlers
- consoles.console\_control\_handlers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6480e8ee-d228-4c07-99df-de1e0c3ca250
ms.openlocfilehash: 41a1326b5b27531bf74ac571d6881a0f67c2b073
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038433"
---
# <a name="console-control-handlers"></a>Identificadores de control de la consola

Cada proceso de consola tiene su propia lista de funciones de controlador de control a las que llama el sistema cuando el proceso recibe una señal [Ctrl + C](ctrl-c-and-ctrl-break-signals.md), [Ctrl + Inter](ctrl-c-and-ctrl-break-signals.md)o [Ctrl + cerrar](ctrl-close-signal.md) . Inicialmente, la lista de controladores de control para cada proceso contiene solo una función de controlador predeterminada que llama a la función [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) . Un proceso de consola puede Agregar o quitar funciones [**HandlerRoutine**](handlerroutine.md) adicionales mediante una llamada a la función [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) . Esta función no afecta a las listas de controladores de control para otros procesos. Cuando un proceso de consola recibe cualquiera de las señales de control, llama a las funciones de controlador en una última base de registro, que se llama primero, hasta que uno de los controladores devuelve **true** . Si ninguno de los controladores devuelve **true** , se llama al controlador predeterminado.

El parámetro *dwCtrlType* de la función identifica qué señal de control se ha recibido y el valor devuelto indica si se ha controlado la señal.

Se inicia un nuevo subproceso dentro del proceso de cliente de línea de comandos para ejecutar las rutinas de controlador. Puede encontrar más información sobre los valores de tiempo de espera y la acción de este subproceso en la documentación de la función [**HandlerRoutine**](handlerroutine.md#remarks) .

Para obtener un ejemplo de una función de controlador de control, vea [registrar una función de controlador de control](registering-a-control-handler-function.md).
