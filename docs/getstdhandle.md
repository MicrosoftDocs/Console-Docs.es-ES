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
ms.openlocfilehash: 42857417cedb661014de869536b798d29c9eb884
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420214"
---
# <a name="getstdhandle-function"></a>Función GetStdHandle

Recupera un identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).

## <a name="syntax"></a>Sintaxis

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a>Parámetros

*nStdHandle* \[in\]  
El dispositivo estándar. Este parámetro puede ser uno de los valores siguientes.

| Valor | Significado |
|-|-|
| **STD_INPUT_HANDLE** (DWORD) -10 | El dispositivo de entrada estándar. Inicialmente, es el búfer de entrada de la consola, `CONIN$`. |
| **STD_OUTPUT_HANDLE** (DWORD) -11 | El dispositivo de salida estándar. Inicialmente, es el búfer de pantalla activo de la consola, `CONOUT$`. |
| **STD_ERROR_HANDLE** (DWORD) -12 | El dispositivo de error estándar. Inicialmente, es el búfer de pantalla activo de la consola, `CONOUT$`. |

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es un identificador del dispositivo especificado o un identificador redirigido establecido por una llamada anterior en [**SetStdHandle**](setstdhandle.md). El identificador tiene los derechos de acceso **GENERIC\_READ** y **GENERIC\_WRITE**, a menos que la aplicación haya usado **SetStdHandle** para establecer un identificador estándar con un acceso inferior.

Si la función no se ejecuta correctamente, el valor devuelto es **INVALID\_HANDLE\_VALUE**. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Si una aplicación no tiene identificadores estándar asociados, como un servicio que se ejecuta en un escritorio interactivo y no los ha redirigido, el valor devuelto es **NULL**.

## <a name="remarks"></a>Comentarios

Las aplicaciones que necesitan leer o escribir en la consola pueden usar los identificadores devueltos por **GetStdHandle**. Cuando se crea una consola, el identificador de entrada estándar es un identificador del búfer de entrada de la consola, y los identificadores de salida estándar y de error estándar son identificadores del búfer de pantalla activo de la consola. Las funciones [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747), o cualquiera de las funciones de la consola que tienen acceso al búfer de entrada de la consola o un búfer de pantalla (por ejemplo, las funciones [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md) o [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)) pueden usar estos identificadores.

Los identificadores estándar de un proceso se pueden redirigir mediante una llamada a [**SetStdHandle**](setstdhandle.md), en cuyo caso **GetStdHandle** devuelve el identificador redirigido. Si se han redirigido los identificadores estándar, puede especificar el valor `CONIN$` en una llamada a la función [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) para obtener un identificador del búfer de entrada de la consola. De forma similar, puede especificar el valor `CONOUT$` para obtener un identificador para el búfer de pantalla activo de la consola.

Los identificadores estándar de un proceso en la entrada del método principal están dictaminados por la configuración de la marca [ **/SUBSYSTEM**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem) que se pasa al enlazador cuando se compiló la aplicación. Al especificar **/SUBSYSTEM:CONSOLE**, se solicita que el sistema operativo rellene los identificadores con una sesión de consola en el inicio, si el elemento primario aún no ha rellenado la tabla de identificadores estándar por herencia. Por el contrario, **/SUBSYSTEM:WINDOWS** implica que la aplicación no necesita una consola y que probablemente no usará los identificadores estándar. Puede encontrar más información sobre la herencia de identificadores en la documentación de [**STARTF\_USESTDHANDLES**](https://docs.microsoft.com/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).

Algunas aplicaciones funcionan fuera de los límites de su subsistema declarado; por ejemplo, una aplicación **/SUBSYSTEM:WINDOWS** puede comprobar o usar identificadores estándar para el registro o la depuración, pero funciona normalmente con una interfaz gráfica de usuario. Estas aplicaciones deberán sondear cuidadosamente el estado de los identificadores estándar en el inicio y usar [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md) y [**FreeConsole**](freeconsole.md) para agregar o quitar una consola si se desea.

Algunas aplicaciones también pueden variar su comportamiento sobre el tipo de identificador heredado. La eliminación de la ambigüedad del tipo entre la consola, la canalización, el archivo y otros se pueden realizar con [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype).

### <a name="attachdetach-behavior"></a>Comportamiento de la asociación o desasociación

Al asociarse a una nueva consola, los identificadores estándar siempre se reemplazan por identificadores de consola, a menos que se especifique **STARTF\_USESTDHANDLES** durante la creación del proceso.

Si el valor existente del identificador estándar es **NULL**, o el valor existente del identificador estándar es similar a un pseudoidentificador de consola, el identificador se reemplaza por un identificador de consola.

Cuando un elemento primario usa tanto **CREATE\_NEW\_CONSOLE** como **STARTF\_USESTDHANDLES** para crear un proceso de consola, no se reemplazarán los identificadores estándar a menos que el valor existente del identificador estándar sea **NULL** o un pseudoidentificador de consola.

> [!NOTE]
>Los procesos de consola *deben* empezar con los identificadores estándar rellenados o se rellenarán automáticamente con los identificadores adecuados para una nueva consola. Las aplicaciones de la interfaz gráfica de usuario (GUI) se pueden iniciar sin los identificadores estándar y no se rellenarán automáticamente.

## <a name="examples"></a>Ejemplos

Para un ejemplo, vea [Lectura de eventos de búfer de entrada](reading-input-buffer-events.md).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Professional |
| Servidor mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Server |
| Encabezado | ProcessEnv.h (via Winbase.h, include Windows.h) |
| Biblioteca | Kernel32.lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Vea también

[Funciones de la consola](console-functions.md)

[Identificadores de consola](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**PeekConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetStdHandle**](setstdhandle.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)
