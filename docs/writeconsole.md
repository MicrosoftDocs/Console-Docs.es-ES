---
title: Función WriteConsole
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
ms.openlocfilehash: 27caf0b0a804b99fdfe695efef4c085bf0c51567
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357615"
---
# <a name="writeconsole-function"></a><span data-ttu-id="30014-104">Función WriteConsole</span><span class="sxs-lookup"><span data-stu-id="30014-104">WriteConsole function</span></span>

<span data-ttu-id="30014-105">Escribe una cadena de caracteres en un búfer de pantalla de la consola a partir de la ubicación actual del cursor.</span><span class="sxs-lookup"><span data-stu-id="30014-105">Writes a character string to a console screen buffer beginning at the current cursor location.</span></span>

## <a name="syntax"></a><span data-ttu-id="30014-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="30014-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## <a name="parameters"></a><span data-ttu-id="30014-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="30014-107">Parameters</span></span>

<span data-ttu-id="30014-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="30014-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="30014-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="30014-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="30014-110">El identificador debe tener derecho de acceso de **GENERIC\_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="30014-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="30014-111">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="30014-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="30014-112">*lpBuffer* \[in\]</span><span class="sxs-lookup"><span data-stu-id="30014-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="30014-113">Puntero a un búfer que contiene los caracteres que se van a escribir en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="30014-113">A pointer to a buffer that contains characters to be written to the console screen buffer.</span></span> <span data-ttu-id="30014-114">Se espera que sea una matriz de `char` para `WriteConsoleA` o `wchar_t` para `WriteConsoleW`.</span><span class="sxs-lookup"><span data-stu-id="30014-114">This is expected to be an array of either `char` for `WriteConsoleA` or `wchar_t` for `WriteConsoleW`.</span></span>

<span data-ttu-id="30014-115">*nNumberOfCharsToWrite* \[in\]</span><span class="sxs-lookup"><span data-stu-id="30014-115">*nNumberOfCharsToWrite* \[in\]</span></span>  
<span data-ttu-id="30014-116">El número de caracteres que se va a escribir.</span><span class="sxs-lookup"><span data-stu-id="30014-116">The number of characters to be written.</span></span> <span data-ttu-id="30014-117">Si el tamaño total del número especificado de caracteres supera el montón disponible, se produce un error en la función con **ERROR\_NOT\_ENOUGH\_MEMORY**.</span><span class="sxs-lookup"><span data-stu-id="30014-117">If the total size of the specified number of characters exceeds the available heap, the function fails with **ERROR\_NOT\_ENOUGH\_MEMORY**.</span></span>

<span data-ttu-id="30014-118">*lpNumberOfCharsWritten* \[out, opcional\]</span><span class="sxs-lookup"><span data-stu-id="30014-118">*lpNumberOfCharsWritten* \[out, optional\]</span></span>  
<span data-ttu-id="30014-119">Puntero a una variable que recibe el número de caracteres escritos realmente.</span><span class="sxs-lookup"><span data-stu-id="30014-119">A pointer to a variable that receives the number of characters actually written.</span></span>

<span data-ttu-id="30014-120">*lpReserved* reservado; debe ser **NULL**.</span><span class="sxs-lookup"><span data-stu-id="30014-120">*lpReserved* Reserved; must be **NULL**.</span></span>

## <a name="return-value"></a><span data-ttu-id="30014-121">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="30014-121">Return value</span></span>

<span data-ttu-id="30014-122">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="30014-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="30014-123">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="30014-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="30014-124">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="30014-124">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="30014-125">Comentarios</span><span class="sxs-lookup"><span data-stu-id="30014-125">Remarks</span></span>

<span data-ttu-id="30014-126">La función **WriteConsole** escribe caracteres en el búfer de pantalla de la consola en la posición actual del cursor.</span><span class="sxs-lookup"><span data-stu-id="30014-126">The **WriteConsole** function writes characters to the console screen buffer at the current cursor position.</span></span> <span data-ttu-id="30014-127">La posición del cursor avanza a medida que se escriben caracteres.</span><span class="sxs-lookup"><span data-stu-id="30014-127">The cursor position advances as characters are written.</span></span> <span data-ttu-id="30014-128">La función [**SetConsoleCursorPosition**](setconsolecursorposition.md) establece la posición actual del cursor.</span><span class="sxs-lookup"><span data-stu-id="30014-128">The [**SetConsoleCursorPosition**](setconsolecursorposition.md) function sets the current cursor position.</span></span>

<span data-ttu-id="30014-129">Los caracteres se escriben con los atributos de color de primer plano y de fondo asociados al búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="30014-129">Characters are written using the foreground and background color attributes associated with the console screen buffer.</span></span> <span data-ttu-id="30014-130">La función [**SetConsoleTextAttribute**](setconsoletextattribute.md) cambia estos colores.</span><span class="sxs-lookup"><span data-stu-id="30014-130">The [**SetConsoleTextAttribute**](setconsoletextattribute.md) function changes these colors.</span></span> <span data-ttu-id="30014-131">Para determinar los atributos de color actuales y la posición actual del cursor, utilice [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span><span class="sxs-lookup"><span data-stu-id="30014-131">To determine the current color attributes and the current cursor position, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span></span>

<span data-ttu-id="30014-132">Todos los modos de entrada que afectan al comportamiento de la función [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) tienen el mismo efecto en **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="30014-132">All of the input modes that affect the behavior of the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) function have the same effect on **WriteConsole**.</span></span> <span data-ttu-id="30014-133">Para recuperar y establecer los modos de salida de un búfer de pantalla de la consola, use las funciones [**GetConsoleMode**](getconsolemode.md) y [**SetConsoleMode**](setconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="30014-133">To retrieve and set the output modes of a console screen buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

<span data-ttu-id="30014-134">**WriteConsole** produce un error si se usa con un identificador estándar que se redirige a un archivo.</span><span class="sxs-lookup"><span data-stu-id="30014-134">**WriteConsole** fails if it is used with a standard handle that is redirected to a file.</span></span> <span data-ttu-id="30014-135">Si una aplicación procesa una salida multilingüe que se puede redirigir, determine si el identificador de salida es un identificador de consola (un método consiste en llamar a la función [**GetConsoleMode**](getconsolemode.md) y comprobar si se realiza correctamente).</span><span class="sxs-lookup"><span data-stu-id="30014-135">If an application processes multilingual output that can be redirected, determine whether the output handle is a console handle (one method is to call the [**GetConsoleMode**](getconsolemode.md) function and check whether it succeeds).</span></span> <span data-ttu-id="30014-136">Si el identificador es un identificador de consola, llame a **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="30014-136">If the handle is a console handle, call **WriteConsole**.</span></span> <span data-ttu-id="30014-137">Si el identificador no es un identificador de consola, la salida se redirige y debe llamar a [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) para realizar la E/S.</span><span class="sxs-lookup"><span data-stu-id="30014-137">If the handle is not a console handle, the output is redirected and you should call [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) to perform the I/O.</span></span> <span data-ttu-id="30014-138">Asegúrese de prefijar un archivo de texto sin formato Unicode con una marca de orden de bytes.</span><span class="sxs-lookup"><span data-stu-id="30014-138">Be sure to prefix a Unicode plain text file with a byte order mark.</span></span> <span data-ttu-id="30014-139">Para obtener más información, consulte [Uso de marcas de orden de bytes](/windows/win32/intl/using-byte-order-marks).</span><span class="sxs-lookup"><span data-stu-id="30014-139">For more information, see [Using Byte Order Marks](/windows/win32/intl/using-byte-order-marks).</span></span>

<span data-ttu-id="30014-140">Aunque una aplicación puede usar **WriteConsole** en modo ANSI para escribir caracteres ANSI, las consolas no admiten secuencias de "escape ANSI" o de "terminal virtuales" a menos que estén habilitadas.</span><span class="sxs-lookup"><span data-stu-id="30014-140">Although an application can use **WriteConsole** in ANSI mode to write ANSI characters, consoles do not support "ANSI escape" or "virtual terminal" sequences unless enabled.</span></span> <span data-ttu-id="30014-141">Consulte [**Secuencias de terminal virtuales de la consola**](console-virtual-terminal-sequences.md) para obtener más información y para ver la aplicabilidad de la versión del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="30014-141">See [**Console Virtual Terminal Sequences**](console-virtual-terminal-sequences.md) for more information and for operating system version applicability.</span></span>

<span data-ttu-id="30014-142">Cuando las secuencias de escape de terminal virtuales no están habilitadas, las funciones de consola pueden proporcionar una funcionalidad equivalente.</span><span class="sxs-lookup"><span data-stu-id="30014-142">When virtual terminal escape sequences are not enabled, console functions can provide equivalent functionality.</span></span> <span data-ttu-id="30014-143">Para obtener más información, vea [**SetCursorPos**](/windows/win32/api/winuser/nf-winuser-setcursorpos), [**SetConsoleTextAttribute**](setconsoletextattribute.md) y [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span><span class="sxs-lookup"><span data-stu-id="30014-143">For more information, see [**SetCursorPos**](/windows/win32/api/winuser/nf-winuser-setcursorpos), [**SetConsoleTextAttribute**](setconsoletextattribute.md), and [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="30014-144">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30014-144">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="30014-145">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="30014-145">Minimum supported client</span></span> | <span data-ttu-id="30014-146">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="30014-146">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="30014-147">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="30014-147">Minimum supported server</span></span> | <span data-ttu-id="30014-148">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="30014-148">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="30014-149">Encabezado</span><span class="sxs-lookup"><span data-stu-id="30014-149">Header</span></span> | <span data-ttu-id="30014-150">ConsoleApi.h (a través de WinCon.h, incluido Windows.h)</span><span class="sxs-lookup"><span data-stu-id="30014-150">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="30014-151">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="30014-151">Library</span></span> | <span data-ttu-id="30014-152">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="30014-152">Kernel32.lib</span></span> |
| <span data-ttu-id="30014-153">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="30014-153">DLL</span></span> | <span data-ttu-id="30014-154">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="30014-154">Kernel32.dll</span></span> |
| <span data-ttu-id="30014-155">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="30014-155">Unicode and ANSI names</span></span> | <span data-ttu-id="30014-156">**WriteConsoleW** (Unicode) y **WriteConsoleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="30014-156">**WriteConsoleW** (Unicode) and **WriteConsoleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="30014-157">Vea también</span><span class="sxs-lookup"><span data-stu-id="30014-157">See also</span></span>

[<span data-ttu-id="30014-158">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="30014-158">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="30014-159">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="30014-159">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="30014-160">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="30014-160">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="30014-161">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="30014-161">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="30014-162">Métodos de entrada y salida</span><span class="sxs-lookup"><span data-stu-id="30014-162">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="30014-163">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="30014-163">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="30014-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="30014-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="30014-165">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="30014-165">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="30014-166">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="30014-166">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="30014-167">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="30014-167">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="30014-168">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="30014-168">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

[<span data-ttu-id="30014-169">**SetCursorPos**</span><span class="sxs-lookup"><span data-stu-id="30014-169">**SetCursorPos**</span></span>](/windows/win32/api/winuser/nf-winuser-setcursorpos)

[<span data-ttu-id="30014-170">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="30014-170">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)