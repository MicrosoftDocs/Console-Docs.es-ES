---
title: GetConsoleSelectionInfo función)
description: Consulte la información de referencia sobre la función GetConsoleSelectionInfo, que recupera información sobre la selección de la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleSelectionInfo
- wincon/GetConsoleSelectionInfo
- GetConsoleSelectionInfo
MS-HAID:
- '\_win32\_getconsoleselectioninfo'
- base.getconsoleselectioninfo
- consoles.getconsoleselectioninfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 912efe9d-75dd-43bd-8dca-08671b5ed79c
topic_type:
- apiref
api_name:
- GetConsoleSelectionInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: d29a960bc6b8d96d98e0667084e31354f2aa9653
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060657"
---
# <a name="getconsoleselectioninfo-function"></a><span data-ttu-id="e7096-104">GetConsoleSelectionInfo función)</span><span class="sxs-lookup"><span data-stu-id="e7096-104">GetConsoleSelectionInfo function</span></span>


<span data-ttu-id="e7096-105">Recupera información sobre la selección de la consola actual.</span><span class="sxs-lookup"><span data-stu-id="e7096-105">Retrieves information about the current console selection.</span></span>

<a name="syntax"></a><span data-ttu-id="e7096-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e7096-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleSelectionInfo(
  _Out_ PCONSOLE_SELECTION_INFO lpConsoleSelectionInfo
);
```

<a name="parameters"></a><span data-ttu-id="e7096-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e7096-107">Parameters</span></span>
----------

<span data-ttu-id="e7096-108">*lpConsoleSelectionInfo* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="e7096-108">*lpConsoleSelectionInfo* \[out\]</span></span>  
<span data-ttu-id="e7096-109">Un puntero a una estructura de [\*\* \_ \_ información de selección de consola\*\*](console-selection-info-str.md) que recibe la información de selección.</span><span class="sxs-lookup"><span data-stu-id="e7096-109">A pointer to a [**CONSOLE\_SELECTION\_INFO**](console-selection-info-str.md) structure that receives the selection information.</span></span>

<a name="return-value"></a><span data-ttu-id="e7096-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="e7096-110">Return value</span></span>
------------

<span data-ttu-id="e7096-111">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="e7096-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e7096-112">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="e7096-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e7096-113">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="e7096-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="e7096-114">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e7096-114">Remarks</span></span>
-------

<span data-ttu-id="e7096-115">Para compilar una aplicación que usa esta función, defina \*\* \_ Win32 \_ WinNT\*\* como 0x0500 o posterior.</span><span class="sxs-lookup"><span data-stu-id="e7096-115">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="e7096-116">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="e7096-116">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="e7096-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e7096-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e7096-118">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="e7096-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="e7096-119">Windows XP [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="e7096-119">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e7096-120">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="e7096-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="e7096-121">Windows Server 2003 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="e7096-121">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e7096-122">Encabezado</span><span class="sxs-lookup"><span data-stu-id="e7096-122">Header</span></span></p></td>
<td><span data-ttu-id="e7096-123">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e7096-123">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e7096-124">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="e7096-124">Library</span></span></p></td>
<td><span data-ttu-id="e7096-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="e7096-125">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e7096-126">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="e7096-126">DLL</span></span></p></td>
<td><span data-ttu-id="e7096-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e7096-127">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="e7096-128"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="e7096-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="e7096-129">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="e7096-129">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e7096-130">Selección de la consola</span><span class="sxs-lookup"><span data-stu-id="e7096-130">Console Selection</span></span>](console-selection.md)

[<span data-ttu-id="e7096-131">**\_información de selección de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="e7096-131">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)

 

 




