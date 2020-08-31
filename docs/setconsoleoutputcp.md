---
title: SetConsoleOutputCP función)
description: Establece la página de códigos de salida utilizada por la consola asociada al proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleOutputCP
- wincon/SetConsoleOutputCP
- SetConsoleOutputCP
MS-HAID:
- '\_win32\_setconsoleoutputcp'
- base.setconsoleoutputcp
- consoles.setconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0b41e66b-ca19-4d69-9f39-92da158344ef
topic_type:
- apiref
api_name:
- SetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: ae1f3970af6c8db1ebedc29e0644ed001258ecc5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061073"
---
# <a name="setconsoleoutputcp-function"></a>SetConsoleOutputCP función)


Establece la página de códigos de salida utilizada por la consola asociada al proceso de llamada. Una consola usa su página de códigos de salida para traducir los valores de caracteres escritos por las distintas funciones de salida en las imágenes que se muestran en la ventana de la consola.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI SetConsoleOutputCP(
  _In_ UINT wCodePageID
);
```

<a name="parameters"></a>Parámetros
----------

*wCodePageID* \[ de\]  
Identificador de la página de códigos que se va a establecer. Para obtener más información, vea la sección Comentarios.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

Una página de códigos asigna códigos de caracteres de 256 a caracteres individuales. Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas.

Si la fuente actual es una fuente Unicode de punto fijo, **SetConsoleOutputCP** cambia la asignación de los valores de caracteres en el conjunto de glifos de la fuente, en lugar de cargar una fuente independiente cada vez que se llama. Esto afecta al modo en que se muestran los caracteres extendidos (valor ASCII superior a 127) en una ventana de consola. Sin embargo, si la fuente actual es una fuente de trama, **SetConsoleOutputCP** no afecta al modo en que se muestran los caracteres extendidos.

Para buscar las páginas de códigos que el sistema operativo instala o admite, utilice la función [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) . Los identificadores de las páginas de códigos disponibles en el equipo local también se almacenan en el registro con la siguiente clave:

**HKEY \_ local \_ Machine \\ System \\ CurrentControlSet \\ control de la página de \\ \\ códigos NLS**

Sin embargo, es mejor usar [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) para enumerar las páginas de códigos, ya que el registro puede diferir en diferentes versiones de Windows.
Para determinar si una página de códigos determinada es válida, utilice la función [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) . Para recuperar más información sobre una página de códigos, incluido su nombre, utilice la función [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) . Para obtener una lista de los identificadores de página de códigos disponibles, vea [identificadores de páginas de códigos](https://msdn.microsoft.com/library/windows/desktop/dd317756).

Para determinar la página de códigos de salida actual de la consola, use la función [**GetConsoleOutputCP**](getconsoleoutputcp.md) . Para establecer y recuperar una página de códigos de entrada de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) y [**GetConsoleCP**](getconsolecp.md) .

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

[**GetConsoleOutputCP**](getconsoleoutputcp.md)

[**SetConsoleCP**](setconsolecp.md)

 

 




