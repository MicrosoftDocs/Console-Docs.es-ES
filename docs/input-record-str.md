---
title: Estructura de INPUT_RECORD
description: Consulte la información de referencia sobre la estructura de INPUT_RECORD, que describe un evento de entrada en el búfer de entrada de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/INPUT_RECORD
- wincon/INPUT_RECORD
- INPUT_RECORD
- wincontypes/PINPUT_RECORD
- wincon/PINPUT_RECORD
- PINPUT_RECORD
MS-HAID:
- '\_win32\_input\_record\_str'
- base.input\_record\_str
- consoles.input\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a46ba7fd-097a-455d-96ac-13aa01e11dc1
topic_type:
- apiref
api_name:
- INPUT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 5d532b5a009681e650991fd083f7d6ab932a05da
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061021"
---
# <a name="input_record-structure"></a>Estructura del registro de entrada \_


Describe un evento de entrada en el búfer de entrada de la consola. Estos registros se pueden leer desde el búfer de entrada mediante la función [**ReadConsoleInput**](readconsoleinput.md) o [**PeekConsoleInput**](peekconsoleinput.md) , o bien escribirse en el búfer de entrada mediante la función [**WriteConsoleInput**](writeconsoleinput.md) .

<a name="syntax"></a>Sintaxis
------

```C
typedef struct _INPUT_RECORD {
  WORD  EventType;
  union {
    KEY_EVENT_RECORD          KeyEvent;
    MOUSE_EVENT_RECORD        MouseEvent;
    WINDOW_BUFFER_SIZE_RECORD WindowBufferSizeEvent;
    MENU_EVENT_RECORD         MenuEvent;
    FOCUS_EVENT_RECORD        FocusEvent;
  } Event;
} INPUT_RECORD;
```

<a name="members"></a>Miembros
-------

**EventType**  
Identificador para el tipo de evento de entrada y el registro de eventos almacenados en el miembro de **evento** .

Este miembro puede ser uno de los valores siguientes.

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
<td><span id="FOCUS_EVENT"></span><span id="focus_event"></span>
<strong>FOCUS_EVENT</strong> 0x0010</td>
<td><p>El miembro de <strong>evento</strong> contiene una estructura de <a href="focus-event-record-str.md" data-raw-source="[&lt;strong&gt;FOCUS_EVENT_RECORD&lt;/strong&gt;](focus-event-record-str.md)"><strong>FOCUS_EVENT_RECORD</strong></a> . Estos eventos se usan internamente y deben omitirse.</p></td>
</tr>
<tr class="even">
<td><span id="KEY_EVENT"></span><span id="key_event"></span>
<strong>KEY_EVENT</strong> 0x0001</td>
<td><p>El miembro de <strong>evento</strong> contiene una estructura de <a href="key-event-record-str.md" data-raw-source="[&lt;strong&gt;KEY_EVENT_RECORD&lt;/strong&gt;](key-event-record-str.md)"><strong>KEY_EVENT_RECORD</strong></a> con información sobre un evento de teclado.</p></td>
</tr>
<tr class="odd">
<td><span id="MENU_EVENT"></span><span id="menu_event"></span>
<strong>MENU_EVENT</strong> 0x0008</td>
<td><p>El miembro de <strong>evento</strong> contiene una estructura de <a href="menu-event-record-str.md" data-raw-source="[&lt;strong&gt;MENU_EVENT_RECORD&lt;/strong&gt;](menu-event-record-str.md)"><strong>MENU_EVENT_RECORD</strong></a> . Estos eventos se usan internamente y deben omitirse.</p></td>
</tr>
<tr class="even">
<td><span id="MOUSE_EVENT"></span><span id="mouse_event"></span>
<strong>MOUSE_EVENT</strong> 0x0002</td>
<td><p>El miembro de <strong>evento</strong> contiene una estructura de <a href="mouse-event-record-str.md" data-raw-source="[&lt;strong&gt;MOUSE_EVENT_RECORD&lt;/strong&gt;](mouse-event-record-str.md)"><strong>MOUSE_EVENT_RECORD</strong></a> con información sobre un evento de presionar el botón o el movimiento del mouse.</p></td>
</tr>
<tr class="odd">
<td><span id="WINDOW_BUFFER_SIZE_EVENT"></span><span id="window_buffer_size_event"></span>
<strong>WINDOW_BUFFER_SIZE_EVENT</strong> 0x0004</td>
<td><p>El miembro de <strong>evento</strong> contiene una estructura de <a href="window-buffer-size-record-str.md" data-raw-source="[&lt;strong&gt;WINDOW_BUFFER_SIZE_RECORD&lt;/strong&gt;](window-buffer-size-record-str.md)"><strong>WINDOW_BUFFER_SIZE_RECORD</strong></a> con información sobre el nuevo tamaño del búfer de pantalla de la consola.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

**Evento**  
La información de eventos. El formato de este miembro depende del tipo de evento especificado por el miembro **EventType** .

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


[**\_registro de eventos de foco \_**](focus-event-record-str.md)

[**\_registro de evento de clave \_**](key-event-record-str.md)

[**\_registro de evento de menú \_**](menu-event-record-str.md)

[**\_registro de eventos del mouse \_**](mouse-event-record-str.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

 

 




