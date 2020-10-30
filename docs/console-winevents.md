---
title: WinEvents de consola
description: Las constantes de eventos siguientes se usan en el parámetro Event de la función de devolución de llamada WinEventProc. Para obtener más información, vea WinEvents.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- winuser/EVENT_CONSOLE_CARET
- winuser/EVENT_CONSOLE_END_APPLICATION
- winuser/EVENT_CONSOLE_LAYOUT
- winuser/EVENT_CONSOLE_START_APPLICATION
- winuser/EVENT_CONSOLE_UPDATE_REGION
- winuser/EVENT_CONSOLE_UPDATE_SCROLL
- winuser/EVENT_CONSOLE_UPDATE_SIMPLE
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
MS-HAID:
- '\_win32\_console\_winevents'
- base.console\_winevents
- consoles.console\_winevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b7078b2d-5508-4e42-bac2-34b70f1856e2
topic_type:
- apiref
api_name:
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
api_location:
- Winuser.h
api_type:
- HeaderDef
ms.openlocfilehash: 2c5d641140316089b38b836bf3fba7534ccd5600
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038333"
---
# <a name="console-winevents"></a>WinEvents de consola

> [!IMPORTANT]
> WinEvents forman parte de **[Microsoft Active Accessibility](https://docs.microsoft.com/windows/win32/winauto/microsoft-active-accessibility)** Framework heredado. No se recomienda el desarrollo mediante estos eventos en favor del marco de **[automatización](https://docs.microsoft.com/windows/win32/winauto/entry-uiauto-win32)** de la interfaz de usuario de Microsoft, que proporciona un conjunto de interfaces más sólido y completo para que las aplicaciones de accesibilidad y automatización interactúen con la consola. 

> [!WARNING]
> El registro de estos eventos es una actividad global y afecta significativamente al rendimiento de todas las aplicaciones de línea de comandos que se ejecutan en un sistema al mismo tiempo, incluidos los servicios y las utilidades en segundo plano. El marco de automatización de la **interfaz de usuario de Microsoft** es específico de la sesión de consola y supera esta limitación.

Las constantes de eventos siguientes se usan en el parámetro *Event* de la función de devolución de llamada [*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) . Para obtener más información, vea [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).

| Constante o valor | Description |
|-|-|
| **EVENT_CONSOLE_CARET** 0x4001 | Se ha cambiado el símbolo de intercalación de la consola. El parámetro *idObject* es uno o varios de los siguientes valores: **CONSOLE_CARET_SELECTION** o **CONSOLE_CARET_VISIBLE** . El parámetro *idChild* es una estructura de **[coordenadas](coord-str.md)** que especifica la posición actual del cursor. |
| **EVENT_CONSOLE_END_APPLICATION** 0x4007 | Se ha salido de un proceso de consola. El parámetro *idObject* contiene el identificador de proceso del proceso terminado. |
| **EVENT_CONSOLE_LAYOUT** 0x4005 | El diseño de la consola ha cambiado. |
| **EVENT_CONSOLE_START_APPLICATION** 0x4006 | Se ha iniciado un nuevo proceso de consola. El parámetro *idObject* contiene el identificador de proceso del proceso recién creado. Si la aplicación es una aplicación de 16 bits, el parámetro *idChild* es **CONSOLE_APPLICATION_16BIT** y *idObject* es el identificador de proceso de la sesión de NTVDM asociada a la consola. |
|**EVENT_CONSOLE_UPDATE_REGION** 0x4002 | Ha cambiado más de un carácter. El parámetro  *idObject* es una estructura de **[coordenadas](coord-str.md)** que especifica el inicio de la región modificada. El parámetro *idChild* es una estructura de **coordenadas** que especifica el final de la región modificada. |
|**EVENT_CONSOLE_UPDATE_SCROLL** 0x4004 | La consola se ha desplazado. El parámetro *idObject* es la distancia horizontal que se ha desplazado la consola. El parámetro *idChild* es la distancia vertical que se ha desplazado la consola. |
|**EVENT_CONSOLE_UPDATE_SIMPLE** 0x4003 | Ha cambiado un solo carácter. El parámetro *idObject* es una estructura de **[coordenadas](coord-str.md)** que especifica el carácter que ha cambiado. El parámetro *idChild* especifica el carácter de la palabra baja y los **[atributos de carácter](console-screen-buffers.md#character-attributes)** de la palabra alta. |

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | Winuser. h |
