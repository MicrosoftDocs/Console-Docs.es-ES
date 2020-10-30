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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 24d41dca61146cc3e835f405889400ae0d168e7f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039223"
---
# <a name="console_history_info-structure"></a><span data-ttu-id="e3bd4-104">Estructura de información del \_ historial de la consola \_</span><span class="sxs-lookup"><span data-stu-id="e3bd4-104">CONSOLE\_HISTORY\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="e3bd4-105">Contiene información sobre el historial de la consola.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-105">Contains information about the console history.</span></span>

## <a name="syntax"></a><span data-ttu-id="e3bd4-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e3bd4-106">Syntax</span></span>

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

## <a name="members"></a><span data-ttu-id="e3bd4-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="e3bd4-107">Members</span></span>

<span data-ttu-id="e3bd4-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="e3bd4-108">**cbSize**</span></span>  
<span data-ttu-id="e3bd4-109">Tamaño de la estructura, en bytes.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-109">The size of the structure, in bytes.</span></span> <span data-ttu-id="e3bd4-110">Establezca este miembro en `sizeof(CONSOLE_HISTORY_INFO)` .</span><span class="sxs-lookup"><span data-stu-id="e3bd4-110">Set this member to `sizeof(CONSOLE_HISTORY_INFO)`.</span></span>

<span data-ttu-id="e3bd4-111">**HistoryBufferSize**</span><span class="sxs-lookup"><span data-stu-id="e3bd4-111">**HistoryBufferSize**</span></span>  
<span data-ttu-id="e3bd4-112">El número de comandos que se mantienen en cada búfer del historial.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-112">The number of commands kept in each history buffer.</span></span>

<span data-ttu-id="e3bd4-113">**NumberOfHistoryBuffers**</span><span class="sxs-lookup"><span data-stu-id="e3bd4-113">**NumberOfHistoryBuffers**</span></span>  
<span data-ttu-id="e3bd4-114">El número de búferes de historial conservados para este proceso de consola.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-114">The number of history buffers kept for this console process.</span></span>

<span data-ttu-id="e3bd4-115">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="e3bd4-115">**dwFlags**</span></span>  
<span data-ttu-id="e3bd4-116">Este parámetro puede ser cero o el valor siguiente.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-116">This parameter can be zero or the following value.</span></span>

| <span data-ttu-id="e3bd4-117">Valor</span><span class="sxs-lookup"><span data-stu-id="e3bd4-117">Value</span></span> | <span data-ttu-id="e3bd4-118">Significado</span><span class="sxs-lookup"><span data-stu-id="e3bd4-118">Meaning</span></span> |
|-|-|
| <span data-ttu-id="e3bd4-119">**HISTORY_NO_DUP_FLAG** 0x1</span><span class="sxs-lookup"><span data-stu-id="e3bd4-119">**HISTORY_NO_DUP_FLAG** 0x1</span></span> | <span data-ttu-id="e3bd4-120">Las entradas duplicadas no se almacenarán en el búfer del historial.</span><span class="sxs-lookup"><span data-stu-id="e3bd4-120">Duplicate entries will not be stored in the history buffer.</span></span>

## <a name="requirements"></a><span data-ttu-id="e3bd4-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3bd4-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e3bd4-122">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="e3bd4-122">Minimum supported client</span></span> | <span data-ttu-id="e3bd4-123">Solo aplicaciones de escritorio de Windows Vista \[\]</span><span class="sxs-lookup"><span data-stu-id="e3bd4-123">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="e3bd4-124">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="e3bd4-124">Minimum supported server</span></span> | <span data-ttu-id="e3bd4-125">Solo aplicaciones de escritorio de Windows Server 2008 \[\]</span><span class="sxs-lookup"><span data-stu-id="e3bd4-125">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="e3bd4-126">Encabezado</span><span class="sxs-lookup"><span data-stu-id="e3bd4-126">Header</span></span> | <span data-ttu-id="e3bd4-127">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e3bd4-127">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="e3bd4-128">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e3bd4-128">See also</span></span>

[<span data-ttu-id="e3bd4-129">**GetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="e3bd4-129">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)

[<span data-ttu-id="e3bd4-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="e3bd4-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)
