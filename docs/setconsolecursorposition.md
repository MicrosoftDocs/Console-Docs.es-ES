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
ms.openlocfilehash: 48671b9c54e61733c2936ac1f112e2d499f31a1a
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357675"
---
# <a name="setconsolecursorposition-function"></a><span data-ttu-id="8226e-104">SetConsoleCursorPosition función)</span><span class="sxs-lookup"><span data-stu-id="8226e-104">SetConsoleCursorPosition function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="8226e-105">Establece la posición del cursor en el búfer de pantalla especificado.</span><span class="sxs-lookup"><span data-stu-id="8226e-105">Sets the cursor position in the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="8226e-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8226e-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

## <a name="parameters"></a><span data-ttu-id="8226e-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="8226e-107">Parameters</span></span>

<span data-ttu-id="8226e-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="8226e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="8226e-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="8226e-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="8226e-110">El identificador debe tener derecho de acceso de **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="8226e-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="8226e-111">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="8226e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="8226e-112">*dwCursorPosition* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="8226e-112">*dwCursorPosition* \[in\]</span></span>  
<span data-ttu-id="8226e-113">Estructura de [**coordenadas**](coord-str.md) que especifica la nueva posición del cursor, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="8226e-113">A [**COORD**](coord-str.md) structure that specifies the new cursor position, in characters.</span></span> <span data-ttu-id="8226e-114">Las coordenadas son la columna y la fila de una celda de carácter de búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="8226e-114">The coordinates are the column and row of a screen buffer character cell.</span></span> <span data-ttu-id="8226e-115">Las coordenadas deben estar dentro de los límites del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="8226e-115">The coordinates must be within the boundaries of the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="8226e-116">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="8226e-116">Return value</span></span>

<span data-ttu-id="8226e-117">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="8226e-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="8226e-118">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="8226e-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="8226e-119">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="8226e-119">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="8226e-120">Comentarios</span><span class="sxs-lookup"><span data-stu-id="8226e-120">Remarks</span></span>

<span data-ttu-id="8226e-121">La posición del cursor determina dónde se muestran los caracteres escritos por la función [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) o [**WriteConsole**](writeconsole.md) , o que se han devuelto por la función [**readfile**](/windows/win32/api/fileapi/nf-fileapi-readfile) o [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="8226e-121">The cursor position determines where characters written by the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) or [**ReadConsole**](readconsole.md) function, are displayed.</span></span> <span data-ttu-id="8226e-122">Para determinar la posición actual del cursor, utilice la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="8226e-122">To determine the current position of the cursor, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="8226e-123">Si la nueva posición del cursor no está dentro de los límites de la ventana del búfer de pantalla de la consola, el origen de la ventana cambia para hacer que el cursor esté visible.</span><span class="sxs-lookup"><span data-stu-id="8226e-123">If the new cursor position is not within the boundaries of the console screen buffer's window, the window origin changes to make the cursor visible.</span></span>

> [!TIP]
> <span data-ttu-id="8226e-124">Esta API tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente en las secciones **[posición de cursor simple](console-virtual-terminal-sequences.md#simple-cursor-positioning)** y **[posición del cursor](console-virtual-terminal-sequences.md#cursor-positioning)** .</span><span class="sxs-lookup"><span data-stu-id="8226e-124">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[simple cursor positioning](console-virtual-terminal-sequences.md#simple-cursor-positioning)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sections.</span></span> <span data-ttu-id="8226e-125">El uso de las secuencias de control de línea, retorno de carro, retroceso y tabulación también puede ayudar con la posición del cursor.</span><span class="sxs-lookup"><span data-stu-id="8226e-125">Use of the newline, carriage return, backspace, and tab control sequences can also assist with cursor positioning.</span></span>

## <a name="examples"></a><span data-ttu-id="8226e-126">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="8226e-126">Examples</span></span>

<span data-ttu-id="8226e-127">Para obtener un ejemplo, consulte [uso de las funciones de entrada y salida de High-Level](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="8226e-127">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="8226e-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8226e-128">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="8226e-129">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="8226e-129">Minimum supported client</span></span> | <span data-ttu-id="8226e-130">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="8226e-130">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="8226e-131">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="8226e-131">Minimum supported server</span></span> | <span data-ttu-id="8226e-132">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="8226e-132">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="8226e-133">Encabezado</span><span class="sxs-lookup"><span data-stu-id="8226e-133">Header</span></span> | <span data-ttu-id="8226e-134">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="8226e-134">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="8226e-135">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="8226e-135">Library</span></span> | <span data-ttu-id="8226e-136">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="8226e-136">Kernel32.lib</span></span> |
| <span data-ttu-id="8226e-137">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="8226e-137">DLL</span></span> | <span data-ttu-id="8226e-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="8226e-138">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="8226e-139">Vea también</span><span class="sxs-lookup"><span data-stu-id="8226e-139">See also</span></span>

[<span data-ttu-id="8226e-140">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="8226e-140">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="8226e-141">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="8226e-141">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="8226e-142">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="8226e-142">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="8226e-143">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="8226e-143">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="8226e-144">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="8226e-144">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="8226e-145">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="8226e-145">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="8226e-146">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="8226e-146">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

[<span data-ttu-id="8226e-147">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="8226e-147">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="8226e-148">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="8226e-148">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)