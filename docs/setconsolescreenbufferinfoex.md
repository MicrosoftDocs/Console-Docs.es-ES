---
title: SetConsoleScreenBufferInfoEx función)
description: Establece la información extendida sobre el búfer de pantalla especificado en el búfer especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleScreenBufferInfoEx
- wincon/SetConsoleScreenBufferInfoEx
- SetConsoleScreenBufferInfoEx
MS-HAID:
- base.setconsolescreenbufferinfoex
- consoles.setconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ff851144-eee9-4410-8fd1-28aa24fc25f1
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4a83c91a60a26d8e962efdf10b127e97beb70a7f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039353"
---
# <a name="setconsolescreenbufferinfoex-function"></a>SetConsoleScreenBufferInfoEx función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Establece la información extendida sobre el búfer de pantalla especificado.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI SetConsoleScreenBufferInfoEx(
  _In_ HANDLE                        hConsoleOutput,
  _In_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de **\_ escritura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*lpConsoleScreenBufferInfoEx* \[ de\]  
Una [**estructura \_ \_ \_ INFOEX de búfer de pantalla**](console-screen-buffer-infoex.md) de la consola que contiene la información del búfer de pantalla de la consola.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

> [!TIP]
> Esta API tiene un equivalente de **[terminal virtual](console-virtual-terminal-sequences.md)** parcial. El **[búfer de posición del cursor](console-virtual-terminal-sequences.md#cursor-positioning)** y **[los atributos de texto](console-virtual-terminal-sequences.md#text-formatting)** tienen equivalentes de secuencia específicos. La tabla de colores no es configurable, pero los **[colores extendidos](console-virtual-terminal-sequences.md#extended-colors)** están disponibles más allá de lo que suele estar disponible a través de **[las funciones](console-functions.md)** de la consola. Los atributos emergentes no tienen ningún equivalente en los menús emergentes es responsabilidad de la aplicación cliente de línea de comandos en el mundo de **terminal virtual** . Por último, el tamaño de la ventana y el estado de la pantalla completa se consideran los privilegios que posee el usuario en el mundo del **terminal virtual** y no tienen ninguna secuencia equivalente.

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows Vista \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows Server 2008 \[\] |
| Encabezado | ConsoleApi2. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Consulte también

[Funciones de la consola](console-functions.md)

[**búfer de pantalla de la consola \_ \_ \_ INFOEX**](console-screen-buffer-infoex.md)

[**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md)
