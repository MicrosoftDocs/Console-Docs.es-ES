---
title: Estructura de CONSOLE_SCREEN_BUFFER_INFOEX
description: Vea información de referencia sobre la estructura de CONSOLE_SCREEN_BUFFER_INFOEX, que contiene información extendida sobre un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFOEX
- wincon/CONSOLE_SCREEN_BUFFER_INFOEX
- CONSOLE_SCREEN_BUFFER_INFOEX
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFOEX
- wincon/PCONSOLE_SCREEN_BUFFER_INFOEX
- PCONSOLE_SCREEN_BUFFER_INFOEX
MS-HAID:
- base.console\_screen\_buffer\_infoex
- consoles.console\_screen\_buffer\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6ed40df3-063d-41c9-8637-510c95104603
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFOEX
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 010120f2d925727e37bd72905bab4536db073371
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060829"
---
# <a name="console_screen_buffer_infoex-structure"></a>\_ \_ Estructura INFOEX del búfer de pantalla de la consola \_


Contiene información extendida sobre un búfer de pantalla de la consola.

<a name="syntax"></a>Sintaxis
------

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

<a name="members"></a>Miembros
-------

**cbSize**  
Tamaño de esta estructura, en bytes.

**dwSize**  
Una estructura de [**coordenadas**](coord-str.md) que contiene el tamaño del búfer de pantalla de la consola, en columnas y filas de caracteres.

**dwCursorPosition**  
Una estructura de [**coordenadas**](coord-str.md) que contiene las coordenadas de columna y fila del cursor en el búfer de pantalla de la consola.

**wAttributes**  
Los atributos de los caracteres escritos en un búfer de pantalla por las funciones [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) y [**WriteConsole**](writeconsole.md) , o bien se repiten en un búfer de pantalla mediante las funciones [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**ReadConsole**](readconsole.md) . Para obtener más información, vea [atributos de caracteres](console-screen-buffers.md#_win32_font_attributes).

**srWindow**  
[**Pequeña estructura \_ Rect**](small-rect-str.md) que contiene las coordenadas del búfer de pantalla de la consola de las esquinas superior izquierda e inferior derecha de la ventana de presentación.

**dwMaximumWindowSize**  
Una estructura de [**coordenadas**](coord-str.md) que contiene el tamaño máximo de la ventana de la consola, en columnas y filas de caracteres, según el tamaño del búfer de pantalla actual y la fuente y el tamaño de la pantalla.

**wPopupAttributes**  
El atributo Fill para los elementos emergentes de la consola.

**bFullscreenSupported**  
Si este miembro es TRUE, se admite el modo de pantalla completa; de lo contrario, no es.

**ColorTable**  
Una matriz de valores [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) que describen la configuración de color de la consola.

<a name="requirements"></a>Requisitos
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Cliente mínimo compatible</p></td>
<td><p>Windows Vista [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="even">
<td><p>Servidor mínimo compatible</p></td>
<td><p>Windows Server 2008 [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="odd">
<td><p>Encabezado</p></td>
<td>ConsoleApi2. h (a través de winCon. h, include Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vea también


[**COORDS**](coord-str.md)

[**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md)

[**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md)

[**PEQUEÑO \_ rectángulo**](small-rect-str.md)

 

 




