---
title: CreateConsoleScreenBuffer función)
description: La función CreateConsoleScreenBuffer crea un búfer de pantalla para la consola de Windows.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/CreateConsoleScreenBuffer
- wincon/CreateConsoleScreenBuffer
- CreateConsoleScreenBuffer
MS-HAID:
- '\_win32\_createconsolescreenbuffer'
- base.createconsolescreenbuffer
- consoles.createconsolescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98bb74e4-dad2-4615-9263-48ba778a06ff
topic_type:
- apiref
api_name:
- CreateConsoleScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 289908708fb1c89c3ec3d990c9e8bf2649914a1b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060773"
---
# <a name="createconsolescreenbuffer-function"></a>CreateConsoleScreenBuffer función)


Crea un búfer de pantalla de la consola.

<a name="syntax"></a>Sintaxis
------

```C
HANDLE WINAPI CreateConsoleScreenBuffer(
  _In_             DWORD               dwDesiredAccess,
  _In_             DWORD               dwShareMode,
  _In_opt_   const SECURITY_ATTRIBUTES *lpSecurityAttributes,
  _In_             DWORD               dwFlags,
  _Reserved_       LPVOID              lpScreenBufferData
);
```

<a name="parameters"></a>Parámetros
----------

*dwDesiredAccess* \[ de\]  
El acceso al búfer de pantalla de la consola. Para obtener una lista de derechos de acceso, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.

*dwShareMode* \[ de\]  
Este parámetro puede ser cero, lo que indica que no se puede compartir el búfer o puede ser uno o varios de los valores siguientes.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Valor</th>
<th>Significado</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="FILE_SHARE_READ"></span><span id="file_share_read"></span>
<strong>FILE_SHARE_READ</strong> 0x00000001</td>
<td><p>Se pueden realizar otras operaciones de apertura en el búfer de pantalla de la consola para tener acceso de lectura.</p></td>
</tr>
<tr class="even">
<td><span id="FILE_SHARE_WRITE"></span><span id="file_share_write"></span>
<strong>FILE_SHARE_WRITE</strong> 0x00000002</td>
<td><p>Se pueden realizar otras operaciones de apertura en el búfer de pantalla de la consola para el acceso de escritura.</p></td>
</tr>
</tbody>
</table>

 

*lpSecurityAttributes* \[ en, opcional\]  
Puntero a una estructura [**de \_ atributos de seguridad**](https://msdn.microsoft.com/library/windows/desktop/aa379560) que determina si los procesos secundarios pueden heredar el identificador devuelto. Si *lpSecurityAttributes* es **null**, el identificador no se puede heredar. El miembro **lpSecurityDescriptor** de la estructura especifica un descriptor de seguridad para el nuevo búfer de pantalla de la consola. Si *lpSecurityAttributes* es **null**, el búfer de pantalla de la consola obtiene un descriptor de seguridad predeterminado. Las ACL del descriptor de seguridad predeterminado para un búfer de pantalla de la consola proceden del token principal o de suplantación del creador.

*dwFlags* \[ de\]  
El tipo de búfer de pantalla de la consola que se va a crear. El único tipo de búfer de pantalla compatible es el ** \_ \_ búfer TEXTMODE**de la consola.

*lpScreenBufferData*   
Sector debe ser **null**.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es un identificador del nuevo búfer de pantalla de la consola.

Si se produce un error en la función, el valor devuelto es un ** \_ \_ valor de identificador no válido**. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

Una consola de puede tener varios búferes de pantalla, pero solo un búfer de pantalla activo. Se puede tener acceso a los búferes de pantalla inactivos para lectura y escritura, pero solo se muestra el búfer de pantalla activo. Para convertir el nuevo búfer de pantalla en el búfer de pantalla activo, utilice la función [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) .

El búfer de pantalla recién creado copiará algunas propiedades del búfer de pantalla activo en el momento en que se llama a esta función. El comportamiento es el siguiente:
- `Font` -copiado del búfer de pantalla activo
- `Display Window Size` -copiado del búfer de pantalla activo
- `Buffer Size` -coincide con `Display Window Size` (**no** copiado)
- `Default Attributes` (colores): copiado del búfer de pantalla activo
- `Default Popup Attributes` (colores): copiado del búfer de pantalla activo

El proceso de llamada puede usar el identificador devuelto en cualquier función que requiera un identificador a un búfer de pantalla de la consola, de acuerdo con las limitaciones de acceso especificadas por el parámetro *dwDesiredAccess* .

El proceso de llamada puede usar la función [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) para crear un controlador de búfer de pantalla duplicado que tenga un acceso o una herencia diferentes del identificador original. Sin embargo, **DuplicateHandle** no se puede usar para crear un duplicado que sea válido para un proceso diferente (excepto a través de la herencia).

Para cerrar el identificador de búfer de pantalla de la consola, use la función [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) .

<a name="examples"></a>Ejemplos
--------

Para obtener un ejemplo, vea [lectura y escritura de bloques de caracteres y atributos](reading-and-writing-blocks-of-characters-and-attributes.md).

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


[Funciones de la consola](console-functions.md)

[Búferes de pantalla de la consola](console-screen-buffers.md)

[**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211)

[**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**atributos de seguridad \_**](https://msdn.microsoft.com/library/windows/desktop/aa379560)

[**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)

 

 




