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
ms.openlocfilehash: 8b3a739a9f66e25687b60a3450c9381822c16e53
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039183"
---
# <a name="console_screen_buffer_info-structure"></a><span data-ttu-id="fa741-104">\_Estructura de \_ información de búfer de pantalla de la consola \_</span><span class="sxs-lookup"><span data-stu-id="fa741-104">CONSOLE\_SCREEN\_BUFFER\_INFO structure</span></span>

<span data-ttu-id="fa741-105">Contiene información sobre un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="fa741-105">Contains information about a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="fa741-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fa741-106">Syntax</span></span>

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFO {
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
} CONSOLE_SCREEN_BUFFER_INFO;
```

## <a name="members"></a><span data-ttu-id="fa741-107">Miembros</span><span class="sxs-lookup"><span data-stu-id="fa741-107">Members</span></span>

<span data-ttu-id="fa741-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="fa741-108">**dwSize**</span></span>  
<span data-ttu-id="fa741-109">Una estructura de [**coordenadas**](coord-str.md) que contiene el tamaño del búfer de pantalla de la consola, en columnas y filas de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fa741-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="fa741-110">**dwCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="fa741-110">**dwCursorPosition**</span></span>  
<span data-ttu-id="fa741-111">Una estructura de [**coordenadas**](coord-str.md) que contiene las coordenadas de columna y fila del cursor en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="fa741-111">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="fa741-112">**wAttributes**</span><span class="sxs-lookup"><span data-stu-id="fa741-112">**wAttributes**</span></span>  
<span data-ttu-id="fa741-113">Los atributos de los caracteres escritos en un búfer de pantalla por las funciones [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) y [**WriteConsole**](writeconsole.md) , o bien se repiten en un búfer de pantalla mediante las funciones [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="fa741-113">The attributes of the characters written to a screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="fa741-114">Para obtener más información, vea [atributos de caracteres](console-screen-buffers.md#character-attributes).</span><span class="sxs-lookup"><span data-stu-id="fa741-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="fa741-115">**srWindow**</span><span class="sxs-lookup"><span data-stu-id="fa741-115">**srWindow**</span></span>  
<span data-ttu-id="fa741-116">[**Pequeña estructura \_ Rect**](small-rect-str.md) que contiene las coordenadas del búfer de pantalla de la consola de las esquinas superior izquierda e inferior derecha de la ventana de presentación.</span><span class="sxs-lookup"><span data-stu-id="fa741-116">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="fa741-117">**dwMaximumWindowSize**</span><span class="sxs-lookup"><span data-stu-id="fa741-117">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="fa741-118">Una estructura de [**coordenadas**](coord-str.md) que contiene el tamaño máximo de la ventana de la consola, en columnas y filas de caracteres, según el tamaño del búfer de pantalla actual y la fuente y el tamaño de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="fa741-118">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

## <a name="examples"></a><span data-ttu-id="fa741-119">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="fa741-119">Examples</span></span>

<span data-ttu-id="fa741-120">Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).</span><span class="sxs-lookup"><span data-stu-id="fa741-120">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="fa741-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fa741-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="fa741-122">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="fa741-122">Minimum supported client</span></span> | <span data-ttu-id="fa741-123">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="fa741-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="fa741-124">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="fa741-124">Minimum supported server</span></span> | <span data-ttu-id="fa741-125">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="fa741-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="fa741-126">Encabezado</span><span class="sxs-lookup"><span data-stu-id="fa741-126">Header</span></span> | <span data-ttu-id="fa741-127">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="fa741-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="fa741-128">Consulte también</span><span class="sxs-lookup"><span data-stu-id="fa741-128">See also</span></span>

[<span data-ttu-id="fa741-129">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="fa741-129">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="fa741-130">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="fa741-130">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="fa741-131">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="fa741-131">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="fa741-132">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="fa741-132">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="fa741-133">**PEQUEÑO \_ rectángulo**</span><span class="sxs-lookup"><span data-stu-id="fa741-133">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="fa741-134">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="fa741-134">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="fa741-135">**Escritura**</span><span class="sxs-lookup"><span data-stu-id="fa741-135">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
