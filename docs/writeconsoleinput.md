---
title: WriteConsoleInput función)
description: Consulte la información de referencia sobre la función WriteConsoleInput, que escribe datos directamente en el búfer de entrada de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/WriteConsoleInput
- wincon/WriteConsoleInput
- WriteConsoleInput
- consoleapi2/WriteConsoleInputA
- wincon/WriteConsoleInputA
- WriteConsoleInputA
- consoleapi2/WriteConsoleInputW
- wincon/WriteConsoleInputW
- WriteConsoleInputW
MS-HAID:
- '\_win32\_writeconsoleinput'
- base.writeconsoleinput
- consoles.writeconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad06231f-5063-4aff-b14d-8df5e6e42430
topic_type:
- apiref
api_name:
- WriteConsoleInput
- WriteConsoleInputA
- WriteConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e4b9cdae52da2e23ff93e1904c4cb24ebac62831
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357785"
---
# <a name="writeconsoleinput-function"></a>WriteConsoleInput función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Escribe los datos directamente en el búfer de entrada de la consola.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

## <a name="parameters"></a>Parámetros

*hConsoleInput* \[ de\]  
Identificador para el búfer de entrada de la consola. El identificador debe tener derecho de acceso de **GENERIC\_WRITE**. Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).

*lpBuffer* \[in\]  
Puntero a una matriz de estructuras [**de \_ registros de entrada**](input-record-str.md) que contienen datos que se van a escribir en el búfer de entrada.

*nLength* \[ de\]  
El número de registros de entrada que se van a escribir.

*lpNumberOfEventsWritten* \[ enuncia\]  
Puntero a una variable que recibe el número de registros de entrada escritos realmente.

## <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Comentarios

**WriteConsoleInput** coloca los registros de entrada en el búfer de entrada detrás de los eventos pendientes en el búfer. El búfer de entrada crece dinámicamente, si es necesario, para contener tantos eventos como se escriban.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> No se recomienda esta API y no tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente. Esta decisión alinea intencionadamente la plataforma de Windows con otros sistemas operativos. Esta operación se considera el **[verbo equivocado](console-buffer-security-and-access-rights.md#wrong-way-verbs)** para este búfer. Es posible que las aplicaciones remotas mediante utilidades y transportes multiplataforma como SSH no funcionen según lo esperado si se usa esta API.

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Professional |
| Servidor mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Server |
| Encabezado | ConsoleApi2. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32.lib |
| Archivo DLL | Kernel32.dll |
| Nombres Unicode y ANSI | **WriteConsoleInputW** (Unicode) y **WriteConsoleInputA** (ANSI) |

## <a name="see-also"></a>Vea también

[Funciones de la consola](console-functions.md)

[**registro de entrada \_**](input-record-str.md)

[Funciones de entrada de la consola de bajo nivel](low-level-console-input-functions.md)

[**MapVirtualKey**](/windows/win32/api/winuser/nf-winuser-mapvirtualkeya)

[**PeekConsoleInput**](peekconsoleinput.md)

[**PeekConsoleInput**](readconsoleinput.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**VkKeyScan**](/windows/win32/api/winuser/nf-winuser-vkkeyscana)