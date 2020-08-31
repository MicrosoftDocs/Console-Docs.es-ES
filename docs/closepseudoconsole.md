---
title: ClosePseudoConsole función)
description: Vea la información de referencia sobre la función ClosePseudoConsole, que cierra un pseudoconsole desde el identificador especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola, conpty, pseudoconsole
topic_type:
- apiref
api_name:
- ClosePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 0674fa9c02c54c9476e2844da69895905865d6f4
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060896"
---
# <a name="closepseudoconsole-function"></a>ClosePseudoConsole función)


Cierra un pseudoconsole del identificador dado.

<a name="syntax"></a>Sintaxis
------

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC 
);
```

<a name="parameters"></a>Parámetros
----------

*hPC* \[ de\]  
Identificador de un psuedoconsole activo tal y como lo abre [CreatePseudoConsole](createpseudoconsole.md).

<a name="return-value"></a>Valor devuelto
------------

*Ninguna*

<a name="remarks"></a>Observaciones
-------

Al cerrar un pseudoconsole, las aplicaciones cliente adjuntas a la sesión también se terminarán.

Un marco pintado final puede llegar `hOutput` desde pseudoconsole cuando se llama a esta API. Se espera que el autor de la llamada vacíe esta información del búfer del canal de comunicación y la presente o la descarte. Si no se agota el búfer, es posible que la llamada de cierre espere indefinidamente hasta que se vacíe o que los canales de comunicación se rompan de otra manera.

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
<td><p>Windows 10 1809 [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="even">
<td><p>Servidor mínimo compatible</p></td>
<td><p>Windows Server 2019 [solo aplicaciones de escritorio]</p></td>
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

[Pseudoconsoles](pseudoconsoles.md)

[**CreatePseudoConsole**](createpseudoconsole.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)
