---
title: Estructura de WINDOW_BUFFER_SIZE_RECORD
description: Vea información de referencia sobre la estructura de WINDOW_BUFFER_SIZE_RECORD, que describe un cambio en el tamaño del búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/WINDOW_BUFFER_SIZE_RECORD
- wincon/WINDOW_BUFFER_SIZE_RECORD
- WINDOW_BUFFER_SIZE_RECORD
- wincontypes/PWINDOW_BUFFER_SIZE_RECORD
- wincon/PWINDOW_BUFFER_SIZE_RECORD
- PWINDOW_BUFFER_SIZE_RECORD
MS-HAID:
- '\_win32\_window\_buffer\_size\_record\_str'
- base.window\_buffer\_size\_record\_str
- consoles.window\_buffer\_size\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f2875e8-aa09-455b-a923-7cc388525b98
topic_type:
- apiref
api_name:
- WINDOW_BUFFER_SIZE_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 355482dfd162e2c29944d53e5b17b0315ea15950
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039273"
---
# <a name="window_buffer_size_record-structure"></a><span data-ttu-id="6ce76-104">\_Estructura de \_ registro del tamaño del búfer de ventana \_</span><span class="sxs-lookup"><span data-stu-id="6ce76-104">WINDOW\_BUFFER\_SIZE\_RECORD structure</span></span>

<span data-ttu-id="6ce76-105">Describe un cambio en el tamaño del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="6ce76-105">Describes a change in the size of the console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="6ce76-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="6ce76-106">Syntax</span></span>

```C
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

## <a name="members"></a><span data-ttu-id="6ce76-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="6ce76-107">Members</span></span>

<span data-ttu-id="6ce76-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="6ce76-108">**dwSize**</span></span>  
<span data-ttu-id="6ce76-109">Una estructura de [**coordenadas**](coord-str.md) que contiene el tamaño del búfer de pantalla de la consola, en columnas y filas de celda de carácter.</span><span class="sxs-lookup"><span data-stu-id="6ce76-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character cell columns and rows.</span></span>

## <a name="remarks"></a><span data-ttu-id="6ce76-110">Comentarios</span><span class="sxs-lookup"><span data-stu-id="6ce76-110">Remarks</span></span>

<span data-ttu-id="6ce76-111">Los eventos de tamaño de búfer se colocan en el búfer de entrada cuando la consola está en modo de ventana ( **habilitar \_ \_ entrada de ventana** ).</span><span class="sxs-lookup"><span data-stu-id="6ce76-111">Buffer size events are placed in the input buffer when the console is in window-aware mode ( **ENABLE\_WINDOW\_INPUT** ).</span></span>

## <a name="examples"></a><span data-ttu-id="6ce76-112">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="6ce76-112">Examples</span></span>

<span data-ttu-id="6ce76-113">Para obtener un ejemplo, vea [leer eventos de búfer de entrada](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="6ce76-113">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="6ce76-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ce76-114">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="6ce76-115">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="6ce76-115">Minimum supported client</span></span> | <span data-ttu-id="6ce76-116">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="6ce76-116">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="6ce76-117">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="6ce76-117">Minimum supported server</span></span> | <span data-ttu-id="6ce76-118">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="6ce76-118">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="6ce76-119">Encabezado</span><span class="sxs-lookup"><span data-stu-id="6ce76-119">Header</span></span> | <span data-ttu-id="6ce76-120">WinConTypes. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="6ce76-120">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="6ce76-121">Consulte también</span><span class="sxs-lookup"><span data-stu-id="6ce76-121">See also</span></span>

[<span data-ttu-id="6ce76-122">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="6ce76-122">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="6ce76-123">**registro de entrada \_**</span><span class="sxs-lookup"><span data-stu-id="6ce76-123">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="6ce76-124">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="6ce76-124">**ReadConsoleInput**</span></span>](readconsoleinput.md)
