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
ms.openlocfilehash: a16fb23d148f75480437211204a0fd7c1f161bfe
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357855"
---
# `CHAR\_INFO structure`

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
| **FOREGROUND_BLUE**`0x0001` | El color del texto contiene azul. |
| **FOREGROUND_GREEN**`0x0002` | El color del texto contiene verde. |
| **FOREGROUND_RED**`0x0004` | El color del texto contiene rojo. |
| **FOREGROUND_INTENSITY**`0x0008` | El color del texto se intensifica. |
| **BACKGROUND_BLUE**`0x0010` | El color de fondo contiene azul. |
| **BACKGROUND_GREEN**`0x0020` | El color de fondo contiene verde. |
| **BACKGROUND_RED**`0x0040` | El color de fondo contiene rojo. |
| **BACKGROUND_INTENSITY**`0x0080` | El color de fondo se intensifica. |
| **COMMON_LVB_LEADING_BYTE**`0x0100` | Byte inicial. |
| **COMMON_LVB_TRAILING_BYTE**`0x0200` | Byte final. |
| **COMMON_LVB_GRID_HORIZONTAL**`0x0400` | Horizontal superior. |
| **COMMON_LVB_GRID_LVERTICAL**`0x0800` | Vertical izquierda. |
| **COMMON_LVB_GRID_RVERTICAL**`0x1000` | Vertical derecha. |
| **COMMON_LVB_REVERSE_VIDEO**`0x4000` | Atributo de primer plano y fondo inverso. |
| **COMMON_LVB_UNDERSCORE**`0x8000` | Guion bajo. |

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Professional |
| Servidor mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Server |
| Encabezado | WinCon. h (incluir Windows. h) |

## <a name="see-also"></a>Consulte también

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)
