---
title: WriteConsoleOutputCharacter función)
description: Copia un número de caracteres en celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/WriteConsoleOutputCharacter
- wincon/WriteConsoleOutputCharacter
- WriteConsoleOutputCharacter
- consoleapi2/WriteConsoleOutputCharacterA
- wincon/WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterA
- consoleapi2/WriteConsoleOutputCharacterW
- wincon/WriteConsoleOutputCharacterW
- WriteConsoleOutputCharacterW
MS-HAID:
- '\_win32\_writeconsoleoutputcharacter'
- base.writeconsoleoutputcharacter
- consoles.writeconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 7cc935ea-6b19-4494-b746-259aa7aaa9cc
topic_type:
- apiref
api_name:
- WriteConsoleOutputCharacter
- WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 462ebfaed09a5c18fa9a075227a5568a789685bd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037213"
---
# <a name="writeconsoleoutputcharacter-function"></a>WriteConsoleOutputCharacter función)

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Copia un número de caracteres en celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.

## <a name="syntax"></a>Sintaxis

```C
BOOL WINAPI WriteConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  LPCTSTR lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a>Parámetros

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de **\_ escritura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*lpCharacter* \[ de\]  
Caracteres que se van a escribir en el búfer de pantalla de la consola.

*nLength* \[ de\]  
El número de caracteres que se va a escribir.

*dwWriteCoord* \[ de\]  
Estructura de [**coordenadas**](coord-str.md) que especifica las coordenadas de caracteres de la primera celda en el búfer de pantalla de la consola en la que se escribirán los caracteres.

*lpNumberOfCharsWritten* \[ enuncia\]  
Puntero a una variable que recibe el número de caracteres escritos realmente.

## <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

## <a name="remarks"></a>Comentarios

Si el número de caracteres que se va a escribir se extiende más allá del final de la fila especificada en el búfer de pantalla de la consola, los caracteres se escriben en la fila siguiente. Si el número de caracteres que se va a escribir se extiende más allá del final del búfer de pantalla de la consola, los caracteres se escriben al final del búfer de pantalla de la consola.

Los valores de atributo en las posiciones escritas en no cambian.

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> Esta API tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente en las secuencias de **[formato de texto](console-virtual-terminal-sequences.md#text-formatting)** y **[posición del cursor](console-virtual-terminal-sequences.md#cursor-positioning)** . Mueva el cursor a la ubicación que se va a insertar, aplique el formato deseado y escriba el texto para rellenar. No hay ningún equivalente para emitir texto en un área sin aplicar también el formato de color activo. Esta decisión alinea intencionadamente la plataforma de Windows con otros sistemas operativos en los que se espera que la aplicación cliente individual Recuerde su propio estado dibujado para su posterior manipulación.

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | ConsoleApi2. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |
| Nombres Unicode y ANSI | **WriteConsoleOutputCharacterW** (Unicode) y **WriteConsoleOutputCharacterA** (ANSI) |

## <a name="see-also"></a>Consulte también

[Funciones de la consola](console-functions.md)

[**COORDS**](coord-str.md)

[Funciones de salida de la consola de bajo nivel](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)
