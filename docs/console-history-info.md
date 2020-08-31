---
title: Estructura de CONSOLE_HISTORY_INFO
description: Vea la información de referencia sobre la estructura de CONSOLE_HISTORY_INFO, que contiene información sobre el historial de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/CONSOLE_HISTORY_INFO
- wincon/CONSOLE_HISTORY_INFO
- CONSOLE_HISTORY_INFO
- consoleapi3/PCONSOLE_HISTORY_INFO
- wincon/PCONSOLE_HISTORY_INFO
- PCONSOLE_HISTORY_INFO
MS-HAID:
- base.console\_history\_info
- consoles.console\_history\_info
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: df7d2f12-5299-47ed-b1f6-2db903dba81b
topic_type:
- apiref
api_name:
- CONSOLE_HISTORY_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: ee0161f0c4aac5a280fd18260ebbb1f7ca57d54a
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061036"
---
# <a name="console_history_info-structure"></a><span data-ttu-id="b1b8a-104">Estructura de información del \_ historial de la consola \_</span><span class="sxs-lookup"><span data-stu-id="b1b8a-104">CONSOLE\_HISTORY\_INFO structure</span></span>


<span data-ttu-id="b1b8a-105">Contiene información sobre el historial de la consola.</span><span class="sxs-lookup"><span data-stu-id="b1b8a-105">Contains information about the console history.</span></span>

<a name="syntax"></a><span data-ttu-id="b1b8a-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b1b8a-106">Syntax</span></span>
------

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

<a name="members"></a><span data-ttu-id="b1b8a-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="b1b8a-107">Members</span></span>
-------

<span data-ttu-id="b1b8a-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="b1b8a-108">**cbSize**</span></span>  
<span data-ttu-id="b1b8a-109">Tamaño de la estructura, en bytes.</span><span class="sxs-lookup"><span data-stu-id="b1b8a-109">The size of the structure, in bytes.</span></span> <span data-ttu-id="b1b8a-110">Establezca este miembro en `sizeof(CONSOLE_HISTORY_INFO)` .</span><span class="sxs-lookup"><span data-stu-id="b1b8a-110">Set this member to `sizeof(CONSOLE_HISTORY_INFO)`.</span></span>

<span data-ttu-id="b1b8a-111">**HistoryBufferSize**</span><span class="sxs-lookup"><span data-stu-id="b1b8a-111">**HistoryBufferSize**</span></span>  
<span data-ttu-id="b1b8a-112">El número de comandos que se mantienen en cada búfer del historial.</span><span class="sxs-lookup"><span data-stu-id="b1b8a-112">The number of commands kept in each history buffer.</span></span>

<span data-ttu-id="b1b8a-113">**NumberOfHistoryBuffers**</span><span class="sxs-lookup"><span data-stu-id="b1b8a-113">**NumberOfHistoryBuffers**</span></span>  
<span data-ttu-id="b1b8a-114">El número de búferes de historial conservados para este proceso de consola.</span><span class="sxs-lookup"><span data-stu-id="b1b8a-114">The number of history buffers kept for this console process.</span></span>

<span data-ttu-id="b1b8a-115">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="b1b8a-115">**dwFlags**</span></span>  
<span data-ttu-id="b1b8a-116">Este parámetro puede ser cero o el valor siguiente.</span><span class="sxs-lookup"><span data-stu-id="b1b8a-116">This parameter can be zero or the following value.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="b1b8a-117">Valor</span><span class="sxs-lookup"><span data-stu-id="b1b8a-117">Value</span></span></th>
<th><span data-ttu-id="b1b8a-118">Significado</span><span class="sxs-lookup"><span data-stu-id="b1b8a-118">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="b1b8a-119"><span id="HISTORY_NO_DUP_FLAG"></span><span id="history_no_dup_flag"></span>
<strong>HISTORY_NO_DUP_FLAG</strong> 0x1</span><span class="sxs-lookup"><span data-stu-id="b1b8a-119"><span id="HISTORY_NO_DUP_FLAG"></span><span id="history_no_dup_flag"></span>
<strong>HISTORY_NO_DUP_FLAG</strong> 0x1</span></span></td>
<td><p><span data-ttu-id="b1b8a-120">Las entradas duplicadas no se almacenarán en el búfer del historial.</span><span class="sxs-lookup"><span data-stu-id="b1b8a-120">Duplicate entries will not be stored in the history buffer.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="requirements"></a><span data-ttu-id="b1b8a-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1b8a-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b1b8a-122">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="b1b8a-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="b1b8a-123">Windows Vista [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="b1b8a-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b1b8a-124">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="b1b8a-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="b1b8a-125">Windows Server 2008 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="b1b8a-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b1b8a-126">Encabezado</span><span class="sxs-lookup"><span data-stu-id="b1b8a-126">Header</span></span></p></td>
<td><span data-ttu-id="b1b8a-127">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b1b8a-127">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="b1b8a-128"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="b1b8a-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="b1b8a-129">**GetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="b1b8a-129">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)

[<span data-ttu-id="b1b8a-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="b1b8a-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)

 

 




