---
title: CTRL + C y CTRL + INTERRUMPIr señales
description: Las combinaciones de teclas CTRL + C y CTRL + INTER reciben un tratamiento especial por parte de los procesos de consola.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_ctrl\_c\_and\_ctrl\_break\_signals'
- base.ctrl\_c\_and\_ctrl\_break\_signals
- consoles.ctrl\_c\_and\_ctrl\_break\_signals
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5357ed99-920b-47a0-a922-d5faed7bf23e
ms.localizationpriority: high
ms.openlocfilehash: 38cc3486a9e945635147c2e17a4d2f0d197d1d3c
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420194"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a><span data-ttu-id="5f975-104">CTRL + C y CTRL + INTERRUMPIr señales</span><span class="sxs-lookup"><span data-stu-id="5f975-104">CTRL+C and CTRL+BREAK Signals</span></span>

<span data-ttu-id="5f975-105">Las combinaciones de teclas <kbd>Ctrl</kbd> + <kbd>C</kbd> y <kbd>Ctrl</kbd> + <kbd>interrumpir</kbd> reciben un tratamiento especial por parte de los procesos de consola.</span><span class="sxs-lookup"><span data-stu-id="5f975-105">The <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations receive special handling by console processes.</span></span> <span data-ttu-id="5f975-106">De forma predeterminada, cuando una ventana de consola tiene el foco de teclado, <kbd>Ctrl</kbd> + <kbd>C</kbd> o <kbd>Ctrl</kbd> + <kbd>inter</kbd> se trata como una señal (SIGINT o SIGBREAK) y no como entrada de teclado.</span><span class="sxs-lookup"><span data-stu-id="5f975-106">By default, when a console window has the keyboard focus, <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> is treated as a signal (SIGINT or SIGBREAK) and not as keyboard input.</span></span> <span data-ttu-id="5f975-107">De forma predeterminada, estas señales se pasan a todos los procesos de la consola que están conectados a la consola.</span><span class="sxs-lookup"><span data-stu-id="5f975-107">By default, these signals are passed to all console processes that are attached to the console.</span></span> <span data-ttu-id="5f975-108">(Los procesos desasociados no se ven afectados.</span><span class="sxs-lookup"><span data-stu-id="5f975-108">(Detached processes are not affected.</span></span> <span data-ttu-id="5f975-109">Vea [**creación de una consola**](creation-of-a-console.md)). El sistema crea un nuevo subproceso en cada proceso de cliente para controlar el evento.</span><span class="sxs-lookup"><span data-stu-id="5f975-109">See [**Creation of a Console**](creation-of-a-console.md).) The system creates a new thread in each client process to handle the event.</span></span> <span data-ttu-id="5f975-110">El subproceso genera una excepción si se está depurando el proceso.</span><span class="sxs-lookup"><span data-stu-id="5f975-110">The thread raises an exception if the process is being debugged.</span></span> <span data-ttu-id="5f975-111">El depurador puede controlar la excepción o continuar con la excepción no controlada.</span><span class="sxs-lookup"><span data-stu-id="5f975-111">The debugger can handle the exception or continue with the exception unhandled.</span></span>

<span data-ttu-id="5f975-112"><kbd>Ctrl</kbd> + <kbd>Break</kbd> siempre se trata como una señal, pero una aplicación puede cambiar el comportamiento predeterminado de <kbd>Ctrl</kbd> + <kbd>C</kbd> de dos maneras que impiden que se llame a las funciones del controlador:</span><span class="sxs-lookup"><span data-stu-id="5f975-112"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but an application can change the default <kbd>CTRL</kbd>+<kbd>C</kbd> behavior in two ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="5f975-113">La función [**SetConsoleMode**](setconsolemode.md) puede deshabilitar el modo de entrada de entrada **\_ procesada \_** para el búfer de entrada de una consola, por lo que Ctrl + C se indica como entrada de teclado en lugar de como señal.</span><span class="sxs-lookup"><span data-stu-id="5f975-113">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** input mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="5f975-114">Cuando se llama a [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) con los valores **null** y **true** para sus parámetros, el proceso de llamada omite las señales Ctrl + C.</span><span class="sxs-lookup"><span data-stu-id="5f975-114">When [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) is called with **NULL** and **TRUE** values for its parameters, the calling process ignores CTRL+C signals.</span></span> <span data-ttu-id="5f975-115">El procesamiento normal de CTRL + C se restaura llamando a **SetConsoleCtrlHandler** con valores **null** y **false** .</span><span class="sxs-lookup"><span data-stu-id="5f975-115">Normal CTRL+C processing is restored by calling **SetConsoleCtrlHandler** with **NULL** and **FALSE** values.</span></span> <span data-ttu-id="5f975-116">Este atributo de omitir o no omitir las señales CTRL + C es heredado por procesos secundarios, pero puede habilitarse o deshabilitarse en cualquier proceso sin que ello afecte a los procesos existentes.</span><span class="sxs-lookup"><span data-stu-id="5f975-116">This attribute of ignoring or not ignoring CTRL+C signals is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>

<span data-ttu-id="5f975-117">Para obtener más información sobre cómo se procesan estas señales, incluidos los tiempos de espera, vea la documentación de devolución de llamada de [**rutina de controlador**](handlerroutine.md) .</span><span class="sxs-lookup"><span data-stu-id="5f975-117">For more information on how these signals are processed, including timeouts, please see the [**Handler Routine**](handlerroutine.md) callback documentation.</span></span>
