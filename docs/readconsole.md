---
title: ReadConsole función)
description: Lee la entrada de caracteres del búfer de entrada de la consola y lo quita del búfer.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/ReadConsole
- wincon/ReadConsole
- ReadConsole
- consoleapi/ReadConsoleA
- wincon/ReadConsoleA
- ReadConsoleA
- consoleapi/ReadConsoleW
- wincon/ReadConsoleW
- ReadConsoleW
MS-HAID:
- '\_win32\_readconsole'
- base.readconsole
- consoles.readconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1aa9ecac-a9b9-4e6d-9206-7a57013de657
topic_type:
- apiref
api_name:
- ReadConsole
- ReadConsoleA
- ReadConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 757d770bc7fea543d15678af5f80f15c17dd0e82
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358285"
---
# <a name="readconsole-function"></a>ReadConsole función)

Lee la entrada de caracteres del búfer de entrada de la consola y lo quita del búfer.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI ReadConsole(
  _In_     HANDLE  hConsoleInput,
  _Out_    LPVOID  lpBuffer,
  _In_     DWORD   nNumberOfCharsToRead,
  _Out_    LPDWORD lpNumberOfCharsRead,
  _In_opt_ LPVOID  pInputControl
);
```

## <a name="parameters"></a>Parámetros

*hConsoleInput* \[ de\]  
Identificador para el búfer de entrada de la consola. El identificador debe tener derecho de acceso de **GENERIC\_READ**. Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).

*lpBuffer* \[ enuncia\]  
Un puntero a un búfer que recibe los datos leídos del búfer de entrada de la consola.

*nNumberOfCharsToRead* \[ de\]  
Número de caracteres que se van a leer. El tamaño del búfer al que apunta el parámetro *lpBuffer* debe ser al menos `nNumberOfCharsToRead * sizeof(TCHAR)` bytes.

*lpNumberOfCharsRead* \[ enuncia\]  
Puntero a una variable que recibe el número de caracteres leídos realmente.

*pInputControl* \[ en, opcional\]  
Puntero a una estructura [**de \_ \_ control READCONSOLE de consola**](console-readconsole-control.md) que especifica un carácter de control para indicar el final de la operación de lectura. Este parámetro puede ser **NULL**.

Este parámetro requiere una entrada Unicode de forma predeterminada. En el modo ANSI, establezca este parámetro en **null**.

## <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Comentarios

**ReadConsole** lee la entrada del teclado desde el búfer de entrada de la consola. Se comporta como la función [**readfile**](/windows/win32/api/fileapi/nf-fileapi-readfile) , salvo que puede leer en modo Unicode (caracteres anchos) o ANSI. Para tener aplicaciones que mantengan un único conjunto de orígenes compatibles con ambos modos, use **ReadConsole** en lugar de **readfile**. Aunque **ReadConsole** solo se puede usar con un identificador de búfer de entrada de la consola, **readfile** se puede usar con otros identificadores (como archivos o canalizaciones). **ReadConsole** produce un error si se usa con un identificador estándar que se ha redirigido para que sea distinto de un identificador de consola.

Todos los modos de entrada que afectan al comportamiento de [**readfile**](/windows/win32/api/fileapi/nf-fileapi-readfile) tienen el mismo efecto en **ReadConsole**. Para recuperar y establecer los modos de entrada de un búfer de entrada de la consola, use las funciones [**GetConsoleMode**](getconsolemode.md) y [**SetConsoleMode**](setconsolemode.md) .

Si el búfer de entrada contiene eventos de entrada distintos de los eventos de teclado (como eventos del mouse o eventos de cambio de tamaño de ventana), se descartan. Estos eventos solo se pueden leer mediante la función [**ReadConsoleInput**](readconsoleinput.md) .

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

El parámetro *pInputControl* se puede usar para habilitar las reactivaciones intermedias desde la lectura en respuesta a un carácter de control de finalización de archivos especificado en una estructura de [**\_ \_ control de READCONSOLE de consola**](console-readconsole-control.md) . Esta característica requiere que se habiliten las extensiones de comandos, que el identificador de salida estándar sea un identificador de salida de consola y que la entrada sea Unicode.

**Windows Server 2003 y Windows XP/2000:** No se admite la característica de lectura intermedia.

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Professional |
| Servidor mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Server |
| Encabezado | ConsoleApi.h (a través de WinCon.h, incluido Windows.h) |
| Biblioteca | Kernel32.lib |
| Archivo DLL | Kernel32.dll |
| Nombres Unicode y ANSI | **ReadConsoleW** (Unicode) y **ReadConsoleA** (ANSI) |

## <a name="see-also"></a>Vea también

[Funciones de la consola](console-functions.md)

[**\_control READCONSOLE de consola \_**](console-readconsole-control.md)

[**GetConsoleMode**](getconsolemode.md)

[Métodos de entrada y salida](input-and-output-methods.md)

[**PeekConsoleInput**](readconsoleinput.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleMode**](setconsolemode.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsole**](writeconsole.md)