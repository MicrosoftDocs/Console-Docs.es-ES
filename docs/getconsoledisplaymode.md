---
title: GetConsoleDisplayMode función)
description: Vea la información de referencia sobre la función GetConsoleDisplayMode, que recupera el modo de presentación de la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 76b3354ac9b44c36ec4cfe3d12257583d10f2ee2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060712"
---
# <a name="getconsoledisplaymode-function"></a><span data-ttu-id="1dab6-104">GetConsoleDisplayMode función)</span><span class="sxs-lookup"><span data-stu-id="1dab6-104">GetConsoleDisplayMode function</span></span>


<span data-ttu-id="1dab6-105">Recupera el modo de presentación de la consola actual.</span><span class="sxs-lookup"><span data-stu-id="1dab6-105">Retrieves the display mode of the current console.</span></span>

<a name="syntax"></a><span data-ttu-id="1dab6-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1dab6-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

<a name="parameters"></a><span data-ttu-id="1dab6-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1dab6-107">Parameters</span></span>
----------

<span data-ttu-id="1dab6-108">*lpModeFlags* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="1dab6-108">*lpModeFlags* \[out\]</span></span>  
<span data-ttu-id="1dab6-109">Modo de presentación de la consola.</span><span class="sxs-lookup"><span data-stu-id="1dab6-109">The display mode of the console.</span></span> <span data-ttu-id="1dab6-110">Este parámetro puede ser uno o varios de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="1dab6-110">This parameter can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="1dab6-111">Valor</span><span class="sxs-lookup"><span data-stu-id="1dab6-111">Value</span></span></th>
<th><span data-ttu-id="1dab6-112">Significado</span><span class="sxs-lookup"><span data-stu-id="1dab6-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="1dab6-113"><span id="CONSOLE_FULLSCREEN"></span><span id="console_fullscreen"></span>
<strong>CONSOLE_FULLSCREEN</strong> 1</span><span class="sxs-lookup"><span data-stu-id="1dab6-113"><span id="CONSOLE_FULLSCREEN"></span><span id="console_fullscreen"></span>
<strong>CONSOLE_FULLSCREEN</strong> 1</span></span></td>
<td><p><span data-ttu-id="1dab6-114">Consola de pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="1dab6-114">Full-screen console.</span></span> <span data-ttu-id="1dab6-115">La consola está en este modo en cuanto se maximiza la ventana.</span><span class="sxs-lookup"><span data-stu-id="1dab6-115">The console is in this mode as soon as the window is maximized.</span></span> <span data-ttu-id="1dab6-116">En este momento, se puede producir un error en la transición al modo de pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="1dab6-116">At this point, the transition to full-screen mode can still fail.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="1dab6-117"><span id="CONSOLE_FULLSCREEN_HARDWARE"></span><span id="console_fullscreen_hardware"></span>
<strong>CONSOLE_FULLSCREEN_HARDWARE</strong> 2</span><span class="sxs-lookup"><span data-stu-id="1dab6-117"><span id="CONSOLE_FULLSCREEN_HARDWARE"></span><span id="console_fullscreen_hardware"></span>
<strong>CONSOLE_FULLSCREEN_HARDWARE</strong> 2</span></span></td>
<td><p><span data-ttu-id="1dab6-118">Consola de pantalla completa que se comunica directamente con el hardware de vídeo.</span><span class="sxs-lookup"><span data-stu-id="1dab6-118">Full-screen console communicating directly with the video hardware.</span></span> <span data-ttu-id="1dab6-119">Este modo se establece después de que la consola esté en modo de <strong>CONSOLE_FULLSCREEN</strong> para indicar que se ha completado la transición al modo de pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="1dab6-119">This mode is set after the console is in <strong>CONSOLE_FULLSCREEN</strong> mode to indicate that the transition to full-screen mode has completed.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="1dab6-120">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1dab6-120">Return value</span></span>
------------

<span data-ttu-id="1dab6-121">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="1dab6-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="1dab6-122">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="1dab6-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="1dab6-123">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="1dab6-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="1dab6-124">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1dab6-124">Remarks</span></span>
-------

<span data-ttu-id="1dab6-125">Para compilar una aplicación que usa esta función, defina \*\* \_ Win32 \_ WinNT\*\* como 0x0500 o posterior.</span><span class="sxs-lookup"><span data-stu-id="1dab6-125">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="1dab6-126">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="1dab6-126">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="1dab6-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1dab6-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="1dab6-128">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="1dab6-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="1dab6-129">Windows XP [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="1dab6-129">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1dab6-130">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="1dab6-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="1dab6-131">Windows Server 2003 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="1dab6-131">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1dab6-132">Encabezado</span><span class="sxs-lookup"><span data-stu-id="1dab6-132">Header</span></span></p></td>
<td><span data-ttu-id="1dab6-133">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1dab6-133">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1dab6-134">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="1dab6-134">Library</span></span></p></td>
<td><span data-ttu-id="1dab6-135">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="1dab6-135">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1dab6-136">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="1dab6-136">DLL</span></span></p></td>
<td><span data-ttu-id="1dab6-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1dab6-137">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="1dab6-138"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="1dab6-138"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="1dab6-139">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="1dab6-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1dab6-140">Modos de consola</span><span class="sxs-lookup"><span data-stu-id="1dab6-140">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="1dab6-141">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="1dab6-141">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)

 

 




