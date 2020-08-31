---
title: GetCurrentConsoleFontEx función)
description: Consulte la información de referencia sobre la función GetCurrentConsoleFontEx, que recupera información extendida sobre la fuente de consola usada actualmente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetCurrentConsoleFontEx
- wincon/GetCurrentConsoleFontEx
- GetCurrentConsoleFontEx
MS-HAID:
- base.getcurrentconsolefontex
- consoles.getcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 97d8e730-4110-4be5-b099-0acc1b6f8eb5
topic_type:
- apiref
api_name:
- GetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0ea8d5ad928003d4039a6c8611073ab3c38ce34f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060652"
---
# <a name="getcurrentconsolefontex-function"></a>GetCurrentConsoleFontEx función)


Recupera información extendida sobre la fuente de consola actual.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI GetCurrentConsoleFontEx(
  _In_  HANDLE               hConsoleOutput,
  _In_  BOOL                 bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

<a name="parameters"></a>Parámetros
----------

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de ** \_ lectura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*bMaximumWindow* \[ de\]  
Si este parámetro es **true**, se recupera la información de fuente para el tamaño máximo de la ventana. Si este parámetro es **false**, se recupera la información de fuente para el tamaño de la ventana actual.

*lpConsoleCurrentFontEx* \[ enuncia\]  
Puntero a una estructura [** \_ \_ INFOEX de fuente de consola**](console-font-infoex.md) que recibe la información de fuente solicitada.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

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
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vea también


[Funciones de la consola](console-functions.md)

[**fuente de consola \_ \_ INFOEX**](console-font-infoex.md)

 

 




