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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4ad86de170c1fef74f133a5d5c51d8de2dea497f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038543"
---
# <a name="input_record-structure"></a><span data-ttu-id="fd218-104">Estructura del registro de entrada \_</span><span class="sxs-lookup"><span data-stu-id="fd218-104">INPUT\_RECORD structure</span></span>

<span data-ttu-id="fd218-105">Describe un evento de entrada en el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="fd218-105">Describes an input event in the console input buffer.</span></span> <span data-ttu-id="fd218-106">Estos registros se pueden leer desde el búfer de entrada mediante la función [**ReadConsoleInput**](readconsoleinput.md) o [**PeekConsoleInput**](peekconsoleinput.md) , o bien escribirse en el búfer de entrada mediante la función [**WriteConsoleInput**](writeconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="fd218-106">These records can be read from the input buffer by using the [**ReadConsoleInput**](readconsoleinput.md) or [**PeekConsoleInput**](peekconsoleinput.md) function, or written to the input buffer by using the [**WriteConsoleInput**](writeconsoleinput.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="fd218-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fd218-107">Syntax</span></span>

```C
typedef struct _INPUT_RECORD {
  WORD  EventType;
  union {
    KEY_EVENT_RECORD          KeyEvent;
    MOUSE_EVENT_RECORD        MouseEvent;
    WINDOW_BUFFER_SIZE_RECORD WindowBufferSizeEvent;
    MENU_EVENT_RECORD         MenuEvent;
    FOCUS_EVENT_RECORD        FocusEvent;
  } Event;
} INPUT_RECORD;
```

## <a name="members"></a><span data-ttu-id="fd218-108">Miembros</span><span class="sxs-lookup"><span data-stu-id="fd218-108">Members</span></span>

<span data-ttu-id="fd218-109">**EventType**</span><span class="sxs-lookup"><span data-stu-id="fd218-109">**EventType**</span></span>  
<span data-ttu-id="fd218-110">Identificador para el tipo de evento de entrada y el registro de eventos almacenados en el miembro de **evento** .</span><span class="sxs-lookup"><span data-stu-id="fd218-110">A handle to the type of input event and the event record stored in the **Event** member.</span></span>

<span data-ttu-id="fd218-111">Este miembro puede ser uno de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="fd218-111">This member can be one of the following values.</span></span>

| <span data-ttu-id="fd218-112">Valor</span><span class="sxs-lookup"><span data-stu-id="fd218-112">Value</span></span> | <span data-ttu-id="fd218-113">Significado</span><span class="sxs-lookup"><span data-stu-id="fd218-113">Meaning</span></span> |
|-|-|
| <span data-ttu-id="fd218-114">**FOCUS_EVENT** 0x0010</span><span class="sxs-lookup"><span data-stu-id="fd218-114">**FOCUS_EVENT** 0x0010</span></span> | <span data-ttu-id="fd218-115">El miembro de **evento** contiene una estructura de **[FOCUS_EVENT_RECORD](focus-event-record-str.md)** .</span><span class="sxs-lookup"><span data-stu-id="fd218-115">The **Event** member contains a **[FOCUS_EVENT_RECORD](focus-event-record-str.md)** structure.</span></span> <span data-ttu-id="fd218-116">Estos eventos se usan internamente y deben omitirse.</span><span class="sxs-lookup"><span data-stu-id="fd218-116">These events are used internally and should be ignored.</span></span> |
| <span data-ttu-id="fd218-117">**KEY_EVENT** 0x0001</span><span class="sxs-lookup"><span data-stu-id="fd218-117">**KEY_EVENT** 0x0001</span></span> | <span data-ttu-id="fd218-118">El miembro de **evento** contiene una estructura de **[KEY_EVENT_RECORD](key-event-record-str.md)** con información sobre un evento de teclado.</span><span class="sxs-lookup"><span data-stu-id="fd218-118">The **Event** member contains a **[KEY_EVENT_RECORD](key-event-record-str.md)** structure with information about a keyboard event.</span></span> |
| <span data-ttu-id="fd218-119">**MENU_EVENT** 0x0008</span><span class="sxs-lookup"><span data-stu-id="fd218-119">**MENU_EVENT** 0x0008</span></span> | <span data-ttu-id="fd218-120">El miembro de **evento** contiene una estructura de **[MENU_EVENT_RECORD](menu-event-record-str.md)** .</span><span class="sxs-lookup"><span data-stu-id="fd218-120">The **Event** member contains a **[MENU_EVENT_RECORD](menu-event-record-str.md)** structure.</span></span> <span data-ttu-id="fd218-121">Estos eventos se usan internamente y deben omitirse.</span><span class="sxs-lookup"><span data-stu-id="fd218-121">These events are used internally and should be ignored.</span></span> |
| <span data-ttu-id="fd218-122">**MOUSE_EVENT** 0x0002</span><span class="sxs-lookup"><span data-stu-id="fd218-122">**MOUSE_EVENT** 0x0002</span></span> | <span data-ttu-id="fd218-123">El miembro de **evento** contiene una estructura de **[MOUSE_EVENT_RECORD](mouse-event-record-str.md)** con información sobre un evento de presionar el botón o el movimiento del mouse.</span><span class="sxs-lookup"><span data-stu-id="fd218-123">The **Event** member contains a **[MOUSE_EVENT_RECORD](mouse-event-record-str.md)** structure with information about a mouse movement or button press event.</span></span> |
| <span data-ttu-id="fd218-124">**WINDOW_BUFFER_SIZE_EVENT** 0x0004</span><span class="sxs-lookup"><span data-stu-id="fd218-124">**WINDOW_BUFFER_SIZE_EVENT** 0x0004</span></span> | <span data-ttu-id="fd218-125">El miembro de **evento** contiene una estructura de **[WINDOW_BUFFER_SIZE_RECORD](window-buffer-size-record-str.md)** con información sobre el nuevo tamaño del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="fd218-125">The **Event** member contains a **[WINDOW_BUFFER_SIZE_RECORD](window-buffer-size-record-str.md)** structure with information about the new size of the console screen buffer.</span></span> |

<span data-ttu-id="fd218-126">**Evento**</span><span class="sxs-lookup"><span data-stu-id="fd218-126">**Event**</span></span>  
<span data-ttu-id="fd218-127">La información de eventos.</span><span class="sxs-lookup"><span data-stu-id="fd218-127">The event information.</span></span> <span data-ttu-id="fd218-128">El formato de este miembro depende del tipo de evento especificado por el miembro **EventType** .</span><span class="sxs-lookup"><span data-stu-id="fd218-128">The format of this member depends on the event type specified by the **EventType** member.</span></span>

## <a name="examples"></a><span data-ttu-id="fd218-129">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="fd218-129">Examples</span></span>

<span data-ttu-id="fd218-130">Para obtener un ejemplo, vea [leer eventos de búfer de entrada](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="fd218-130">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="fd218-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fd218-131">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="fd218-132">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="fd218-132">Minimum supported client</span></span> | <span data-ttu-id="fd218-133">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="fd218-133">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="fd218-134">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="fd218-134">Minimum supported server</span></span> | <span data-ttu-id="fd218-135">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="fd218-135">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="fd218-136">Encabezado</span><span class="sxs-lookup"><span data-stu-id="fd218-136">Header</span></span> | <span data-ttu-id="fd218-137">WinConTypes. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="fd218-137">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="fd218-138">Consulte también</span><span class="sxs-lookup"><span data-stu-id="fd218-138">See also</span></span>

[<span data-ttu-id="fd218-139">**\_registro de eventos de foco \_**</span><span class="sxs-lookup"><span data-stu-id="fd218-139">**FOCUS\_EVENT\_RECORD**</span></span>](focus-event-record-str.md)

[<span data-ttu-id="fd218-140">**\_registro de evento de clave \_**</span><span class="sxs-lookup"><span data-stu-id="fd218-140">**KEY\_EVENT\_RECORD**</span></span>](key-event-record-str.md)

[<span data-ttu-id="fd218-141">**\_registro de evento de menú \_**</span><span class="sxs-lookup"><span data-stu-id="fd218-141">**MENU\_EVENT\_RECORD**</span></span>](menu-event-record-str.md)

[<span data-ttu-id="fd218-142">**\_registro de eventos del mouse \_**</span><span class="sxs-lookup"><span data-stu-id="fd218-142">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="fd218-143">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="fd218-143">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="fd218-144">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="fd218-144">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="fd218-145">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="fd218-145">**WriteConsoleInput**</span></span>](writeconsoleinput.md)
