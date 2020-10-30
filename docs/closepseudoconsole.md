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
ms.openlocfilehash: 067fa732f5badfe46ee6391c892aa037613cb4dd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037293"
---
# <a name="closepseudoconsole-function"></a><span data-ttu-id="fcc7b-104">ClosePseudoConsole función)</span><span class="sxs-lookup"><span data-stu-id="fcc7b-104">ClosePseudoConsole function</span></span>

<span data-ttu-id="fcc7b-105">Cierra un pseudoconsole del identificador dado.</span><span class="sxs-lookup"><span data-stu-id="fcc7b-105">Closes a pseudoconsole from the given handle.</span></span>

## <a name="syntax"></a><span data-ttu-id="fcc7b-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fcc7b-106">Syntax</span></span>

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC
);
```

## <a name="parameters"></a><span data-ttu-id="fcc7b-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="fcc7b-107">Parameters</span></span>

<span data-ttu-id="fcc7b-108">*hPC* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="fcc7b-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="fcc7b-109">Identificador de un pseudoconsole activo tal y como lo abre [CreatePseudoConsole](createpseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="fcc7b-109">A handle to an active pseudoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

## <a name="return-value"></a><span data-ttu-id="fcc7b-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="fcc7b-110">Return value</span></span>

<span data-ttu-id="fcc7b-111">*Ninguna*</span><span class="sxs-lookup"><span data-stu-id="fcc7b-111">*none*</span></span>

## <a name="remarks"></a><span data-ttu-id="fcc7b-112">Comentarios</span><span class="sxs-lookup"><span data-stu-id="fcc7b-112">Remarks</span></span>

<span data-ttu-id="fcc7b-113">Al cerrar un pseudoconsole, las aplicaciones cliente adjuntas a la sesión también se terminarán.</span><span class="sxs-lookup"><span data-stu-id="fcc7b-113">Upon closing a pseudoconsole, client applications attached to the session will be terminated as well.</span></span>

<span data-ttu-id="fcc7b-114">Un marco pintado final puede llegar al `hOutput` identificador proporcionado originalmente a [CreatePsuedoConsole](createpseudoconsole.md) cuando se llama a esta API.</span><span class="sxs-lookup"><span data-stu-id="fcc7b-114">A final painted frame may arrive on the `hOutput` handle originally provided to [CreatePsuedoConsole](createpseudoconsole.md) when this API is called.</span></span> <span data-ttu-id="fcc7b-115">Se espera que el autor de la llamada vacíe esta información del búfer del canal de comunicación y la presente o la descarte.</span><span class="sxs-lookup"><span data-stu-id="fcc7b-115">It is expected that the caller will drain this information from the communication channel buffer and either present it or discard it.</span></span> <span data-ttu-id="fcc7b-116">Si no se agota el búfer, es posible que la llamada de cierre espere indefinidamente hasta que se vacíe o que los canales de comunicación se rompan de otra manera.</span><span class="sxs-lookup"><span data-stu-id="fcc7b-116">Failure to drain the buffer may cause the Close call to wait indefinitely until it is drained or the communication channels are broken another way.</span></span>

## <a name="requirements"></a><span data-ttu-id="fcc7b-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fcc7b-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="fcc7b-118">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="fcc7b-118">Minimum supported client</span></span> | <span data-ttu-id="fcc7b-119">Actualización 2018 de octubre de Windows 10 (versión 1809) \[ solo para aplicaciones de escritorio\]</span><span class="sxs-lookup"><span data-stu-id="fcc7b-119">Windows 10 October 2018 Update (version 1809) \[desktop apps only\]</span></span> |
| <span data-ttu-id="fcc7b-120">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="fcc7b-120">Minimum supported server</span></span> | <span data-ttu-id="fcc7b-121">Solo aplicaciones de escritorio de Windows Server 2019 \[\]</span><span class="sxs-lookup"><span data-stu-id="fcc7b-121">Windows Server 2019 \[desktop apps only\]</span></span> |
| <span data-ttu-id="fcc7b-122">Encabezado</span><span class="sxs-lookup"><span data-stu-id="fcc7b-122">Header</span></span> | <span data-ttu-id="fcc7b-123">ConsoleApi. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="fcc7b-123">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="fcc7b-124">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="fcc7b-124">Library</span></span> | <span data-ttu-id="fcc7b-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="fcc7b-125">Kernel32.lib</span></span> |
| <span data-ttu-id="fcc7b-126">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="fcc7b-126">DLL</span></span> | <span data-ttu-id="fcc7b-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="fcc7b-127">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="fcc7b-128">Consulte también</span><span class="sxs-lookup"><span data-stu-id="fcc7b-128">See also</span></span>

[<span data-ttu-id="fcc7b-129">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="fcc7b-129">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="fcc7b-130">**ClosePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="fcc7b-130">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="fcc7b-131">**ResizePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="fcc7b-131">**ResizePseudoConsole**</span></span>](resizepseudoconsole.md)
