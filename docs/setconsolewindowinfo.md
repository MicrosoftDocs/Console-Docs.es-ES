---
title: SetConsoleWindowInfo función)
description: Establece el tamaño y la posición actuales de la ventana de un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleWindowInfo
- wincon/SetConsoleWindowInfo
- SetConsoleWindowInfo
MS-HAID:
- '\_win32\_setconsolewindowinfo'
- base.setconsolewindowinfo
- consoles.setconsolewindowinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad16a8fe-ca91-41d6-93b1-8cce6d54b1da
topic_type:
- apiref
api_name:
- SetConsoleWindowInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: ae09434a1fc67902d2160f4e66890f4392eac3f8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060816"
---
# <a name="setconsolewindowinfo-function"></a>SetConsoleWindowInfo función)


Establece el tamaño y la posición actuales de la ventana de un búfer de pantalla de la consola.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI SetConsoleWindowInfo(
  _In_       HANDLE     hConsoleOutput,
  _In_       BOOL       bAbsolute,
  _In_ const SMALL_RECT *lpConsoleWindow
);
```

<a name="parameters"></a>Parámetros
----------

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de ** \_ lectura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*bAbsolute* \[ de\]  
Si este parámetro es **true**, las coordenadas especifican las nuevas esquinas superior izquierda e inferior derecha de la ventana. Si es **false**, las coordenadas son relativas a las coordenadas de la esquina de la ventana actual.

*lpConsoleWindow* \[ de\]  
Puntero a una [**pequeña estructura \_ Rect**](small-rect-str.md) que especifica las nuevas esquinas superior izquierda e inferior derecha de la ventana.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

Se produce un error en la función si el rectángulo de la ventana especificado se extiende más allá de los límites del búfer de pantalla de la consola. Esto significa que los miembros **superior** e **izquierdo** del rectángulo *lpConsoleWindow* (o las coordenadas superior e izquierda calculadas, si *bAbsolute* es false) no pueden ser menores que cero. Del mismo modo, los miembros **inferior** y **derecho** (o las coordenadas inferior y derecha calculadas) no pueden ser mayores que (alto del búfer de pantalla – 1) y (ancho del búfer de pantalla – 1), respectivamente. También se produce un error en la función si el miembro **derecho** (o la coordenada derecha calculada) es menor o igual que el miembro **izquierdo** (o la coordenada izquierda calculada) o si el miembro **inferior** (o la coordenada inferior calculada) es menor o igual que el miembro **superior** (o la coordenada superior calculada).

En el caso de las consolas de más de un búfer de pantalla, el cambio de la ubicación de la ventana para un búfer de pantalla no afecta a las ubicaciones de ventana de los otros búferes de pantalla.

Para determinar el tamaño y la posición actuales de la ventana de un búfer de pantalla, utilice la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) . Esta función también devuelve el tamaño máximo de la ventana, dado el tamaño actual del búfer de pantalla, el tamaño de fuente actual y el tamaño de la pantalla. La función [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) devuelve el tamaño máximo de la ventana a partir de la fuente actual y los tamaños de pantalla, pero no tiene en cuenta el tamaño del búfer de pantalla de la consola.

**SetConsoleWindowInfo** se puede usar para desplazarse por el contenido del búfer de pantalla de la consola desplazando la posición del rectángulo de la ventana sin cambiar su tamaño.

<a name="examples"></a>Ejemplos
--------

Para obtener un ejemplo, vea [desplazarse por la ventana de un búfer de pantalla](scrolling-a-screen-buffer-s-window.md).

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

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[Desplazarse por el búfer de pantalla](scrolling-the-screen-buffer.md)

[**PEQUEÑO \_ rectángulo**](small-rect-str.md)

 

 




