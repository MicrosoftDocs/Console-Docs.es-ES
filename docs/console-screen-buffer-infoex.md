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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: baf6eeb51cbae5ce410c190852c22ae237e6a367
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038353"
---
# <a name="console_screen_buffer_infoex-structure"></a><span data-ttu-id="2aee6-104">\_ \_ Estructura INFOEX del búfer de pantalla de la consola \_</span><span class="sxs-lookup"><span data-stu-id="2aee6-104">CONSOLE\_SCREEN\_BUFFER\_INFOEX structure</span></span>

<span data-ttu-id="2aee6-105">Contiene información extendida sobre un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="2aee6-105">Contains extended information about a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="2aee6-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2aee6-106">Syntax</span></span>

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

## <a name="members"></a><span data-ttu-id="2aee6-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="2aee6-107">Members</span></span>

<span data-ttu-id="2aee6-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="2aee6-108">**cbSize**</span></span>  
<span data-ttu-id="2aee6-109">Tamaño de esta estructura, en bytes.</span><span class="sxs-lookup"><span data-stu-id="2aee6-109">The size of this structure, in bytes.</span></span>

<span data-ttu-id="2aee6-110">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="2aee6-110">**dwSize**</span></span>  
<span data-ttu-id="2aee6-111">Una estructura de [**coordenadas**](coord-str.md) que contiene el tamaño del búfer de pantalla de la consola, en columnas y filas de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2aee6-111">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="2aee6-112">**dwCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="2aee6-112">**dwCursorPosition**</span></span>  
<span data-ttu-id="2aee6-113">Una estructura de [**coordenadas**](coord-str.md) que contiene las coordenadas de columna y fila del cursor en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="2aee6-113">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="2aee6-114">**wAttributes**</span><span class="sxs-lookup"><span data-stu-id="2aee6-114">**wAttributes**</span></span>  
<span data-ttu-id="2aee6-115">Los atributos de los caracteres escritos en un búfer de pantalla por las funciones [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) y [**WriteConsole**](writeconsole.md) , o bien se repiten en un búfer de pantalla mediante las funciones [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="2aee6-115">The attributes of the characters written to a screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="2aee6-116">Para obtener más información, vea [atributos de caracteres](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="2aee6-116">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="2aee6-117">**srWindow**</span><span class="sxs-lookup"><span data-stu-id="2aee6-117">**srWindow**</span></span>  
<span data-ttu-id="2aee6-118">[**Pequeña estructura \_ Rect**](small-rect-str.md) que contiene las coordenadas del búfer de pantalla de la consola de las esquinas superior izquierda e inferior derecha de la ventana de presentación.</span><span class="sxs-lookup"><span data-stu-id="2aee6-118">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="2aee6-119">**dwMaximumWindowSize**</span><span class="sxs-lookup"><span data-stu-id="2aee6-119">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="2aee6-120">Una estructura de [**coordenadas**](coord-str.md) que contiene el tamaño máximo de la ventana de la consola, en columnas y filas de caracteres, según el tamaño del búfer de pantalla actual y la fuente y el tamaño de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="2aee6-120">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

<span data-ttu-id="2aee6-121">**wPopupAttributes**</span><span class="sxs-lookup"><span data-stu-id="2aee6-121">**wPopupAttributes**</span></span>  
<span data-ttu-id="2aee6-122">El atributo Fill para los elementos emergentes de la consola.</span><span class="sxs-lookup"><span data-stu-id="2aee6-122">The fill attribute for console pop-ups.</span></span>

<span data-ttu-id="2aee6-123">**bFullscreenSupported**</span><span class="sxs-lookup"><span data-stu-id="2aee6-123">**bFullscreenSupported**</span></span>  
<span data-ttu-id="2aee6-124">Si este miembro es `TRUE` , se admite el modo de pantalla completa; de lo contrario, no es.</span><span class="sxs-lookup"><span data-stu-id="2aee6-124">If this member is `TRUE`, full-screen mode is supported; otherwise, it is not.</span></span> <span data-ttu-id="2aee6-125">Siempre será `FALSE` para los sistemas posteriores a Windows Vista con el [modelo de controlador WDDM](https://docs.microsoft.com/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) , ya que el acceso de VGA directo real al monitor ya no está disponible.</span><span class="sxs-lookup"><span data-stu-id="2aee6-125">This will always be `FALSE` for systems after Windows Vista with the [WDDM driver model](https://docs.microsoft.com/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) as true direct VGA access to the monitor is no longer available.</span></span>

<span data-ttu-id="2aee6-126">**ColorTable**</span><span class="sxs-lookup"><span data-stu-id="2aee6-126">**ColorTable**</span></span>  
<span data-ttu-id="2aee6-127">Una matriz de valores [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) que describen la configuración de color de la consola.</span><span class="sxs-lookup"><span data-stu-id="2aee6-127">An array of [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) values that describe the console's color settings.</span></span>

## <a name="requirements"></a><span data-ttu-id="2aee6-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2aee6-128">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="2aee6-129">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="2aee6-129">Minimum supported client</span></span> | <span data-ttu-id="2aee6-130">Solo aplicaciones de escritorio de Windows Vista \[\]</span><span class="sxs-lookup"><span data-stu-id="2aee6-130">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="2aee6-131">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="2aee6-131">Minimum supported server</span></span> | <span data-ttu-id="2aee6-132">Solo aplicaciones de escritorio de Windows Server 2008 \[\]</span><span class="sxs-lookup"><span data-stu-id="2aee6-132">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="2aee6-133">Encabezado</span><span class="sxs-lookup"><span data-stu-id="2aee6-133">Header</span></span> | <span data-ttu-id="2aee6-134">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2aee6-134">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="2aee6-135">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2aee6-135">See also</span></span>

[<span data-ttu-id="2aee6-136">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="2aee6-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="2aee6-137">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="2aee6-137">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)

[<span data-ttu-id="2aee6-138">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="2aee6-138">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)

[<span data-ttu-id="2aee6-139">**PEQUEÑO \_ rectángulo**</span><span class="sxs-lookup"><span data-stu-id="2aee6-139">**SMALL\_RECT**</span></span>](small-rect-str.md)
