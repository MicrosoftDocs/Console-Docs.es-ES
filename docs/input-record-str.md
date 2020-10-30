---
title: Estructura de INPUT_RECORD
description: Consulte la información de referencia sobre la estructura de INPUT_RECORD, que describe un evento de entrada en el búfer de entrada de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/INPUT_RECORD
- wincon/INPUT_RECORD
- INPUT_RECORD
- wincontypes/PINPUT_RECORD
- wincon/PINPUT_RECORD
- PINPUT_RECORD
MS-HAID:
- '\_win32\_input\_record\_str'
- base.input\_record\_str
- consoles.input\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a46ba7fd-097a-455d-96ac-13aa01e11dc1
topic_type:
- apiref
api_name:
- INPUT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4ad86de170c1fef74f133a5d5c51d8de2dea497f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038543"
---
# <a name="input_record-structure"></a>Estructura del registro de entrada \_

Describe un evento de entrada en el búfer de entrada de la consola. Estos registros se pueden leer desde el búfer de entrada mediante la función [**ReadConsoleInput**](readconsoleinput.md) o [**PeekConsoleInput**](peekconsoleinput.md) , o bien escribirse en el búfer de entrada mediante la función [**WriteConsoleInput**](writeconsoleinput.md) .

## <a name="syntax"></a>Sintaxis

```C
typedef struct _INPUT_RECORD {
  WORD  EventType;
  union {
    KEY_EVENT_RECORD          KeyEvent;
    MOUSE_EVENT_RECORD        MouseEvent;
    WINDOW_BUFFER_SIZE_RECORD WindowBufferSizeEvent;
    MENU_EVENT_RECORD         MenuEvent;
    FOCUS_EVENT_RECORD        FocusEvent;
  } Event;
} INPUT_RECORD;
```

## <a name="members"></a>Miembros

**EventType**  
Identificador para el tipo de evento de entrada y el registro de eventos almacenados en el miembro de **evento** .

Este miembro puede ser uno de los valores siguientes.

| Valor | Significado |
|-|-|
| **FOCUS_EVENT** 0x0010 | El miembro de **evento** contiene una estructura de **[FOCUS_EVENT_RECORD](focus-event-record-str.md)** . Estos eventos se usan internamente y deben omitirse. |
| **KEY_EVENT** 0x0001 | El miembro de **evento** contiene una estructura de **[KEY_EVENT_RECORD](key-event-record-str.md)** con información sobre un evento de teclado. |
| **MENU_EVENT** 0x0008 | El miembro de **evento** contiene una estructura de **[MENU_EVENT_RECORD](menu-event-record-str.md)** . Estos eventos se usan internamente y deben omitirse. |
| **MOUSE_EVENT** 0x0002 | El miembro de **evento** contiene una estructura de **[MOUSE_EVENT_RECORD](mouse-event-record-str.md)** con información sobre un evento de presionar el botón o el movimiento del mouse. |
| **WINDOW_BUFFER_SIZE_EVENT** 0x0004 | El miembro de **evento** contiene una estructura de **[WINDOW_BUFFER_SIZE_RECORD](window-buffer-size-record-str.md)** con información sobre el nuevo tamaño del búfer de pantalla de la consola. |

**Evento**  
La información de eventos. El formato de este miembro depende del tipo de evento especificado por el miembro **EventType** .

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, vea [leer eventos de búfer de entrada](reading-input-buffer-events.md).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Professional \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows 2000 Server \[\] |
| Encabezado | WinConTypes. h (a través de WinCon. h, include Windows. h) |

## <a name="see-also"></a>Consulte también

[**\_registro de eventos de foco \_**](focus-event-record-str.md)

[**\_registro de evento de clave \_**](key-event-record-str.md)

[**\_registro de evento de menú \_**](menu-event-record-str.md)

[**\_registro de eventos del mouse \_**](mouse-event-record-str.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**PeekConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)
