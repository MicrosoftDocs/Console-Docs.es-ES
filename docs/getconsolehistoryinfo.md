---
title: GetConsoleHistoryInfo función)
description: Consulte la información de referencia sobre la función GetConsoleHistoryInfo, que recupera la configuración del historial de la consola del proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleHistoryInfo
- wincon/GetConsoleHistoryInfo
- GetConsoleHistoryInfo
MS-HAID:
- base.getconsolehistoryinfo
- consoles.getconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 145008b3-8a4a-4e6a-9144-ee787ce90ef4
topic_type:
- apiref
api_name:
- GetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 8335b7e23ffec0e894221f97f2c01be5b081d31f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038033"
---
# <a name="getconsolehistoryinfo-function"></a>GetConsoleHistoryInfo función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Recupera la configuración del historial de la consola del proceso que realiza la llamada.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a>Parámetros

*lpConsoleHistoryInfo* \[ enuncia\]  
Puntero a una estructura [**de \_ \_ información del historial**](console-history-info.md) de la consola que recibe la configuración del historial de la consola del proceso que realiza la llamada.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

Si el proceso de llamada no es un proceso de consola, se produce un error en la función y se establece el último error en **\_ acceso \_ denegado** .

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

[**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)
