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
ms.openlocfilehash: eaa50df16248597f1054f0741113ecc9be1f3264
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060941"
---
# <a name="setconsolecursorposition-function"></a><span data-ttu-id="60d23-104">SetConsoleCursorPosition función)</span><span class="sxs-lookup"><span data-stu-id="60d23-104">SetConsoleCursorPosition function</span></span>


<span data-ttu-id="60d23-105">Establece la posición del cursor en el búfer de pantalla especificado.</span><span class="sxs-lookup"><span data-stu-id="60d23-105">Sets the cursor position in the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="60d23-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="60d23-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

<a name="parameters"></a><span data-ttu-id="60d23-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="60d23-107">Parameters</span></span>
----------

<span data-ttu-id="60d23-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="60d23-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="60d23-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="60d23-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="60d23-110">El identificador debe tener el derecho de acceso de \*\* \_ lectura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="60d23-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="60d23-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="60d23-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="60d23-112">*dwCursorPosition* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="60d23-112">*dwCursorPosition* \[in\]</span></span>  
<span data-ttu-id="60d23-113">Estructura de [**coordenadas**](coord-str.md) que especifica la nueva posición del cursor, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="60d23-113">A [**COORD**](coord-str.md) structure that specifies the new cursor position, in characters.</span></span> <span data-ttu-id="60d23-114">Las coordenadas son la columna y la fila de una celda de carácter de búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="60d23-114">The coordinates are the column and row of a screen buffer character cell.</span></span> <span data-ttu-id="60d23-115">Las coordenadas deben estar dentro de los límites del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="60d23-115">The coordinates must be within the boundaries of the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="60d23-116">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="60d23-116">Return value</span></span>
------------

<span data-ttu-id="60d23-117">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="60d23-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="60d23-118">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="60d23-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="60d23-119">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="60d23-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="60d23-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="60d23-120">Remarks</span></span>
-------

<span data-ttu-id="60d23-121">La posición del cursor determina dónde se muestran los caracteres escritos por la función [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md) , o que se han devuelto por la función [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="60d23-121">The cursor position determines where characters written by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function, are displayed.</span></span> <span data-ttu-id="60d23-122">Para determinar la posición actual del cursor, utilice la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="60d23-122">To determine the current position of the cursor, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="60d23-123">Si la nueva posición del cursor no está dentro de los límites de la ventana del búfer de pantalla de la consola, el origen de la ventana cambia para hacer que el cursor esté visible.</span><span class="sxs-lookup"><span data-stu-id="60d23-123">If the new cursor position is not within the boundaries of the console screen buffer's window, the window origin changes to make the cursor visible.</span></span>

<a name="examples"></a><span data-ttu-id="60d23-124">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="60d23-124">Examples</span></span>
--------

<span data-ttu-id="60d23-125">Para obtener un ejemplo, vea [usar las funciones de entrada y salida de alto nivel](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="60d23-125">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

<a name="requirements"></a><span data-ttu-id="60d23-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="60d23-126">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="60d23-127">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="60d23-127">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="60d23-128">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="60d23-128">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="60d23-129">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="60d23-129">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="60d23-130">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="60d23-130">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="60d23-131">Encabezado</span><span class="sxs-lookup"><span data-stu-id="60d23-131">Header</span></span></p></td>
<td><span data-ttu-id="60d23-132">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="60d23-132">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="60d23-133">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="60d23-133">Library</span></span></p></td>
<td><span data-ttu-id="60d23-134">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="60d23-134">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="60d23-135">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="60d23-135">DLL</span></span></p></td>
<td><span data-ttu-id="60d23-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="60d23-136">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="60d23-137"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="60d23-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="60d23-138">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="60d23-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="60d23-139">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="60d23-139">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="60d23-140">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="60d23-140">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="60d23-141">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="60d23-141">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="60d23-142">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="60d23-142">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="60d23-143">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="60d23-143">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="60d23-144">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="60d23-144">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

[<span data-ttu-id="60d23-145">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="60d23-145">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="60d23-146">**Escritura**</span><span class="sxs-lookup"><span data-stu-id="60d23-146">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




