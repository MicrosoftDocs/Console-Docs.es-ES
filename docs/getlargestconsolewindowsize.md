---
title: GetLargestConsoleWindowSize función)
description: Recupera el tamaño de la ventana de la consola más grande posible, en función de la fuente actual y el tamaño de la pantalla.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/GetLargestConsoleWindowSize
- wincon/GetLargestConsoleWindowSize
- GetLargestConsoleWindowSize
MS-HAID:
- '\_win32\_getlargestconsolewindowsize'
- base.getlargestconsolewindowsize
- consoles.getlargestconsolewindowsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3e5897f3-4987-4a82-ab19-06c0b231ba67
topic_type:
- apiref
api_name:
- GetLargestConsoleWindowSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: ddaa4716886fccaaa87e86362719020eb2408765
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037843"
---
# <a name="getlargestconsolewindowsize-function"></a>GetLargestConsoleWindowSize función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Recupera el tamaño de la ventana de la consola más grande posible, en función de la fuente actual y el tamaño de la pantalla.

## <a name="syntax"></a>Sintaxis

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es una estructura de [**coordenadas**](coord-str.md) que especifica el número de columnas de celda de caracteres (miembro **X** ) y las filas (miembro **y** ) de la ventana de la consola más grande posible. De lo contrario, los miembros de la estructura son cero.

Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

La función no tiene en cuenta el tamaño del búfer de pantalla de la consola, lo que significa que el tamaño de la ventana devuelto puede ser mayor que el tamaño del búfer de pantalla de la consola. La función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) se puede usar para determinar el tamaño máximo de la ventana de la consola, según el tamaño actual del búfer de pantalla, la fuente actual y el tamaño de presentación.

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | ConsoleApi2. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Consulte también

[Funciones de la consola](console-functions.md)

[**COORDS**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[Tamaño de búfer de ventana y pantalla](window-and-screen-buffer-size.md)
