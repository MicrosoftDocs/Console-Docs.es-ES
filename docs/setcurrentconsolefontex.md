---
title: SetCurrentConsoleFontEx función)
description: Consulte la información de referencia sobre la función SetCurrentConsoleFontEx, que establece la información extendida sobre la fuente de consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/SetCurrentConsoleFontEx
- wincon/SetCurrentConsoleFontEx
- SetCurrentConsoleFontEx
MS-HAID:
- base.setcurrentconsolefontex
- consoles.setcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: fbc31e2a-31df-4e9e-9f61-35a4ff812f8f
topic_type:
- apiref
api_name:
- SetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 1ba89b90a0362261aafbe5ac6462224b3c0172dc
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037060"
---
# <a name="setcurrentconsolefontex-function"></a>SetCurrentConsoleFontEx función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Establece la información extendida sobre la fuente de consola actual.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI SetCurrentConsoleFontEx(
  _In_ HANDLE               hConsoleOutput,
  _In_ BOOL                 bMaximumWindow,
  _In_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de **\_ escritura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*bMaximumWindow* \[ de\]  
Si este parámetro es **true** , la información de fuente se establece para el tamaño máximo de la ventana. Si este parámetro es **false** , se establece la información de fuente para el tamaño de la ventana actual.

*lpConsoleCurrentFontEx* \[ de\]  
Puntero a una estructura [**\_ \_ INFOEX**](console-font-infoex.md) de la fuente de la consola que contiene la información de la fuente.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0500 o posterior. Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows Vista \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows Server 2008 \[\] |
| Encabezado | ConsoleApi3. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Consulte también

[Funciones de la consola](console-functions.md)

[**fuente de consola \_ \_ INFOEX**](console-font-infoex.md)
