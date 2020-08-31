---
title: GetNumberOfConsoleMouseButtons función)
description: Recupera el número de botones del mouse que usa la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetNumberOfConsoleMouseButtons
- wincon/GetNumberOfConsoleMouseButtons
- GetNumberOfConsoleMouseButtons
MS-HAID:
- '\_win32\_getnumberofconsolemousebuttons'
- base.getnumberofconsolemousebuttons
- consoles.getnumberofconsolemousebuttons
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2
topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 67089bd301ac2632f9a99ca24cc2042789f6a3e8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061028"
---
# <a name="getnumberofconsolemousebuttons-function"></a>GetNumberOfConsoleMouseButtons función)


Recupera el número de botones del mouse que usa la consola actual.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

<a name="parameters"></a>Parámetros
----------

*lpNumberOfMouseButtons* \[ enuncia\]  
Puntero a una variable que recibe el número de botones del mouse.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

Cuando una consola recibe la entrada del mouse, una estructura de [** \_ registro de entrada**](input-record-str.md) que contiene una estructura de [** \_ \_ registro de eventos del mouse**](mouse-event-record-str.md) se coloca en el búfer de entrada de la consola. El miembro **dwButtonState** del ** \_ \_ registro de eventos del mouse** tiene un bit que indica el estado de cada botón del mouse. El bit es 1 si el botón está presionado y 0 si el botón está activo. Para determinar el número de bits que son significativos, use **GetNumberOfConsoleMouseButtons**.

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

[Búfer de entrada de la consola](console-input-buffer.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**registro de entrada \_**](input-record-str.md)

[**\_registro de eventos del mouse \_**](mouse-event-record-str.md)

 

 




