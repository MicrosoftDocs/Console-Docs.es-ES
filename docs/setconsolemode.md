---
title: SetConsoleMode función)
description: Establece el modo de entrada del búfer de entrada de una consola o el modo de salida de un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/SetConsoleMode
- wincon/SetConsoleMode
- SetConsoleMode
MS-HAID:
- '\_win32\_setconsolemode'
- base.setconsolemode
- consoles.setconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 77508d58-8a7a-4c47-9ec5-dc61e5c4beac
topic_type:
- apiref
api_name:
- SetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: b382e6567d2099e2d6eacf33c8e19233f20c6400
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039363"
---
# <a name="setconsolemode-function"></a>SetConsoleMode función)

Establece el modo de entrada del búfer de entrada de una consola o el modo de salida de un búfer de pantalla de la consola.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

## <a name="parameters"></a>Parámetros

*hConsoleHandle* \[ de\]  
Identificador para el búfer de entrada de la consola o un búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de **\_ lectura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*dwMode* \[ de\]  
Modo de entrada o de salida que se va a establecer.

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

Para determinar el modo actual de un búfer de entrada de la consola o un búfer de pantalla, utilice la función [**GetConsoleMode**](getconsolemode.md) .

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, vea [leer eventos de búfer de entrada](reading-input-buffer-events.md).

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

[Modos de consola](console-modes.md)

[**GetConsoleMode**](getconsolemode.md)

[**HandlerRoutine**](handlerroutine.md)

[**ReadConsole**](readconsole.md)

[**PeekConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**WriteConsole**](writeconsole.md)

[**Escritura**](https://msdn.microsoft.com/library/windows/desktop/aa365747)
