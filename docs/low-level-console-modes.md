---
title: Modos de consola de bajo nivel
description: Los tipos de eventos de entrada que se indican en el búfer de entrada de la consola dependen de los modos de entrada del mouse y de la ventana de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_low\_level\_console\_modes'
- base.low\_level\_console\_modes
- consoles.low\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 41bfdc51-27cb-4d5e-898c-507ffc8789b9
ms.openlocfilehash: 375b3b6eaef499324bdbde24ec973d91c50dda5b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060820"
---
# <a name="low-level-console-modes"></a>Modos de consola de bajo nivel


Los tipos de eventos de entrada que se indican en el búfer de entrada de la consola dependen de los modos de entrada del mouse y de la ventana de la consola. El modo de entrada procesado de la consola determina cómo controla el sistema la combinación de teclas CTRL + C. Para establecer o recuperar el estado de los modos de entrada de una consola, una aplicación puede especificar un identificador de búfer de entrada de la consola en una llamada a la función [**SetConsoleMode**](setconsolemode.md) o [**GetConsoleMode**](getconsolemode.md) . Los siguientes modos se usan con los identificadores de entrada de la consola.


| Mode                         | Descripción                                                                                                                                                                                                                                                                                                                                                                                           |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **HABILITAR \_ la \_ entrada del mouse**     | Controla si los eventos del mouse se muestran en el búfer de entrada. De forma predeterminada, la entrada de mouse está habilitada y la entrada de ventana está deshabilitada. Cambiar cualquiera de estos modos afecta solo a la entrada que se produce después de establecer el modo; los eventos de mouse o de ventana pendientes en el búfer de entrada no se vacían. El puntero del mouse se muestra independientemente del modo del mouse.                                                |
| **HABILITAR \_ entrada de ventana \_**    | Controla si se registran los eventos de cambio de tamaño del búfer en el búfer de entrada. De forma predeterminada, la entrada de mouse está habilitada y la entrada de ventana está deshabilitada. Cambiar cualquiera de estos modos afecta solo a la entrada que se produce después de establecer el modo; los eventos de mouse o de ventana pendientes en el búfer de entrada no se vacían. El puntero del mouse se muestra independientemente del modo del mouse.                                      |
| **HABILITAR \_ entrada procesada \_** | Controla el procesamiento de entradas de las aplicaciones mediante las funciones de e/s de la consola de alto nivel. Sin embargo, si está habilitado el modo de entrada procesado, la combinación de teclas CTRL + C no se muestra en el búfer de entrada de la consola. En su lugar, se pasa a la función de controlador de control adecuada. Para obtener más información sobre los controladores de control, vea [controladores de control de consola](console-control-handlers.md). |



Los modos de salida de un búfer de pantalla no afectan al comportamiento de las funciones de salida de bajo nivel.








