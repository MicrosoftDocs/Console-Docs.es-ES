---
title: FillConsoleOutputAttribute función)
description: Establece los atributos de carácter para un número especificado de celdas de caracteres, a partir de las coordenadas especificadas en un búfer de pantalla.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/FillConsoleOutputAttribute
- wincon/FillConsoleOutputAttribute
- FillConsoleOutputAttribute
MS-HAID:
- '\_win32\_fillconsoleoutputattribute'
- base.fillconsoleoutputattribute
- consoles.fillconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 09440263-71c4-4b7a-8fc6-a2b4fcd677ff
topic_type:
- apiref
api_name:
- FillConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 40eb97e43e406d68ff625db110998ebf69eb26f7
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039073"
---
# <a name="fillconsoleoutputattribute-function"></a>FillConsoleOutputAttribute función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Establece los atributos de carácter para un número especificado de celdas de caracteres, a partir de las coordenadas especificadas en un búfer de pantalla.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de **\_ escritura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*wAttribute* \[ de\]  
Atributos que se van a usar al escribir en el búfer de pantalla de la consola. Para obtener más información, vea [atributos de caracteres](console-screen-buffers.md#character-attributes).

*nLength* \[ de\]  
El número de celdas de caracteres que se van a establecer en los atributos de color especificados.

*dwWriteCoord* \[ de\]  
Estructura de [**coordenadas**](coord-str.md) que especifica las coordenadas de caracteres de la primera celda cuyos atributos se van a establecer.

*lpNumberOfAttrsWritten* \[ enuncia\]  
Puntero a una variable que recibe el número de celdas de caracteres cuyos atributos se establecieron realmente.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

Si el número de celdas de caracteres cuyos atributos se van a establecer se extiende más allá del final de la fila especificada en el búfer de pantalla de la consola, se establecen las celdas de la fila siguiente. Si el número de celdas que se van a escribir se extiende más allá del final del búfer de pantalla de la consola, las celdas se escriben hasta el final del búfer de pantalla de la consola.

Los valores de caracteres en las posiciones escritas en no cambian.

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

## <a name="see-also"></a>Consulte también

[Funciones de la consola](console-functions.md)

[**COORDS**](coord-str.md)

[**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)

[Funciones de salida de la consola de bajo nivel](low-level-console-output-functions.md)

[**SetConsoleTextAttribute**](setconsoletextattribute.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)
