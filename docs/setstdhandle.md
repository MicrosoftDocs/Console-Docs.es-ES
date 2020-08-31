---
title: SetStdHandle función)
description: Establece el identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 6ab17a2162d31c956ec64dbb33696c20ae085298
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061100"
---
# <a name="setstdhandle-function"></a><span data-ttu-id="f9b25-104">SetStdHandle función)</span><span class="sxs-lookup"><span data-stu-id="f9b25-104">SetStdHandle function</span></span>


<span data-ttu-id="f9b25-105">Establece el identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).</span><span class="sxs-lookup"><span data-stu-id="f9b25-105">Sets the handle for the specified standard device (standard input, standard output, or standard error).</span></span>

<a name="syntax"></a><span data-ttu-id="f9b25-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f9b25-106">Syntax</span></span>
------

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

<a name="parameters"></a><span data-ttu-id="f9b25-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="f9b25-107">Parameters</span></span>
----------

<span data-ttu-id="f9b25-108">*nStdHandle* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="f9b25-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="f9b25-109">El dispositivo estándar para el que se establecerá el identificador.</span><span class="sxs-lookup"><span data-stu-id="f9b25-109">The standard device for which the handle is to be set.</span></span> <span data-ttu-id="f9b25-110">Este parámetro puede ser uno de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="f9b25-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="f9b25-111">Valor</span><span class="sxs-lookup"><span data-stu-id="f9b25-111">Value</span></span></th>
<th><span data-ttu-id="f9b25-112">Significado</span><span class="sxs-lookup"><span data-stu-id="f9b25-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="f9b25-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</span><span class="sxs-lookup"><span data-stu-id="f9b25-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</span></span></td>
<td><p><span data-ttu-id="f9b25-114">El dispositivo de entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="f9b25-114">The standard input device.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="f9b25-115"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</span><span class="sxs-lookup"><span data-stu-id="f9b25-115"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</span></span></td>
<td><p><span data-ttu-id="f9b25-116">El dispositivo de salida estándar.</span><span class="sxs-lookup"><span data-stu-id="f9b25-116">The standard output device.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="f9b25-117"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</span><span class="sxs-lookup"><span data-stu-id="f9b25-117"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</span></span></td>
<td><p><span data-ttu-id="f9b25-118">El dispositivo de error estándar.</span><span class="sxs-lookup"><span data-stu-id="f9b25-118">The standard error device.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="f9b25-119">*hHandle* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="f9b25-119">*hHandle* \[in\]</span></span>  
<span data-ttu-id="f9b25-120">Identificador del dispositivo estándar.</span><span class="sxs-lookup"><span data-stu-id="f9b25-120">The handle for the standard device.</span></span>

<a name="return-value"></a><span data-ttu-id="f9b25-121">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="f9b25-121">Return value</span></span>
------------

<span data-ttu-id="f9b25-122">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="f9b25-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="f9b25-123">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="f9b25-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="f9b25-124">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="f9b25-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="f9b25-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="f9b25-125">Remarks</span></span>
-------

<span data-ttu-id="f9b25-126">Es posible que los identificadores estándar de un proceso se hayan Redirigido mediante una llamada a **SetStdHandle**, en cuyo caso [**GetStdHandle**](getstdhandle.md) devolverá el identificador redirigido.</span><span class="sxs-lookup"><span data-stu-id="f9b25-126">The standard handles of a process may have been redirected by a call to **SetStdHandle**, in which case [**GetStdHandle**](getstdhandle.md) will return the redirected handle.</span></span> <span data-ttu-id="f9b25-127">Si se han redirigido los identificadores estándar, puede especificar el valor de CONIN $ en una llamada a la función [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) para obtener un identificador para el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="f9b25-127">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="f9b25-128">De forma similar, puede especificar el valor de CONOUT $ para obtener un identificador para el búfer de pantalla activo de la consola.</span><span class="sxs-lookup"><span data-stu-id="f9b25-128">Similarly, you can specify the CONOUT$ value to get a handle to the console's active screen buffer.</span></span>

<a name="examples"></a><span data-ttu-id="f9b25-129">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="f9b25-129">Examples</span></span>
--------

<span data-ttu-id="f9b25-130">Para obtener un ejemplo, consulte [creación de un proceso secundario con entrada y salida redirigidas](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span><span class="sxs-lookup"><span data-stu-id="f9b25-130">For an example, see [Creating a Child Process with Redirected Input and Output](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span></span>

<a name="requirements"></a><span data-ttu-id="f9b25-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9b25-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f9b25-132">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="f9b25-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="f9b25-133">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="f9b25-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f9b25-134">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="f9b25-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="f9b25-135">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="f9b25-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f9b25-136">Encabezado</span><span class="sxs-lookup"><span data-stu-id="f9b25-136">Header</span></span></p></td>
<td><span data-ttu-id="f9b25-137">ProcessEnv. h (a través de Winbase. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f9b25-137">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f9b25-138">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="f9b25-138">Library</span></span></p></td>
<td><span data-ttu-id="f9b25-139">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="f9b25-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f9b25-140">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="f9b25-140">DLL</span></span></p></td>
<td><span data-ttu-id="f9b25-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f9b25-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="f9b25-142"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="f9b25-142"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="f9b25-143">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="f9b25-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f9b25-144">Identificadores de consola</span><span class="sxs-lookup"><span data-stu-id="f9b25-144">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="f9b25-145">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="f9b25-145">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="f9b25-146">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="f9b25-146">**GetStdHandle**</span></span>](getstdhandle.md)

 

 




