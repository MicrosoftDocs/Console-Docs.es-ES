---
title: ReadConsoleOutput función)
description: Lee datos de atributos de caracteres y colores de un bloque rectangular de celdas de caracteres en un búfer de pantalla de la consola y escribe datos en el búfer de destino.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/ReadConsoleOutput
- wincon/ReadConsoleOutput
- ReadConsoleOutput
- consoleapi2/ReadConsoleOutputA
- wincon/ReadConsoleOutputA
- ReadConsoleOutputA
- consoleapi2/ReadConsoleOutputW
- wincon/ReadConsoleOutputW
- ReadConsoleOutputW
MS-HAID:
- '\_win32\_readconsoleoutput'
- base.readconsoleoutput
- consoles.readconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d1391684-6a8f-4b5e-9706-11970a957710
topic_type:
- apiref
api_name:
- ReadConsoleOutput
- ReadConsoleOutputA
- ReadConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0ce2a5a62ee7719d0184247c9ef3327850e12c1b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037763"
---
# <a name="readconsoleoutput-function"></a>ReadConsoleOutput función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Lee los datos de atributos de caracteres y colores de un bloque rectangular de celdas de caracteres en un búfer de pantalla de la consola, y la función escribe los datos en un bloque rectangular en una ubicación especificada del búfer de destino.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI ReadConsoleOutput(
  _In_    HANDLE      hConsoleOutput,
  _Out_   PCHAR_INFO  lpBuffer,
  _In_    COORD       dwBufferSize,
  _In_    COORD       dwBufferCoord,
  _Inout_ PSMALL_RECT lpReadRegion
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de **\_ lectura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*lpBuffer* \[ enuncia\]  
Un puntero a un búfer de destino que recibe los datos leídos del búfer de pantalla de la consola. Este puntero se trata como el origen de una matriz bidimensional de estructuras [**de \_ información de char**](char-info-str.md) cuyo tamaño se especifica mediante el parámetro *dwBufferSize* .

*dwBufferSize* \[ de\]  
Tamaño del parámetro *lpBuffer* , en celdas de carácter. El miembro **X** de la estructura [**coordenadas**](coord-str.md) es el número de columnas; el miembro **Y** es el número de filas.

*dwBufferCoord* \[ de\]  
Coordenadas de la celda superior izquierda del parámetro *lpBuffer* que recibe los datos leídos del búfer de pantalla de la consola. El miembro **X** de la estructura [**coordenadas**](coord-str.md) es la columna y el miembro **y** es la fila.

*lpReadRegion* \[ in, out\]  
Puntero a una estructura [**\_ Rect pequeña**](small-rect-str.md) . En la entrada, los miembros de la estructura especifican las coordenadas superior izquierda e inferior derecha del rectángulo del búfer de pantalla de la consola desde el que se va a leer la función. En la salida, los miembros de la estructura especifican el rectángulo real que se usó.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

**ReadConsoleOutput** trata el búfer de pantalla de la consola y el búfer de destino como matrices bidimensionales (columnas y filas de celdas de caracteres). El rectángulo al que apunta el parámetro *lpReadRegion* especifica el tamaño y la ubicación del bloque que se va a leer desde el búfer de pantalla de la consola. Un rectángulo de destino del mismo tamaño se encuentra con la celda superior izquierda en las coordenadas del parámetro *dwBufferCoord* en la matriz *lpBuffer* . Los datos leídos de las celdas del rectángulo de origen del búfer de pantalla de la consola se copian en las celdas correspondientes del búfer de destino. Si la celda correspondiente está fuera de los límites del rectángulo del búfer de destino (cuyas dimensiones se especifican mediante el parámetro *dwBufferSize* ), los datos no se copian.

Las celdas del búfer de destino que se corresponden con las coordenadas que no están dentro de los límites del búfer de pantalla de la consola permanecen sin cambios. En otras palabras, se trata de las celdas para las que no hay datos de búfer de pantalla disponibles para leer.

Antes de que **ReadConsoleOutput** devuelva, establece los miembros de la estructura a la que apunta el parámetro *lpReadRegion* en el rectángulo del búfer de pantalla real cuyas celdas se copiaron en el búfer de destino. Este rectángulo refleja las celdas del rectángulo de origen para las que existía una celda correspondiente en el búfer de destino, porque **ReadConsoleOutput** recorta las dimensiones del rectángulo de origen para ajustarse a los límites del búfer de pantalla de la consola.

Si el rectángulo especificado por *lpReadRegion* se encuentra completamente fuera de los límites del búfer de pantalla de la consola, o si el rectángulo correspondiente se coloca completamente fuera de los límites del búfer de destino, no se copia ningún dato. En este caso, la función devuelve con los miembros de la estructura a la que apunta el conjunto de parámetros *lpReadRegion* , de modo que el miembro de la **derecha** es menor que el **izquierdo** , o el miembro **inferior** es menor que la **parte superior** . Para determinar el tamaño del búfer de pantalla de la consola, use la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .

La función **ReadConsoleOutput** no tiene ningún efecto en la posición del cursor del búfer de la pantalla de la consola. La función no cambia el contenido del búfer de pantalla de la consola.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, vea [lectura y escritura de bloques de caracteres y atributos](reading-and-writing-blocks-of-characters-and-attributes.md).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | ConsoleApi2. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |
| Nombres Unicode y ANSI | **ReadConsoleOutputW** (Unicode) y **ReadConsoleOutputA** (ANSI) |

## <a name="see-also"></a>Consulte también

[Funciones de la consola](console-functions.md)

[Funciones de salida de la consola de bajo nivel](low-level-console-output-functions.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**PEQUEÑO \_ rectángulo**](small-rect-str.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**información de carácter \_**](char-info-str.md)

[**COORDS**](coord-str.md)
