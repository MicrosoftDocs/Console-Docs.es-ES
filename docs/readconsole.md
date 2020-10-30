---
title: ReadConsole función)
description: Lee la entrada de caracteres del búfer de entrada de la consola y lo quita del búfer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/ReadConsole
- wincon/ReadConsole
- ReadConsole
- consoleapi/ReadConsoleA
- wincon/ReadConsoleA
- ReadConsoleA
- consoleapi/ReadConsoleW
- wincon/ReadConsoleW
- ReadConsoleW
MS-HAID:
- '\_win32\_readconsole'
- base.readconsole
- consoles.readconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1aa9ecac-a9b9-4e6d-9206-7a57013de657
topic_type:
- apiref
api_name:
- ReadConsole
- ReadConsoleA
- ReadConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: f38994156a8c8e58c952a2ffc3d5d9531ec027e7
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037773"
---
# <a name="readconsole-function"></a><span data-ttu-id="35bf5-104">ReadConsole función)</span><span class="sxs-lookup"><span data-stu-id="35bf5-104">ReadConsole function</span></span>

<span data-ttu-id="35bf5-105">Lee la entrada de caracteres del búfer de entrada de la consola y lo quita del búfer.</span><span class="sxs-lookup"><span data-stu-id="35bf5-105">Reads character input from the console input buffer and removes it from the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="35bf5-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="35bf5-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsole(
  _In_     HANDLE  hConsoleInput,
  _Out_    LPVOID  lpBuffer,
  _In_     DWORD   nNumberOfCharsToRead,
  _Out_    LPDWORD lpNumberOfCharsRead,
  _In_opt_ LPVOID  pInputControl
);
```

## <a name="parameters"></a><span data-ttu-id="35bf5-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="35bf5-107">Parameters</span></span>

<span data-ttu-id="35bf5-108">*hConsoleInput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="35bf5-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="35bf5-109">Identificador para el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="35bf5-109">A handle to the console input buffer.</span></span> <span data-ttu-id="35bf5-110">El identificador debe tener el derecho de acceso de **\_ lectura genérico** .</span><span class="sxs-lookup"><span data-stu-id="35bf5-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="35bf5-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="35bf5-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="35bf5-112">*lpBuffer* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="35bf5-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="35bf5-113">Un puntero a un búfer que recibe los datos leídos del búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="35bf5-113">A pointer to a buffer that receives the data read from the console input buffer.</span></span>

<span data-ttu-id="35bf5-114">*nNumberOfCharsToRead* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="35bf5-114">*nNumberOfCharsToRead* \[in\]</span></span>  
<span data-ttu-id="35bf5-115">Número de caracteres que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="35bf5-115">The number of characters to be read.</span></span> <span data-ttu-id="35bf5-116">El tamaño del búfer al que apunta el parámetro *lpBuffer* debe ser al menos `nNumberOfCharsToRead * sizeof(TCHAR)` bytes.</span><span class="sxs-lookup"><span data-stu-id="35bf5-116">The size of the buffer pointed to by the *lpBuffer* parameter should be at least `nNumberOfCharsToRead * sizeof(TCHAR)` bytes.</span></span>

<span data-ttu-id="35bf5-117">*lpNumberOfCharsRead* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="35bf5-117">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="35bf5-118">Puntero a una variable que recibe el número de caracteres leídos realmente.</span><span class="sxs-lookup"><span data-stu-id="35bf5-118">A pointer to a variable that receives the number of characters actually read.</span></span>

<span data-ttu-id="35bf5-119">*pInputControl* \[ en, opcional\]</span><span class="sxs-lookup"><span data-stu-id="35bf5-119">*pInputControl* \[in, optional\]</span></span>  
<span data-ttu-id="35bf5-120">Puntero a una estructura [**de \_ \_ control READCONSOLE de consola**](console-readconsole-control.md) que especifica un carácter de control para indicar el final de la operación de lectura.</span><span class="sxs-lookup"><span data-stu-id="35bf5-120">A pointer to a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure that specifies a control character to signal the end of the read operation.</span></span> <span data-ttu-id="35bf5-121">Este parámetro puede ser **null** .</span><span class="sxs-lookup"><span data-stu-id="35bf5-121">This parameter can be **NULL** .</span></span>

<span data-ttu-id="35bf5-122">Este parámetro requiere una entrada Unicode de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="35bf5-122">This parameter requires Unicode input by default.</span></span> <span data-ttu-id="35bf5-123">En el modo ANSI, establezca este parámetro en **null** .</span><span class="sxs-lookup"><span data-stu-id="35bf5-123">For ANSI mode, set this parameter to **NULL** .</span></span>

## <a name="return-value"></a><span data-ttu-id="35bf5-124">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="35bf5-124">Return value</span></span>

<span data-ttu-id="35bf5-125">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="35bf5-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="35bf5-126">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="35bf5-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="35bf5-127">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="35bf5-127">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="35bf5-128">Comentarios</span><span class="sxs-lookup"><span data-stu-id="35bf5-128">Remarks</span></span>

<span data-ttu-id="35bf5-129">**ReadConsole** lee la entrada del teclado desde el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="35bf5-129">**ReadConsole** reads keyboard input from a console's input buffer.</span></span> <span data-ttu-id="35bf5-130">Se comporta como la función [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) , salvo que puede leer en modo Unicode (caracteres anchos) o ANSI.</span><span class="sxs-lookup"><span data-stu-id="35bf5-130">It behaves like the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) function, except that it can read in either Unicode (wide-character) or ANSI mode.</span></span> <span data-ttu-id="35bf5-131">Para tener aplicaciones que mantengan un único conjunto de orígenes compatibles con ambos modos, use **ReadConsole** en lugar de **readfile** .</span><span class="sxs-lookup"><span data-stu-id="35bf5-131">To have applications that maintain a single set of sources compatible with both modes, use **ReadConsole** rather than **ReadFile** .</span></span> <span data-ttu-id="35bf5-132">Aunque **ReadConsole** solo se puede usar con un identificador de búfer de entrada de la consola, **readfile** se puede usar con otros identificadores (como archivos o canalizaciones).</span><span class="sxs-lookup"><span data-stu-id="35bf5-132">Although **ReadConsole** can only be used with a console input buffer handle, **ReadFile** can be used with other handles (such as files or pipes).</span></span> <span data-ttu-id="35bf5-133">**ReadConsole** produce un error si se usa con un identificador estándar que se ha redirigido para que sea distinto de un identificador de consola.</span><span class="sxs-lookup"><span data-stu-id="35bf5-133">**ReadConsole** fails if used with a standard handle that has been redirected to be something other than a console handle.</span></span>

<span data-ttu-id="35bf5-134">Todos los modos de entrada que afectan al comportamiento de [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) tienen el mismo efecto en **ReadConsole** .</span><span class="sxs-lookup"><span data-stu-id="35bf5-134">All of the input modes that affect the behavior of [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) have the same effect on **ReadConsole** .</span></span> <span data-ttu-id="35bf5-135">Para recuperar y establecer los modos de entrada de un búfer de entrada de la consola, use las funciones [**GetConsoleMode**](getconsolemode.md) y [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="35bf5-135">To retrieve and set the input modes of a console input buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

<span data-ttu-id="35bf5-136">Si el búfer de entrada contiene eventos de entrada distintos de los eventos de teclado (como eventos del mouse o eventos de cambio de tamaño de ventana), se descartan.</span><span class="sxs-lookup"><span data-stu-id="35bf5-136">If the input buffer contains input events other than keyboard events (such as mouse events or window-resizing events), they are discarded.</span></span> <span data-ttu-id="35bf5-137">Estos eventos solo se pueden leer mediante la función [**ReadConsoleInput**](readconsoleinput.md) .</span><span class="sxs-lookup"><span data-stu-id="35bf5-137">Those events can only be read by using the [**ReadConsoleInput**](readconsoleinput.md) function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

<span data-ttu-id="35bf5-138">El parámetro *pInputControl* se puede usar para habilitar las reactivaciones intermedias desde la lectura en respuesta a un carácter de control de finalización de archivos especificado en una estructura de [**\_ \_ control de READCONSOLE de consola**](console-readconsole-control.md) .</span><span class="sxs-lookup"><span data-stu-id="35bf5-138">The *pInputControl* parameter can be used to enable intermediate wakeups from the read in response to a file-completion control character specified in a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure.</span></span> <span data-ttu-id="35bf5-139">Esta característica requiere que se habiliten las extensiones de comandos, que el identificador de salida estándar sea un identificador de salida de consola y que la entrada sea Unicode.</span><span class="sxs-lookup"><span data-stu-id="35bf5-139">This feature requires command extensions to be enabled, the standard output handle to be a console output handle, and input to be Unicode.</span></span>

<span data-ttu-id="35bf5-140">**Windows Server 2003 y Windows XP/2000:** No se admite la característica de lectura intermedia.</span><span class="sxs-lookup"><span data-stu-id="35bf5-140">**Windows Server 2003 and Windows XP/2000:** The intermediate read feature is not supported.</span></span>

## <a name="requirements"></a><span data-ttu-id="35bf5-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="35bf5-141">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="35bf5-142">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="35bf5-142">Minimum supported client</span></span> | <span data-ttu-id="35bf5-143">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="35bf5-143">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="35bf5-144">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="35bf5-144">Minimum supported server</span></span> | <span data-ttu-id="35bf5-145">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="35bf5-145">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="35bf5-146">Encabezado</span><span class="sxs-lookup"><span data-stu-id="35bf5-146">Header</span></span> | <span data-ttu-id="35bf5-147">ConsoleApi. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="35bf5-147">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="35bf5-148">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="35bf5-148">Library</span></span> | <span data-ttu-id="35bf5-149">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="35bf5-149">Kernel32.lib</span></span> |
| <span data-ttu-id="35bf5-150">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="35bf5-150">DLL</span></span> | <span data-ttu-id="35bf5-151">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="35bf5-151">Kernel32.dll</span></span> |
| <span data-ttu-id="35bf5-152">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="35bf5-152">Unicode and ANSI names</span></span> | <span data-ttu-id="35bf5-153">**ReadConsoleW** (Unicode) y **ReadConsoleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="35bf5-153">**ReadConsoleW** (Unicode) and **ReadConsoleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="35bf5-154">Consulte también</span><span class="sxs-lookup"><span data-stu-id="35bf5-154">See also</span></span>

[<span data-ttu-id="35bf5-155">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="35bf5-155">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="35bf5-156">**\_control READCONSOLE de consola \_**</span><span class="sxs-lookup"><span data-stu-id="35bf5-156">**CONSOLE\_READCONSOLE\_CONTROL**</span></span>](console-readconsole-control.md)

[<span data-ttu-id="35bf5-157">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="35bf5-157">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="35bf5-158">Métodos de entrada y salida</span><span class="sxs-lookup"><span data-stu-id="35bf5-158">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="35bf5-159">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="35bf5-159">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="35bf5-160">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="35bf5-160">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="35bf5-161">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="35bf5-161">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="35bf5-162">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="35bf5-162">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="35bf5-163">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="35bf5-163">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="35bf5-164">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="35bf5-164">**WriteConsole**</span></span>](writeconsole.md)
