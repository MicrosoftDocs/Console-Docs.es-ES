---
title: FreeConsole función)
description: Vea la información de referencia sobre la función FreeConsole, que separa el proceso de llamada de su consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/FreeConsole
- wincon/FreeConsole
- FreeConsole
MS-HAID:
- '\_win32\_freeconsole'
- base.freeconsole
- consoles.freeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6c525325-696e-4d8b-8337-cbf9e31c900c
topic_type:
- apiref
api_name:
- FreeConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 3c8ba7b236b379bb57729538e065afebb68cc0cf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060740"
---
# <a name="freeconsole-function"></a><span data-ttu-id="caa81-104">FreeConsole función)</span><span class="sxs-lookup"><span data-stu-id="caa81-104">FreeConsole function</span></span>


<span data-ttu-id="caa81-105">Desasocia el proceso de llamada de su consola.</span><span class="sxs-lookup"><span data-stu-id="caa81-105">Detaches the calling process from its console.</span></span>

<a name="syntax"></a><span data-ttu-id="caa81-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="caa81-106">Syntax</span></span>
------

```C
BOOL WINAPI FreeConsole(void);
```

<a name="parameters"></a><span data-ttu-id="caa81-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="caa81-107">Parameters</span></span>
----------

<span data-ttu-id="caa81-108">Esta función no tiene parámetros.</span><span class="sxs-lookup"><span data-stu-id="caa81-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="caa81-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="caa81-109">Return value</span></span>
------------

<span data-ttu-id="caa81-110">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="caa81-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="caa81-111">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="caa81-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="caa81-112">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="caa81-112">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="caa81-113">Observaciones</span><span class="sxs-lookup"><span data-stu-id="caa81-113">Remarks</span></span>
-------

<span data-ttu-id="caa81-114">Un proceso se puede adjuntar a como máximo una consola.</span><span class="sxs-lookup"><span data-stu-id="caa81-114">A process can be attached to at most one console.</span></span> <span data-ttu-id="caa81-115">Si el proceso de llamada no está asociado ya a una consola de, el código de error devuelto es un \*\* \_ \_ parámetro no válido de error\*\* (87).</span><span class="sxs-lookup"><span data-stu-id="caa81-115">If the calling process is not already attached to a console, the error code returned is **ERROR\_INVALID\_PARAMETER** (87).</span></span>

<span data-ttu-id="caa81-116">Un proceso puede usar la función **FreeConsole** para desasociarse de su consola.</span><span class="sxs-lookup"><span data-stu-id="caa81-116">A process can use the **FreeConsole** function to detach itself from its console.</span></span> <span data-ttu-id="caa81-117">Si otros procesos comparten la consola, la consola no se destruye, pero el proceso que llamó a **FreeConsole** no puede hacer referencia a ella.</span><span class="sxs-lookup"><span data-stu-id="caa81-117">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="caa81-118">Una consola se cierra cuando el último proceso asociado a ella finaliza o llama a **FreeConsole**.</span><span class="sxs-lookup"><span data-stu-id="caa81-118">A console is closed when the last process attached to it terminates or calls **FreeConsole**.</span></span> <span data-ttu-id="caa81-119">Una vez que un proceso llama a **FreeConsole**, puede llamar a la función [**AllocConsole**](allocconsole.md) para crear una nueva consola o [**AttachConsole**](attachconsole.md) para asociar a otra consola.</span><span class="sxs-lookup"><span data-stu-id="caa81-119">After a process calls **FreeConsole**, it can call the [**AllocConsole**](allocconsole.md) function to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<a name="requirements"></a><span data-ttu-id="caa81-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="caa81-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="caa81-121">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="caa81-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="caa81-122">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="caa81-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="caa81-123">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="caa81-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="caa81-124">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="caa81-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="caa81-125">Encabezado</span><span class="sxs-lookup"><span data-stu-id="caa81-125">Header</span></span></p></td>
<td><span data-ttu-id="caa81-126">ConsoleApi. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="caa81-126">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="caa81-127">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="caa81-127">Library</span></span></p></td>
<td><span data-ttu-id="caa81-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="caa81-128">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="caa81-129">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="caa81-129">DLL</span></span></p></td>
<td><span data-ttu-id="caa81-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="caa81-130">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="caa81-131"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="caa81-131"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="caa81-132">**AllocConsole**</span><span class="sxs-lookup"><span data-stu-id="caa81-132">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="caa81-133">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="caa81-133">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="caa81-134">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="caa81-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="caa81-135">Consolas</span><span class="sxs-lookup"><span data-stu-id="caa81-135">Consoles</span></span>](consoles.md)

 

 




