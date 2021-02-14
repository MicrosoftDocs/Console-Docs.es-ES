---
title: GetConsoleProcessList función)
description: Vea la información de referencia sobre la función GetConsoleProcessList, que recupera una lista de los procesos adjuntos a la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleProcessList
- wincon/GetConsoleProcessList
- GetConsoleProcessList
MS-HAID:
- '\_win32\_getconsoleprocesslist'
- base.getconsoleprocesslist
- consoles.getconsoleprocesslist
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3d21103b-662d-4393-ae3f-773cd9e4a930
topic_type:
- apiref
api_name:
- GetConsoleProcessList
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: b067d701b2568165a4cf0f9368c37a06ba6863c8
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358945"
---
# <a name="getconsoleprocesslist-function"></a><span data-ttu-id="c57ae-104">GetConsoleProcessList función)</span><span class="sxs-lookup"><span data-stu-id="c57ae-104">GetConsoleProcessList function</span></span>

<span data-ttu-id="c57ae-105">Recupera una lista de los procesos adjuntos a la consola actual.</span><span class="sxs-lookup"><span data-stu-id="c57ae-105">Retrieves a list of the processes attached to the current console.</span></span>

## <a name="syntax"></a><span data-ttu-id="c57ae-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c57ae-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleProcessList(
  _Out_ LPDWORD lpdwProcessList,
  _In_  DWORD   dwProcessCount
);
```

## <a name="parameters"></a><span data-ttu-id="c57ae-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="c57ae-107">Parameters</span></span>

<span data-ttu-id="c57ae-108">*lpdwProcessList* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="c57ae-108">*lpdwProcessList* \[out\]</span></span>  
<span data-ttu-id="c57ae-109">Un puntero a un búfer que recibe una matriz de identificadores de proceso cuando se realiza correctamente.</span><span class="sxs-lookup"><span data-stu-id="c57ae-109">A pointer to a buffer that receives an array of process identifiers upon success.</span></span> <span data-ttu-id="c57ae-110">Debe ser un búfer válido y no puede ser `NULL` .</span><span class="sxs-lookup"><span data-stu-id="c57ae-110">This must be a valid buffer and cannot be `NULL`.</span></span> <span data-ttu-id="c57ae-111">El búfer debe tener espacio para recibir al menos un identificador de proceso devuelto.</span><span class="sxs-lookup"><span data-stu-id="c57ae-111">The buffer must have space to receive at least 1 returned process id.</span></span>

<span data-ttu-id="c57ae-112">*dwProcessCount* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="c57ae-112">*dwProcessCount* \[in\]</span></span>  
<span data-ttu-id="c57ae-113">Número máximo de identificadores de proceso que se pueden almacenar en el búfer de *lpdwProcessList* .</span><span class="sxs-lookup"><span data-stu-id="c57ae-113">The maximum number of process identifiers that can be stored in the *lpdwProcessList* buffer.</span></span> <span data-ttu-id="c57ae-114">Debe ser mayor que 0.</span><span class="sxs-lookup"><span data-stu-id="c57ae-114">This must be greater than 0.</span></span>

## <a name="return-value"></a><span data-ttu-id="c57ae-115">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="c57ae-115">Return value</span></span>

<span data-ttu-id="c57ae-116">Si la función se ejecuta correctamente, el valor devuelto es menor o igual que *dwProcessCount* y representa el número de identificadores de proceso almacenados en el búfer *lpdwProcessList* .</span><span class="sxs-lookup"><span data-stu-id="c57ae-116">If the function succeeds, the return value is less than or equal to *dwProcessCount* and represents the number of process identifiers stored in the *lpdwProcessList* buffer.</span></span>

<span data-ttu-id="c57ae-117">Si el búfer es demasiado pequeño para contener todos los identificadores de proceso válidos, el valor devuelto es el número necesario de elementos de matriz.</span><span class="sxs-lookup"><span data-stu-id="c57ae-117">If the buffer is too small to hold all the valid process identifiers, the return value is the required number of array elements.</span></span> <span data-ttu-id="c57ae-118">La función habrá almacenado ningún identificador en el búfer.</span><span class="sxs-lookup"><span data-stu-id="c57ae-118">The function will have stored no identifiers in the buffer.</span></span> <span data-ttu-id="c57ae-119">En esta situación, use el valor devuelto para asignar un búfer lo suficientemente grande como para almacenar toda la lista y volver a llamar a la función.</span><span class="sxs-lookup"><span data-stu-id="c57ae-119">In this situation, use the return value to allocate a buffer that is large enough to store the entire list and call the function again.</span></span>

<span data-ttu-id="c57ae-120">Si el valor devuelto es cero, se ha producido un error en la función porque cada consola tiene al menos un proceso asociado.</span><span class="sxs-lookup"><span data-stu-id="c57ae-120">If the return value is zero, the function has failed, because every console has at least one process associated with it.</span></span> <span data-ttu-id="c57ae-121">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="c57ae-121">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

<span data-ttu-id="c57ae-122">Si `NULL` se proporcionó una lista de procesos o el número de procesos era 0, la llamada devolverá 0 y `GetLastError` devolverá `ERROR_INVALID_PARAMETER` .</span><span class="sxs-lookup"><span data-stu-id="c57ae-122">If a `NULL` process list was provided or the process count was 0, the call will return 0 and `GetLastError` will return `ERROR_INVALID_PARAMETER`.</span></span> <span data-ttu-id="c57ae-123">Proporcione un búfer de al menos un elemento para llamar a esta función.</span><span class="sxs-lookup"><span data-stu-id="c57ae-123">Please provide a buffer of at least one element to call this function.</span></span> <span data-ttu-id="c57ae-124">Asigne un búfer mayor y vuelva a llamar a si el código de retorno es mayor que la longitud del búfer proporcionado.</span><span class="sxs-lookup"><span data-stu-id="c57ae-124">Allocate a larger buffer and call again if the return code is larger than the length of the provided buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="c57ae-125">Comentarios</span><span class="sxs-lookup"><span data-stu-id="c57ae-125">Remarks</span></span>

<span data-ttu-id="c57ae-126">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0501 o posterior.</span><span class="sxs-lookup"><span data-stu-id="c57ae-126">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="c57ae-127">Para obtener más información, consulte [uso de los encabezados de Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="c57ae-127">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

## <a name="requirements"></a><span data-ttu-id="c57ae-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c57ae-128">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c57ae-129">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="c57ae-129">Minimum supported client</span></span> | <span data-ttu-id="c57ae-130">Solo aplicaciones de escritorio de Windows XP \[\]</span><span class="sxs-lookup"><span data-stu-id="c57ae-130">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="c57ae-131">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="c57ae-131">Minimum supported server</span></span> | <span data-ttu-id="c57ae-132">Solo aplicaciones de escritorio de Windows Server 2003 \[\]</span><span class="sxs-lookup"><span data-stu-id="c57ae-132">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="c57ae-133">Encabezado</span><span class="sxs-lookup"><span data-stu-id="c57ae-133">Header</span></span> | <span data-ttu-id="c57ae-134">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c57ae-134">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c57ae-135">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="c57ae-135">Library</span></span> | <span data-ttu-id="c57ae-136">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="c57ae-136">Kernel32.lib</span></span> |
| <span data-ttu-id="c57ae-137">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="c57ae-137">DLL</span></span> | <span data-ttu-id="c57ae-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c57ae-138">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="c57ae-139">Vea también</span><span class="sxs-lookup"><span data-stu-id="c57ae-139">See also</span></span>

[<span data-ttu-id="c57ae-140">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="c57ae-140">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="c57ae-141">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="c57ae-141">Console Functions</span></span>](console-functions.md)