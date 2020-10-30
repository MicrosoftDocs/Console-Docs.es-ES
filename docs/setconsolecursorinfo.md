---
title: SetConsoleCursorInfo función)
description: Establece el tamaño y la visibilidad del cursor para el búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleCursorInfo
- wincon/SetConsoleCursorInfo
- SetConsoleCursorInfo
MS-HAID:
- '\_win32\_setconsolecursorinfo'
- base.setconsolecursorinfo
- consoles.setconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c98cbffb-18de-41e8-bba7-5fb46a0c5d25
topic_type:
- apiref
api_name:
- SetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4bbb14dd501d483f35fbce5e1a729eaf002b1579
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039403"
---
# <a name="setconsolecursorinfo-function"></a>SetConsoleCursorInfo función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Establece el tamaño y la visibilidad del cursor para el búfer de pantalla de la consola especificado.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de **\_ lectura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*lpConsoleCursorInfo* \[ de\]  
Puntero a una estructura [**de \_ \_ información del cursor**](console-cursor-info-str.md) de la consola que proporciona las nuevas especificaciones del cursor del búfer de pantalla de la consola.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

Cuando el cursor de un búfer de pantalla está visible, su apariencia puede variar, desde llenar completamente una celda de carácter hasta que aparezca como una línea horizontal en la parte inferior de la celda. El miembro **dwSize** de la estructura de [**\_ \_ información del cursor**](console-cursor-info-str.md) de la consola especifica el porcentaje de una celda de caracteres que se rellena con el cursor. Si este miembro es menor que 1 o mayor que 100, **SetConsoleCursorInfo** produce un error.

> [!TIP]
> Esta API tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente en la sección de **[visibilidad del cursor](console-virtual-terminal-sequences.md#cursor-visibility)** con las `^[[?25h` `^[[?25l` secuencias y. 

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

[**\_información del cursor de la consola \_**](console-cursor-info-str.md)

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)
