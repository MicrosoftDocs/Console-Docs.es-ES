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
# <a name="input_record-structure"></a><span data-ttu-id="2b21e-104">Estructura del registro de entrada \_</span><span class="sxs-lookup"><span data-stu-id="2b21e-104">INPUT\_RECORD structure</span></span>


<span data-ttu-id="2b21e-105">Describe un evento de entrada en el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="2b21e-105">Describes an input event in the console input buffer.</span></span> <span data-ttu-id="2b21e-106">Estos registros se pueden leer desde el búfer de entrada mediante la función [**ReadConsoleInput**](readconsoleinput.md) o [**PeekConsoleInput**](peekconsoleinput.md) , o bien escribirse en el búfer de entrada mediante la función [**WriteConsoleInput**](writeconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="2b21e-106">These records can be read from the input buffer by using the [**ReadConsoleInput**](readconsoleinput.md) or [**PeekConsoleInput**](peekconsoleinput.md) function, or written to the input buffer by using the [**WriteConsoleInput**](writeconsoleinput.md) function.</span></span>

<a name="syntax"></a><span data-ttu-id="2b21e-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2b21e-107">Syntax</span></span>
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

<a name="members"></a><span data-ttu-id="2b21e-108">Miembros</span><span class="sxs-lookup"><span data-stu-id="2b21e-108">Members</span></span>
-------

<span data-ttu-id="2b21e-109">**EventType**</span><span class="sxs-lookup"><span data-stu-id="2b21e-109">**EventType**</span></span>  
<span data-ttu-id="2b21e-110">Identificador para el tipo de evento de entrada y el registro de eventos almacenados en el miembro de **evento** .</span><span class="sxs-lookup"><span data-stu-id="2b21e-110">A handle to the type of input event and the event record stored in the **Event** member.</span></span>

<span data-ttu-id="2b21e-111">Este miembro puede ser uno de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="2b21e-111">This member can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="2b21e-112">Valor</span><span class="sxs-lookup"><span data-stu-id="2b21e-112">Value</span></span></th>
<th><span data-ttu-id="2b21e-113">Significado</span><span class="sxs-lookup"><span data-stu-id="2b21e-113">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="2b21e-114"><span id="FOCUS_EVENT"></span><span id="focus_event"></span>
<strong>FOCUS_EVENT</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="2b21e-114"><span id="FOCUS_EVENT"></span><span id="focus_event"></span>
<strong>FOCUS_EVENT</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="2b21e-115">El miembro de <strong>evento</strong> contiene una estructura de <a href="focus-event-record-str.md" data-raw-source="[&lt;strong&gt;FOCUS_EVENT_RECORD&lt;/strong&gt;](focus-event-record-str.md)"><strong>FOCUS_EVENT_RECORD</strong></a> .</span><span class="sxs-lookup"><span data-stu-id="2b21e-115">The <strong>Event</strong> member contains a <a href="focus-event-record-str.md" data-raw-source="[&lt;strong&gt;FOCUS_EVENT_RECORD&lt;/strong&gt;](focus-event-record-str.md)"><strong>FOCUS_EVENT_RECORD</strong></a> structure.</span></span> <span data-ttu-id="2b21e-116">Estos eventos se usan internamente y deben omitirse.</span><span class="sxs-lookup"><span data-stu-id="2b21e-116">These events are used internally and should be ignored.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="2b21e-117"><span id="KEY_EVENT"></span><span id="key_event"></span>
<strong>KEY_EVENT</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="2b21e-117"><span id="KEY_EVENT"></span><span id="key_event"></span>
<strong>KEY_EVENT</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="2b21e-118">El miembro de <strong>evento</strong> contiene una estructura de <a href="key-event-record-str.md" data-raw-source="[&lt;strong&gt;KEY_EVENT_RECORD&lt;/strong&gt;](key-event-record-str.md)"><strong>KEY_EVENT_RECORD</strong></a> con información sobre un evento de teclado.</span><span class="sxs-lookup"><span data-stu-id="2b21e-118">The <strong>Event</strong> member contains a <a href="key-event-record-str.md" data-raw-source="[&lt;strong&gt;KEY_EVENT_RECORD&lt;/strong&gt;](key-event-record-str.md)"><strong>KEY_EVENT_RECORD</strong></a> structure with information about a keyboard event.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="2b21e-119"><span id="MENU_EVENT"></span><span id="menu_event"></span>
<strong>MENU_EVENT</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="2b21e-119"><span id="MENU_EVENT"></span><span id="menu_event"></span>
<strong>MENU_EVENT</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="2b21e-120">El miembro de <strong>evento</strong> contiene una estructura de <a href="menu-event-record-str.md" data-raw-source="[&lt;strong&gt;MENU_EVENT_RECORD&lt;/strong&gt;](menu-event-record-str.md)"><strong>MENU_EVENT_RECORD</strong></a> .</span><span class="sxs-lookup"><span data-stu-id="2b21e-120">The <strong>Event</strong> member contains a <a href="menu-event-record-str.md" data-raw-source="[&lt;strong&gt;MENU_EVENT_RECORD&lt;/strong&gt;](menu-event-record-str.md)"><strong>MENU_EVENT_RECORD</strong></a> structure.</span></span> <span data-ttu-id="2b21e-121">Estos eventos se usan internamente y deben omitirse.</span><span class="sxs-lookup"><span data-stu-id="2b21e-121">These events are used internally and should be ignored.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="2b21e-122"><span id="MOUSE_EVENT"></span><span id="mouse_event"></span>
<strong>MOUSE_EVENT</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="2b21e-122"><span id="MOUSE_EVENT"></span><span id="mouse_event"></span>
<strong>MOUSE_EVENT</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="2b21e-123">El miembro de <strong>evento</strong> contiene una estructura de <a href="mouse-event-record-str.md" data-raw-source="[&lt;strong&gt;MOUSE_EVENT_RECORD&lt;/strong&gt;](mouse-event-record-str.md)"><strong>MOUSE_EVENT_RECORD</strong></a> con información sobre un evento de presionar el botón o el movimiento del mouse.</span><span class="sxs-lookup"><span data-stu-id="2b21e-123">The <strong>Event</strong> member contains a <a href="mouse-event-record-str.md" data-raw-source="[&lt;strong&gt;MOUSE_EVENT_RECORD&lt;/strong&gt;](mouse-event-record-str.md)"><strong>MOUSE_EVENT_RECORD</strong></a> structure with information about a mouse movement or button press event.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="2b21e-124"><span id="WINDOW_BUFFER_SIZE_EVENT"></span><span id="window_buffer_size_event"></span>
<strong>WINDOW_BUFFER_SIZE_EVENT</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="2b21e-124"><span id="WINDOW_BUFFER_SIZE_EVENT"></span><span id="window_buffer_size_event"></span>
<strong>WINDOW_BUFFER_SIZE_EVENT</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="2b21e-125">El miembro de <strong>evento</strong> contiene una estructura de <a href="window-buffer-size-record-str.md" data-raw-source="[&lt;strong&gt;WINDOW_BUFFER_SIZE_RECORD&lt;/strong&gt;](window-buffer-size-record-str.md)"><strong>WINDOW_BUFFER_SIZE_RECORD</strong></a> con información sobre el nuevo tamaño del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="2b21e-125">The <strong>Event</strong> member contains a <a href="window-buffer-size-record-str.md" data-raw-source="[&lt;strong&gt;WINDOW_BUFFER_SIZE_RECORD&lt;/strong&gt;](window-buffer-size-record-str.md)"><strong>WINDOW_BUFFER_SIZE_RECORD</strong></a> structure with information about the new size of the console screen buffer.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="2b21e-126">**Evento**</span><span class="sxs-lookup"><span data-stu-id="2b21e-126">**Event**</span></span>  
<span data-ttu-id="2b21e-127">La información de eventos.</span><span class="sxs-lookup"><span data-stu-id="2b21e-127">The event information.</span></span> <span data-ttu-id="2b21e-128">El formato de este miembro depende del tipo de evento especificado por el miembro **EventType** .</span><span class="sxs-lookup"><span data-stu-id="2b21e-128">The format of this member depends on the event type specified by the **EventType** member.</span></span>

<a name="examples"></a><span data-ttu-id="2b21e-129">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="2b21e-129">Examples</span></span>
--------

<span data-ttu-id="2b21e-130">Para obtener un ejemplo, vea [leer eventos de búfer de entrada](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="2b21e-130">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="2b21e-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2b21e-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="2b21e-132">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="2b21e-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="2b21e-133">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="2b21e-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2b21e-134">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="2b21e-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="2b21e-135">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="2b21e-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2b21e-136">Encabezado</span><span class="sxs-lookup"><span data-stu-id="2b21e-136">Header</span></span></p></td>
<td><span data-ttu-id="2b21e-137">WinConTypes. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2b21e-137">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="2b21e-138"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="2b21e-138"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="2b21e-139">**\_registro de eventos de foco \_**</span><span class="sxs-lookup"><span data-stu-id="2b21e-139">**FOCUS\_EVENT\_RECORD**</span></span>](focus-event-record-str.md)

[<span data-ttu-id="2b21e-140">**\_registro de evento de clave \_**</span><span class="sxs-lookup"><span data-stu-id="2b21e-140">**KEY\_EVENT\_RECORD**</span></span>](key-event-record-str.md)

[<span data-ttu-id="2b21e-141">**\_registro de evento de menú \_**</span><span class="sxs-lookup"><span data-stu-id="2b21e-141">**MENU\_EVENT\_RECORD**</span></span>](menu-event-record-str.md)

[<span data-ttu-id="2b21e-142">**\_registro de eventos del mouse \_**</span><span class="sxs-lookup"><span data-stu-id="2b21e-142">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="2b21e-143">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="2b21e-143">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="2b21e-144">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="2b21e-144">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="2b21e-145">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="2b21e-145">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 




