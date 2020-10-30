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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: aaf1cfaea2a8822c142aab87f6dcf1b022b7160c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038373"
---
# <a name="console_selection_info-structure"></a><span data-ttu-id="3f41b-104">Estructura de información de \_ selección de consola \_</span><span class="sxs-lookup"><span data-stu-id="3f41b-104">CONSOLE\_SELECTION\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="3f41b-105">Contiene información para una selección de consola.</span><span class="sxs-lookup"><span data-stu-id="3f41b-105">Contains information for a console selection.</span></span>

## <a name="syntax"></a><span data-ttu-id="3f41b-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3f41b-106">Syntax</span></span>

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

## <a name="members"></a><span data-ttu-id="3f41b-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="3f41b-107">Members</span></span>

<span data-ttu-id="3f41b-108">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="3f41b-108">**dwFlags**</span></span>  
<span data-ttu-id="3f41b-109">El indicador de selección.</span><span class="sxs-lookup"><span data-stu-id="3f41b-109">The selection indicator.</span></span> <span data-ttu-id="3f41b-110">Este miembro puede ser uno o varios de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="3f41b-110">This member can be one or more of the following values.</span></span>

| <span data-ttu-id="3f41b-111">Valor</span><span class="sxs-lookup"><span data-stu-id="3f41b-111">Value</span></span> | <span data-ttu-id="3f41b-112">Significado</span><span class="sxs-lookup"><span data-stu-id="3f41b-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="3f41b-113">**CONSOLE_MOUSE_DOWN** 0x0008</span><span class="sxs-lookup"><span data-stu-id="3f41b-113">**CONSOLE_MOUSE_DOWN** 0x0008</span></span> | <span data-ttu-id="3f41b-114">El mouse está inactivo.</span><span class="sxs-lookup"><span data-stu-id="3f41b-114">Mouse is down.</span></span> <span data-ttu-id="3f41b-115">El usuario está ajustando activamente el rectángulo de selección con un mouse.</span><span class="sxs-lookup"><span data-stu-id="3f41b-115">The user is actively adjusting the selection rectangle with a mouse.</span></span> |
| <span data-ttu-id="3f41b-116">**CONSOLE_MOUSE_SELECTION** 0x0004</span><span class="sxs-lookup"><span data-stu-id="3f41b-116">**CONSOLE_MOUSE_SELECTION** 0x0004</span></span> | <span data-ttu-id="3f41b-117">Seleccionar con el mouse.</span><span class="sxs-lookup"><span data-stu-id="3f41b-117">Selecting with the mouse.</span></span> <span data-ttu-id="3f41b-118">Si está desactivado, el usuario está `conhost.exe` seleccionando el modo de marca de funcionamiento con el teclado.</span><span class="sxs-lookup"><span data-stu-id="3f41b-118">If off, the user is operating `conhost.exe` mark mode selection with the keyboard.</span></span> |
| <span data-ttu-id="3f41b-119">**CONSOLE_NO_SELECTION** 0x0000</span><span class="sxs-lookup"><span data-stu-id="3f41b-119">**CONSOLE_NO_SELECTION** 0x0000</span></span> | <span data-ttu-id="3f41b-120">No hay ninguna selección.</span><span class="sxs-lookup"><span data-stu-id="3f41b-120">No selection.</span></span> |
| <span data-ttu-id="3f41b-121">**CONSOLE_SELECTION_IN_PROGRESS** 0x0001</span><span class="sxs-lookup"><span data-stu-id="3f41b-121">**CONSOLE_SELECTION_IN_PROGRESS** 0x0001</span></span> | <span data-ttu-id="3f41b-122">La selección ha comenzado.</span><span class="sxs-lookup"><span data-stu-id="3f41b-122">Selection has begun.</span></span> <span data-ttu-id="3f41b-123">Si se selecciona una selección del mouse, normalmente no se producirá sin la `CONSOLE_SELECTION_NOT_EMPTY` marca.</span><span class="sxs-lookup"><span data-stu-id="3f41b-123">If a mouse selection, this will typically not occur without the `CONSOLE_SELECTION_NOT_EMPTY` flag.</span></span> <span data-ttu-id="3f41b-124">Si se selecciona un teclado, esto puede ocurrir cuando se ha escrito el modo de marca pero el usuario sigue navegando a la posición inicial.</span><span class="sxs-lookup"><span data-stu-id="3f41b-124">If a keyboard selection, this may occur when mark mode has been entered but the user is still navigating to the initial position.</span></span> |
| <span data-ttu-id="3f41b-125">**CONSOLE_SELECTION_NOT_EMPTY** 0x0002</span><span class="sxs-lookup"><span data-stu-id="3f41b-125">**CONSOLE_SELECTION_NOT_EMPTY** 0x0002</span></span> | <span data-ttu-id="3f41b-126">Rectángulo de selección no vacío.</span><span class="sxs-lookup"><span data-stu-id="3f41b-126">Selection rectangle not empty.</span></span> <span data-ttu-id="3f41b-127">La carga de *dwSelectionAnchor* y *srSelection* es válida.</span><span class="sxs-lookup"><span data-stu-id="3f41b-127">The payload of *dwSelectionAnchor* and *srSelection* are valid.</span></span>  |

<span data-ttu-id="3f41b-128">**dwSelectionAnchor**</span><span class="sxs-lookup"><span data-stu-id="3f41b-128">**dwSelectionAnchor**</span></span>  
<span data-ttu-id="3f41b-129">Estructura de [**coordenadas**](coord-str.md) que especifica el delimitador de selección, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="3f41b-129">A [**COORD**](coord-str.md) structure that specifies the selection anchor, in characters.</span></span>

<span data-ttu-id="3f41b-130">**srSelection**</span><span class="sxs-lookup"><span data-stu-id="3f41b-130">**srSelection**</span></span>  
<span data-ttu-id="3f41b-131">[**Pequeña estructura \_ Rect**](small-rect-str.md) que especifica el rectángulo de selección.</span><span class="sxs-lookup"><span data-stu-id="3f41b-131">A [**SMALL\_RECT**](small-rect-str.md) structure that specifies the selection rectangle.</span></span>

## <a name="requirements"></a><span data-ttu-id="3f41b-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3f41b-132">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="3f41b-133">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="3f41b-133">Minimum supported client</span></span> | <span data-ttu-id="3f41b-134">Solo aplicaciones de escritorio de Windows XP \[\]</span><span class="sxs-lookup"><span data-stu-id="3f41b-134">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="3f41b-135">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="3f41b-135">Minimum supported server</span></span> | <span data-ttu-id="3f41b-136">Solo aplicaciones de escritorio de Windows Server 2003 \[\]</span><span class="sxs-lookup"><span data-stu-id="3f41b-136">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="3f41b-137">Encabezado</span><span class="sxs-lookup"><span data-stu-id="3f41b-137">Header</span></span> | <span data-ttu-id="3f41b-138">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="3f41b-138">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="3f41b-139">Consulte también</span><span class="sxs-lookup"><span data-stu-id="3f41b-139">See also</span></span>

[<span data-ttu-id="3f41b-140">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="3f41b-140">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="3f41b-141">**GetConsoleSelectionInfo**</span><span class="sxs-lookup"><span data-stu-id="3f41b-141">**GetConsoleSelectionInfo**</span></span>](getconsoleselectioninfo.md)

[<span data-ttu-id="3f41b-142">**PEQUEÑO \_ rectángulo**</span><span class="sxs-lookup"><span data-stu-id="3f41b-142">**SMALL\_RECT**</span></span>](small-rect-str.md)
