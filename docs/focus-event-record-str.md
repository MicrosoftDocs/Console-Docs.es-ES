---
title: Estructura de FOCUS_EVENT_RECORD
description: Describe un evento de foco en una estructura de registro de entrada de la consola \_ . Estos eventos se usan internamente y deben omitirse.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/FOCUS_EVENT_RECORD
- wincon/FOCUS_EVENT_RECORD
- FOCUS_EVENT_RECORD
- wincontypes/PFOCUS_EVENT_RECORD
- wincon/PFOCUS_EVENT_RECORD
- PFOCUS_EVENT_RECORD
MS-HAID:
- '\_win32\_focus\_event\_record\_str'
- base.focus\_event\_record\_str
- consoles.focus\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 4db0ae89-8446-4f0a-98e2-ba0b11ef7efe
topic_type:
- apiref
api_name:
- FOCUS_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: dc86c1b5b1c42a9d905673da4ea368de76a5fae9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038173"
---
# <a name="focus_event_record-structure"></a><span data-ttu-id="4f1a9-105">Estructura del registro de \_ eventos de foco \_</span><span class="sxs-lookup"><span data-stu-id="4f1a9-105">FOCUS\_EVENT\_RECORD structure</span></span>

<span data-ttu-id="4f1a9-106">Describe un evento de foco en una estructura de [**\_ registro de entrada**](input-record-str.md) de la consola.</span><span class="sxs-lookup"><span data-stu-id="4f1a9-106">Describes a focus event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="4f1a9-107">Estos eventos se usan internamente y deben omitirse.</span><span class="sxs-lookup"><span data-stu-id="4f1a9-107">These events are used internally and should be ignored.</span></span>

## <a name="syntax"></a><span data-ttu-id="4f1a9-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4f1a9-108">Syntax</span></span>

```C
typedef struct _FOCUS_EVENT_RECORD {
  BOOL bSetFocus;
} FOCUS_EVENT_RECORD;
```

## <a name="members"></a><span data-ttu-id="4f1a9-109">Miembros</span><span class="sxs-lookup"><span data-stu-id="4f1a9-109">Members</span></span>

<span data-ttu-id="4f1a9-110">**bSetFocus**</span><span class="sxs-lookup"><span data-stu-id="4f1a9-110">**bSetFocus**</span></span>  
<span data-ttu-id="4f1a9-111">Reservado.</span><span class="sxs-lookup"><span data-stu-id="4f1a9-111">Reserved.</span></span>

## <a name="requirements"></a><span data-ttu-id="4f1a9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4f1a9-112">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4f1a9-113">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="4f1a9-113">Minimum supported client</span></span> | <span data-ttu-id="4f1a9-114">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="4f1a9-114">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="4f1a9-115">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="4f1a9-115">Minimum supported server</span></span> | <span data-ttu-id="4f1a9-116">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="4f1a9-116">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="4f1a9-117">Encabezado</span><span class="sxs-lookup"><span data-stu-id="4f1a9-117">Header</span></span> | <span data-ttu-id="4f1a9-118">WinConTypes. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4f1a9-118">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="4f1a9-119">Consulte también</span><span class="sxs-lookup"><span data-stu-id="4f1a9-119">See also</span></span>

[<span data-ttu-id="4f1a9-120">**registro de entrada \_**</span><span class="sxs-lookup"><span data-stu-id="4f1a9-120">**INPUT\_RECORD**</span></span>](input-record-str.md)
