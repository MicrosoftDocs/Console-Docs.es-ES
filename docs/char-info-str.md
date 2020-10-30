---
title: Estructura de CHAR_INFO
description: Especifica un carácter Unicode o ANSI y sus atributos. Las funciones de consola utilizan esta estructura para leer y escribir en un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/CHAR_INFO
- wincon/CHAR_INFO
- CHAR_INFO
- wincontypes/PCHAR_INFO
- wincon/PCHAR_INFO
- PCHAR_INFO
MS-HAID:
- '\_win32\_char\_info\_str'
- base.char\_info\_str
- consoles.char\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5574a862-b262-41af-8862-e9837c5c7b5f
topic_type:
- apiref
api_name:
- CHAR_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: b07938d6ac58744533711c91a04b1a0188f7daf6
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037383"
---
# <a name="char_info-structure"></a>\_Estructura char info

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Especifica un carácter Unicode o ANSI y sus atributos. Las funciones de consola utilizan esta estructura para leer y escribir en un búfer de pantalla de la consola.

## <a name="syntax"></a>Sintaxis

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

## <a name="members"></a>Miembros

**Char**  
Unión de los siguientes miembros.

**UnicodeChar**  
Carácter Unicode de una celda de carácter de búfer de pantalla.

**AsciiChar**  
Carácter ANSI de una celda de carácter de búfer de pantalla.

**Atributos**  
Atributos de carácter. Este miembro puede ser cero o cualquier combinación de los valores siguientes.

| Valor | Significado |
|-|-|
| **FOREGROUND_BLUE**`0x0001` | El color del texto contiene el azul. |
| **FOREGROUND_GREEN**`0x0002` | El color del texto contiene verde. |
| **FOREGROUND_RED**`0x0004` | El color del texto contiene rojo. |
| **FOREGROUND_INTENSITY**`0x0008` | El color del texto se intensifica. |
| **BACKGROUND_BLUE**`0x0010` | El color de fondo contiene el azul. |
| **BACKGROUND_GREEN**`0x0020` | El color de fondo contiene verde. |
| **BACKGROUND_RED**`0x0040` | El color de fondo contiene rojo. |
| **BACKGROUND_INTENSITY**`0x0080` | Se intensifica el color de fondo. |
| **COMMON_LVB_LEADING_BYTE**`0x0100` | Byte inicial. |
| **COMMON_LVB_TRAILING_BYTE**`0x0200` | Byte final. |
| **COMMON_LVB_GRID_HORIZONTAL**`0x0400` | Horizontal superior. |
| **COMMON_LVB_GRID_LVERTICAL**`0x0800` | Vertical izquierda. |
| **COMMON_LVB_GRID_RVERTICAL**`0x1000` | Vertical derecha. |
| **COMMON_LVB_REVERSE_VIDEO**`0x4000` | Atributo de primer plano y fondo inverso. |
| **COMMON_LVB_UNDERSCORE**`0x8000` | Subrayado. |

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | WinCon. h (incluir Windows. h) |

## <a name="see-also"></a>Consulte también

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)
