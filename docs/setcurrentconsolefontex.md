---
title: SetCurrentConsoleFontEx función)
description: Consulte la información de referencia sobre la función SetCurrentConsoleFontEx, que establece la información extendida sobre la fuente de consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/SetCurrentConsoleFontEx
- wincon/SetCurrentConsoleFontEx
- SetCurrentConsoleFontEx
MS-HAID:
- base.setcurrentconsolefontex
- consoles.setcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: fbc31e2a-31df-4e9e-9f61-35a4ff812f8f
topic_type:
- apiref
api_name:
- SetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 9d97383f40c38489ac3ea5e7c75386163b9d5d2d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060813"
---
# <a name="setcurrentconsolefontex-function"></a><span data-ttu-id="de090-104">SetCurrentConsoleFontEx función)</span><span class="sxs-lookup"><span data-stu-id="de090-104">SetCurrentConsoleFontEx function</span></span>


<span data-ttu-id="de090-105">Establece la información extendida sobre la fuente de consola actual.</span><span class="sxs-lookup"><span data-stu-id="de090-105">Sets extended information about the current console font.</span></span>

<a name="syntax"></a><span data-ttu-id="de090-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="de090-106">Syntax</span></span>
------

```C
BOOL WINAPI SetCurrentConsoleFontEx(
  _In_ HANDLE               hConsoleOutput,
  _In_ BOOL                 bMaximumWindow,
  _In_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

<a name="parameters"></a><span data-ttu-id="de090-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="de090-107">Parameters</span></span>
----------

<span data-ttu-id="de090-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="de090-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="de090-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="de090-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="de090-110">El identificador debe tener el derecho de acceso de \*\* \_ escritura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="de090-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="de090-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="de090-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="de090-112">*bMaximumWindow* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="de090-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="de090-113">Si este parámetro es **true**, la información de fuente se establece para el tamaño máximo de la ventana.</span><span class="sxs-lookup"><span data-stu-id="de090-113">If this parameter is **TRUE**, font information is set for the maximum window size.</span></span> <span data-ttu-id="de090-114">Si este parámetro es **false**, se establece la información de fuente para el tamaño de la ventana actual.</span><span class="sxs-lookup"><span data-stu-id="de090-114">If this parameter is **FALSE**, font information is set for the current window size.</span></span>

<span data-ttu-id="de090-115">*lpConsoleCurrentFontEx* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="de090-115">*lpConsoleCurrentFontEx* \[in\]</span></span>  
<span data-ttu-id="de090-116">Puntero a una estructura [\*\* \_ \_ INFOEX\*\*](console-font-infoex.md) de la fuente de la consola que contiene la información de la fuente.</span><span class="sxs-lookup"><span data-stu-id="de090-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that contains the font information.</span></span>

<a name="return-value"></a><span data-ttu-id="de090-117">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="de090-117">Return value</span></span>
------------

<span data-ttu-id="de090-118">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="de090-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="de090-119">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="de090-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="de090-120">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="de090-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="de090-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="de090-121">Remarks</span></span>
-------

<span data-ttu-id="de090-122">Para compilar una aplicación que usa esta función, defina \*\* \_ Win32 \_ WinNT\*\* como 0x0500 o posterior.</span><span class="sxs-lookup"><span data-stu-id="de090-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="de090-123">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="de090-123">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="de090-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="de090-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="de090-125">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="de090-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="de090-126">Windows Vista [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="de090-126">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="de090-127">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="de090-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="de090-128">Windows Server 2008 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="de090-128">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="de090-129">Encabezado</span><span class="sxs-lookup"><span data-stu-id="de090-129">Header</span></span></p></td>
<td><span data-ttu-id="de090-130">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="de090-130">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="de090-131">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="de090-131">Library</span></span></p></td>
<td><span data-ttu-id="de090-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="de090-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="de090-133">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="de090-133">DLL</span></span></p></td>
<td><span data-ttu-id="de090-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="de090-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="de090-135"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="de090-135"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="de090-136">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="de090-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="de090-137">**fuente de consola \_ \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="de090-137">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)

 

 




