---
title: FillConsoleOutputCharacter función)
description: Escribe un carácter en el búfer de la pantalla de la consola un número especificado de veces, comenzando en las coordenadas especificadas.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/FillConsoleOutputCharacter
- wincon/FillConsoleOutputCharacter
- FillConsoleOutputCharacter
- consoleapi2/FillConsoleOutputCharacterA
- wincon/FillConsoleOutputCharacterA
- FillConsoleOutputCharacterA
- consoleapi2/FillConsoleOutputCharacterW
- wincon/FillConsoleOutputCharacterW
- FillConsoleOutputCharacterW
MS-HAID:
- '\_win32\_fillconsoleoutputcharacter'
- base.fillconsoleoutputcharacter
- consoles.fillconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 37579cc9-14b3-4fd9-81ed-abaad5c7bd1a
topic_type:
- apiref
api_name:
- FillConsoleOutputCharacter
- FillConsoleOutputCharacterA
- FillConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 8860a1feab39bc83f28a867fa9acc491cc00e4b7
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038193"
---
# <a name="fillconsoleoutputcharacter-function"></a>FillConsoleOutputCharacter función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Escribe un carácter en el búfer de la pantalla de la consola un número especificado de veces, comenzando en las coordenadas especificadas.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de **\_ escritura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*cCharacter* \[ de\]  
Carácter que se va a escribir en el búfer de pantalla de la consola.

*nLength* \[ de\]  
El número de celdas de caracteres en las que se debe escribir el carácter.

*dwWriteCoord* \[ de\]  
Estructura de [**coordenadas**](coord-str.md) que especifica las coordenadas de caracteres de la primera celda en la que se va a escribir el carácter.

*lpNumberOfCharsWritten* \[ enuncia\]  
Puntero a una variable que recibe el número de caracteres escritos realmente en el búfer de pantalla de la consola.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

Si el número de caracteres que se va a escribir se extiende más allá del final de la fila especificada en el búfer de pantalla de la consola, los caracteres se escriben en la fila siguiente. Si el número de caracteres que se va a escribir se extiende más allá del final del búfer de pantalla de la consola, los caracteres se escriben al final del búfer de pantalla de la consola.

Los valores de atributo en las posiciones escritas no cambian.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Esta API no se recomienda y no tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** específico equivalente. No se admite el rellenado de la región fuera de la ventana visible y se reserva para el espacio de historial del terminal. El rellenado de un área visible con nuevo texto o color se realiza mediante el **[movimiento del cursor](console-virtual-terminal-sequences.md#cursor-positioning)** , **[la configuración de los nuevos atributos](console-virtual-terminal-sequences.md#text-formatting)** y la escritura del texto deseado para esa región, repitiendo los caracteres si es necesario para la longitud de la ejecución de relleno. Es posible que se requiera un movimiento de cursor adicional seguido de la escritura del texto deseado para rellenar una región rectangular. Se espera que la aplicación cliente mantenga su propia memoria de lo que se encuentra en la pantalla y que no puede consultar el estado remoto. Puede encontrar más información en la **[consola clásica](classic-vs-vt.md)** y en la documentación de terminal virtual.

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | ConsoleApi2. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |
| Nombres Unicode y ANSI | **FillConsoleOutputCharacterW** (Unicode) y **FillConsoleOutputCharacterA** (ANSI) |

## <a name="see-also"></a>Consulte también

[Funciones de la consola](console-functions.md)

[**COORDS**](coord-str.md)

[**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)

[Funciones de salida de la consola de bajo nivel](low-level-console-output-functions.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)
