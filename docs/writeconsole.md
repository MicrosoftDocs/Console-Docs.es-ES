---
title: WriteConsole función)
description: Escribe una cadena de caracteres en un búfer de pantalla de la consola a partir de la ubicación actual del cursor.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/WriteConsole
- wincon/WriteConsole
- WriteConsole
- consoleapi/WriteConsoleA
- wincon/WriteConsoleA
- WriteConsoleA
- consoleapi/WriteConsoleW
- wincon/WriteConsoleW
- WriteConsoleW
MS-HAID:
- '\_win32\_writeconsole'
- base.writeconsole
- consoles.writeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1a13d9ef-75a9-49fd-9717-207f18612b59
topic_type:
- apiref
api_name:
- WriteConsole
- WriteConsoleA
- WriteConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 426aa6711e46e0d5cda1eb1b7dab7b2b0b7156d6
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420294"
---
# <a name="writeconsole-function"></a><span data-ttu-id="1ea6e-104">WriteConsole función)</span><span class="sxs-lookup"><span data-stu-id="1ea6e-104">WriteConsole function</span></span>

<span data-ttu-id="1ea6e-105">Escribe una cadena de caracteres en un búfer de pantalla de la consola a partir de la ubicación actual del cursor.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-105">Writes a character string to a console screen buffer beginning at the current cursor location.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ea6e-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1ea6e-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## <a name="parameters"></a><span data-ttu-id="1ea6e-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1ea6e-107">Parameters</span></span>

<span data-ttu-id="1ea6e-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="1ea6e-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="1ea6e-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="1ea6e-110">El identificador debe tener el derecho de acceso de **\_ escritura genérico** .</span><span class="sxs-lookup"><span data-stu-id="1ea6e-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="1ea6e-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="1ea6e-112">*lpBuffer* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="1ea6e-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="1ea6e-113">Un puntero a un búfer que contiene los caracteres que se van a escribir en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-113">A pointer to a buffer that contains characters to be written to the console screen buffer.</span></span> <span data-ttu-id="1ea6e-114">Se espera que sea una matriz de `char` para `WriteConsoleA` o `wchar_t` para `WriteConsoleW` .</span><span class="sxs-lookup"><span data-stu-id="1ea6e-114">This is expected to be an array of either `char` for `WriteConsoleA` or `wchar_t` for `WriteConsoleW`.</span></span>

<span data-ttu-id="1ea6e-115">*nNumberOfCharsToWrite* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="1ea6e-115">*nNumberOfCharsToWrite* \[in\]</span></span>  
<span data-ttu-id="1ea6e-116">El número de caracteres que se va a escribir.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-116">The number of characters to be written.</span></span> <span data-ttu-id="1ea6e-117">Si el tamaño total del número de caracteres especificado supera el montón disponible, se produce un error en la función y **\_ no \_ hay suficiente \_ memoria**.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-117">If the total size of the specified number of characters exceeds the available heap, the function fails with **ERROR\_NOT\_ENOUGH\_MEMORY**.</span></span>

<span data-ttu-id="1ea6e-118">*lpNumberOfCharsWritten* \[ out, opcional\]</span><span class="sxs-lookup"><span data-stu-id="1ea6e-118">*lpNumberOfCharsWritten* \[out, optional\]</span></span>  
<span data-ttu-id="1ea6e-119">Puntero a una variable que recibe el número de caracteres escritos realmente.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-119">A pointer to a variable that receives the number of characters actually written.</span></span>

<span data-ttu-id="1ea6e-120">*lpReserved* Sector debe ser **null**.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-120">*lpReserved* Reserved; must be **NULL**.</span></span>

## <a name="return-value"></a><span data-ttu-id="1ea6e-121">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1ea6e-121">Return value</span></span>

<span data-ttu-id="1ea6e-122">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="1ea6e-123">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="1ea6e-124">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="1ea6e-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="1ea6e-125">Comentarios</span><span class="sxs-lookup"><span data-stu-id="1ea6e-125">Remarks</span></span>

<span data-ttu-id="1ea6e-126">La función **WriteConsole** escribe caracteres en el búfer de pantalla de la consola en la posición actual del cursor.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-126">The **WriteConsole** function writes characters to the console screen buffer at the current cursor position.</span></span> <span data-ttu-id="1ea6e-127">La posición del cursor avanza a medida que se escriben caracteres.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-127">The cursor position advances as characters are written.</span></span> <span data-ttu-id="1ea6e-128">La función [**SetConsoleCursorPosition**](setconsolecursorposition.md) establece la posición actual del cursor.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-128">The [**SetConsoleCursorPosition**](setconsolecursorposition.md) function sets the current cursor position.</span></span>

<span data-ttu-id="1ea6e-129">Los caracteres se escriben con los atributos de color de primer plano y de fondo asociados al búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-129">Characters are written using the foreground and background color attributes associated with the console screen buffer.</span></span> <span data-ttu-id="1ea6e-130">La función [**SetConsoleTextAttribute**](setconsoletextattribute.md) cambia estos colores.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-130">The [**SetConsoleTextAttribute**](setconsoletextattribute.md) function changes these colors.</span></span> <span data-ttu-id="1ea6e-131">Para determinar los atributos de color actuales y la posición actual del cursor, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span><span class="sxs-lookup"><span data-stu-id="1ea6e-131">To determine the current color attributes and the current cursor position, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span></span>

<span data-ttu-id="1ea6e-132">Todos los modos de entrada que afectan al comportamiento de la función [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) tienen el mismo efecto en **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-132">All of the input modes that affect the behavior of the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) function have the same effect on **WriteConsole**.</span></span> <span data-ttu-id="1ea6e-133">Para recuperar y establecer los modos de salida de un búfer de pantalla de la consola, use las funciones [**GetConsoleMode**](getconsolemode.md) y [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="1ea6e-133">To retrieve and set the output modes of a console screen buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

<span data-ttu-id="1ea6e-134">**WriteConsole** produce un error si se usa con un identificador estándar que se redirige a un archivo.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-134">**WriteConsole** fails if it is used with a standard handle that is redirected to a file.</span></span> <span data-ttu-id="1ea6e-135">Si una aplicación procesa una salida multilingüe que se puede redirigir, determine si el identificador de salida es un identificador de consola (un método es llamar a la función [**GetConsoleMode**](getconsolemode.md) y comprobar si se realiza correctamente).</span><span class="sxs-lookup"><span data-stu-id="1ea6e-135">If an application processes multilingual output that can be redirected, determine whether the output handle is a console handle (one method is to call the [**GetConsoleMode**](getconsolemode.md) function and check whether it succeeds).</span></span> <span data-ttu-id="1ea6e-136">Si el identificador es un identificador de consola, llame a **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-136">If the handle is a console handle, call **WriteConsole**.</span></span> <span data-ttu-id="1ea6e-137">Si el identificador no es un identificador de consola, se redirige el resultado y se debe llamar a [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) para realizar la e/s.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-137">If the handle is not a console handle, the output is redirected and you should call [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) to perform the I/O.</span></span> <span data-ttu-id="1ea6e-138">Asegúrese de prefijar un archivo de texto sin formato Unicode con una marca de orden de bytes.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-138">Be sure to prefix a Unicode plain text file with a byte order mark.</span></span> <span data-ttu-id="1ea6e-139">Para obtener más información, vea [usar marcas de orden de bytes](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span><span class="sxs-lookup"><span data-stu-id="1ea6e-139">For more information, see [Using Byte Order Marks](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span></span>

<span data-ttu-id="1ea6e-140">Aunque una aplicación puede usar **WriteConsole** en modo ANSI para escribir caracteres ANSI, las consolas no admiten secuencias de "ANSI escape" o "terminal virtual" a menos que estén habilitadas.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-140">Although an application can use **WriteConsole** in ANSI mode to write ANSI characters, consoles do not support "ANSI escape" or "virtual terminal" sequences unless enabled.</span></span> <span data-ttu-id="1ea6e-141">Consulte [**secuencias de terminal virtuales**](console-virtual-terminal-sequences.md) de la consola para obtener más información y para la aplicabilidad de la versión del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-141">See [**Console Virtual Terminal Sequences**](console-virtual-terminal-sequences.md) for more information and for operating system version applicability.</span></span>

<span data-ttu-id="1ea6e-142">Cuando las secuencias de escape de terminal virtual no están habilitadas, las funciones de consola pueden proporcionar una funcionalidad equivalente.</span><span class="sxs-lookup"><span data-stu-id="1ea6e-142">When virtual terminal escape sequences are not enabled, console functions can provide equivalent functionality.</span></span> <span data-ttu-id="1ea6e-143">Para obtener más información, vea [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md)y [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span><span class="sxs-lookup"><span data-stu-id="1ea6e-143">For more information, see [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md), and [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="1ea6e-144">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ea6e-144">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1ea6e-145">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="1ea6e-145">Minimum supported client</span></span> | <span data-ttu-id="1ea6e-146">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="1ea6e-146">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="1ea6e-147">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="1ea6e-147">Minimum supported server</span></span> | <span data-ttu-id="1ea6e-148">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="1ea6e-148">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="1ea6e-149">Encabezado</span><span class="sxs-lookup"><span data-stu-id="1ea6e-149">Header</span></span> | <span data-ttu-id="1ea6e-150">ConsoleApi. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1ea6e-150">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="1ea6e-151">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="1ea6e-151">Library</span></span> | <span data-ttu-id="1ea6e-152">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="1ea6e-152">Kernel32.lib</span></span> |
| <span data-ttu-id="1ea6e-153">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="1ea6e-153">DLL</span></span> | <span data-ttu-id="1ea6e-154">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1ea6e-154">Kernel32.dll</span></span> |
| <span data-ttu-id="1ea6e-155">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="1ea6e-155">Unicode and ANSI names</span></span> | <span data-ttu-id="1ea6e-156">**WriteConsoleW** (Unicode) y **WriteConsoleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="1ea6e-156">**WriteConsoleW** (Unicode) and **WriteConsoleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="1ea6e-157">Vea también</span><span class="sxs-lookup"><span data-stu-id="1ea6e-157">See also</span></span>

[<span data-ttu-id="1ea6e-158">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="1ea6e-158">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1ea6e-159">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="1ea6e-159">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="1ea6e-160">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="1ea6e-160">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="1ea6e-161">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="1ea6e-161">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="1ea6e-162">Métodos de entrada y salida</span><span class="sxs-lookup"><span data-stu-id="1ea6e-162">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="1ea6e-163">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="1ea6e-163">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="1ea6e-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="1ea6e-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="1ea6e-165">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="1ea6e-165">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="1ea6e-166">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="1ea6e-166">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="1ea6e-167">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="1ea6e-167">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="1ea6e-168">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="1ea6e-168">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

<span data-ttu-id="1ea6e-169">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="1ea6e-169">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span></span>

[<span data-ttu-id="1ea6e-170">**Escritura**</span><span class="sxs-lookup"><span data-stu-id="1ea6e-170">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
