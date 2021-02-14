---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- wincontypes/SMALL_RECT
- wincon/SMALL_RECT
- SMALL_RECT
title: Estructura de SMALL_RECT
description: Define las coordenadas de las esquinas superior izquierda e inferior derecha de un rectángulo.
MS-HAID:
- '\_win32\_small\_rect\_str'
- base.small\_rect\_str
- consoles.small\_rect\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 62639815-c7e9-4ae2-b152-61290f78422b
topic_type:
- apiref
api_name:
- SMALL_RECT
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: f9cbe94fff616a93d835f47b618a28bb9f521891
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358495"
---
# <a name="small_rect-structure"></a>PEQUEÑA \_ estructura Rect

Define las coordenadas de las esquinas superior izquierda e inferior derecha de un rectángulo.

## <a name="syntax"></a>Sintaxis

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

## <a name="members"></a>Miembros

**Left**  
Coordenada x de la esquina superior izquierda del rectángulo.

**Top** (Principales)  
Coordenada y de la esquina superior izquierda del rectángulo.

**Right**  
Coordenada x de la esquina inferior derecha del rectángulo.

**Bottom**  
Coordenada y de la esquina inferior derecha del rectángulo.

## <a name="remarks"></a>Comentarios

Las funciones de consola utilizan esta estructura para especificar áreas rectangulares de búferes de pantalla de la consola, donde las coordenadas especifican las filas y columnas de las celdas de caracteres del búfer de pantalla.

## <a name="examples"></a>Ejemplos

Para obtener un ejemplo, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Professional |
| Servidor mínimo compatible | \[Solo aplicaciones de escritorio\] de Windows 2000 Server |
| Encabezado | WinConTypes. h (a través de WinCon. h, include Windows. h) |

## <a name="see-also"></a>Consulte también

[**RECT**](/previous-versions//dd162897(v=vs.85))

[**RECTl**](/previous-versions//dd162907(v=vs.85))