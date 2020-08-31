---
title: AttachConsole función)
description: Vea la información de referencia sobre la función AttachConsole, que asocia el proceso de llamada a la consola del proceso especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- base.attachconsole
- consoles.attachconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c4048a2fb4c93d9f286ffc1ef7f38923836f37bf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060921"
---
# <a name="attachconsole-function"></a>AttachConsole función)


Asocia el proceso de llamada a la consola del proceso especificado.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

<a name="parameters"></a>Parámetros
----------

*dwProcessId* \[ de\]  
Identificador del proceso cuya consola se va a usar. Este parámetro puede ser uno de los valores siguientes.

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
<td><em>pid</em></td>
<td><p>Use la consola del proceso especificado.</p></td>
</tr>
<tr class="even">
<td><span id="ATTACH_PARENT_PROCESS"></span><span id="attach_parent_process"></span>
<strong>ATTACH_PARENT_PROCESS</strong> (DWORD)-1</td>
<td><p>Use la consola del elemento primario del proceso actual.</p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

Un proceso se puede adjuntar a como máximo una consola. Si el proceso de llamada ya está asociado a una consola de, el código de error devuelto es **error de \_ acceso \_ denegado** (5). Si el proceso especificado no tiene una consola de, el código de error devuelto es un **identificador de error \_ no válido \_ ** (6). Si el proceso especificado no existe, el código de error devuelto es un **parámetro de error \_ no válido \_ ** (87).

Un proceso puede usar la función [**FreeConsole**](freeconsole.md) para desasociarse de su consola. Si otros procesos comparten la consola, la consola no se destruye, pero el proceso que llamó a **FreeConsole** no puede hacer referencia a ella. Una consola se cierra cuando el último proceso asociado a ella finaliza o llama a **FreeConsole**. Una vez que un proceso llama a **FreeConsole**, puede llamar a la función [**AllocConsole**](allocconsole.md) para crear una nueva consola o **AttachConsole** para asociar a otra consola.

Para compilar una aplicación que usa esta función, defina ** \_ Win32 \_ WinNT** como 0x0501 o posterior. Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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

[Consolas](consoles.md)

[**AllocConsole**](allocconsole.md)

[**FreeConsole**](freeconsole.md)

[**GetConsoleProcessList**](getconsoleprocesslist.md)

 

 




