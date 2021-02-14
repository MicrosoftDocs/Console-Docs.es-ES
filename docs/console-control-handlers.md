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
ms.openlocfilehash: 06528cfc93d074bd0cc2579d5ba50445025a04fb
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358145"
---
# <a name="console-control-handlers"></a><span data-ttu-id="513ca-104">Identificadores de control de la consola</span><span class="sxs-lookup"><span data-stu-id="513ca-104">Console Control Handlers</span></span>

<span data-ttu-id="513ca-105">Cada proceso de consola tiene su propia lista de funciones de controlador de control a las que llama el sistema cuando el proceso recibe una señal [Ctrl + C](ctrl-c-and-ctrl-break-signals.md), [Ctrl + Inter](ctrl-c-and-ctrl-break-signals.md)o [Ctrl + cerrar](ctrl-close-signal.md) .</span><span class="sxs-lookup"><span data-stu-id="513ca-105">Each console process has its own list of control handler functions that are called by the system when the process receives a [CTRL+C](ctrl-c-and-ctrl-break-signals.md), [CTRL+BREAK](ctrl-c-and-ctrl-break-signals.md), or [CTRL+CLOSE](ctrl-close-signal.md) signal.</span></span> <span data-ttu-id="513ca-106">Inicialmente, la lista de controladores de control para cada proceso contiene solo una función de controlador predeterminada que llama a la función [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) .</span><span class="sxs-lookup"><span data-stu-id="513ca-106">Initially, the list of control handlers for each process contains only a default handler function that calls the [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) function.</span></span> <span data-ttu-id="513ca-107">Un proceso de consola puede Agregar o quitar funciones [**HandlerRoutine**](handlerroutine.md) adicionales mediante una llamada a la función [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) .</span><span class="sxs-lookup"><span data-stu-id="513ca-107">A console process can add or remove additional [**HandlerRoutine**](handlerroutine.md) functions by calling the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function.</span></span> <span data-ttu-id="513ca-108">Esta función no afecta a las listas de controladores de control para otros procesos.</span><span class="sxs-lookup"><span data-stu-id="513ca-108">This function does not affect the lists of control handlers for other processes.</span></span> <span data-ttu-id="513ca-109">Cuando un proceso de consola recibe cualquiera de las señales de control, llama a las funciones de controlador en una última base de registro, que se llama primero, hasta que uno de los controladores devuelve **true**.</span><span class="sxs-lookup"><span data-stu-id="513ca-109">When a console process receives any of the control signals, it calls the handler functions on a last-registered, first-called basis until one of the handlers returns **TRUE**.</span></span> <span data-ttu-id="513ca-110">Si ninguno de los controladores devuelve **true**, se llama al controlador predeterminado.</span><span class="sxs-lookup"><span data-stu-id="513ca-110">If none of the handlers returns **TRUE**, the default handler is called.</span></span>

<span data-ttu-id="513ca-111">El parámetro *dwCtrlType* de la función identifica qué señal de control se ha recibido y el valor devuelto indica si se ha controlado la señal.</span><span class="sxs-lookup"><span data-stu-id="513ca-111">The function's *dwCtrlType* parameter identifies which control signal was received, and the return value indicates whether the signal was handled.</span></span>

<span data-ttu-id="513ca-112">Se inicia un nuevo subproceso dentro del proceso de cliente de línea de comandos para ejecutar las rutinas de controlador.</span><span class="sxs-lookup"><span data-stu-id="513ca-112">A new thread is started inside the command-line client process to run the handler routines.</span></span> <span data-ttu-id="513ca-113">Puede encontrar más información sobre los valores de tiempo de espera y la acción de este subproceso en la documentación de la función [**HandlerRoutine**](handlerroutine.md#remarks) .</span><span class="sxs-lookup"><span data-stu-id="513ca-113">More information on the timeout values and action of this thread can be found in the [**HandlerRoutine**](handlerroutine.md#remarks) function documentation.</span></span>

<span data-ttu-id="513ca-114">Para obtener un ejemplo de una función de controlador de control, vea [registrar una función de controlador de control](registering-a-control-handler-function.md).</span><span class="sxs-lookup"><span data-stu-id="513ca-114">For an example of a control handler function, see [Registering a Control Handler Function](registering-a-control-handler-function.md).</span></span>