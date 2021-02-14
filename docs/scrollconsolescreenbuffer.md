---
title: ScrollConsoleScreenBuffer función)
description: Vea la información de referencia sobre la función ScrollConsoleScreenBuffer, que mueve un bloque de datos en un búfer de pantalla.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/ScrollConsoleScreenBuffer
- wincon/ScrollConsoleScreenBuffer
- ScrollConsoleScreenBuffer
- consoleapi2/ScrollConsoleScreenBufferA
- wincon/ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferA
- consoleapi2/ScrollConsoleScreenBufferW
- wincon/ScrollConsoleScreenBufferW
- ScrollConsoleScreenBufferW
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d78bf4c9-2314-466c-b617-619259c824b5
topic_type:
- apiref
api_name:
- ScrollConsoleScreenBuffer
- ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 1bf009a91063c12ad14604349d68ca0de1d8eaa1
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358675"
---
# <a name="scrollconsolescreenbuffer-function"></a>ScrollConsoleScreenBuffer función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Mueve un bloque de datos en un búfer de pantalla. Los efectos del movimiento se pueden limitar especificando un rectángulo de recorte, por lo que el contenido del búfer de pantalla de la consola fuera del rectángulo de recorte no se modifica.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI ScrollConsoleScreenBuffer(
  _In_           HANDLE     hConsoleOutput,
  _In_     const SMALL_RECT *lpScrollRectangle,
  _In_opt_ const SMALL_RECT *lpClipRectangle,
  _In_           COORD      dwDestinationOrigin,
  _In_     const CHAR_INFO  *lpFill
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[in\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener derecho de acceso de **GENERIC\_READ**. Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).

*lpScrollRectangle* \[ de\]  
Puntero a una [**pequeña estructura \_ Rect**](small-rect-str.md) cuyos miembros especifican las coordenadas superior izquierda e inferior derecha del rectángulo del búfer de pantalla de la consola que se va a desplace.

*lpClipRectangle* \[ en, opcional\]  
Puntero a una [**pequeña estructura \_ Rect**](small-rect-str.md) cuyos miembros especifican las coordenadas superior izquierda e inferior derecha del rectángulo del búfer de pantalla de la consola que se ve afectado por el desplazamiento. Este puntero puede ser **null**.

*dwDestinationOrigin* \[ de\]  
Estructura de [**coordenadas**](coord-str.md) que especifica la esquina superior izquierda de la nueva ubicación del contenido de *lpScrollRectangle* , en caracteres.

*lpFill* \[ de\]  
Puntero a una estructura [**de \_ información**](char-info-str.md) de caracteres que especifica los atributos de carácter y color que se van a usar para rellenar las celdas dentro de la intersección de *lpScrollRectangle* y *lpClipRectangle* que se dejaron vacíos como resultado del movimiento.

## <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Comentarios

**ScrollConsoleScreenBuffer** copia el contenido de una región rectangular de un búfer de pantalla, especificado por el parámetro *lpScrollRectangle* , en otra área del búfer de pantalla de la consola. El rectángulo de destino tiene las mismas dimensiones que el rectángulo *lpScrollRectangle* con la esquina superior izquierda en las coordenadas especificadas por el parámetro *dwDestinationOrigin* . Las partes de *lpScrollRectangle* que no se superponen con el rectángulo de destino se rellenan con los atributos de carácter y color especificados por el parámetro *lpFill* .

El rectángulo de recorte se aplica a los cambios realizados en el rectángulo *lpScrollRectangle* y el rectángulo de destino. Por ejemplo, si el rectángulo de recorte no incluye una región que se habría rellenado con el contenido de *lpFill*, el contenido original de la región quedará sin cambios.

Si las regiones de desplazamiento o de destino se extienden más allá de las dimensiones del búfer de pantalla de la consola, se recortan. Por ejemplo, si *lpScrollRectangle* es la región contenida en (0,0) y (19, 19) y *dwDestinationOrigin* es (10, 15), el rectángulo de destino es la región contenida en (10, 15) y (29, 34). Sin embargo, si el búfer de la pantalla de la consola tiene 50 caracteres de ancho y 30 caracteres de alto, el rectángulo de destino se recorta a (10, 15) y (29, 29). Los cambios en el búfer de pantalla de la consola también se recortan según *lpClipRectangle*, si el parámetro especifica una estructura [**\_ Rect pequeña**](small-rect-str.md) . Si el rectángulo de recorte se especifica como (0,0) y (49, 19), solo se realizan los cambios que se producen en esa región del búfer de pantalla de la consola.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> No se recomienda esta API y no tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente. El uso se puede aproximar con **[márgenes de desplazamiento](console-virtual-terminal-sequences.md#scrolling-margins)** para corregir un área de la pantalla, **[colocar el cursor](console-virtual-terminal-sequences.md#cursor-positioning)** para establecer la posición activa fuera de la región y nuevas líneas para forzar el movimiento del texto. El espacio restante se puede rellenar moviendo el cursor, **[estableciendo los atributos gráficos](console-virtual-terminal-sequences.md#text-formatting)** y escribiendo texto normal.

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Professional |
| Servidor mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Server |
| Encabezado | ConsoleApi2. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32.lib |
| Archivo DLL | Kernel32.dll |
| Nombres Unicode y ANSI | **ScrollConsoleScreenBufferW** (Unicode) y **ScrollConsoleScreenBufferA** (ANSI) |

## <a name="see-also"></a>Consulte también

[**información de carácter \_**](char-info-str.md)

[Funciones de la consola](console-functions.md)

[**COORDS**](coord-str.md)

[Desplazarse por el búfer de pantalla](scrolling-the-screen-buffer.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[**PEQUEÑO \_ rectángulo**](small-rect-str.md)