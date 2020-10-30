---
title: GetConsoleCursorInfo función)
description: Recupera información sobre el tamaño y la visibilidad del cursor para el búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/GetConsoleCursorInfo
- wincon/GetConsoleCursorInfo
- GetConsoleCursorInfo
MS-HAID:
- '\_win32\_getconsolecursorinfo'
- base.getconsolecursorinfo
- consoles.getconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6200577d-8d84-46bd-9330-d0b6cbbb3e52
topic_type:
- apiref
api_name:
- GetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 2d9869c5c291addaf94a06fa67e11e3195ead686
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038923"
---
# <a name="getconsolecursorinfo-function"></a>GetConsoleCursorInfo función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Recupera información sobre el tamaño y la visibilidad del cursor para el búfer de pantalla de la consola especificado.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI GetConsoleCursorInfo(
  _In_  HANDLE               hConsoleOutput,
  _Out_ PCONSOLE_CURSOR_INFO lpConsoleCursorInfo
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de **\_ lectura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*lpConsoleCursorInfo* \[ enuncia\]  
Puntero a una estructura [**de \_ \_ información del cursor**](console-cursor-info-str.md) de la consola que recibe información sobre el cursor de la consola.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Observaciones

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | ConsoleApi2. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Consulte también

[Funciones de la consola](console-functions.md)

[Búferes de pantalla de la consola](console-screen-buffers.md)

[**\_información del cursor de la consola \_**](console-cursor-info-str.md)

[**SetConsoleCursorInfo**](setconsolecursorinfo.md)
