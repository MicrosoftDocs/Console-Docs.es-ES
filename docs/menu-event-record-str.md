---
title: Estructura de MENU_EVENT_RECORD
description: Describe un evento de menú en una estructura de registro de entrada de la consola \_ . Estos eventos se usan internamente y deben omitirse.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/MENU_EVENT_RECORD
- wincon/MENU_EVENT_RECORD
- MENU_EVENT_RECORD
- wincontypes/PMENU_EVENT_RECORD
- wincon/PMENU_EVENT_RECORD
- PMENU_EVENT_RECORD
MS-HAID:
- '\_win32\_menu\_event\_record\_str'
- base.menu\_event\_record\_str
- consoles.menu\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 7efef0e0-01ba-44ba-a972-25c6b3aed2bd
topic_type:
- apiref
api_name:
- MENU_EVENT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8bbfbf6ad8bd885d69ce08e94dfced93b0bd3257
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060613"
---
# <a name="menu_event_record-structure"></a>Estructura de registros de \_ eventos de menú \_


Describe un evento de menú en una estructura de [** \_ registro de entrada**](input-record-str.md) de la consola. Estos eventos se usan internamente y deben omitirse.

<a name="syntax"></a>Sintaxis
------

```C
typedef struct _MENU_EVENT_RECORD {
  UINT dwCommandId;
} MENU_EVENT_RECORD, *PMENU_EVENT_RECORD;
```

<a name="members"></a>Miembros
-------

**dwCommandId**  
Reservado.

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
<td>WinConTypes. h (a través de winCon. h, include Windows. h)</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>Vea también


[**registro de entrada \_**](input-record-str.md)

 

 




