---
title: Estructura de COORD
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: c8e6f87c3a2730a8af21b9bc064c71900fb82f5b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038313"
---
# <a name="coord-structure"></a><span data-ttu-id="acc0a-104">Estructura de COORD</span><span class="sxs-lookup"><span data-stu-id="acc0a-104">COORD structure</span></span>

<span data-ttu-id="acc0a-105">Define las coordenadas de una celda de caracteres en un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="acc0a-105">Defines the coordinates of a character cell in a console screen buffer.</span></span> <span data-ttu-id="acc0a-106">El origen del sistema de coordenadas (0,0) está en la celda superior izquierda del búfer.</span><span class="sxs-lookup"><span data-stu-id="acc0a-106">The origin of the coordinate system (0,0) is at the top, left cell of the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="acc0a-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="acc0a-107">Syntax</span></span>

```C
typedef struct _COORD {
  SHORT X;
  SHORT Y;
} COORD, *PCOORD;
```

## <a name="members"></a><span data-ttu-id="acc0a-108">Miembros</span><span class="sxs-lookup"><span data-stu-id="acc0a-108">Members</span></span>

<span data-ttu-id="acc0a-109">**X**</span><span class="sxs-lookup"><span data-stu-id="acc0a-109">**X**</span></span>  
<span data-ttu-id="acc0a-110">La coordenada horizontal o el valor de la columna.</span><span class="sxs-lookup"><span data-stu-id="acc0a-110">The horizontal coordinate or column value.</span></span> <span data-ttu-id="acc0a-111">Las unidades dependen de la llamada de función.</span><span class="sxs-lookup"><span data-stu-id="acc0a-111">The units depend on the function call.</span></span>

<span data-ttu-id="acc0a-112">**S**</span><span class="sxs-lookup"><span data-stu-id="acc0a-112">**Y**</span></span>  
<span data-ttu-id="acc0a-113">La coordenada vertical o el valor de fila.</span><span class="sxs-lookup"><span data-stu-id="acc0a-113">The vertical coordinate or row value.</span></span> <span data-ttu-id="acc0a-114">Las unidades dependen de la llamada de función.</span><span class="sxs-lookup"><span data-stu-id="acc0a-114">The units depend on the function call.</span></span>

## <a name="examples"></a><span data-ttu-id="acc0a-115">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="acc0a-115">Examples</span></span>

<span data-ttu-id="acc0a-116">Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="acc0a-116">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="acc0a-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="acc0a-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="acc0a-118">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="acc0a-118">Minimum supported client</span></span> | <span data-ttu-id="acc0a-119">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="acc0a-119">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="acc0a-120">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="acc0a-120">Minimum supported server</span></span> | <span data-ttu-id="acc0a-121">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="acc0a-121">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="acc0a-122">Encabezado</span><span class="sxs-lookup"><span data-stu-id="acc0a-122">Header</span></span> | <span data-ttu-id="acc0a-123">WinConTypes. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="acc0a-123">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="acc0a-124">Consulte también</span><span class="sxs-lookup"><span data-stu-id="acc0a-124">See also</span></span>

[<span data-ttu-id="acc0a-125">**\_información de fuente de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="acc0a-125">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="acc0a-126">**\_información del \_ búfer de pantalla de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="acc0a-126">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="acc0a-127">**\_información de selección de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="acc0a-127">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)

[<span data-ttu-id="acc0a-128">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="acc0a-128">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="acc0a-129">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="acc0a-129">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="acc0a-130">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="acc0a-130">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)

[<span data-ttu-id="acc0a-131">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="acc0a-131">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="acc0a-132">**\_registro de eventos del mouse \_**</span><span class="sxs-lookup"><span data-stu-id="acc0a-132">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="acc0a-133">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="acc0a-133">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="acc0a-134">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="acc0a-134">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="acc0a-135">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="acc0a-135">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="acc0a-136">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="acc0a-136">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="acc0a-137">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="acc0a-137">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="acc0a-138">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="acc0a-138">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)

[<span data-ttu-id="acc0a-139">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="acc0a-139">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="acc0a-140">**\_registro de \_ tamaño de búfer de ventana \_**</span><span class="sxs-lookup"><span data-stu-id="acc0a-140">**WINDOW\_BUFFER\_SIZE\_RECORD**</span></span>](window-buffer-size-record-str.md)

[<span data-ttu-id="acc0a-141">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="acc0a-141">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="acc0a-142">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="acc0a-142">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="acc0a-143">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="acc0a-143">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
