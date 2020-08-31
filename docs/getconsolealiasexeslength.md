---
title: GetConsoleAliasExesLength función)
description: Recupera el tamaño necesario para el búfer usado por la función GetConsoleAliasExes.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapie/GetConsoleAliasExesLength
- wincon/GetConsoleAliasExesLength
- GetConsoleAliasExesLength
- consoleapie/GetConsoleAliasExesLengthA
- wincon/GetConsoleAliasExesLengthA
- GetConsoleAliasExesLengthA
- consoleapie/GetConsoleAliasExesLengthW
- wincon/GetConsoleAliasExesLengthW
- GetConsoleAliasExesLengthW
MS-HAID:
- base.getconsolealiasexeslength
- consoles.getconsolealiasexeslength
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 4f23bbb1-3e43-47a9-b91a-e91529b07fb5
topic_type:
- apiref
api_name:
- GetConsoleAliasExesLength
- GetConsoleAliasExesLengthA
- GetConsoleAliasExesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0f4459254e9382a0c784ceb2c214af056087ab1b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060705"
---
# <a name="getconsolealiasexeslength-function"></a>GetConsoleAliasExesLength función)


Recupera el tamaño necesario para el búfer usado por la función [**GetConsoleAliasExes**](getconsolealiasexes.md) .

<a name="syntax"></a>Sintaxis
------

```C
DWORD WINAPI GetConsoleAliasExesLength(void);
```

<a name="parameters"></a>Parámetros
----------

Esta función no tiene parámetros.

<a name="return-value"></a>Valor devuelto
------------

Tamaño del búfer necesario para almacenar los nombres de todos los archivos ejecutables que tienen definidos alias de consola, en bytes.

<a name="remarks"></a>Observaciones
-------

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
<td><p><strong>GetConsoleAliasExesLengthW</strong> (Unicode) y <strong>GetConsoleAliasExesLengthA</strong> (ANSI)</p></td>
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

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)

 

 




