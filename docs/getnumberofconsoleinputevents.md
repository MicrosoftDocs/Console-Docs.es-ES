---
title: GetNumberOfConsoleInputEvents función)
description: Recupera el número de registros de entrada no leídos en el búfer de entrada de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/GetNumberOfConsoleInputEvents
- wincon/GetNumberOfConsoleInputEvents
- GetNumberOfConsoleInputEvents
MS-HAID:
- '\_win32\_getnumberofconsoleinputevents'
- base.getnumberofconsoleinputevents
- consoles.getnumberofconsoleinputevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1083b4f1-8fa6-4054-a516-3b447c3b0130
topic_type:
- apiref
api_name:
- GetNumberOfConsoleInputEvents
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: c5e3a59308239898f78796170d08f8b21ca1b667
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060653"
---
# <a name="getnumberofconsoleinputevents-function"></a><span data-ttu-id="264ac-104">GetNumberOfConsoleInputEvents función)</span><span class="sxs-lookup"><span data-stu-id="264ac-104">GetNumberOfConsoleInputEvents function</span></span>


<span data-ttu-id="264ac-105">Recupera el número de registros de entrada no leídos en el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="264ac-105">Retrieves the number of unread input records in the console's input buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="264ac-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="264ac-106">Syntax</span></span>
------

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

<a name="parameters"></a><span data-ttu-id="264ac-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="264ac-107">Parameters</span></span>
----------

<span data-ttu-id="264ac-108">*hConsoleInput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="264ac-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="264ac-109">Identificador para el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="264ac-109">A handle to the console input buffer.</span></span> <span data-ttu-id="264ac-110">El identificador debe tener el derecho de acceso de \*\* \_ lectura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="264ac-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="264ac-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="264ac-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="264ac-112">*lpcNumberOfEvents* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="264ac-112">*lpcNumberOfEvents* \[out\]</span></span>  
<span data-ttu-id="264ac-113">Un puntero a una variable que recibe el número de registros de entrada no leídos en el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="264ac-113">A pointer to a variable that receives the number of unread input records in the console's input buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="264ac-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="264ac-114">Return value</span></span>
------------

<span data-ttu-id="264ac-115">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="264ac-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="264ac-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="264ac-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="264ac-117">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="264ac-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="264ac-118">Observaciones</span><span class="sxs-lookup"><span data-stu-id="264ac-118">Remarks</span></span>
-------

<span data-ttu-id="264ac-119">La función **GetNumberOfConsoleInputEvents** informa del número total de registros de entrada no leídos en el búfer de entrada, incluidos el teclado, el mouse y los registros de entrada de cambio de tamaño de ventana.</span><span class="sxs-lookup"><span data-stu-id="264ac-119">The **GetNumberOfConsoleInputEvents** function reports the total number of unread input records in the input buffer, including keyboard, mouse, and window-resizing input records.</span></span> <span data-ttu-id="264ac-120">Los procesos que usan la función [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) solo pueden leer entradas de teclado.</span><span class="sxs-lookup"><span data-stu-id="264ac-120">Processes using the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function can only read keyboard input.</span></span> <span data-ttu-id="264ac-121">Los procesos que usan la función [**ReadConsoleInput**](readconsoleinput.md) pueden leer todos los tipos de registros de entrada.</span><span class="sxs-lookup"><span data-stu-id="264ac-121">Processes using the [**ReadConsoleInput**](readconsoleinput.md) function can read all types of input records.</span></span>

<span data-ttu-id="264ac-122">Un proceso puede especificar un identificador de búfer de entrada de la consola en una de las [funciones de espera](https://msdn.microsoft.com/library/windows/desktop/ms687069) para determinar si hay una entrada de consola sin leer.</span><span class="sxs-lookup"><span data-stu-id="264ac-122">A process can specify a console input buffer handle in one of the [wait functions](https://msdn.microsoft.com/library/windows/desktop/ms687069) to determine when there is unread console input.</span></span> <span data-ttu-id="264ac-123">Cuando el búfer de entrada no está vacío, se señala el estado de un controlador de búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="264ac-123">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="264ac-124">Para leer los registros de entrada desde un búfer de entrada de la consola sin afectar al número de registros no leídos, utilice la función [**PeekConsoleInput**](peekconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="264ac-124">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="264ac-125">Para descartar todos los registros no leídos en el búfer de entrada de la consola, use la función [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .</span><span class="sxs-lookup"><span data-stu-id="264ac-125">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

<a name="requirements"></a><span data-ttu-id="264ac-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="264ac-126">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="264ac-127">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="264ac-127">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="264ac-128">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="264ac-128">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="264ac-129">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="264ac-129">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="264ac-130">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="264ac-130">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="264ac-131">Encabezado</span><span class="sxs-lookup"><span data-stu-id="264ac-131">Header</span></span></p></td>
<td><span data-ttu-id="264ac-132">ConsoleApi. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="264ac-132">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="264ac-133">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="264ac-133">Library</span></span></p></td>
<td><span data-ttu-id="264ac-134">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="264ac-134">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="264ac-135">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="264ac-135">DLL</span></span></p></td>
<td><span data-ttu-id="264ac-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="264ac-136">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="264ac-137"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="264ac-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="264ac-138">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="264ac-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="264ac-139">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="264ac-139">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="264ac-140">Funciones de entrada de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="264ac-140">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="264ac-141">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="264ac-141">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="264ac-142">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="264ac-142">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="264ac-143">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="264ac-143">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="264ac-144">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="264ac-144">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

 

 




