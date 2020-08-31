---
title: SetCurrentConsoleFontEx función)
description: Consulte la información de referencia sobre la función SetCurrentConsoleFontEx, que establece la información extendida sobre la fuente de consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/SetCurrentConsoleFontEx
- wincon/SetCurrentConsoleFontEx
- SetCurrentConsoleFontEx
MS-HAID:
- base.setcurrentconsolefontex
- consoles.setcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: fbc31e2a-31df-4e9e-9f61-35a4ff812f8f
topic_type:
- apiref
api_name:
- SetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 9d97383f40c38489ac3ea5e7c75386163b9d5d2d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060813"
---
# <a name="setcurrentconsolefontex-function"></a>SetCurrentConsoleFontEx función)


Establece la información extendida sobre la fuente de consola actual.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI SetCurrentConsoleFontEx(
  _In_ HANDLE               hConsoleOutput,
  _In_ BOOL                 bMaximumWindow,
  _In_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

<a name="parameters"></a>Parámetros
----------

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de ** \_ escritura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*bMaximumWindow* \[ de\]  
Si este parámetro es **true**, la información de fuente se establece para el tamaño máximo de la ventana. Si este parámetro es **false**, se establece la información de fuente para el tamaño de la ventana actual.

*lpConsoleCurrentFontEx* \[ de\]  
Puntero a una estructura [** \_ \_ INFOEX**](console-font-infoex.md) de la fuente de la consola que contiene la información de la fuente.

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
<td><p>Windows Vista [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="even">
<td><p>Servidor mínimo compatible</p></td>
<td><p>Windows Server 2008 [solo aplicaciones de escritorio]</p></td>
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

[**fuente de consola \_ \_ INFOEX**](console-font-infoex.md)

 

 




