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
ms.openlocfilehash: 8ae6bb36007ede4015c91dfd4fe2a8ba8c898465
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358315"
---
# <a name="peekconsoleinput-function"></a><span data-ttu-id="5d826-104">PeekConsoleInput función)</span><span class="sxs-lookup"><span data-stu-id="5d826-104">PeekConsoleInput function</span></span>

<span data-ttu-id="5d826-105">Lee datos del búfer de entrada de la consola especificado sin quitarlo del búfer.</span><span class="sxs-lookup"><span data-stu-id="5d826-105">Reads data from the specified console input buffer without removing it from the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d826-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5d826-106">Syntax</span></span>

```C
BOOL WINAPI PeekConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

## <a name="parameters"></a><span data-ttu-id="5d826-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5d826-107">Parameters</span></span>

<span data-ttu-id="5d826-108">*hConsoleInput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="5d826-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="5d826-109">Identificador para el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="5d826-109">A handle to the console input buffer.</span></span> <span data-ttu-id="5d826-110">El identificador debe tener derecho de acceso de **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="5d826-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="5d826-111">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="5d826-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="5d826-112">*lpBuffer* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="5d826-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="5d826-113">Puntero a una matriz de estructuras [**de \_ registros de entrada**](input-record-str.md) que recibe los datos del búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="5d826-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="5d826-114">*nLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="5d826-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="5d826-115">Tamaño de la matriz a la que apunta el parámetro *lpBuffer* , en elementos de matriz.</span><span class="sxs-lookup"><span data-stu-id="5d826-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="5d826-116">*lpNumberOfEventsRead* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="5d826-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="5d826-117">Puntero a una variable que recibe el número de registros de entrada leídos.</span><span class="sxs-lookup"><span data-stu-id="5d826-117">A pointer to a variable that receives the number of input records read.</span></span>

## <a name="return-value"></a><span data-ttu-id="5d826-118">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="5d826-118">Return value</span></span>

<span data-ttu-id="5d826-119">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="5d826-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="5d826-120">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="5d826-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="5d826-121">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="5d826-121">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="5d826-122">Comentarios</span><span class="sxs-lookup"><span data-stu-id="5d826-122">Remarks</span></span>

<span data-ttu-id="5d826-123">Si el número de registros solicitado supera el número de registros disponibles en el búfer, se lee el número disponible.</span><span class="sxs-lookup"><span data-stu-id="5d826-123">If the number of records requested exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="5d826-124">Si no hay datos disponibles, la función se devuelve inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="5d826-124">If no data is available, the function returns immediately.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## <a name="requirements"></a><span data-ttu-id="5d826-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d826-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="5d826-126">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="5d826-126">Minimum supported client</span></span> | <span data-ttu-id="5d826-127">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="5d826-127">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="5d826-128">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="5d826-128">Minimum supported server</span></span> | <span data-ttu-id="5d826-129">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="5d826-129">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="5d826-130">Encabezado</span><span class="sxs-lookup"><span data-stu-id="5d826-130">Header</span></span> | <span data-ttu-id="5d826-131">ConsoleApi.h (a través de WinCon.h, incluido Windows.h)</span><span class="sxs-lookup"><span data-stu-id="5d826-131">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="5d826-132">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="5d826-132">Library</span></span> | <span data-ttu-id="5d826-133">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="5d826-133">Kernel32.lib</span></span> |
| <span data-ttu-id="5d826-134">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="5d826-134">DLL</span></span> | <span data-ttu-id="5d826-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="5d826-135">Kernel32.dll</span></span> |
| <span data-ttu-id="5d826-136">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="5d826-136">Unicode and ANSI names</span></span> | <span data-ttu-id="5d826-137">**PeekConsoleInputW** (Unicode) y **PeekConsoleInputA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="5d826-137">**PeekConsoleInputW** (Unicode) and **PeekConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="5d826-138">Vea también</span><span class="sxs-lookup"><span data-stu-id="5d826-138">See also</span></span>

[<span data-ttu-id="5d826-139">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="5d826-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="5d826-140">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="5d826-140">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="5d826-141">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="5d826-141">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="5d826-142">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="5d826-142">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="5d826-143">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="5d826-143">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

[<span data-ttu-id="5d826-144">**registro de entrada \_**</span><span class="sxs-lookup"><span data-stu-id="5d826-144">**INPUT\_RECORD**</span></span>](input-record-str.md)