---
title: AllocConsole función)
description: Consulte la información de referencia sobre la función AllocConsole, que asigna una nueva consola para el proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/AllocConsole
- wincon/AllocConsole
- AllocConsole
MS-HAID:
- '\_win32\_allocconsole'
- base.allocconsole
- consoles.allocconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bdf3bf2f-8eb8-4ba6-bf3a-a67b29dffda2
topic_type:
- apiref
api_name:
- AllocConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 2e06cdc82c4e58dd09b99fa08bf4917ad37b552f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060928"
---
# <a name="allocconsole-function"></a>AllocConsole función)


Asigna una nueva consola para el proceso de llamada.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI AllocConsole(void);
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

Un proceso solo se puede asociar a una consola, por lo que se produce un error en la función **AllocConsole** si el proceso de llamada ya tiene una consola. Un proceso puede usar la función [**FreeConsole**](freeconsole.md) para desasociarse de su consola actual y, después, puede llamar a **AllocConsole** para crear una nueva consola o [**AttachConsole**](attachconsole.md) para adjuntar a otra consola.

Si el proceso de llamada crea un proceso secundario, el elemento secundario hereda la nueva consola.

**AllocConsole** inicializa la entrada estándar, la salida estándar y los identificadores de error estándar para la nueva consola. El identificador de entrada estándar es un identificador del búfer de entrada de la consola, y los identificadores de salida estándar y de error estándar son identificadores del búfer de pantalla de la consola. Para recuperar estos identificadores, use la función [**GetStdHandle**](getstdhandle.md) .

Esta función se usa principalmente en una aplicación de interfaz gráfica de usuario (GUI) para crear una ventana de consola. Las aplicaciones de GUI se inicializan sin una consola de. Las aplicaciones de consola se inicializan con una consola de, a menos que se creen como procesos desasociados (llamando a la función [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) con la marca de ** \_ proceso separado** ).

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

[Consolas](consoles.md)

[**AttachConsole**](attachconsole.md)

[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[**FreeConsole**](freeconsole.md)

[**GetStdHandle**](getstdhandle.md)

 

 




