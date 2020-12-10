---
title: Función SetConsoleCtrlHandler
description: Agrega o quita una función HandlerRoutine definida por la aplicación de la lista de funciones de controlador para el proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/SetConsoleCtrlHandler
- wincon/SetConsoleCtrlHandler
- SetConsoleCtrlHandler
MS-HAID:
- '\_win32\_setconsolectrlhandler'
- base.setconsolectrlhandler
- consoles.setconsolectrlhandler
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6fc64265-1403-45ea-925c-c5eb31d56734
topic_type:
- apiref
api_name:
- SetConsoleCtrlHandler
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 208eebc92b718fed9856a48dfaf5cbebdaddc1e1
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420274"
---
# <a name="setconsolectrlhandler-function"></a><span data-ttu-id="30e71-104">Función SetConsoleCtrlHandler</span><span class="sxs-lookup"><span data-stu-id="30e71-104">SetConsoleCtrlHandler function</span></span>

<span data-ttu-id="30e71-105">Agrega o quita una función [**HandlerRoutine**](handlerroutine.md) definida por la aplicación de la lista de funciones de controlador para el proceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="30e71-105">Adds or removes an application-defined [**HandlerRoutine**](handlerroutine.md) function from the list of handler functions for the calling process.</span></span>

<span data-ttu-id="30e71-106">Si no se especifica ninguna función de controlador, la función establece un atributo heredable que determina si el proceso de llamada ignora las señales de <kbd>CTRL</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="30e71-106">If no handler function is specified, the function sets an inheritable attribute that determines whether the calling process ignores <kbd>CTRL</kbd>+<kbd>C</kbd> signals.</span></span>

## <a name="syntax"></a><span data-ttu-id="30e71-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="30e71-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

## <a name="parameters"></a><span data-ttu-id="30e71-108">Parámetros</span><span class="sxs-lookup"><span data-stu-id="30e71-108">Parameters</span></span>

<span data-ttu-id="30e71-109">*HandlerRoutine* \[in, opcional\]</span><span class="sxs-lookup"><span data-stu-id="30e71-109">*HandlerRoutine* \[in, optional\]</span></span>  
<span data-ttu-id="30e71-110">Puntero a la función [**HandlerRoutine**](handlerroutine.md) definida por la aplicación que se va a agregar o quitar.</span><span class="sxs-lookup"><span data-stu-id="30e71-110">A pointer to the application-defined [**HandlerRoutine**](handlerroutine.md) function to be added or removed.</span></span> <span data-ttu-id="30e71-111">Este parámetro puede ser **NULL**.</span><span class="sxs-lookup"><span data-stu-id="30e71-111">This parameter can be **NULL**.</span></span>

<span data-ttu-id="30e71-112">*Add* \[in\]</span><span class="sxs-lookup"><span data-stu-id="30e71-112">*Add* \[in\]</span></span>  
<span data-ttu-id="30e71-113">Si este parámetro es **TRUE**, se agrega el controlador; si es **FALSE**, se quita el controlador.</span><span class="sxs-lookup"><span data-stu-id="30e71-113">If this parameter is **TRUE**, the handler is added; if it is **FALSE**, the handler is removed.</span></span>

<span data-ttu-id="30e71-114">Si el parámetro *HandlerRoutine* es **NULL**, un valor **TRUE** provoca que el proceso de llamada ignore la entrada <kbd>CTRL</kbd>+<kbd>C</kbd>. Un valor **FALSE** restaura el procesamiento normal de la entrada <kbd>CTRL</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="30e71-114">If the *HandlerRoutine* parameter is **NULL**, a **TRUE** value causes the calling process to ignore <kbd>CTRL</kbd>+<kbd>C</kbd> input, and a **FALSE** value restores normal processing of <kbd>CTRL</kbd>+<kbd>C</kbd> input.</span></span> <span data-ttu-id="30e71-115">Los procesos secundarios heredan este atributo de ignorar o procesar <kbd>CTRL</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="30e71-115">This attribute of ignoring or processing <kbd>CTRL</kbd>+<kbd>C</kbd> is inherited by child processes.</span></span>

## <a name="return-value"></a><span data-ttu-id="30e71-116">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="30e71-116">Return value</span></span>

<span data-ttu-id="30e71-117">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="30e71-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="30e71-118">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="30e71-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="30e71-119">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="30e71-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="30e71-120">Comentarios</span><span class="sxs-lookup"><span data-stu-id="30e71-120">Remarks</span></span>

<span data-ttu-id="30e71-121">Esta función proporciona una notificación similar a la aplicación de consola y los servicios que [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) proporciona para aplicaciones gráficas con un bombeo de mensajes.</span><span class="sxs-lookup"><span data-stu-id="30e71-121">This function provides a similar notification for console application and services that [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) provides for graphical applications with a message pump.</span></span> <span data-ttu-id="30e71-122">También puede usar esta función desde una aplicación gráfica, pero no hay ninguna garantía de que llegue antes de la notificación de **WM\_QUERYENDSESSION**.</span><span class="sxs-lookup"><span data-stu-id="30e71-122">You could also use this function from a graphical application, but there is no guarantee it would arrive before the notification from **WM\_QUERYENDSESSION**.</span></span>

<span data-ttu-id="30e71-123">Cada proceso de consola tiene su propia lista de funciones [**HandlerRoutine**](handlerroutine.md) definidas por la aplicación que controlan las señales de <kbd>CTRL</kbd>+<kbd>C</kbd> y <kbd>CTRL</kbd>+<kbd>BREAK</kbd>.</span><span class="sxs-lookup"><span data-stu-id="30e71-123">Each console process has its own list of application-defined [**HandlerRoutine**](handlerroutine.md) functions that handle <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> signals.</span></span> <span data-ttu-id="30e71-124">Las funciones de controlador también controlan las señales generadas por el sistema cuando el usuario cierra la consola, cierra sesión o apaga el sistema.</span><span class="sxs-lookup"><span data-stu-id="30e71-124">The handler functions also handle signals generated by the system when the user closes the console, logs off, or shuts down the system.</span></span> <span data-ttu-id="30e71-125">Inicialmente, la lista de controladores para cada proceso solo contiene una función de controlador predeterminada que llama a la función [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658).</span><span class="sxs-lookup"><span data-stu-id="30e71-125">Initially, the handler list for each process contains only a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function.</span></span> <span data-ttu-id="30e71-126">Un proceso de consola agrega o quita funciones de controlador adicionales mediante una llamada a la función **SetConsoleCtrlHandler**, que no afecta a la lista de funciones de controlador para otros procesos.</span><span class="sxs-lookup"><span data-stu-id="30e71-126">A console process adds or removes additional handler functions by calling the **SetConsoleCtrlHandler** function, which does not affect the list of handler functions for other processes.</span></span> <span data-ttu-id="30e71-127">Cuando un proceso de consola recibe alguna de las señales de control, se llama a sus funciones de controlador en función del último registro y la primera llamada, hasta que uno de los controladores devuelve `TRUE`.</span><span class="sxs-lookup"><span data-stu-id="30e71-127">When a console process receives any of the control signals, its handler functions are called on a last-registered, first-called basis until one of the handlers returns `TRUE`.</span></span> <span data-ttu-id="30e71-128">Si ninguno de los controladores devuelve `TRUE`, se llama al controlador predeterminado.</span><span class="sxs-lookup"><span data-stu-id="30e71-128">If none of the handlers returns `TRUE`, the default handler is called.</span></span>

<span data-ttu-id="30e71-129">En el caso de los procesos de consola, normalmente las combinaciones de teclas <kbd>CTRL</kbd>+<kbd>C</kbd> y <kbd>CTRL</kbd>+<kbd>BREAK</kbd> se tratan como señales (**CTRL\_C\_EVENT** y **CTRL\_BREAK\_EVENT**).</span><span class="sxs-lookup"><span data-stu-id="30e71-129">For console processes, the <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations are typically treated as signals (**CTRL\_C\_EVENT** and **CTRL\_BREAK\_EVENT**).</span></span> <span data-ttu-id="30e71-130">Cuando una ventana de consola con el foco de teclado recibe <kbd>CTRL</kbd>+<kbd>C</kbd> o <kbd>CTRL</kbd>+<kbd>BREAK</kbd>, normalmente la señal se pasa a todos los procesos que comparten esa consola.</span><span class="sxs-lookup"><span data-stu-id="30e71-130">When a console window with the keyboard focus receives <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd>, the signal is typically passed to all processes sharing that console.</span></span>

<span data-ttu-id="30e71-131"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> se trata siempre como una señal, pero un comportamiento típico de <kbd>CTRL</kbd>+<kbd>C</kbd> se puede cambiar de tres maneras que impidan que se llame a las funciones del controlador:</span><span class="sxs-lookup"><span data-stu-id="30e71-131"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but typical <kbd>CTRL</kbd>+<kbd>C</kbd> behavior can be changed in three ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="30e71-132">La función [**SetConsoleMode**](setconsolemode.md) puede deshabilitar el modo **ENABLE\_PROCESSED\_INPUT** para el búfer de entrada de una consola, por lo que <kbd>CTRL</kbd>+<kbd>C</kbd> se indica como entrada del teclado en lugar de como una señal.</span><span class="sxs-lookup"><span data-stu-id="30e71-132">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** mode for a console's input buffer, so <kbd>CTRL</kbd>+<kbd>C</kbd> is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="30e71-133">La llamada a **SetConsoleCtrlHandler** con los argumentos **NULL** y **TRUE** hace que el proceso de llamada ignore las señales de <kbd>CTRL</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="30e71-133">Calling **SetConsoleCtrlHandler** with the **NULL** and **TRUE** arguments causes the calling process to ignore <kbd>CTRL</kbd>+<kbd>C</kbd> signals.</span></span> <span data-ttu-id="30e71-134">Los procesos secundarios heredan este atributo, pero puede habilitarse o deshabilitarse en cualquier proceso sin que ello afecte a los procesos existentes.</span><span class="sxs-lookup"><span data-stu-id="30e71-134">This attribute is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>
- <span data-ttu-id="30e71-135">Si se está depurando un proceso de consola y no se han deshabilitado las señales de <kbd>CTRL</kbd>+<kbd>C</kbd>, el sistema genera una excepción **DBG\_CONTROL\_C**.</span><span class="sxs-lookup"><span data-stu-id="30e71-135">If a console process is being debugged and <kbd>CTRL</kbd>+<kbd>C</kbd> signals have not been disabled, the system generates a **DBG\_CONTROL\_C** exception.</span></span> <span data-ttu-id="30e71-136">Esta excepción solo se produce en beneficio del depurador y una aplicación nunca debe utilizar un controlador de excepciones para tratarla.</span><span class="sxs-lookup"><span data-stu-id="30e71-136">This exception is raised only for the benefit of the debugger, and an application should never use an exception handler to deal with it.</span></span> <span data-ttu-id="30e71-137">Si el depurador controla la excepción, una aplicación no tendrá en cuenta <kbd>CTRL</kbd>+<kbd>C</kbd>, con una excepción: se terminarán las esperas que generan alertas.</span><span class="sxs-lookup"><span data-stu-id="30e71-137">If the debugger handles the exception, an application will not notice the <kbd>CTRL</kbd>+<kbd>C</kbd>, with one exception: alertable waits will terminate.</span></span> <span data-ttu-id="30e71-138">Si el depurador pasa la excepción como no controlada, <kbd>CTRL</kbd>+<kbd>C</kbd> se pasa al proceso de consola y se trata como una señal, como se explicó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="30e71-138">If the debugger passes the exception on unhandled, <kbd>CTRL</kbd>+<kbd>C</kbd> is passed to the console process and treated as a signal, as previously discussed.</span></span>

<span data-ttu-id="30e71-139">Un proceso de consola puede usar la función [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) para enviar una señal de <kbd>CTRL</kbd>+<kbd>C</kbd> o <kbd>CTRL</kbd>+<kbd>BREAK</kbd> a un grupo de procesos de consola.</span><span class="sxs-lookup"><span data-stu-id="30e71-139">A console process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> signal to a console process group.</span></span>

<span data-ttu-id="30e71-140">El sistema genera señales de **CTRL\_CLOSE\_EVENT**, **CTRL\_LOGOFF\_EVENT** y **CTRL\_SHUTDOWN\_EVENT** cuando el usuario cierra la consola, cierra sesión o apaga el sistema para que el proceso tenga una oportunidad de limpiarse antes de que finalice.</span><span class="sxs-lookup"><span data-stu-id="30e71-140">The system generates **CTRL\_CLOSE\_EVENT**, **CTRL\_LOGOFF\_EVENT**, and **CTRL\_SHUTDOWN\_EVENT** signals when the user closes the console, logs off, or shuts down the system so that the process has an opportunity to clean up before termination.</span></span> <span data-ttu-id="30e71-141">Es posible que las funciones de consola o cualquier función en tiempo de ejecución de C que llame a funciones de consola no funcionen de forma confiable durante el procesamiento de cualquiera de las tres señales mencionadas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="30e71-141">Console functions, or any C run-time functions that call console functions, may not work reliably during processing of any of the three signals mentioned previously.</span></span> <span data-ttu-id="30e71-142">El motivo es que es posible que se haya llamado a algunas o todas las rutinas de limpieza internas de la consola antes de ejecutar el controlador de la señal de proceso.</span><span class="sxs-lookup"><span data-stu-id="30e71-142">The reason is that some or all of the internal console cleanup routines may have been called before executing the process signal handler.</span></span>

<span data-ttu-id="30e71-143">**Windows 7, Windows 8, Windows 8.1 y Windows 10:**</span><span class="sxs-lookup"><span data-stu-id="30e71-143">**Windows 7, Windows 8, Windows 8.1 and Windows 10:**</span></span>

<span data-ttu-id="30e71-144">Si una aplicación de consola carga la biblioteca gdi32.dll o user32.dll, no se llama a la función [**HandlerRoutine**](handlerroutine.md) que se especifica cuando se llama a **SetConsoleCtrlHandler** para los eventos **CTRL\_LOGOFF\_EVENT** y **CTRL\_SHUTDOWN\_EVENT**.</span><span class="sxs-lookup"><span data-stu-id="30e71-144">If a console application loads the gdi32.dll or user32.dll library, the [**HandlerRoutine**](handlerroutine.md) function that you specify when you call **SetConsoleCtrlHandler** does not get called for the **CTRL\_LOGOFF\_EVENT** and **CTRL\_SHUTDOWN\_EVENT** events.</span></span> <span data-ttu-id="30e71-145">El sistema operativo reconoce los procesos que cargan gdi32.dll o user32.dll como aplicaciones Windows en lugar de aplicaciones de consola.</span><span class="sxs-lookup"><span data-stu-id="30e71-145">The operating system recognizes processes that load gdi32.dll or user32.dll as Windows applications rather than console applications.</span></span> <span data-ttu-id="30e71-146">Este comportamiento también se produce en las aplicaciones de consola que no llaman directamente a las funciones de gdi32.dll o user32.dll, sino que llaman a funciones como [funciones de Shell](https://msdn.microsoft.com/library/windows/desktop/bb776426) que, a su vez, llaman a funciones de gdi32.dll o user32.dll.</span><span class="sxs-lookup"><span data-stu-id="30e71-146">This behavior also occurs for console applications that do not call functions in gdi32.dll or user32.dll directly, but do call functions such as [Shell functions](https://msdn.microsoft.com/library/windows/desktop/bb776426) that do in turn call functions in gdi32.dll or user32.dll.</span></span>

<span data-ttu-id="30e71-147">Para recibir eventos cuando un usuario cierra sesión o el dispositivo se apaga en estas circunstancias, cree una ventana oculta en la aplicación de consola y, a continuación, controle los mensajes de la ventana [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) y [**WM\_ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) que recibe la ventana oculta.</span><span class="sxs-lookup"><span data-stu-id="30e71-147">To receive events when a user signs out or the device shuts down in these circumstances, create a hidden window in your console application, and then handle the [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) and [**WM\_ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) window messages that the hidden window receives.</span></span> <span data-ttu-id="30e71-148">Para crear una ventana oculta, llame al método [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) con el parámetro *dwExStyle* establecido en 0.</span><span class="sxs-lookup"><span data-stu-id="30e71-148">You can create a hidden window by calling the [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) method with the *dwExStyle* parameter set to 0.</span></span>

## <a name="examples"></a><span data-ttu-id="30e71-149">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="30e71-149">Examples</span></span>

<span data-ttu-id="30e71-150">Por ejemplo, consulte [Registro de una función de identificador de control](registering-a-control-handler-function.md).</span><span class="sxs-lookup"><span data-stu-id="30e71-150">For an example, see [Registering a Control Handler Function](registering-a-control-handler-function.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="30e71-151">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30e71-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="30e71-152">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="30e71-152">Minimum supported client</span></span> | <span data-ttu-id="30e71-153">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="30e71-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="30e71-154">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="30e71-154">Minimum supported server</span></span> | <span data-ttu-id="30e71-155">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="30e71-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="30e71-156">Encabezado</span><span class="sxs-lookup"><span data-stu-id="30e71-156">Header</span></span> | <span data-ttu-id="30e71-157">ConsoleApi.h (a través de WinCon.h, incluido Windows.h)</span><span class="sxs-lookup"><span data-stu-id="30e71-157">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="30e71-158">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="30e71-158">Library</span></span> | <span data-ttu-id="30e71-159">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="30e71-159">Kernel32.lib</span></span> |
| <span data-ttu-id="30e71-160">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="30e71-160">DLL</span></span> | <span data-ttu-id="30e71-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="30e71-161">Kernel32.dll</span></span> |
| <span data-ttu-id="30e71-162">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="30e71-162">Unicode and ANSI names</span></span> | |

## <a name="see-also"></a><span data-ttu-id="30e71-163">Vea también</span><span class="sxs-lookup"><span data-stu-id="30e71-163">See also</span></span>

[<span data-ttu-id="30e71-164">Identificadores de control de la consola</span><span class="sxs-lookup"><span data-stu-id="30e71-164">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="30e71-165">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="30e71-165">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="30e71-166">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="30e71-166">**ExitProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[<span data-ttu-id="30e71-167">**GenerateConsoleCtrlEvent**</span><span class="sxs-lookup"><span data-stu-id="30e71-167">**GenerateConsoleCtrlEvent**</span></span>](generateconsolectrlevent.md)

[<span data-ttu-id="30e71-168">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="30e71-168">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="30e71-169">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="30e71-169">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="30e71-170">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="30e71-170">**SetConsoleMode**</span></span>](setconsolemode.md)
