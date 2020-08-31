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
ms.openlocfilehash: bc313abbcb28016968355cc405e0cc2de3d36cb0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061043"
---
# <a name="writeconsoleoutputcharacter-function"></a>WriteConsoleOutputCharacter función)


Copia un número de caracteres en celdas consecutivas de un búfer de pantalla de la consola, comenzando en una ubicación especificada.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI WriteConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  LPCTSTR lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

<a name="parameters"></a>Parámetros
----------

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de ** \_ escritura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*lpCharacter* \[ de\]  
Caracteres que se van a escribir en el búfer de pantalla de la consola.

*nLength* \[ de\]  
El número de caracteres que se va a escribir.

*dwWriteCoord* \[ de\]  
Estructura de [**coordenadas**](coord-str.md) que especifica las coordenadas de caracteres de la primera celda en el búfer de pantalla de la consola en la que se escribirán los caracteres.

*lpNumberOfCharsWritten* \[ enuncia\]  
Puntero a una variable que recibe el número de caracteres escritos realmente.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

Si el número de caracteres que se va a escribir se extiende más allá del final de la fila especificada en el búfer de pantalla de la consola, los caracteres se escriben en la fila siguiente. Si el número de caracteres que se va a escribir se extiende más allá del final del búfer de pantalla de la consola, los caracteres se escriben al final del búfer de pantalla de la consola.

Los valores de atributo en las posiciones escritas en no cambian.

Esta función usa caracteres Unicode o caracteres de 8 bits de la página de códigos actual de la consola. La página de códigos de la consola tiene como valor predeterminado la página de códigos OEM del sistema. Para cambiar la página de códigos de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) , o bien use los comandos **chcp** o **mode con CP Select =** .

<a name="requirements"></a>Requisitos
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Cliente mínimo compatible</p></td>
<td><p>Windows 2000 Professional [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="even">
<td><p>Servidor mínimo compatible</p></td>
<td><p>Windows 2000 Server [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="odd">
<td><p>Encabezado</p></td>
<td>ConsoleApi2. h (a través de winCon. h, include Windows. h)</td>
</tr>
<tr class="even">
<td><p>Biblioteca</p></td>
<td>Kernel32. lib</td>
</tr>
<tr class="odd">
<td><p>Archivo DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
<td><p>Nombres Unicode y ANSI</p></td>
<td><p><strong>WriteConsoleOutputCharacterW</strong> (Unicode) y <strong>WriteConsoleOutputCharacterA</strong> (ANSI)</p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vea también


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

 

 




