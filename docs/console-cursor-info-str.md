---
title: Estructura de CONSOLE_CURSOR_INFO
description: Contiene la información de tamaño y visibilidad sobre el cursor de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/CONSOLE_CURSOR_INFO
- wincon/CONSOLE_CURSOR_INFO
- CONSOLE_CURSOR_INFO
- wincontypes/PCONSOLE_CURSOR_INFO
- wincon/PCONSOLE_CURSOR_INFO
- PCONSOLE_CURSOR_INFO
MS-HAID:
- '\_win32\_console\_cursor\_info\_str'
- base.console\_cursor\_info\_str
- consoles.console\_cursor\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0e71ce8c-e008-4bd7-922e-c44484b425ef
topic_type:
- apiref
api_name:
- CONSOLE_CURSOR_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 0ac3eb459810f2c8ebc861759312350a487abd3c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060872"
---
# <a name="console_cursor_info-structure"></a>Estructura de información del \_ cursor de la consola \_


Contiene información sobre el cursor de la consola.

<a name="syntax"></a>Sintaxis
------

```C
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

<a name="members"></a>Miembros
-------

**dwSize**  
Porcentaje de la celda de caracteres que rellena el cursor. Este valor se encuentra entre 1 y 100. La apariencia del cursor varía, desde que se rellena completamente la celda hasta que se muestra como una línea horizontal en la parte inferior de la celda.

**Nota:**    Aunque el valor de **dwSize** está normalmente entre 1 y 100, en algunas circunstancias se puede devolver un valor fuera de ese intervalo. Por ejemplo, si **CursorSize** se establece en 0 en el registro, el valor de **dwSize** devuelto sería 0.

 

**bVisible**  
Visibilidad del cursor. Si el cursor está visible, este miembro es **true**.

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
<td>WINCON. h (incluir Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vea también


[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**SetConsoleCursorInfo**](setconsolecursorinfo.md)

 

 




