---
title: WriteConsoleOutput función)
description: Escribe datos de atributos de caracteres y colores en un bloque rectangular especificado de celdas de caracteres en un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/WriteConsoleOutput
- wincon/WriteConsoleOutput
- WriteConsoleOutput
- consoleapi2/WriteConsoleOutputA
- wincon/WriteConsoleOutputA
- WriteConsoleOutputA
- consoleapi2/WriteConsoleOutputW
- wincon/WriteConsoleOutputW
- WriteConsoleOutputW
MS-HAID:
- '\_win32\_writeconsoleoutput'
- base.writeconsoleoutput
- consoles.writeconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a98b8118-97ce-4dd4-a337-122d4a76f232
topic_type:
- apiref
api_name:
- WriteConsoleOutput
- WriteConsoleOutputA
- WriteConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: b67f741aafcb067e85d339d550646261a46c273a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037263"
---
# <a name="writeconsoleoutput-function"></a>WriteConsoleOutput función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Escribe datos de atributos de caracteres y colores en un bloque rectangular especificado de celdas de caracteres en un búfer de pantalla de la consola. Los datos que se van a escribir se toman de un bloque rectangular de tamaño correspondiente en una ubicación especificada del búfer de origen.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI WriteConsoleOutput(
  _In_          HANDLE      hConsoleOutput,
  _In_    const CHAR_INFO   *lpBuffer,
  _In_          COORD       dwBufferSize,
  _In_          COORD       dwBufferCoord,
  _Inout_       PSMALL_RECT lpWriteRegion
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de **\_ escritura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*lpBuffer* \[ de\]  
Los datos que se van a escribir en el búfer de pantalla de la consola. Este puntero se trata como el origen de una matriz bidimensional de estructuras [**de \_ información de char**](char-info-str.md) cuyo tamaño se especifica mediante el parámetro *dwBufferSize* .

*dwBufferSize* \[ de\]  
Tamaño del búfer al que apunta el parámetro *lpBuffer* , en celdas de caracteres. El miembro **X** de la estructura [**coordenadas**](coord-str.md) es el número de columnas; el miembro **Y** es el número de filas.

*dwBufferCoord* \[ de\]  
Coordenadas de la celda superior izquierda del búfer a la que apunta el parámetro *lpBuffer* . El miembro **X** de la estructura [**coordenadas**](coord-str.md) es la columna y el miembro **y** es la fila.

*lpWriteRegion* \[ in, out\]  
Puntero a una estructura [**\_ Rect pequeña**](small-rect-str.md) . En la entrada, los miembros de la estructura especifican las coordenadas superior izquierda e inferior derecha del rectángulo del búfer de pantalla de la consola en el que se va a escribir. En la salida, los miembros de la estructura especifican el rectángulo real que se usó.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

**WriteConsoleOutput** trata el búfer de origen y el búfer de pantalla de destino como matrices bidimensionales (columnas y filas de celdas de caracteres). El rectángulo al que apunta el parámetro *lpWriteRegion* especifica el tamaño y la ubicación del bloque en el que se va a escribir en el búfer de pantalla de la consola. Un rectángulo del mismo tamaño se encuentra con la celda superior izquierda en las coordenadas del parámetro *dwBufferCoord* en la matriz *lpBuffer* . Los datos de las celdas que están en la intersección de este rectángulo y el rectángulo del búfer de origen (cuyas dimensiones se especifican mediante el parámetro *dwBufferSize* ) se escriben en el rectángulo de destino.

Las celdas del rectángulo de destino cuya ubicación de origen correspondiente están fuera de los límites del rectángulo del búfer de origen dejan de ser afectadas por la operación de escritura. En otras palabras, se trata de las celdas para las que no hay datos disponibles para su escritura.

Antes de que **WriteConsoleOutput** devuelva, establece los miembros de *lpWriteRegion* en el rectángulo del búfer de pantalla real afectado por la operación de escritura. Este rectángulo refleja las celdas del rectángulo de destino para las que existe una celda correspondiente en el búfer de origen, porque **WriteConsoleOutput** recorta las dimensiones del rectángulo de destino en los límites del búfer de pantalla de la consola.

Si el rectángulo especificado por *lpWriteRegion* se encuentra completamente fuera de los límites del búfer de pantalla de la consola, o si el rectángulo correspondiente se coloca completamente fuera de los límites del búfer de origen, no se escribe ningún dato. En este caso, la función devuelve con los miembros de la estructura a la que apunta el conjunto de parámetros *lpWriteRegion* , de modo que el miembro de la **derecha** es menor que el **izquierdo** , o el miembro **inferior** es menor que la **parte superior** . Para determinar el tamaño del búfer de pantalla de la consola, use la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .

**WriteConsoleOutput** no tiene ningún efecto en la posición del cursor.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Esta API tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente en las secuencias de **[formato de texto](console-virtual-terminal-sequences.md#text-formatting)** y **[posición del cursor](console-virtual-terminal-sequences.md#cursor-positioning)** . Mueva el cursor a la ubicación que se va a insertar, aplique el formato deseado y escriba el texto. Se recomiendan las _secuencias de terminal virtuales_ para todo el desarrollo nuevo y en curso.

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
| Nombres Unicode y ANSI | **WriteConsoleOutputW** (Unicode) y **WriteConsoleOutputA** (ANSI) |

## <a name="see-also"></a>Consulte también

[Funciones de la consola](console-functions.md)

[**información de carácter \_**](char-info-str.md)

[**COORDS**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[Funciones de salida de la consola de bajo nivel](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**PEQUEÑO \_ rectángulo**](small-rect-str.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)
