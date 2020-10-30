---
title: FreeConsole función)
description: Vea la información de referencia sobre la función FreeConsole, que separa el proceso de llamada de su consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/FreeConsole
- wincon/FreeConsole
- FreeConsole
MS-HAID:
- '\_win32\_freeconsole'
- base.freeconsole
- consoles.freeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6c525325-696e-4d8b-8337-cbf9e31c900c
topic_type:
- apiref
api_name:
- FreeConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: af4382026b8e6455319e16ee21255fbc9352e3cd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039023"
---
# <a name="freeconsole-function"></a>FreeConsole función)

Desasocia el proceso de llamada de su consola.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI FreeConsole(void);
```

## <a name="parameters"></a>Parámetros

Esta función no tiene parámetros.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

Un proceso se puede adjuntar a como máximo una consola. Si el proceso de llamada no está asociado ya a una consola de, el código de error devuelto es un **\_ \_ parámetro no válido de error** (87).

Un proceso puede usar la función **FreeConsole** para desasociarse de su consola. Si otros procesos comparten la consola, la consola no se destruye, pero el proceso que llamó a **FreeConsole** no puede hacer referencia a ella. Una consola se cierra cuando el último proceso asociado a ella finaliza o llama a **FreeConsole** . Una vez que un proceso llama a **FreeConsole** , puede llamar a la función [**AllocConsole**](allocconsole.md) para crear una nueva consola o [**AttachConsole**](attachconsole.md) para asociar a otra consola.

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | ConsoleApi. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Consulte también

[**AllocConsole**](allocconsole.md)

[**AttachConsole**](attachconsole.md)

[Funciones de la consola](console-functions.md)

[Consolas](consoles.md)
