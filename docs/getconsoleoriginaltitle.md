---
title: GetConsoleOriginalTitle función)
description: Vea la información de referencia sobre la función GetConsoleOriginalTitle, que recupera el título original de la ventana de la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 109d41a141083fc4691ebaf2546ec8f412f7b861
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060673"
---
# <a name="getconsoleoriginaltitle-function"></a>GetConsoleOriginalTitle función)


Recupera el título original de la ventana de la consola actual.

<a name="syntax"></a>Sintaxis
------

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a>Parámetros
----------

*lpConsoleTitle* \[ enuncia\]  
Un puntero a un búfer que recibe una cadena terminada en null que contiene el título original.

*nSize* \[ de\]  
Tamaño del búfer de *lpConsoleTitle* , en caracteres.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es la longitud de la cadena copiada en el búfer, en caracteres.

Si el búfer no es lo suficientemente grande como para almacenar el título, el valor devuelto es cero y [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) devuelve el **error \_ Success**.

Si se produce un error en la función, el valor devuelto es cero y [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) devuelve el código de error.

<a name="remarks"></a>Observaciones
-------

Para establecer el título de una ventana de la consola, use la función [**SetConsoleTitle**](setconsoletitle.md) . Para recuperar la cadena de título actual, utilice la función [**GetConsoleTitle**](getconsoletitle.md) .

Para compilar una aplicación que usa esta función, defina ** \_ Win32 \_ WinNT** como 0x0600 o posterior. Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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
<td><p>Windows Vista [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="even">
<td><p>Servidor mínimo compatible</p></td>
<td><p>Windows Server 2008 [solo aplicaciones de escritorio]</p></td>
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
<td><p><strong>GetConsoleOriginalTitleW</strong> (Unicode) y <strong>GetConsoleOriginalTitleA</strong> (ANSI)</p></td>
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

[**GetConsoleTitle**](getconsoletitle.md)

[**SetConsoleTitle**](setconsoletitle.md)

 

 




