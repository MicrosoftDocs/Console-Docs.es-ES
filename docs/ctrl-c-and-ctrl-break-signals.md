---
title: Señales de Ctrl+C y Ctrl+Inter
description: Las combinaciones de teclas Ctrl+C y Ctrl+Inter reciben un tratamiento especial por parte de los procesos de consola.
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420194"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a><span data-ttu-id="0d5d5-104">Señales de Ctrl+C y Ctrl+Inter</span><span class="sxs-lookup"><span data-stu-id="0d5d5-104">CTRL+C and CTRL+BREAK Signals</span></span>

<span data-ttu-id="0d5d5-105">Las combinaciones de teclas <kbd>Ctrl</kbd>+<kbd>C</kbd> y <kbd>Ctrl</kbd>+<kbd>Inter</kbd> reciben un tratamiento especial por parte de los procesos de consola.</span><span class="sxs-lookup"><span data-stu-id="0d5d5-105">The <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations receive special handling by console processes.</span></span> <span data-ttu-id="0d5d5-106">De forma predeterminada, cuando una ventana de consola tiene el foco del teclado, <kbd>Ctrl</kbd>+<kbd>C</kbd> o <kbd>Ctrl</kbd>+<kbd>Inter</kbd> se trata como una señal (SIGINT o SIGBREAK) y no como entrada de teclado.</span><span class="sxs-lookup"><span data-stu-id="0d5d5-106">By default, when a console window has the keyboard focus, <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> is treated as a signal (SIGINT or SIGBREAK) and not as keyboard input.</span></span> <span data-ttu-id="0d5d5-107">De forma predeterminada, estas señales se pasan a todos los procesos de la consola que están asociados a la consola.</span><span class="sxs-lookup"><span data-stu-id="0d5d5-107">By default, these signals are passed to all console processes that are attached to the console.</span></span> <span data-ttu-id="0d5d5-108">(Los procesos desasociados no se ven afectados.</span><span class="sxs-lookup"><span data-stu-id="0d5d5-108">(Detached processes are not affected.</span></span> <span data-ttu-id="0d5d5-109">Consulte [**Creación de una consola**](creation-of-a-console.md)). El sistema crea un nuevo subproceso en cada proceso de cliente para controlar el evento.</span><span class="sxs-lookup"><span data-stu-id="0d5d5-109">See [**Creation of a Console**](creation-of-a-console.md).) The system creates a new thread in each client process to handle the event.</span></span> <span data-ttu-id="0d5d5-110">El subproceso genera una excepción si se está depurando el proceso.</span><span class="sxs-lookup"><span data-stu-id="0d5d5-110">The thread raises an exception if the process is being debugged.</span></span> <span data-ttu-id="0d5d5-111">El depurador puede controlar la excepción o continuar con la excepción sin controlar.</span><span class="sxs-lookup"><span data-stu-id="0d5d5-111">The debugger can handle the exception or continue with the exception unhandled.</span></span>

<span data-ttu-id="0d5d5-112"><kbd>Ctrl</kbd>+<kbd>Inter</kbd> se trata siempre como una señal, pero una aplicación puede cambiar el comportamiento predeterminado de <kbd>Ctrl</kbd>+<kbd>C</kbd> de dos maneras que impidan que se llame a las funciones del controlador:</span><span class="sxs-lookup"><span data-stu-id="0d5d5-112"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but an application can change the default <kbd>CTRL</kbd>+<kbd>C</kbd> behavior in two ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="0d5d5-113">La función [**SetConsoleMode**](setconsolemode.md) puede deshabilitar el modo de entrada **ENABLE\_PROCESSED\_INPUT** para el búfer de entrada de una consola, por lo que Ctrl+C se indica como entrada del teclado en lugar de como una señal.</span><span class="sxs-lookup"><span data-stu-id="0d5d5-113">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** input mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="0d5d5-114">Cuando se llama a [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) con los valores **NULL** y **TRUE** para sus parámetros, el proceso de llamada omite las señales de Ctrl+C.</span><span class="sxs-lookup"><span data-stu-id="0d5d5-114">When [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) is called with **NULL** and **TRUE** values for its parameters, the calling process ignores CTRL+C signals.</span></span> <span data-ttu-id="0d5d5-115">El procesamiento normal de Ctrl+C se restaura llamando a **SetConsoleCtrlHandler** con los valores **NULL** y **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="0d5d5-115">Normal CTRL+C processing is restored by calling **SetConsoleCtrlHandler** with **NULL** and **FALSE** values.</span></span> <span data-ttu-id="0d5d5-116">Los procesos secundarios heredan este atributo de omitir o no omitir las señales de Ctrl+C, pero puede habilitarse o deshabilitarse en cualquier proceso sin que ello afecte a los procesos existentes.</span><span class="sxs-lookup"><span data-stu-id="0d5d5-116">This attribute of ignoring or not ignoring CTRL+C signals is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>

<span data-ttu-id="0d5d5-117">Para obtener más información sobre cómo se procesan estas señales, incluidos los tiempos de espera, vea la documentación de devolución de llamada de [**Rutina del controlador**](handlerroutine.md).</span><span class="sxs-lookup"><span data-stu-id="0d5d5-117">For more information on how these signals are processed, including timeouts, please see the [**Handler Routine**](handlerroutine.md) callback documentation.</span></span>
