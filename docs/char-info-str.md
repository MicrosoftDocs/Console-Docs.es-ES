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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 6244edaa06b6dd69f8ab3962cf42cb893d08f699
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060909"
---
# <a name="char_info-structure"></a><span data-ttu-id="1c901-105">\_Estructura char info</span><span class="sxs-lookup"><span data-stu-id="1c901-105">CHAR\_INFO structure</span></span>


<span data-ttu-id="1c901-106">Especifica un carácter Unicode o ANSI y sus atributos.</span><span class="sxs-lookup"><span data-stu-id="1c901-106">Specifies a Unicode or ANSI character and its attributes.</span></span> <span data-ttu-id="1c901-107">Las funciones de consola utilizan esta estructura para leer y escribir en un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="1c901-107">This structure is used by console functions to read from and write to a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="1c901-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1c901-108">Syntax</span></span>
------

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

<a name="members"></a><span data-ttu-id="1c901-109">Miembros</span><span class="sxs-lookup"><span data-stu-id="1c901-109">Members</span></span>
-------

<span data-ttu-id="1c901-110">**Char**</span><span class="sxs-lookup"><span data-stu-id="1c901-110">**Char**</span></span>  
<span data-ttu-id="1c901-111">Unión de los siguientes miembros.</span><span class="sxs-lookup"><span data-stu-id="1c901-111">A union of the following members.</span></span>

<span data-ttu-id="1c901-112">**UnicodeChar**</span><span class="sxs-lookup"><span data-stu-id="1c901-112">**UnicodeChar**</span></span>  
<span data-ttu-id="1c901-113">Carácter Unicode de una celda de carácter de búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="1c901-113">Unicode character of a screen buffer character cell.</span></span>

<span data-ttu-id="1c901-114">**AsciiChar**</span><span class="sxs-lookup"><span data-stu-id="1c901-114">**AsciiChar**</span></span>  
<span data-ttu-id="1c901-115">Carácter ANSI de una celda de carácter de búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="1c901-115">ANSI character of a screen buffer character cell.</span></span>

<span data-ttu-id="1c901-116">**Atributos**</span><span class="sxs-lookup"><span data-stu-id="1c901-116">**Attributes**</span></span>  
<span data-ttu-id="1c901-117">Atributos de carácter.</span><span class="sxs-lookup"><span data-stu-id="1c901-117">The character attributes.</span></span> <span data-ttu-id="1c901-118">Este miembro puede ser cero o cualquier combinación de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="1c901-118">This member can be zero or any combination of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="1c901-119">Valor</span><span class="sxs-lookup"><span data-stu-id="1c901-119">Value</span></span></th>
<th><span data-ttu-id="1c901-120">Significado</span><span class="sxs-lookup"><span data-stu-id="1c901-120">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="1c901-121"><span id="FOREGROUND_BLUE"></span><span id="foreground_blue"></span>
<strong>FOREGROUND_BLUE</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="1c901-121"><span id="FOREGROUND_BLUE"></span><span id="foreground_blue"></span>
<strong>FOREGROUND_BLUE</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="1c901-122">El color del texto contiene el azul.</span><span class="sxs-lookup"><span data-stu-id="1c901-122">Text color contains blue.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="1c901-123"><span id="FOREGROUND_GREEN"></span><span id="foreground_green"></span>
<strong>FOREGROUND_GREEN</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="1c901-123"><span id="FOREGROUND_GREEN"></span><span id="foreground_green"></span>
<strong>FOREGROUND_GREEN</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="1c901-124">El color del texto contiene verde.</span><span class="sxs-lookup"><span data-stu-id="1c901-124">Text color contains green.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="1c901-125"><span id="FOREGROUND_RED"></span><span id="foreground_red"></span>
<strong>FOREGROUND_RED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="1c901-125"><span id="FOREGROUND_RED"></span><span id="foreground_red"></span>
<strong>FOREGROUND_RED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="1c901-126">El color del texto contiene rojo.</span><span class="sxs-lookup"><span data-stu-id="1c901-126">Text color contains red.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="1c901-127"><span id="FOREGROUND_INTENSITY"></span><span id="foreground_intensity"></span>
<strong>FOREGROUND_INTENSITY</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="1c901-127"><span id="FOREGROUND_INTENSITY"></span><span id="foreground_intensity"></span>
<strong>FOREGROUND_INTENSITY</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="1c901-128">El color del texto se intensifica.</span><span class="sxs-lookup"><span data-stu-id="1c901-128">Text color is intensified.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="1c901-129"><span id="BACKGROUND_BLUE"></span><span id="background_blue"></span>
<strong>BACKGROUND_BLUE</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="1c901-129"><span id="BACKGROUND_BLUE"></span><span id="background_blue"></span>
<strong>BACKGROUND_BLUE</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="1c901-130">El color de fondo contiene el azul.</span><span class="sxs-lookup"><span data-stu-id="1c901-130">Background color contains blue.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="1c901-131"><span id="BACKGROUND_GREEN"></span><span id="background_green"></span>
<strong>BACKGROUND_GREEN</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="1c901-131"><span id="BACKGROUND_GREEN"></span><span id="background_green"></span>
<strong>BACKGROUND_GREEN</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="1c901-132">El color de fondo contiene verde.</span><span class="sxs-lookup"><span data-stu-id="1c901-132">Background color contains green.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="1c901-133"><span id="BACKGROUND_RED"></span><span id="background_red"></span>
<strong>BACKGROUND_RED</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="1c901-133"><span id="BACKGROUND_RED"></span><span id="background_red"></span>
<strong>BACKGROUND_RED</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="1c901-134">El color de fondo contiene rojo.</span><span class="sxs-lookup"><span data-stu-id="1c901-134">Background color contains red.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="1c901-135"><span id="BACKGROUND_INTENSITY"></span><span id="background_intensity"></span>
<strong>BACKGROUND_INTENSITY</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="1c901-135"><span id="BACKGROUND_INTENSITY"></span><span id="background_intensity"></span>
<strong>BACKGROUND_INTENSITY</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="1c901-136">Se intensifica el color de fondo.</span><span class="sxs-lookup"><span data-stu-id="1c901-136">Background color is intensified.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="1c901-137"><span id="COMMON_LVB_LEADING_BYTE"></span><span id="common_lvb_leading_byte"></span>
<strong>COMMON_LVB_LEADING_BYTE</strong> 0x0100</span><span class="sxs-lookup"><span data-stu-id="1c901-137"><span id="COMMON_LVB_LEADING_BYTE"></span><span id="common_lvb_leading_byte"></span>
<strong>COMMON_LVB_LEADING_BYTE</strong> 0x0100</span></span></td>
<td><p><span data-ttu-id="1c901-138">Byte inicial.</span><span class="sxs-lookup"><span data-stu-id="1c901-138">Leading byte.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="1c901-139"><span id="COMMON_LVB_TRAILING_BYTE"></span><span id="common_lvb_trailing_byte"></span>
<strong>COMMON_LVB_TRAILING_BYTE</strong> 0x0200</span><span class="sxs-lookup"><span data-stu-id="1c901-139"><span id="COMMON_LVB_TRAILING_BYTE"></span><span id="common_lvb_trailing_byte"></span>
<strong>COMMON_LVB_TRAILING_BYTE</strong> 0x0200</span></span></td>
<td><p><span data-ttu-id="1c901-140">Byte final.</span><span class="sxs-lookup"><span data-stu-id="1c901-140">Trailing byte.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="1c901-141"><span id="COMMON_LVB_GRID_HORIZONTAL"></span><span id="common_lvb_grid_horizontal"></span>
<strong>COMMON_LVB_GRID_HORIZONTAL</strong> 0x0400</span><span class="sxs-lookup"><span data-stu-id="1c901-141"><span id="COMMON_LVB_GRID_HORIZONTAL"></span><span id="common_lvb_grid_horizontal"></span>
<strong>COMMON_LVB_GRID_HORIZONTAL</strong> 0x0400</span></span></td>
<td><p><span data-ttu-id="1c901-142">Horizontal superior</span><span class="sxs-lookup"><span data-stu-id="1c901-142">Top horizontal</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="1c901-143"><span id="COMMON_LVB_GRID_LVERTICAL"></span><span id="common_lvb_grid_lvertical"></span>
<strong>COMMON_LVB_GRID_LVERTICAL</strong> 0x0800</span><span class="sxs-lookup"><span data-stu-id="1c901-143"><span id="COMMON_LVB_GRID_LVERTICAL"></span><span id="common_lvb_grid_lvertical"></span>
<strong>COMMON_LVB_GRID_LVERTICAL</strong> 0x0800</span></span></td>
<td><p><span data-ttu-id="1c901-144">Vertical izquierda.</span><span class="sxs-lookup"><span data-stu-id="1c901-144">Left vertical.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="1c901-145"><span id="COMMON_LVB_GRID_RVERTICAL"></span><span id="common_lvb_grid_rvertical"></span>
<strong>COMMON_LVB_GRID_RVERTICAL</strong> 0x1000</span><span class="sxs-lookup"><span data-stu-id="1c901-145"><span id="COMMON_LVB_GRID_RVERTICAL"></span><span id="common_lvb_grid_rvertical"></span>
<strong>COMMON_LVB_GRID_RVERTICAL</strong> 0x1000</span></span></td>
<td><p><span data-ttu-id="1c901-146">Vertical derecha.</span><span class="sxs-lookup"><span data-stu-id="1c901-146">Right vertical.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="1c901-147"><span id="COMMON_LVB_REVERSE_VIDEO"></span><span id="common_lvb_reverse_video"></span>
<strong>COMMON_LVB_REVERSE_VIDEO</strong> 0x4000</span><span class="sxs-lookup"><span data-stu-id="1c901-147"><span id="COMMON_LVB_REVERSE_VIDEO"></span><span id="common_lvb_reverse_video"></span>
<strong>COMMON_LVB_REVERSE_VIDEO</strong> 0x4000</span></span></td>
<td><p><span data-ttu-id="1c901-148">Atributo de primer plano y fondo inverso.</span><span class="sxs-lookup"><span data-stu-id="1c901-148">Reverse foreground and background attribute.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="1c901-149"><span id="COMMON_LVB_UNDERSCORE"></span><span id="common_lvb_underscore"></span>
<strong>COMMON_LVB_UNDERSCORE</strong> 0x8000</span><span class="sxs-lookup"><span data-stu-id="1c901-149"><span id="COMMON_LVB_UNDERSCORE"></span><span id="common_lvb_underscore"></span>
<strong>COMMON_LVB_UNDERSCORE</strong> 0x8000</span></span></td>
<td><p><span data-ttu-id="1c901-150">Subrayado.</span><span class="sxs-lookup"><span data-stu-id="1c901-150">Underscore.</span></span></p></td>
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

 

<a name="examples"></a><span data-ttu-id="1c901-151">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="1c901-151">Examples</span></span>
--------

<span data-ttu-id="1c901-152">Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="1c901-152">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="1c901-153">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1c901-153">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="1c901-154">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="1c901-154">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="1c901-155">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="1c901-155">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1c901-156">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="1c901-156">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="1c901-157">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="1c901-157">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1c901-158">Encabezado</span><span class="sxs-lookup"><span data-stu-id="1c901-158">Header</span></span></p></td>
<td><span data-ttu-id="1c901-159">WINCON. h (incluir Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1c901-159">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="1c901-160"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="1c901-160"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="1c901-161">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="1c901-161">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="1c901-162">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="1c901-162">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="1c901-163">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="1c901-163">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

 

 




