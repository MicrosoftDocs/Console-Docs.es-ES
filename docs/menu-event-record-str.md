---
title: Estructura de MENU_EVENT_RECORD
description: Describe un evento de menú en una estructura de registro de entrada de la consola \_ . Estos eventos se usan internamente y deben omitirse.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/MENU_EVENT_RECORD
- wincon/MENU_EVENT_RECORD
- MENU_EVENT_RECORD
- wincontypes/PMENU_EVENT_RECORD
- wincon/PMENU_EVENT_RECORD
- PMENU_EVENT_RECORD
MS-HAID:
- '\_win32\_menu\_event\_record\_str'
- base.menu\_event\_record\_str
- consoles.menu\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 7efef0e0-01ba-44ba-a972-25c6b3aed2bd
topic_type:
- apiref
api_name:
- MENU_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: dfca825c03dbf0e63041e68adc5e43f2ca0ef669
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039523"
---
# <a name="menu_event_record-structure"></a><span data-ttu-id="4dddd-105">Estructura de registros de \_ eventos de menú \_</span><span class="sxs-lookup"><span data-stu-id="4dddd-105">MENU\_EVENT\_RECORD structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="4dddd-106">Describe un evento de menú en una estructura de [**\_ registro de entrada**](input-record-str.md) de la consola.</span><span class="sxs-lookup"><span data-stu-id="4dddd-106">Describes a menu event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="4dddd-107">Estos eventos se usan internamente y deben omitirse.</span><span class="sxs-lookup"><span data-stu-id="4dddd-107">These events are used internally and should be ignored.</span></span>

## <a name="syntax"></a><span data-ttu-id="4dddd-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4dddd-108">Syntax</span></span>

```C
typedef struct _MENU_EVENT_RECORD {
  UINT dwCommandId;
} MENU_EVENT_RECORD, *PMENU_EVENT_RECORD;
```

## <a name="members"></a><span data-ttu-id="4dddd-109">Miembros</span><span class="sxs-lookup"><span data-stu-id="4dddd-109">Members</span></span>

<span data-ttu-id="4dddd-110">**dwCommandId**</span><span class="sxs-lookup"><span data-stu-id="4dddd-110">**dwCommandId**</span></span>  
<span data-ttu-id="4dddd-111">Reservado.</span><span class="sxs-lookup"><span data-stu-id="4dddd-111">Reserved.</span></span>

## <a name="requirements"></a><span data-ttu-id="4dddd-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4dddd-112">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4dddd-113">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="4dddd-113">Minimum supported client</span></span> | <span data-ttu-id="4dddd-114">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="4dddd-114">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="4dddd-115">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="4dddd-115">Minimum supported server</span></span> | <span data-ttu-id="4dddd-116">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="4dddd-116">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="4dddd-117">Encabezado</span><span class="sxs-lookup"><span data-stu-id="4dddd-117">Header</span></span> | <span data-ttu-id="4dddd-118">WinConTypes. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4dddd-118">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="4dddd-119">Consulte también</span><span class="sxs-lookup"><span data-stu-id="4dddd-119">See also</span></span>

[<span data-ttu-id="4dddd-120">**registro de entrada \_**</span><span class="sxs-lookup"><span data-stu-id="4dddd-120">**INPUT\_RECORD**</span></span>](input-record-str.md)
