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
# <a name="getstdhandle-function"></a>GetStdHandle (función)

Recupera un identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).

## <a name="syntax"></a>Sintaxis

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a>Parámetros

*nStdHandle* \[ de\]  
El dispositivo estándar. Este parámetro puede ser uno de los valores siguientes.

| Value | Significado |
|-|-|
| **STD_INPUT_HANDLE** (DWORD)-10 | El dispositivo de entrada estándar. Inicialmente, es el búfer de entrada de la consola, `CONIN$` . |
| **STD_OUTPUT_HANDLE** (DWORD)-11 | El dispositivo de salida estándar. Inicialmente, es el búfer de pantalla de la consola activo, `CONOUT$` . |
| **STD_ERROR_HANDLE** (DWORD)-12 | El dispositivo de error estándar. Inicialmente, es el búfer de pantalla de la consola activo, `CONOUT$` . |

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es un identificador del dispositivo especificado o un identificador Redirigido establecido por una llamada anterior a [**SetStdHandle**](setstdhandle.md). El identificador tiene derechos de acceso genéricos de **\_ lectura** y **\_ escritura** , a menos que la aplicación haya usado **SetStdHandle** para establecer un identificador estándar con un acceso inferior.

Si se produce un error en la función, el valor devuelto es un **\_ \_ valor de identificador no válido**. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Si una aplicación no tiene identificadores estándar asociados, como un servicio que se ejecuta en un escritorio interactivo y no los ha redirigido, el valor devuelto es **null**.

## <a name="remarks"></a>Comentarios

Los identificadores devueltos por **GetStdHandle** pueden ser usados por aplicaciones que necesitan leer o escribir en la consola. Cuando se crea una consola, el identificador de entrada estándar es un identificador del búfer de entrada de la consola, y los identificadores de salida estándar y de error estándar son identificadores del búfer de pantalla activo de la consola. Estos identificadores pueden ser utilizados por las funciones [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) , o por cualquiera de las funciones de consola que tienen acceso al búfer de entrada de la consola o a un búfer de pantalla (por ejemplo, las funciones [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md)o [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) ).

Los identificadores estándar de un proceso se pueden redirigir mediante una llamada a [**SetStdHandle**](setstdhandle.md), en cuyo caso **GetStdHandle** devuelve el identificador redirigido. Si se han redirigido los identificadores estándar, puede especificar el `CONIN$` valor en una llamada a la función [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) para obtener un identificador de un búfer de entrada de la consola. De forma similar, puede especificar el `CONOUT$` valor para obtener un identificador para el búfer de pantalla activo de la consola.

Los identificadores estándar de un proceso en la entrada del método Main están dictados por la configuración de la marca [**/Subsystem**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem) que se pasa al enlazador cuando se compiló la aplicación. Al especificar **/Subsystem: Console** , se solicita que el sistema operativo rellene los identificadores con una sesión de consola al inicio, si el elemento primario aún no ha rellenado la tabla de identificadores estándar por herencia. En el contrario, **/Subsystem: Windows** implica que la aplicación no necesita una consola y probablemente no esté usando los manipuladores estándar. Puede encontrar más información sobre cómo controlar la herencia en la documentación de [**STARTF \_ USESTDHANDLES**](https://docs.microsoft.com/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).

Algunas aplicaciones funcionan fuera de los límites de su subsistema declarado; por ejemplo, una aplicación **/Subsystem: Windows** puede comprobar o utilizar los identificadores estándar para el registro o la depuración, pero funciona normalmente con una interfaz gráfica de usuario. Estas aplicaciones deberán sondear cuidadosamente el estado de los identificadores estándar en el inicio y hacer uso de [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md)y [**FreeConsole**](freeconsole.md) para agregar o quitar una consola si lo desea.

Algunas aplicaciones también pueden variar su comportamiento en el tipo de identificador heredado. Ambigüedad: el tipo entre la consola, la canalización, el archivo y otros se puede realizar con [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype).

### <a name="attachdetach-behavior"></a>Comportamiento de adjuntar/separar

Al conectarse a una nueva consola, los identificadores estándar siempre se reemplazan por identificadores de consola, a menos que se haya especificado **STARTF \_ USESTDHANDLES** durante la creación del proceso.

Si el valor existente del identificador estándar es **null**, o el valor existente del identificador estándar es similar a un pseudohandle de consola, el identificador se reemplaza por un identificador de consola.

Cuando un elemento primario usa **Create \_ New \_ Console** y **STARTF \_ USESTDHANDLES** para crear un proceso de consola, no se reemplazarán los identificadores estándar a menos que el valor existente del identificador estándar sea **null** o una pseudohandle de consola.

> [!NOTE]
>Los procesos de la consola *deben* comenzar con los identificadores estándar llenos o se rellenarán automáticamente con los identificadores adecuados para una nueva consola. Las aplicaciones de la interfaz gráfica de usuario (GUI) se pueden iniciar sin los identificadores estándar y no se rellenarán automáticamente.

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, vea [leer eventos de búfer de entrada](reading-input-buffer-events.md).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | ProcessEnv. h (a través de Winbase. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
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

[**Escritura**](https://msdn.microsoft.com/library/windows/desktop/aa365747)
