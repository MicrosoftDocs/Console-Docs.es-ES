---
title: GenerateConsoleCtrlEvent función)
description: Envía una señal especificada a un grupo de procesos de consola que comparte la consola asociada al proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/GenerateConsoleCtrlEvent
- wincon/GenerateConsoleCtrlEvent
- GenerateConsoleCtrlEvent
MS-HAID:
- '\_win32\_generateconsolectrlevent'
- base.generateconsolectrlevent
- consoles.generateconsolectrlevent
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ed392d97-6fd0-4256-a783-bc7d27d01a10
topic_type:
- apiref
api_name:
- GenerateConsoleCtrlEvent
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 31c0330a002362542a799ab7e038d3f65497ded3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060736"
---
# <a name="generateconsolectrlevent-function"></a>GenerateConsoleCtrlEvent función)


Envía una señal especificada a un grupo de procesos de consola que comparte la consola asociada al proceso de llamada.

<a name="syntax"></a>Sintaxis
------

```C
BOOL WINAPI GenerateConsoleCtrlEvent(
  _In_ DWORD dwCtrlEvent,
  _In_ DWORD dwProcessGroupId
);
```

<a name="parameters"></a>Parámetros
----------

*dwCtrlEvent* \[ de\]  
Tipo de señal que se va a generar. Este parámetro puede ser uno de los valores siguientes.

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
<td><span id="CTRL_C_EVENT"></span><span id="ctrl_c_event"></span>
<strong>CTRL_C_EVENT</strong> 0</td>
<td><p>Genera una señal CTRL + C. Esta señal no se puede generar para grupos de procesos. Si <em>dwProcessGroupId</em> es distinto de cero, esta función se realizará correctamente, pero los procesos del grupo de procesos especificado no recibirán la señal CTRL + C.</p></td>
</tr>
<tr class="even">
<td><span id="CTRL_BREAK_EVENT"></span><span id="ctrl_break_event"></span>
<strong>CTRL_BREAK_EVENT</strong> 1</td>
<td><p>Genera una señal CTRL + INTER.</p></td>
</tr>
</tbody>
</table>

 

*dwProcessGroupId* \[ de\]  
Identificador del grupo de procesos que va a recibir la señal. Un grupo de procesos se crea cuando se especifica la marca **crear \_ nuevo \_ \_ grupo de procesos** en una llamada a la función [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) . El identificador de proceso del nuevo proceso también es el identificador del grupo de procesos de un nuevo grupo de procesos. El grupo de procesos incluye todos los procesos que son descendientes del proceso raíz. Solo los procesos del grupo que comparten la misma consola que el proceso de llamada reciben la señal. En otras palabras, si un proceso del grupo crea una nueva consola, ese proceso no recibe la señal ni sus descendientes.

Si este parámetro es cero, la señal se genera en todos los procesos que comparten la consola del proceso de llamada.

<a name="return-value"></a>Valor devuelto
------------

Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).

<a name="remarks"></a>Observaciones
-------

**GenerateConsoleCtrlEvent** hace que se llame a las funciones de controlador de control de los procesos del grupo de destino. Todos los procesos de la consola tienen una función de controlador predeterminada que llama a la función [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) . Un proceso de consola puede usar la función [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) para instalar o quitar otras funciones de controlador.

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) también puede habilitar un atributo heredable que hace que el proceso de llamada ignore las señales Ctrl + C. Si **GenerateConsoleCtrlEvent** envía una señal CTRL + C a un proceso para el que este atributo está habilitado, no se llama a las funciones de controlador para ese proceso. CTRL + INTERRUMPIr señales siempre hace que se llame a las funciones de controlador.

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


[Controladores de control de consola](console-control-handlers.md)

[Funciones de la consola](console-functions.md)

[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md)

 

 




