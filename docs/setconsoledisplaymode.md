---
title: SetConsoleDisplayMode función)
description: Vea la información de referencia sobre la función SetConsoleDisplayMode, que establece el modo de presentación del búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- base.setconsoledisplaymode
- consoles.setconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744
topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0d4564b9a7562fb495c9834df98708d5faff5334
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060857"
---
# <a name="setconsoledisplaymode-function"></a><span data-ttu-id="da165-104">SetConsoleDisplayMode función)</span><span class="sxs-lookup"><span data-stu-id="da165-104">SetConsoleDisplayMode function</span></span>


<span data-ttu-id="da165-105">Establece el modo de presentación del búfer de pantalla de la consola especificado.</span><span class="sxs-lookup"><span data-stu-id="da165-105">Sets the display mode of the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="da165-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="da165-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

<a name="parameters"></a><span data-ttu-id="da165-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="da165-107">Parameters</span></span>
----------

<span data-ttu-id="da165-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="da165-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="da165-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="da165-109">A handle to the console screen buffer.</span></span>

<span data-ttu-id="da165-110">*dwFlags* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="da165-110">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="da165-111">Modo de presentación de la consola.</span><span class="sxs-lookup"><span data-stu-id="da165-111">The display mode of the console.</span></span> <span data-ttu-id="da165-112">Este parámetro puede ser uno o varios de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="da165-112">This parameter can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="da165-113">Valor</span><span class="sxs-lookup"><span data-stu-id="da165-113">Value</span></span></th>
<th><span data-ttu-id="da165-114">Significado</span><span class="sxs-lookup"><span data-stu-id="da165-114">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="da165-115"><span id="CONSOLE_FULLSCREEN_MODE"></span><span id="console_fullscreen_mode"></span>
<strong>CONSOLE_FULLSCREEN_MODE</strong> 1</span><span class="sxs-lookup"><span data-stu-id="da165-115"><span id="CONSOLE_FULLSCREEN_MODE"></span><span id="console_fullscreen_mode"></span>
<strong>CONSOLE_FULLSCREEN_MODE</strong> 1</span></span></td>
<td><p><span data-ttu-id="da165-116">El texto se muestra en el modo de pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="da165-116">Text is displayed in full-screen mode.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="da165-117"><span id="CONSOLE_WINDOWED_MODE"></span><span id="console_windowed_mode"></span>
<strong>CONSOLE_WINDOWED_MODE</strong> 2</span><span class="sxs-lookup"><span data-stu-id="da165-117"><span id="CONSOLE_WINDOWED_MODE"></span><span id="console_windowed_mode"></span>
<strong>CONSOLE_WINDOWED_MODE</strong> 2</span></span></td>
<td><p><span data-ttu-id="da165-118">El texto se muestra en una ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="da165-118">Text is displayed in a console window.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="da165-119">*lpNewScreenBufferDimensions* \[ out, opcional\]</span><span class="sxs-lookup"><span data-stu-id="da165-119">*lpNewScreenBufferDimensions* \[out, optional\]</span></span>  
<span data-ttu-id="da165-120">Puntero a una estructura de [**coordenadas**](coord-str.md) que recibe las nuevas dimensiones del búfer de pantalla, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="da165-120">A pointer to a [**COORD**](coord-str.md) structure that receives the new dimensions of the screen buffer, in characters.</span></span>

<a name="return-value"></a><span data-ttu-id="da165-121">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="da165-121">Return value</span></span>
------------

<span data-ttu-id="da165-122">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="da165-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="da165-123">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="da165-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="da165-124">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="da165-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="da165-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da165-125">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="da165-126">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="da165-126">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="da165-127">Windows XP [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="da165-127">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="da165-128">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="da165-128">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="da165-129">Windows Server 2003 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="da165-129">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="da165-130">Encabezado</span><span class="sxs-lookup"><span data-stu-id="da165-130">Header</span></span></p></td>
<td><span data-ttu-id="da165-131">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="da165-131">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="da165-132">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="da165-132">Library</span></span></p></td>
<td><span data-ttu-id="da165-133">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="da165-133">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="da165-134">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="da165-134">DLL</span></span></p></td>
<td><span data-ttu-id="da165-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="da165-135">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="da165-136"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="da165-136"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="da165-137">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="da165-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="da165-138">Modos de consola</span><span class="sxs-lookup"><span data-stu-id="da165-138">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="da165-139">**GetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="da165-139">**GetConsoleDisplayMode**</span></span>](getconsoledisplaymode.md)

 

 




