---
title: Estructura de KEY_EVENT_RECORD
description: Describe un evento de entrada de teclado en una estructura de registro de entrada de la consola \_ .
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/KEY_EVENT_RECORD
- wincon/KEY_EVENT_RECORD
- KEY_EVENT_RECORD
- wincontypes/PKEY_EVENT_RECORD
- wincon/PKEY_EVENT_RECORD
- PKEY_EVENT_RECORD
MS-HAID:
- '\_win32\_key\_event\_record\_str'
- base.key\_event\_record\_str
- consoles.key\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b3fed86b-84ef-48e4-97e1-cb3d65f714a7
topic_type:
- apiref
api_name:
- KEY_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: bcc58b90e71b848e3b6e4b0bf5ba162323830529
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357805"
---
# <a name="key_event_record-structure"></a>Estructura del registro de \_ eventos clave \_

Describe un evento de entrada de teclado en una estructura de [**\_ registro de entrada**](input-record-str.md) de la consola.

## <a name="syntax"></a>Sintaxis

```C
typedef struct _KEY_EVENT_RECORD {
  BOOL  bKeyDown;
  WORD  wRepeatCount;
  WORD  wVirtualKeyCode;
  WORD  wVirtualScanCode;
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } uChar;
  DWORD dwControlKeyState;
} KEY_EVENT_RECORD;
```

## <a name="members"></a>Miembros

**bKeyDown**  
Si se presiona la tecla, este miembro es **true**. De lo contrario, este miembro es **false** (se libera la tecla).

**wRepeatCount**  
Recuento de repeticiones, que indica que una clave se mantiene presionada. Por ejemplo, cuando se mantiene presionada una tecla, podría obtener cinco eventos con este miembro igual a 1, un evento con este miembro igual a 5 o varios eventos con este miembro mayor o igual que 1.

**wVirtualKeyCode**  
[Código de clave virtual](/windows/win32/inputdev/virtual-key-codes) que identifica la clave especificada de una manera independiente del dispositivo.

**wVirtualScanCode**  
Código de análisis virtual de la clave especificada que representa el valor dependiente del dispositivo generado por el hardware del teclado.

**uChar**  
Unión de los siguientes miembros.

**UnicodeChar**  
Carácter Unicode traducido.

**AsciiChar**  
Carácter ASCII traducido.

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

## <a name="remarks"></a>Comentarios

Las claves mejoradas para los teclados de IBM® 101-y 102-Key son las teclas INS, SUPR, Inicio, fin, Re Pág, Av Pág y dirección en los clústeres a la izquierda del teclado. y la división (/) y escriba las teclas en el teclado.

Los eventos de entrada de teclado se generan cuando se presiona o se suelta cualquier tecla, incluidas las teclas de control. Sin embargo, la tecla ALT cuando se presiona y se libera sin combinar con otro carácter, tiene un significado especial para el sistema y no se pasa a la aplicación. Además, la combinación de teclas CTRL + C no se pasa si el identificador de entrada está en modo procesado **( \_ habilitar \_ entrada procesada**).

## <a name="examples"></a>Ejemplos

Para un ejemplo, vea [Lectura de eventos de búfer de entrada](reading-input-buffer-events.md).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Professional |
| Servidor mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Server |
| Encabezado | WinConTypes. h (a través de WinCon. h, include Windows. h) |

## <a name="see-also"></a>Consulte también

[**PeekConsoleInput**](peekconsoleinput.md)

[**PeekConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

[**registro de entrada \_**](input-record-str.md)