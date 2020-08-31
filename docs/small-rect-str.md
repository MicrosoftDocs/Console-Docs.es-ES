---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/SMALL_RECT
- wincon/SMALL_RECT
- SMALL_RECT
title: Estructura de SMALL_RECT
description: Define las coordenadas de las esquinas superior izquierda e inferior derecha de un rectángulo.
MS-HAID:
- '\_win32\_small\_rect\_str'
- base.small\_rect\_str
- consoles.small\_rect\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 62639815-c7e9-4ae2-b152-61290f78422b
topic_type:
- apiref
api_name:
- SMALL_RECT
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: b0c0bfe93c85af89c5aaefeda032795de72ed627
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061118"
---
# <a name="small_rect-structure"></a><span data-ttu-id="a46e8-104">PEQUEÑA \_ estructura Rect</span><span class="sxs-lookup"><span data-stu-id="a46e8-104">SMALL\_RECT structure</span></span>


<span data-ttu-id="a46e8-105">Define las coordenadas de las esquinas superior izquierda e inferior derecha de un rectángulo.</span><span class="sxs-lookup"><span data-stu-id="a46e8-105">Defines the coordinates of the upper left and lower right corners of a rectangle.</span></span>

<a name="syntax"></a><span data-ttu-id="a46e8-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="a46e8-106">Syntax</span></span>
------

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

<a name="members"></a><span data-ttu-id="a46e8-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="a46e8-107">Members</span></span>
-------

<span data-ttu-id="a46e8-108">**Left**</span><span class="sxs-lookup"><span data-stu-id="a46e8-108">**Left**</span></span>  
<span data-ttu-id="a46e8-109">Coordenada x de la esquina superior izquierda del rectángulo.</span><span class="sxs-lookup"><span data-stu-id="a46e8-109">The x-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="a46e8-110">**Top** (Principales)</span><span class="sxs-lookup"><span data-stu-id="a46e8-110">**Top**</span></span>  
<span data-ttu-id="a46e8-111">Coordenada y de la esquina superior izquierda del rectángulo.</span><span class="sxs-lookup"><span data-stu-id="a46e8-111">The y-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="a46e8-112">**Right**</span><span class="sxs-lookup"><span data-stu-id="a46e8-112">**Right**</span></span>  
<span data-ttu-id="a46e8-113">Coordenada x de la esquina inferior derecha del rectángulo.</span><span class="sxs-lookup"><span data-stu-id="a46e8-113">The x-coordinate of the lower right corner of the rectangle.</span></span>

<span data-ttu-id="a46e8-114">**Inferior**</span><span class="sxs-lookup"><span data-stu-id="a46e8-114">**Bottom**</span></span>  
<span data-ttu-id="a46e8-115">Coordenada y de la esquina inferior derecha del rectángulo.</span><span class="sxs-lookup"><span data-stu-id="a46e8-115">The y-coordinate of the lower right corner of the rectangle.</span></span>

<a name="remarks"></a><span data-ttu-id="a46e8-116">Observaciones</span><span class="sxs-lookup"><span data-stu-id="a46e8-116">Remarks</span></span>
-------

<span data-ttu-id="a46e8-117">Las funciones de consola utilizan esta estructura para especificar áreas rectangulares de búferes de pantalla de la consola, donde las coordenadas especifican las filas y columnas de las celdas de caracteres del búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="a46e8-117">This structure is used by console functions to specify rectangular areas of console screen buffers, where the coordinates specify the rows and columns of screen-buffer character cells.</span></span>

<a name="examples"></a><span data-ttu-id="a46e8-118">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="a46e8-118">Examples</span></span>
--------

<span data-ttu-id="a46e8-119">Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="a46e8-119">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="a46e8-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a46e8-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="a46e8-121">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="a46e8-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="a46e8-122">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="a46e8-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a46e8-123">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="a46e8-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="a46e8-124">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="a46e8-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a46e8-125">Encabezado</span><span class="sxs-lookup"><span data-stu-id="a46e8-125">Header</span></span></p></td>
<td><span data-ttu-id="a46e8-126">WinConTypes. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="a46e8-126">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="a46e8-127"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="a46e8-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="a46e8-128">**RECT**</span><span class="sxs-lookup"><span data-stu-id="a46e8-128">**RECT**</span></span>](https://msdn.microsoft.com/library/windows/desktop/dd162897)

[<span data-ttu-id="a46e8-129">**RECTl**</span><span class="sxs-lookup"><span data-stu-id="a46e8-129">**RECTL**</span></span>](https://msdn.microsoft.com/library/windows/desktop/dd162907)

 

 




