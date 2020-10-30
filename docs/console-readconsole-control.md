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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8a703a1eaa370e16095e1b10eb146a0718f332e9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039193"
---
# <a name="console_readconsole_control-structure"></a><span data-ttu-id="85981-104">\_Estructura del control READCONSOLE de consola \_</span><span class="sxs-lookup"><span data-stu-id="85981-104">CONSOLE\_READCONSOLE\_CONTROL structure</span></span>

<span data-ttu-id="85981-105">Contiene información para una operación de lectura de la consola.</span><span class="sxs-lookup"><span data-stu-id="85981-105">Contains information for a console read operation.</span></span>

## <a name="syntax"></a><span data-ttu-id="85981-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="85981-106">Syntax</span></span>

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

## <a name="members"></a><span data-ttu-id="85981-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="85981-107">Members</span></span>

<span data-ttu-id="85981-108">**nLength**</span><span class="sxs-lookup"><span data-stu-id="85981-108">**nLength**</span></span>  
<span data-ttu-id="85981-109">Tamaño de la estructura.</span><span class="sxs-lookup"><span data-stu-id="85981-109">The size of the structure.</span></span> <span data-ttu-id="85981-110">Establezca este miembro en `sizeof(CONSOLE_READCONSOLE_CONTROL)` .</span><span class="sxs-lookup"><span data-stu-id="85981-110">Set this member to `sizeof(CONSOLE_READCONSOLE_CONTROL)`.</span></span>

<span data-ttu-id="85981-111">**nInitialChars**</span><span class="sxs-lookup"><span data-stu-id="85981-111">**nInitialChars**</span></span>  
<span data-ttu-id="85981-112">Número de caracteres que se van a omitir (y, por tanto, conservar) antes de escribir la entrada recién leída en el búfer pasado a la función [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="85981-112">The number of characters to skip (and thus preserve) before writing newly read input in the buffer passed to the [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="85981-113">Este valor debe ser menor que el parámetro *nNumberOfCharsToRead* de la función **ReadConsole** .</span><span class="sxs-lookup"><span data-stu-id="85981-113">This value must be less than the *nNumberOfCharsToRead* parameter of the **ReadConsole** function.</span></span>

<span data-ttu-id="85981-114">**dwCtrlWakeupMask**</span><span class="sxs-lookup"><span data-stu-id="85981-114">**dwCtrlWakeupMask**</span></span>  
<span data-ttu-id="85981-115">Máscara que especifica los caracteres de control entre `0x00` y que `0x1F` deben usarse para indicar que la lectura ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="85981-115">A mask specifying which control characters between `0x00` and `0x1F` should be used to signal that the read is complete.</span></span> <span data-ttu-id="85981-116">Cada bit corresponde a un carácter con el bit menos significativo correspondiente a `0x00` o `NUL` y el bit más significativo correspondiente a `0x1F` o `US` .</span><span class="sxs-lookup"><span data-stu-id="85981-116">Each bit corresponds to a character with the least significant bit corresponding to `0x00` or `NUL` and the most significant bit corresponding to `0x1F` or `US`.</span></span> <span data-ttu-id="85981-117">Se pueden especificar varios bits (caracteres de control).</span><span class="sxs-lookup"><span data-stu-id="85981-117">Multiple bits (control characters) can be specified.</span></span>

<span data-ttu-id="85981-118">**dwControlKeyState**</span><span class="sxs-lookup"><span data-stu-id="85981-118">**dwControlKeyState**</span></span>  
<span data-ttu-id="85981-119">Estado de las teclas de control.</span><span class="sxs-lookup"><span data-stu-id="85981-119">The state of the control keys.</span></span> <span data-ttu-id="85981-120">Este miembro puede ser uno o varios de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="85981-120">This member can be one or more of the following values.</span></span>

| <span data-ttu-id="85981-121">Valor</span><span class="sxs-lookup"><span data-stu-id="85981-121">Value</span></span> | <span data-ttu-id="85981-122">Significado</span><span class="sxs-lookup"><span data-stu-id="85981-122">Meaning</span></span> |
|-|-|
| <span data-ttu-id="85981-123">**CAPSLOCK_ON** 0x0080</span><span class="sxs-lookup"><span data-stu-id="85981-123">**CAPSLOCK_ON** 0x0080</span></span> | <span data-ttu-id="85981-124">La luz de Bloq Mayús está activada.</span><span class="sxs-lookup"><span data-stu-id="85981-124">The CAPS LOCK light is on.</span></span> |
| <span data-ttu-id="85981-125">**ENHANCED_KEY** 0x0100</span><span class="sxs-lookup"><span data-stu-id="85981-125">**ENHANCED_KEY** 0x0100</span></span> | <span data-ttu-id="85981-126">La clave se ha mejorado.</span><span class="sxs-lookup"><span data-stu-id="85981-126">The key is enhanced.</span></span> <span data-ttu-id="85981-127">Vea la [sección Comentarios](key-event-record-str.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="85981-127">See [remarks](key-event-record-str.md#remarks).</span></span> |
| <span data-ttu-id="85981-128">**LEFT_ALT_PRESSED** 0x0002</span><span class="sxs-lookup"><span data-stu-id="85981-128">**LEFT_ALT_PRESSED** 0x0002</span></span> | <span data-ttu-id="85981-129">Se presiona la tecla ALT izquierda.</span><span class="sxs-lookup"><span data-stu-id="85981-129">The left ALT key is pressed.</span></span> |
| <span data-ttu-id="85981-130">**LEFT_CTRL_PRESSED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="85981-130">**LEFT_CTRL_PRESSED** 0x0008</span></span> | <span data-ttu-id="85981-131">Se presiona la tecla CTRL izquierda.</span><span class="sxs-lookup"><span data-stu-id="85981-131">The left CTRL key is pressed.</span></span> |
| <span data-ttu-id="85981-132">**NUMLOCK_ON** 0x0020</span><span class="sxs-lookup"><span data-stu-id="85981-132">**NUMLOCK_ON** 0x0020</span></span> | <span data-ttu-id="85981-133">La luz BLOQ NUM está activada.</span><span class="sxs-lookup"><span data-stu-id="85981-133">The NUM LOCK light is on.</span></span> |
| <span data-ttu-id="85981-134">**RIGHT_ALT_PRESSED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="85981-134">**RIGHT_ALT_PRESSED** 0x0001</span></span> | <span data-ttu-id="85981-135">Se presiona la tecla ALT derecha.</span><span class="sxs-lookup"><span data-stu-id="85981-135">The right ALT key is pressed.</span></span> |
| <span data-ttu-id="85981-136">**RIGHT_CTRL_PRESSED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="85981-136">**RIGHT_CTRL_PRESSED** 0x0004</span></span> | <span data-ttu-id="85981-137">Se presiona la tecla CTRL derecha.</span><span class="sxs-lookup"><span data-stu-id="85981-137">The right CTRL key is pressed.</span></span> |
| <span data-ttu-id="85981-138">**SCROLLLOCK_ON** 0x0040</span><span class="sxs-lookup"><span data-stu-id="85981-138">**SCROLLLOCK_ON** 0x0040</span></span> | <span data-ttu-id="85981-139">La luz de Bloq Despl está activada.</span><span class="sxs-lookup"><span data-stu-id="85981-139">The SCROLL LOCK light is on.</span></span> |
| <span data-ttu-id="85981-140">**SHIFT_PRESSED** 0x0010</span><span class="sxs-lookup"><span data-stu-id="85981-140">**SHIFT_PRESSED** 0x0010</span></span> | <span data-ttu-id="85981-141">Se presiona la tecla Mayús.</span><span class="sxs-lookup"><span data-stu-id="85981-141">The SHIFT key is pressed.</span></span> |

## <a name="requirements"></a><span data-ttu-id="85981-142">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85981-142">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="85981-143">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="85981-143">Minimum supported client</span></span> | <span data-ttu-id="85981-144">Solo aplicaciones de escritorio de Windows Vista \[\]</span><span class="sxs-lookup"><span data-stu-id="85981-144">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="85981-145">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="85981-145">Minimum supported server</span></span> | <span data-ttu-id="85981-146">Solo aplicaciones de escritorio de Windows Server 2008 \[\]</span><span class="sxs-lookup"><span data-stu-id="85981-146">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="85981-147">Encabezado</span><span class="sxs-lookup"><span data-stu-id="85981-147">Header</span></span> | <span data-ttu-id="85981-148">ConsoleApi. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="85981-148">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="85981-149">Consulte también</span><span class="sxs-lookup"><span data-stu-id="85981-149">See also</span></span>

[<span data-ttu-id="85981-150">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="85981-150">**ReadConsole**</span></span>](readconsole.md)
