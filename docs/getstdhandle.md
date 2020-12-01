---
title: GetStdHandle (función)
description: Recupera un identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- processenv/GetStdHandle
- winbase/GetStdHandle
- GetStdHandle
MS-HAID:
- '\_win32\_getstdhandle'
- base.getstdhandle
- consoles.getstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 23cd76e9-671a-48d0-9b82-2beda8917348
topic_type:
- apiref
api_name:
- GetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 42857417cedb661014de869536b798d29c9eb884
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420214"
---
# <a name="getstdhandle-function"></a><span data-ttu-id="964ab-104">GetStdHandle (función)</span><span class="sxs-lookup"><span data-stu-id="964ab-104">GetStdHandle function</span></span>

<span data-ttu-id="964ab-105">Recupera un identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).</span><span class="sxs-lookup"><span data-stu-id="964ab-105">Retrieves a handle to the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="964ab-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="964ab-106">Syntax</span></span>

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a><span data-ttu-id="964ab-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="964ab-107">Parameters</span></span>

<span data-ttu-id="964ab-108">*nStdHandle* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="964ab-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="964ab-109">El dispositivo estándar.</span><span class="sxs-lookup"><span data-stu-id="964ab-109">The standard device.</span></span> <span data-ttu-id="964ab-110">Este parámetro puede ser uno de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="964ab-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="964ab-111">Value</span><span class="sxs-lookup"><span data-stu-id="964ab-111">Value</span></span> | <span data-ttu-id="964ab-112">Significado</span><span class="sxs-lookup"><span data-stu-id="964ab-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="964ab-113">**STD_INPUT_HANDLE** (DWORD)-10</span><span class="sxs-lookup"><span data-stu-id="964ab-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="964ab-114">El dispositivo de entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="964ab-114">The standard input device.</span></span> <span data-ttu-id="964ab-115">Inicialmente, es el búfer de entrada de la consola, `CONIN$` .</span><span class="sxs-lookup"><span data-stu-id="964ab-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="964ab-116">**STD_OUTPUT_HANDLE** (DWORD)-11</span><span class="sxs-lookup"><span data-stu-id="964ab-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="964ab-117">El dispositivo de salida estándar.</span><span class="sxs-lookup"><span data-stu-id="964ab-117">The standard output device.</span></span> <span data-ttu-id="964ab-118">Inicialmente, es el búfer de pantalla de la consola activo, `CONOUT$` .</span><span class="sxs-lookup"><span data-stu-id="964ab-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="964ab-119">**STD_ERROR_HANDLE** (DWORD)-12</span><span class="sxs-lookup"><span data-stu-id="964ab-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="964ab-120">El dispositivo de error estándar.</span><span class="sxs-lookup"><span data-stu-id="964ab-120">The standard error device.</span></span> <span data-ttu-id="964ab-121">Inicialmente, es el búfer de pantalla de la consola activo, `CONOUT$` .</span><span class="sxs-lookup"><span data-stu-id="964ab-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

## <a name="return-value"></a><span data-ttu-id="964ab-122">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="964ab-122">Return value</span></span>

<span data-ttu-id="964ab-123">Si la función se ejecuta correctamente, el valor devuelto es un identificador del dispositivo especificado o un identificador Redirigido establecido por una llamada anterior a [**SetStdHandle**](setstdhandle.md).</span><span class="sxs-lookup"><span data-stu-id="964ab-123">If the function succeeds, the return value is a handle to the specified device, or a redirected handle set by a previous call to [**SetStdHandle**](setstdhandle.md).</span></span> <span data-ttu-id="964ab-124">El identificador tiene derechos de acceso genéricos de **\_ lectura** y **\_ escritura** , a menos que la aplicación haya usado **SetStdHandle** para establecer un identificador estándar con un acceso inferior.</span><span class="sxs-lookup"><span data-stu-id="964ab-124">The handle has **GENERIC\_READ** and **GENERIC\_WRITE** access rights, unless the application has used **SetStdHandle** to set a standard handle with lesser access.</span></span>

<span data-ttu-id="964ab-125">Si se produce un error en la función, el valor devuelto es un **\_ \_ valor de identificador no válido**.</span><span class="sxs-lookup"><span data-stu-id="964ab-125">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="964ab-126">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="964ab-126">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="964ab-127">Si una aplicación no tiene identificadores estándar asociados, como un servicio que se ejecuta en un escritorio interactivo y no los ha redirigido, el valor devuelto es **null**.</span><span class="sxs-lookup"><span data-stu-id="964ab-127">If an application does not have associated standard handles, such as a service running on an interactive desktop, and has not redirected them, the return value is **NULL**.</span></span>

## <a name="remarks"></a><span data-ttu-id="964ab-128">Comentarios</span><span class="sxs-lookup"><span data-stu-id="964ab-128">Remarks</span></span>

<span data-ttu-id="964ab-129">Los identificadores devueltos por **GetStdHandle** pueden ser usados por aplicaciones que necesitan leer o escribir en la consola.</span><span class="sxs-lookup"><span data-stu-id="964ab-129">Handles returned by **GetStdHandle** can be used by applications that need to read from or write to the console.</span></span> <span data-ttu-id="964ab-130">Cuando se crea una consola, el identificador de entrada estándar es un identificador del búfer de entrada de la consola, y los identificadores de salida estándar y de error estándar son identificadores del búfer de pantalla activo de la consola.</span><span class="sxs-lookup"><span data-stu-id="964ab-130">When a console is created, the standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles of the console's active screen buffer.</span></span> <span data-ttu-id="964ab-131">Estos identificadores pueden ser utilizados por las funciones [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) , o por cualquiera de las funciones de consola que tienen acceso al búfer de entrada de la consola o a un búfer de pantalla (por ejemplo, las funciones [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md)o [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) ).</span><span class="sxs-lookup"><span data-stu-id="964ab-131">These handles can be used by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) functions, or by any of the console functions that access the console input buffer or a screen buffer (for example, the [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md), or [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) functions).</span></span>

<span data-ttu-id="964ab-132">Los identificadores estándar de un proceso se pueden redirigir mediante una llamada a [**SetStdHandle**](setstdhandle.md), en cuyo caso **GetStdHandle** devuelve el identificador redirigido.</span><span class="sxs-lookup"><span data-stu-id="964ab-132">The standard handles of a process may be redirected by a call to [**SetStdHandle**](setstdhandle.md), in which case **GetStdHandle** returns the redirected handle.</span></span> <span data-ttu-id="964ab-133">Si se han redirigido los identificadores estándar, puede especificar el `CONIN$` valor en una llamada a la función [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) para obtener un identificador de un búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="964ab-133">If the standard handles have been redirected, you can specify the `CONIN$` value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="964ab-134">De forma similar, puede especificar el `CONOUT$` valor para obtener un identificador para el búfer de pantalla activo de la consola.</span><span class="sxs-lookup"><span data-stu-id="964ab-134">Similarly, you can specify the `CONOUT$` value to get a handle to a console's active screen buffer.</span></span>

<span data-ttu-id="964ab-135">Los identificadores estándar de un proceso en la entrada del método Main están dictados por la configuración de la marca [**/Subsystem**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem) que se pasa al enlazador cuando se compiló la aplicación.</span><span class="sxs-lookup"><span data-stu-id="964ab-135">The standard handles of a process on entry of the main method are dictated by the configuration of the [**/SUBSYSTEM**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem) flag passed to the linker when the application was built.</span></span> <span data-ttu-id="964ab-136">Al especificar **/Subsystem: Console** , se solicita que el sistema operativo rellene los identificadores con una sesión de consola al inicio, si el elemento primario aún no ha rellenado la tabla de identificadores estándar por herencia.</span><span class="sxs-lookup"><span data-stu-id="964ab-136">Specifying **/SUBSYSTEM:CONSOLE** requests that the operating system fill the handles with a console session on startup, if the parent didn't already fill the standard handle table by inheritance.</span></span> <span data-ttu-id="964ab-137">En el contrario, **/Subsystem: Windows** implica que la aplicación no necesita una consola y probablemente no esté usando los manipuladores estándar.</span><span class="sxs-lookup"><span data-stu-id="964ab-137">On the contrary, **/SUBSYSTEM:WINDOWS** implies that the application does not need a console and will likely not be making use of the standard handles.</span></span> <span data-ttu-id="964ab-138">Puede encontrar más información sobre cómo controlar la herencia en la documentación de [**STARTF \_ USESTDHANDLES**](https://docs.microsoft.com/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).</span><span class="sxs-lookup"><span data-stu-id="964ab-138">More information on handle inheritance can be found in the documentation for [**STARTF\_USESTDHANDLES**](https://docs.microsoft.com/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).</span></span>

<span data-ttu-id="964ab-139">Algunas aplicaciones funcionan fuera de los límites de su subsistema declarado; por ejemplo, una aplicación **/Subsystem: Windows** puede comprobar o utilizar los identificadores estándar para el registro o la depuración, pero funciona normalmente con una interfaz gráfica de usuario.</span><span class="sxs-lookup"><span data-stu-id="964ab-139">Some applications operate outside the boundaries of their declared subsystem; for instance, a **/SUBSYSTEM:WINDOWS** application might check/use standard handles for logging or debugging purposes but operate normally with a graphical user interface.</span></span> <span data-ttu-id="964ab-140">Estas aplicaciones deberán sondear cuidadosamente el estado de los identificadores estándar en el inicio y hacer uso de [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md)y [**FreeConsole**](freeconsole.md) para agregar o quitar una consola si lo desea.</span><span class="sxs-lookup"><span data-stu-id="964ab-140">These applications will need to carefully probe the state of standard handles on startup and make use of [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md), and [**FreeConsole**](freeconsole.md) to add/remove a console if desired.</span></span>

<span data-ttu-id="964ab-141">Algunas aplicaciones también pueden variar su comportamiento en el tipo de identificador heredado.</span><span class="sxs-lookup"><span data-stu-id="964ab-141">Some applications may also vary their behavior on the type of inherited handle.</span></span> <span data-ttu-id="964ab-142">Ambigüedad: el tipo entre la consola, la canalización, el archivo y otros se puede realizar con [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype).</span><span class="sxs-lookup"><span data-stu-id="964ab-142">Disambiguating the type between console, pipe, file, and others can be performed with [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype).</span></span>

### <a name="attachdetach-behavior"></a><span data-ttu-id="964ab-143">Comportamiento de adjuntar/separar</span><span class="sxs-lookup"><span data-stu-id="964ab-143">Attach/detach behavior</span></span>

<span data-ttu-id="964ab-144">Al conectarse a una nueva consola, los identificadores estándar siempre se reemplazan por identificadores de consola, a menos que se haya especificado **STARTF \_ USESTDHANDLES** durante la creación del proceso.</span><span class="sxs-lookup"><span data-stu-id="964ab-144">When attaching to a new console, standard handles are always replaced with console handles unless **STARTF\_USESTDHANDLES** was specified during process creation.</span></span>

<span data-ttu-id="964ab-145">Si el valor existente del identificador estándar es **null**, o el valor existente del identificador estándar es similar a un pseudohandle de consola, el identificador se reemplaza por un identificador de consola.</span><span class="sxs-lookup"><span data-stu-id="964ab-145">If the existing value of the standard handle is **NULL**, or the existing value of the standard handle looks like a console pseudohandle, the handle is replaced with a console handle.</span></span>

<span data-ttu-id="964ab-146">Cuando un elemento primario usa **Create \_ New \_ Console** y **STARTF \_ USESTDHANDLES** para crear un proceso de consola, no se reemplazarán los identificadores estándar a menos que el valor existente del identificador estándar sea **null** o una pseudohandle de consola.</span><span class="sxs-lookup"><span data-stu-id="964ab-146">When a parent uses both **CREATE\_NEW\_CONSOLE** and **STARTF\_USESTDHANDLES** to create a console process, standard handles will not be replaced unless the existing value of the standard handle is **NULL** or a console pseudohandle.</span></span>

> [!NOTE]
><span data-ttu-id="964ab-147">Los procesos de la consola *deben* comenzar con los identificadores estándar llenos o se rellenarán automáticamente con los identificadores adecuados para una nueva consola.</span><span class="sxs-lookup"><span data-stu-id="964ab-147">Console processes *must* start with the standard handles filled or they will be filled automatically with appropriate handles to a new console.</span></span> <span data-ttu-id="964ab-148">Las aplicaciones de la interfaz gráfica de usuario (GUI) se pueden iniciar sin los identificadores estándar y no se rellenarán automáticamente.</span><span class="sxs-lookup"><span data-stu-id="964ab-148">Graphical user interface (GUI) applications can be started without the standard handles and they will not be automatically filled.</span></span>

## <a name="examples"></a><span data-ttu-id="964ab-149">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="964ab-149">Examples</span></span>

<span data-ttu-id="964ab-150">Para obtener un ejemplo, vea [leer eventos de búfer de entrada](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="964ab-150">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="964ab-151">Requisitos</span><span class="sxs-lookup"><span data-stu-id="964ab-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="964ab-152">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="964ab-152">Minimum supported client</span></span> | <span data-ttu-id="964ab-153">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="964ab-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="964ab-154">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="964ab-154">Minimum supported server</span></span> | <span data-ttu-id="964ab-155">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="964ab-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="964ab-156">Encabezado</span><span class="sxs-lookup"><span data-stu-id="964ab-156">Header</span></span> | <span data-ttu-id="964ab-157">ProcessEnv. h (a través de Winbase. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="964ab-157">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="964ab-158">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="964ab-158">Library</span></span> | <span data-ttu-id="964ab-159">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="964ab-159">Kernel32.lib</span></span> |
| <span data-ttu-id="964ab-160">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="964ab-160">DLL</span></span> | <span data-ttu-id="964ab-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="964ab-161">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="964ab-162">Vea también</span><span class="sxs-lookup"><span data-stu-id="964ab-162">See also</span></span>

[<span data-ttu-id="964ab-163">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="964ab-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="964ab-164">Identificadores de consola</span><span class="sxs-lookup"><span data-stu-id="964ab-164">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="964ab-165">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="964ab-165">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="964ab-166">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="964ab-166">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="964ab-167">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="964ab-167">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="964ab-168">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="964ab-168">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="964ab-169">**SetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="964ab-169">**SetStdHandle**</span></span>](setstdhandle.md)

[<span data-ttu-id="964ab-170">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="964ab-170">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="964ab-171">**Escritura**</span><span class="sxs-lookup"><span data-stu-id="964ab-171">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
