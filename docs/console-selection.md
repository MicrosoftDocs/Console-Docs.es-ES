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
# <a name="console-selection"></a>Selección de la consola

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Una aplicación de accesibilidad necesita información sobre la selección del usuario en la consola de. Para recuperar la selección actual de la consola, llame a la función [**GetConsoleSelectionInfo**](getconsoleselectioninfo.md) . La estructura de [**\_ \_ información de selección de consola**](console-selection-info-str.md) contiene información sobre la selección, como el delimitador, las coordenadas y el estado.
