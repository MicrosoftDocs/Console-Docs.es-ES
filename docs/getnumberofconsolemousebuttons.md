---
title: GetNumberOfConsoleMouseButtons función)
description: Recupera el número de botones del mouse que usa la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetNumberOfConsoleMouseButtons
- wincon/GetNumberOfConsoleMouseButtons
- GetNumberOfConsoleMouseButtons
MS-HAID:
- '\_win32\_getnumberofconsolemousebuttons'
- base.getnumberofconsolemousebuttons
- consoles.getnumberofconsolemousebuttons
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2
topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 96a63f3d35170ed419ceb90a063044a93c0b1951
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037833"
---
# <a name="getnumberofconsolemousebuttons-function"></a>GetNumberOfConsoleMouseButtons función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Recupera el número de botones del mouse que usa la consola actual.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

## <a name="parameters"></a>Parámetros

*lpNumberOfMouseButtons* \[ enuncia\]  
Puntero a una variable que recibe el número de botones del mouse.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

Cuando una consola recibe la entrada del mouse, una estructura de [**\_ registro de entrada**](input-record-str.md) que contiene una estructura de [**\_ \_ registro de eventos del mouse**](mouse-event-record-str.md) se coloca en el búfer de entrada de la consola. El miembro **dwButtonState** del **\_ \_ registro de eventos del mouse** tiene un bit que indica el estado de cada botón del mouse. El bit es 1 si el botón está presionado y 0 si el botón está activo. Para determinar el número de bits que son significativos, use **GetNumberOfConsoleMouseButtons** .

> [!TIP]
> No se recomienda esta API y no tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente. Esta decisión alinea intencionadamente la plataforma de Windows con otros sistemas operativos. Este estado solo es relevante para el usuario local, la sesión y el contexto de privilegios. Es posible que las aplicaciones remotas mediante utilidades y transportes multiplataforma como SSH no funcionen según lo esperado si se usa esta API.

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | ConsoleApi3. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Consulte también

[Funciones de la consola](console-functions.md)

[Búfer de entrada de la consola](console-input-buffer.md)

[**PeekConsoleInput**](readconsoleinput.md)

[**registro de entrada \_**](input-record-str.md)

[**\_registro de eventos del mouse \_**](mouse-event-record-str.md)
