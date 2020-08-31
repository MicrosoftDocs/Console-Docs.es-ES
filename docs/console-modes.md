---
title: Modos de consola
description: Asociado a cada búfer de entrada de la consola hay un conjunto de modos de entrada que afecta a las operaciones de entrada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_modes'
- base.console\_modes
- consoles.console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f0dcc123-3b12-44c4-8f94-920203f5198e
ms.openlocfilehash: b00f53a282833b560a29c6bed4c7ef0b9e056ba5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060853"
---
# <a name="console-modes"></a><span data-ttu-id="b2c62-104">Modos de consola</span><span class="sxs-lookup"><span data-stu-id="b2c62-104">Console Modes</span></span>


<span data-ttu-id="b2c62-105">Asociado a cada búfer de entrada de la consola hay un conjunto de modos de entrada que afecta a las operaciones de entrada.</span><span class="sxs-lookup"><span data-stu-id="b2c62-105">Associated with each console input buffer is a set of input modes that affects input operations.</span></span> <span data-ttu-id="b2c62-106">Del mismo modo, cada búfer de pantalla de la consola tiene un conjunto de modos de salida que afecta a las operaciones de salida.</span><span class="sxs-lookup"><span data-stu-id="b2c62-106">Similarly, each console screen buffer has a set of output modes that affects output operations.</span></span> <span data-ttu-id="b2c62-107">Los modos de entrada se pueden dividir en dos grupos: los que afectan a las funciones de entrada de alto nivel y a los que afectan a las funciones de entrada de bajo nivel.</span><span class="sxs-lookup"><span data-stu-id="b2c62-107">The input modes can be divided into two groups: those that affect the high-level input functions and those that affect the low-level input functions.</span></span> <span data-ttu-id="b2c62-108">Los modos de salida solo afectan a las aplicaciones que usan las funciones de salida de alto nivel.</span><span class="sxs-lookup"><span data-stu-id="b2c62-108">The output modes only affect applications that use the high-level output functions.</span></span>

<span data-ttu-id="b2c62-109">La función [**GetConsoleMode**](getconsolemode.md) notifica el modo de entrada actual del búfer de entrada de una consola o el modo de salida actual de un búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="b2c62-109">The [**GetConsoleMode**](getconsolemode.md) function reports the current input mode of a console's input buffer or the current output mode of a screen buffer.</span></span> <span data-ttu-id="b2c62-110">La función [**SetConsoleMode**](setconsolemode.md) establece el modo actual de un búfer de entrada de la consola o de un búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="b2c62-110">The [**SetConsoleMode**](setconsolemode.md) function sets the current mode of either a console input buffer or a screen buffer.</span></span> <span data-ttu-id="b2c62-111">Si una consola tiene varios búferes de pantalla, los modos de salida de cada uno de ellos pueden ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="b2c62-111">If a console has multiple screen buffers, the output modes of each can be different.</span></span> <span data-ttu-id="b2c62-112">Una aplicación puede cambiar los modos de e/s en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="b2c62-112">An application can change I/O modes at any time.</span></span> <span data-ttu-id="b2c62-113">Para obtener más información sobre los modos de consola que afectan a las operaciones de e/s de alto nivel y de bajo nivel, vea modos de consola de [alto](high-level-console-modes.md) nivel y [modos de consola de bajo nivel](low-level-console-modes.md).</span><span class="sxs-lookup"><span data-stu-id="b2c62-113">For more information about the console modes that affect high-level and low-level I/O operations, see [High-Level Console Modes](high-level-console-modes.md) and [Low-Level Console Modes](low-level-console-modes.md).</span></span>

<span data-ttu-id="b2c62-114">La función [**GetConsoleDisplayMode**](getconsoledisplaymode.md) notifica si la consola actual está en modo de pantalla completa y si se comunica directamente con el hardware.</span><span class="sxs-lookup"><span data-stu-id="b2c62-114">The [**GetConsoleDisplayMode**](getconsoledisplaymode.md) function reports whether the current console is in full-screen mode and whether it communicates directly with the hardware.</span></span>

 

 




