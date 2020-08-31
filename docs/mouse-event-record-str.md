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
# <a name="mouse_event_record-structure"></a><span data-ttu-id="92ce5-104">Estructura de registro de \_ eventos del mouse \_</span><span class="sxs-lookup"><span data-stu-id="92ce5-104">MOUSE\_EVENT\_RECORD structure</span></span>


<span data-ttu-id="92ce5-105">Describe un evento de entrada del mouse en una estructura de [\*\* \_ registro de entrada\*\*](input-record-str.md) de la consola.</span><span class="sxs-lookup"><span data-stu-id="92ce5-105">Describes a mouse input event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span>

<a name="syntax"></a><span data-ttu-id="92ce5-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="92ce5-106">Syntax</span></span>
------

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

<a name="members"></a><span data-ttu-id="92ce5-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="92ce5-107">Members</span></span>
-------

<span data-ttu-id="92ce5-108">**dwMousePosition**</span><span class="sxs-lookup"><span data-stu-id="92ce5-108">**dwMousePosition**</span></span>  
<span data-ttu-id="92ce5-109">Una estructura de [**coordenadas**](coord-str.md) que contiene la ubicación del cursor, en cuanto a las coordenadas de la celda de caracteres del búfer de la pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="92ce5-109">A [**COORD**](coord-str.md) structure that contains the location of the cursor, in terms of the console screen buffer's character-cell coordinates.</span></span>

<span data-ttu-id="92ce5-110">**dwButtonState**</span><span class="sxs-lookup"><span data-stu-id="92ce5-110">**dwButtonState**</span></span>  
<span data-ttu-id="92ce5-111">Estado de los botones del mouse.</span><span class="sxs-lookup"><span data-stu-id="92ce5-111">The status of the mouse buttons.</span></span> <span data-ttu-id="92ce5-112">El bit menos significativo corresponde al botón primario del mouse.</span><span class="sxs-lookup"><span data-stu-id="92ce5-112">The least significant bit corresponds to the leftmost mouse button.</span></span> <span data-ttu-id="92ce5-113">El siguiente bit menos significativo corresponde al botón secundario del mouse.</span><span class="sxs-lookup"><span data-stu-id="92ce5-113">The next least significant bit corresponds to the rightmost mouse button.</span></span> <span data-ttu-id="92ce5-114">El bit siguiente indica el siguiente botón del mouse.</span><span class="sxs-lookup"><span data-stu-id="92ce5-114">The next bit indicates the next-to-leftmost mouse button.</span></span> <span data-ttu-id="92ce5-115">Después, los bits se corresponden de izquierda a derecha a los botones del mouse.</span><span class="sxs-lookup"><span data-stu-id="92ce5-115">The bits then correspond left to right to the mouse buttons.</span></span> <span data-ttu-id="92ce5-116">Un bit es 1 si se presionó el botón.</span><span class="sxs-lookup"><span data-stu-id="92ce5-116">A bit is 1 if the button was pressed.</span></span>

<span data-ttu-id="92ce5-117">Las siguientes constantes se definen para los cinco primeros botones del mouse.</span><span class="sxs-lookup"><span data-stu-id="92ce5-117">The following constants are defined for the first five mouse buttons.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="92ce5-118">Valor</span><span class="sxs-lookup"><span data-stu-id="92ce5-118">Value</span></span></th>
<th><span data-ttu-id="92ce5-119">Significado</span><span class="sxs-lookup"><span data-stu-id="92ce5-119">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="92ce5-120"><span id="FROM_LEFT_1ST_BUTTON_PRESSED"></span><span id="from_left_1st_button_pressed"></span>
<strong>FROM_LEFT_1ST_BUTTON_PRESSED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="92ce5-120"><span id="FROM_LEFT_1ST_BUTTON_PRESSED"></span><span id="from_left_1st_button_pressed"></span>
<strong>FROM_LEFT_1ST_BUTTON_PRESSED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="92ce5-121">Botón primario del mouse.</span><span class="sxs-lookup"><span data-stu-id="92ce5-121">The leftmost mouse button.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="92ce5-122"><span id="FROM_LEFT_2ND_BUTTON_PRESSED"></span><span id="from_left_2nd_button_pressed"></span>
<strong>FROM_LEFT_2ND_BUTTON_PRESSED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="92ce5-122"><span id="FROM_LEFT_2ND_BUTTON_PRESSED"></span><span id="from_left_2nd_button_pressed"></span>
<strong>FROM_LEFT_2ND_BUTTON_PRESSED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="92ce5-123">Segundo botón de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="92ce5-123">The second button from the left.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="92ce5-124"><span id="FROM_LEFT_3RD_BUTTON_PRESSED"></span><span id="from_left_3rd_button_pressed"></span>
<strong>FROM_LEFT_3RD_BUTTON_PRESSED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="92ce5-124"><span id="FROM_LEFT_3RD_BUTTON_PRESSED"></span><span id="from_left_3rd_button_pressed"></span>
<strong>FROM_LEFT_3RD_BUTTON_PRESSED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="92ce5-125">Tercer botón de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="92ce5-125">The third button from the left.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="92ce5-126"><span id="FROM_LEFT_4TH_BUTTON_PRESSED"></span><span id="from_left_4th_button_pressed"></span>
<strong>FROM_LEFT_4TH_BUTTON_PRESSED</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="92ce5-126"><span id="FROM_LEFT_4TH_BUTTON_PRESSED"></span><span id="from_left_4th_button_pressed"></span>
<strong>FROM_LEFT_4TH_BUTTON_PRESSED</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="92ce5-127">Cuarto botón de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="92ce5-127">The fourth button from the left.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="92ce5-128"><span id="RIGHTMOST_BUTTON_PRESSED"></span><span id="rightmost_button_pressed"></span>
<strong>RIGHTMOST_BUTTON_PRESSED</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="92ce5-128"><span id="RIGHTMOST_BUTTON_PRESSED"></span><span id="rightmost_button_pressed"></span>
<strong>RIGHTMOST_BUTTON_PRESSED</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="92ce5-129">Botón secundario del mouse.</span><span class="sxs-lookup"><span data-stu-id="92ce5-129">The rightmost mouse button.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="92ce5-130">**dwControlKeyState**</span><span class="sxs-lookup"><span data-stu-id="92ce5-130">**dwControlKeyState**</span></span>  
<span data-ttu-id="92ce5-131">Estado de las teclas de control.</span><span class="sxs-lookup"><span data-stu-id="92ce5-131">The state of the control keys.</span></span> <span data-ttu-id="92ce5-132">Este miembro puede ser uno o varios de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="92ce5-132">This member can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="92ce5-133">Valor</span><span class="sxs-lookup"><span data-stu-id="92ce5-133">Value</span></span></th>
<th><span data-ttu-id="92ce5-134">Significado</span><span class="sxs-lookup"><span data-stu-id="92ce5-134">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="92ce5-135"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="92ce5-135"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="92ce5-136">La luz de Bloq Mayús está activada.</span><span class="sxs-lookup"><span data-stu-id="92ce5-136">The CAPS LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="92ce5-137"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span><span class="sxs-lookup"><span data-stu-id="92ce5-137"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span></span></td>
<td><p><span data-ttu-id="92ce5-138">La clave se ha mejorado.</span><span class="sxs-lookup"><span data-stu-id="92ce5-138">The key is enhanced.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="92ce5-139"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="92ce5-139"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="92ce5-140">Se presiona la tecla ALT izquierda.</span><span class="sxs-lookup"><span data-stu-id="92ce5-140">The left ALT key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="92ce5-141"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="92ce5-141"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="92ce5-142">Se presiona la tecla CTRL izquierda.</span><span class="sxs-lookup"><span data-stu-id="92ce5-142">The left CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="92ce5-143"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="92ce5-143"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="92ce5-144">La luz BLOQ NUM está activada.</span><span class="sxs-lookup"><span data-stu-id="92ce5-144">The NUM LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="92ce5-145"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="92ce5-145"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="92ce5-146">Se presiona la tecla ALT derecha.</span><span class="sxs-lookup"><span data-stu-id="92ce5-146">The right ALT key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="92ce5-147"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="92ce5-147"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="92ce5-148">Se presiona la tecla CTRL derecha.</span><span class="sxs-lookup"><span data-stu-id="92ce5-148">The right CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="92ce5-149"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="92ce5-149"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="92ce5-150">La luz de Bloq Despl está activada.</span><span class="sxs-lookup"><span data-stu-id="92ce5-150">The SCROLL LOCK light is on.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="92ce5-151"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="92ce5-151"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="92ce5-152">Se presiona la tecla Mayús.</span><span class="sxs-lookup"><span data-stu-id="92ce5-152">The SHIFT key is pressed.</span></span></p></td>
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

 

<span data-ttu-id="92ce5-153">**dwEventFlags**</span><span class="sxs-lookup"><span data-stu-id="92ce5-153">**dwEventFlags**</span></span>  
<span data-ttu-id="92ce5-154">Tipo de evento del mouse.</span><span class="sxs-lookup"><span data-stu-id="92ce5-154">The type of mouse event.</span></span> <span data-ttu-id="92ce5-155">Si este valor es cero, indica que se presiona o se suelta un botón del mouse.</span><span class="sxs-lookup"><span data-stu-id="92ce5-155">If this value is zero, it indicates a mouse button being pressed or released.</span></span> <span data-ttu-id="92ce5-156">De lo contrario, este miembro es uno de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="92ce5-156">Otherwise, this member is one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="92ce5-157">Valor</span><span class="sxs-lookup"><span data-stu-id="92ce5-157">Value</span></span></th>
<th><span data-ttu-id="92ce5-158">Significado</span><span class="sxs-lookup"><span data-stu-id="92ce5-158">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="92ce5-159"><span id="DOUBLE_CLICK"></span><span id="double_click"></span>
<strong>DOUBLE_CLICK</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="92ce5-159"><span id="DOUBLE_CLICK"></span><span id="double_click"></span>
<strong>DOUBLE_CLICK</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="92ce5-160">Se produjo el segundo clic (presionar el botón) de un doble clic.</span><span class="sxs-lookup"><span data-stu-id="92ce5-160">The second click (button press) of a double-click occurred.</span></span> <span data-ttu-id="92ce5-161">El primer clic se devuelve como un evento de presionar botón normal.</span><span class="sxs-lookup"><span data-stu-id="92ce5-161">The first click is returned as a regular button-press event.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="92ce5-162"><span id="MOUSE_HWHEELED"></span><span id="mouse_hwheeled"></span>
<strong>MOUSE_HWHEELED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="92ce5-162"><span id="MOUSE_HWHEELED"></span><span id="mouse_hwheeled"></span>
<strong>MOUSE_HWHEELED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="92ce5-163">Se ha despasado la rueda del mouse horizontal.</span><span class="sxs-lookup"><span data-stu-id="92ce5-163">The horizontal mouse wheel was moved.</span></span></p>
<p><span data-ttu-id="92ce5-164">Si la palabra alta del miembro <strong>dwButtonState</strong> contiene un valor positivo, la rueda se giró hacia la derecha.</span><span class="sxs-lookup"><span data-stu-id="92ce5-164">If the high word of the <strong>dwButtonState</strong> member contains a positive value, the wheel was rotated to the right.</span></span> <span data-ttu-id="92ce5-165">De lo contrario, la rueda se giró hacia la izquierda.</span><span class="sxs-lookup"><span data-stu-id="92ce5-165">Otherwise, the wheel was rotated to the left.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="92ce5-166"><span id="MOUSE_MOVED"></span><span id="mouse_moved"></span>
<strong>MOUSE_MOVED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="92ce5-166"><span id="MOUSE_MOVED"></span><span id="mouse_moved"></span>
<strong>MOUSE_MOVED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="92ce5-167">Se ha producido un cambio en la posición del mouse.</span><span class="sxs-lookup"><span data-stu-id="92ce5-167">A change in mouse position occurred.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="92ce5-168"><span id="MOUSE_WHEELED"></span><span id="mouse_wheeled"></span>
<strong>MOUSE_WHEELED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="92ce5-168"><span id="MOUSE_WHEELED"></span><span id="mouse_wheeled"></span>
<strong>MOUSE_WHEELED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="92ce5-169">Rueda del mouse vertical movida.</span><span class="sxs-lookup"><span data-stu-id="92ce5-169">The vertical mouse wheel was moved.</span></span></p>
<p><span data-ttu-id="92ce5-170">Si la palabra alta del miembro <strong>dwButtonState</strong> contiene un valor positivo, la rueda se giró hacia delante, alejándose del usuario.</span><span class="sxs-lookup"><span data-stu-id="92ce5-170">If the high word of the <strong>dwButtonState</strong> member contains a positive value, the wheel was rotated forward, away from the user.</span></span> <span data-ttu-id="92ce5-171">De lo contrario, la rueda se giró hacia atrás, hacia el usuario.</span><span class="sxs-lookup"><span data-stu-id="92ce5-171">Otherwise, the wheel was rotated backward, toward the user.</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="remarks"></a><span data-ttu-id="92ce5-172">Observaciones</span><span class="sxs-lookup"><span data-stu-id="92ce5-172">Remarks</span></span>
-------

<span data-ttu-id="92ce5-173">Los eventos del mouse se colocan en el búfer de entrada cuando la consola está en modo de mouse (**Habilitar la \_ \_ entrada del mouse**).</span><span class="sxs-lookup"><span data-stu-id="92ce5-173">Mouse events are placed in the input buffer when the console is in mouse mode (**ENABLE\_MOUSE\_INPUT**).</span></span>

<span data-ttu-id="92ce5-174">Los eventos del mouse se generan cada vez que el usuario mueve el mouse, o presiona o suelta uno de los botones del mouse.</span><span class="sxs-lookup"><span data-stu-id="92ce5-174">Mouse events are generated whenever the user moves the mouse, or presses or releases one of the mouse buttons.</span></span> <span data-ttu-id="92ce5-175">Los eventos del mouse se colocan en el búfer de entrada de la consola solo cuando el grupo de consola tiene el foco de teclado y el cursor se encuentra dentro de los bordes de la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="92ce5-175">Mouse events are placed in a console's input buffer only when the console group has the keyboard focus and the cursor is within the borders of the console's window.</span></span>

<a name="examples"></a><span data-ttu-id="92ce5-176">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="92ce5-176">Examples</span></span>
--------

<span data-ttu-id="92ce5-177">Para obtener un ejemplo, vea [leer eventos de búfer de entrada](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="92ce5-177">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="92ce5-178">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92ce5-178">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="92ce5-179">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="92ce5-179">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="92ce5-180">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="92ce5-180">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="92ce5-181">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="92ce5-181">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="92ce5-182">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="92ce5-182">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="92ce5-183">Encabezado</span><span class="sxs-lookup"><span data-stu-id="92ce5-183">Header</span></span></p></td>
<td><span data-ttu-id="92ce5-184">WinConTypes. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="92ce5-184">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="92ce5-185"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="92ce5-185"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="92ce5-186">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="92ce5-186">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="92ce5-187">**registro de entrada \_**</span><span class="sxs-lookup"><span data-stu-id="92ce5-187">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="92ce5-188">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="92ce5-188">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="92ce5-189">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="92ce5-189">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="92ce5-190">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="92ce5-190">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 




