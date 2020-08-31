---
title: Estructura de KEY_EVENT_RECORD
description: Describe un evento de entrada de teclado en una estructura de registro de entrada de la consola \_ .
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/KEY_EVENT_RECORD
- wincon/KEY_EVENT_RECORD
- KEY_EVENT_RECORD
- wincontypes/PKEY_EVENT_RECORD
- wincon/PKEY_EVENT_RECORD
- PKEY_EVENT_RECORD
MS-HAID:
- '\_win32\_key\_event\_record\_str'
- base.key\_event\_record\_str
- consoles.key\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b3fed86b-84ef-48e4-97e1-cb3d65f714a7
topic_type:
- apiref
api_name:
- KEY_EVENT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: fd7386d5796442d34cdaa29fcf52831bc6aa1d78
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061016"
---
# <a name="key_event_record-structure"></a>Estructura del registro de \_ eventos clave \_


Describe un evento de entrada de teclado en una estructura de [** \_ registro de entrada**](input-record-str.md) de la consola.

<a name="syntax"></a>Sintaxis
------

```C
typedef struct _KEY_EVENT_RECORD {
  BOOL  bKeyDown;
  WORD  wRepeatCount;
  WORD  wVirtualKeyCode;
  WORD  wVirtualScanCode;
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } uChar;
  DWORD dwControlKeyState;
} KEY_EVENT_RECORD;
```

<a name="members"></a>Miembros
-------

**bKeyDown**  
Si se presiona la tecla, este miembro es **true**. De lo contrario, este miembro es **false** (se libera la tecla).

**wRepeatCount**  
Recuento de repeticiones, que indica que una clave se mantiene presionada. Por ejemplo, cuando se mantiene presionada una tecla, podría obtener cinco eventos con este miembro igual a 1, un evento con este miembro igual a 5 o varios eventos con este miembro mayor o igual que 1.

**wVirtualKeyCode**  
[Código de clave virtual](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) que identifica la clave especificada de una manera independiente del dispositivo.

**wVirtualScanCode**  
Código de análisis virtual de la clave especificada que representa el valor dependiente del dispositivo generado por el hardware del teclado.

**uChar**  
Unión de los siguientes miembros.

**UnicodeChar**  
Carácter Unicode traducido.

**AsciiChar**  
Carácter ASCII traducido.

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

 

<a name="remarks"></a>Observaciones
-------

Las claves mejoradas para los teclados de IBM® 101-y 102-Key son las teclas INS, SUPR, Inicio, fin, Re Pág, Av Pág y dirección en los clústeres a la izquierda del teclado. y la división (/) y escriba las teclas en el teclado.

Los eventos de entrada de teclado se generan cuando se presiona o se suelta cualquier tecla, incluidas las teclas de control. Sin embargo, la tecla ALT cuando se presiona y se libera sin combinar con otro carácter, tiene un significado especial para el sistema y no se pasa a la aplicación. Además, la combinación de teclas CTRL + C no se pasa si el identificador de entrada está en modo procesado **( \_ habilitar \_ entrada procesada**).

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


[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

[**registro de entrada \_**](input-record-str.md)

 

 




