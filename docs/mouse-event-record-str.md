---
title: Estructura de MOUSE_EVENT_RECORD
description: Vea la información de referencia sobre la estructura de MOUSE_EVENT_RECORD, que describe un evento de entrada del mouse en una estructura de INPUT_RECORD de consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/MOUSE_EVENT_RECORD
- wincon/MOUSE_EVENT_RECORD
- MOUSE_EVENT_RECORD
- wincontypes/PMOUSE_EVENT_RECORD
- wincon/PMOUSE_EVENT_RECORD
- PMOUSE_EVENT_RECORD
MS-HAID:
- '\_win32\_mouse\_event\_record\_str'
- base.mouse\_event\_record\_str
- consoles.mouse\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ea54c6-8872-4111-8d72-1377409b9247
topic_type:
- apiref
api_name:
- MOUSE_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: c10047d1386f3bce1546ee21bacdc81b8fb7bb55
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038523"
---
# <a name="mouse_event_record-structure"></a>Estructura de registro de \_ eventos del mouse \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Describe un evento de entrada del mouse en una estructura de [**\_ registro de entrada**](input-record-str.md) de la consola.

## <a name="syntax"></a>Sintaxis

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

## <a name="members"></a>Miembros

**dwMousePosition**  
Una estructura de [**coordenadas**](coord-str.md) que contiene la ubicación del cursor, en cuanto a las coordenadas de la celda de caracteres del búfer de la pantalla de la consola.

**dwButtonState**  
Estado de los botones del mouse. El bit menos significativo corresponde al botón primario del mouse. El siguiente bit menos significativo corresponde al botón secundario del mouse. El bit siguiente indica el siguiente botón del mouse. Después, los bits se corresponden de izquierda a derecha a los botones del mouse. Un bit es 1 si se presionó el botón.

Las siguientes constantes se definen para los cinco primeros botones del mouse.

| Valor | Significado |
|-|-|
| **FROM_LEFT_1ST_BUTTON_PRESSED** 0x0001 | Botón primario del mouse. |
| **FROM_LEFT_2ND_BUTTON_PRESSED** 0x0004 | El segundo botón pantalla la izquierda. |
| **FROM_LEFT_3RD_BUTTON_PRESSED** 0x0008 | Tercer botón de la izquierda. |
| **FROM_LEFT_4TH_BUTTON_PRESSED** 0x0010 | Cuarto botón de la izquierda. |
| **RIGHTMOST_BUTTON_PRESSED** 0x0002 | Botón secundario del mouse. |

**dwControlKeyState**  
Estado de las teclas de control. Este miembro puede ser uno o varios de los valores siguientes.

| Valor | Significado |
|-|-|
| **CAPSLOCK_ON** 0x0080 | La luz de Bloq Mayús está activada. |
| **ENHANCED_KEY** 0x0100 | La clave se ha mejorado. Vea la [sección Comentarios](key-event-record-str.md#remarks). |
| **LEFT_ALT_PRESSED** 0x0002 | Se presiona la tecla ALT izquierda. |
| **LEFT_CTRL_PRESSED** 0x0008 | Se presiona la tecla CTRL izquierda. |
| **NUMLOCK_ON** 0x0020 | La luz BLOQ NUM está activada. |
| **RIGHT_ALT_PRESSED** 0x0001 | Se presiona la tecla ALT derecha. |
| **RIGHT_CTRL_PRESSED** 0x0004 | Se presiona la tecla CTRL derecha. |
| **SCROLLLOCK_ON** 0x0040 | La luz de Bloq Despl está activada. |
| **SHIFT_PRESSED** 0x0010 | Se presiona la tecla Mayús. |

**dwEventFlags**  
Tipo de evento del mouse. Si este valor es cero, indica que se presiona o se suelta un botón del mouse. De lo contrario, este miembro es uno de los valores siguientes.

| Valor | Significado |
|-|-|
| **DOUBLE_CLICK** 0x0002 | Se produjo el segundo clic (presionar el botón) de un doble clic. El primer clic se devuelve como un evento de presionar botón normal. |
| **MOUSE_HWHEELED** 0x0008 | Se ha despasado la rueda del mouse horizontal.<br /><br />Si la palabra alta del miembro **dwButtonState** contiene un valor positivo, la rueda se giró hacia la derecha. De lo contrario, la rueda se giró hacia la izquierda. |
| **MOUSE_MOVED** 0x0001 | Se ha producido un cambio en la posición del mouse. |
| **MOUSE_WHEELED** 0x0004 | Rueda del mouse vertical movida.<br /><br />Si la palabra alta del miembro **dwButtonState** contiene un valor positivo, la rueda se giró hacia delante, alejándose del usuario. De lo contrario, la rueda se giró hacia atrás, hacia el usuario. |

## <a name="remarks"></a>Comentarios

Los eventos del mouse se colocan en el búfer de entrada cuando la consola está en modo de mouse ( **Habilitar la \_ \_ entrada del mouse** ).

Los eventos del mouse se generan cada vez que el usuario mueve el mouse, o presiona o suelta uno de los botones del mouse. Los eventos del mouse se colocan en el búfer de entrada de la consola solo cuando el grupo de consola tiene el foco de teclado y el cursor se encuentra dentro de los bordes de la ventana de la consola.

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

[**PeekConsoleInput**](peekconsoleinput.md)

[**PeekConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)
