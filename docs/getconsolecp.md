---
title: GetConsoleCP función)
description: Recupera la página de códigos de entrada utilizada por la consola asociada al proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/GetConsoleCP
- wincon/GetConsoleCP
- GetConsoleCP
MS-HAID:
- '\_win32\_getconsolecp'
- base.getconsolecp
- consoles.getconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9e0af6d9-0f5c-45b3-a686-22449d26de47
topic_type:
- apiref
api_name:
- GetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: fd581c1f11f457054257e1e36e55b726f48b34fb
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358465"
---
# <a name="getconsolecp-function"></a>GetConsoleCP función)

Recupera la página de códigos de entrada utilizada por la consola asociada al proceso de llamada. Una consola usa su página de códigos de entrada para traducir la entrada del teclado en el valor de carácter correspondiente.

## <a name="syntax"></a>Sintaxis

```C
UINT WINAPI GetConsoleCP(void);
```

## <a name="parameters"></a>Parámetros

Esta función no tiene parámetros.

## <a name="return-value"></a>Valor devuelto

El valor devuelto es un código que identifica la página de códigos. Para obtener una lista de identificadores, vea [identificadores de páginas de códigos](/windows/win32/intl/code-page-identifiers).

Si el valor devuelto es cero, se ha producido un error en la función. Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="remarks"></a>Comentarios

Una página de códigos asigna códigos de caracteres de 256 a caracteres individuales. Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas. Para recuperar más información sobre una página de códigos, incluido su nombre, vea la función [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) .

Para establecer la página de códigos de entrada de la consola, use la función [**SetConsoleCP**](setconsolecp.md) . Para establecer y consultar la página de códigos de salida de la consola, use las funciones [**SetConsoleOutputCP**](setconsoleoutputcp.md) y [**GetConsoleOutputCP**](getconsoleoutputcp.md) .

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Professional |
| Servidor mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Server |
| Encabezado | ConsoleApi.h (a través de WinCon.h, incluido Windows.h) |
| Biblioteca | Kernel32.lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Vea también

[Páginas de código de la consola](console-code-pages.md)

[Funciones de la consola](console-functions.md)

[**GetConsoleOutputCP**](getconsoleoutputcp.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)