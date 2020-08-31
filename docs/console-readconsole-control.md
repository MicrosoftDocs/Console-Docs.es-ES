---
title: Estructura de CONSOLE_READCONSOLE_CONTROL
description: Consulte la información de referencia sobre la estructura de CONSOLE_READCONSOLE_CONTROL, que contiene información para una operación de lectura de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/CONSOLE_READCONSOLE_CONTROL
- wincon/CONSOLE_READCONSOLE_CONTROL
- CONSOLE_READCONSOLE_CONTROL
- consoleapi/PCONSOLE_READCONSOLE_CONTROL
- wincon/PCONSOLE_READCONSOLE_CONTROL
- PCONSOLE_READCONSOLE_CONTROL
MS-HAID:
- base.console\_readconsole\_control
- consoles.console\_readconsole\_control
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a8451a6-d692-43af-88c4-972c4dc5e07c
topic_type:
- apiref
api_name:
- CONSOLE_READCONSOLE_CONTROL
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4fc6af26cd540a7af207af252963c21ba216cdee
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060844"
---
# <a name="console_readconsole_control-structure"></a><span data-ttu-id="fc2d6-104">\_Estructura del control READCONSOLE de consola \_</span><span class="sxs-lookup"><span data-stu-id="fc2d6-104">CONSOLE\_READCONSOLE\_CONTROL structure</span></span>


<span data-ttu-id="fc2d6-105">Contiene información para una operación de lectura de la consola.</span><span class="sxs-lookup"><span data-stu-id="fc2d6-105">Contains information for a console read operation.</span></span>

<a name="syntax"></a><span data-ttu-id="fc2d6-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fc2d6-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

<a name="members"></a><span data-ttu-id="fc2d6-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="fc2d6-107">Members</span></span>
-------

<span data-ttu-id="fc2d6-108">**nLength**</span><span class="sxs-lookup"><span data-stu-id="fc2d6-108">**nLength**</span></span>  
<span data-ttu-id="fc2d6-109">Tamaño de la estructura.</span><span class="sxs-lookup"><span data-stu-id="fc2d6-109">The size of the structure.</span></span> <span data-ttu-id="fc2d6-110">Establezca este miembro en `sizeof(CONSOLE_READCONSOLE_CONTROL)` .</span><span class="sxs-lookup"><span data-stu-id="fc2d6-110">Set this member to `sizeof(CONSOLE_READCONSOLE_CONTROL)`.</span></span>

<span data-ttu-id="fc2d6-111">**nInitialChars**</span><span class="sxs-lookup"><span data-stu-id="fc2d6-111">**nInitialChars**</span></span>  
<span data-ttu-id="fc2d6-112">Número de caracteres que se van a omitir (y, por tanto, conservar) antes de escribir la entrada recién leída en el búfer pasado a la función [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="fc2d6-112">The number of characters to skip (and thus preserve) before writing newly read input in the buffer passed to the [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="fc2d6-113">Este valor debe ser menor que el parámetro *nNumberOfCharsToRead* de la función **ReadConsole** .</span><span class="sxs-lookup"><span data-stu-id="fc2d6-113">This value must be less than the *nNumberOfCharsToRead* parameter of the **ReadConsole** function.</span></span>

<span data-ttu-id="fc2d6-114">**dwCtrlWakeupMask**</span><span class="sxs-lookup"><span data-stu-id="fc2d6-114">**dwCtrlWakeupMask**</span></span>  
<span data-ttu-id="fc2d6-115">Un carácter de control definido por el usuario que se usa para indicar que la lectura ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="fc2d6-115">A user-defined control character used to signal that the read is complete.</span></span>

<span data-ttu-id="fc2d6-116">**dwControlKeyState**</span><span class="sxs-lookup"><span data-stu-id="fc2d6-116">**dwControlKeyState**</span></span>  
<span data-ttu-id="fc2d6-117">Estado de las teclas de control.</span><span class="sxs-lookup"><span data-stu-id="fc2d6-117">The state of the control keys.</span></span> <span data-ttu-id="fc2d6-118">Este miembro puede ser uno o varios de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="fc2d6-118">This member can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="fc2d6-119">Valor</span><span class="sxs-lookup"><span data-stu-id="fc2d6-119">Value</span></span></th>
<th><span data-ttu-id="fc2d6-120">Significado</span><span class="sxs-lookup"><span data-stu-id="fc2d6-120">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="fc2d6-121"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="fc2d6-121"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="fc2d6-122">La luz de Bloq Mayús está activada.</span><span class="sxs-lookup"><span data-stu-id="fc2d6-122">The CAPS LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="fc2d6-123"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span><span class="sxs-lookup"><span data-stu-id="fc2d6-123"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span></span></td>
<td><p><span data-ttu-id="fc2d6-124">La clave se ha mejorado.</span><span class="sxs-lookup"><span data-stu-id="fc2d6-124">The key is enhanced.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="fc2d6-125"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="fc2d6-125"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="fc2d6-126">Se presiona la tecla ALT izquierda.</span><span class="sxs-lookup"><span data-stu-id="fc2d6-126">The left ALT key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="fc2d6-127"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="fc2d6-127"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="fc2d6-128">Se presiona la tecla CTRL izquierda.</span><span class="sxs-lookup"><span data-stu-id="fc2d6-128">The left CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="fc2d6-129"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="fc2d6-129"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="fc2d6-130">La luz BLOQ NUM está activada.</span><span class="sxs-lookup"><span data-stu-id="fc2d6-130">The NUM LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="fc2d6-131"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="fc2d6-131"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="fc2d6-132">Se presiona la tecla ALT derecha.</span><span class="sxs-lookup"><span data-stu-id="fc2d6-132">The right ALT key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="fc2d6-133"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="fc2d6-133"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="fc2d6-134">Se presiona la tecla CTRL derecha.</span><span class="sxs-lookup"><span data-stu-id="fc2d6-134">The right CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="fc2d6-135"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="fc2d6-135"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="fc2d6-136">La luz de Bloq Despl está activada.</span><span class="sxs-lookup"><span data-stu-id="fc2d6-136">The SCROLL LOCK light is on.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="fc2d6-137"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="fc2d6-137"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="fc2d6-138">Se presiona la tecla Mayús.</span><span class="sxs-lookup"><span data-stu-id="fc2d6-138">The SHIFT key is pressed.</span></span></p></td>
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

 

<a name="requirements"></a><span data-ttu-id="fc2d6-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc2d6-139">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="fc2d6-140">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="fc2d6-140">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="fc2d6-141">Windows Vista [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="fc2d6-141">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="fc2d6-142">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="fc2d6-142">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="fc2d6-143">Windows Server 2008 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="fc2d6-143">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="fc2d6-144">Encabezado</span><span class="sxs-lookup"><span data-stu-id="fc2d6-144">Header</span></span></p></td>
<td><span data-ttu-id="fc2d6-145">ConsoleApi. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="fc2d6-145">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="fc2d6-146"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="fc2d6-146"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="fc2d6-147">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="fc2d6-147">**ReadConsole**</span></span>](readconsole.md)

 

 




