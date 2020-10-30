---
title: SetConsoleHistoryInfo función)
description: Establece la configuración del historial para la consola de Windows del proceso que realiza la llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/SetConsoleHistoryInfo
- wincon/SetConsoleHistoryInfo
- SetConsoleHistoryInfo
MS-HAID:
- base.setconsolehistoryinfo
- consoles.setconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: db180f53-aa3c-4a91-bc3e-9f3f0bb7ab01
topic_type:
- apiref
api_name:
- SetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 618661b8c59506e2ba5e1f2b2b283ccf823b831a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039383"
---
# <a name="setconsolehistoryinfo-function"></a>SetConsoleHistoryInfo función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Establece la configuración del historial de la consola del proceso que realiza la llamada.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI SetConsoleHistoryInfo(
  _In_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a>Parámetros

*lpConsoleHistoryInfo* \[ de\]  
Un puntero a una estructura de [**\_ \_ información del historial**](console-history-info.md) de la consola que contiene la configuración del historial de la consola del proceso.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

Si el proceso de llamada no es un proceso de consola, se produce un error en la función y se establece el último código de error en **\_ acceso \_ denegado** .

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

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

[**\_información del historial de la consola \_**](console-history-info.md)

[**GetConsoleHistoryInfo**](getconsolehistoryinfo.md)
