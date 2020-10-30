---
title: Selección de la consola
description: Una aplicación de accesibilidad necesita información sobre la selección del usuario en la consola de.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_selection'
- base.console\_selection
- consoles.console\_selection
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f631e1b-d502-45b7-9c15-34c01e913738
ms.openlocfilehash: afc2d0a7615381b394df7f496aaf1b2a6002d04f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039163"
---
# <a name="console-selection"></a><span data-ttu-id="595d2-104">Selección de la consola</span><span class="sxs-lookup"><span data-stu-id="595d2-104">Console Selection</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="595d2-105">Una aplicación de accesibilidad necesita información sobre la selección del usuario en la consola de.</span><span class="sxs-lookup"><span data-stu-id="595d2-105">An accessibility application needs information about the user's selection in the console.</span></span> <span data-ttu-id="595d2-106">Para recuperar la selección actual de la consola, llame a la función [**GetConsoleSelectionInfo**](getconsoleselectioninfo.md) .</span><span class="sxs-lookup"><span data-stu-id="595d2-106">To retrieve the current console selection, call the [**GetConsoleSelectionInfo**](getconsoleselectioninfo.md) function.</span></span> <span data-ttu-id="595d2-107">La estructura de [**\_ \_ información de selección de consola**](console-selection-info-str.md) contiene información sobre la selección, como el delimitador, las coordenadas y el estado.</span><span class="sxs-lookup"><span data-stu-id="595d2-107">The [**CONSOLE\_SELECTION\_INFO**](console-selection-info-str.md) structure contains information about the selection, such as the anchor, coordinates, and status.</span></span>
