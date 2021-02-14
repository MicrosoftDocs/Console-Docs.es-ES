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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: a16fb23d148f75480437211204a0fd7c1f161bfe
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357855"
---
# `CHAR\_INFO structure`

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="098d9-105">Especifica un carácter Unicode o ANSI y sus atributos.</span><span class="sxs-lookup"><span data-stu-id="098d9-105">Specifies a Unicode or ANSI character and its attributes.</span></span> <span data-ttu-id="098d9-106">Las funciones de consola utilizan esta estructura para leer y escribir en un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="098d9-106">This structure is used by console functions to read from and write to a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="098d9-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="098d9-107">Syntax</span></span>

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

## <a name="members"></a><span data-ttu-id="098d9-108">Miembros</span><span class="sxs-lookup"><span data-stu-id="098d9-108">Members</span></span>

<span data-ttu-id="098d9-109">**Char**</span><span class="sxs-lookup"><span data-stu-id="098d9-109">**Char**</span></span>  
<span data-ttu-id="098d9-110">Unión de los siguientes miembros.</span><span class="sxs-lookup"><span data-stu-id="098d9-110">A union of the following members.</span></span>

<span data-ttu-id="098d9-111">**UnicodeChar**</span><span class="sxs-lookup"><span data-stu-id="098d9-111">**UnicodeChar**</span></span>  
<span data-ttu-id="098d9-112">Carácter Unicode de una celda de carácter de búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="098d9-112">Unicode character of a screen buffer character cell.</span></span>

<span data-ttu-id="098d9-113">**AsciiChar**</span><span class="sxs-lookup"><span data-stu-id="098d9-113">**AsciiChar**</span></span>  
<span data-ttu-id="098d9-114">Carácter ANSI de una celda de carácter de búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="098d9-114">ANSI character of a screen buffer character cell.</span></span>

<span data-ttu-id="098d9-115">**Atributos**</span><span class="sxs-lookup"><span data-stu-id="098d9-115">**Attributes**</span></span>  
<span data-ttu-id="098d9-116">Atributos de carácter.</span><span class="sxs-lookup"><span data-stu-id="098d9-116">The character attributes.</span></span> <span data-ttu-id="098d9-117">Este miembro puede ser cero o cualquier combinación de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="098d9-117">This member can be zero or any combination of the following values.</span></span>

| <span data-ttu-id="098d9-118">Valor</span><span class="sxs-lookup"><span data-stu-id="098d9-118">Value</span></span> | <span data-ttu-id="098d9-119">Significado</span><span class="sxs-lookup"><span data-stu-id="098d9-119">Meaning</span></span> |
|-|-|
| <span data-ttu-id="098d9-120">**FOREGROUND_BLUE**`0x0001`</span><span class="sxs-lookup"><span data-stu-id="098d9-120">**FOREGROUND_BLUE** `0x0001`</span></span> | <span data-ttu-id="098d9-121">El color del texto contiene azul.</span><span class="sxs-lookup"><span data-stu-id="098d9-121">Text color contains blue.</span></span> |
| <span data-ttu-id="098d9-122">**FOREGROUND_GREEN**`0x0002`</span><span class="sxs-lookup"><span data-stu-id="098d9-122">**FOREGROUND_GREEN** `0x0002`</span></span> | <span data-ttu-id="098d9-123">El color del texto contiene verde.</span><span class="sxs-lookup"><span data-stu-id="098d9-123">Text color contains green.</span></span> |
| <span data-ttu-id="098d9-124">**FOREGROUND_RED**`0x0004`</span><span class="sxs-lookup"><span data-stu-id="098d9-124">**FOREGROUND_RED** `0x0004`</span></span> | <span data-ttu-id="098d9-125">El color del texto contiene rojo.</span><span class="sxs-lookup"><span data-stu-id="098d9-125">Text color contains red.</span></span> |
| <span data-ttu-id="098d9-126">**FOREGROUND_INTENSITY**`0x0008`</span><span class="sxs-lookup"><span data-stu-id="098d9-126">**FOREGROUND_INTENSITY** `0x0008`</span></span> | <span data-ttu-id="098d9-127">El color del texto se intensifica.</span><span class="sxs-lookup"><span data-stu-id="098d9-127">Text color is intensified.</span></span> |
| <span data-ttu-id="098d9-128">**BACKGROUND_BLUE**`0x0010`</span><span class="sxs-lookup"><span data-stu-id="098d9-128">**BACKGROUND_BLUE** `0x0010`</span></span> | <span data-ttu-id="098d9-129">El color de fondo contiene azul.</span><span class="sxs-lookup"><span data-stu-id="098d9-129">Background color contains blue.</span></span> |
| <span data-ttu-id="098d9-130">**BACKGROUND_GREEN**`0x0020`</span><span class="sxs-lookup"><span data-stu-id="098d9-130">**BACKGROUND_GREEN** `0x0020`</span></span> | <span data-ttu-id="098d9-131">El color de fondo contiene verde.</span><span class="sxs-lookup"><span data-stu-id="098d9-131">Background color contains green.</span></span> |
| <span data-ttu-id="098d9-132">**BACKGROUND_RED**`0x0040`</span><span class="sxs-lookup"><span data-stu-id="098d9-132">**BACKGROUND_RED** `0x0040`</span></span> | <span data-ttu-id="098d9-133">El color de fondo contiene rojo.</span><span class="sxs-lookup"><span data-stu-id="098d9-133">Background color contains red.</span></span> |
| <span data-ttu-id="098d9-134">**BACKGROUND_INTENSITY**`0x0080`</span><span class="sxs-lookup"><span data-stu-id="098d9-134">**BACKGROUND_INTENSITY** `0x0080`</span></span> | <span data-ttu-id="098d9-135">El color de fondo se intensifica.</span><span class="sxs-lookup"><span data-stu-id="098d9-135">Background color is intensified.</span></span> |
| <span data-ttu-id="098d9-136">**COMMON_LVB_LEADING_BYTE**`0x0100`</span><span class="sxs-lookup"><span data-stu-id="098d9-136">**COMMON_LVB_LEADING_BYTE** `0x0100`</span></span> | <span data-ttu-id="098d9-137">Byte inicial.</span><span class="sxs-lookup"><span data-stu-id="098d9-137">Leading byte.</span></span> |
| <span data-ttu-id="098d9-138">**COMMON_LVB_TRAILING_BYTE**`0x0200`</span><span class="sxs-lookup"><span data-stu-id="098d9-138">**COMMON_LVB_TRAILING_BYTE** `0x0200`</span></span> | <span data-ttu-id="098d9-139">Byte final.</span><span class="sxs-lookup"><span data-stu-id="098d9-139">Trailing byte.</span></span> |
| <span data-ttu-id="098d9-140">**COMMON_LVB_GRID_HORIZONTAL**`0x0400`</span><span class="sxs-lookup"><span data-stu-id="098d9-140">**COMMON_LVB_GRID_HORIZONTAL** `0x0400`</span></span> | <span data-ttu-id="098d9-141">Horizontal superior.</span><span class="sxs-lookup"><span data-stu-id="098d9-141">Top horizontal.</span></span> |
| <span data-ttu-id="098d9-142">**COMMON_LVB_GRID_LVERTICAL**`0x0800`</span><span class="sxs-lookup"><span data-stu-id="098d9-142">**COMMON_LVB_GRID_LVERTICAL** `0x0800`</span></span> | <span data-ttu-id="098d9-143">Vertical izquierda.</span><span class="sxs-lookup"><span data-stu-id="098d9-143">Left vertical.</span></span> |
| <span data-ttu-id="098d9-144">**COMMON_LVB_GRID_RVERTICAL**`0x1000`</span><span class="sxs-lookup"><span data-stu-id="098d9-144">**COMMON_LVB_GRID_RVERTICAL** `0x1000`</span></span> | <span data-ttu-id="098d9-145">Vertical derecha.</span><span class="sxs-lookup"><span data-stu-id="098d9-145">Right vertical.</span></span> |
| <span data-ttu-id="098d9-146">**COMMON_LVB_REVERSE_VIDEO**`0x4000`</span><span class="sxs-lookup"><span data-stu-id="098d9-146">**COMMON_LVB_REVERSE_VIDEO** `0x4000`</span></span> | <span data-ttu-id="098d9-147">Atributo de primer plano y fondo inverso.</span><span class="sxs-lookup"><span data-stu-id="098d9-147">Reverse foreground and background attribute.</span></span> |
| <span data-ttu-id="098d9-148">**COMMON_LVB_UNDERSCORE**`0x8000`</span><span class="sxs-lookup"><span data-stu-id="098d9-148">**COMMON_LVB_UNDERSCORE** `0x8000`</span></span> | <span data-ttu-id="098d9-149">Guion bajo.</span><span class="sxs-lookup"><span data-stu-id="098d9-149">Underscore.</span></span> |

## <a name="examples"></a><span data-ttu-id="098d9-150">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="098d9-150">Examples</span></span>

<span data-ttu-id="098d9-151">Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="098d9-151">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="098d9-152">Requisitos</span><span class="sxs-lookup"><span data-stu-id="098d9-152">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="098d9-153">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="098d9-153">Minimum supported client</span></span> | <span data-ttu-id="098d9-154">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="098d9-154">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="098d9-155">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="098d9-155">Minimum supported server</span></span> | <span data-ttu-id="098d9-156">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="098d9-156">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="098d9-157">Encabezado</span><span class="sxs-lookup"><span data-stu-id="098d9-157">Header</span></span> | <span data-ttu-id="098d9-158">WinCon. h (incluir Windows. h)</span><span class="sxs-lookup"><span data-stu-id="098d9-158">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="098d9-159">Consulte también</span><span class="sxs-lookup"><span data-stu-id="098d9-159">See also</span></span>

[<span data-ttu-id="098d9-160">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="098d9-160">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="098d9-161">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="098d9-161">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="098d9-162">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="098d9-162">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)
