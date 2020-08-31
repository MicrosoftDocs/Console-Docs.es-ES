---
title: FreeConsole función)
description: Vea la información de referencia sobre la función FreeConsole, que separa el proceso de llamada de su consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/FreeConsole
- wincon/FreeConsole
- FreeConsole
MS-HAID:
- '\_win32\_freeconsole'
- base.freeconsole
- consoles.freeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6c525325-696e-4d8b-8337-cbf9e31c900c
topic_type:
- apiref
api_name:
- FreeConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 3c8ba7b236b379bb57729538e065afebb68cc0cf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060740"
---
# <a name="freeconsole-function"></a>FreeConsole función)


Desasocia el proceso de llamada de su consola.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI FreeConsole(void);
```

<a name="parameters"></a>Parámetros
----------

Esta función no tiene parámetros.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

Un proceso se puede adjuntar a como máximo una consola. Si el proceso de llamada no está asociado ya a una consola de, el código de error devuelto es un ** \_ \_ parámetro no válido de error** (87).

Un proceso puede usar la función **FreeConsole** para desasociarse de su consola. Si otros procesos comparten la consola, la consola no se destruye, pero el proceso que llamó a **FreeConsole** no puede hacer referencia a ella. Una consola se cierra cuando el último proceso asociado a ella finaliza o llama a **FreeConsole**. Una vez que un proceso llama a **FreeConsole**, puede llamar a la función [**AllocConsole**](allocconsole.md) para crear una nueva consola o [**AttachConsole**](attachconsole.md) para asociar a otra consola.

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


[**AllocConsole**](allocconsole.md)

[**AttachConsole**](attachconsole.md)

[Funciones de la consola](console-functions.md)

[Consolas](consoles.md)

 

 




