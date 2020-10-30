---
title: Estructura de CONSOLE_CURSOR_INFO
description: Contiene la información de tamaño y visibilidad sobre el cursor de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/CONSOLE_CURSOR_INFO
- wincon/CONSOLE_CURSOR_INFO
- CONSOLE_CURSOR_INFO
- wincontypes/PCONSOLE_CURSOR_INFO
- wincon/PCONSOLE_CURSOR_INFO
- PCONSOLE_CURSOR_INFO
MS-HAID:
- '\_win32\_console\_cursor\_info\_str'
- base.console\_cursor\_info\_str
- consoles.console\_cursor\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0e71ce8c-e008-4bd7-922e-c44484b425ef
topic_type:
- apiref
api_name:
- CONSOLE_CURSOR_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: cdfcc00035738aa468d9795e4f6d32a54b96e1d0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037020"
---
# <a name="console_cursor_info-structure"></a><span data-ttu-id="5a12a-104">Estructura de información del \_ cursor de la consola \_</span><span class="sxs-lookup"><span data-stu-id="5a12a-104">CONSOLE\_CURSOR\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="5a12a-105">Contiene información sobre el cursor de la consola.</span><span class="sxs-lookup"><span data-stu-id="5a12a-105">Contains information about the console cursor.</span></span>

## <a name="syntax"></a><span data-ttu-id="5a12a-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5a12a-106">Syntax</span></span>

```C
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

## <a name="members"></a><span data-ttu-id="5a12a-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="5a12a-107">Members</span></span>

<span data-ttu-id="5a12a-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="5a12a-108">**dwSize**</span></span>  
<span data-ttu-id="5a12a-109">Porcentaje de la celda de caracteres que rellena el cursor.</span><span class="sxs-lookup"><span data-stu-id="5a12a-109">The percentage of the character cell that is filled by the cursor.</span></span> <span data-ttu-id="5a12a-110">Este valor se encuentra entre 1 y 100.</span><span class="sxs-lookup"><span data-stu-id="5a12a-110">This value is between 1 and 100.</span></span> <span data-ttu-id="5a12a-111">La apariencia del cursor varía, desde que se rellena completamente la celda hasta que se muestra como una línea horizontal en la parte inferior de la celda.</span><span class="sxs-lookup"><span data-stu-id="5a12a-111">The cursor appearance varies, ranging from completely filling the cell to showing up as a horizontal line at the bottom of the cell.</span></span>

> [!NOTE]
><span data-ttu-id="5a12a-112">Aunque el valor de **dwSize** está normalmente entre 1 y 100, en algunas circunstancias se puede devolver un valor fuera de ese intervalo.</span><span class="sxs-lookup"><span data-stu-id="5a12a-112">While the **dwSize** value is normally between 1 and 100, under some circumstances a value outside of that range might be returned.</span></span> <span data-ttu-id="5a12a-113">Por ejemplo, si **CursorSize** se establece en 0 en el registro, el valor de **dwSize** devuelto sería 0.</span><span class="sxs-lookup"><span data-stu-id="5a12a-113">For example, if **CursorSize** is set to 0 in the registry, the **dwSize** value returned would be 0.</span></span>

 <span data-ttu-id="5a12a-114">**bVisible**</span><span class="sxs-lookup"><span data-stu-id="5a12a-114">**bVisible**</span></span>  
<span data-ttu-id="5a12a-115">Visibilidad del cursor.</span><span class="sxs-lookup"><span data-stu-id="5a12a-115">The visibility of the cursor.</span></span> <span data-ttu-id="5a12a-116">Si el cursor está visible, este miembro es **true** .</span><span class="sxs-lookup"><span data-stu-id="5a12a-116">If the cursor is visible, this member is **TRUE** .</span></span>

## <a name="requirements"></a><span data-ttu-id="5a12a-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5a12a-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="5a12a-118">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="5a12a-118">Minimum supported client</span></span> | <span data-ttu-id="5a12a-119">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="5a12a-119">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="5a12a-120">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="5a12a-120">Minimum supported server</span></span> | <span data-ttu-id="5a12a-121">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="5a12a-121">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="5a12a-122">Encabezado</span><span class="sxs-lookup"><span data-stu-id="5a12a-122">Header</span></span> | <span data-ttu-id="5a12a-123">WinCon. h (incluir Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5a12a-123">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="5a12a-124">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5a12a-124">See also</span></span>

[<span data-ttu-id="5a12a-125">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="5a12a-125">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="5a12a-126">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="5a12a-126">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)
