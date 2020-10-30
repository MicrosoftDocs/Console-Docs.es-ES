---
title: SetConsoleActiveScreenBuffer función)
description: Establece el búfer de pantalla especificado para que sea el búfer de pantalla de la consola que se muestra actualmente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleActiveScreenBuffer
- wincon/SetConsoleActiveScreenBuffer
- SetConsoleActiveScreenBuffer
MS-HAID:
- '\_win32\_setconsoleactivescreenbuffer'
- base.setconsoleactivescreenbuffer
- consoles.setconsoleactivescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c026cb94-c8ec-44ee-b432-3870ae3006c2
topic_type:
- apiref
api_name:
- SetConsoleActiveScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 7eb27a383a0bdbfc985188eb477ab9a878f33274
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039443"
---
# <a name="setconsoleactivescreenbuffer-function"></a>SetConsoleActiveScreenBuffer función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Establece el búfer de pantalla especificado para que sea el búfer de pantalla de la consola que se muestra actualmente.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI SetConsoleActiveScreenBuffer(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

Una consola puede tener varios búferes de pantalla. **SetConsoleActiveScreenBuffer** determina cuál de ellas se muestra. Puede escribir en un búfer de pantalla inactivo y, a continuación, usar **SetConsoleActiveScreenBuffer** para mostrar el contenido del búfer.

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, vea [lectura y escritura de bloques de caracteres y atributos](reading-and-writing-blocks-of-characters-and-attributes.md).

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

[Búferes de pantalla de la consola](console-screen-buffers.md)

[**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)
