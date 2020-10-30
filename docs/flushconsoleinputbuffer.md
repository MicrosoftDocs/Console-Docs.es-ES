---
title: FlushConsoleInputBuffer función)
description: Vacía el búfer de entrada de la consola. Se descartan todos los registros de entrada que se encuentran actualmente en el búfer de entrada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/FlushConsoleInputBuffer
- wincon/FlushConsoleInputBuffer
- FlushConsoleInputBuffer
MS-HAID:
- '\_win32\_flushconsoleinputbuffer'
- base.flushconsoleinputbuffer
- consoles.flushconsoleinputbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6f7832d6-1fb2-4ca8-bd07-43123c990851
topic_type:
- apiref
api_name:
- FlushConsoleInputBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 543552e9252c1f28701a0b316b43597cdd9cd2c9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039053"
---
# <a name="flushconsoleinputbuffer-function"></a>FlushConsoleInputBuffer función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Vacía el búfer de entrada de la consola. Se descartan todos los registros de entrada que se encuentran actualmente en el búfer de entrada.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI FlushConsoleInputBuffer(
  _In_ HANDLE hConsoleInput
);
```

## <a name="parameters"></a>Parámetros

*hConsoleInput* \[ de\]  
Identificador para el búfer de entrada de la consola. El identificador debe tener el derecho de acceso de **\_ escritura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

> [!TIP]
> No se recomienda esta API y no tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente. Al intentar vaciar la cola de entrada a la vez, se puede destruir el estado de la cola de una manera inesperada.

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | ConsoleApi2. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Consulte también

[Funciones de la consola](console-functions.md)

[Funciones de entrada de la consola de bajo nivel](low-level-console-input-functions.md)

[**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**PeekConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)
