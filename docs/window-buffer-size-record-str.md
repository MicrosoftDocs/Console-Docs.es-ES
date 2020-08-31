---
title: Estructura de WINDOW_BUFFER_SIZE_RECORD
description: Vea información de referencia sobre la estructura de WINDOW_BUFFER_SIZE_RECORD, que describe un cambio en el tamaño del búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/WINDOW_BUFFER_SIZE_RECORD
- wincon/WINDOW_BUFFER_SIZE_RECORD
- WINDOW_BUFFER_SIZE_RECORD
- wincontypes/PWINDOW_BUFFER_SIZE_RECORD
- wincon/PWINDOW_BUFFER_SIZE_RECORD
- PWINDOW_BUFFER_SIZE_RECORD
MS-HAID:
- '\_win32\_window\_buffer\_size\_record\_str'
- base.window\_buffer\_size\_record\_str
- consoles.window\_buffer\_size\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f2875e8-aa09-455b-a923-7cc388525b98
topic_type:
- apiref
api_name:
- WINDOW_BUFFER_SIZE_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 0041c4390fe331302df458965faec0ace2d1888f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061109"
---
# <a name="window_buffer_size_record-structure"></a>\_Estructura de \_ registro del tamaño del búfer de ventana \_


Describe un cambio en el tamaño del búfer de pantalla de la consola.

<a name="syntax"></a>Sintaxis
------

```C
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

<a name="members"></a>Miembros
-------

**dwSize**  
Una estructura de [**coordenadas**](coord-str.md) que contiene el tamaño del búfer de pantalla de la consola, en columnas y filas de celda de carácter.

<a name="remarks"></a>Observaciones
-------

Los eventos de tamaño de búfer se colocan en el búfer de entrada cuando la consola está en modo de ventana (**habilitar \_ \_ entrada de ventana**).

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
<td>WinConTypes. h (a través de winCon. h, include Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vea también


[**COORDS**](coord-str.md)

[**registro de entrada \_**](input-record-str.md)

[**ReadConsoleInput**](readconsoleinput.md)

 

 




