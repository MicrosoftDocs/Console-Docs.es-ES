---
title: Estructura de CONSOLE_READCONSOLE_CONTROL
description: Consulte la información de referencia sobre la estructura de CONSOLE_READCONSOLE_CONTROL, que contiene información para una operación de lectura de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/CONSOLE_READCONSOLE_CONTROL
- wincon/CONSOLE_READCONSOLE_CONTROL
- CONSOLE_READCONSOLE_CONTROL
- consoleapi/PCONSOLE_READCONSOLE_CONTROL
- wincon/PCONSOLE_READCONSOLE_CONTROL
- PCONSOLE_READCONSOLE_CONTROL
MS-HAID:
- base.console\_readconsole\_control
- consoles.console\_readconsole\_control
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a8451a6-d692-43af-88c4-972c4dc5e07c
topic_type:
- apiref
api_name:
- CONSOLE_READCONSOLE_CONTROL
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4fc6af26cd540a7af207af252963c21ba216cdee
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060844"
---
# <a name="console_readconsole_control-structure"></a>\_Estructura del control READCONSOLE de consola \_


Contiene información para una operación de lectura de la consola.

<a name="syntax"></a>Sintaxis
------

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

<a name="members"></a>Miembros
-------

**nLength**  
Tamaño de la estructura. Establezca este miembro en `sizeof(CONSOLE_READCONSOLE_CONTROL)` .

**nInitialChars**  
Número de caracteres que se van a omitir (y, por tanto, conservar) antes de escribir la entrada recién leída en el búfer pasado a la función [**ReadConsole**](readconsole.md) . Este valor debe ser menor que el parámetro *nNumberOfCharsToRead* de la función **ReadConsole** .

**dwCtrlWakeupMask**  
Un carácter de control definido por el usuario que se usa para indicar que la lectura ha finalizado.

**dwControlKeyState**  
Estado de las teclas de control. Este miembro puede ser uno o varios de los valores siguientes.

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
<td><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</td>
<td><p>La luz de Bloq Mayús está activada.</p></td>
</tr>
<tr class="even">
<td><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</td>
<td><p>La clave se ha mejorado.</p></td>
</tr>
<tr class="odd">
<td><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</td>
<td><p>Se presiona la tecla ALT izquierda.</p></td>
</tr>
<tr class="even">
<td><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</td>
<td><p>Se presiona la tecla CTRL izquierda.</p></td>
</tr>
<tr class="odd">
<td><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</td>
<td><p>La luz BLOQ NUM está activada.</p></td>
</tr>
<tr class="even">
<td><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</td>
<td><p>Se presiona la tecla ALT derecha.</p></td>
</tr>
<tr class="odd">
<td><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</td>
<td><p>Se presiona la tecla CTRL derecha.</p></td>
</tr>
<tr class="even">
<td><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</td>
<td><p>La luz de Bloq Despl está activada.</p></td>
</tr>
<tr class="odd">
<td><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</td>
<td><p>Se presiona la tecla Mayús.</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
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
<td>ConsoleApi. h (a través de winCon. h, include Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vea también


[**ReadConsole**](readconsole.md)

 

 




