---
title: Asociar a una consola
description: Un proceso puede usar la función AttachConsole para adjuntar a una consola. Un proceso se puede adjuntar a una consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_attaching\_to\_a\_console'
- base.attaching\_to\_a\_console
- consoles.attaching\_to\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 348e572f-2448-4384-9822-fab01d4ba255
ms.openlocfilehash: e6ab7da4022d45cd2b1d42957f15f4ffa7e068f3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060913"
---
# <a name="attaching-to-a-console"></a><span data-ttu-id="31bf6-105">Asociar a una consola</span><span class="sxs-lookup"><span data-stu-id="31bf6-105">Attaching to a Console</span></span>


<span data-ttu-id="31bf6-106">Un proceso puede usar la función [**AttachConsole**](attachconsole.md) para adjuntar a una consola.</span><span class="sxs-lookup"><span data-stu-id="31bf6-106">A process can use the [**AttachConsole**](attachconsole.md) function to attach to a console.</span></span> <span data-ttu-id="31bf6-107">Un proceso se puede adjuntar a una consola.</span><span class="sxs-lookup"><span data-stu-id="31bf6-107">A process can be attached to one console.</span></span>

<span data-ttu-id="31bf6-108">Una consola de puede tener muchos procesos asociados.</span><span class="sxs-lookup"><span data-stu-id="31bf6-108">A console can have many processes attached to it.</span></span> <span data-ttu-id="31bf6-109">Para recuperar una lista de los procesos adjuntos a una consola, llame a la función [**GetConsoleProcessList**](getconsoleprocesslist.md) .</span><span class="sxs-lookup"><span data-stu-id="31bf6-109">To retrieve a list of the processes attached to a console, call the [**GetConsoleProcessList**](getconsoleprocesslist.md) function.</span></span>

 

 




