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
ms.openlocfilehash: 086c09b00ba15ad3e1922655fbd9b5f39d872d41
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060649"
---
# <a name="getlargestconsolewindowsize-function"></a>GetLargestConsoleWindowSize función)


Recupera el tamaño de la ventana de la consola más grande posible, en función de la fuente actual y el tamaño de la pantalla.

<a name="syntax"></a>Sintaxis
------

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

<a name="parameters"></a>Parámetros
----------

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es una estructura de [**coordenadas**](coord-str.md) que especifica el número de columnas de celda de caracteres (miembro**X** ) y las filas (miembro**y** ) de la ventana de la consola más grande posible. De lo contrario, los miembros de la estructura son cero.

Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

La función no tiene en cuenta el tamaño del búfer de pantalla de la consola, lo que significa que el tamaño de la ventana devuelto puede ser mayor que el tamaño del búfer de pantalla de la consola. La función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) se puede usar para determinar el tamaño máximo de la ventana de la consola, según el tamaño actual del búfer de pantalla, la fuente actual y el tamaño de presentación.

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
<td><p>Windows 2000 Professional [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="even">
<td><p>Servidor mínimo compatible</p></td>
<td><p>Windows 2000 Server [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="odd">
<td><p>Encabezado</p></td>
<td>ConsoleApi2. h (a través de winCon. h, include Windows. h)</td>
</tr>
<tr class="even">
<td><p>Biblioteca</p></td>
<td>Kernel32. lib</td>
</tr>
<tr class="odd">
<td><p>Archivo DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vea también


[Funciones de la consola](console-functions.md)

[**COORDS**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[Tamaño de búfer de ventana y pantalla](window-and-screen-buffer-size.md)

 

 




