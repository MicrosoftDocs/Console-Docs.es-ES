---
title: Estructura de CONSOLE_SCREEN_BUFFER_INFOEX
description: Vea información de referencia sobre la estructura de CONSOLE_SCREEN_BUFFER_INFOEX, que contiene información extendida sobre un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFOEX
- wincon/CONSOLE_SCREEN_BUFFER_INFOEX
- CONSOLE_SCREEN_BUFFER_INFOEX
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFOEX
- wincon/PCONSOLE_SCREEN_BUFFER_INFOEX
- PCONSOLE_SCREEN_BUFFER_INFOEX
MS-HAID:
- base.console\_screen\_buffer\_infoex
- consoles.console\_screen\_buffer\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6ed40df3-063d-41c9-8637-510c95104603
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFOEX
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 010120f2d925727e37bd72905bab4536db073371
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060829"
---
# <a name="console_screen_buffer_infoex-structure"></a><span data-ttu-id="19621-104">\_ \_ Estructura INFOEX del búfer de pantalla de la consola \_</span><span class="sxs-lookup"><span data-stu-id="19621-104">CONSOLE\_SCREEN\_BUFFER\_INFOEX structure</span></span>


<span data-ttu-id="19621-105">Contiene información extendida sobre un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="19621-105">Contains extended information about a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="19621-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="19621-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

<a name="members"></a><span data-ttu-id="19621-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="19621-107">Members</span></span>
-------

<span data-ttu-id="19621-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="19621-108">**cbSize**</span></span>  
<span data-ttu-id="19621-109">Tamaño de esta estructura, en bytes.</span><span class="sxs-lookup"><span data-stu-id="19621-109">The size of this structure, in bytes.</span></span>

<span data-ttu-id="19621-110">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="19621-110">**dwSize**</span></span>  
<span data-ttu-id="19621-111">Una estructura de [**coordenadas**](coord-str.md) que contiene el tamaño del búfer de pantalla de la consola, en columnas y filas de caracteres.</span><span class="sxs-lookup"><span data-stu-id="19621-111">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="19621-112">**dwCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="19621-112">**dwCursorPosition**</span></span>  
<span data-ttu-id="19621-113">Una estructura de [**coordenadas**](coord-str.md) que contiene las coordenadas de columna y fila del cursor en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="19621-113">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="19621-114">**wAttributes**</span><span class="sxs-lookup"><span data-stu-id="19621-114">**wAttributes**</span></span>  
<span data-ttu-id="19621-115">Los atributos de los caracteres escritos en un búfer de pantalla por las funciones [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) y [**WriteConsole**](writeconsole.md) , o bien se repiten en un búfer de pantalla mediante las funciones [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="19621-115">The attributes of the characters written to a screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="19621-116">Para obtener más información, vea [atributos de caracteres](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="19621-116">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="19621-117">**srWindow**</span><span class="sxs-lookup"><span data-stu-id="19621-117">**srWindow**</span></span>  
<span data-ttu-id="19621-118">[**Pequeña estructura \_ Rect**](small-rect-str.md) que contiene las coordenadas del búfer de pantalla de la consola de las esquinas superior izquierda e inferior derecha de la ventana de presentación.</span><span class="sxs-lookup"><span data-stu-id="19621-118">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="19621-119">**dwMaximumWindowSize**</span><span class="sxs-lookup"><span data-stu-id="19621-119">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="19621-120">Una estructura de [**coordenadas**](coord-str.md) que contiene el tamaño máximo de la ventana de la consola, en columnas y filas de caracteres, según el tamaño del búfer de pantalla actual y la fuente y el tamaño de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="19621-120">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

<span data-ttu-id="19621-121">**wPopupAttributes**</span><span class="sxs-lookup"><span data-stu-id="19621-121">**wPopupAttributes**</span></span>  
<span data-ttu-id="19621-122">El atributo Fill para los elementos emergentes de la consola.</span><span class="sxs-lookup"><span data-stu-id="19621-122">The fill attribute for console pop-ups.</span></span>

<span data-ttu-id="19621-123">**bFullscreenSupported**</span><span class="sxs-lookup"><span data-stu-id="19621-123">**bFullscreenSupported**</span></span>  
<span data-ttu-id="19621-124">Si este miembro es TRUE, se admite el modo de pantalla completa; de lo contrario, no es.</span><span class="sxs-lookup"><span data-stu-id="19621-124">If this member is TRUE, full-screen mode is supported; otherwise, it is not.</span></span>

<span data-ttu-id="19621-125">**ColorTable**</span><span class="sxs-lookup"><span data-stu-id="19621-125">**ColorTable**</span></span>  
<span data-ttu-id="19621-126">Una matriz de valores [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) que describen la configuración de color de la consola.</span><span class="sxs-lookup"><span data-stu-id="19621-126">An array of [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) values that describe the console's color settings.</span></span>

<a name="requirements"></a><span data-ttu-id="19621-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="19621-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="19621-128">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="19621-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="19621-129">Windows Vista [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="19621-129">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="19621-130">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="19621-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="19621-131">Windows Server 2008 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="19621-131">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="19621-132">Encabezado</span><span class="sxs-lookup"><span data-stu-id="19621-132">Header</span></span></p></td>
<td><span data-ttu-id="19621-133">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="19621-133">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="19621-134"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="19621-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="19621-135">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="19621-135">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="19621-136">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="19621-136">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)

[<span data-ttu-id="19621-137">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="19621-137">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)

[<span data-ttu-id="19621-138">**PEQUEÑO \_ rectángulo**</span><span class="sxs-lookup"><span data-stu-id="19621-138">**SMALL\_RECT**</span></span>](small-rect-str.md)

 

 




