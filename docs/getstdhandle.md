---
title: Función GetStdHandle
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
ms.openlocfilehash: 0804e12ff7510cd41bec66e1a45f8a31add7c17a
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358755"
---
# <a name="getstdhandle-function"></a><span data-ttu-id="583e2-104">Función GetStdHandle</span><span class="sxs-lookup"><span data-stu-id="583e2-104">GetStdHandle function</span></span>

<span data-ttu-id="583e2-105">Recupera un identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).</span><span class="sxs-lookup"><span data-stu-id="583e2-105">Retrieves a handle to the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="583e2-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="583e2-106">Syntax</span></span>

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a><span data-ttu-id="583e2-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="583e2-107">Parameters</span></span>

<span data-ttu-id="583e2-108">*nStdHandle* \[in\]</span><span class="sxs-lookup"><span data-stu-id="583e2-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="583e2-109">El dispositivo estándar.</span><span class="sxs-lookup"><span data-stu-id="583e2-109">The standard device.</span></span> <span data-ttu-id="583e2-110">Este parámetro puede ser uno de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="583e2-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="583e2-111">Valor</span><span class="sxs-lookup"><span data-stu-id="583e2-111">Value</span></span> | <span data-ttu-id="583e2-112">Significado</span><span class="sxs-lookup"><span data-stu-id="583e2-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="583e2-113">**STD_INPUT_HANDLE** (DWORD) -10</span><span class="sxs-lookup"><span data-stu-id="583e2-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="583e2-114">El dispositivo de entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="583e2-114">The standard input device.</span></span> <span data-ttu-id="583e2-115">Inicialmente, es el búfer de entrada de la consola, `CONIN$`.</span><span class="sxs-lookup"><span data-stu-id="583e2-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="583e2-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span><span class="sxs-lookup"><span data-stu-id="583e2-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="583e2-117">El dispositivo de salida estándar.</span><span class="sxs-lookup"><span data-stu-id="583e2-117">The standard output device.</span></span> <span data-ttu-id="583e2-118">Inicialmente, es el búfer de pantalla activo de la consola, `CONOUT$`.</span><span class="sxs-lookup"><span data-stu-id="583e2-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="583e2-119">**STD_ERROR_HANDLE** (DWORD) -12</span><span class="sxs-lookup"><span data-stu-id="583e2-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="583e2-120">El dispositivo de error estándar.</span><span class="sxs-lookup"><span data-stu-id="583e2-120">The standard error device.</span></span> <span data-ttu-id="583e2-121">Inicialmente, es el búfer de pantalla activo de la consola, `CONOUT$`.</span><span class="sxs-lookup"><span data-stu-id="583e2-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

## <a name="return-value"></a><span data-ttu-id="583e2-122">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="583e2-122">Return value</span></span>

<span data-ttu-id="583e2-123">Si la función se ejecuta correctamente, el valor devuelto es un identificador del dispositivo especificado o un identificador redirigido establecido por una llamada anterior en [**SetStdHandle**](setstdhandle.md).</span><span class="sxs-lookup"><span data-stu-id="583e2-123">If the function succeeds, the return value is a handle to the specified device, or a redirected handle set by a previous call to [**SetStdHandle**](setstdhandle.md).</span></span> <span data-ttu-id="583e2-124">El identificador tiene los derechos de acceso **GENERIC\_READ** y **GENERIC\_WRITE**, a menos que la aplicación haya usado **SetStdHandle** para establecer un identificador estándar con un acceso inferior.</span><span class="sxs-lookup"><span data-stu-id="583e2-124">The handle has **GENERIC\_READ** and **GENERIC\_WRITE** access rights, unless the application has used **SetStdHandle** to set a standard handle with lesser access.</span></span>

<span data-ttu-id="583e2-125">Si la función no se ejecuta correctamente, el valor devuelto es **INVALID\_HANDLE\_VALUE**.</span><span class="sxs-lookup"><span data-stu-id="583e2-125">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="583e2-126">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="583e2-126">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

<span data-ttu-id="583e2-127">Si una aplicación no tiene identificadores estándar asociados, como un servicio que se ejecuta en un escritorio interactivo y no los ha redirigido, el valor devuelto es **NULL**.</span><span class="sxs-lookup"><span data-stu-id="583e2-127">If an application does not have associated standard handles, such as a service running on an interactive desktop, and has not redirected them, the return value is **NULL**.</span></span>

## <a name="remarks"></a><span data-ttu-id="583e2-128">Comentarios</span><span class="sxs-lookup"><span data-stu-id="583e2-128">Remarks</span></span>

<span data-ttu-id="583e2-129">Las aplicaciones que necesitan leer o escribir en la consola pueden usar los identificadores devueltos por **GetStdHandle**.</span><span class="sxs-lookup"><span data-stu-id="583e2-129">Handles returned by **GetStdHandle** can be used by applications that need to read from or write to the console.</span></span> <span data-ttu-id="583e2-130">Cuando se crea una consola, el identificador de entrada estándar es un identificador del búfer de entrada de la consola, y los identificadores de salida estándar y de error estándar son identificadores del búfer de pantalla activo de la consola.</span><span class="sxs-lookup"><span data-stu-id="583e2-130">When a console is created, the standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles of the console's active screen buffer.</span></span> <span data-ttu-id="583e2-131">Las funciones [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) y [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile), o cualquiera de las funciones de la consola que tienen acceso al búfer de entrada de la consola o un búfer de pantalla (por ejemplo, las funciones [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md) o [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)) pueden usar estos identificadores.</span><span class="sxs-lookup"><span data-stu-id="583e2-131">These handles can be used by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) and [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) functions, or by any of the console functions that access the console input buffer or a screen buffer (for example, the [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md), or [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) functions).</span></span>

<span data-ttu-id="583e2-132">Los identificadores estándar de un proceso se pueden redirigir mediante una llamada a [**SetStdHandle**](setstdhandle.md), en cuyo caso **GetStdHandle** devuelve el identificador redirigido.</span><span class="sxs-lookup"><span data-stu-id="583e2-132">The standard handles of a process may be redirected by a call to [**SetStdHandle**](setstdhandle.md), in which case **GetStdHandle** returns the redirected handle.</span></span> <span data-ttu-id="583e2-133">Si se han redirigido los identificadores estándar, puede especificar el valor `CONIN$` en una llamada a la función [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) para obtener un identificador del búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="583e2-133">If the standard handles have been redirected, you can specify the `CONIN$` value in a call to the [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="583e2-134">De forma similar, puede especificar el valor `CONOUT$` para obtener un identificador para el búfer de pantalla activo de la consola.</span><span class="sxs-lookup"><span data-stu-id="583e2-134">Similarly, you can specify the `CONOUT$` value to get a handle to a console's active screen buffer.</span></span>

<span data-ttu-id="583e2-135">Los identificadores estándar de un proceso en la entrada del método principal están dictaminados por la configuración de la marca [ **/SUBSYSTEM**](/cpp/build/reference/subsystem-specify-subsystem) que se pasa al enlazador cuando se compiló la aplicación.</span><span class="sxs-lookup"><span data-stu-id="583e2-135">The standard handles of a process on entry of the main method are dictated by the configuration of the [**/SUBSYSTEM**](/cpp/build/reference/subsystem-specify-subsystem) flag passed to the linker when the application was built.</span></span> <span data-ttu-id="583e2-136">Al especificar **/SUBSYSTEM:CONSOLE**, se solicita que el sistema operativo rellene los identificadores con una sesión de consola en el inicio, si el elemento primario aún no ha rellenado la tabla de identificadores estándar por herencia.</span><span class="sxs-lookup"><span data-stu-id="583e2-136">Specifying **/SUBSYSTEM:CONSOLE** requests that the operating system fill the handles with a console session on startup, if the parent didn't already fill the standard handle table by inheritance.</span></span> <span data-ttu-id="583e2-137">Por el contrario, **/SUBSYSTEM:WINDOWS** implica que la aplicación no necesita una consola y que probablemente no usará los identificadores estándar.</span><span class="sxs-lookup"><span data-stu-id="583e2-137">On the contrary, **/SUBSYSTEM:WINDOWS** implies that the application does not need a console and will likely not be making use of the standard handles.</span></span> <span data-ttu-id="583e2-138">Puede encontrar más información sobre la herencia de identificadores en la documentación de [**STARTF\_USESTDHANDLES**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).</span><span class="sxs-lookup"><span data-stu-id="583e2-138">More information on handle inheritance can be found in the documentation for [**STARTF\_USESTDHANDLES**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).</span></span>

<span data-ttu-id="583e2-139">Algunas aplicaciones funcionan fuera de los límites de su subsistema declarado; por ejemplo, una aplicación **/SUBSYSTEM:WINDOWS** puede comprobar o usar identificadores estándar para el registro o la depuración, pero funciona normalmente con una interfaz gráfica de usuario.</span><span class="sxs-lookup"><span data-stu-id="583e2-139">Some applications operate outside the boundaries of their declared subsystem; for instance, a **/SUBSYSTEM:WINDOWS** application might check/use standard handles for logging or debugging purposes but operate normally with a graphical user interface.</span></span> <span data-ttu-id="583e2-140">Estas aplicaciones deberán sondear cuidadosamente el estado de los identificadores estándar en el inicio y usar [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md) y [**FreeConsole**](freeconsole.md) para agregar o quitar una consola si se desea.</span><span class="sxs-lookup"><span data-stu-id="583e2-140">These applications will need to carefully probe the state of standard handles on startup and make use of [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md), and [**FreeConsole**](freeconsole.md) to add/remove a console if desired.</span></span>

<span data-ttu-id="583e2-141">Algunas aplicaciones también pueden variar su comportamiento sobre el tipo de identificador heredado.</span><span class="sxs-lookup"><span data-stu-id="583e2-141">Some applications may also vary their behavior on the type of inherited handle.</span></span> <span data-ttu-id="583e2-142">La eliminación de la ambigüedad del tipo entre la consola, la canalización, el archivo y otros se pueden realizar con [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype).</span><span class="sxs-lookup"><span data-stu-id="583e2-142">Disambiguating the type between console, pipe, file, and others can be performed with [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype).</span></span>

### <a name="attachdetach-behavior"></a><span data-ttu-id="583e2-143">Comportamiento de la asociación o desasociación</span><span class="sxs-lookup"><span data-stu-id="583e2-143">Attach/detach behavior</span></span>

<span data-ttu-id="583e2-144">Al asociarse a una nueva consola, los identificadores estándar siempre se reemplazan por identificadores de consola, a menos que se especifique **STARTF\_USESTDHANDLES** durante la creación del proceso.</span><span class="sxs-lookup"><span data-stu-id="583e2-144">When attaching to a new console, standard handles are always replaced with console handles unless **STARTF\_USESTDHANDLES** was specified during process creation.</span></span>

<span data-ttu-id="583e2-145">Si el valor existente del identificador estándar es **NULL**, o el valor existente del identificador estándar es similar a un pseudoidentificador de consola, el identificador se reemplaza por un identificador de consola.</span><span class="sxs-lookup"><span data-stu-id="583e2-145">If the existing value of the standard handle is **NULL**, or the existing value of the standard handle looks like a console pseudohandle, the handle is replaced with a console handle.</span></span>

<span data-ttu-id="583e2-146">Cuando un elemento primario usa tanto **CREATE\_NEW\_CONSOLE** como **STARTF\_USESTDHANDLES** para crear un proceso de consola, no se reemplazarán los identificadores estándar a menos que el valor existente del identificador estándar sea **NULL** o un pseudoidentificador de consola.</span><span class="sxs-lookup"><span data-stu-id="583e2-146">When a parent uses both **CREATE\_NEW\_CONSOLE** and **STARTF\_USESTDHANDLES** to create a console process, standard handles will not be replaced unless the existing value of the standard handle is **NULL** or a console pseudohandle.</span></span>

> [!NOTE]
><span data-ttu-id="583e2-147">Los procesos de consola *deben* empezar con los identificadores estándar rellenados o se rellenarán automáticamente con los identificadores adecuados para una nueva consola.</span><span class="sxs-lookup"><span data-stu-id="583e2-147">Console processes *must* start with the standard handles filled or they will be filled automatically with appropriate handles to a new console.</span></span> <span data-ttu-id="583e2-148">Las aplicaciones de la interfaz gráfica de usuario (GUI) se pueden iniciar sin los identificadores estándar y no se rellenarán automáticamente.</span><span class="sxs-lookup"><span data-stu-id="583e2-148">Graphical user interface (GUI) applications can be started without the standard handles and they will not be automatically filled.</span></span>

## <a name="examples"></a><span data-ttu-id="583e2-149">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="583e2-149">Examples</span></span>

<span data-ttu-id="583e2-150">Para un ejemplo, vea [Lectura de eventos de búfer de entrada](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="583e2-150">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="583e2-151">Requisitos</span><span class="sxs-lookup"><span data-stu-id="583e2-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="583e2-152">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="583e2-152">Minimum supported client</span></span> | <span data-ttu-id="583e2-153">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="583e2-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="583e2-154">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="583e2-154">Minimum supported server</span></span> | <span data-ttu-id="583e2-155">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="583e2-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="583e2-156">Encabezado</span><span class="sxs-lookup"><span data-stu-id="583e2-156">Header</span></span> | <span data-ttu-id="583e2-157">ProcessEnv.h (via Winbase.h, include Windows.h)</span><span class="sxs-lookup"><span data-stu-id="583e2-157">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="583e2-158">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="583e2-158">Library</span></span> | <span data-ttu-id="583e2-159">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="583e2-159">Kernel32.lib</span></span> |
| <span data-ttu-id="583e2-160">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="583e2-160">DLL</span></span> | <span data-ttu-id="583e2-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="583e2-161">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="583e2-162">Vea también</span><span class="sxs-lookup"><span data-stu-id="583e2-162">See also</span></span>

[<span data-ttu-id="583e2-163">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="583e2-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="583e2-164">Identificadores de consola</span><span class="sxs-lookup"><span data-stu-id="583e2-164">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="583e2-165">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="583e2-165">**CreateFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-createfilea)

[<span data-ttu-id="583e2-166">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="583e2-166">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="583e2-167">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="583e2-167">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="583e2-168">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="583e2-168">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="583e2-169">**SetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="583e2-169">**SetStdHandle**</span></span>](setstdhandle.md)

[<span data-ttu-id="583e2-170">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="583e2-170">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="583e2-171">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="583e2-171">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)