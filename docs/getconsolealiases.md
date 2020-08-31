---
title: GetConsoleAliases función)
description: Recupera todos los alias de consola definidos para el ejecutable especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleAliases
- wincon/GetConsoleAliases
- GetConsoleAliases
- consoleapi3/GetConsoleAliasesA
- wincon/GetConsoleAliasesA
- GetConsoleAliasesA
- consoleapi3/GetConsoleAliasesW
- wincon/GetConsoleAliasesW
- GetConsoleAliasesW
MS-HAID:
- base.getconsolealiases
- consoles.getconsolealiases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 92eefa4e-ffde-4886-afde-5aecf450b425
topic_type:
- apiref
api_name:
- GetConsoleAliases
- GetConsoleAliasesA
- GetConsoleAliasesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 9e8e28323d5b696390d574a86561d7414f419bcc
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060713"
---
# <a name="getconsolealiases-function"></a>GetConsoleAliases función)


Recupera todos los alias de consola definidos para el ejecutable especificado.

<a name="syntax"></a>Sintaxis
------

```C
DWORD WINAPI GetConsoleAliases(
  _Out_ LPTSTR lpAliasBuffer,
  _In_  DWORD  AliasBufferLength,
  _In_  LPTSTR lpExeName
);
```

<a name="parameters"></a>Parámetros
----------

*lpAliasBuffer* \[ enuncia\]  
Un puntero a un búfer que recibe los alias.

El formato de los datos es el siguiente: *Source1* = *Target1* \\ 0*source2* = *TARGET2* \\ 0... *Código fuente* = *Destino* \\ 0, donde *N* es el número de alias de consola definidos.

*AliasBufferLength* \[ de\]  
Tamaño del búfer al que apunta *lpAliasBuffer*, en bytes.

*lpExeName* \[ de\]  
Archivo ejecutable cuyos alias se van a recuperar.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

Para determinar el tamaño necesario para el búfer de *lpExeName* , use la función [**GetConsoleAliasesLength**](getconsolealiaseslength.md) .

Para compilar una aplicación que usa esta función, defina ** \_ Win32 \_ WinNT** como 0x0501 o posterior. Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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
<td>ConsoleApi3. h (a través de winCon. h, include Windows. h)</td>
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
<td><p><strong>GetConsoleAliasesW</strong> (Unicode) y <strong>GetConsoleAliasesA</strong> (ANSI)</p></td>
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


[**AddConsoleAlias**](addconsolealias.md)

[Alias de la consola](console-aliases.md)

[Funciones de la consola](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliasesLength**](getconsolealiaseslength.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)

 

 




