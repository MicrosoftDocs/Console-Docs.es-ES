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
ms.openlocfilehash: de5138326c0800016cf5ca6e3232f032abcd01de
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061052"
---
# <a name="writeconsole-function"></a><span data-ttu-id="bf6e9-104">WriteConsole función)</span><span class="sxs-lookup"><span data-stu-id="bf6e9-104">WriteConsole function</span></span>


<span data-ttu-id="bf6e9-105">Escribe una cadena de caracteres en un búfer de pantalla de la consola a partir de la ubicación actual del cursor.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-105">Writes a character string to a console screen buffer beginning at the current cursor location.</span></span>

<a name="syntax"></a><span data-ttu-id="bf6e9-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="bf6e9-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

<a name="parameters"></a><span data-ttu-id="bf6e9-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bf6e9-107">Parameters</span></span>
----------

<span data-ttu-id="bf6e9-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="bf6e9-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="bf6e9-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="bf6e9-110">El identificador debe tener el derecho de acceso de \*\* \_ escritura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="bf6e9-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="bf6e9-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="bf6e9-112">*lpBuffer* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="bf6e9-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="bf6e9-113">Un puntero a un búfer que contiene los caracteres que se van a escribir en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-113">A pointer to a buffer that contains characters to be written to the console screen buffer.</span></span>

<span data-ttu-id="bf6e9-114">*nNumberOfCharsToWrite* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="bf6e9-114">*nNumberOfCharsToWrite* \[in\]</span></span>  
<span data-ttu-id="bf6e9-115">El número de caracteres que se va a escribir.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-115">The number of characters to be written.</span></span> <span data-ttu-id="bf6e9-116">Si el tamaño total del número de caracteres especificado supera el montón disponible, se produce un error en la función y \*\* \_ no \_ hay suficiente \_ memoria\*\*.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-116">If the total size of the specified number of characters exceeds the available heap, the function fails with **ERROR\_NOT\_ENOUGH\_MEMORY**.</span></span>

<span data-ttu-id="bf6e9-117">*lpNumberOfCharsWritten* \[ out, opcional\]</span><span class="sxs-lookup"><span data-stu-id="bf6e9-117">*lpNumberOfCharsWritten* \[out, optional\]</span></span>  
<span data-ttu-id="bf6e9-118">Puntero a una variable que recibe el número de caracteres escritos realmente.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-118">A pointer to a variable that receives the number of characters actually written.</span></span>

<span data-ttu-id="bf6e9-119">*lpReserved* </span><span class="sxs-lookup"><span data-stu-id="bf6e9-119">*lpReserved* </span></span>  
<span data-ttu-id="bf6e9-120">Sector debe ser **null**.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-120">Reserved; must be **NULL**.</span></span>

<a name="return-value"></a><span data-ttu-id="bf6e9-121">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="bf6e9-121">Return value</span></span>
------------

<span data-ttu-id="bf6e9-122">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="bf6e9-123">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="bf6e9-124">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="bf6e9-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="bf6e9-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="bf6e9-125">Remarks</span></span>
-------

<span data-ttu-id="bf6e9-126">La función **WriteConsole** escribe caracteres en el búfer de pantalla de la consola en la posición actual del cursor.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-126">The **WriteConsole** function writes characters to the console screen buffer at the current cursor position.</span></span> <span data-ttu-id="bf6e9-127">La posición del cursor avanza a medida que se escriben caracteres.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-127">The cursor position advances as characters are written.</span></span> <span data-ttu-id="bf6e9-128">La función [**SetConsoleCursorPosition**](setconsolecursorposition.md) establece la posición actual del cursor.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-128">The [**SetConsoleCursorPosition**](setconsolecursorposition.md) function sets the current cursor position.</span></span>

<span data-ttu-id="bf6e9-129">Los caracteres se escriben con los atributos de color de primer plano y de fondo asociados al búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-129">Characters are written using the foreground and background color attributes associated with the console screen buffer.</span></span> <span data-ttu-id="bf6e9-130">La función [**SetConsoleTextAttribute**](setconsoletextattribute.md) cambia estos colores.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-130">The [**SetConsoleTextAttribute**](setconsoletextattribute.md) function changes these colors.</span></span> <span data-ttu-id="bf6e9-131">Para determinar los atributos de color actuales y la posición actual del cursor, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span><span class="sxs-lookup"><span data-stu-id="bf6e9-131">To determine the current color attributes and the current cursor position, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span></span>

<span data-ttu-id="bf6e9-132">Todos los modos de entrada que afectan al comportamiento de la función [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) tienen el mismo efecto en **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-132">All of the input modes that affect the behavior of the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) function have the same effect on **WriteConsole**.</span></span> <span data-ttu-id="bf6e9-133">Para recuperar y establecer los modos de salida de un búfer de pantalla de la consola, use las funciones [**GetConsoleMode**](getconsolemode.md) y [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="bf6e9-133">To retrieve and set the output modes of a console screen buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

<span data-ttu-id="bf6e9-134">La función **WriteConsole** usa caracteres Unicode o caracteres ANSI de la página de códigos actual de la consola.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-134">The **WriteConsole** function uses either Unicode characters or ANSI characters from the console's current code page.</span></span> <span data-ttu-id="bf6e9-135">La página de códigos de la consola tiene como valor predeterminado la página de códigos OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-135">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="bf6e9-136">Para cambiar la página de códigos de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) , o bien use los comandos **chcp** o **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="bf6e9-136">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<span data-ttu-id="bf6e9-137">**WriteConsole** produce un error si se usa con un identificador estándar que se redirige a un archivo.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-137">**WriteConsole** fails if it is used with a standard handle that is redirected to a file.</span></span> <span data-ttu-id="bf6e9-138">Si una aplicación procesa una salida multilingüe que se puede redirigir, determine si el identificador de salida es un identificador de consola (un método es llamar a la función [**GetConsoleMode**](getconsolemode.md) y comprobar si se realiza correctamente).</span><span class="sxs-lookup"><span data-stu-id="bf6e9-138">If an application processes multilingual output that can be redirected, determine whether the output handle is a console handle (one method is to call the [**GetConsoleMode**](getconsolemode.md) function and check whether it succeeds).</span></span> <span data-ttu-id="bf6e9-139">Si el identificador es un identificador de consola, llame a **WriteConsole**.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-139">If the handle is a console handle, call **WriteConsole**.</span></span> <span data-ttu-id="bf6e9-140">Si el identificador no es un identificador de consola, se redirige el resultado y se debe llamar a [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) para realizar la e/s.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-140">If the handle is not a console handle, the output is redirected and you should call [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) to perform the I/O.</span></span> <span data-ttu-id="bf6e9-141">Asegúrese de prefijar un archivo de texto sin formato Unicode con una marca de orden de bytes.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-141">Be sure to prefix a Unicode plain text file with a byte order mark.</span></span> <span data-ttu-id="bf6e9-142">Para obtener más información, vea [usar marcas de orden de bytes](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span><span class="sxs-lookup"><span data-stu-id="bf6e9-142">For more information, see [Using Byte Order Marks](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span></span>

<span data-ttu-id="bf6e9-143">Aunque una aplicación puede usar **WriteConsole** en modo ANSI para escribir caracteres ANSI, las consolas no admiten secuencias de escape ANSI.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-143">Although an application can use **WriteConsole** in ANSI mode to write ANSI characters, consoles do not support ANSI escape sequences.</span></span> <span data-ttu-id="bf6e9-144">Sin embargo, algunas funciones proporcionan una funcionalidad equivalente.</span><span class="sxs-lookup"><span data-stu-id="bf6e9-144">However, some functions provide equivalent functionality.</span></span> <span data-ttu-id="bf6e9-145">Para obtener más información, vea [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md)y [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span><span class="sxs-lookup"><span data-stu-id="bf6e9-145">For more information, see [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md), and [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span></span>

<a name="requirements"></a><span data-ttu-id="bf6e9-146">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf6e9-146">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="bf6e9-147">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="bf6e9-147">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="bf6e9-148">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="bf6e9-148">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bf6e9-149">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="bf6e9-149">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="bf6e9-150">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="bf6e9-150">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bf6e9-151">Encabezado</span><span class="sxs-lookup"><span data-stu-id="bf6e9-151">Header</span></span></p></td>
<td><span data-ttu-id="bf6e9-152">ConsoleApi. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="bf6e9-152">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bf6e9-153">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="bf6e9-153">Library</span></span></p></td>
<td><span data-ttu-id="bf6e9-154">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="bf6e9-154">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bf6e9-155">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="bf6e9-155">DLL</span></span></p></td>
<td><span data-ttu-id="bf6e9-156">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="bf6e9-156">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bf6e9-157">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="bf6e9-157">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="bf6e9-158"><strong>WriteConsoleW</strong> (Unicode) y <strong>WriteConsoleA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="bf6e9-158"><strong>WriteConsoleW</strong> (Unicode) and <strong>WriteConsoleA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="bf6e9-159"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="bf6e9-159"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="bf6e9-160">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="bf6e9-160">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="bf6e9-161">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="bf6e9-161">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="bf6e9-162">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="bf6e9-162">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="bf6e9-163">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="bf6e9-163">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="bf6e9-164">Métodos de entrada y salida</span><span class="sxs-lookup"><span data-stu-id="bf6e9-164">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="bf6e9-165">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="bf6e9-165">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="bf6e9-166">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="bf6e9-166">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="bf6e9-167">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="bf6e9-167">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="bf6e9-168">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="bf6e9-168">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="bf6e9-169">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="bf6e9-169">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="bf6e9-170">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="bf6e9-170">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

<span data-ttu-id="bf6e9-171">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="bf6e9-171">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span></span>

[<span data-ttu-id="bf6e9-172">**Escritura**</span><span class="sxs-lookup"><span data-stu-id="bf6e9-172">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




