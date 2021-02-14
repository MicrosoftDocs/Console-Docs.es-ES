---
title: GetConsoleDisplayMode función)
description: Vea la información de referencia sobre la función GetConsoleDisplayMode, que recupera el modo de presentación de la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 5b9ec78dc6fe5d7baa1a9af64010fd577f101c47
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358355"
---
# <a name="getconsoledisplaymode-function"></a>GetConsoleDisplayMode función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Recupera el modo de presentación de la consola actual.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

## <a name="parameters"></a>Parámetros

*lpModeFlags* \[ enuncia\]  
Modo de presentación de la consola. Este parámetro puede ser uno o varios de los valores siguientes.

| Valor | Significado |
|-|-|
| **CONSOLE_FULLSCREEN** 1 | Consola de pantalla completa. La consola está en este modo en cuanto se maximiza la ventana. En este momento, se puede producir un error en la transición al modo de pantalla completa. |
| **CONSOLE_FULLSCREEN_HARDWARE** 2 | Consola de pantalla completa que se comunica directamente con el hardware de vídeo. Este modo se establece después de que la consola esté en modo de **CONSOLE_FULLSCREEN** para indicar que se ha completado la transición al modo de pantalla completa. |

> [!NOTE]
> La transición al modo de hardware de vídeo de pantalla completa del 100% se quitó en Windows Vista con la replataforma de la pila de gráficos a [WDDM](//windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model). En versiones posteriores de Windows, el estado máximo resultante es **CONSOLE_FULLSCREEN** que representa una ventana frameless que aparece como pantalla completa, pero que no está en el control exclusivo del hardware.

## <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Comentarios

Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0500 o posterior. Para obtener más información, consulte [uso de los encabezados de Windows](/windows/win32/winprog/using-the-windows-headers).

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows XP \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows Server 2003 \[\] |
| Encabezado | ConsoleApi3. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32.lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Vea también

[Funciones de la consola](console-functions.md)

[Modos de consola](console-modes.md)

[**SetConsoleDisplayMode**](setconsoledisplaymode.md)