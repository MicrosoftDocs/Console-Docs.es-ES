---
title: GetLargestConsoleWindowSize función)
description: Recupera el tamaño de la ventana de la consola más grande posible, en función de la fuente actual y el tamaño de la pantalla.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/GetLargestConsoleWindowSize
- wincon/GetLargestConsoleWindowSize
- GetLargestConsoleWindowSize
MS-HAID:
- '\_win32\_getlargestconsolewindowsize'
- base.getlargestconsolewindowsize
- consoles.getlargestconsolewindowsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3e5897f3-4987-4a82-ab19-06c0b231ba67
topic_type:
- apiref
api_name:
- GetLargestConsoleWindowSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 086c09b00ba15ad3e1922655fbd9b5f39d872d41
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060649"
---
# <a name="getlargestconsolewindowsize-function"></a><span data-ttu-id="1a439-104">GetLargestConsoleWindowSize función)</span><span class="sxs-lookup"><span data-stu-id="1a439-104">GetLargestConsoleWindowSize function</span></span>


<span data-ttu-id="1a439-105">Recupera el tamaño de la ventana de la consola más grande posible, en función de la fuente actual y el tamaño de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="1a439-105">Retrieves the size of the largest possible console window, based on the current font and the size of the display.</span></span>

<a name="syntax"></a><span data-ttu-id="1a439-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1a439-106">Syntax</span></span>
------

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

<a name="parameters"></a><span data-ttu-id="1a439-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1a439-107">Parameters</span></span>
----------

<span data-ttu-id="1a439-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="1a439-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="1a439-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="1a439-109">A handle to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="1a439-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1a439-110">Return value</span></span>
------------

<span data-ttu-id="1a439-111">Si la función se ejecuta correctamente, el valor devuelto es una estructura de [**coordenadas**](coord-str.md) que especifica el número de columnas de celda de caracteres (miembro**X** ) y las filas (miembro**y** ) de la ventana de la consola más grande posible.</span><span class="sxs-lookup"><span data-stu-id="1a439-111">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that specifies the number of character cell columns (**X** member) and rows (**Y** member) in the largest possible console window.</span></span> <span data-ttu-id="1a439-112">De lo contrario, los miembros de la estructura son cero.</span><span class="sxs-lookup"><span data-stu-id="1a439-112">Otherwise, the members of the structure are zero.</span></span>

<span data-ttu-id="1a439-113">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="1a439-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="1a439-114">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1a439-114">Remarks</span></span>
-------

<span data-ttu-id="1a439-115">La función no tiene en cuenta el tamaño del búfer de pantalla de la consola, lo que significa que el tamaño de la ventana devuelto puede ser mayor que el tamaño del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="1a439-115">The function does not take into consideration the size of the console screen buffer, which means that the window size returned may be larger than the size of the console screen buffer.</span></span> <span data-ttu-id="1a439-116">La función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) se puede usar para determinar el tamaño máximo de la ventana de la consola, según el tamaño actual del búfer de pantalla, la fuente actual y el tamaño de presentación.</span><span class="sxs-lookup"><span data-stu-id="1a439-116">The [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function can be used to determine the maximum size of the console window, given the current screen buffer size, the current font, and the display size.</span></span>

<a name="requirements"></a><span data-ttu-id="1a439-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1a439-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="1a439-118">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="1a439-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="1a439-119">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="1a439-119">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1a439-120">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="1a439-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="1a439-121">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="1a439-121">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1a439-122">Encabezado</span><span class="sxs-lookup"><span data-stu-id="1a439-122">Header</span></span></p></td>
<td><span data-ttu-id="1a439-123">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1a439-123">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1a439-124">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="1a439-124">Library</span></span></p></td>
<td><span data-ttu-id="1a439-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="1a439-125">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1a439-126">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="1a439-126">DLL</span></span></p></td>
<td><span data-ttu-id="1a439-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1a439-127">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="1a439-128"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="1a439-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="1a439-129">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="1a439-129">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1a439-130">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="1a439-130">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="1a439-131">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="1a439-131">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="1a439-132">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="1a439-132">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="1a439-133">Tamaño de búfer de ventana y pantalla</span><span class="sxs-lookup"><span data-stu-id="1a439-133">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)

 

 




