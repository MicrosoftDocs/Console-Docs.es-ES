---
title: GetConsoleOriginalTitle función)
description: Vea la información de referencia sobre la función GetConsoleOriginalTitle, que recupera el título original de la ventana de la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 3c4fc202601cec9257b6cf95efdd460c64122b80
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359005"
---
# <a name="getconsoleoriginaltitle-function"></a>GetConsoleOriginalTitle función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Recupera el título original de la ventana de la consola actual.

## <a name="syntax"></a>Sintaxis

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a>Parámetros

*lpConsoleTitle* \[ enuncia\]  
Un puntero a un búfer que recibe una cadena terminada en null que contiene el título original.

*nSize* \[ de\]  
Tamaño del búfer de *lpConsoleTitle* , en caracteres.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es la longitud de la cadena copiada en el búfer, en caracteres.

Si el búfer no es lo suficientemente grande como para almacenar el título, el valor devuelto es cero y [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) devuelve el **error \_ Success**.

Si se produce un error en la función, el valor devuelto es cero y [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) devuelve el código de error.

## <a name="remarks"></a>Comentarios

Para establecer el título de una ventana de la consola, use la función [**SetConsoleTitle**](setconsoletitle.md) . Para recuperar la cadena de título actual, utilice la función [**GetConsoleTitle**](getconsoletitle.md) .

Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0600 o posterior. Para obtener más información, consulte [uso de los encabezados de Windows](/windows/win32/winprog/using-the-windows-headers).

> [!TIP]
> No se recomienda esta API y no tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente. Esta decisión alinea intencionadamente la plataforma de Windows con otros sistemas operativos. Es posible que las aplicaciones remotas mediante utilidades y transportes multiplataforma como SSH no funcionen según lo esperado si se usa esta API.

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows Vista \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows Server 2008 \[\] |
| Encabezado | ConsoleApi2. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32.lib |
| Archivo DLL | Kernel32.dll |
| Nombres Unicode y ANSI | **GetConsoleOriginalTitleW** (Unicode) y **GetConsoleOriginalTitleA** (ANSI) |

## <a name="see-also"></a>Vea también

[Funciones de la consola](console-functions.md)

[**GetConsoleTitle**](getconsoletitle.md)

[**SetConsoleTitle**](setconsoletitle.md)