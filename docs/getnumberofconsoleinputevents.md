---
title: GetNumberOfConsoleInputEvents función)
description: Recupera el número de registros de entrada no leídos en el búfer de entrada de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/GetNumberOfConsoleInputEvents
- wincon/GetNumberOfConsoleInputEvents
- GetNumberOfConsoleInputEvents
MS-HAID:
- '\_win32\_getnumberofconsoleinputevents'
- base.getnumberofconsoleinputevents
- consoles.getnumberofconsoleinputevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1083b4f1-8fa6-4054-a516-3b447c3b0130
topic_type:
- apiref
api_name:
- GetNumberOfConsoleInputEvents
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: c5e3a59308239898f78796170d08f8b21ca1b667
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060653"
---
# <a name="getnumberofconsoleinputevents-function"></a>GetNumberOfConsoleInputEvents función)


Recupera el número de registros de entrada no leídos en el búfer de entrada de la consola.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

<a name="parameters"></a>Parámetros
----------

*hConsoleInput* \[ de\]  
Identificador para el búfer de entrada de la consola. El identificador debe tener el derecho de acceso de ** \_ lectura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*lpcNumberOfEvents* \[ enuncia\]  
Un puntero a una variable que recibe el número de registros de entrada no leídos en el búfer de entrada de la consola.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

La función **GetNumberOfConsoleInputEvents** informa del número total de registros de entrada no leídos en el búfer de entrada, incluidos el teclado, el mouse y los registros de entrada de cambio de tamaño de ventana. Los procesos que usan la función [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) solo pueden leer entradas de teclado. Los procesos que usan la función [**ReadConsoleInput**](readconsoleinput.md) pueden leer todos los tipos de registros de entrada.

Un proceso puede especificar un identificador de búfer de entrada de la consola en una de las [funciones de espera](https://msdn.microsoft.com/library/windows/desktop/ms687069) para determinar si hay una entrada de consola sin leer. Cuando el búfer de entrada no está vacío, se señala el estado de un controlador de búfer de entrada de la consola.

Para leer los registros de entrada desde un búfer de entrada de la consola sin afectar al número de registros no leídos, utilice la función [**PeekConsoleInput**](peekconsoleinput.md) . Para descartar todos los registros no leídos en el búfer de entrada de la consola, use la función [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .

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
<td>ConsoleApi. h (a través de winCon. h, include Windows. h)</td>
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

[**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

[Funciones de entrada de la consola de bajo nivel](low-level-console-input-functions.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsole**](readconsole.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

 

 




