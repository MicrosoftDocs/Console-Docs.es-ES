---
title: Estructura de CONSOLE_SCREEN_BUFFER_INFO
description: Vea información de referencia sobre la estructura de CONSOLE_SCREEN_BUFFER_INFO, que contiene información sobre un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFO
- wincon/CONSOLE_SCREEN_BUFFER_INFO
- CONSOLE_SCREEN_BUFFER_INFO
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFO
- wincon/PCONSOLE_SCREEN_BUFFER_INFO
- PCONSOLE_SCREEN_BUFFER_INFO
MS-HAID:
- '\_win32\_console\_screen\_buffer\_info\_str'
- base.console\_screen\_buffer\_info\_str
- consoles.console\_screen\_buffer\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 586b3e0f-2f6b-4a03-b8e4-602a892be56d
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8b3a739a9f66e25687b60a3450c9381822c16e53
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039183"
---
# <a name="console_screen_buffer_info-structure"></a>\_Estructura de \_ información de búfer de pantalla de la consola \_

Contiene información sobre un búfer de pantalla de la consola.

## <a name="syntax"></a>Sintaxis

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFO {
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
} CONSOLE_SCREEN_BUFFER_INFO;
```

## <a name="members"></a>Miembros

**dwSize**  
Una estructura de [**coordenadas**](coord-str.md) que contiene el tamaño del búfer de pantalla de la consola, en columnas y filas de caracteres.

**dwCursorPosition**  
Una estructura de [**coordenadas**](coord-str.md) que contiene las coordenadas de columna y fila del cursor en el búfer de pantalla de la consola.

**wAttributes**  
Los atributos de los caracteres escritos en un búfer de pantalla por las funciones [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) y [**WriteConsole**](writeconsole.md) , o bien se repiten en un búfer de pantalla mediante las funciones [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**ReadConsole**](readconsole.md) . Para obtener más información, vea [atributos de caracteres](console-screen-buffers.md#character-attributes).

**srWindow**  
[**Pequeña estructura \_ Rect**](small-rect-str.md) que contiene las coordenadas del búfer de pantalla de la consola de las esquinas superior izquierda e inferior derecha de la ventana de presentación.

**dwMaximumWindowSize**  
Una estructura de [**coordenadas**](coord-str.md) que contiene el tamaño máximo de la ventana de la consola, en columnas y filas de caracteres, según el tamaño del búfer de pantalla actual y la fuente y el tamaño de la pantalla.

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | ConsoleApi2. h (a través de WinCon. h, include Windows. h) |

## <a name="see-also"></a>Consulte también

[**COORDS**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**PEQUEÑO \_ rectángulo**](small-rect-str.md)

[**WriteConsole**](writeconsole.md)

[**Escritura**](https://msdn.microsoft.com/library/windows/desktop/aa365747)
