---
title: FlushConsoleInputBuffer función)
description: Vacía el búfer de entrada de la consola. Se descartan todos los registros de entrada que se encuentran actualmente en el búfer de entrada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/FlushConsoleInputBuffer
- wincon/FlushConsoleInputBuffer
- FlushConsoleInputBuffer
MS-HAID:
- '\_win32\_flushconsoleinputbuffer'
- base.flushconsoleinputbuffer
- consoles.flushconsoleinputbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6f7832d6-1fb2-4ca8-bd07-43123c990851
topic_type:
- apiref
api_name:
- FlushConsoleInputBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: dd184e1fc1f788912be00e9270ccb239c20b8ce8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060744"
---
# <a name="flushconsoleinputbuffer-function"></a>FlushConsoleInputBuffer función)


Vacía el búfer de entrada de la consola. Se descartan todos los registros de entrada que se encuentran actualmente en el búfer de entrada.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI FlushConsoleInputBuffer(
  _In_ HANDLE hConsoleInput
);
```

<a name="parameters"></a>Parámetros
----------

*hConsoleInput* \[ de\]  
Identificador para el búfer de entrada de la consola. El identificador debe tener el derecho de acceso de ** \_ escritura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

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

[Funciones de entrada de la consola de bajo nivel](low-level-console-input-functions.md)

[**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

 

 




