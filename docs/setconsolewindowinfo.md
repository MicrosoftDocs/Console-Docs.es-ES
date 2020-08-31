---
title: SetConsoleWindowInfo función)
description: Establece el tamaño y la posición actuales de la ventana de un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleWindowInfo
- wincon/SetConsoleWindowInfo
- SetConsoleWindowInfo
MS-HAID:
- '\_win32\_setconsolewindowinfo'
- base.setconsolewindowinfo
- consoles.setconsolewindowinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad16a8fe-ca91-41d6-93b1-8cce6d54b1da
topic_type:
- apiref
api_name:
- SetConsoleWindowInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: ae09434a1fc67902d2160f4e66890f4392eac3f8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060816"
---
# <a name="setconsolewindowinfo-function"></a><span data-ttu-id="2ff1e-104">SetConsoleWindowInfo función)</span><span class="sxs-lookup"><span data-stu-id="2ff1e-104">SetConsoleWindowInfo function</span></span>


<span data-ttu-id="2ff1e-105">Establece el tamaño y la posición actuales de la ventana de un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="2ff1e-105">Sets the current size and position of a console screen buffer's window.</span></span>

<a name="syntax"></a><span data-ttu-id="2ff1e-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2ff1e-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleWindowInfo(
  _In_       HANDLE     hConsoleOutput,
  _In_       BOOL       bAbsolute,
  _In_ const SMALL_RECT *lpConsoleWindow
);
```

<a name="parameters"></a><span data-ttu-id="2ff1e-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="2ff1e-107">Parameters</span></span>
----------

<span data-ttu-id="2ff1e-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="2ff1e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="2ff1e-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="2ff1e-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="2ff1e-110">El identificador debe tener el derecho de acceso de \*\* \_ lectura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="2ff1e-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="2ff1e-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="2ff1e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="2ff1e-112">*bAbsolute* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="2ff1e-112">*bAbsolute* \[in\]</span></span>  
<span data-ttu-id="2ff1e-113">Si este parámetro es **true**, las coordenadas especifican las nuevas esquinas superior izquierda e inferior derecha de la ventana.</span><span class="sxs-lookup"><span data-stu-id="2ff1e-113">If this parameter is **TRUE**, the coordinates specify the new upper-left and lower-right corners of the window.</span></span> <span data-ttu-id="2ff1e-114">Si es **false**, las coordenadas son relativas a las coordenadas de la esquina de la ventana actual.</span><span class="sxs-lookup"><span data-stu-id="2ff1e-114">If it is **FALSE**, the coordinates are relative to the current window-corner coordinates.</span></span>

<span data-ttu-id="2ff1e-115">*lpConsoleWindow* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="2ff1e-115">*lpConsoleWindow* \[in\]</span></span>  
<span data-ttu-id="2ff1e-116">Puntero a una [**pequeña estructura \_ Rect**](small-rect-str.md) que especifica las nuevas esquinas superior izquierda e inferior derecha de la ventana.</span><span class="sxs-lookup"><span data-stu-id="2ff1e-116">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure that specifies the new upper-left and lower-right corners of the window.</span></span>

<a name="return-value"></a><span data-ttu-id="2ff1e-117">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="2ff1e-117">Return value</span></span>
------------

<span data-ttu-id="2ff1e-118">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="2ff1e-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="2ff1e-119">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="2ff1e-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="2ff1e-120">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="2ff1e-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="2ff1e-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="2ff1e-121">Remarks</span></span>
-------

<span data-ttu-id="2ff1e-122">Se produce un error en la función si el rectángulo de la ventana especificado se extiende más allá de los límites del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="2ff1e-122">The function fails if the specified window rectangle extends beyond the boundaries of the console screen buffer.</span></span> <span data-ttu-id="2ff1e-123">Esto significa que los miembros **superior** e **izquierdo** del rectángulo *lpConsoleWindow* (o las coordenadas superior e izquierda calculadas, si *bAbsolute* es false) no pueden ser menores que cero.</span><span class="sxs-lookup"><span data-stu-id="2ff1e-123">This means that the **Top** and **Left** members of the *lpConsoleWindow* rectangle (or the calculated top and left coordinates, if *bAbsolute* is FALSE) cannot be less than zero.</span></span> <span data-ttu-id="2ff1e-124">Del mismo modo, los miembros **inferior** y **derecho** (o las coordenadas inferior y derecha calculadas) no pueden ser mayores que (alto del búfer de pantalla – 1) y (ancho del búfer de pantalla – 1), respectivamente.</span><span class="sxs-lookup"><span data-stu-id="2ff1e-124">Similarly, the **Bottom** and **Right** members (or the calculated bottom and right coordinates) cannot be greater than (screen buffer height – 1) and (screen buffer width – 1), respectively.</span></span> <span data-ttu-id="2ff1e-125">También se produce un error en la función si el miembro **derecho** (o la coordenada derecha calculada) es menor o igual que el miembro **izquierdo** (o la coordenada izquierda calculada) o si el miembro **inferior** (o la coordenada inferior calculada) es menor o igual que el miembro **superior** (o la coordenada superior calculada).</span><span class="sxs-lookup"><span data-stu-id="2ff1e-125">The function also fails if the **Right** member (or calculated right coordinate) is less than or equal to the **Left** member (or calculated left coordinate) or if the **Bottom** member (or calculated bottom coordinate) is less than or equal to the **Top** member (or calculated top coordinate).</span></span>

<span data-ttu-id="2ff1e-126">En el caso de las consolas de más de un búfer de pantalla, el cambio de la ubicación de la ventana para un búfer de pantalla no afecta a las ubicaciones de ventana de los otros búferes de pantalla.</span><span class="sxs-lookup"><span data-stu-id="2ff1e-126">For consoles with more than one screen buffer, changing the window location for one screen buffer does not affect the window locations of the other screen buffers.</span></span>

<span data-ttu-id="2ff1e-127">Para determinar el tamaño y la posición actuales de la ventana de un búfer de pantalla, utilice la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="2ff1e-127">To determine the current size and position of a screen buffer's window, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span> <span data-ttu-id="2ff1e-128">Esta función también devuelve el tamaño máximo de la ventana, dado el tamaño actual del búfer de pantalla, el tamaño de fuente actual y el tamaño de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="2ff1e-128">This function also returns the maximum size of the window, given the current screen buffer size, the current font size, and the screen size.</span></span> <span data-ttu-id="2ff1e-129">La función [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) devuelve el tamaño máximo de la ventana a partir de la fuente actual y los tamaños de pantalla, pero no tiene en cuenta el tamaño del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="2ff1e-129">The [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) function returns the maximum window size given the current font and screen sizes, but it does not consider the size of the console screen buffer.</span></span>

<span data-ttu-id="2ff1e-130">**SetConsoleWindowInfo** se puede usar para desplazarse por el contenido del búfer de pantalla de la consola desplazando la posición del rectángulo de la ventana sin cambiar su tamaño.</span><span class="sxs-lookup"><span data-stu-id="2ff1e-130">**SetConsoleWindowInfo** can be used to scroll the contents of the console screen buffer by shifting the position of the window rectangle without changing its size.</span></span>

<a name="examples"></a><span data-ttu-id="2ff1e-131">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="2ff1e-131">Examples</span></span>
--------

<span data-ttu-id="2ff1e-132">Para obtener un ejemplo, vea [desplazarse por la ventana de un búfer de pantalla](scrolling-a-screen-buffer-s-window.md).</span><span class="sxs-lookup"><span data-stu-id="2ff1e-132">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

<a name="requirements"></a><span data-ttu-id="2ff1e-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ff1e-133">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="2ff1e-134">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="2ff1e-134">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="2ff1e-135">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="2ff1e-135">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2ff1e-136">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="2ff1e-136">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="2ff1e-137">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="2ff1e-137">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2ff1e-138">Encabezado</span><span class="sxs-lookup"><span data-stu-id="2ff1e-138">Header</span></span></p></td>
<td><span data-ttu-id="2ff1e-139">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2ff1e-139">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2ff1e-140">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="2ff1e-140">Library</span></span></p></td>
<td><span data-ttu-id="2ff1e-141">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="2ff1e-141">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2ff1e-142">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="2ff1e-142">DLL</span></span></p></td>
<td><span data-ttu-id="2ff1e-143">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2ff1e-143">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="2ff1e-144"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="2ff1e-144"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="2ff1e-145">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="2ff1e-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2ff1e-146">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="2ff1e-146">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="2ff1e-147">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="2ff1e-147">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="2ff1e-148">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="2ff1e-148">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="2ff1e-149">Desplazarse por el búfer de pantalla</span><span class="sxs-lookup"><span data-stu-id="2ff1e-149">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

[<span data-ttu-id="2ff1e-150">**PEQUEÑO \_ rectángulo**</span><span class="sxs-lookup"><span data-stu-id="2ff1e-150">**SMALL\_RECT**</span></span>](small-rect-str.md)

 

 




