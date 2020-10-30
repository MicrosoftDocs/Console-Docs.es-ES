---
title: PeekConsoleInput función)
description: Lee datos del búfer de entrada de la consola especificado sin quitarlo del búfer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/PeekConsoleInput
- wincon/PeekConsoleInput
- PeekConsoleInput
- consoleapi/PeekConsoleInputA
- wincon/PeekConsoleInputA
- PeekConsoleInputA
- consoleapi/PeekConsoleInputW
- wincon/PeekConsoleInputW
- PeekConsoleInputW
MS-HAID:
- '\_win32\_peekconsoleinput'
- base.peekconsoleinput
- consoles.peekconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9982dc20-43bd-4ee3-a68d-157c9134daca
topic_type:
- apiref
api_name:
- PeekConsoleInput
- PeekConsoleInputA
- PeekConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 9052f15b36e16dd2ddf7fe46d3d201aa21403f91
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039503"
---
# <a name="peekconsoleinput-function"></a><span data-ttu-id="730fe-104">PeekConsoleInput función)</span><span class="sxs-lookup"><span data-stu-id="730fe-104">PeekConsoleInput function</span></span>

<span data-ttu-id="730fe-105">Lee datos del búfer de entrada de la consola especificado sin quitarlo del búfer.</span><span class="sxs-lookup"><span data-stu-id="730fe-105">Reads data from the specified console input buffer without removing it from the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="730fe-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="730fe-106">Syntax</span></span>

```C
BOOL WINAPI PeekConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

## <a name="parameters"></a><span data-ttu-id="730fe-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="730fe-107">Parameters</span></span>

<span data-ttu-id="730fe-108">*hConsoleInput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="730fe-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="730fe-109">Identificador para el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="730fe-109">A handle to the console input buffer.</span></span> <span data-ttu-id="730fe-110">El identificador debe tener el derecho de acceso de **\_ lectura genérico** .</span><span class="sxs-lookup"><span data-stu-id="730fe-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="730fe-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="730fe-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="730fe-112">*lpBuffer* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="730fe-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="730fe-113">Puntero a una matriz de estructuras [**de \_ registros de entrada**](input-record-str.md) que recibe los datos del búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="730fe-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="730fe-114">*nLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="730fe-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="730fe-115">Tamaño de la matriz a la que apunta el parámetro *lpBuffer* , en elementos de matriz.</span><span class="sxs-lookup"><span data-stu-id="730fe-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="730fe-116">*lpNumberOfEventsRead* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="730fe-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="730fe-117">Puntero a una variable que recibe el número de registros de entrada leídos.</span><span class="sxs-lookup"><span data-stu-id="730fe-117">A pointer to a variable that receives the number of input records read.</span></span>

## <a name="return-value"></a><span data-ttu-id="730fe-118">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="730fe-118">Return value</span></span>

<span data-ttu-id="730fe-119">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="730fe-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="730fe-120">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="730fe-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="730fe-121">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="730fe-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="730fe-122">Comentarios</span><span class="sxs-lookup"><span data-stu-id="730fe-122">Remarks</span></span>

<span data-ttu-id="730fe-123">Si el número de registros solicitado supera el número de registros disponibles en el búfer, se lee el número disponible.</span><span class="sxs-lookup"><span data-stu-id="730fe-123">If the number of records requested exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="730fe-124">Si no hay datos disponibles, la función se devuelve inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="730fe-124">If no data is available, the function returns immediately.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## <a name="requirements"></a><span data-ttu-id="730fe-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="730fe-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="730fe-126">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="730fe-126">Minimum supported client</span></span> | <span data-ttu-id="730fe-127">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="730fe-127">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="730fe-128">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="730fe-128">Minimum supported server</span></span> | <span data-ttu-id="730fe-129">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="730fe-129">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="730fe-130">Encabezado</span><span class="sxs-lookup"><span data-stu-id="730fe-130">Header</span></span> | <span data-ttu-id="730fe-131">ConsoleApi. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="730fe-131">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="730fe-132">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="730fe-132">Library</span></span> | <span data-ttu-id="730fe-133">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="730fe-133">Kernel32.lib</span></span> |
| <span data-ttu-id="730fe-134">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="730fe-134">DLL</span></span> | <span data-ttu-id="730fe-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="730fe-135">Kernel32.dll</span></span> |
| <span data-ttu-id="730fe-136">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="730fe-136">Unicode and ANSI names</span></span> | <span data-ttu-id="730fe-137">**PeekConsoleInputW** (Unicode) y **PeekConsoleInputA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="730fe-137">**PeekConsoleInputW** (Unicode) and **PeekConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="730fe-138">Consulte también</span><span class="sxs-lookup"><span data-stu-id="730fe-138">See also</span></span>

[<span data-ttu-id="730fe-139">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="730fe-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="730fe-140">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="730fe-140">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="730fe-141">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="730fe-141">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="730fe-142">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="730fe-142">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="730fe-143">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="730fe-143">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

[<span data-ttu-id="730fe-144">**registro de entrada \_**</span><span class="sxs-lookup"><span data-stu-id="730fe-144">**INPUT\_RECORD**</span></span>](input-record-str.md)
