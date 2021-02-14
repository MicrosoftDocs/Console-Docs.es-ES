---
title: AttachConsole función)
description: Vea la información de referencia sobre la función AttachConsole, que asocia el proceso de llamada a la consola del proceso especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- base.attachconsole
- consoles.attachconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: a1be050dccc0c77b6ad448cc45e87906a115d82c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357845"
---
# <a name="attachconsole-function"></a>AttachConsole función)

Asocia el proceso de llamada a la consola del proceso especificado como una aplicación cliente.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

## <a name="parameters"></a>Parámetros

*dwProcessId* \[ de\]  
Identificador del proceso cuya consola se va a usar. Este parámetro puede ser uno de los valores siguientes.

| Valor | Significado |
|-|-|
| *pid* | Use la consola del proceso especificado. |
| **Asociar \_ \_proceso primario**`(DWORD)-1` | Use la consola del elemento primario del proceso actual. |

## <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Comentarios

Un proceso se puede adjuntar a como máximo una consola. Si el proceso de llamada ya está asociado a una consola de, el código de error devuelto es **error de \_ acceso \_ denegado** ( `5` ). Si el proceso especificado no tiene una consola de, el código de error devuelto es un **error de \_ \_ identificador no válido** ( `6` ). Si el proceso especificado no existe, el código de error devuelto es un **parámetro de error \_ no válido \_** ( `87` ).

Un proceso puede usar la función [**FreeConsole**](freeconsole.md) para desasociarse de su consola. Si otros procesos comparten la consola, la consola no se destruye, pero el proceso que llamó a **FreeConsole** no puede hacer referencia a ella. Una consola se cierra cuando el último proceso asociado a ella finaliza o llama a **FreeConsole**. Una vez que un proceso llama a **FreeConsole**, puede llamar a la función [**AllocConsole**](allocconsole.md) para crear una nueva consola o **AttachConsole** para asociar a otra consola.

Esta función es principalmente útil para las aplicaciones que se vincularon con [**/Subsystem: Windows**](/cpp/build/reference/subsystem-specify-subsystem), que implica al sistema operativo que no se necesita una consola antes de entrar en el método Main del programa. En esa instancia, es probable que los identificadores estándar recuperados con [**GetStdHandle**](getstdhandle.md) no sean válidos en el inicio hasta que se llame a **AttachConsole** . La excepción a esto es si la aplicación se inicia con la herencia de identificadores por su proceso primario.

Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como `0x0501` o posterior. Para obtener más información, consulte [uso de los encabezados de Windows](/windows/win32/winprog/using-the-windows-headers).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows XP \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows Server 2003 \[\] |
| Encabezado | ConsoleApi.h (a través de WinCon.h, incluido Windows.h) |
| Biblioteca | Kernel32.lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Vea también

[Funciones de la consola](console-functions.md)

[Consolas](consoles.md)

[**AllocConsole**](allocconsole.md)

[**FreeConsole**](freeconsole.md)

[**GetConsoleProcessList**](getconsoleprocesslist.md)