---
title: SetConsoleCursorPosition función)
description: Vea la información de referencia sobre la función SetConsoleCursorPosition, que establece la posición del cursor en el búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleCursorPosition
- wincon/SetConsoleCursorPosition
- SetConsoleCursorPosition
MS-HAID:
- '\_win32\_setconsolecursorposition'
- base.setconsolecursorposition
- consoles.setconsolecursorposition
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8e9abada-a64e-429f-8286-ced1169c7104
topic_type:
- apiref
api_name:
- SetConsoleCursorPosition
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c93fbf4b619b522a95af2b03a49d60ff6f880e7d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039373"
---
# <a name="setconsolecursorposition-function"></a>SetConsoleCursorPosition función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Establece la posición del cursor en el búfer de pantalla especificado.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de **\_ lectura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*dwCursorPosition* \[ de\]  
Estructura de [**coordenadas**](coord-str.md) que especifica la nueva posición del cursor, en caracteres. Las coordenadas son la columna y la fila de una celda de carácter de búfer de pantalla. Las coordenadas deben estar dentro de los límites del búfer de pantalla de la consola.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

La posición del cursor determina dónde se muestran los caracteres escritos por la función [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md) , o que se han devuelto por la función [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) . Para determinar la posición actual del cursor, utilice la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .

Si la nueva posición del cursor no está dentro de los límites de la ventana del búfer de pantalla de la consola, el origen de la ventana cambia para hacer que el cursor esté visible.

> [!TIP]
> Esta API tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente en las secciones **[posición de cursor simple](console-virtual-terminal-sequences.md#simple-cursor-positioning)** y **[posición del cursor](console-virtual-terminal-sequences.md#cursor-positioning)** . El uso de las secuencias de control de línea, retorno de carro, retroceso y tabulación también puede ayudar con la posición del cursor.

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, consulte [uso de las funciones de entrada y salida de High-Level](using-the-high-level-input-and-output-functions.md).

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

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetConsoleCursorInfo**](setconsolecursorinfo.md)

[**WriteConsole**](writeconsole.md)

[**Escritura**](https://msdn.microsoft.com/library/windows/desktop/aa365747)
