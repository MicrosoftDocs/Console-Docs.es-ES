---
title: Estructura de CONSOLE_SELECTION_INFO
description: Consulte la información de referencia sobre la estructura de CONSOLE_SELECTION_INFO, que contiene información para una selección de consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/CONSOLE_SELECTION_INFO
- wincon/CONSOLE_SELECTION_INFO
- CONSOLE_SELECTION_INFO
- consoleapi3/PCONSOLE_SELECTION_INFO
- wincon/PCONSOLE_SELECTION_INFO
- PCONSOLE_SELECTION_INFO
MS-HAID:
- '\_win32\_console\_selection\_info\_str'
- base.console\_selection\_info\_str
- consoles.console\_selection\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9530b249-8db4-4516-9cc8-2b452c6751f9
topic_type:
- apiref
api_name:
- CONSOLE_SELECTION_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: aaf1cfaea2a8822c142aab87f6dcf1b022b7160c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038373"
---
# <a name="console_selection_info-structure"></a>Estructura de información de \_ selección de consola \_

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Contiene información para una selección de consola.

## <a name="syntax"></a>Sintaxis

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

## <a name="members"></a>Miembros

**dwFlags**  
El indicador de selección. Este miembro puede ser uno o varios de los valores siguientes.

| Valor | Significado |
|-|-|
| **CONSOLE_MOUSE_DOWN** 0x0008 | El mouse está inactivo. El usuario está ajustando activamente el rectángulo de selección con un mouse. |
| **CONSOLE_MOUSE_SELECTION** 0x0004 | Seleccionar con el mouse. Si está desactivado, el usuario está `conhost.exe` seleccionando el modo de marca de funcionamiento con el teclado. |
| **CONSOLE_NO_SELECTION** 0x0000 | No hay ninguna selección. |
| **CONSOLE_SELECTION_IN_PROGRESS** 0x0001 | La selección ha comenzado. Si se selecciona una selección del mouse, normalmente no se producirá sin la `CONSOLE_SELECTION_NOT_EMPTY` marca. Si se selecciona un teclado, esto puede ocurrir cuando se ha escrito el modo de marca pero el usuario sigue navegando a la posición inicial. |
| **CONSOLE_SELECTION_NOT_EMPTY** 0x0002 | Rectángulo de selección no vacío. La carga de *dwSelectionAnchor* y *srSelection* es válida.  |

**dwSelectionAnchor**  
Estructura de [**coordenadas**](coord-str.md) que especifica el delimitador de selección, en caracteres.

**srSelection**  
[**Pequeña estructura \_ Rect**](small-rect-str.md) que especifica el rectángulo de selección.

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Solo aplicaciones de escritorio de Windows XP \[\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows Server 2003 \[\] |
| Encabezado | ConsoleApi3. h (a través de WinCon. h, include Windows. h) |

## <a name="see-also"></a>Consulte también

[**COORDS**](coord-str.md)

[**GetConsoleSelectionInfo**](getconsoleselectioninfo.md)

[**PEQUEÑO \_ rectángulo**](small-rect-str.md)
