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
# <a name="high-level-console-modes"></a>Modos de consola de High-Level

El comportamiento de las funciones de la consola de alto nivel se ve afectado por los modos de entrada y salida de la consola. Todos los siguientes modos de entrada de la consola están habilitados para el búfer de entrada de la consola cuando se crea una consola:

- Modo de entrada de línea
- Modo de entrada procesado
- Modo de entrada de eco

Los dos modos de salida de la consola siguientes están habilitados para un búfer de pantalla de la consola cuando se crea:

- Modo de salida procesado
- Encapsulado en modo de salida EOL

Los tres modos de entrada, junto con el modo de salida procesado, están diseñados para funcionar juntos. Es mejor habilitar o deshabilitar todos estos modos como un grupo. Cuando todos están habilitados, se dice que la aplicación está en modo "cocido", lo que significa que la mayor parte del procesamiento se controla para la aplicación. Cuando se deshabilitan todos, la aplicación está en modo "sin procesar", lo que significa que la entrada no se filtra y se deja cualquier procesamiento en la aplicación.

Una aplicación puede usar la función [**GetConsoleMode**](getconsolemode.md) para determinar el modo actual del búfer de entrada o el búfer de pantalla de una consola. Puede habilitar o deshabilitar cualquiera de estos modos con los siguientes valores en la función [**SetConsoleMode**](setconsolemode.md) . Tenga en cuenta que al establecer el modo de salida de un búfer de pantalla no se ve afectado el modo de salida de otros búferes de pantalla.

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]
