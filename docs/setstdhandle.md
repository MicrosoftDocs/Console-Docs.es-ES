---
title: SetStdHandle función)
description: Establece el identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 6ab17a2162d31c956ec64dbb33696c20ae085298
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061100"
---
# <a name="setstdhandle-function"></a>SetStdHandle función)


Establece el identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).

<a name="syntax"></a>Sintaxis
------

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

<a name="parameters"></a>Parámetros
----------

*nStdHandle* \[ de\]  
El dispositivo estándar para el que se establecerá el identificador. Este parámetro puede ser uno de los valores siguientes.

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
<td><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</td>
<td><p>El dispositivo de entrada estándar.</p></td>
</tr>
<tr class="even">
<td><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</td>
<td><p>El dispositivo de salida estándar.</p></td>
</tr>
<tr class="odd">
<td><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</td>
<td><p>El dispositivo de error estándar.</p></td>
</tr>
</tbody>
</table>

 

*hHandle* \[ de\]  
Identificador del dispositivo estándar.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

Es posible que los identificadores estándar de un proceso se hayan Redirigido mediante una llamada a **SetStdHandle**, en cuyo caso [**GetStdHandle**](getstdhandle.md) devolverá el identificador redirigido. Si se han redirigido los identificadores estándar, puede especificar el valor de CONIN $ en una llamada a la función [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) para obtener un identificador para el búfer de entrada de la consola. De forma similar, puede especificar el valor de CONOUT $ para obtener un identificador para el búfer de pantalla activo de la consola.

<a name="examples"></a>Ejemplos
--------

Para obtener un ejemplo, consulte [creación de un proceso secundario con entrada y salida redirigidas](https://msdn.microsoft.com/library/windows/desktop/ms682499).

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
<td>ProcessEnv. h (a través de Winbase. h, include Windows. h)</td>
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

[Identificadores de consola](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetStdHandle**](getstdhandle.md)

 

 




