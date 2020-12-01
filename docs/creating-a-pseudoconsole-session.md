---
title: Creación de una sesión de Pseudoconsole
description: Una sesión de pseudoconsole permitirá que una aplicación hospede las actividades de una aplicación en modo de carácter.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola, conpty, pseudoconsole, Windows PTY, pseudo Console
ms.localizationpriority: high
ms.openlocfilehash: 8cd057d3e74659fdeff6c569ddb053c881af1de8
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420234"
---
# <a name="creating-a-pseudoconsole-session"></a><span data-ttu-id="b1ff3-104">Creación de una sesión de Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="b1ff3-104">Creating a Pseudoconsole session</span></span>

<span data-ttu-id="b1ff3-105">La Pseudoconsole de Windows, que a veces también se conoce como pseudo Console, ConPTY o Windows PTY, es un mecanismo diseñado para crear un host externo para actividades de subsistema en modo de carácter que reemplazan la parte de interactividad del usuario de la ventana host de consola predeterminada.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-105">The Windows Pseudoconsole, sometimes also referred to as pseudo console, ConPTY, or the Windows PTY, is a mechanism designed for creating an external host for character-mode subsystem activities that replace the user interactivity portion of the default console host window.</span></span>

<span data-ttu-id="b1ff3-106">Hospedar una sesión de pseudoconsole es un poco diferente de una sesión de consola tradicional.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-106">Hosting a pseudoconsole session is a bit different than a traditional console session.</span></span> <span data-ttu-id="b1ff3-107">Las sesiones de consola tradicionales se inician automáticamente cuando el sistema operativo reconoce que una aplicación en modo de caracteres está a punto de ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-107">Traditional console sessions automatically start when the operating system recognizes that a character-mode application is about to run.</span></span> <span data-ttu-id="b1ff3-108">Por el contrario, una sesión de pseudoconsole y los canales de comunicación deben ser creados por la aplicación de hospedaje antes de crear el proceso con la aplicación de modo de carácter secundario que se va a hospedar.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-108">In contrast, a pseudoconsole session and the communication channels need to be created by the hosting application prior to creating the process with the child character-mode application to be hosted.</span></span> <span data-ttu-id="b1ff3-109">El proceso secundario se seguirá creando con la función [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) , pero con cierta información adicional que dirigirá al sistema operativo para establecer el entorno adecuado.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-109">The child process will still be created using the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function, but with some additional information that will direct the operating system to establish the appropriate environment.</span></span>

<span data-ttu-id="b1ff3-110">Puede encontrar información general adicional acerca de este sistema en la [entrada de blog del anuncio inicial](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span><span class="sxs-lookup"><span data-stu-id="b1ff3-110">You can find additional background information about this system on the [initial announcement blog post](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span></span>

<span data-ttu-id="b1ff3-111">Puede encontrar ejemplos completos del uso de Pseudoconsole en nuestro repositorio de GitHub [Microsoft/Terminal](https://github.com/microsoft/terminal) en el directorio Samples.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-111">Complete examples of using the Pseudoconsole are available on our GitHub repository [microsoft/terminal](https://github.com/microsoft/terminal) in the samples directory.</span></span>

## <a name="preparing-the-communication-channels"></a><span data-ttu-id="b1ff3-112">Preparación de los canales de comunicación</span><span class="sxs-lookup"><span data-stu-id="b1ff3-112">Preparing the communication channels</span></span>

<span data-ttu-id="b1ff3-113">El primer paso consiste en crear un par de canales de comunicación sincrónicos que se proporcionarán durante la creación de la sesión de pseudoconsole para la comunicación bidireccional con la aplicación hospedada.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-113">The first step is to create a pair of synchronous communication channels that will be provided during creation of the pseudoconsole session for bidirectional communication with the hosted application.</span></span> <span data-ttu-id="b1ff3-114">El sistema pseudoconsole procesa estos canales usando [**readfile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) y [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) con [e/s sincrónicas](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output).</span><span class="sxs-lookup"><span data-stu-id="b1ff3-114">These channels are processed by the pseudoconsole system using [**ReadFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) and [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) with [synchronous I/O](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output).</span></span> <span data-ttu-id="b1ff3-115">Los identificadores de archivo o de dispositivo de e/s, como una secuencia de archivos o una canalización, son aceptables, siempre que no se requiera una estructura [**superpuesta**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) para la comunicación asincrónica.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-115">File or I/O device handles like a file stream or pipe are acceptable as long as an [**OVERLAPPED**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) structure is not required for asynchronous communication.</span></span>

> [!WARNING]
><span data-ttu-id="b1ff3-116">Para evitar las condiciones de carrera y los interbloqueos, recomendamos encarecidamente que cada uno de los canales de comunicación se represente en un subproceso independiente que mantenga su propio estado de búfer de cliente y cola de mensajes dentro de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-116">To prevent race conditions and deadlocks, we highly recommend that each of the communication channels is serviced on a separate thread that maintains its own client buffer state and messaging queue inside your application.</span></span> <span data-ttu-id="b1ff3-117">El mantenimiento de todas las actividades de pseudoconsole en el mismo subproceso puede dar lugar a un interbloqueo donde se llena uno de los búferes de comunicaciones y a esperar a que se produzca una acción mientras se intenta enviar una solicitud de bloqueo en otro canal.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-117">Servicing all of the pseudoconsole activities on the same thread may result in a deadlock where one of the communications buffers is filled and waiting for your action while you attempt to dispatch a blocking request on another channel.</span></span>

## <a name="creating-the-pseudoconsole"></a><span data-ttu-id="b1ff3-118">Crear Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="b1ff3-118">Creating the Pseudoconsole</span></span>

<span data-ttu-id="b1ff3-119">Con los canales de comunicación que se han establecido, identifique el extremo "lectura" del canal de entrada y el extremo "escritura" del canal de salida.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-119">With the communications channels that have been established, identify the "read" end of the input channel and the "write" end of the output channel.</span></span> <span data-ttu-id="b1ff3-120">Este par de identificadores se proporciona al llamar a [**CreatePseudoConsole**](createpseudoconsole.md) para crear el objeto.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-120">This pair of handles is provided on calling [**CreatePseudoConsole**](createpseudoconsole.md) to create the object.</span></span>

<span data-ttu-id="b1ff3-121">Al crearse, se requiere un tamaño que represente las dimensiones X e y (en el recuento de caracteres).</span><span class="sxs-lookup"><span data-stu-id="b1ff3-121">On creation, a size representing the X and Y dimensions (in count of characters) is required.</span></span> <span data-ttu-id="b1ff3-122">Estas son las dimensiones que se aplicarán a la superficie de visualización de la ventana de presentación final (terminal).</span><span class="sxs-lookup"><span data-stu-id="b1ff3-122">These are the dimensions that will apply to the display surface for the final (terminal) presentation window.</span></span> <span data-ttu-id="b1ff3-123">Los valores se utilizan para crear un búfer en memoria dentro del sistema pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-123">The values are used to create an in-memory buffer inside the pseudoconsole system.</span></span>

<span data-ttu-id="b1ff3-124">El tamaño de búfer proporciona respuestas a las aplicaciones de modo de carácter de cliente que sondean la información con las funciones de la [consola del lado cliente](console-functions.md) como [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) y dictan el diseño y el posicionamiento del texto cuando los clientes usan funciones como [**WriteConsoleOutput**](writeconsoleoutput.md).</span><span class="sxs-lookup"><span data-stu-id="b1ff3-124">The buffer size provide answers to client character-mode applications that probe for information using the [client-side console functions](console-functions.md) like [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) and dictates the layout and positioning of text when clients use functions like [**WriteConsoleOutput**](writeconsoleoutput.md).</span></span>

<span data-ttu-id="b1ff3-125">Por último, se proporciona un campo Flags en la creación de un pseudoconsole para llevar a cabo una funcionalidad especial.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-125">Finally, a flags field is provided on creation of a pseudoconsole to perform special functionality.</span></span> <span data-ttu-id="b1ff3-126">De forma predeterminada, establezca esta opción en 0 para que no tenga ninguna funcionalidad especial.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-126">By default, set this to 0 to have no special functionality.</span></span>

<span data-ttu-id="b1ff3-127">En este momento, solo hay una marca especial disponible para solicitar la herencia de la posición del cursor desde una sesión de consola ya conectada al llamador de la API de pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-127">At this time, only one special flag is available to request the inheritence of the cursor position from a console session already attached to the caller of the pseudoconsole API.</span></span> <span data-ttu-id="b1ff3-128">Esto está pensado para su uso en escenarios más avanzados donde una aplicación de hospedaje que está preparando una sesión de pseudoconsole también es una aplicación de modo de carácter de cliente de otro entorno de consola.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-128">This is intended for use in more advanced scenarios where a hosting application that is preparing a pseudoconsole session is itself also a client character-mode application of a another console environment.</span></span>

<span data-ttu-id="b1ff3-129">A continuación se proporciona un fragmento de código de ejemplo que usa [**CreatePipe**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) para establecer un par de canales de comunicación y crear el pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-129">A sample snippet is provided below utilizing [**CreatePipe**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) to establish a pair of communication channels and create the pseudoconsole.</span></span>

```C

HRESULT SetUpPseudoConsole(COORD size)
{
    HRESULT hr = S_OK;

    // Create communication channels

    // - Close these after CreateProcess of child application with pseudoconsole object.
    HANDLE inputReadSide, outputWriteSide;

    // - Hold onto these and use them for communication with the child through the pseudoconsole.
    HANDLE outputReadSide, inputWriteSide;

    if (!CreatePipe(&inputReadSide, &inputWriteSide, NULL, 0))
    {
        return HRESULT_FROM_WIN32(GetLastError());
    }

    if (!CreatePipe(&outputReadSide, &outputWriteSide, NULL, 0))
    {
        return HRESULT_FROM_WIN32(GetLastError());
    }

    HPCON hPC;
    hr = CreatePseudoConsole(size, inputReadSide, outputWriteSide, 0, &hPC);
    if (FAILED(hr))
    {
        return hr;
    }

    // ...

}
```

> [!NOTE]
><span data-ttu-id="b1ff3-130">Este fragmento de código está incompleto y se usa solo para la demostración de esta llamada específica.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-130">This snippet is incomplete and used for demonstration of this specific call only.</span></span> <span data-ttu-id="b1ff3-131">Deberá administrar la duración del **identificador** de forma adecuada.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-131">You will need to manage the lifetime of the **HANDLE** s appropriately.</span></span> <span data-ttu-id="b1ff3-132">Si no se puede administrar correctamente la duración de los **Controladores**, se pueden producir escenarios de interbloqueo, especialmente con llamadas de e/s sincrónicas.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-132">Failure to manage the lifetime of **HANDLE** s correctly can result in deadlock scenarios, especially with synchronous I/O calls.</span></span>

<span data-ttu-id="b1ff3-133">Tras la finalización de la llamada [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) para crear la aplicación de modo de caracteres de cliente conectada a pseudoconsole, los identificadores proporcionados durante la creación se deben liberar de este proceso.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-133">Upon completion of the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) call to create the client character-mode application attached to the pseudoconsole, the handles given during creation should be freed from this process.</span></span> <span data-ttu-id="b1ff3-134">Esto reducirá el recuento de referencias en el objeto de dispositivo subyacente y permitirá a las operaciones de e/s detectar correctamente un canal roto cuando la sesión pseudoconsole cierre su copia de los identificadores.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-134">This will decrease the reference count on the underlying device object and allow I/O operations to properly detect a broken channel when the pseudoconsole session closes its copy of the handles.</span></span>

## <a name="preparing-for-creation-of-the-child-process"></a><span data-ttu-id="b1ff3-135">Preparación para la creación del proceso secundario</span><span class="sxs-lookup"><span data-stu-id="b1ff3-135">Preparing for Creation of the Child Process</span></span>

<span data-ttu-id="b1ff3-136">La siguiente fase consiste en preparar la estructura [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) que va a transmitir la información de pseudoconsole al iniciar el proceso secundario.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-136">The next phase is to prepare the [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure that will convey the pseudoconsole information while starting the child process.</span></span>

<span data-ttu-id="b1ff3-137">Esta estructura contiene la capacidad de proporcionar información de inicio compleja, incluidos los atributos para la creación de procesos y subprocesos.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-137">This structure contains the ability to provide complex startup information including attributes for process and thread creation.</span></span>

<span data-ttu-id="b1ff3-138">Use [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) en un modo de doble llamada para calcular primero el número de bytes necesarios para contener la lista, asignar la memoria solicitada y, a continuación, llamar de nuevo al puntero de memoria opaca para que se configure como la lista de atributos.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-138">Use [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) in a double-call fashion to first calculate the number of bytes required to hold the list, allocate the memory requested, then call again providing the opaque memory pointer to have it set up as the attribute list.</span></span>

<span data-ttu-id="b1ff3-139">A continuación, llame a [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) pasando la lista de atributos inicializada con la marca **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, el identificador PSEUDOCONSOLE y el tamaño del identificador PSEUDOCONSOLE.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-139">Next, call [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) passing the initialized attribute list with the flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, the pseudoconsole handle, and the size of the pseudoconsole handle.</span></span>

```C

HRESULT PrepareStartupInformation(HPCON hpc, STARTUPINFOEX* psi)
{
    // Prepare Startup Information structure
    STARTUPINFOEX si;
    ZeroMemory(&si, sizeof(si));
    si.StartupInfo.cb = sizeof(STARTUPINFOEX);

    // Discover the size required for the list
    size_t bytesRequired;
    InitializeProcThreadAttributeList(NULL, 1, 0, &bytesRequired);

    // Allocate memory to represent the list
    si.lpAttributeList = (PPROC_THREAD_ATTRIBUTE_LIST)HeapAlloc(GetProcessHeap(), 0, bytesRequired);
    if (!si.lpAttributeList)
    {
        return E_OUTOFMEMORY;
    }

    // Initialize the list memory location
    if (!InitializeProcThreadAttributeList(si.lpAttributeList, 1, 0, &bytesRequired))
    {
        HeapFree(GetProcessHeap(), 0, si.lpAttributeList);
        return HRESULT_FROM_WIN32(GetLastError());
    }

    // Set the pseudoconsole information into the list
    if (!UpdateProcThreadAttribute(attributeList,
                                   0,
                                   PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE,
                                   hpc,
                                   sizeof(hpc),
                                   NULL,
                                   NULL))
    {
        HeapFree(GetProcessHeap(), 0, si.lpAttributeList);
        return HRESULT_FROM_WIN32(GetLastError());
    }

    *psi = si;

    return S_OK;
}

```

## <a name="creating-the-hosted-process"></a><span data-ttu-id="b1ff3-140">Crear el proceso hospedado</span><span class="sxs-lookup"><span data-stu-id="b1ff3-140">Creating the Hosted Process</span></span>

<span data-ttu-id="b1ff3-141">A continuación, llame a [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) pasando la estructura [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) junto con la ruta de acceso al archivo ejecutable y cualquier información de configuración adicional, si procede.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-141">Next, call [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) passing the [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure along with the path to the executable and any additional configuration information if applicable.</span></span> <span data-ttu-id="b1ff3-142">Es importante establecer la marca de **EXTENDED_STARTUPINFO_PRESENT** al llamar a para avisar al sistema de que la referencia de pseudoconsole está contenida en la información extendida.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-142">It is important to set the **EXTENDED_STARTUPINFO_PRESENT** flag when calling to alert the system that the pseudoconsole reference is contained in the extended information.</span></span>

```C
HRESULT SetUpPseudoConsole(COORD size)
{
    // ...

    PCWSTR childApplication = L"C:\\windows\\system32\\cmd.exe";

    // Create mutable text string for CreateProcessW command line string.
    const size_t charsRequired = wcslen(childApplication) + 1; // +1 null terminator
    PWSTR cmdLineMutable = (PWSTR)HeapAlloc(GetProcessHeap(), 0, sizeof(wchar_t) * charsRequired);

    if (!cmdLineMutable)
    {
        return E_OUTOFMEMORY;
    }

    wcscpy_s(cmdLineMutable, bytesRequired, childApplication);

    PROCESS_INFORMATION pi;
    ZeroMemory(&pi, sizeof(pi));

    // Call CreateProcess
    if (!CreateProcessW(NULL,
                        cmdLineMutable,
                        NULL,
                        NULL,
                        FALSE,
                        EXTENDED_STARTUPINFO_PRESENT,
                        NULL,
                        NULL,
                        &siEx.StartupInfo,
                        &pi))
    {
        HeapFree(GetProcessHeap(), 0, cmdLineMutable);
        return HRESULT_FROM_WIN32(GetLastError());
    }

    // ...
}
```

> [!NOTE]
> <span data-ttu-id="b1ff3-143">El cierre de la sesión de pseudoconsole mientras el proceso hospedado todavía se está iniciando y la conexión puede dar lugar a que la aplicación cliente muestre un cuadro de diálogo de error.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-143">Closing the pseudoconsole session while the hosted process is still starting up and connecting can result in an error dialog being shown by the client application.</span></span> <span data-ttu-id="b1ff3-144">Se muestra el mismo cuadro de diálogo de error si al proceso hospedado se le asigna un identificador de pseudoconsole no válido para el inicio.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-144">The same error dialog is shown if the hosted process is given an invalid pseudoconsole handle for startup.</span></span> <span data-ttu-id="b1ff3-145">En el código de inicialización del proceso hospedado, las dos circunstancias son idénticas.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-145">To the hosted process initialization code, the two circumstances are identical.</span></span> <span data-ttu-id="b1ff3-146">El cuadro de diálogo emergente de la aplicación cliente hospedada en caso de error se leerá `0xc0000142` con un mensaje localizado que detalla el error de inicialización.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-146">The pop-up dialog from the hosted client application on failure will read `0xc0000142` with a localized message detailing failure to initialize.</span></span>

## <a name="communicating-with-the-pseudoconsole-session"></a><span data-ttu-id="b1ff3-147">Comunicación con la sesión de Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="b1ff3-147">Communicating with the Pseudoconsole Session</span></span>

<span data-ttu-id="b1ff3-148">Una vez que el proceso se crea correctamente, la aplicación host puede usar el extremo de escritura de la canalización de entrada para enviar información de interacción con el usuario en el pseudoconsole y el extremo de lectura de la canalización de salida para recibir información de presentación gráfica de la pseudo consola.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-148">Once the process is created successfully, the hosting application can use the write end of the input pipe to send user interaction information into the pseudoconsole and the read end of the output pipe to receive graphical presentation information from the pseudo console.</span></span>

<span data-ttu-id="b1ff3-149">Es completamente la aplicación de hospedaje decidir cómo controlar la actividad adicional.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-149">It is completely up to the hosting application to decide how to handle further activity.</span></span> <span data-ttu-id="b1ff3-150">La aplicación de hospedaje podría iniciar una ventana en otro subproceso para recopilar la entrada de interacción del usuario y serializarla en el extremo de escritura de la canalización de entrada para el pseudoconsole y la aplicación de modo de carácter hospedada.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-150">The hosting application could launch a window in another thread to collect user interaction input and serialize it into the write end of the input pipe for the pseudoconsole and the hosted character-mode application.</span></span> <span data-ttu-id="b1ff3-151">Se puede iniciar otro subproceso para purgar el extremo de lectura de la canalización de salida de pseudoconsole, descodificar el texto y la información de la [secuencia de terminal virtual](console-virtual-terminal-sequences.md) y presentarlo en la pantalla.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-151">Another thread could be launched to drain the read end of the output pipe for the pseudoconsole, decode the text and [virtual terminal sequence](console-virtual-terminal-sequences.md) information, and present that to the screen.</span></span>

<span data-ttu-id="b1ff3-152">Los subprocesos también se pueden usar para retransmitir la información de los canales de pseudoconsole a otro canal o dispositivo, incluida una red para la información remota en otro proceso o equipo y para evitar cualquier transcodificación local de la información.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-152">Threads could also be used to relay the information from the pseudoconsole channels out to a different channel or device including a network to remote information to another process or machine and avoiding any local transcoding of the information.</span></span>

## <a name="resizing-the-pseudoconsole"></a><span data-ttu-id="b1ff3-153">Cambiar el tamaño de Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="b1ff3-153">Resizing the Pseudoconsole</span></span>

<span data-ttu-id="b1ff3-154">A lo largo del tiempo de ejecución, puede haber una circunstancia en la que se deba cambiar el tamaño del búfer debido a una interacción del usuario o a una solicitud que se reciba fuera de banda desde otro dispositivo de visualización o interacción.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-154">Throughout the course of runtime, there may be a circumstance by which the size of the buffer needs to be changed due to a user interaction or a request received out of band from another display/interaction device.</span></span>

<span data-ttu-id="b1ff3-155">Esto se puede hacer con la función [**ResizePseudoConsole**](resizepseudoconsole.md) que especifica el alto y el ancho del búfer en un recuento de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-155">This can be done with the [**ResizePseudoConsole**](resizepseudoconsole.md) function specifying both the height and width of the buffer in a count of characters.</span></span>

```C
// Theoretical event handler function with theoretical
// event that has associated display properties
// on Source property.
void OnWindowResize(Event e)
{
    // Retrieve width and height dimensions of display in
    // characters using theoretical height/width functions
    // that can retrieve the properties from the display
    // attached to the event.
    COORD size;
    size.X = GetViewWidth(e.Source);
    size.Y = GetViewHeight(e.Source);

    // Call pseudoconsole API to inform buffer dimension update
    ResizePseudoConsole(m_hpc, size);
}
```

## <a name="ending-the-pseudoconsole-session"></a><span data-ttu-id="b1ff3-156">Finalización de la sesión de Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="b1ff3-156">Ending the Pseudoconsole Session</span></span>

<span data-ttu-id="b1ff3-157">Para finalizar la sesión, llame a la función [**ClosePseudoConsole**](closepseudoconsole.md) con el identificador de la creación de pseudoconsole original.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-157">To end the session, call the [**ClosePseudoConsole**](closepseudoconsole.md) function with the handle from the original pseudoconsole creation.</span></span> <span data-ttu-id="b1ff3-158">Cualquier aplicación de modo de carácter de cliente adjunta, como la de la llamada [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) , se terminará cuando se cierre la sesión.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-158">Any attached client character-mode applications, such as the one from the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) call, will be terminated when the session is closed.</span></span> <span data-ttu-id="b1ff3-159">Si el elemento secundario original era una aplicación de tipo shell que crea otros procesos, también se terminarán todos los procesos asociados relacionados en el árbol.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-159">If the original child was a shell-type application that creates other processes, any related attached processes in the tree will also be terminated.</span></span>

> [!WARNING]
><span data-ttu-id="b1ff3-160">Cerrar la sesión tiene varios efectos secundarios que pueden dar lugar a una condición de interbloqueo si el pseudoconsole se usa en un modo sincrónico de un solo subproceso.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-160">Closing the session has several side effects which can result in a deadlock condition if the pseudoconsole is used in a single-threaded synchronous fashion.</span></span> <span data-ttu-id="b1ff3-161">La acción de cerrar la sesión pseudoconsole puede emitir una actualización de fotogramas finales en `hOutput` la que se debe purgar del búfer del canal de comunicaciones.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-161">The act of closing the pseudoconsole session may emit a final frame update to `hOutput` which should be drained from the communications channel buffer.</span></span> <span data-ttu-id="b1ff3-162">Además, si `PSEUDOCONSOLE_INHERIT_CURSOR` se seleccionó al crear el pseudoconsole, al intentar cerrar el pseudoconsole sin responder al mensaje de consulta de herencia de cursor (recibido en `hOutput` y respondiendo a través de `hInput` ) se puede producir otra condición de interbloqueo.</span><span class="sxs-lookup"><span data-stu-id="b1ff3-162">Additionally, if `PSEUDOCONSOLE_INHERIT_CURSOR` was selected while creating the pseudoconsole, attempting to close the pseudoconsole without responding to the cursor inheritence query message (received on `hOutput` and replied to via `hInput`) may result in another deadlock condition.</span></span> <span data-ttu-id="b1ff3-163">Se recomienda que los canales de comunicaciones para los pseudoconsole se representen en subprocesos individuales y se sigan purgando y procesando hasta que se interrumpa su propio acuerdo por la aplicación cliente o finalizando las actividades de destrucción en la llamada a la función [**ClosePseudoConsole**](closepseudoconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="b1ff3-163">It is recommended that communications channels for the pseudoconsole are serviced on individual threads and remain drained and processed until broken of their own accord by the client application exiting or by the completion of teardown activities in calling the [**ClosePseudoConsole**](closepseudoconsole.md) function.</span></span>
