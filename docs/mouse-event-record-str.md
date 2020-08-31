---
title: Estructura de MOUSE_EVENT_RECORD
description: Vea la información de referencia sobre la estructura de MOUSE_EVENT_RECORD, que describe un evento de entrada del mouse en una estructura de INPUT_RECORD de consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/MOUSE_EVENT_RECORD
- wincon/MOUSE_EVENT_RECORD
- MOUSE_EVENT_RECORD
- wincontypes/PMOUSE_EVENT_RECORD
- wincon/PMOUSE_EVENT_RECORD
- PMOUSE_EVENT_RECORD
MS-HAID:
- '\_win32\_mouse\_event\_record\_str'
- base.mouse\_event\_record\_str
- consoles.mouse\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ea54c6-8872-4111-8d72-1377409b9247
topic_type:
- apiref
api_name:
- MOUSE_EVENT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: a3e95e9d35cdf2af2ec6836021dd8819323a4790
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060597"
---
# <a name="mouse_event_record-structure"></a>Estructura de registro de \_ eventos del mouse \_


Describe un evento de entrada del mouse en una estructura de [** \_ registro de entrada**](input-record-str.md) de la consola.

<a name="syntax"></a>Sintaxis
------

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

<a name="members"></a>Miembros
-------

**dwMousePosition**  
Una estructura de [**coordenadas**](coord-str.md) que contiene la ubicación del cursor, en cuanto a las coordenadas de la celda de caracteres del búfer de la pantalla de la consola.

**dwButtonState**  
Estado de los botones del mouse. El bit menos significativo corresponde al botón primario del mouse. El siguiente bit menos significativo corresponde al botón secundario del mouse. El bit siguiente indica el siguiente botón del mouse. Después, los bits se corresponden de izquierda a derecha a los botones del mouse. Un bit es 1 si se presionó el botón.

Las siguientes constantes se definen para los cinco primeros botones del mouse.

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
<td><span id="FROM_LEFT_1ST_BUTTON_PRESSED"></span><span id="from_left_1st_button_pressed"></span>
<strong>FROM_LEFT_1ST_BUTTON_PRESSED</strong> 0x0001</td>
<td><p>Botón primario del mouse.</p></td>
</tr>
<tr class="even">
<td><span id="FROM_LEFT_2ND_BUTTON_PRESSED"></span><span id="from_left_2nd_button_pressed"></span>
<strong>FROM_LEFT_2ND_BUTTON_PRESSED</strong> 0x0004</td>
<td><p>Segundo botón de la izquierda.</p></td>
</tr>
<tr class="odd">
<td><span id="FROM_LEFT_3RD_BUTTON_PRESSED"></span><span id="from_left_3rd_button_pressed"></span>
<strong>FROM_LEFT_3RD_BUTTON_PRESSED</strong> 0x0008</td>
<td><p>Tercer botón de la izquierda.</p></td>
</tr>
<tr class="even">
<td><span id="FROM_LEFT_4TH_BUTTON_PRESSED"></span><span id="from_left_4th_button_pressed"></span>
<strong>FROM_LEFT_4TH_BUTTON_PRESSED</strong> 0x0010</td>
<td><p>Cuarto botón de la izquierda.</p></td>
</tr>
<tr class="odd">
<td><span id="RIGHTMOST_BUTTON_PRESSED"></span><span id="rightmost_button_pressed"></span>
<strong>RIGHTMOST_BUTTON_PRESSED</strong> 0x0002</td>
<td><p>Botón secundario del mouse.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

**dwControlKeyState**  
Estado de las teclas de control. Este miembro puede ser uno o varios de los valores siguientes.

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
<td><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</td>
<td><p>La luz de Bloq Mayús está activada.</p></td>
</tr>
<tr class="even">
<td><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</td>
<td><p>La clave se ha mejorado.</p></td>
</tr>
<tr class="odd">
<td><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</td>
<td><p>Se presiona la tecla ALT izquierda.</p></td>
</tr>
<tr class="even">
<td><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</td>
<td><p>Se presiona la tecla CTRL izquierda.</p></td>
</tr>
<tr class="odd">
<td><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</td>
<td><p>La luz BLOQ NUM está activada.</p></td>
</tr>
<tr class="even">
<td><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</td>
<td><p>Se presiona la tecla ALT derecha.</p></td>
</tr>
<tr class="odd">
<td><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</td>
<td><p>Se presiona la tecla CTRL derecha.</p></td>
</tr>
<tr class="even">
<td><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</td>
<td><p>La luz de Bloq Despl está activada.</p></td>
</tr>
<tr class="odd">
<td><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</td>
<td><p>Se presiona la tecla Mayús.</p></td>
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

 

**dwEventFlags**  
Tipo de evento del mouse. Si este valor es cero, indica que se presiona o se suelta un botón del mouse. De lo contrario, este miembro es uno de los valores siguientes.

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
<td><span id="DOUBLE_CLICK"></span><span id="double_click"></span>
<strong>DOUBLE_CLICK</strong> 0x0002</td>
<td><p>Se produjo el segundo clic (presionar el botón) de un doble clic. El primer clic se devuelve como un evento de presionar botón normal.</p></td>
</tr>
<tr class="even">
<td><span id="MOUSE_HWHEELED"></span><span id="mouse_hwheeled"></span>
<strong>MOUSE_HWHEELED</strong> 0x0008</td>
<td><p>Se ha despasado la rueda del mouse horizontal.</p>
<p>Si la palabra alta del miembro <strong>dwButtonState</strong> contiene un valor positivo, la rueda se giró hacia la derecha. De lo contrario, la rueda se giró hacia la izquierda.</p></td>
</tr>
<tr class="odd">
<td><span id="MOUSE_MOVED"></span><span id="mouse_moved"></span>
<strong>MOUSE_MOVED</strong> 0x0001</td>
<td><p>Se ha producido un cambio en la posición del mouse.</p></td>
</tr>
<tr class="even">
<td><span id="MOUSE_WHEELED"></span><span id="mouse_wheeled"></span>
<strong>MOUSE_WHEELED</strong> 0x0004</td>
<td><p>Rueda del mouse vertical movida.</p>
<p>Si la palabra alta del miembro <strong>dwButtonState</strong> contiene un valor positivo, la rueda se giró hacia delante, alejándose del usuario. De lo contrario, la rueda se giró hacia atrás, hacia el usuario.</p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="remarks"></a>Observaciones
-------

Los eventos del mouse se colocan en el búfer de entrada cuando la consola está en modo de mouse (**Habilitar la \_ \_ entrada del mouse**).

Los eventos del mouse se generan cada vez que el usuario mueve el mouse, o presiona o suelta uno de los botones del mouse. Los eventos del mouse se colocan en el búfer de entrada de la consola solo cuando el grupo de consola tiene el foco de teclado y el cursor se encuentra dentro de los bordes de la ventana de la consola.

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

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

 

 




