---
title: Estructura de CONSOLE_FONT_INFOEX
description: Vea la información de referencia sobre la estructura de CONSOLE_FONT_INFOEX, que contiene información extendida para una fuente de consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/CONSOLE_FONT_INFOEX
- wincon/CONSOLE_FONT_INFOEX
- CONSOLE_FONT_INFOEX
- consoleapi3/PCONSOLE_FONT_INFOEX
- wincon/PCONSOLE_FONT_INFOEX
- PCONSOLE_FONT_INFOEX
MS-HAID:
- base.console\_font\_infoex
- consoles.console\_font\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e9a087e1-264d-4d48-8adb-771a0e35b511
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFOEX
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: ef89d1bf47a4153d44140d3f9f4845bb7496680e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039263"
---
# <a name="console_font_infoex-structure"></a>\_ \_ Estructura INFOEX de la consola

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contiene información extendida para una fuente de consola.

## <a name="syntax"></a>Sintaxis

```C
typedef struct _CONSOLE_FONT_INFOEX {
  ULONG cbSize;
  DWORD nFont;
  COORD dwFontSize;
  UINT  FontFamily;
  UINT  FontWeight;
  WCHAR FaceName[LF_FACESIZE];
} CONSOLE_FONT_INFOEX, *PCONSOLE_FONT_INFOEX;
```

## <a name="members"></a>Miembros

**cbSize**  
Tamaño de esta estructura, en bytes. Este miembro debe establecerse en `sizeof(CONSOLE_FONT_INFOEX)` antes de llamar a [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) o se producirá un error.

**nFont**  
Índice de la fuente en la tabla de fuentes de la consola del sistema.

**dwFontSize**  
Una estructura de [**coordenadas**](coord-str.md) que contiene el ancho y el alto de cada carácter de la fuente, en unidades lógicas. El miembro **X** contiene el ancho, mientras que el miembro **Y** contiene el alto.

**FontFamily**  
El paso y la familia de la fuente. Para obtener información sobre los valores posibles para este miembro, vea la descripción del miembro **tmPitchAndFamily** de la estructura [**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132) .

**FontWeight**  
Espesor de la fuente. El peso puede oscilar entre 100 y 1000, en múltiplos de 100. Por ejemplo, el peso normal es 400, mientras que 700 está en negrita.

**FaceName**  
Nombre del tipo de letra (por ejemplo, Courier o Arial).

## <a name="remarks"></a>Comentarios

Para obtener el tamaño de la fuente, pase el índice de fuente a la función [**GetConsoleFontSize**](getconsolefontsize.md) .

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows Vista \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows Server 2008 \[\] |
| Encabezado | WinCon. h (incluir Windows. h) |

## <a name="see-also"></a>Consulte también

[**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md)
