---
title: Estructura de CONSOLE_SELECTION_INFO
description: Consulte la información de referencia sobre la estructura de CONSOLE_SELECTION_INFO, que contiene información para una selección de consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/CONSOLE_SELECTION_INFO
- wincon/CONSOLE_SELECTION_INFO
- CONSOLE_SELECTION_INFO
- consoleapi3/PCONSOLE_SELECTION_INFO
- wincon/PCONSOLE_SELECTION_INFO
- PCONSOLE_SELECTION_INFO
MS-HAID:
- '\_win32\_console\_selection\_info\_str'
- base.console\_selection\_info\_str
- consoles.console\_selection\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9530b249-8db4-4516-9cc8-2b452c6751f9
topic_type:
- apiref
api_name:
- CONSOLE_SELECTION_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: a16fe43e7b7cc4b5890284921823aee7b79217b2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060805"
---
# <a name="console_selection_info-structure"></a><span data-ttu-id="66cac-104">Estructura de información de \_ selección de consola \_</span><span class="sxs-lookup"><span data-stu-id="66cac-104">CONSOLE\_SELECTION\_INFO structure</span></span>


<span data-ttu-id="66cac-105">Contiene información para una selección de consola.</span><span class="sxs-lookup"><span data-stu-id="66cac-105">Contains information for a console selection.</span></span>

<a name="syntax"></a><span data-ttu-id="66cac-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="66cac-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

<a name="members"></a><span data-ttu-id="66cac-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="66cac-107">Members</span></span>
-------

<span data-ttu-id="66cac-108">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="66cac-108">**dwFlags**</span></span>  
<span data-ttu-id="66cac-109">El indicador de selección.</span><span class="sxs-lookup"><span data-stu-id="66cac-109">The selection indicator.</span></span> <span data-ttu-id="66cac-110">Este miembro puede ser uno o varios de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="66cac-110">This member can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="66cac-111">Valor</span><span class="sxs-lookup"><span data-stu-id="66cac-111">Value</span></span></th>
<th><span data-ttu-id="66cac-112">Significado</span><span class="sxs-lookup"><span data-stu-id="66cac-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="66cac-113"><span id="CONSOLE_MOUSE_DOWN"></span><span id="console_mouse_down"></span>
<strong>CONSOLE_MOUSE_DOWN</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="66cac-113"><span id="CONSOLE_MOUSE_DOWN"></span><span id="console_mouse_down"></span>
<strong>CONSOLE_MOUSE_DOWN</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="66cac-114">El mouse está inactivo</span><span class="sxs-lookup"><span data-stu-id="66cac-114">Mouse is down</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="66cac-115"><span id="CONSOLE_MOUSE_SELECTION"></span><span id="console_mouse_selection"></span>
<strong>CONSOLE_MOUSE_SELECTION</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="66cac-115"><span id="CONSOLE_MOUSE_SELECTION"></span><span id="console_mouse_selection"></span>
<strong>CONSOLE_MOUSE_SELECTION</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="66cac-116">Seleccionar con el mouse</span><span class="sxs-lookup"><span data-stu-id="66cac-116">Selecting with the mouse</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="66cac-117"><span id="CONSOLE_NO_SELECTION"></span><span id="console_no_selection"></span>
<strong>CONSOLE_NO_SELECTION</strong> 0x0000</span><span class="sxs-lookup"><span data-stu-id="66cac-117"><span id="CONSOLE_NO_SELECTION"></span><span id="console_no_selection"></span>
<strong>CONSOLE_NO_SELECTION</strong> 0x0000</span></span></td>
<td><p><span data-ttu-id="66cac-118">Sin selección</span><span class="sxs-lookup"><span data-stu-id="66cac-118">No selection</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="66cac-119"><span id="CONSOLE_SELECTION_IN_PROGRESS"></span><span id="console_selection_in_progress"></span>
<strong>CONSOLE_SELECTION_IN_PROGRESS</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="66cac-119"><span id="CONSOLE_SELECTION_IN_PROGRESS"></span><span id="console_selection_in_progress"></span>
<strong>CONSOLE_SELECTION_IN_PROGRESS</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="66cac-120">La selección ha empezado</span><span class="sxs-lookup"><span data-stu-id="66cac-120">Selection has begun</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="66cac-121"><span id="CONSOLE_SELECTION_NOT_EMPTY"></span><span id="console_selection_not_empty"></span>
<strong>CONSOLE_SELECTION_NOT_EMPTY</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="66cac-121"><span id="CONSOLE_SELECTION_NOT_EMPTY"></span><span id="console_selection_not_empty"></span>
<strong>CONSOLE_SELECTION_NOT_EMPTY</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="66cac-122">El rectángulo de selección no está vacío</span><span class="sxs-lookup"><span data-stu-id="66cac-122">Selection rectangle is not empty</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="66cac-123">**dwSelectionAnchor**</span><span class="sxs-lookup"><span data-stu-id="66cac-123">**dwSelectionAnchor**</span></span>  
<span data-ttu-id="66cac-124">Estructura de [**coordenadas**](coord-str.md) que especifica el delimitador de selección, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="66cac-124">A [**COORD**](coord-str.md) structure that specifies the selection anchor, in characters.</span></span>

<span data-ttu-id="66cac-125">**srSelection**</span><span class="sxs-lookup"><span data-stu-id="66cac-125">**srSelection**</span></span>  
<span data-ttu-id="66cac-126">[**Pequeña estructura \_ Rect**](small-rect-str.md) que especifica el rectángulo de selección.</span><span class="sxs-lookup"><span data-stu-id="66cac-126">A [**SMALL\_RECT**](small-rect-str.md) structure that specifies the selection rectangle.</span></span>

<a name="requirements"></a><span data-ttu-id="66cac-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="66cac-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="66cac-128">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="66cac-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="66cac-129">Windows XP [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="66cac-129">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="66cac-130">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="66cac-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="66cac-131">Windows Server 2003 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="66cac-131">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="66cac-132">Encabezado</span><span class="sxs-lookup"><span data-stu-id="66cac-132">Header</span></span></p></td>
<td><span data-ttu-id="66cac-133">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="66cac-133">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="66cac-134"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="66cac-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="66cac-135">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="66cac-135">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="66cac-136">**GetConsoleSelectionInfo**</span><span class="sxs-lookup"><span data-stu-id="66cac-136">**GetConsoleSelectionInfo**</span></span>](getconsoleselectioninfo.md)

[<span data-ttu-id="66cac-137">**PEQUEÑO \_ rectángulo**</span><span class="sxs-lookup"><span data-stu-id="66cac-137">**SMALL\_RECT**</span></span>](small-rect-str.md)

 

 




