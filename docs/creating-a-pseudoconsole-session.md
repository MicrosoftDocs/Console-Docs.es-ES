---
title: Creación de una sesión de pseudoconsola
description: Una sesión de pseudoconsola permitirá que una aplicación hospede las actividades de una aplicación de modo caracteres.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: consola, aplicaciones de modo caracteres, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola, ConPTY, pseudoconsola, Windows PTY, pseudoconsola
ms.localizationpriority: high
ms.openlocfilehash: c1a83b308e4d9a23fdb6b2778561030e619dfdb3
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357935"
---
# <a name="creating-a-pseudoconsole-session"></a>Creación de una sesión de pseudoconsola

La pseudoconsola de Windows, que a veces también se denomina pseudoconsola, ConPTY o Windows PTY, es un mecanismo diseñado para crear un host externo para las actividades en modo caracteres del subsistema que reemplazan la parte de interactividad del usuario de la ventana predeterminada del host de consola.

Hospedar una sesión de pseudoconsola es un poco diferente de una sesión de consola tradicional. Las sesiones de consola tradicionales se inician automáticamente cuando el sistema operativo reconoce que va a ejecutarse una aplicación de modo caracteres. Por el contrario, es necesario que la aplicación de hospedaje cree una sesión de pseudoconsola y los canales de comunicación antes de crear el proceso con la aplicación de modo caracteres secundaria que se va a hospedar. El proceso secundario seguirá creándose con la función [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa), pero con cierta información adicional que dirigirá el sistema operativo a establecer el entorno adecuado.

Puede encontrar información de fondo adicional sobre este sistema en la [entrada de blog del anuncio inicial](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).

Puede encontrar ejemplos completos del uso de la pseudoconsola en nuestro repositorio de GitHub [microsoft/terminal](https://github.com/microsoft/terminal) en el directorio samples.

## <a name="preparing-the-communication-channels"></a>Preparación de los canales de comunicación

El primer paso consiste en crear un par de canales de comunicación sincrónicos que se proporcionarán durante la creación de la sesión de pseudoconsola para la comunicación bidireccional con la aplicación hospedada. El sistema de pseudoconsola procesa estos canales mediante las funciones [**ReadFile**](/windows/desktop/api/fileapi/nf-fileapi-readfile) y [**WriteFile**](/windows/desktop/api/fileapi/nf-fileapi-writefile) con [E/S sincrónicas](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output). Los identificadores de archivo o de dispositivo de E/S, como una secuencia de archivos o una canalización, son aceptables siempre que no se requiera una estructura [**OVERLAPPED**](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) para la comunicación asincrónica.

> [!WARNING]
>Para evitar condiciones de carrera e interbloqueos, recomendamos encarecidamente que cada uno de los canales de comunicación se atienda en un subproceso independiente que mantenga su propio estado de búfer de cliente y cola de mensajes dentro de la aplicación. El mantenimiento de todas las actividades de pseudoconsola en el mismo subproceso puede dar lugar a un interbloqueo, en el que se llena uno de los búferes de comunicaciones y espera a que se produzca una acción mientras se intenta enviar una solicitud de bloqueo en otro canal.

## <a name="creating-the-pseudoconsole"></a>Creación de la pseudoconsola

Con los canales de comunicación que se han establecido, identifique el extremo de "lectura" del canal de entrada y el extremo de "escritura" del canal de salida. Este par de identificadores se proporciona al llamar a [**CreatePseudoConsole**](createpseudoconsole.md) para crear el objeto.

Para la creación, se requiere un tamaño que represente las dimensiones X e Y (en número de caracteres). Estas son las dimensiones que se aplicarán a la superficie de visualización de la ventana de presentación final (terminal). Los valores se utilizan para crear un búfer en memoria dentro del sistema de pseudoconsola.

El tamaño de búfer proporciona respuestas a las aplicaciones de modo caracteres cliente que sondean información con las [funciones de consola del lado cliente](console-functions.md) como [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) y dictaminan el diseño y la posición del texto cuando los clientes usan funciones como [**WriteConsoleOutput**](writeconsoleoutput.md).

Por último, se proporciona un campo de marcas en la creación de una pseudoconsola para llevar a cabo funcionalidades especiales. De forma predeterminada, establezca esta opción en 0 para que no tenga ninguna funcionalidad especial.

En este momento, solo hay una marca especial disponible para solicitar la herencia de la posición del cursor de una sesión de consola ya asociada al llamador de la API de pseudoconsola. Esto está pensado para su uso en escenarios más avanzados donde una aplicación de hospedaje que está preparando una sesión de pseudoconsola también es una aplicación de modo caracteres cliente de otro entorno de consola.

A continuación, se proporciona un fragmento de código de ejemplo que utiliza [**CreatePipe**](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe) para establecer un par de canales de comunicación y crear la pseudoconsola.

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
>Este fragmento de código está incompleto y se usa solo para mostrar esta llamada específica. Tendrá que administrar la duración de los elementos **HANDLE** de manera adecuada. Si no se administra la duración de los elementos **HANDLE** correctamente, pueden producirse escenarios de interbloqueo, especialmente con llamadas de E/S sincrónicas.

Tras la finalización de la llamada a [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) para crear la aplicación de modo caracteres cliente asociada a la pseudoconsola, los identificadores proporcionados durante la creación deben liberarse del proceso. Esto reducirá el número de referencias en el objeto de dispositivo subyacente y permitirá a las operaciones de E/S detectar correctamente un canal roto cuando la sesión de pseudoconsola cierre su copia de los identificadores.

## <a name="preparing-for-creation-of-the-child-process"></a>Preparación de la creación del proceso secundario

La siguiente fase consiste en preparar la estructura [**STARTUPINFOEX**](/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) que va a transmitir la información de la pseudoconsola al iniciar el proceso secundario.

Esta estructura contiene la capacidad de proporcionar información de inicio compleja, incluidos los atributos para la creación de procesos y subprocesos.

Use [**InitializeProcThreadAttributeList**](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) en modo de doble llamada para calcular primero el número de bytes necesarios para contener la lista, asignar la memoria solicitada y, luego llamar de nuevo proporcionando el puntero de memoria opaco para que se configure como la lista de atributos.

A continuación, llame a [**UpdateProcThreadAttribute**](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) y pase la lista de atributos inicializados con la marca **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, el identificador de pseudoconsola y el tamaño del identificador de pseudoconsola.

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

## <a name="creating-the-hosted-process"></a>Creación del proceso hospedado

Después, llame a [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) pasando la estructura [**STARTUPINFOEX**](/windows/desktop/api/winbase/ns-winbase-_startupinfoexw), junto con la ruta de acceso al archivo ejecutable y cualquier información de configuración adicional, si procede. Es importante establecer la marca **EXTENDED_STARTUPINFO_PRESENT** cuando se llama para avisar al sistema de que la referencia de pseudoconsola está contenida en la información extendida.

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
> El cierre de la sesión de pseudoconsola mientras el proceso hospedado todavía se está iniciando y conectando puede dar lugar a que la aplicación cliente muestre un cuadro de diálogo de error. Se muestra el mismo cuadro de diálogo de error si se asigna al proceso hospedado un identificador de pseudoconsola no válido para el inicio. En el código de inicialización del proceso hospedado, las dos circunstancias son idénticas. El cuadro de diálogo emergente de la aplicación cliente hospedada en caso de error indicará `0xc0000142` con un mensaje localizado que detalla el error de inicialización.

## <a name="communicating-with-the-pseudoconsole-session"></a>Comunicación con la sesión de pseudoconsola

Una vez que el proceso se ha creado correctamente, la aplicación de hospedaje puede usar el extremo de escritura de la canalización de entrada para enviar información de interacción con el usuario a la pseudoconsola y el extremo de lectura de la canalización de salida para recibir información de presentación gráfica de la pseudoconsola.

Corresponde a la aplicación de hospedaje por completo decidir cómo controlar la actividad adicional. La aplicación de hospedaje puede iniciar una ventana en otro subproceso para recopilar la entrada de interacción del usuario y serializarla en el extremo de escritura de la canalización de entrada para la pseudoconsola y la aplicación de modo caracteres hospedada. Se puede iniciar otro subproceso para purgar el extremo de lectura de la canalización de salida de la pseudoconsola, descodificar el texto y la información de [secuencia de terminal virtual](console-virtual-terminal-sequences.md) y presentarlo en la pantalla.

También se pueden usar subprocesos para retransmitir la información de los canales de la pseudoconsola a otro canal o dispositivo, incluida una red para la información remota de otro proceso o máquina y evitar cualquier transcodificación local de la información.

## <a name="resizing-the-pseudoconsole"></a>Cambio de tamaño de la pseudoconsola

A lo largo del tiempo de ejecución, puede haber circunstancias en las que se deba cambiar el tamaño del búfer debido a una interacción del usuario o a una solicitud recibida fuera de banda de otro dispositivo de visualización o interacción.

Esto puede hacerse con la función [**ResizePseudoConsole**](resizepseudoconsole.md) que especifica el alto y el ancho del búfer en número de caracteres.

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

## <a name="ending-the-pseudoconsole-session"></a>Finalización de la sesión de pseudoconsola

Para finalizar la sesión, llame a la función [**ClosePseudoConsole**](closepseudoconsole.md) con el identificador de la creación de la pseudoconsola original. Cualquier aplicación de modo caracteres cliente asociada, como la de la llamada a [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa), se terminará cuando se cierre la sesión. Si el elemento secundario original era una aplicación de tipo shell que crea otros procesos, también se terminarán todos los procesos asociados relacionados del árbol.

> [!WARNING]
>Cerrar la sesión tiene varios efectos secundarios que pueden dar lugar a una condición de interbloqueo si la pseudoconsola se usa en modo sincrónico de un solo subproceso. La acción de cerrar la sesión de pseudoconsola puede emitir una actualización de marco final a `hOutput` que se debe purgar del búfer del canal de comunicaciones. Además, si se seleccionó `PSEUDOCONSOLE_INHERIT_CURSOR` al crear la pseudoconsola, si se intenta cerrar el pseudoconsola sin responder al mensaje de consulta de herencia de cursor (recibido en `hOutput` y al que se ha respondido a través de `hInput`) puede producirse otra condición de interbloqueo. Se recomienda que los canales de comunicaciones para la pseudoconsola se representen en subprocesos individuales y se sigan purgando y procesando hasta que se interrumpan a iniciativa propia por la aplicación cliente o al completar las actividades de desmontaje de la llamada a la función [**ClosePseudoConsole**](closepseudoconsole.md).