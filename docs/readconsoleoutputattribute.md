---
title: ReadConsoleOutputAttribute función)
description: Copia un número especificado de atributos de carácter de las celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/ReadConsoleOutputAttribute
- wincon/ReadConsoleOutputAttribute
- ReadConsoleOutputAttribute
MS-HAID:
- '\_win32\_readconsoleoutputattribute'
- base.readconsoleoutputattribute
- consoles.readconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c3e35779-a487-47f1-8d07-0d5fae99d54a
topic_type:
- apiref
api_name:
- ReadConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: f64e39b7b68e24e6c2aa7e9704c285bbbbc234f0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039513"
---
# <a name="readconsoleoutputattribute-function"></a>ReadConsoleOutputAttribute función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Copia un número especificado de atributos de carácter de las celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI ReadConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPWORD  lpAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfAttrsRead
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de **\_ lectura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*lpAttribute* \[ enuncia\]  
Un puntero a un búfer que recibe los atributos utilizados por el búfer de pantalla de la consola.

Para obtener más información, vea [atributos de caracteres](console-screen-buffers.md#character-attributes).

*nLength* \[ de\]  
Número de celdas de caracteres del búfer de pantalla desde las que se van a leer. El tamaño del búfer al que apunta el parámetro *lpAttribute* debe ser `nLength * sizeof(WORD)` .

*dwReadCoord* \[ de\]  
Coordenadas de la primera celda en el búfer de pantalla de la consola desde la que se va a leer, en caracteres. El miembro **X** de la estructura [**coordenadas**](coord-str.md) es la columna y el miembro **y** es la fila.

*lpNumberOfAttrsRead* \[ enuncia\]  
Puntero a una variable que recibe el número de atributos leídos realmente.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

Si el número de atributos que se van a leer de se extiende más allá del final de la fila de búfer de pantalla especificada, los atributos se leen de la fila siguiente. Si el número de atributos que se van a leer se extiende más allá del final del búfer de pantalla de la consola, se leen los atributos hasta el final del búfer de pantalla de la consola.

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

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

[**COORDS**](coord-str.md)

[Funciones de salida de la consola de bajo nivel](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)
