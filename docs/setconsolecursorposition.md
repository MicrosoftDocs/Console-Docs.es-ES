---
title: SetConsoleCursorPosition función)
description: Vea la información de referencia sobre la función SetConsoleCursorPosition, que establece la posición del cursor en el búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleCursorPosition
- wincon/SetConsoleCursorPosition
- SetConsoleCursorPosition
MS-HAID:
- '\_win32\_setconsolecursorposition'
- base.setconsolecursorposition
- consoles.setconsolecursorposition
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8e9abada-a64e-429f-8286-ced1169c7104
topic_type:
- apiref
api_name:
- SetConsoleCursorPosition
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c93fbf4b619b522a95af2b03a49d60ff6f880e7d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039373"
---
# <a name="setconsolecursorposition-function"></a><span data-ttu-id="4eac3-104">SetConsoleCursorPosition función)</span><span class="sxs-lookup"><span data-stu-id="4eac3-104">SetConsoleCursorPosition function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="4eac3-105">Establece la posición del cursor en el búfer de pantalla especificado.</span><span class="sxs-lookup"><span data-stu-id="4eac3-105">Sets the cursor position in the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="4eac3-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4eac3-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

## <a name="parameters"></a><span data-ttu-id="4eac3-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4eac3-107">Parameters</span></span>

<span data-ttu-id="4eac3-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="4eac3-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="4eac3-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="4eac3-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="4eac3-110">El identificador debe tener el derecho de acceso de **\_ lectura genérico** .</span><span class="sxs-lookup"><span data-stu-id="4eac3-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="4eac3-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="4eac3-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="4eac3-112">*dwCursorPosition* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="4eac3-112">*dwCursorPosition* \[in\]</span></span>  
<span data-ttu-id="4eac3-113">Estructura de [**coordenadas**](coord-str.md) que especifica la nueva posición del cursor, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="4eac3-113">A [**COORD**](coord-str.md) structure that specifies the new cursor position, in characters.</span></span> <span data-ttu-id="4eac3-114">Las coordenadas son la columna y la fila de una celda de carácter de búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="4eac3-114">The coordinates are the column and row of a screen buffer character cell.</span></span> <span data-ttu-id="4eac3-115">Las coordenadas deben estar dentro de los límites del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="4eac3-115">The coordinates must be within the boundaries of the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="4eac3-116">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4eac3-116">Return value</span></span>

<span data-ttu-id="4eac3-117">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="4eac3-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4eac3-118">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="4eac3-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4eac3-119">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4eac3-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="4eac3-120">Comentarios</span><span class="sxs-lookup"><span data-stu-id="4eac3-120">Remarks</span></span>

<span data-ttu-id="4eac3-121">La posición del cursor determina dónde se muestran los caracteres escritos por la función [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md) , o que se han devuelto por la función [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="4eac3-121">The cursor position determines where characters written by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function, are displayed.</span></span> <span data-ttu-id="4eac3-122">Para determinar la posición actual del cursor, utilice la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="4eac3-122">To determine the current position of the cursor, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="4eac3-123">Si la nueva posición del cursor no está dentro de los límites de la ventana del búfer de pantalla de la consola, el origen de la ventana cambia para hacer que el cursor esté visible.</span><span class="sxs-lookup"><span data-stu-id="4eac3-123">If the new cursor position is not within the boundaries of the console screen buffer's window, the window origin changes to make the cursor visible.</span></span>

> [!TIP]
> <span data-ttu-id="4eac3-124">Esta API tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente en las secciones **[posición de cursor simple](console-virtual-terminal-sequences.md#simple-cursor-positioning)** y **[posición del cursor](console-virtual-terminal-sequences.md#cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="4eac3-124">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[simple cursor positioning](console-virtual-terminal-sequences.md#simple-cursor-positioning)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sections.</span></span> <span data-ttu-id="4eac3-125">El uso de las secuencias de control de línea, retorno de carro, retroceso y tabulación también puede ayudar con la posición del cursor.</span><span class="sxs-lookup"><span data-stu-id="4eac3-125">Use of the newline, carriage return, backspace, and tab control sequences can also assist with cursor positioning.</span></span>

## <a name="examples"></a><span data-ttu-id="4eac3-126">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="4eac3-126">Examples</span></span>

<span data-ttu-id="4eac3-127">Para obtener un ejemplo, consulte [uso de las funciones de entrada y salida de High-Level](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4eac3-127">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="4eac3-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4eac3-128">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4eac3-129">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="4eac3-129">Minimum supported client</span></span> | <span data-ttu-id="4eac3-130">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="4eac3-130">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="4eac3-131">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="4eac3-131">Minimum supported server</span></span> | <span data-ttu-id="4eac3-132">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="4eac3-132">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="4eac3-133">Encabezado</span><span class="sxs-lookup"><span data-stu-id="4eac3-133">Header</span></span> | <span data-ttu-id="4eac3-134">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4eac3-134">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="4eac3-135">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="4eac3-135">Library</span></span> | <span data-ttu-id="4eac3-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4eac3-136">Kernel32.lib</span></span> |
| <span data-ttu-id="4eac3-137">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="4eac3-137">DLL</span></span> | <span data-ttu-id="4eac3-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4eac3-138">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="4eac3-139">Consulte también</span><span class="sxs-lookup"><span data-stu-id="4eac3-139">See also</span></span>

[<span data-ttu-id="4eac3-140">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="4eac3-140">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4eac3-141">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="4eac3-141">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="4eac3-142">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="4eac3-142">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="4eac3-143">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="4eac3-143">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="4eac3-144">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="4eac3-144">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="4eac3-145">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="4eac3-145">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="4eac3-146">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="4eac3-146">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

[<span data-ttu-id="4eac3-147">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="4eac3-147">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="4eac3-148">**Escritura**</span><span class="sxs-lookup"><span data-stu-id="4eac3-148">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
