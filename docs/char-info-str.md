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
ms.openlocfilehash: b07938d6ac58744533711c91a04b1a0188f7daf6
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037383"
---
# <a name="char_info-structure"></a><span data-ttu-id="7a374-105">\_Estructura char info</span><span class="sxs-lookup"><span data-stu-id="7a374-105">CHAR\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="7a374-106">Especifica un carácter Unicode o ANSI y sus atributos.</span><span class="sxs-lookup"><span data-stu-id="7a374-106">Specifies a Unicode or ANSI character and its attributes.</span></span> <span data-ttu-id="7a374-107">Las funciones de consola utilizan esta estructura para leer y escribir en un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="7a374-107">This structure is used by console functions to read from and write to a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="7a374-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7a374-108">Syntax</span></span>

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

## <a name="members"></a><span data-ttu-id="7a374-109">Miembros</span><span class="sxs-lookup"><span data-stu-id="7a374-109">Members</span></span>

<span data-ttu-id="7a374-110">**Char**</span><span class="sxs-lookup"><span data-stu-id="7a374-110">**Char**</span></span>  
<span data-ttu-id="7a374-111">Unión de los siguientes miembros.</span><span class="sxs-lookup"><span data-stu-id="7a374-111">A union of the following members.</span></span>

<span data-ttu-id="7a374-112">**UnicodeChar**</span><span class="sxs-lookup"><span data-stu-id="7a374-112">**UnicodeChar**</span></span>  
<span data-ttu-id="7a374-113">Carácter Unicode de una celda de carácter de búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="7a374-113">Unicode character of a screen buffer character cell.</span></span>

<span data-ttu-id="7a374-114">**AsciiChar**</span><span class="sxs-lookup"><span data-stu-id="7a374-114">**AsciiChar**</span></span>  
<span data-ttu-id="7a374-115">Carácter ANSI de una celda de carácter de búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="7a374-115">ANSI character of a screen buffer character cell.</span></span>

<span data-ttu-id="7a374-116">**Atributos**</span><span class="sxs-lookup"><span data-stu-id="7a374-116">**Attributes**</span></span>  
<span data-ttu-id="7a374-117">Atributos de carácter.</span><span class="sxs-lookup"><span data-stu-id="7a374-117">The character attributes.</span></span> <span data-ttu-id="7a374-118">Este miembro puede ser cero o cualquier combinación de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="7a374-118">This member can be zero or any combination of the following values.</span></span>

| <span data-ttu-id="7a374-119">Valor</span><span class="sxs-lookup"><span data-stu-id="7a374-119">Value</span></span> | <span data-ttu-id="7a374-120">Significado</span><span class="sxs-lookup"><span data-stu-id="7a374-120">Meaning</span></span> |
|-|-|
| <span data-ttu-id="7a374-121">**FOREGROUND_BLUE**`0x0001`</span><span class="sxs-lookup"><span data-stu-id="7a374-121">**FOREGROUND_BLUE** `0x0001`</span></span> | <span data-ttu-id="7a374-122">El color del texto contiene el azul.</span><span class="sxs-lookup"><span data-stu-id="7a374-122">Text color contains blue.</span></span> |
| <span data-ttu-id="7a374-123">**FOREGROUND_GREEN**`0x0002`</span><span class="sxs-lookup"><span data-stu-id="7a374-123">**FOREGROUND_GREEN** `0x0002`</span></span> | <span data-ttu-id="7a374-124">El color del texto contiene verde.</span><span class="sxs-lookup"><span data-stu-id="7a374-124">Text color contains green.</span></span> |
| <span data-ttu-id="7a374-125">**FOREGROUND_RED**`0x0004`</span><span class="sxs-lookup"><span data-stu-id="7a374-125">**FOREGROUND_RED** `0x0004`</span></span> | <span data-ttu-id="7a374-126">El color del texto contiene rojo.</span><span class="sxs-lookup"><span data-stu-id="7a374-126">Text color contains red.</span></span> |
| <span data-ttu-id="7a374-127">**FOREGROUND_INTENSITY**`0x0008`</span><span class="sxs-lookup"><span data-stu-id="7a374-127">**FOREGROUND_INTENSITY** `0x0008`</span></span> | <span data-ttu-id="7a374-128">El color del texto se intensifica.</span><span class="sxs-lookup"><span data-stu-id="7a374-128">Text color is intensified.</span></span> |
| <span data-ttu-id="7a374-129">**BACKGROUND_BLUE**`0x0010`</span><span class="sxs-lookup"><span data-stu-id="7a374-129">**BACKGROUND_BLUE** `0x0010`</span></span> | <span data-ttu-id="7a374-130">El color de fondo contiene el azul.</span><span class="sxs-lookup"><span data-stu-id="7a374-130">Background color contains blue.</span></span> |
| <span data-ttu-id="7a374-131">**BACKGROUND_GREEN**`0x0020`</span><span class="sxs-lookup"><span data-stu-id="7a374-131">**BACKGROUND_GREEN** `0x0020`</span></span> | <span data-ttu-id="7a374-132">El color de fondo contiene verde.</span><span class="sxs-lookup"><span data-stu-id="7a374-132">Background color contains green.</span></span> |
| <span data-ttu-id="7a374-133">**BACKGROUND_RED**`0x0040`</span><span class="sxs-lookup"><span data-stu-id="7a374-133">**BACKGROUND_RED** `0x0040`</span></span> | <span data-ttu-id="7a374-134">El color de fondo contiene rojo.</span><span class="sxs-lookup"><span data-stu-id="7a374-134">Background color contains red.</span></span> |
| <span data-ttu-id="7a374-135">**BACKGROUND_INTENSITY**`0x0080`</span><span class="sxs-lookup"><span data-stu-id="7a374-135">**BACKGROUND_INTENSITY** `0x0080`</span></span> | <span data-ttu-id="7a374-136">Se intensifica el color de fondo.</span><span class="sxs-lookup"><span data-stu-id="7a374-136">Background color is intensified.</span></span> |
| <span data-ttu-id="7a374-137">**COMMON_LVB_LEADING_BYTE**`0x0100`</span><span class="sxs-lookup"><span data-stu-id="7a374-137">**COMMON_LVB_LEADING_BYTE** `0x0100`</span></span> | <span data-ttu-id="7a374-138">Byte inicial.</span><span class="sxs-lookup"><span data-stu-id="7a374-138">Leading byte.</span></span> |
| <span data-ttu-id="7a374-139">**COMMON_LVB_TRAILING_BYTE**`0x0200`</span><span class="sxs-lookup"><span data-stu-id="7a374-139">**COMMON_LVB_TRAILING_BYTE** `0x0200`</span></span> | <span data-ttu-id="7a374-140">Byte final.</span><span class="sxs-lookup"><span data-stu-id="7a374-140">Trailing byte.</span></span> |
| <span data-ttu-id="7a374-141">**COMMON_LVB_GRID_HORIZONTAL**`0x0400`</span><span class="sxs-lookup"><span data-stu-id="7a374-141">**COMMON_LVB_GRID_HORIZONTAL** `0x0400`</span></span> | <span data-ttu-id="7a374-142">Horizontal superior.</span><span class="sxs-lookup"><span data-stu-id="7a374-142">Top horizontal.</span></span> |
| <span data-ttu-id="7a374-143">**COMMON_LVB_GRID_LVERTICAL**`0x0800`</span><span class="sxs-lookup"><span data-stu-id="7a374-143">**COMMON_LVB_GRID_LVERTICAL** `0x0800`</span></span> | <span data-ttu-id="7a374-144">Vertical izquierda.</span><span class="sxs-lookup"><span data-stu-id="7a374-144">Left vertical.</span></span> |
| <span data-ttu-id="7a374-145">**COMMON_LVB_GRID_RVERTICAL**`0x1000`</span><span class="sxs-lookup"><span data-stu-id="7a374-145">**COMMON_LVB_GRID_RVERTICAL** `0x1000`</span></span> | <span data-ttu-id="7a374-146">Vertical derecha.</span><span class="sxs-lookup"><span data-stu-id="7a374-146">Right vertical.</span></span> |
| <span data-ttu-id="7a374-147">**COMMON_LVB_REVERSE_VIDEO**`0x4000`</span><span class="sxs-lookup"><span data-stu-id="7a374-147">**COMMON_LVB_REVERSE_VIDEO** `0x4000`</span></span> | <span data-ttu-id="7a374-148">Atributo de primer plano y fondo inverso.</span><span class="sxs-lookup"><span data-stu-id="7a374-148">Reverse foreground and background attribute.</span></span> |
| <span data-ttu-id="7a374-149">**COMMON_LVB_UNDERSCORE**`0x8000`</span><span class="sxs-lookup"><span data-stu-id="7a374-149">**COMMON_LVB_UNDERSCORE** `0x8000`</span></span> | <span data-ttu-id="7a374-150">Subrayado.</span><span class="sxs-lookup"><span data-stu-id="7a374-150">Underscore.</span></span> |

## <a name="examples"></a><span data-ttu-id="7a374-151">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="7a374-151">Examples</span></span>

<span data-ttu-id="7a374-152">Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="7a374-152">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="7a374-153">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a374-153">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="7a374-154">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="7a374-154">Minimum supported client</span></span> | <span data-ttu-id="7a374-155">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="7a374-155">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="7a374-156">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="7a374-156">Minimum supported server</span></span> | <span data-ttu-id="7a374-157">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="7a374-157">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="7a374-158">Encabezado</span><span class="sxs-lookup"><span data-stu-id="7a374-158">Header</span></span> | <span data-ttu-id="7a374-159">WinCon. h (incluir Windows. h)</span><span class="sxs-lookup"><span data-stu-id="7a374-159">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="7a374-160">Consulte también</span><span class="sxs-lookup"><span data-stu-id="7a374-160">See also</span></span>

[<span data-ttu-id="7a374-161">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="7a374-161">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="7a374-162">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="7a374-162">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="7a374-163">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="7a374-163">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)
