---
title: Estructura de CONSOLE_SCREEN_BUFFER_INFO
description: Vea información de referencia sobre la estructura de CONSOLE_SCREEN_BUFFER_INFO, que contiene información sobre un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFO
- wincon/CONSOLE_SCREEN_BUFFER_INFO
- CONSOLE_SCREEN_BUFFER_INFO
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFO
- wincon/PCONSOLE_SCREEN_BUFFER_INFO
- PCONSOLE_SCREEN_BUFFER_INFO
MS-HAID:
- '\_win32\_console\_screen\_buffer\_info\_str'
- base.console\_screen\_buffer\_info\_str
- consoles.console\_screen\_buffer\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 586b3e0f-2f6b-4a03-b8e4-602a892be56d
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 31ef1cf8e78029be48d5217cbc82f84663d627b5
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358125"
---
# <a name="console_screen_buffer_info-structure"></a><span data-ttu-id="e62a8-104">\_Estructura de \_ información de búfer de pantalla de la consola \_</span><span class="sxs-lookup"><span data-stu-id="e62a8-104">CONSOLE\_SCREEN\_BUFFER\_INFO structure</span></span>

<span data-ttu-id="e62a8-105">Contiene información sobre un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="e62a8-105">Contains information about a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="e62a8-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e62a8-106">Syntax</span></span>

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFO {
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
} CONSOLE_SCREEN_BUFFER_INFO;
```

## <a name="members"></a><span data-ttu-id="e62a8-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="e62a8-107">Members</span></span>

<span data-ttu-id="e62a8-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="e62a8-108">**dwSize**</span></span>  
<span data-ttu-id="e62a8-109">Una estructura de [**coordenadas**](coord-str.md) que contiene el tamaño del búfer de pantalla de la consola, en columnas y filas de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e62a8-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="e62a8-110">**dwCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="e62a8-110">**dwCursorPosition**</span></span>  
<span data-ttu-id="e62a8-111">Una estructura de [**coordenadas**](coord-str.md) que contiene las coordenadas de columna y fila del cursor en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="e62a8-111">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="e62a8-112">**wAttributes**</span><span class="sxs-lookup"><span data-stu-id="e62a8-112">**wAttributes**</span></span>  
<span data-ttu-id="e62a8-113">Los atributos de los caracteres escritos en un búfer de pantalla por las funciones [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) y [**WriteConsole**](writeconsole.md) , o bien se repiten en un búfer de pantalla mediante las funciones [**readfile**](/windows/win32/api/fileapi/nf-fileapi-readfile) y [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="e62a8-113">The attributes of the characters written to a screen buffer by the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="e62a8-114">Para obtener más información, vea [atributos de caracteres](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="e62a8-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="e62a8-115">**srWindow**</span><span class="sxs-lookup"><span data-stu-id="e62a8-115">**srWindow**</span></span>  
<span data-ttu-id="e62a8-116">[**Pequeña estructura \_ Rect**](small-rect-str.md) que contiene las coordenadas del búfer de pantalla de la consola de las esquinas superior izquierda e inferior derecha de la ventana de presentación.</span><span class="sxs-lookup"><span data-stu-id="e62a8-116">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="e62a8-117">**dwMaximumWindowSize**</span><span class="sxs-lookup"><span data-stu-id="e62a8-117">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="e62a8-118">Una estructura de [**coordenadas**](coord-str.md) que contiene el tamaño máximo de la ventana de la consola, en columnas y filas de caracteres, según el tamaño del búfer de pantalla actual y la fuente y el tamaño de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="e62a8-118">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

## <a name="examples"></a><span data-ttu-id="e62a8-119">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="e62a8-119">Examples</span></span>

<span data-ttu-id="e62a8-120">Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="e62a8-120">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="e62a8-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e62a8-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e62a8-122">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="e62a8-122">Minimum supported client</span></span> | <span data-ttu-id="e62a8-123">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="e62a8-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="e62a8-124">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="e62a8-124">Minimum supported server</span></span> | <span data-ttu-id="e62a8-125">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="e62a8-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="e62a8-126">Encabezado</span><span class="sxs-lookup"><span data-stu-id="e62a8-126">Header</span></span> | <span data-ttu-id="e62a8-127">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e62a8-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="e62a8-128">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e62a8-128">See also</span></span>

[<span data-ttu-id="e62a8-129">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="e62a8-129">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="e62a8-130">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="e62a8-130">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="e62a8-131">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="e62a8-131">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="e62a8-132">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="e62a8-132">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="e62a8-133">**PEQUEÑO \_ rectángulo**</span><span class="sxs-lookup"><span data-stu-id="e62a8-133">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="e62a8-134">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="e62a8-134">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="e62a8-135">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="e62a8-135">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)