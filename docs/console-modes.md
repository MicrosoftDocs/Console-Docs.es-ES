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
# <a name="console-modes"></a>Modos de consola

Asociado a cada búfer de entrada de la consola hay un conjunto de modos de entrada que afecta a las operaciones de entrada. Del mismo modo, cada búfer de pantalla de la consola tiene un conjunto de modos de salida que afecta a las operaciones de salida. Los modos de entrada se pueden dividir en dos grupos: los que afectan a las funciones de entrada de alto nivel y a los que afectan a las funciones de entrada de bajo nivel. Los modos de salida solo afectan a las aplicaciones que usan las funciones de salida de alto nivel.

La función [**GetConsoleMode**](getconsolemode.md) notifica el modo de entrada actual del búfer de entrada de una consola o el modo de salida actual de un búfer de pantalla. La función [**SetConsoleMode**](setconsolemode.md) establece el modo actual de un búfer de entrada de la consola o de un búfer de pantalla. Si una consola tiene varios búferes de pantalla, los modos de salida de cada uno de ellos pueden ser diferentes. Una aplicación puede cambiar los modos de e/s en cualquier momento. Para obtener más información sobre los modos de consola que afectan a las operaciones de e/s de alto nivel y de bajo nivel, vea modos de consola de [alto](high-level-console-modes.md) nivel y [modos de consola de bajo nivel](low-level-console-modes.md).

Una aplicación de línea de comandos debería esperar que otras aplicaciones de línea de comandos puedan cambiar el modo de consola en cualquier momento y no restaurar su formato original antes de que se devuelva el control. Además, se recomienda que todas las aplicaciones de línea de comandos capturen el modo de consola inicial en el inicio e intenten restaurarlos al salir para garantizar un impacto mínimo en otras aplicaciones de línea de comandos adjuntas a la misma consola.

La función [**GetConsoleDisplayMode**](getconsoledisplaymode.md) notifica si la consola actual está en modo de pantalla completa.
