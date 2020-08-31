---
title: GetConsoleProcessList función)
description: Vea la información de referencia sobre la función GetConsoleProcessList, que recupera una lista de los procesos adjuntos a la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleProcessList
- wincon/GetConsoleProcessList
- GetConsoleProcessList
MS-HAID:
- '\_win32\_getconsoleprocesslist'
- base.getconsoleprocesslist
- consoles.getconsoleprocesslist
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3d21103b-662d-4393-ae3f-773cd9e4a930
topic_type:
- apiref
api_name:
- GetConsoleProcessList
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 5b032754172886fd83a8152caeb5e2228b917930
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060693"
---
# <a name="getconsoleprocesslist-function"></a>GetConsoleProcessList función)


Recupera una lista de los procesos adjuntos a la consola actual.

<a name="syntax"></a>Sintaxis
------

```C
DWORD WINAPI GetConsoleProcessList(
  _Out_ LPDWORD lpdwProcessList,
  _In_  DWORD   dwProcessCount
);
```

<a name="parameters"></a>Parámetros
----------

*lpdwProcessList* \[ enuncia\]  
Un puntero a un búfer que recibe una matriz de identificadores de proceso cuando se realiza correctamente. Debe ser un búfer válido y no puede ser `NULL` . El búfer debe tener espacio para recibir al menos un identificador de proceso devuelto.

*dwProcessCount* \[ de\]  
Número máximo de identificadores de proceso que se pueden almacenar en el búfer de *lpdwProcessList* . Debe ser mayor que 0.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es menor o igual que *dwProcessCount* y representa el número de identificadores de proceso almacenados en el búfer *lpdwProcessList* .

Si el búfer es demasiado pequeño para contener todos los identificadores de proceso válidos, el valor devuelto es el número necesario de elementos de matriz. La función habrá almacenado ningún identificador en el búfer. En esta situación, use el valor devuelto para asignar un búfer lo suficientemente grande como para almacenar toda la lista y volver a llamar a la función.

Si el valor devuelto es cero, se ha producido un error en la función porque cada consola tiene al menos un proceso asociado. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

Si `NULL` se proporcionó una lista de procesos o el número de procesos era 0, la llamada devolverá 0 y `GetLastError` devolverá `ERROR_INVALID_PARAMETER` . Proporcione un búfer de al menos un elemento para llamar a esta función. Asigne un búfer mayor y vuelva a llamar a si el código de retorno es mayor que la longitud del búfer proporcionado.

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


[**AttachConsole**](attachconsole.md)

[Funciones de la consola](console-functions.md)

 

 




