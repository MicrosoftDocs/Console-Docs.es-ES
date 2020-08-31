---
title: GetStdHandle (función)
description: Recupera un identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- processenv/GetStdHandle
- winbase/GetStdHandle
- GetStdHandle
MS-HAID:
- '\_win32\_getstdhandle'
- base.getstdhandle
- consoles.getstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 23cd76e9-671a-48d0-9b82-2beda8917348
topic_type:
- apiref
api_name:
- GetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 613aacf4052e8e3b38c0a3e254ac4dd2b55ced5d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060617"
---
# <a name="getstdhandle-function"></a><span data-ttu-id="fe07a-104">GetStdHandle (función)</span><span class="sxs-lookup"><span data-stu-id="fe07a-104">GetStdHandle function</span></span>


<span data-ttu-id="fe07a-105">Recupera un identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).</span><span class="sxs-lookup"><span data-stu-id="fe07a-105">Retrieves a handle to the specified standard device (standard input, standard output, or standard error).</span></span>

<a name="syntax"></a><span data-ttu-id="fe07a-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fe07a-106">Syntax</span></span>
------

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

<a name="parameters"></a><span data-ttu-id="fe07a-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="fe07a-107">Parameters</span></span>
----------

<span data-ttu-id="fe07a-108">*nStdHandle* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="fe07a-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="fe07a-109">El dispositivo estándar.</span><span class="sxs-lookup"><span data-stu-id="fe07a-109">The standard device.</span></span> <span data-ttu-id="fe07a-110">Este parámetro puede ser uno de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="fe07a-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="fe07a-111">Valor</span><span class="sxs-lookup"><span data-stu-id="fe07a-111">Value</span></span></th>
<th><span data-ttu-id="fe07a-112">Significado</span><span class="sxs-lookup"><span data-stu-id="fe07a-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="fe07a-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</span><span class="sxs-lookup"><span data-stu-id="fe07a-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD) -10</span></span></td>
<td><p><span data-ttu-id="fe07a-114">El dispositivo de entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="fe07a-114">The standard input device.</span></span> <span data-ttu-id="fe07a-115">Inicialmente, es el búfer de entrada de la consola, CONIN $.</span><span class="sxs-lookup"><span data-stu-id="fe07a-115">Initially, this is the console input buffer, CONIN$.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="fe07a-116"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</span><span class="sxs-lookup"><span data-stu-id="fe07a-116"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD) -11</span></span></td>
<td><p><span data-ttu-id="fe07a-117">El dispositivo de salida estándar.</span><span class="sxs-lookup"><span data-stu-id="fe07a-117">The standard output device.</span></span> <span data-ttu-id="fe07a-118">Inicialmente, es el búfer de pantalla de la consola activo, CONOUT $.</span><span class="sxs-lookup"><span data-stu-id="fe07a-118">Initially, this is the active console screen buffer, CONOUT$.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="fe07a-119"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</span><span class="sxs-lookup"><span data-stu-id="fe07a-119"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD) -12</span></span></td>
<td><p><span data-ttu-id="fe07a-120">El dispositivo de error estándar.</span><span class="sxs-lookup"><span data-stu-id="fe07a-120">The standard error device.</span></span> <span data-ttu-id="fe07a-121">Inicialmente, es el búfer de pantalla de la consola activo, CONOUT $.</span><span class="sxs-lookup"><span data-stu-id="fe07a-121">Initially, this is the active console screen buffer, CONOUT$.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="fe07a-122">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="fe07a-122">Return value</span></span>
------------

<span data-ttu-id="fe07a-123">Si la función se ejecuta correctamente, el valor devuelto es un identificador del dispositivo especificado o un identificador Redirigido establecido por una llamada anterior a [**SetStdHandle**](setstdhandle.md).</span><span class="sxs-lookup"><span data-stu-id="fe07a-123">If the function succeeds, the return value is a handle to the specified device, or a redirected handle set by a previous call to [**SetStdHandle**](setstdhandle.md).</span></span> <span data-ttu-id="fe07a-124">El identificador tiene derechos de acceso genéricos de \*\* \_ lectura\*\* y \*\* \_ escritura\*\* , a menos que la aplicación haya usado **SetStdHandle** para establecer un identificador estándar con un acceso inferior.</span><span class="sxs-lookup"><span data-stu-id="fe07a-124">The handle has **GENERIC\_READ** and **GENERIC\_WRITE** access rights, unless the application has used **SetStdHandle** to set a standard handle with lesser access.</span></span>

<span data-ttu-id="fe07a-125">Si se produce un error en la función, el valor devuelto es un \*\* \_ \_ valor de identificador no válido\*\*.</span><span class="sxs-lookup"><span data-stu-id="fe07a-125">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="fe07a-126">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="fe07a-126">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="fe07a-127">Si una aplicación no tiene identificadores estándar asociados, como un servicio que se ejecuta en un escritorio interactivo y no los ha redirigido, el valor devuelto es **null**.</span><span class="sxs-lookup"><span data-stu-id="fe07a-127">If an application does not have associated standard handles, such as a service running on an interactive desktop, and has not redirected them, the return value is **NULL**.</span></span>

<a name="remarks"></a><span data-ttu-id="fe07a-128">Observaciones</span><span class="sxs-lookup"><span data-stu-id="fe07a-128">Remarks</span></span>
-------

<span data-ttu-id="fe07a-129">Los identificadores devueltos por **GetStdHandle** pueden ser usados por aplicaciones que necesitan leer o escribir en la consola.</span><span class="sxs-lookup"><span data-stu-id="fe07a-129">Handles returned by **GetStdHandle** can be used by applications that need to read from or write to the console.</span></span> <span data-ttu-id="fe07a-130">Cuando se crea una consola, el identificador de entrada estándar es un identificador del búfer de entrada de la consola, y los identificadores de salida estándar y de error estándar son identificadores del búfer de pantalla activo de la consola.</span><span class="sxs-lookup"><span data-stu-id="fe07a-130">When a console is created, the standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles of the console's active screen buffer.</span></span> <span data-ttu-id="fe07a-131">Estos identificadores pueden ser utilizados por las funciones [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) , o por cualquiera de las funciones de consola que tienen acceso al búfer de entrada de la consola o a un búfer de pantalla (por ejemplo, las funciones [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md)o [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) ).</span><span class="sxs-lookup"><span data-stu-id="fe07a-131">These handles can be used by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) functions, or by any of the console functions that access the console input buffer or a screen buffer (for example, the [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md), or [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) functions).</span></span>

<span data-ttu-id="fe07a-132">Los identificadores estándar de un proceso se pueden redirigir mediante una llamada a [**SetStdHandle**](setstdhandle.md), en cuyo caso **GetStdHandle** devuelve el identificador redirigido.</span><span class="sxs-lookup"><span data-stu-id="fe07a-132">The standard handles of a process may be redirected by a call to [**SetStdHandle**](setstdhandle.md), in which case **GetStdHandle** returns the redirected handle.</span></span> <span data-ttu-id="fe07a-133">Si se han redirigido los identificadores estándar, puede especificar el valor de CONIN $ en una llamada a la función [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) para obtener un identificador para el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="fe07a-133">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="fe07a-134">De forma similar, puede especificar el valor de CONOUT $ para obtener un identificador para el búfer de pantalla activo de la consola.</span><span class="sxs-lookup"><span data-stu-id="fe07a-134">Similarly, you can specify the CONOUT$ value to get a handle to a console's active screen buffer.</span></span>

### <a name="span-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanattachdetach-behavior"></a><span data-ttu-id="fe07a-135"><span id="Attach_detach_behavior"></span><span id="attach_detach_behavior"></span><span id="ATTACH_DETACH_BEHAVIOR"></span>Comportamiento de adjuntar/separar</span><span class="sxs-lookup"><span data-stu-id="fe07a-135"><span id="Attach_detach_behavior"></span><span id="attach_detach_behavior"></span><span id="ATTACH_DETACH_BEHAVIOR"></span>Attach/detach behavior</span></span>

<span data-ttu-id="fe07a-136">Al conectarse a una nueva consola, los identificadores estándar siempre se reemplazan por identificadores de consola, a menos que se haya especificado **STARTF \_ USESTDHANDLES** durante la creación del proceso.</span><span class="sxs-lookup"><span data-stu-id="fe07a-136">When attaching to a new console, standard handles are always replaced with console handles unless **STARTF\_USESTDHANDLES** was specified during process creation.</span></span>

<span data-ttu-id="fe07a-137">Si el valor existente del identificador estándar es **null**, o el valor existente del identificador estándar es similar a un pseudohandle de consola, el identificador se reemplaza por un identificador de consola.</span><span class="sxs-lookup"><span data-stu-id="fe07a-137">If the existing value of the standard handle is **NULL**, or the existing value of the standard handle looks like a console pseudohandle, the handle is replaced with a console handle.</span></span>

<span data-ttu-id="fe07a-138">Cuando un elemento primario usa **Create \_ New \_ Console** y **STARTF \_ USESTDHANDLES** para crear un proceso de consola, no se reemplazarán los identificadores estándar a menos que el valor existente del identificador estándar sea NULL o una pseudohandle de consola.</span><span class="sxs-lookup"><span data-stu-id="fe07a-138">When a parent uses both **CREATE\_NEW\_CONSOLE** and **STARTF\_USESTDHANDLES** to create a console process, standard handles will not be replaced unless the existing value of the standard handle is NULL or a console pseudohandle.</span></span>

<a name="examples"></a><span data-ttu-id="fe07a-139">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="fe07a-139">Examples</span></span>
--------

<span data-ttu-id="fe07a-140">Para obtener un ejemplo, vea [leer eventos de búfer de entrada](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="fe07a-140">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="fe07a-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fe07a-141">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="fe07a-142">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="fe07a-142">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="fe07a-143">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="fe07a-143">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="fe07a-144">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="fe07a-144">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="fe07a-145">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="fe07a-145">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="fe07a-146">Encabezado</span><span class="sxs-lookup"><span data-stu-id="fe07a-146">Header</span></span></p></td>
<td><span data-ttu-id="fe07a-147">ProcessEnv. h (a través de Winbase. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="fe07a-147">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="fe07a-148">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="fe07a-148">Library</span></span></p></td>
<td><span data-ttu-id="fe07a-149">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="fe07a-149">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="fe07a-150">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="fe07a-150">DLL</span></span></p></td>
<td><span data-ttu-id="fe07a-151">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="fe07a-151">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="fe07a-152"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="fe07a-152"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="fe07a-153">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="fe07a-153">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="fe07a-154">Identificadores de consola</span><span class="sxs-lookup"><span data-stu-id="fe07a-154">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="fe07a-155">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="fe07a-155">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="fe07a-156">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="fe07a-156">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="fe07a-157">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="fe07a-157">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="fe07a-158">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="fe07a-158">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="fe07a-159">**SetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="fe07a-159">**SetStdHandle**</span></span>](setstdhandle.md)

[<span data-ttu-id="fe07a-160">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="fe07a-160">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="fe07a-161">**Escritura**</span><span class="sxs-lookup"><span data-stu-id="fe07a-161">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




