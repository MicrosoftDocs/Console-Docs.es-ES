---
title: Estructura de CONSOLE_FONT_INFO
description: Vea la información de referencia sobre la estructura de CONSOLE_FONT_INFO, que contiene el índice y el tamaño de una fuente de consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/CONSOLE_FONT_INFO
- wincon/CONSOLE_FONT_INFO
- CONSOLE_FONT_INFO
- wincontypes/PCONSOLE_FONT_INFO
- wincon/PCONSOLE_FONT_INFO
- PCONSOLE_FONT_INFO
MS-HAID:
- '\_win32\_console\_font\_info\_str'
- base.console\_font\_info\_str
- consoles.console\_font\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 380b8183-1964-46f2-a511-01f39f21f5c5
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 6c437e626ed6d207da4672a3a5ea60c2ea0ee008
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037143"
---
# <a name="console_font_info-structure"></a>Estructura de información de \_ fuente de consola \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contiene información de una fuente de consola.

## <a name="syntax"></a>Sintaxis

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

## <a name="members"></a>Miembros

**nFont**  
Índice de la fuente en la tabla de fuentes de la consola del sistema.

**dwFontSize**  
Una estructura de [**coordenadas**](coord-str.md) que contiene el ancho y el alto de cada carácter de la fuente, en unidades lógicas. El miembro **X** contiene el ancho, mientras que el miembro **Y** contiene el alto.

## <a name="remarks"></a>Comentarios

Para obtener el tamaño de la fuente, pase el índice de fuente a la función [**GetConsoleFontSize**](getconsolefontsize.md) .

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows XP \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows Server 2003 \[\] |
| Encabezado | WinCon. h (incluir Windows. h) |

## <a name="see-also"></a>Consulte también

[**COORDS**](coord-str.md)

[**GetCurrentConsoleFont**](getcurrentconsolefont.md)
