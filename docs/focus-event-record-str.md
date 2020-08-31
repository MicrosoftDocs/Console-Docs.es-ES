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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 61f37e3645a66ca9f755f66f0baa03a2238983ad
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060741"
---
# <a name="focus_event_record-structure"></a><span data-ttu-id="9fae7-105">Estructura del registro de \_ eventos de foco \_</span><span class="sxs-lookup"><span data-stu-id="9fae7-105">FOCUS\_EVENT\_RECORD structure</span></span>


<span data-ttu-id="9fae7-106">Describe un evento de foco en una estructura de [\*\* \_ registro de entrada\*\*](input-record-str.md) de la consola.</span><span class="sxs-lookup"><span data-stu-id="9fae7-106">Describes a focus event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="9fae7-107">Estos eventos se usan internamente y deben omitirse.</span><span class="sxs-lookup"><span data-stu-id="9fae7-107">These events are used internally and should be ignored.</span></span>

<a name="syntax"></a><span data-ttu-id="9fae7-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9fae7-108">Syntax</span></span>
------

```C
typedef struct _FOCUS_EVENT_RECORD {
  BOOL bSetFocus;
} FOCUS_EVENT_RECORD;
```

<a name="members"></a><span data-ttu-id="9fae7-109">Miembros</span><span class="sxs-lookup"><span data-stu-id="9fae7-109">Members</span></span>
-------

<span data-ttu-id="9fae7-110">**bSetFocus**</span><span class="sxs-lookup"><span data-stu-id="9fae7-110">**bSetFocus**</span></span>  
<span data-ttu-id="9fae7-111">Reservado.</span><span class="sxs-lookup"><span data-stu-id="9fae7-111">Reserved.</span></span>

<a name="requirements"></a><span data-ttu-id="9fae7-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9fae7-112">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="9fae7-113">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="9fae7-113">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="9fae7-114">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="9fae7-114">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="9fae7-115">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="9fae7-115">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="9fae7-116">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="9fae7-116">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="9fae7-117">Encabezado</span><span class="sxs-lookup"><span data-stu-id="9fae7-117">Header</span></span></p></td>
<td><span data-ttu-id="9fae7-118">WinConTypes. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9fae7-118">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="9fae7-119"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="9fae7-119"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="9fae7-120">**registro de entrada \_**</span><span class="sxs-lookup"><span data-stu-id="9fae7-120">**INPUT\_RECORD**</span></span>](input-record-str.md)

 

 




