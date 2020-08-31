---
title: GetConsoleDisplayMode función)
description: Vea la información de referencia sobre la función GetConsoleDisplayMode, que recupera el modo de presentación de la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 76b3354ac9b44c36ec4cfe3d12257583d10f2ee2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060712"
---
# <a name="getconsoledisplaymode-function"></a>GetConsoleDisplayMode función)


Recupera el modo de presentación de la consola actual.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

<a name="parameters"></a>Parámetros
----------

*lpModeFlags* \[ enuncia\]  
Modo de presentación de la consola. Este parámetro puede ser uno o varios de los valores siguientes.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Valor</th>
<th>Significado</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="CONSOLE_FULLSCREEN"></span><span id="console_fullscreen"></span>
<strong>CONSOLE_FULLSCREEN</strong> 1</td>
<td><p>Consola de pantalla completa. La consola está en este modo en cuanto se maximiza la ventana. En este momento, se puede producir un error en la transición al modo de pantalla completa.</p></td>
</tr>
<tr class="even">
<td><span id="CONSOLE_FULLSCREEN_HARDWARE"></span><span id="console_fullscreen_hardware"></span>
<strong>CONSOLE_FULLSCREEN_HARDWARE</strong> 2</td>
<td><p>Consola de pantalla completa que se comunica directamente con el hardware de vídeo. Este modo se establece después de que la consola esté en modo de <strong>CONSOLE_FULLSCREEN</strong> para indicar que se ha completado la transición al modo de pantalla completa.</p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

Para compilar una aplicación que usa esta función, defina ** \_ Win32 \_ WinNT** como 0x0500 o posterior. Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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
<td><p>Windows XP [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="even">
<td><p>Servidor mínimo compatible</p></td>
<td><p>Windows Server 2003 [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="odd">
<td><p>Encabezado</p></td>
<td>ConsoleApi3. h (a través de winCon. h, include Windows. h)</td>
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

[Modos de consola](console-modes.md)

[**SetConsoleDisplayMode**](setconsoledisplaymode.md)

 

 




