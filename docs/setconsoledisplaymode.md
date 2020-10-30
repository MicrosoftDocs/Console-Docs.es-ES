---
title: SetConsoleDisplayMode función)
description: Vea la información de referencia sobre la función SetConsoleDisplayMode, que establece el modo de presentación del búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- base.setconsoledisplaymode
- consoles.setconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744
topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 52d7e50d7ced5615cb296c0590876e4604057e42
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039393"
---
# <a name="setconsoledisplaymode-function"></a>SetConsoleDisplayMode función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Establece el modo de presentación del búfer de pantalla de la consola especificado.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola.

*dwFlags* \[ de\]  
Modo de presentación de la consola. Este parámetro puede ser uno o varios de los valores siguientes.

| Valor | Significado |
|-|-|
| **CONSOLE_FULLSCREEN_MODE** 1 | El texto se muestra en el modo de pantalla completa. |
| **CONSOLE_WINDOWED_MODE** 2 | El texto se muestra en una ventana de la consola. |

*lpNewScreenBufferDimensions* \[ out, opcional\]  
Puntero a una estructura de [**coordenadas**](coord-str.md) que recibe las nuevas dimensiones del búfer de pantalla, en caracteres.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Observaciones

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows XP \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows Server 2003 \[\] |
| Encabezado | ConsoleApi3. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Consulte también

[Funciones de la consola](console-functions.md)

[Modos de consola](console-modes.md)

[**GetConsoleDisplayMode**](getconsoledisplaymode.md)
