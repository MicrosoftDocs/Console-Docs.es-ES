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
ms.openlocfilehash: c36191738e09911dc9cc7c441371616001d250db
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357565"
---
# <a name="flushconsoleinputbuffer-function"></a><span data-ttu-id="5199b-105">FlushConsoleInputBuffer función)</span><span class="sxs-lookup"><span data-stu-id="5199b-105">FlushConsoleInputBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="5199b-106">Vacía el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="5199b-106">Flushes the console input buffer.</span></span> <span data-ttu-id="5199b-107">Se descartan todos los registros de entrada que se encuentran actualmente en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="5199b-107">All input records currently in the input buffer are discarded.</span></span>

## <a name="syntax"></a><span data-ttu-id="5199b-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5199b-108">Syntax</span></span>

```C
BOOL WINAPI FlushConsoleInputBuffer(
  _In_ HANDLE hConsoleInput
);
```

## <a name="parameters"></a><span data-ttu-id="5199b-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5199b-109">Parameters</span></span>

<span data-ttu-id="5199b-110">*hConsoleInput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="5199b-110">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="5199b-111">Identificador para el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="5199b-111">A handle to the console input buffer.</span></span> <span data-ttu-id="5199b-112">El identificador debe tener derecho de acceso de **GENERIC\_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="5199b-112">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="5199b-113">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="5199b-113">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

## <a name="return-value"></a><span data-ttu-id="5199b-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="5199b-114">Return value</span></span>

<span data-ttu-id="5199b-115">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="5199b-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="5199b-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="5199b-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="5199b-117">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="5199b-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="5199b-118">Comentarios</span><span class="sxs-lookup"><span data-stu-id="5199b-118">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="5199b-119">No se recomienda esta API y no tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente.</span><span class="sxs-lookup"><span data-stu-id="5199b-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="5199b-120">Al intentar vaciar la cola de entrada a la vez, se puede destruir el estado de la cola de una manera inesperada.</span><span class="sxs-lookup"><span data-stu-id="5199b-120">Attempting to empty the input queue all at once can destroy state in the queue in an unexpected manner.</span></span>

## <a name="requirements"></a><span data-ttu-id="5199b-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5199b-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="5199b-122">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="5199b-122">Minimum supported client</span></span> | <span data-ttu-id="5199b-123">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="5199b-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="5199b-124">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="5199b-124">Minimum supported server</span></span> | <span data-ttu-id="5199b-125">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="5199b-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="5199b-126">Encabezado</span><span class="sxs-lookup"><span data-stu-id="5199b-126">Header</span></span> | <span data-ttu-id="5199b-127">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5199b-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="5199b-128">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="5199b-128">Library</span></span> | <span data-ttu-id="5199b-129">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="5199b-129">Kernel32.lib</span></span> |
| <span data-ttu-id="5199b-130">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="5199b-130">DLL</span></span> | <span data-ttu-id="5199b-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="5199b-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="5199b-132">Vea también</span><span class="sxs-lookup"><span data-stu-id="5199b-132">See also</span></span>

[<span data-ttu-id="5199b-133">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="5199b-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="5199b-134">Funciones de entrada de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="5199b-134">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="5199b-135">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="5199b-135">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="5199b-136">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="5199b-136">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="5199b-137">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="5199b-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="5199b-138">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="5199b-138">**WriteConsoleInput**</span></span>](writeconsoleinput.md)