---
title: Función WriteConsole
description: Escribe una cadena de caracteres en un búfer de pantalla de la consola a partir de la ubicación actual del cursor.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/WriteConsole
- wincon/WriteConsole
- WriteConsole
- consoleapi/WriteConsoleA
- wincon/WriteConsoleA
- WriteConsoleA
- consoleapi/WriteConsoleW
- wincon/WriteConsoleW
- WriteConsoleW
MS-HAID:
- '\_win32\_writeconsole'
- base.writeconsole
- consoles.writeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1a13d9ef-75a9-49fd-9717-207f18612b59
topic_type:
- apiref
api_name:
- WriteConsole
- WriteConsoleA
- WriteConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 27caf0b0a804b99fdfe695efef4c085bf0c51567
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357615"
---
# <a name="writeconsole-function"></a>Función WriteConsole

Escribe una cadena de caracteres en un búfer de pantalla de la consola a partir de la ubicación actual del cursor.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[in\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener derecho de acceso de **GENERIC\_WRITE**. Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).

*lpBuffer* \[in\]  
Puntero a un búfer que contiene los caracteres que se van a escribir en el búfer de pantalla de la consola. Se espera que sea una matriz de `char` para `WriteConsoleA` o `wchar_t` para `WriteConsoleW`.

*nNumberOfCharsToWrite* \[in\]  
El número de caracteres que se va a escribir. Si el tamaño total del número especificado de caracteres supera el montón disponible, se produce un error en la función con **ERROR\_NOT\_ENOUGH\_MEMORY**.

*lpNumberOfCharsWritten* \[out, opcional\]  
Puntero a una variable que recibe el número de caracteres escritos realmente.

*lpReserved* reservado; debe ser **NULL**.

## <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Comentarios

La función **WriteConsole** escribe caracteres en el búfer de pantalla de la consola en la posición actual del cursor. La posición del cursor avanza a medida que se escriben caracteres. La función [**SetConsoleCursorPosition**](setconsolecursorposition.md) establece la posición actual del cursor.

Los caracteres se escriben con los atributos de color de primer plano y de fondo asociados al búfer de pantalla de la consola. La función [**SetConsoleTextAttribute**](setconsoletextattribute.md) cambia estos colores. Para determinar los atributos de color actuales y la posición actual del cursor, utilice [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).

Todos los modos de entrada que afectan al comportamiento de la función [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) tienen el mismo efecto en **WriteConsole**. Para recuperar y establecer los modos de salida de un búfer de pantalla de la consola, use las funciones [**GetConsoleMode**](getconsolemode.md) y [**SetConsoleMode**](setconsolemode.md).

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

**WriteConsole** produce un error si se usa con un identificador estándar que se redirige a un archivo. Si una aplicación procesa una salida multilingüe que se puede redirigir, determine si el identificador de salida es un identificador de consola (un método consiste en llamar a la función [**GetConsoleMode**](getconsolemode.md) y comprobar si se realiza correctamente). Si el identificador es un identificador de consola, llame a **WriteConsole**. Si el identificador no es un identificador de consola, la salida se redirige y debe llamar a [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) para realizar la E/S. Asegúrese de prefijar un archivo de texto sin formato Unicode con una marca de orden de bytes. Para obtener más información, consulte [Uso de marcas de orden de bytes](/windows/win32/intl/using-byte-order-marks).

Aunque una aplicación puede usar **WriteConsole** en modo ANSI para escribir caracteres ANSI, las consolas no admiten secuencias de "escape ANSI" o de "terminal virtuales" a menos que estén habilitadas. Consulte [**Secuencias de terminal virtuales de la consola**](console-virtual-terminal-sequences.md) para obtener más información y para ver la aplicabilidad de la versión del sistema operativo.

Cuando las secuencias de escape de terminal virtuales no están habilitadas, las funciones de consola pueden proporcionar una funcionalidad equivalente. Para obtener más información, vea [**SetCursorPos**](/windows/win32/api/winuser/nf-winuser-setcursorpos), [**SetConsoleTextAttribute**](setconsoletextattribute.md) y [**GetConsoleCursorInfo**](getconsolecursorinfo.md).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Professional |
| Servidor mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Server |
| Encabezado | ConsoleApi.h (a través de WinCon.h, incluido Windows.h) |
| Biblioteca | Kernel32.lib |
| Archivo DLL | Kernel32.dll |
| Nombres Unicode y ANSI | **WriteConsoleW** (Unicode) y **WriteConsoleA** (ANSI) |

## <a name="see-also"></a>Vea también

[Funciones de la consola](console-functions.md)

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**GetConsoleMode**](getconsolemode.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[Métodos de entrada y salida](input-and-output-methods.md)

[**ReadConsole**](readconsole.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleMode**](setconsolemode.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleTextAttribute**](setconsoletextattribute.md)

[**SetCursorPos**](/windows/win32/api/winuser/nf-winuser-setcursorpos)

[**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)