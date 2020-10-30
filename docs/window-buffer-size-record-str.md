---
title: Estructura de WINDOW_BUFFER_SIZE_RECORD
description: Vea información de referencia sobre la estructura de WINDOW_BUFFER_SIZE_RECORD, que describe un cambio en el tamaño del búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/WINDOW_BUFFER_SIZE_RECORD
- wincon/WINDOW_BUFFER_SIZE_RECORD
- WINDOW_BUFFER_SIZE_RECORD
- wincontypes/PWINDOW_BUFFER_SIZE_RECORD
- wincon/PWINDOW_BUFFER_SIZE_RECORD
- PWINDOW_BUFFER_SIZE_RECORD
MS-HAID:
- '\_win32\_window\_buffer\_size\_record\_str'
- base.window\_buffer\_size\_record\_str
- consoles.window\_buffer\_size\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f2875e8-aa09-455b-a923-7cc388525b98
topic_type:
- apiref
api_name:
- WINDOW_BUFFER_SIZE_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 355482dfd162e2c29944d53e5b17b0315ea15950
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039273"
---
# <a name="window_buffer_size_record-structure"></a>\_Estructura de \_ registro del tamaño del búfer de ventana \_

Describe un cambio en el tamaño del búfer de pantalla de la consola.

## <a name="syntax"></a>Sintaxis

```C
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

## <a name="members"></a>Miembros

**dwSize**  
Una estructura de [**coordenadas**](coord-str.md) que contiene el tamaño del búfer de pantalla de la consola, en columnas y filas de celda de carácter.

## <a name="remarks"></a>Comentarios

Los eventos de tamaño de búfer se colocan en el búfer de entrada cuando la consola está en modo de ventana ( **habilitar \_ \_ entrada de ventana** ).

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, vea [leer eventos de búfer de entrada](reading-input-buffer-events.md).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | WinConTypes. h (a través de WinCon. h, include Windows. h) |

## <a name="see-also"></a>Consulte también

[**COORDS**](coord-str.md)

[**registro de entrada \_**](input-record-str.md)

[**PeekConsoleInput**](readconsoleinput.md)
