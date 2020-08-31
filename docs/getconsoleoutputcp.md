---
title: GetConsoleOutputCP función)
description: Recupera la página de códigos de salida utilizada por la consola asociada al proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/GetConsoleOutputCP
- wincon/GetConsoleOutputCP
- GetConsoleOutputCP
MS-HAID:
- '\_win32\_getconsoleoutputcp'
- base.getconsoleoutputcp
- consoles.getconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c23706c7-ce17-4825-a494-20ca44534d45
topic_type:
- apiref
api_name:
- GetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: e80618ebd5c6b29f00e79594c55bfa15fab315ba
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060684"
---
# <a name="getconsoleoutputcp-function"></a>GetConsoleOutputCP función)


Recupera la página de códigos de salida utilizada por la consola asociada al proceso de llamada. Una consola usa su página de códigos de salida para traducir los valores de caracteres escritos por las distintas funciones de salida en las imágenes que se muestran en la ventana de la consola.

<a name="syntax"></a>Sintaxis
------

```C
UINT WINAPI GetConsoleOutputCP(void);
```

<a name="parameters"></a>Parámetros
----------

Esta función no tiene parámetros.

<a name="return-value"></a>Valor devuelto
------------

El valor devuelto es un código que identifica la página de códigos. Para obtener una lista de identificadores, vea [identificadores de páginas de códigos](https://msdn.microsoft.com/library/windows/desktop/dd317756).

Si el valor devuelto es cero, se ha producido un error en la función. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

Una página de códigos asigna códigos de caracteres de 256 a caracteres individuales. Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas. Para recuperar más información sobre una página de códigos, incluido su nombre, vea la función [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .

Para establecer la página de códigos de salida de la consola, use la función [**SetConsoleOutputCP**](setconsoleoutputcp.md) . Para establecer y consultar la página de códigos de entrada de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) y [**GetConsoleCP**](getconsolecp.md) .

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
<td>ConsoleApi. h (a través de winCon. h, include Windows. h)</td>
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
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vea también


[Páginas de códigos de la consola](console-code-pages.md)

[Funciones de la consola](console-functions.md)

[**GetConsoleCP**](getconsolecp.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

 

 




