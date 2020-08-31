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
ms.openlocfilehash: dd184e1fc1f788912be00e9270ccb239c20b8ce8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060744"
---
# <a name="flushconsoleinputbuffer-function"></a><span data-ttu-id="3c17b-105">FlushConsoleInputBuffer función)</span><span class="sxs-lookup"><span data-stu-id="3c17b-105">FlushConsoleInputBuffer function</span></span>


<span data-ttu-id="3c17b-106">Vacía el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="3c17b-106">Flushes the console input buffer.</span></span> <span data-ttu-id="3c17b-107">Se descartan todos los registros de entrada que se encuentran actualmente en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="3c17b-107">All input records currently in the input buffer are discarded.</span></span>

<a name="syntax"></a><span data-ttu-id="3c17b-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3c17b-108">Syntax</span></span>
------

```C
BOOL WINAPI FlushConsoleInputBuffer(
  _In_ HANDLE hConsoleInput
);
```

<a name="parameters"></a><span data-ttu-id="3c17b-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3c17b-109">Parameters</span></span>
----------

<span data-ttu-id="3c17b-110">*hConsoleInput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="3c17b-110">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="3c17b-111">Identificador para el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="3c17b-111">A handle to the console input buffer.</span></span> <span data-ttu-id="3c17b-112">El identificador debe tener el derecho de acceso de \*\* \_ escritura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="3c17b-112">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="3c17b-113">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="3c17b-113">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<a name="return-value"></a><span data-ttu-id="3c17b-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="3c17b-114">Return value</span></span>
------------

<span data-ttu-id="3c17b-115">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="3c17b-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="3c17b-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="3c17b-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="3c17b-117">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="3c17b-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="3c17b-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c17b-118">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="3c17b-119">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="3c17b-119">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="3c17b-120">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="3c17b-120">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3c17b-121">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="3c17b-121">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="3c17b-122">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="3c17b-122">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3c17b-123">Encabezado</span><span class="sxs-lookup"><span data-stu-id="3c17b-123">Header</span></span></p></td>
<td><span data-ttu-id="3c17b-124">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="3c17b-124">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3c17b-125">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="3c17b-125">Library</span></span></p></td>
<td><span data-ttu-id="3c17b-126">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="3c17b-126">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3c17b-127">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="3c17b-127">DLL</span></span></p></td>
<td><span data-ttu-id="3c17b-128">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3c17b-128">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="3c17b-129"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="3c17b-129"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="3c17b-130">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="3c17b-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3c17b-131">Funciones de entrada de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="3c17b-131">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="3c17b-132">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="3c17b-132">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="3c17b-133">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="3c17b-133">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="3c17b-134">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="3c17b-134">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="3c17b-135">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="3c17b-135">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 




