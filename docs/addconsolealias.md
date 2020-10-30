---
title: AddConsoleAlias función)
description: Vea la información de referencia sobre la función AddConsoleAlias, que define un alias de consola para el ejecutable especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/AddConsoleAlias
- consoleapi3/AddConsoleAliasA
- consoleapi3/AddConsoleAliasW
- wincon/AddConsoleAlias
- wincon/AddConsoleAliasA
- wincon/AddConsoleAliasW
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
MS-HAID:
- base.addconsolealias
- consoles.addconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e4072c3c-cf32-4992-847e-efdb846e5784
topic_type:
- apiref
api_name:
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 2f2396122e693ab76ddf4e4e0bcdb2d38a2c042b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037560"
---
# <a name="addconsolealias-function"></a>AddConsoleAlias función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Define un alias de consola para el ejecutable especificado.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

## <a name="parameters"></a>Parámetros

*Origen* \[ de de\]  
El alias de la consola que se va a asignar al texto especificado por el *destino* .

*Destino* \[ de de\]  
Texto que se va a sustituir por el *origen* . Si este parámetro es **null** , se quita el alias de la consola.

*ExeName* \[ de\]  
Nombre del archivo ejecutable para el que se va a definir el alias de la consola.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es **true** .

Si se produce un error en la función, el valor devuelto es **false** . Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0501 o posterior. Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, vea [alias de consola](console-aliases.md).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | ConsoleApi3. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |
| Nombres Unicode y ANSI | **AddConsoleAliasW** (Unicode) y **AddConsoleAliasA** (ANSI) |

## <a name="see-also"></a>Consulte también

[Alias de la consola](console-aliases.md)

[Funciones de la consola](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)
