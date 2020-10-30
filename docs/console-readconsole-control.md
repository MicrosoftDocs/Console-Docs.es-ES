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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8a703a1eaa370e16095e1b10eb146a0718f332e9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039193"
---
# <a name="console_readconsole_control-structure"></a>\_Estructura del control READCONSOLE de consola \_

Contiene información para una operación de lectura de la consola.

## <a name="syntax"></a>Sintaxis

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

## <a name="members"></a>Miembros

**nLength**  
Tamaño de la estructura. Establezca este miembro en `sizeof(CONSOLE_READCONSOLE_CONTROL)` .

**nInitialChars**  
Número de caracteres que se van a omitir (y, por tanto, conservar) antes de escribir la entrada recién leída en el búfer pasado a la función [**ReadConsole**](readconsole.md) . Este valor debe ser menor que el parámetro *nNumberOfCharsToRead* de la función **ReadConsole** .

**dwCtrlWakeupMask**  
Máscara que especifica los caracteres de control entre `0x00` y que `0x1F` deben usarse para indicar que la lectura ha finalizado. Cada bit corresponde a un carácter con el bit menos significativo correspondiente a `0x00` o `NUL` y el bit más significativo correspondiente a `0x1F` o `US` . Se pueden especificar varios bits (caracteres de control).

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

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows Vista \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows Server 2008 \[\] |
| Encabezado | ConsoleApi. h (a través de WinCon. h, include Windows. h) |

## <a name="see-also"></a>Consulte también

[**ReadConsole**](readconsole.md)
