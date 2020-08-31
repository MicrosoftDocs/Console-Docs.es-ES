---
title: ReadConsoleInput función)
description: Lee datos de un búfer de entrada de la consola y lo quita del búfer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/ReadConsoleInput
- wincon/ReadConsoleInput
- ReadConsoleInput
- consoleapi/ReadConsoleInputA
- wincon/ReadConsoleInputA
- ReadConsoleInputA
- consoleapi/ReadConsoleInputW
- wincon/ReadConsoleInputW
- ReadConsoleInputW
MS-HAID:
- '\_win32\_readconsoleinput'
- base.readconsoleinput
- consoles.readconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5a9f7b18-cdea-4041-a377-5532d30e0105
topic_type:
- apiref
api_name:
- ReadConsoleInput
- ReadConsoleInputA
- ReadConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 38a5ee0d1572d6e40ab103cfc402d616a99d2ca5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061005"
---
# <a name="readconsoleinput-function"></a>ReadConsoleInput función)


Lee datos de un búfer de entrada de la consola y lo quita del búfer.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI ReadConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

<a name="parameters"></a>Parámetros
----------

*hConsoleInput* \[ de\]  
Identificador para el búfer de entrada de la consola. El identificador debe tener el derecho de acceso de ** \_ lectura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*lpBuffer* \[ enuncia\]  
Puntero a una matriz de estructuras [**de \_ registros de entrada**](input-record-str.md) que recibe los datos del búfer de entrada.

*nLength* \[ de\]  
Tamaño de la matriz a la que apunta el parámetro *lpBuffer* , en elementos de matriz.

*lpNumberOfEventsRead* \[ enuncia\]  
Puntero a una variable que recibe el número de registros de entrada leídos.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

Si el número de registros solicitados en el parámetro *nLength* supera el número de registros disponibles en el búfer, se lee el número disponible. La función no devuelve ningún resultado hasta que se ha leído al menos un registro de entrada.

Un proceso puede especificar un identificador de búfer de entrada de la consola en una de las [funciones de espera](https://msdn.microsoft.com/library/windows/desktop/ms687069) para determinar si hay una entrada de consola sin leer. Cuando el búfer de entrada no está vacío, se señala el estado de un controlador de búfer de entrada de la consola.

Para determinar el número de registros de entrada no leídos en el búfer de entrada de la consola, use la función [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) . Para leer los registros de entrada desde un búfer de entrada de la consola sin afectar al número de registros no leídos, utilice la función [**PeekConsoleInput**](peekconsoleinput.md) . Para descartar todos los registros no leídos en el búfer de entrada de la consola, use la función [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .

Esta función usa caracteres Unicode o caracteres de 8 bits de la página de códigos actual de la consola. La página de códigos de la consola tiene como valor predeterminado la página de códigos OEM del sistema. Para cambiar la página de códigos de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) , o bien use los comandos **chcp** o **mode con CP Select =** .

<a name="examples"></a>Ejemplos
--------

Para obtener un ejemplo, vea [leer eventos de búfer de entrada](reading-input-buffer-events.md).

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
<td><p>Nombres Unicode y ANSI</p></td>
<td><p><strong>ReadConsoleInputW</strong> (Unicode) y <strong>ReadConsoleInputA</strong> (ANSI)</p></td>
</tr>
<tr class="odd">
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

[**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)

[**registro de entrada \_**](input-record-str.md)

[Funciones de entrada de la consola de bajo nivel](low-level-console-input-functions.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleInput**](writeconsoleinput.md)

 

 




