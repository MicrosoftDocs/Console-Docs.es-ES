---
title: Estructura de CHAR_INFO
description: Especifica un carácter Unicode o ANSI y sus atributos. Las funciones de consola utilizan esta estructura para leer y escribir en un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/CHAR_INFO
- wincon/CHAR_INFO
- CHAR_INFO
- wincontypes/PCHAR_INFO
- wincon/PCHAR_INFO
- PCHAR_INFO
MS-HAID:
- '\_win32\_char\_info\_str'
- base.char\_info\_str
- consoles.char\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5574a862-b262-41af-8862-e9837c5c7b5f
topic_type:
- apiref
api_name:
- CHAR_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 6244edaa06b6dd69f8ab3962cf42cb893d08f699
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060909"
---
# <a name="char_info-structure"></a>\_Estructura char info


Especifica un carácter Unicode o ANSI y sus atributos. Las funciones de consola utilizan esta estructura para leer y escribir en un búfer de pantalla de la consola.

<a name="syntax"></a>Sintaxis
------

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

<a name="members"></a>Miembros
-------

**Char**  
Unión de los siguientes miembros.

**UnicodeChar**  
Carácter Unicode de una celda de carácter de búfer de pantalla.

**AsciiChar**  
Carácter ANSI de una celda de carácter de búfer de pantalla.

**Atributos**  
Atributos de carácter. Este miembro puede ser cero o cualquier combinación de los valores siguientes.

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
<td><span id="FOREGROUND_BLUE"></span><span id="foreground_blue"></span>
<strong>FOREGROUND_BLUE</strong> 0x0001</td>
<td><p>El color del texto contiene el azul.</p></td>
</tr>
<tr class="even">
<td><span id="FOREGROUND_GREEN"></span><span id="foreground_green"></span>
<strong>FOREGROUND_GREEN</strong> 0x0002</td>
<td><p>El color del texto contiene verde.</p></td>
</tr>
<tr class="odd">
<td><span id="FOREGROUND_RED"></span><span id="foreground_red"></span>
<strong>FOREGROUND_RED</strong> 0x0004</td>
<td><p>El color del texto contiene rojo.</p></td>
</tr>
<tr class="even">
<td><span id="FOREGROUND_INTENSITY"></span><span id="foreground_intensity"></span>
<strong>FOREGROUND_INTENSITY</strong> 0x0008</td>
<td><p>El color del texto se intensifica.</p></td>
</tr>
<tr class="odd">
<td><span id="BACKGROUND_BLUE"></span><span id="background_blue"></span>
<strong>BACKGROUND_BLUE</strong> 0x0010</td>
<td><p>El color de fondo contiene el azul.</p></td>
</tr>
<tr class="even">
<td><span id="BACKGROUND_GREEN"></span><span id="background_green"></span>
<strong>BACKGROUND_GREEN</strong> 0x0020</td>
<td><p>El color de fondo contiene verde.</p></td>
</tr>
<tr class="odd">
<td><span id="BACKGROUND_RED"></span><span id="background_red"></span>
<strong>BACKGROUND_RED</strong> 0x0040</td>
<td><p>El color de fondo contiene rojo.</p></td>
</tr>
<tr class="even">
<td><span id="BACKGROUND_INTENSITY"></span><span id="background_intensity"></span>
<strong>BACKGROUND_INTENSITY</strong> 0x0080</td>
<td><p>Se intensifica el color de fondo.</p></td>
</tr>
<tr class="odd">
<td><span id="COMMON_LVB_LEADING_BYTE"></span><span id="common_lvb_leading_byte"></span>
<strong>COMMON_LVB_LEADING_BYTE</strong> 0x0100</td>
<td><p>Byte inicial.</p></td>
</tr>
<tr class="even">
<td><span id="COMMON_LVB_TRAILING_BYTE"></span><span id="common_lvb_trailing_byte"></span>
<strong>COMMON_LVB_TRAILING_BYTE</strong> 0x0200</td>
<td><p>Byte final.</p></td>
</tr>
<tr class="odd">
<td><span id="COMMON_LVB_GRID_HORIZONTAL"></span><span id="common_lvb_grid_horizontal"></span>
<strong>COMMON_LVB_GRID_HORIZONTAL</strong> 0x0400</td>
<td><p>Horizontal superior</p></td>
</tr>
<tr class="even">
<td><span id="COMMON_LVB_GRID_LVERTICAL"></span><span id="common_lvb_grid_lvertical"></span>
<strong>COMMON_LVB_GRID_LVERTICAL</strong> 0x0800</td>
<td><p>Vertical izquierda.</p></td>
</tr>
<tr class="odd">
<td><span id="COMMON_LVB_GRID_RVERTICAL"></span><span id="common_lvb_grid_rvertical"></span>
<strong>COMMON_LVB_GRID_RVERTICAL</strong> 0x1000</td>
<td><p>Vertical derecha.</p></td>
</tr>
<tr class="even">
<td><span id="COMMON_LVB_REVERSE_VIDEO"></span><span id="common_lvb_reverse_video"></span>
<strong>COMMON_LVB_REVERSE_VIDEO</strong> 0x4000</td>
<td><p>Atributo de primer plano y fondo inverso.</p></td>
</tr>
<tr class="odd">
<td><span id="COMMON_LVB_UNDERSCORE"></span><span id="common_lvb_underscore"></span>
<strong>COMMON_LVB_UNDERSCORE</strong> 0x8000</td>
<td><p>Subrayado.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
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

 

<a name="examples"></a>Ejemplos
--------

Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).

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


[**ReadConsoleOutput**](readconsoleoutput.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

 

 




