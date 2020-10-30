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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: c10047d1386f3bce1546ee21bacdc81b8fb7bb55
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038523"
---
# <a name="mouse_event_record-structure"></a><span data-ttu-id="9ad2f-104">Estructura de registro de \_ eventos del mouse \_</span><span class="sxs-lookup"><span data-stu-id="9ad2f-104">MOUSE\_EVENT\_RECORD structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="9ad2f-105">Describe un evento de entrada del mouse en una estructura de [**\_ registro de entrada**](input-record-str.md) de la consola.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-105">Describes a mouse input event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="9ad2f-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9ad2f-106">Syntax</span></span>

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

## <a name="members"></a><span data-ttu-id="9ad2f-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="9ad2f-107">Members</span></span>

<span data-ttu-id="9ad2f-108">**dwMousePosition**</span><span class="sxs-lookup"><span data-stu-id="9ad2f-108">**dwMousePosition**</span></span>  
<span data-ttu-id="9ad2f-109">Una estructura de [**coordenadas**](coord-str.md) que contiene la ubicación del cursor, en cuanto a las coordenadas de la celda de caracteres del búfer de la pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-109">A [**COORD**](coord-str.md) structure that contains the location of the cursor, in terms of the console screen buffer's character-cell coordinates.</span></span>

<span data-ttu-id="9ad2f-110">**dwButtonState**</span><span class="sxs-lookup"><span data-stu-id="9ad2f-110">**dwButtonState**</span></span>  
<span data-ttu-id="9ad2f-111">Estado de los botones del mouse.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-111">The status of the mouse buttons.</span></span> <span data-ttu-id="9ad2f-112">El bit menos significativo corresponde al botón primario del mouse.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-112">The least significant bit corresponds to the leftmost mouse button.</span></span> <span data-ttu-id="9ad2f-113">El siguiente bit menos significativo corresponde al botón secundario del mouse.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-113">The next least significant bit corresponds to the rightmost mouse button.</span></span> <span data-ttu-id="9ad2f-114">El bit siguiente indica el siguiente botón del mouse.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-114">The next bit indicates the next-to-leftmost mouse button.</span></span> <span data-ttu-id="9ad2f-115">Después, los bits se corresponden de izquierda a derecha a los botones del mouse.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-115">The bits then correspond left to right to the mouse buttons.</span></span> <span data-ttu-id="9ad2f-116">Un bit es 1 si se presionó el botón.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-116">A bit is 1 if the button was pressed.</span></span>

<span data-ttu-id="9ad2f-117">Las siguientes constantes se definen para los cinco primeros botones del mouse.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-117">The following constants are defined for the first five mouse buttons.</span></span>

| <span data-ttu-id="9ad2f-118">Valor</span><span class="sxs-lookup"><span data-stu-id="9ad2f-118">Value</span></span> | <span data-ttu-id="9ad2f-119">Significado</span><span class="sxs-lookup"><span data-stu-id="9ad2f-119">Meaning</span></span> |
|-|-|
| <span data-ttu-id="9ad2f-120">**FROM_LEFT_1ST_BUTTON_PRESSED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="9ad2f-120">**FROM_LEFT_1ST_BUTTON_PRESSED** 0x0001</span></span> | <span data-ttu-id="9ad2f-121">Botón primario del mouse.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-121">The leftmost mouse button.</span></span> |
| <span data-ttu-id="9ad2f-122">**FROM_LEFT_2ND_BUTTON_PRESSED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="9ad2f-122">**FROM_LEFT_2ND_BUTTON_PRESSED** 0x0004</span></span> | <span data-ttu-id="9ad2f-123">El segundo botón pantalla la izquierda.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-123">The second button fom the left.</span></span> |
| <span data-ttu-id="9ad2f-124">**FROM_LEFT_3RD_BUTTON_PRESSED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="9ad2f-124">**FROM_LEFT_3RD_BUTTON_PRESSED** 0x0008</span></span> | <span data-ttu-id="9ad2f-125">Tercer botón de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-125">The third button from the left.</span></span> |
| <span data-ttu-id="9ad2f-126">**FROM_LEFT_4TH_BUTTON_PRESSED** 0x0010</span><span class="sxs-lookup"><span data-stu-id="9ad2f-126">**FROM_LEFT_4TH_BUTTON_PRESSED** 0x0010</span></span> | <span data-ttu-id="9ad2f-127">Cuarto botón de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-127">The fourth button from the left.</span></span> |
| <span data-ttu-id="9ad2f-128">**RIGHTMOST_BUTTON_PRESSED** 0x0002</span><span class="sxs-lookup"><span data-stu-id="9ad2f-128">**RIGHTMOST_BUTTON_PRESSED** 0x0002</span></span> | <span data-ttu-id="9ad2f-129">Botón secundario del mouse.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-129">The rightmost mouse button.</span></span> |

<span data-ttu-id="9ad2f-130">**dwControlKeyState**</span><span class="sxs-lookup"><span data-stu-id="9ad2f-130">**dwControlKeyState**</span></span>  
<span data-ttu-id="9ad2f-131">Estado de las teclas de control.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-131">The state of the control keys.</span></span> <span data-ttu-id="9ad2f-132">Este miembro puede ser uno o varios de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-132">This member can be one or more of the following values.</span></span>

| <span data-ttu-id="9ad2f-133">Valor</span><span class="sxs-lookup"><span data-stu-id="9ad2f-133">Value</span></span> | <span data-ttu-id="9ad2f-134">Significado</span><span class="sxs-lookup"><span data-stu-id="9ad2f-134">Meaning</span></span> |
|-|-|
| <span data-ttu-id="9ad2f-135">**CAPSLOCK_ON** 0x0080</span><span class="sxs-lookup"><span data-stu-id="9ad2f-135">**CAPSLOCK_ON** 0x0080</span></span> | <span data-ttu-id="9ad2f-136">La luz de Bloq Mayús está activada.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-136">The CAPS LOCK light is on.</span></span> |
| <span data-ttu-id="9ad2f-137">**ENHANCED_KEY** 0x0100</span><span class="sxs-lookup"><span data-stu-id="9ad2f-137">**ENHANCED_KEY** 0x0100</span></span> | <span data-ttu-id="9ad2f-138">La clave se ha mejorado.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-138">The key is enhanced.</span></span> <span data-ttu-id="9ad2f-139">Vea la [sección Comentarios](key-event-record-str.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="9ad2f-139">See [remarks](key-event-record-str.md#remarks).</span></span> |
| <span data-ttu-id="9ad2f-140">**LEFT_ALT_PRESSED** 0x0002</span><span class="sxs-lookup"><span data-stu-id="9ad2f-140">**LEFT_ALT_PRESSED** 0x0002</span></span> | <span data-ttu-id="9ad2f-141">Se presiona la tecla ALT izquierda.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-141">The left ALT key is pressed.</span></span> |
| <span data-ttu-id="9ad2f-142">**LEFT_CTRL_PRESSED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="9ad2f-142">**LEFT_CTRL_PRESSED** 0x0008</span></span> | <span data-ttu-id="9ad2f-143">Se presiona la tecla CTRL izquierda.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-143">The left CTRL key is pressed.</span></span> |
| <span data-ttu-id="9ad2f-144">**NUMLOCK_ON** 0x0020</span><span class="sxs-lookup"><span data-stu-id="9ad2f-144">**NUMLOCK_ON** 0x0020</span></span> | <span data-ttu-id="9ad2f-145">La luz BLOQ NUM está activada.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-145">The NUM LOCK light is on.</span></span> |
| <span data-ttu-id="9ad2f-146">**RIGHT_ALT_PRESSED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="9ad2f-146">**RIGHT_ALT_PRESSED** 0x0001</span></span> | <span data-ttu-id="9ad2f-147">Se presiona la tecla ALT derecha.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-147">The right ALT key is pressed.</span></span> |
| <span data-ttu-id="9ad2f-148">**RIGHT_CTRL_PRESSED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="9ad2f-148">**RIGHT_CTRL_PRESSED** 0x0004</span></span> | <span data-ttu-id="9ad2f-149">Se presiona la tecla CTRL derecha.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-149">The right CTRL key is pressed.</span></span> |
| <span data-ttu-id="9ad2f-150">**SCROLLLOCK_ON** 0x0040</span><span class="sxs-lookup"><span data-stu-id="9ad2f-150">**SCROLLLOCK_ON** 0x0040</span></span> | <span data-ttu-id="9ad2f-151">La luz de Bloq Despl está activada.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-151">The SCROLL LOCK light is on.</span></span> |
| <span data-ttu-id="9ad2f-152">**SHIFT_PRESSED** 0x0010</span><span class="sxs-lookup"><span data-stu-id="9ad2f-152">**SHIFT_PRESSED** 0x0010</span></span> | <span data-ttu-id="9ad2f-153">Se presiona la tecla Mayús.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-153">The SHIFT key is pressed.</span></span> |

<span data-ttu-id="9ad2f-154">**dwEventFlags**</span><span class="sxs-lookup"><span data-stu-id="9ad2f-154">**dwEventFlags**</span></span>  
<span data-ttu-id="9ad2f-155">Tipo de evento del mouse.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-155">The type of mouse event.</span></span> <span data-ttu-id="9ad2f-156">Si este valor es cero, indica que se presiona o se suelta un botón del mouse.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-156">If this value is zero, it indicates a mouse button being pressed or released.</span></span> <span data-ttu-id="9ad2f-157">De lo contrario, este miembro es uno de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-157">Otherwise, this member is one of the following values.</span></span>

| <span data-ttu-id="9ad2f-158">Valor</span><span class="sxs-lookup"><span data-stu-id="9ad2f-158">Value</span></span> | <span data-ttu-id="9ad2f-159">Significado</span><span class="sxs-lookup"><span data-stu-id="9ad2f-159">Meaning</span></span> |
|-|-|
| <span data-ttu-id="9ad2f-160">**DOUBLE_CLICK** 0x0002</span><span class="sxs-lookup"><span data-stu-id="9ad2f-160">**DOUBLE_CLICK** 0x0002</span></span> | <span data-ttu-id="9ad2f-161">Se produjo el segundo clic (presionar el botón) de un doble clic.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-161">The second click (button press) of a double-click occurred.</span></span> <span data-ttu-id="9ad2f-162">El primer clic se devuelve como un evento de presionar botón normal.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-162">The first click is returned as a regular button-press event.</span></span> |
| <span data-ttu-id="9ad2f-163">**MOUSE_HWHEELED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="9ad2f-163">**MOUSE_HWHEELED** 0x0008</span></span> | <span data-ttu-id="9ad2f-164">Se ha despasado la rueda del mouse horizontal.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-164">The horizontal mouse wheel was moved.</span></span><br /><br /><span data-ttu-id="9ad2f-165">Si la palabra alta del miembro **dwButtonState** contiene un valor positivo, la rueda se giró hacia la derecha.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-165">If the high word of the **dwButtonState** member contains a positive value, the wheel was rotated to the right.</span></span> <span data-ttu-id="9ad2f-166">De lo contrario, la rueda se giró hacia la izquierda.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-166">Otherwise, the wheel was rotated to the left.</span></span> |
| <span data-ttu-id="9ad2f-167">**MOUSE_MOVED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="9ad2f-167">**MOUSE_MOVED** 0x0001</span></span> | <span data-ttu-id="9ad2f-168">Se ha producido un cambio en la posición del mouse.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-168">A change in mouse position occurred.</span></span> |
| <span data-ttu-id="9ad2f-169">**MOUSE_WHEELED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="9ad2f-169">**MOUSE_WHEELED** 0x0004</span></span> | <span data-ttu-id="9ad2f-170">Rueda del mouse vertical movida.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-170">The vertical mouse wheel was moved.</span></span><br /><br /><span data-ttu-id="9ad2f-171">Si la palabra alta del miembro **dwButtonState** contiene un valor positivo, la rueda se giró hacia delante, alejándose del usuario.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-171">If the high word of the **dwButtonState** member contains a positive value, the wheel was rotated forward, away from the user.</span></span> <span data-ttu-id="9ad2f-172">De lo contrario, la rueda se giró hacia atrás, hacia el usuario.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-172">Otherwise, the wheel was rotated backward, toward the user.</span></span> |

## <a name="remarks"></a><span data-ttu-id="9ad2f-173">Comentarios</span><span class="sxs-lookup"><span data-stu-id="9ad2f-173">Remarks</span></span>

<span data-ttu-id="9ad2f-174">Los eventos del mouse se colocan en el búfer de entrada cuando la consola está en modo de mouse ( **Habilitar la \_ \_ entrada del mouse** ).</span><span class="sxs-lookup"><span data-stu-id="9ad2f-174">Mouse events are placed in the input buffer when the console is in mouse mode ( **ENABLE\_MOUSE\_INPUT** ).</span></span>

<span data-ttu-id="9ad2f-175">Los eventos del mouse se generan cada vez que el usuario mueve el mouse, o presiona o suelta uno de los botones del mouse.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-175">Mouse events are generated whenever the user moves the mouse, or presses or releases one of the mouse buttons.</span></span> <span data-ttu-id="9ad2f-176">Los eventos del mouse se colocan en el búfer de entrada de la consola solo cuando el grupo de consola tiene el foco de teclado y el cursor se encuentra dentro de los bordes de la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="9ad2f-176">Mouse events are placed in a console's input buffer only when the console group has the keyboard focus and the cursor is within the borders of the console's window.</span></span>

## <a name="examples"></a><span data-ttu-id="9ad2f-177">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="9ad2f-177">Examples</span></span>

<span data-ttu-id="9ad2f-178">Para obtener un ejemplo, vea [leer eventos de búfer de entrada](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="9ad2f-178">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="9ad2f-179">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ad2f-179">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="9ad2f-180">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="9ad2f-180">Minimum supported client</span></span> | <span data-ttu-id="9ad2f-181">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="9ad2f-181">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="9ad2f-182">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="9ad2f-182">Minimum supported server</span></span> | <span data-ttu-id="9ad2f-183">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="9ad2f-183">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="9ad2f-184">Encabezado</span><span class="sxs-lookup"><span data-stu-id="9ad2f-184">Header</span></span> | <span data-ttu-id="9ad2f-185">WinConTypes. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9ad2f-185">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="9ad2f-186">Consulte también</span><span class="sxs-lookup"><span data-stu-id="9ad2f-186">See also</span></span>

[<span data-ttu-id="9ad2f-187">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="9ad2f-187">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="9ad2f-188">**registro de entrada \_**</span><span class="sxs-lookup"><span data-stu-id="9ad2f-188">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="9ad2f-189">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="9ad2f-189">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="9ad2f-190">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="9ad2f-190">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="9ad2f-191">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="9ad2f-191">**WriteConsoleInput**</span></span>](writeconsoleinput.md)
