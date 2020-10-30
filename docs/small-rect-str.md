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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 93121864c8754b281b92051a5e4a174b2d5956a3
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037103"
---
# <a name="small_rect-structure"></a><span data-ttu-id="b48c5-104">PEQUEÑA \_ estructura Rect</span><span class="sxs-lookup"><span data-stu-id="b48c5-104">SMALL\_RECT structure</span></span>

<span data-ttu-id="b48c5-105">Define las coordenadas de las esquinas superior izquierda e inferior derecha de un rectángulo.</span><span class="sxs-lookup"><span data-stu-id="b48c5-105">Defines the coordinates of the upper left and lower right corners of a rectangle.</span></span>

## <a name="syntax"></a><span data-ttu-id="b48c5-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b48c5-106">Syntax</span></span>

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

## <a name="members"></a><span data-ttu-id="b48c5-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="b48c5-107">Members</span></span>

<span data-ttu-id="b48c5-108">**Left**</span><span class="sxs-lookup"><span data-stu-id="b48c5-108">**Left**</span></span>  
<span data-ttu-id="b48c5-109">Coordenada x de la esquina superior izquierda del rectángulo.</span><span class="sxs-lookup"><span data-stu-id="b48c5-109">The x-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="b48c5-110">**Top** (Principales)</span><span class="sxs-lookup"><span data-stu-id="b48c5-110">**Top**</span></span>  
<span data-ttu-id="b48c5-111">Coordenada y de la esquina superior izquierda del rectángulo.</span><span class="sxs-lookup"><span data-stu-id="b48c5-111">The y-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="b48c5-112">**Right**</span><span class="sxs-lookup"><span data-stu-id="b48c5-112">**Right**</span></span>  
<span data-ttu-id="b48c5-113">Coordenada x de la esquina inferior derecha del rectángulo.</span><span class="sxs-lookup"><span data-stu-id="b48c5-113">The x-coordinate of the lower right corner of the rectangle.</span></span>

<span data-ttu-id="b48c5-114">**Bottom**</span><span class="sxs-lookup"><span data-stu-id="b48c5-114">**Bottom**</span></span>  
<span data-ttu-id="b48c5-115">Coordenada y de la esquina inferior derecha del rectángulo.</span><span class="sxs-lookup"><span data-stu-id="b48c5-115">The y-coordinate of the lower right corner of the rectangle.</span></span>

## <a name="remarks"></a><span data-ttu-id="b48c5-116">Comentarios</span><span class="sxs-lookup"><span data-stu-id="b48c5-116">Remarks</span></span>

<span data-ttu-id="b48c5-117">Las funciones de consola utilizan esta estructura para especificar áreas rectangulares de búferes de pantalla de la consola, donde las coordenadas especifican las filas y columnas de las celdas de caracteres del búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="b48c5-117">This structure is used by console functions to specify rectangular areas of console screen buffers, where the coordinates specify the rows and columns of screen-buffer character cells.</span></span>

## <a name="examples"></a><span data-ttu-id="b48c5-118">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="b48c5-118">Examples</span></span>

<span data-ttu-id="b48c5-119">Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="b48c5-119">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="b48c5-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b48c5-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b48c5-121">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="b48c5-121">Minimum supported client</span></span> | <span data-ttu-id="b48c5-122">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="b48c5-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="b48c5-123">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="b48c5-123">Minimum supported server</span></span> | <span data-ttu-id="b48c5-124">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="b48c5-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="b48c5-125">Encabezado</span><span class="sxs-lookup"><span data-stu-id="b48c5-125">Header</span></span> | <span data-ttu-id="b48c5-126">WinConTypes. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b48c5-126">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="b48c5-127">Consulte también</span><span class="sxs-lookup"><span data-stu-id="b48c5-127">See also</span></span>

[<span data-ttu-id="b48c5-128">**RECT**</span><span class="sxs-lookup"><span data-stu-id="b48c5-128">**RECT**</span></span>](https://msdn.microsoft.com/library/windows/desktop/dd162897)

[<span data-ttu-id="b48c5-129">**RECTl**</span><span class="sxs-lookup"><span data-stu-id="b48c5-129">**RECTL**</span></span>](https://msdn.microsoft.com/library/windows/desktop/dd162907)
