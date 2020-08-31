---
title: COORDENADAS de la estructura
description: Define las coordenadas de una celda de caracteres en un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/COORD
- wincon/COORD
- COORD
- wincontypes/PCOORD
- wincon/PCOORD
- PCOORD
MS-HAID:
- '\_win32\_coord\_str'
- base.coord\_str
- consoles.coord\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d730c46e-ea17-475e-b956-8ee5f4f5c04e
topic_type:
- apiref
api_name:
- COORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: c29594cbddd69ae8ca6d3f958acd0eeb3cb60e9b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060776"
---
# <a name="coord-structure"></a><span data-ttu-id="0855f-104">COORDENADAS de la estructura</span><span class="sxs-lookup"><span data-stu-id="0855f-104">COORD structure</span></span>


<span data-ttu-id="0855f-105">Define las coordenadas de una celda de caracteres en un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="0855f-105">Defines the coordinates of a character cell in a console screen buffer.</span></span> <span data-ttu-id="0855f-106">El origen del sistema de coordenadas (0,0) está en la celda superior izquierda del búfer.</span><span class="sxs-lookup"><span data-stu-id="0855f-106">The origin of the coordinate system (0,0) is at the top, left cell of the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="0855f-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0855f-107">Syntax</span></span>
------

```C
typedef struct _COORD {
  SHORT X;
  SHORT Y;
} COORD, *PCOORD;
```

<a name="members"></a><span data-ttu-id="0855f-108">Miembros</span><span class="sxs-lookup"><span data-stu-id="0855f-108">Members</span></span>
-------

<span data-ttu-id="0855f-109">**X**</span><span class="sxs-lookup"><span data-stu-id="0855f-109">**X**</span></span>  
<span data-ttu-id="0855f-110">La coordenada horizontal o el valor de la columna.</span><span class="sxs-lookup"><span data-stu-id="0855f-110">The horizontal coordinate or column value.</span></span> <span data-ttu-id="0855f-111">Las unidades dependen de la llamada de función.</span><span class="sxs-lookup"><span data-stu-id="0855f-111">The units depend on the function call.</span></span>

<span data-ttu-id="0855f-112">**S**</span><span class="sxs-lookup"><span data-stu-id="0855f-112">**Y**</span></span>  
<span data-ttu-id="0855f-113">La coordenada vertical o el valor de fila.</span><span class="sxs-lookup"><span data-stu-id="0855f-113">The vertical coordinate or row value.</span></span> <span data-ttu-id="0855f-114">Las unidades dependen de la llamada de función.</span><span class="sxs-lookup"><span data-stu-id="0855f-114">The units depend on the function call.</span></span>

<a name="examples"></a><span data-ttu-id="0855f-115">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="0855f-115">Examples</span></span>
--------

<span data-ttu-id="0855f-116">Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="0855f-116">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="0855f-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0855f-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="0855f-118">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="0855f-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="0855f-119">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="0855f-119">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0855f-120">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="0855f-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="0855f-121">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="0855f-121">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0855f-122">Encabezado</span><span class="sxs-lookup"><span data-stu-id="0855f-122">Header</span></span></p></td>
<td><span data-ttu-id="0855f-123">WinConTypes. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0855f-123">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="0855f-124"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="0855f-124"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="0855f-125">**\_información de fuente de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="0855f-125">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="0855f-126">**\_información del \_ búfer de pantalla de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="0855f-126">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="0855f-127">**\_información de selección de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="0855f-127">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)

[<span data-ttu-id="0855f-128">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="0855f-128">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="0855f-129">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="0855f-129">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="0855f-130">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="0855f-130">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)

[<span data-ttu-id="0855f-131">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="0855f-131">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="0855f-132">**\_registro de eventos del mouse \_**</span><span class="sxs-lookup"><span data-stu-id="0855f-132">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="0855f-133">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="0855f-133">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="0855f-134">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="0855f-134">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="0855f-135">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="0855f-135">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="0855f-136">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="0855f-136">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="0855f-137">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="0855f-137">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="0855f-138">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="0855f-138">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)

[<span data-ttu-id="0855f-139">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="0855f-139">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="0855f-140">**\_registro de \_ tamaño de búfer de ventana \_**</span><span class="sxs-lookup"><span data-stu-id="0855f-140">**WINDOW\_BUFFER\_SIZE\_RECORD**</span></span>](window-buffer-size-record-str.md)

[<span data-ttu-id="0855f-141">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="0855f-141">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="0855f-142">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="0855f-142">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="0855f-143">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="0855f-143">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 




