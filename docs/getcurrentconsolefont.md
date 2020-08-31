---
title: GetCurrentConsoleFont función)
description: Recupera información sobre la fuente de consola actual para un búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetCurrentConsoleFont
- wincon/GetCurrentConsoleFont
- GetCurrentConsoleFont
MS-HAID:
- '\_win32\_getcurrentconsolefont'
- base.getcurrentconsolefont
- consoles.getcurrentconsolefont
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 347508ea-5c15-4568-b99f-1e7f5cdac8c1
topic_type:
- apiref
api_name:
- GetCurrentConsoleFont
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 4116dcf034c619544ed1689e3161f4eca4250a81
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060645"
---
# <a name="getcurrentconsolefont-function"></a>GetCurrentConsoleFont función)


Recupera información sobre la fuente de consola actual.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI GetCurrentConsoleFont(
  _In_  HANDLE             hConsoleOutput,
  _In_  BOOL               bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFO lpConsoleCurrentFont
);
```

<a name="parameters"></a>Parámetros
----------

*hConsoleOutput* \[ de\]  
Identificador del búfer de pantalla de la consola. El identificador debe tener el derecho de acceso de ** \_ lectura genérico** . Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*bMaximumWindow* \[ de\]  
Si este parámetro es **true**, se recupera la información de fuente para el tamaño máximo de la ventana. Si este parámetro es **false**, se recupera la información de fuente para el tamaño de la ventana actual.

*lpConsoleCurrentFont* \[ enuncia\]  
Puntero a una estructura [**de \_ \_ información de fuente de consola**](console-font-info-str.md) que recibe la información de fuente solicitada.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

Para compilar una aplicación que usa esta función, defina ** \_ Win32 \_ WinNT** como 0x0500 o posterior. Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).

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
<td><p>Windows XP [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="even">
<td><p>Servidor mínimo compatible</p></td>
<td><p>Windows Server 2003 [solo aplicaciones de escritorio]</p></td>
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

[Búferes de pantalla de la consola](console-screen-buffers.md)

[**\_información de fuente de la consola \_**](console-font-info-str.md)

[**GetConsoleFontSize**](getconsolefontsize.md)

 

 




