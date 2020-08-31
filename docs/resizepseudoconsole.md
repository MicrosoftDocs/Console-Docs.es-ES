---
title: ResizePseudoConsole función)
description: Vea la información de referencia sobre la función ResizePseudoConsole, que cambia el tamaño de los búferes internos para un pseudoconsole al tamaño especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola, conpty, pseudoconsole
f1_keywords:
- consoleapi/ResizePseudoConsole
- ResizePseudoConsole
topic_type:
- apiref
api_name:
- ResizePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a4f6ff773538eda4d4c84c4b0bac2e647f6b80d8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060980"
---
# <a name="resizepseudoconsole-function"></a>ResizePseudoConsole función)


Cambia el tamaño de los búferes internos de un pseudoconsole al tamaño especificado.

<a name="syntax"></a>Sintaxis
------

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

<a name="parameters"></a>Parámetros
----------

*hPC* \[ de\]  
Identificador de un psuedoconsole activo tal y como lo abre [CreatePseudoConsole](createpseudoconsole.md).

*tamaño* \[ de de\]  
Dimensiones de la ventana o búfer en el recuento de caracteres que se usarán para el búfer interno de este pseudoconsole. 

<a name="return-value"></a>Valor devuelto
------------

Tipo: **HRESULT**

Si este método se ejecuta correctamente, devuelve **S_OK**. De lo contrario, devuelve un código de error **HRESULT** .

<a name="remarks"></a>Observaciones
-------

Esta función puede cambiar el tamaño de los búferes internos en la sesión de pseudoconsole para que coincida con el tamaño de búfer o de ventana que se usa para la presentación en el extremo del terminal. Esto garantiza que las aplicaciones de la interfaz de línea de comandos (CUI) conectadas que usan las funciones de la [consola](console-functions.md) para comunicarse tendrán las dimensiones correctas devueltas en sus llamadas.

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

[**ClosePseudoConsole**](closepseudoconsole.md)
