---
title: GetNumberOfConsoleInputEvents función)
description: Recupera el número de registros de entrada no leídos en el búfer de entrada de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/GetNumberOfConsoleInputEvents
- wincon/GetNumberOfConsoleInputEvents
- GetNumberOfConsoleInputEvents
MS-HAID:
- '\_win32\_getnumberofconsoleinputevents'
- base.getnumberofconsoleinputevents
- consoles.getnumberofconsoleinputevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1083b4f1-8fa6-4054-a516-3b447c3b0130
topic_type:
- apiref
api_name:
- GetNumberOfConsoleInputEvents
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: b4cad78d35114c509f4e810a858e6ae3b8bfb644
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038693"
---
# <a name="getnumberofconsoleinputevents-function"></a>GetNumberOfConsoleInputEvents función)

Recupera el número de registros de entrada no leídos en el búfer de entrada de la consola.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

## <a name="parameters"></a>Parámetros

*hConsoleInput* \[ de\]  
Identificador para el búfer de entrada de la consola. El identificador debe tener el derecho de acceso de **\_ lectura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*lpcNumberOfEvents* \[ enuncia\]  
Un puntero a una variable que recibe el número de registros de entrada no leídos en el búfer de entrada de la consola.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

La función **GetNumberOfConsoleInputEvents** informa del número total de registros de entrada no leídos en el búfer de entrada, incluidos el teclado, el mouse y los registros de entrada de cambio de tamaño de ventana. Los procesos que usan la función [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) solo pueden leer entradas de teclado. Los procesos que usan la función [**ReadConsoleInput**](readconsoleinput.md) pueden leer todos los tipos de registros de entrada.

Un proceso puede especificar un identificador de búfer de entrada de la consola en una de las [funciones de espera](https://msdn.microsoft.com/library/windows/desktop/ms687069) para determinar si hay una entrada de consola sin leer. Cuando el búfer de entrada no está vacío, se señala el estado de un controlador de búfer de entrada de la consola.

Para leer los registros de entrada desde un búfer de entrada de la consola sin afectar al número de registros no leídos, utilice la función [**PeekConsoleInput**](peekconsoleinput.md) . Para descartar todos los registros no leídos en el búfer de entrada de la consola, use la función [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) .

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | ConsoleApi. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Consulte también

[Funciones de la consola](console-functions.md)

[**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

[Funciones de entrada de la consola de bajo nivel](low-level-console-input-functions.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsole**](readconsole.md)

[**PeekConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)
