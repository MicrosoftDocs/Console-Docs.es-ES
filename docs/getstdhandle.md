---
title: GetStdHandle (función)
description: Recupera un identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- processenv/GetStdHandle
- winbase/GetStdHandle
- GetStdHandle
MS-HAID:
- '\_win32\_getstdhandle'
- base.getstdhandle
- consoles.getstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 23cd76e9-671a-48d0-9b82-2beda8917348
topic_type:
- apiref
api_name:
- GetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 613aacf4052e8e3b38c0a3e254ac4dd2b55ced5d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060617"
---
# <a name="getstdhandle-function"></a>GetStdHandle (función)


Recupera un identificador del dispositivo estándar especificado (entrada estándar, salida estándar o error estándar).

<a name="syntax"></a>Sintaxis
------

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

<a name="parameters"></a>Parámetros
----------

*nStdHandle* \[ de\]  
El dispositivo estándar. Este parámetro puede ser uno de los valores siguientes.

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
<td><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</td>
<td><p>El dispositivo de entrada estándar. Inicialmente, es el búfer de entrada de la consola, CONIN $.</p></td>
</tr>
<tr class="even">
<td><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</td>
<td><p>El dispositivo de salida estándar. Inicialmente, es el búfer de pantalla de la consola activo, CONOUT $.</p></td>
</tr>
<tr class="odd">
<td><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</td>
<td><p>El dispositivo de error estándar. Inicialmente, es el búfer de pantalla de la consola activo, CONOUT $.</p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es un identificador del dispositivo especificado o un identificador Redirigido establecido por una llamada anterior a [**SetStdHandle**](setstdhandle.md). El identificador tiene derechos de acceso genéricos de ** \_ lectura** y ** \_ escritura** , a menos que la aplicación haya usado **SetStdHandle** para establecer un identificador estándar con un acceso inferior.

Si se produce un error en la función, el valor devuelto es un ** \_ \_ valor de identificador no válido**. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Si una aplicación no tiene identificadores estándar asociados, como un servicio que se ejecuta en un escritorio interactivo y no los ha redirigido, el valor devuelto es **null**.

<a name="remarks"></a>Observaciones
-------

Los identificadores devueltos por **GetStdHandle** pueden ser usados por aplicaciones que necesitan leer o escribir en la consola. Cuando se crea una consola, el identificador de entrada estándar es un identificador del búfer de entrada de la consola, y los identificadores de salida estándar y de error estándar son identificadores del búfer de pantalla activo de la consola. Estos identificadores pueden ser utilizados por las funciones [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) , o por cualquiera de las funciones de consola que tienen acceso al búfer de entrada de la consola o a un búfer de pantalla (por ejemplo, las funciones [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md)o [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) ).

Los identificadores estándar de un proceso se pueden redirigir mediante una llamada a [**SetStdHandle**](setstdhandle.md), en cuyo caso **GetStdHandle** devuelve el identificador redirigido. Si se han redirigido los identificadores estándar, puede especificar el valor de CONIN $ en una llamada a la función [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) para obtener un identificador para el búfer de entrada de la consola. De forma similar, puede especificar el valor de CONOUT $ para obtener un identificador para el búfer de pantalla activo de la consola.

### <a name="span-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanattachdetach-behavior"></a><span id="Attach_detach_behavior"></span><span id="attach_detach_behavior"></span><span id="ATTACH_DETACH_BEHAVIOR"></span>Comportamiento de adjuntar/separar

Al conectarse a una nueva consola, los identificadores estándar siempre se reemplazan por identificadores de consola, a menos que se haya especificado **STARTF \_ USESTDHANDLES** durante la creación del proceso.

Si el valor existente del identificador estándar es **null**, o el valor existente del identificador estándar es similar a un pseudohandle de consola, el identificador se reemplaza por un identificador de consola.

Cuando un elemento primario usa **Create \_ New \_ Console** y **STARTF \_ USESTDHANDLES** para crear un proceso de consola, no se reemplazarán los identificadores estándar a menos que el valor existente del identificador estándar sea NULL o una pseudohandle de consola.

<a name="examples"></a>Ejemplos
--------

Para obtener un ejemplo, vea [leer eventos de búfer de entrada](reading-input-buffer-events.md).

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
<td>ProcessEnv. h (a través de Winbase. h, include Windows. h)</td>
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

[Identificadores de consola](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetStdHandle**](setstdhandle.md)

[**WriteConsole**](writeconsole.md)

[**Escritura**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




