---
title: Señales de Ctrl+C y Ctrl+Inter
description: Las combinaciones de teclas Ctrl+C y Ctrl+Inter reciben un tratamiento especial por parte de los procesos de consola.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_ctrl\_c\_and\_ctrl\_break\_signals'
- base.ctrl\_c\_and\_ctrl\_break\_signals
- consoles.ctrl\_c\_and\_ctrl\_break\_signals
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5357ed99-920b-47a0-a922-d5faed7bf23e
ms.localizationpriority: high
ms.openlocfilehash: 38cc3486a9e945635147c2e17a4d2f0d197d1d3c
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420194"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a>Señales de Ctrl+C y Ctrl+Inter

Las combinaciones de teclas <kbd>Ctrl</kbd>+<kbd>C</kbd> y <kbd>Ctrl</kbd>+<kbd>Inter</kbd> reciben un tratamiento especial por parte de los procesos de consola. De forma predeterminada, cuando una ventana de consola tiene el foco del teclado, <kbd>Ctrl</kbd>+<kbd>C</kbd> o <kbd>Ctrl</kbd>+<kbd>Inter</kbd> se trata como una señal (SIGINT o SIGBREAK) y no como entrada de teclado. De forma predeterminada, estas señales se pasan a todos los procesos de la consola que están asociados a la consola. (Los procesos desasociados no se ven afectados. Consulte [**Creación de una consola**](creation-of-a-console.md)). El sistema crea un nuevo subproceso en cada proceso de cliente para controlar el evento. El subproceso genera una excepción si se está depurando el proceso. El depurador puede controlar la excepción o continuar con la excepción sin controlar.

<kbd>Ctrl</kbd>+<kbd>Inter</kbd> se trata siempre como una señal, pero una aplicación puede cambiar el comportamiento predeterminado de <kbd>Ctrl</kbd>+<kbd>C</kbd> de dos maneras que impidan que se llame a las funciones del controlador:

- La función [**SetConsoleMode**](setconsolemode.md) puede deshabilitar el modo de entrada **ENABLE\_PROCESSED\_INPUT** para el búfer de entrada de una consola, por lo que Ctrl+C se indica como entrada del teclado en lugar de como una señal.
- Cuando se llama a [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) con los valores **NULL** y **TRUE** para sus parámetros, el proceso de llamada omite las señales de Ctrl+C. El procesamiento normal de Ctrl+C se restaura llamando a **SetConsoleCtrlHandler** con los valores **NULL** y **FALSE**. Los procesos secundarios heredan este atributo de omitir o no omitir las señales de Ctrl+C, pero puede habilitarse o deshabilitarse en cualquier proceso sin que ello afecte a los procesos existentes.

Para obtener más información sobre cómo se procesan estas señales, incluidos los tiempos de espera, vea la documentación de devolución de llamada de [**Rutina del controlador**](handlerroutine.md).
