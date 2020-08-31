---
title: WinEvents de consola
description: Las constantes de eventos siguientes se usan en el parámetro Event de la función de devolución de llamada WinEventProc. Para obtener más información, vea WinEvents.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- winuser/EVENT_CONSOLE_CARET
- winuser/EVENT_CONSOLE_END_APPLICATION
- winuser/EVENT_CONSOLE_LAYOUT
- winuser/EVENT_CONSOLE_START_APPLICATION
- winuser/EVENT_CONSOLE_UPDATE_REGION
- winuser/EVENT_CONSOLE_UPDATE_SCROLL
- winuser/EVENT_CONSOLE_UPDATE_SIMPLE
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
MS-HAID:
- '\_win32\_console\_winevents'
- base.console\_winevents
- consoles.console\_winevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b7078b2d-5508-4e42-bac2-34b70f1856e2
topic_type:
- apiref
api_name:
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
api_location:
- Winuser.h
api_type:
- HeaderDef
ms.openlocfilehash: ab58df01b3fb29e6efea3ecd0aab145fe2f298c2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060780"
---
# <a name="console-winevents"></a>WinEvents de consola


Las constantes de eventos siguientes se usan en el parámetro *Event* de la función de devolución de llamada [*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) . Para obtener más información, vea [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Constante o valor</th>
<th>Descripción</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="EVENT_CONSOLE_CARET"></span><span id="event_console_caret"></span>
<strong>EVENT_CONSOLE_CARET</strong> 0x4001</td>
<td><p>Se ha cambiado el símbolo de intercalación de la consola. El parámetro <em>idObject</em> es uno o varios de los siguientes valores: <strong>CONSOLE_CARET_SELECTION</strong> o <strong>CONSOLE_CARET_VISIBLE</strong>.</p>
<p>El parámetro <em>idChild</em> es una estructura de <strong><a href="https://docs.microsoft.com/windows/console/coord-str">coordenadas</a></strong> que especifica la posición actual del cursor.</p></td>
</tr>
<tr class="even">
<td><span id="EVENT_CONSOLE_END_APPLICATION"></span><span id="event_console_end_application"></span>
<strong>EVENT_CONSOLE_END_APPLICATION</strong> 0x4007</td>
<td><p>Se ha salido de un proceso de consola. El parámetro <em>idObject</em> contiene el identificador de proceso del proceso terminado.</p></td>
</tr>
<tr class="odd">
<td><span id="EVENT_CONSOLE_LAYOUT"></span><span id="event_console_layout"></span>
<strong>EVENT_CONSOLE_LAYOUT</strong> 0x4005</td>
<td><p>El diseño de la consola ha cambiado.</p></td>
</tr>
<tr class="even">
<td><span id="EVENT_CONSOLE_START_APPLICATION"></span><span id="event_console_start_application"></span>
<strong>EVENT_CONSOLE_START_APPLICATION</strong> 0x4006</td>
<td><p>Se ha iniciado un nuevo proceso de consola. El parámetro <em>idObject</em> contiene el identificador de proceso del proceso recién creado. Si la aplicación es una aplicación de 16 bits, el parámetro <em>idChild</em> es <strong>CONSOLE_APPLICATION_16BIT</strong> y <em>idObject</em> es el identificador de proceso de la sesión de NTVDM asociada a la consola.</p></td>
</tr>
<tr class="odd">
<td><span id="EVENT_CONSOLE_UPDATE_REGION"></span><span id="event_console_update_region"></span>
<strong>EVENT_CONSOLE_UPDATE_REGION</strong> 0x4002</td>
<td><p>Ha cambiado más de un carácter. El parámetro <em>idObject</em> es una estructura de <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>coordenadas</strong></a> que especifica el inicio de la región modificada. El parámetro <em>idChild</em> es una estructura de <strong>coordenadas</strong> que especifica el final de la región modificada.</p></td>
</tr>
<tr class="even">
<td><span id="EVENT_CONSOLE_UPDATE_SCROLL"></span><span id="event_console_update_scroll"></span>
<strong>EVENT_CONSOLE_UPDATE_SCROLL</strong> 0x4004</td>
<td><p>La consola se ha desplazado. El parámetro <em>idObject</em> es la distancia horizontal que se ha desplazado la consola. El parámetro <em>idChild</em> es la distancia vertical que se ha desplazado la consola.</p></td>
</tr>
<tr class="odd">
<td><span id="EVENT_CONSOLE_UPDATE_SIMPLE"></span><span id="event_console_update_simple"></span>
<strong>EVENT_CONSOLE_UPDATE_SIMPLE</strong> 0x4003</td>
<td><p>Ha cambiado un solo carácter. El parámetro <em>idObject</em> es una estructura de <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>coordenadas</strong></a> que especifica el carácter que ha cambiado. El parámetro <em>idChild</em> especifica el carácter de la palabra baja y los <a href="console-screen-buffers.md#_win32_font_attributes" data-raw-source="[character attributes](console-screen-buffers.md#_win32_font_attributes)">atributos de carácter</a> de la palabra alta.</p></td>
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
<td><p>Windows 2000 Professional [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="even">
<td><p>Servidor mínimo compatible</p></td>
<td><p>Windows 2000 Server [solo aplicaciones de escritorio]</p></td>
</tr>
<tr class="odd">
<td><p>Encabezado</p></td>
<td>Winuser. h</td>
</tr>
</tbody>
</table>
