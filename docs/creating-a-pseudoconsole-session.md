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
# <a name="creating-a-pseudoconsole-session"></a>Creación de una sesión de Pseudoconsole

La Pseudoconsole de Windows, que a veces también se conoce como pseudo Console, ConPTY o Windows PTY, es un mecanismo diseñado para crear un host externo para actividades de subsistema en modo de carácter que reemplazan la parte de interactividad del usuario de la ventana host de consola predeterminada.

Hospedar una sesión de pseudoconsole es un poco diferente de una sesión de consola tradicional. Las sesiones de consola tradicionales se inician automáticamente cuando el sistema operativo reconoce que una aplicación en modo de caracteres está a punto de ejecutarse. Por el contrario, una sesión de pseudoconsole y los canales de comunicación deben ser creados por la aplicación de hospedaje antes de crear el proceso con la aplicación de modo de carácter secundario que se va a hospedar. El proceso secundario se seguirá creando con la función [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) , pero con cierta información adicional que dirigirá al sistema operativo para establecer el entorno adecuado.

Puede encontrar información general adicional acerca de este sistema en la [entrada de blog del anuncio inicial](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).

Puede encontrar ejemplos completos del uso de Pseudoconsole en nuestro repositorio de GitHub [Microsoft/Terminal](https://github.com/microsoft/terminal) en el directorio Samples.

## <a name="preparing-the-communication-channels"></a>Preparación de los canales de comunicación

El primer paso consiste en crear un par de canales de comunicación sincrónicos que se proporcionarán durante la creación de la sesión de pseudoconsole para la comunicación bidireccional con la aplicación hospedada. El sistema pseudoconsole procesa estos canales usando [**readfile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) y [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) con [e/s sincrónicas](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output). Los identificadores de archivo o de dispositivo de e/s, como una secuencia de archivos o una canalización, son aceptables, siempre que no se requiera una estructura [**superpuesta**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) para la comunicación asincrónica.

> [!WARNING]
>Para evitar las condiciones de carrera y los interbloqueos, recomendamos encarecidamente que cada uno de los canales de comunicación se represente en un subproceso independiente que mantenga su propio estado de búfer de cliente y cola de mensajes dentro de la aplicación. El mantenimiento de todas las actividades de pseudoconsole en el mismo subproceso puede dar lugar a un interbloqueo donde se llena uno de los búferes de comunicaciones y a esperar a que se produzca una acción mientras se intenta enviar una solicitud de bloqueo en otro canal.

## <a name="creating-the-pseudoconsole"></a>Crear Pseudoconsole

Con los canales de comunicación que se han establecido, identifique el extremo "lectura" del canal de entrada y el extremo "escritura" del canal de salida. Este par de identificadores se proporciona al llamar a [**CreatePseudoConsole**](createpseudoconsole.md) para crear el objeto.

Al crearse, se requiere un tamaño que represente las dimensiones X e y (en el recuento de caracteres). Estas son las dimensiones que se aplicarán a la superficie de visualización de la ventana de presentación final (terminal). Los valores se utilizan para crear un búfer en memoria dentro del sistema pseudoconsole.

El tamaño de búfer proporciona respuestas a las aplicaciones de modo de carácter de cliente que sondean la información con las funciones de la [consola del lado cliente](console-functions.md) como [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) y dictan el diseño y el posicionamiento del texto cuando los clientes usan funciones como [**WriteConsoleOutput**](writeconsoleoutput.md).

Por último, se proporciona un campo Flags en la creación de un pseudoconsole para llevar a cabo una funcionalidad especial. De forma predeterminada, establezca esta opción en 0 para que no tenga ninguna funcionalidad especial.

En este momento, solo hay una marca especial disponible para solicitar la herencia de la posición del cursor desde una sesión de consola ya conectada al llamador de la API de pseudoconsole. Esto está pensado para su uso en escenarios más avanzados donde una aplicación de hospedaje que está preparando una sesión de pseudoconsole también es una aplicación de modo de carácter de cliente de otro entorno de consola.

A continuación se proporciona un fragmento de código de ejemplo que usa [**CreatePipe**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) para establecer un par de canales de comunicación y crear el pseudoconsole.

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
>Este fragmento de código está incompleto y se usa solo para la demostración de esta llamada específica. Deberá administrar la duración del **identificador** de forma adecuada. Si no se puede administrar correctamente la duración de los **Controladores**, se pueden producir escenarios de interbloqueo, especialmente con llamadas de e/s sincrónicas.

Tras la finalización de la llamada [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) para crear la aplicación de modo de caracteres de cliente conectada a pseudoconsole, los identificadores proporcionados durante la creación se deben liberar de este proceso. Esto reducirá el recuento de referencias en el objeto de dispositivo subyacente y permitirá a las operaciones de e/s detectar correctamente un canal roto cuando la sesión pseudoconsole cierre su copia de los identificadores.

## <a name="preparing-for-creation-of-the-child-process"></a>Preparación para la creación del proceso secundario

La siguiente fase consiste en preparar la estructura [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) que va a transmitir la información de pseudoconsole al iniciar el proceso secundario.

Esta estructura contiene la capacidad de proporcionar información de inicio compleja, incluidos los atributos para la creación de procesos y subprocesos.

Use [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) en un modo de doble llamada para calcular primero el número de bytes necesarios para contener la lista, asignar la memoria solicitada y, a continuación, llamar de nuevo al puntero de memoria opaca para que se configure como la lista de atributos.

A continuación, llame a [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) pasando la lista de atributos inicializada con la marca **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, el identificador PSEUDOCONSOLE y el tamaño del identificador PSEUDOCONSOLE.

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

## <a name="creating-the-hosted-process"></a>Crear el proceso hospedado

A continuación, llame a [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) pasando la estructura [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) junto con la ruta de acceso al archivo ejecutable y cualquier información de configuración adicional, si procede. Es importante establecer la marca de **EXTENDED_STARTUPINFO_PRESENT** al llamar a para avisar al sistema de que la referencia de pseudoconsole está contenida en la información extendida.

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
> El cierre de la sesión de pseudoconsole mientras el proceso hospedado todavía se está iniciando y la conexión puede dar lugar a que la aplicación cliente muestre un cuadro de diálogo de error. Se muestra el mismo cuadro de diálogo de error si al proceso hospedado se le asigna un identificador de pseudoconsole no válido para el inicio. En el código de inicialización del proceso hospedado, las dos circunstancias son idénticas. El cuadro de diálogo emergente de la aplicación cliente hospedada en caso de error se leerá `0xc0000142` con un mensaje localizado que detalla el error de inicialización.

## <a name="communicating-with-the-pseudoconsole-session"></a>Comunicación con la sesión de Pseudoconsole

Una vez que el proceso se crea correctamente, la aplicación host puede usar el extremo de escritura de la canalización de entrada para enviar información de interacción con el usuario en el pseudoconsole y el extremo de lectura de la canalización de salida para recibir información de presentación gráfica de la pseudo consola.

Es completamente la aplicación de hospedaje decidir cómo controlar la actividad adicional. La aplicación de hospedaje podría iniciar una ventana en otro subproceso para recopilar la entrada de interacción del usuario y serializarla en el extremo de escritura de la canalización de entrada para el pseudoconsole y la aplicación de modo de carácter hospedada. Se puede iniciar otro subproceso para purgar el extremo de lectura de la canalización de salida de pseudoconsole, descodificar el texto y la información de la [secuencia de terminal virtual](console-virtual-terminal-sequences.md) y presentarlo en la pantalla.

Los subprocesos también se pueden usar para retransmitir la información de los canales de pseudoconsole a otro canal o dispositivo, incluida una red para la información remota en otro proceso o equipo y para evitar cualquier transcodificación local de la información.

## <a name="resizing-the-pseudoconsole"></a>Cambiar el tamaño de Pseudoconsole

A lo largo del tiempo de ejecución, puede haber una circunstancia en la que se deba cambiar el tamaño del búfer debido a una interacción del usuario o a una solicitud que se reciba fuera de banda desde otro dispositivo de visualización o interacción.

Esto se puede hacer con la función [**ResizePseudoConsole**](resizepseudoconsole.md) que especifica el alto y el ancho del búfer en un recuento de caracteres.

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

## <a name="ending-the-pseudoconsole-session"></a>Finalización de la sesión de Pseudoconsole

Para finalizar la sesión, llame a la función [**ClosePseudoConsole**](closepseudoconsole.md) con el identificador de la creación de pseudoconsole original. Cualquier aplicación de modo de carácter de cliente adjunta, como la de la llamada [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) , se terminará cuando se cierre la sesión. Si el elemento secundario original era una aplicación de tipo shell que crea otros procesos, también se terminarán todos los procesos asociados relacionados en el árbol.

> [!WARNING]
>Cerrar la sesión tiene varios efectos secundarios que pueden dar lugar a una condición de interbloqueo si el pseudoconsole se usa en un modo sincrónico de un solo subproceso. La acción de cerrar la sesión pseudoconsole puede emitir una actualización de fotogramas finales en `hOutput` la que se debe purgar del búfer del canal de comunicaciones. Además, si `PSEUDOCONSOLE_INHERIT_CURSOR` se seleccionó al crear el pseudoconsole, al intentar cerrar el pseudoconsole sin responder al mensaje de consulta de herencia de cursor (recibido en `hOutput` y respondiendo a través de `hInput` ) se puede producir otra condición de interbloqueo. Se recomienda que los canales de comunicaciones para los pseudoconsole se representen en subprocesos individuales y se sigan purgando y procesando hasta que se interrumpa su propio acuerdo por la aplicación cliente o finalizando las actividades de destrucción en la llamada a la función [**ClosePseudoConsole**](closepseudoconsole.md) .
