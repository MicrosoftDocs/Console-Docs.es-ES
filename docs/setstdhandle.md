---
title: SetStdHandle función)
description: Establece el identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 36531872df90239e2b909c80fb75ad3011280c78
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039303"
---
# <a name="setstdhandle-function"></a>SetStdHandle función)

Establece el identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).

## <a name="syntax"></a>Sintaxis

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

## <a name="parameters"></a>Parámetros

*nStdHandle* \[ de\]  
El dispositivo estándar para el que se establecerá el identificador. Este parámetro puede ser uno de los valores siguientes.

| Valor | Significado |
|-|-|
| **STD_INPUT_HANDLE** (DWORD)-10 | El dispositivo de entrada estándar. Inicialmente, es el búfer de entrada de la consola, `CONIN$` . |
| **STD_OUTPUT_HANDLE** (DWORD)-11 | El dispositivo de salida estándar. Inicialmente, es el búfer de pantalla de la consola activo, `CONOUT$` . |
| **STD_ERROR_HANDLE** (DWORD)-12 | El dispositivo de error estándar. Inicialmente, es el búfer de pantalla de la consola activo, `CONOUT$` . |

*hHandle* \[ de\]  
Identificador del dispositivo estándar.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

Es posible que los identificadores estándar de un proceso se hayan Redirigido mediante una llamada a **SetStdHandle** , en cuyo caso [**GetStdHandle**](getstdhandle.md) devolverá el identificador redirigido. Si se han redirigido los identificadores estándar, puede especificar el valor de CONIN $ en una llamada a la función [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) para obtener un identificador para el búfer de entrada de la consola. De forma similar, puede especificar el valor de CONOUT $ para obtener un identificador para el búfer de pantalla activo de la consola.

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, consulte [creación de un proceso secundario con entrada y salida redirigidas](https://msdn.microsoft.com/library/windows/desktop/ms682499).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | ProcessEnv. h (a través de Winbase. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Consulte también

[Funciones de la consola](console-functions.md)

[Identificadores de consola](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetStdHandle**](getstdhandle.md)
