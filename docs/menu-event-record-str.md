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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: dfca825c03dbf0e63041e68adc5e43f2ca0ef669
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039523"
---
# <a name="menu_event_record-structure"></a>Estructura de registros de \_ eventos de menú \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Describe un evento de menú en una estructura de [**\_ registro de entrada**](input-record-str.md) de la consola. Estos eventos se usan internamente y deben omitirse.

## <a name="syntax"></a>Sintaxis

```C
typedef struct _MENU_EVENT_RECORD {
  UINT dwCommandId;
} MENU_EVENT_RECORD, *PMENU_EVENT_RECORD;
```

## <a name="members"></a>Miembros

**dwCommandId**  
Reservado.

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | WinConTypes. h (a través de WinCon. h, include Windows. h) |

## <a name="see-also"></a>Consulte también

[**registro de entrada \_**](input-record-str.md)
