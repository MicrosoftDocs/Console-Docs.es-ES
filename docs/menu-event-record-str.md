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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8bbfbf6ad8bd885d69ce08e94dfced93b0bd3257
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060613"
---
# <a name="menu_event_record-structure"></a><span data-ttu-id="94ee6-105">Estructura de registros de \_ eventos de menú \_</span><span class="sxs-lookup"><span data-stu-id="94ee6-105">MENU\_EVENT\_RECORD structure</span></span>


<span data-ttu-id="94ee6-106">Describe un evento de menú en una estructura de [\*\* \_ registro de entrada\*\*](input-record-str.md) de la consola.</span><span class="sxs-lookup"><span data-stu-id="94ee6-106">Describes a menu event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="94ee6-107">Estos eventos se usan internamente y deben omitirse.</span><span class="sxs-lookup"><span data-stu-id="94ee6-107">These events are used internally and should be ignored.</span></span>

<a name="syntax"></a><span data-ttu-id="94ee6-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="94ee6-108">Syntax</span></span>
------

```C
typedef struct _MENU_EVENT_RECORD {
  UINT dwCommandId;
} MENU_EVENT_RECORD, *PMENU_EVENT_RECORD;
```

<a name="members"></a><span data-ttu-id="94ee6-109">Miembros</span><span class="sxs-lookup"><span data-stu-id="94ee6-109">Members</span></span>
-------

<span data-ttu-id="94ee6-110">**dwCommandId**</span><span class="sxs-lookup"><span data-stu-id="94ee6-110">**dwCommandId**</span></span>  
<span data-ttu-id="94ee6-111">Reservado.</span><span class="sxs-lookup"><span data-stu-id="94ee6-111">Reserved.</span></span>

<a name="requirements"></a><span data-ttu-id="94ee6-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="94ee6-112">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="94ee6-113">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="94ee6-113">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="94ee6-114">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="94ee6-114">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="94ee6-115">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="94ee6-115">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="94ee6-116">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="94ee6-116">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="94ee6-117">Encabezado</span><span class="sxs-lookup"><span data-stu-id="94ee6-117">Header</span></span></p></td>
<td><span data-ttu-id="94ee6-118">WinConTypes. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="94ee6-118">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="94ee6-119"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="94ee6-119"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="94ee6-120">**registro de entrada \_**</span><span class="sxs-lookup"><span data-stu-id="94ee6-120">**INPUT\_RECORD**</span></span>](input-record-str.md)

 

 




