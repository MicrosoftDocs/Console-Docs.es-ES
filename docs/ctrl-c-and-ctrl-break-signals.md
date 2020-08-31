---
title: CTRL + C y CTRL + INTERRUMPIr señales
description: Las combinaciones de teclas CTRL + C y CTRL + INTER reciben un tratamiento especial por parte de los procesos de consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_ctrl\_c\_and\_ctrl\_break\_signals'
- base.ctrl\_c\_and\_ctrl\_break\_signals
- consoles.ctrl\_c\_and\_ctrl\_break\_signals
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5357ed99-920b-47a0-a922-d5faed7bf23e
ms.openlocfilehash: 95e28c9d390e9edb0be7dcac5aa4600224ab118c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060752"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a><span data-ttu-id="7f0f2-104">CTRL + C y CTRL + INTERRUMPIr señales</span><span class="sxs-lookup"><span data-stu-id="7f0f2-104">CTRL+C and CTRL+BREAK Signals</span></span>


<span data-ttu-id="7f0f2-105">Las combinaciones de teclas CTRL + C y CTRL + INTER reciben un tratamiento especial por parte de los procesos de consola.</span><span class="sxs-lookup"><span data-stu-id="7f0f2-105">The CTRL+C and CTRL+BREAK key combinations receive special handling by console processes.</span></span> <span data-ttu-id="7f0f2-106">De forma predeterminada, cuando una ventana de consola tiene el foco de teclado, CTRL + C o CTRL + INTER se tratan como una señal (SIGINT o SIGBREAK) y no como entrada de teclado.</span><span class="sxs-lookup"><span data-stu-id="7f0f2-106">By default, when a console window has the keyboard focus, CTRL+C or CTRL+BREAK is treated as a signal (SIGINT or SIGBREAK) and not as keyboard input.</span></span> <span data-ttu-id="7f0f2-107">De forma predeterminada, estas señales se pasan a todos los procesos de la consola que están conectados a la consola.</span><span class="sxs-lookup"><span data-stu-id="7f0f2-107">By default, these signals are passed to all console processes that are attached to the console.</span></span> <span data-ttu-id="7f0f2-108">(Los procesos desasociados no se ven afectados). El sistema crea un nuevo subproceso en cada proceso de cliente para controlar el evento.</span><span class="sxs-lookup"><span data-stu-id="7f0f2-108">(Detached processes are not affected.) The system creates a new thread in each client process to handle the event.</span></span> <span data-ttu-id="7f0f2-109">El subproceso genera una excepción si se está depurando el proceso.</span><span class="sxs-lookup"><span data-stu-id="7f0f2-109">The thread raises an exception if the process is being debugged.</span></span> <span data-ttu-id="7f0f2-110">El depurador puede controlar la excepción o continuar con la excepción no controlada.</span><span class="sxs-lookup"><span data-stu-id="7f0f2-110">The debugger can handle the exception or continue with the exception unhandled.</span></span>

<span data-ttu-id="7f0f2-111">CTRL + INTER siempre se trata como una señal, pero una aplicación puede cambiar el comportamiento predeterminado de CTRL + C de dos maneras que impiden que se llame a las funciones del controlador:</span><span class="sxs-lookup"><span data-stu-id="7f0f2-111">CTRL+BREAK is always treated as a signal, but an application can change the default CTRL+C behavior in two ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="7f0f2-112">La función [**SetConsoleMode**](setconsolemode.md) puede deshabilitar el modo de entrada de entrada \*\* \_ procesada \_ \*\* para el búfer de entrada de una consola, por lo que Ctrl + C se indica como entrada de teclado en lugar de como señal.</span><span class="sxs-lookup"><span data-stu-id="7f0f2-112">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** input mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="7f0f2-113">Cuando se llama a [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) con los valores **null** y **true** para sus parámetros, el proceso de llamada omite las señales Ctrl + C.</span><span class="sxs-lookup"><span data-stu-id="7f0f2-113">When [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) is called with **NULL** and **TRUE** values for its parameters, the calling process ignores CTRL+C signals.</span></span> <span data-ttu-id="7f0f2-114">El procesamiento normal de CTRL + C se restaura llamando a **SetConsoleCtrlHandler** con valores **null** y **false** .</span><span class="sxs-lookup"><span data-stu-id="7f0f2-114">Normal CTRL+C processing is restored by calling **SetConsoleCtrlHandler** with **NULL** and **FALSE** values.</span></span> <span data-ttu-id="7f0f2-115">Este atributo de omitir o no omitir las señales CTRL + C es heredado por procesos secundarios, pero puede habilitarse o deshabilitarse en cualquier proceso sin que ello afecte a los procesos existentes.</span><span class="sxs-lookup"><span data-stu-id="7f0f2-115">This attribute of ignoring or not ignoring CTRL+C signals is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>

 

 




