---
title: Modos de consola de High-Level
description: El comportamiento de las funciones de la consola de alto nivel se ve afectado por los modos de entrada y salida de la consola.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_high\_level\_console\_modes'
- base.high\_level\_console\_modes
- consoles.high\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3ec915eb-333d-484d-a14d-46377b503ecc
ms.openlocfilehash: 418983a788957578e97fee70624fd80c1b09bc04
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038650"
---
# <a name="high-level-console-modes"></a><span data-ttu-id="b5124-104">Modos de consola de High-Level</span><span class="sxs-lookup"><span data-stu-id="b5124-104">High-Level Console Modes</span></span>

<span data-ttu-id="b5124-105">El comportamiento de las funciones de la consola de alto nivel se ve afectado por los modos de entrada y salida de la consola.</span><span class="sxs-lookup"><span data-stu-id="b5124-105">The behavior of the high-level console functions is affected by the console input and output modes.</span></span> <span data-ttu-id="b5124-106">Todos los siguientes modos de entrada de la consola están habilitados para el búfer de entrada de la consola cuando se crea una consola:</span><span class="sxs-lookup"><span data-stu-id="b5124-106">All of the following console input modes are enabled for a console's input buffer when a console is created:</span></span>

- <span data-ttu-id="b5124-107">Modo de entrada de línea</span><span class="sxs-lookup"><span data-stu-id="b5124-107">Line input mode</span></span>
- <span data-ttu-id="b5124-108">Modo de entrada procesado</span><span class="sxs-lookup"><span data-stu-id="b5124-108">Processed input mode</span></span>
- <span data-ttu-id="b5124-109">Modo de entrada de eco</span><span class="sxs-lookup"><span data-stu-id="b5124-109">Echo input mode</span></span>

<span data-ttu-id="b5124-110">Los dos modos de salida de la consola siguientes están habilitados para un búfer de pantalla de la consola cuando se crea:</span><span class="sxs-lookup"><span data-stu-id="b5124-110">Both of the following console output modes are enabled for a console screen buffer when it is created:</span></span>

- <span data-ttu-id="b5124-111">Modo de salida procesado</span><span class="sxs-lookup"><span data-stu-id="b5124-111">Processed output mode</span></span>
- <span data-ttu-id="b5124-112">Encapsulado en modo de salida EOL</span><span class="sxs-lookup"><span data-stu-id="b5124-112">Wrapping at EOL output mode</span></span>

<span data-ttu-id="b5124-113">Los tres modos de entrada, junto con el modo de salida procesado, están diseñados para funcionar juntos.</span><span class="sxs-lookup"><span data-stu-id="b5124-113">All three input modes, along with processed output mode, are designed to work together.</span></span> <span data-ttu-id="b5124-114">Es mejor habilitar o deshabilitar todos estos modos como un grupo.</span><span class="sxs-lookup"><span data-stu-id="b5124-114">It is best to either enable or disable all of these modes as a group.</span></span> <span data-ttu-id="b5124-115">Cuando todos están habilitados, se dice que la aplicación está en modo "cocido", lo que significa que la mayor parte del procesamiento se controla para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b5124-115">When all are enabled, the application is said to be in "cooked" mode, which means that most of the processing is handled for the application.</span></span> <span data-ttu-id="b5124-116">Cuando se deshabilitan todos, la aplicación está en modo "sin procesar", lo que significa que la entrada no se filtra y se deja cualquier procesamiento en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b5124-116">When all are disabled, the application is in "raw" mode, which means that input is unfiltered and any processing is left to the application.</span></span>

<span data-ttu-id="b5124-117">Una aplicación puede usar la función [**GetConsoleMode**](getconsolemode.md) para determinar el modo actual del búfer de entrada o el búfer de pantalla de una consola.</span><span class="sxs-lookup"><span data-stu-id="b5124-117">An application can use the [**GetConsoleMode**](getconsolemode.md) function to determine the current mode of a console's input buffer or screen buffer.</span></span> <span data-ttu-id="b5124-118">Puede habilitar o deshabilitar cualquiera de estos modos con los siguientes valores en la función [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="b5124-118">You can enable or disable any of these modes by using the following values in the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="b5124-119">Tenga en cuenta que al establecer el modo de salida de un búfer de pantalla no se ve afectado el modo de salida de otros búferes de pantalla.</span><span class="sxs-lookup"><span data-stu-id="b5124-119">Note that setting the output mode of one screen buffer does not affect the output mode of other screen buffers.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]
