---
title: ClosePseudoConsole función)
description: Vea la información de referencia sobre la función ClosePseudoConsole, que cierra un pseudoconsole desde el identificador especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola, conpty, pseudoconsole
topic_type:
- apiref
api_name:
- ClosePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 0674fa9c02c54c9476e2844da69895905865d6f4
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060896"
---
# <a name="closepseudoconsole-function"></a><span data-ttu-id="95d28-104">ClosePseudoConsole función)</span><span class="sxs-lookup"><span data-stu-id="95d28-104">ClosePseudoConsole function</span></span>


<span data-ttu-id="95d28-105">Cierra un pseudoconsole del identificador dado.</span><span class="sxs-lookup"><span data-stu-id="95d28-105">Closes a pseudoconsole from the given handle.</span></span>

<a name="syntax"></a><span data-ttu-id="95d28-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="95d28-106">Syntax</span></span>
------

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC 
);
```

<a name="parameters"></a><span data-ttu-id="95d28-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="95d28-107">Parameters</span></span>
----------

<span data-ttu-id="95d28-108">*hPC* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="95d28-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="95d28-109">Identificador de un psuedoconsole activo tal y como lo abre [CreatePseudoConsole](createpseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="95d28-109">A handle to an active psuedoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

<a name="return-value"></a><span data-ttu-id="95d28-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="95d28-110">Return value</span></span>
------------

<span data-ttu-id="95d28-111">*Ninguna*</span><span class="sxs-lookup"><span data-stu-id="95d28-111">*none*</span></span>

<a name="remarks"></a><span data-ttu-id="95d28-112">Observaciones</span><span class="sxs-lookup"><span data-stu-id="95d28-112">Remarks</span></span>
-------

<span data-ttu-id="95d28-113">Al cerrar un pseudoconsole, las aplicaciones cliente adjuntas a la sesión también se terminarán.</span><span class="sxs-lookup"><span data-stu-id="95d28-113">Upon closing a pseudoconsole, client applications attached to the session will be terminated as well.</span></span>

<span data-ttu-id="95d28-114">Un marco pintado final puede llegar `hOutput` desde pseudoconsole cuando se llama a esta API.</span><span class="sxs-lookup"><span data-stu-id="95d28-114">A final painted frame may arrive on `hOutput` from the pseudoconsole when this API is called.</span></span> <span data-ttu-id="95d28-115">Se espera que el autor de la llamada vacíe esta información del búfer del canal de comunicación y la presente o la descarte.</span><span class="sxs-lookup"><span data-stu-id="95d28-115">It is expected that the caller will drain this information from the communication channel buffer and either present it or discard it.</span></span> <span data-ttu-id="95d28-116">Si no se agota el búfer, es posible que la llamada de cierre espere indefinidamente hasta que se vacíe o que los canales de comunicación se rompan de otra manera.</span><span class="sxs-lookup"><span data-stu-id="95d28-116">Failure to drain the buffer may cause the Close call to wait indefinitely until it is drained or the communication channels are broken another way.</span></span>

<a name="requirements"></a><span data-ttu-id="95d28-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95d28-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="95d28-118">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="95d28-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="95d28-119">Windows 10 1809 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="95d28-119">Windows 10 1809 [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="95d28-120">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="95d28-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="95d28-121">Windows Server 2019 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="95d28-121">Windows Server 2019 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="95d28-122">Encabezado</span><span class="sxs-lookup"><span data-stu-id="95d28-122">Header</span></span></p></td>
<td><span data-ttu-id="95d28-123">ConsoleApi. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="95d28-123">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="95d28-124">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="95d28-124">Library</span></span></p></td>
<td><span data-ttu-id="95d28-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="95d28-125">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="95d28-126">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="95d28-126">DLL</span></span></p></td>
<td><span data-ttu-id="95d28-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="95d28-127">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="95d28-128"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="95d28-128"><span id="see_also"></span>See also</span></span>

[<span data-ttu-id="95d28-129">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="95d28-129">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="95d28-130">**CreatePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="95d28-130">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="95d28-131">**ResizePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="95d28-131">**ResizePseudoConsole**</span></span>](resizepseudoconsole.md)
