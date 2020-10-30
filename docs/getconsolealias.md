---
title: GetConsoleAlias función)
description: Recupera el texto para el alias de consola especificado y el nombre del archivo ejecutable.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleAlias
- wincon/GetConsoleAlias
- GetConsoleAlias
- consoleapi3/GetConsoleAliasA
- wincon/GetConsoleAliasA
- GetConsoleAliasA
- consoleapi3/GetConsoleAliasW
- wincon/GetConsoleAliasW
- GetConsoleAliasW
MS-HAID:
- base.getconsolealias
- consoles.getconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e8514f24-8121-4fad-94bb-c9eedf7a700d
topic_type:
- apiref
api_name:
- GetConsoleAlias
- GetConsoleAliasA
- GetConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 37c441c48c2bb71fc8e590d4f8a80032561f833e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039033"
---
# <a name="getconsolealias-function"></a>GetConsoleAlias función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Recupera el texto para el archivo ejecutable y el alias de consola especificados.

## <a name="syntax"></a>Sintaxis

```C
DWORD WINAPI GetConsoleAlias(
  _In_  LPTSTR lpSource,
  _Out_ LPTSTR lpTargetBuffer,
  _In_  DWORD  TargetBufferLength,
  _In_  LPTSTR lpExeName
);
```

## <a name="parameters"></a>Parámetros

*lpSource* \[ de\]  
El alias de la consola cuyo texto se va a recuperar.

*lpTargetBuffer* \[ enuncia\]  
Un puntero a un búfer que recibe el texto asociado al alias de la consola.

*TargetBufferLength* \[ de\]  
Tamaño del búfer al que apunta *lpTargetBuffer* , en bytes.

*lpExeName* \[ de\]  
Nombre del archivo ejecutable.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0501 o posterior. Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | ConsoleApi3. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |
| Nombres Unicode y ANSI | **GetConsoleAliasW** (Unicode) y **GetConsoleAliasA** (ANSI) |

## <a name="see-also"></a>Consulte también

[Alias de la consola](console-aliases.md)

[Funciones de la consola](console-functions.md)

[**AddConsoleAlias**](addconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)
