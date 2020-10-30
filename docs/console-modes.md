---
title: Modos de consola
description: Asociado a cada búfer de entrada de la consola hay un conjunto de modos de entrada que afecta a las operaciones de entrada.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_modes'
- base.console\_modes
- consoles.console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f0dcc123-3b12-44c4-8f94-920203f5198e
ms.openlocfilehash: 0bd048101546d20735745656677702f9f07115fd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039203"
---
# <a name="console-modes"></a><span data-ttu-id="6289f-104">Modos de consola</span><span class="sxs-lookup"><span data-stu-id="6289f-104">Console Modes</span></span>

<span data-ttu-id="6289f-105">Asociado a cada búfer de entrada de la consola hay un conjunto de modos de entrada que afecta a las operaciones de entrada.</span><span class="sxs-lookup"><span data-stu-id="6289f-105">Associated with each console input buffer is a set of input modes that affects input operations.</span></span> <span data-ttu-id="6289f-106">Del mismo modo, cada búfer de pantalla de la consola tiene un conjunto de modos de salida que afecta a las operaciones de salida.</span><span class="sxs-lookup"><span data-stu-id="6289f-106">Similarly, each console screen buffer has a set of output modes that affects output operations.</span></span> <span data-ttu-id="6289f-107">Los modos de entrada se pueden dividir en dos grupos: los que afectan a las funciones de entrada de alto nivel y a los que afectan a las funciones de entrada de bajo nivel.</span><span class="sxs-lookup"><span data-stu-id="6289f-107">The input modes can be divided into two groups: those that affect the high-level input functions and those that affect the low-level input functions.</span></span> <span data-ttu-id="6289f-108">Los modos de salida solo afectan a las aplicaciones que usan las funciones de salida de alto nivel.</span><span class="sxs-lookup"><span data-stu-id="6289f-108">The output modes only affect applications that use the high-level output functions.</span></span>

<span data-ttu-id="6289f-109">La función [**GetConsoleMode**](getconsolemode.md) notifica el modo de entrada actual del búfer de entrada de una consola o el modo de salida actual de un búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="6289f-109">The [**GetConsoleMode**](getconsolemode.md) function reports the current input mode of a console's input buffer or the current output mode of a screen buffer.</span></span> <span data-ttu-id="6289f-110">La función [**SetConsoleMode**](setconsolemode.md) establece el modo actual de un búfer de entrada de la consola o de un búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="6289f-110">The [**SetConsoleMode**](setconsolemode.md) function sets the current mode of either a console input buffer or a screen buffer.</span></span> <span data-ttu-id="6289f-111">Si una consola tiene varios búferes de pantalla, los modos de salida de cada uno de ellos pueden ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="6289f-111">If a console has multiple screen buffers, the output modes of each can be different.</span></span> <span data-ttu-id="6289f-112">Una aplicación puede cambiar los modos de e/s en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="6289f-112">An application can change I/O modes at any time.</span></span> <span data-ttu-id="6289f-113">Para obtener más información sobre los modos de consola que afectan a las operaciones de e/s de alto nivel y de bajo nivel, vea modos de consola de [alto](high-level-console-modes.md) nivel y [modos de consola de bajo nivel](low-level-console-modes.md).</span><span class="sxs-lookup"><span data-stu-id="6289f-113">For more information about the console modes that affect high-level and low-level I/O operations, see [High-Level Console Modes](high-level-console-modes.md) and [Low-Level Console Modes](low-level-console-modes.md).</span></span>

<span data-ttu-id="6289f-114">Una aplicación de línea de comandos debería esperar que otras aplicaciones de línea de comandos puedan cambiar el modo de consola en cualquier momento y no restaurar su formato original antes de que se devuelva el control.</span><span class="sxs-lookup"><span data-stu-id="6289f-114">A command-line application should expect that other command-line applications may change the console mode at any time and may not restore it to its original form before control is returned.</span></span> <span data-ttu-id="6289f-115">Además, se recomienda que todas las aplicaciones de línea de comandos capturen el modo de consola inicial en el inicio e intenten restaurarlos al salir para garantizar un impacto mínimo en otras aplicaciones de línea de comandos adjuntas a la misma consola.</span><span class="sxs-lookup"><span data-stu-id="6289f-115">Additionally, we recommend that all command-line applications should capture the initial console mode at startup and attempt to restore it when exiting to ensure minimal impact on other command-line applications attached to the same console.</span></span>

<span data-ttu-id="6289f-116">La función [**GetConsoleDisplayMode**](getconsoledisplaymode.md) notifica si la consola actual está en modo de pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="6289f-116">The [**GetConsoleDisplayMode**](getconsoledisplaymode.md) function reports whether the current console is in full-screen mode.</span></span>
