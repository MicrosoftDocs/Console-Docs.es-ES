---
title: AttachConsole función)
description: Vea la información de referencia sobre la función AttachConsole, que asocia el proceso de llamada a la consola del proceso especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- base.attachconsole
- consoles.attachconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c4048a2fb4c93d9f286ffc1ef7f38923836f37bf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060921"
---
# <a name="attachconsole-function"></a><span data-ttu-id="afc99-104">AttachConsole función)</span><span class="sxs-lookup"><span data-stu-id="afc99-104">AttachConsole function</span></span>


<span data-ttu-id="afc99-105">Asocia el proceso de llamada a la consola del proceso especificado.</span><span class="sxs-lookup"><span data-stu-id="afc99-105">Attaches the calling process to the console of the specified process.</span></span>

<a name="syntax"></a><span data-ttu-id="afc99-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="afc99-106">Syntax</span></span>
------

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

<a name="parameters"></a><span data-ttu-id="afc99-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="afc99-107">Parameters</span></span>
----------

<span data-ttu-id="afc99-108">*dwProcessId* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="afc99-108">*dwProcessId* \[in\]</span></span>  
<span data-ttu-id="afc99-109">Identificador del proceso cuya consola se va a usar.</span><span class="sxs-lookup"><span data-stu-id="afc99-109">The identifier of the process whose console is to be used.</span></span> <span data-ttu-id="afc99-110">Este parámetro puede ser uno de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="afc99-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="afc99-111">Valor</span><span class="sxs-lookup"><span data-stu-id="afc99-111">Value</span></span></th>
<th><span data-ttu-id="afc99-112">Significado</span><span class="sxs-lookup"><span data-stu-id="afc99-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="afc99-113"><em>pid</em></span><span class="sxs-lookup"><span data-stu-id="afc99-113"><em>pid</em></span></span></td>
<td><p><span data-ttu-id="afc99-114">Use la consola del proceso especificado.</span><span class="sxs-lookup"><span data-stu-id="afc99-114">Use the console of the specified process.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="afc99-115"><span id="ATTACH_PARENT_PROCESS"></span><span id="attach_parent_process"></span>
<strong>ATTACH_PARENT_PROCESS</strong> (DWORD)-1</span><span class="sxs-lookup"><span data-stu-id="afc99-115"><span id="ATTACH_PARENT_PROCESS"></span><span id="attach_parent_process"></span>
<strong>ATTACH_PARENT_PROCESS</strong> (DWORD)-1</span></span></td>
<td><p><span data-ttu-id="afc99-116">Use la consola del elemento primario del proceso actual.</span><span class="sxs-lookup"><span data-stu-id="afc99-116">Use the console of the parent of the current process.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="afc99-117">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="afc99-117">Return value</span></span>
------------

<span data-ttu-id="afc99-118">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="afc99-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="afc99-119">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="afc99-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="afc99-120">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="afc99-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="afc99-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="afc99-121">Remarks</span></span>
-------

<span data-ttu-id="afc99-122">Un proceso se puede adjuntar a como máximo una consola.</span><span class="sxs-lookup"><span data-stu-id="afc99-122">A process can be attached to at most one console.</span></span> <span data-ttu-id="afc99-123">Si el proceso de llamada ya está asociado a una consola de, el código de error devuelto es **error de \_ acceso \_ denegado** (5).</span><span class="sxs-lookup"><span data-stu-id="afc99-123">If the calling process is already attached to a console, the error code returned is **ERROR\_ACCESS\_DENIED** (5).</span></span> <span data-ttu-id="afc99-124">Si el proceso especificado no tiene una consola de, el código de error devuelto es un \*\*identificador de error \_ no válido \_ \*\* (6).</span><span class="sxs-lookup"><span data-stu-id="afc99-124">If the specified process does not have a console, the error code returned is **ERROR\_INVALID\_HANDLE** (6).</span></span> <span data-ttu-id="afc99-125">Si el proceso especificado no existe, el código de error devuelto es un \*\*parámetro de error \_ no válido \_ \*\* (87).</span><span class="sxs-lookup"><span data-stu-id="afc99-125">If the specified process does not exist, the error code returned is **ERROR\_INVALID\_PARAMETER** (87).</span></span>

<span data-ttu-id="afc99-126">Un proceso puede usar la función [**FreeConsole**](freeconsole.md) para desasociarse de su consola.</span><span class="sxs-lookup"><span data-stu-id="afc99-126">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console.</span></span> <span data-ttu-id="afc99-127">Si otros procesos comparten la consola, la consola no se destruye, pero el proceso que llamó a **FreeConsole** no puede hacer referencia a ella.</span><span class="sxs-lookup"><span data-stu-id="afc99-127">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="afc99-128">Una consola se cierra cuando el último proceso asociado a ella finaliza o llama a **FreeConsole**.</span><span class="sxs-lookup"><span data-stu-id="afc99-128">A console is closed when the last process attached to it terminates or calls **FreeConsole**.</span></span> <span data-ttu-id="afc99-129">Una vez que un proceso llama a **FreeConsole**, puede llamar a la función [**AllocConsole**](allocconsole.md) para crear una nueva consola o **AttachConsole** para asociar a otra consola.</span><span class="sxs-lookup"><span data-stu-id="afc99-129">After a process calls **FreeConsole**, it can call the [**AllocConsole**](allocconsole.md) function to create a new console or **AttachConsole** to attach to another console.</span></span>

<span data-ttu-id="afc99-130">Para compilar una aplicación que usa esta función, defina \*\* \_ Win32 \_ WinNT\*\* como 0x0501 o posterior.</span><span class="sxs-lookup"><span data-stu-id="afc99-130">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="afc99-131">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="afc99-131">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="afc99-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="afc99-132">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="afc99-133">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="afc99-133">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="afc99-134">Windows XP [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="afc99-134">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="afc99-135">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="afc99-135">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="afc99-136">Windows Server 2003 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="afc99-136">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="afc99-137">Encabezado</span><span class="sxs-lookup"><span data-stu-id="afc99-137">Header</span></span></p></td>
<td><span data-ttu-id="afc99-138">ConsoleApi. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="afc99-138">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="afc99-139">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="afc99-139">Library</span></span></p></td>
<td><span data-ttu-id="afc99-140">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="afc99-140">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="afc99-141">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="afc99-141">DLL</span></span></p></td>
<td><span data-ttu-id="afc99-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="afc99-142">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="afc99-143"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="afc99-143"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="afc99-144">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="afc99-144">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="afc99-145">Consolas</span><span class="sxs-lookup"><span data-stu-id="afc99-145">Consoles</span></span>](consoles.md)

[<span data-ttu-id="afc99-146">**AllocConsole**</span><span class="sxs-lookup"><span data-stu-id="afc99-146">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="afc99-147">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="afc99-147">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="afc99-148">**GetConsoleProcessList**</span><span class="sxs-lookup"><span data-stu-id="afc99-148">**GetConsoleProcessList**</span></span>](getconsoleprocesslist.md)

 

 




