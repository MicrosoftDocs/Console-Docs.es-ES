---
title: Estructura de CONSOLE_CURSOR_INFO
description: Contiene la información de tamaño y visibilidad sobre el cursor de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/CONSOLE_CURSOR_INFO
- wincon/CONSOLE_CURSOR_INFO
- CONSOLE_CURSOR_INFO
- wincontypes/PCONSOLE_CURSOR_INFO
- wincon/PCONSOLE_CURSOR_INFO
- PCONSOLE_CURSOR_INFO
MS-HAID:
- '\_win32\_console\_cursor\_info\_str'
- base.console\_cursor\_info\_str
- consoles.console\_cursor\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0e71ce8c-e008-4bd7-922e-c44484b425ef
topic_type:
- apiref
api_name:
- CONSOLE_CURSOR_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: cdfcc00035738aa468d9795e4f6d32a54b96e1d0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037020"
---
# <a name="console_cursor_info-structure"></a>Estructura de información del \_ cursor de la consola \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contiene información sobre el cursor de la consola.

## <a name="syntax"></a>Sintaxis

```C
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

## <a name="members"></a>Miembros

**dwSize**  
Porcentaje de la celda de caracteres que rellena el cursor. Este valor se encuentra entre 1 y 100. La apariencia del cursor varía, desde que se rellena completamente la celda hasta que se muestra como una línea horizontal en la parte inferior de la celda.

> [!NOTE]
>Aunque el valor de **dwSize** está normalmente entre 1 y 100, en algunas circunstancias se puede devolver un valor fuera de ese intervalo. Por ejemplo, si **CursorSize** se establece en 0 en el registro, el valor de **dwSize** devuelto sería 0.

 **bVisible**  
Visibilidad del cursor. Si el cursor está visible, este miembro es **true** .

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | WinCon. h (incluir Windows. h) |

## <a name="see-also"></a>Consulte también

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**SetConsoleCursorInfo**](setconsolecursorinfo.md)
