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
# <a name="console-modes"></a>Modos de consola


Asociado a cada búfer de entrada de la consola hay un conjunto de modos de entrada que afecta a las operaciones de entrada. Del mismo modo, cada búfer de pantalla de la consola tiene un conjunto de modos de salida que afecta a las operaciones de salida. Los modos de entrada se pueden dividir en dos grupos: los que afectan a las funciones de entrada de alto nivel y a los que afectan a las funciones de entrada de bajo nivel. Los modos de salida solo afectan a las aplicaciones que usan las funciones de salida de alto nivel.

La función [**GetConsoleMode**](getconsolemode.md) notifica el modo de entrada actual del búfer de entrada de una consola o el modo de salida actual de un búfer de pantalla. La función [**SetConsoleMode**](setconsolemode.md) establece el modo actual de un búfer de entrada de la consola o de un búfer de pantalla. Si una consola tiene varios búferes de pantalla, los modos de salida de cada uno de ellos pueden ser diferentes. Una aplicación puede cambiar los modos de e/s en cualquier momento. Para obtener más información sobre los modos de consola que afectan a las operaciones de e/s de alto nivel y de bajo nivel, vea modos de consola de [alto](high-level-console-modes.md) nivel y [modos de consola de bajo nivel](low-level-console-modes.md).

La función [**GetConsoleDisplayMode**](getconsoledisplaymode.md) notifica si la consola actual está en modo de pantalla completa y si se comunica directamente con el hardware.

 

 




