---
title: Cerrar una consola
description: Un proceso puede usar la función FreeConsole para desasociarse de su consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_closing\_a\_console'
- base.closing\_a\_console
- consoles.closing\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 254b7cfc-4dee-452f-a409-4fc90d20d4c1
ms.openlocfilehash: bdd6b98f96f4ecb64aa6750396c30ef2dd6d0f74
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060893"
---
# <a name="closing-a-console"></a><span data-ttu-id="b8447-104">Cerrar una consola</span><span class="sxs-lookup"><span data-stu-id="b8447-104">Closing a Console</span></span>


<span data-ttu-id="b8447-105">Un proceso puede usar la función [**FreeConsole**](freeconsole.md) para desasociarse de su consola.</span><span class="sxs-lookup"><span data-stu-id="b8447-105">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console.</span></span> <span data-ttu-id="b8447-106">Si otros procesos comparten la consola, la consola no se destruye, pero el proceso que llamó a **FreeConsole** no puede hacer referencia a ella.</span><span class="sxs-lookup"><span data-stu-id="b8447-106">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="b8447-107">Después de llamar a **FreeConsole**, el proceso puede usar [**AllocConsole**](allocconsole.md) para crear una nueva consola o [**AttachConsole**](attachconsole.md) para adjuntar a otra consola.</span><span class="sxs-lookup"><span data-stu-id="b8447-107">After calling **FreeConsole**, the process can use [**AllocConsole**](allocconsole.md) to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<span data-ttu-id="b8447-108">Una consola se cierra cuando el último proceso asociado a ella finaliza o llama a [**FreeConsole**](freeconsole.md).</span><span class="sxs-lookup"><span data-stu-id="b8447-108">A console is closed when the last process attached to it terminates or calls [**FreeConsole**](freeconsole.md).</span></span>

 

 




