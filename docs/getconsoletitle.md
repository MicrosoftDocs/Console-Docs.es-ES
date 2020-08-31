---
title: GetConsoleTitle función)
description: Recupera el título y el tamaño del título de la ventana de la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/GetConsoleTitle
- wincon/GetConsoleTitle
- GetConsoleTitle
- consoleapi2/GetConsoleTitleA
- wincon/GetConsoleTitleA
- GetConsoleTitleA
- consoleapi2/GetConsoleTitleW
- wincon/GetConsoleTitleW
- GetConsoleTitleW
MS-HAID:
- '\_win32\_getconsoletitle'
- base.getconsoletitle
- consoles.getconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c58bba36-9813-4bdc-83bf-30d55f8d7d79
topic_type:
- apiref
api_name:
- GetConsoleTitle
- GetConsoleTitleA
- GetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-Ms-Win-Core-Console-Ansi-L2-1-0.dll
- Kernel32Legacy.dll
api_type:
- DllExport
ms.openlocfilehash: 5b8e78e65e52c3f10be14afa6a122fa12609a2eb
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060656"
---
# <a name="getconsoletitle-function"></a>GetConsoleTitle función)


Recupera el título de la ventana de la consola actual.

<a name="syntax"></a>Sintaxis
------

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a>Parámetros
----------

*lpConsoleTitle* \[ enuncia\]  
Un puntero a un búfer que recibe una cadena terminada en null que contiene el título. Si el búfer es demasiado pequeño para almacenar el título, la función almacena tantos caracteres del título como quepan en el búfer, terminando con un terminador null.

*nSize* \[ de\]  
Tamaño del búfer al que apunta el parámetro *lpConsoleTitle* , en caracteres.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es la longitud del título de la ventana de la consola, en caracteres.

Si se produce un error en la función, el valor devuelto es cero y [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) devuelve el código de error.

<a name="remarks"></a>Observaciones
-------

Para establecer el título de una ventana de la consola, use la función [**SetConsoleTitle**](setconsoletitle.md) . Para recuperar la cadena de título original, utilice la función [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) .

Esta función usa caracteres Unicode o caracteres de 8 bits de la página de códigos actual de la consola. La página de códigos de la consola tiene como valor predeterminado la página de códigos OEM del sistema. Para cambiar la página de códigos de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) , o bien use los comandos **chcp** o **mode con CP Select =** .

<a name="examples"></a>Ejemplos
--------

Para obtener un ejemplo, vea [**SetConsoleTitle**](setconsoletitle.md).

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
<td><p><strong>GetConsoleTitleW</strong> (Unicode) y <strong>GetConsoleTitleA</strong> (ANSI)</p></td>
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

[**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleTitle**](setconsoletitle.md)

 

 




