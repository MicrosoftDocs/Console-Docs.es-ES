---
title: FlushConsoleInputBuffer función)
description: Vacía el búfer de entrada de la consola. Se descartan todos los registros de entrada que se encuentran actualmente en el búfer de entrada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/FlushConsoleInputBuffer
- wincon/FlushConsoleInputBuffer
- FlushConsoleInputBuffer
MS-HAID:
- '\_win32\_flushconsoleinputbuffer'
- base.flushconsoleinputbuffer
- consoles.flushconsoleinputbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6f7832d6-1fb2-4ca8-bd07-43123c990851
topic_type:
- apiref
api_name:
- FlushConsoleInputBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 543552e9252c1f28701a0b316b43597cdd9cd2c9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039053"
---
# <a name="flushconsoleinputbuffer-function"></a><span data-ttu-id="4c8d1-105">FlushConsoleInputBuffer función)</span><span class="sxs-lookup"><span data-stu-id="4c8d1-105">FlushConsoleInputBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="4c8d1-106">Vacía el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="4c8d1-106">Flushes the console input buffer.</span></span> <span data-ttu-id="4c8d1-107">Se descartan todos los registros de entrada que se encuentran actualmente en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="4c8d1-107">All input records currently in the input buffer are discarded.</span></span>

## <a name="syntax"></a><span data-ttu-id="4c8d1-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4c8d1-108">Syntax</span></span>

```C
BOOL WINAPI FlushConsoleInputBuffer(
  _In_ HANDLE hConsoleInput
);
```

## <a name="parameters"></a><span data-ttu-id="4c8d1-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4c8d1-109">Parameters</span></span>

<span data-ttu-id="4c8d1-110">*hConsoleInput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="4c8d1-110">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="4c8d1-111">Identificador para el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="4c8d1-111">A handle to the console input buffer.</span></span> <span data-ttu-id="4c8d1-112">El identificador debe tener el derecho de acceso de **\_ escritura genérico** .</span><span class="sxs-lookup"><span data-stu-id="4c8d1-112">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="4c8d1-113">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="4c8d1-113">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

## <a name="return-value"></a><span data-ttu-id="4c8d1-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4c8d1-114">Return value</span></span>

<span data-ttu-id="4c8d1-115">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="4c8d1-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4c8d1-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="4c8d1-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4c8d1-117">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4c8d1-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="4c8d1-118">Comentarios</span><span class="sxs-lookup"><span data-stu-id="4c8d1-118">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="4c8d1-119">No se recomienda esta API y no tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente.</span><span class="sxs-lookup"><span data-stu-id="4c8d1-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="4c8d1-120">Al intentar vaciar la cola de entrada a la vez, se puede destruir el estado de la cola de una manera inesperada.</span><span class="sxs-lookup"><span data-stu-id="4c8d1-120">Attempting to empty the input queue all at once can destroy state in the queue in an unexpected manner.</span></span>

## <a name="requirements"></a><span data-ttu-id="4c8d1-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c8d1-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4c8d1-122">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="4c8d1-122">Minimum supported client</span></span> | <span data-ttu-id="4c8d1-123">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="4c8d1-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="4c8d1-124">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="4c8d1-124">Minimum supported server</span></span> | <span data-ttu-id="4c8d1-125">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="4c8d1-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="4c8d1-126">Encabezado</span><span class="sxs-lookup"><span data-stu-id="4c8d1-126">Header</span></span> | <span data-ttu-id="4c8d1-127">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4c8d1-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="4c8d1-128">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="4c8d1-128">Library</span></span> | <span data-ttu-id="4c8d1-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4c8d1-129">Kernel32.lib</span></span> |
| <span data-ttu-id="4c8d1-130">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="4c8d1-130">DLL</span></span> | <span data-ttu-id="4c8d1-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4c8d1-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="4c8d1-132">Consulte también</span><span class="sxs-lookup"><span data-stu-id="4c8d1-132">See also</span></span>

[<span data-ttu-id="4c8d1-133">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="4c8d1-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4c8d1-134">Funciones de entrada de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="4c8d1-134">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="4c8d1-135">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="4c8d1-135">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="4c8d1-136">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="4c8d1-136">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="4c8d1-137">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="4c8d1-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="4c8d1-138">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="4c8d1-138">**WriteConsoleInput**</span></span>](writeconsoleinput.md)
