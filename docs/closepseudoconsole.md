---
title: ClosePseudoConsole función)
description: Vea la información de referencia sobre la función ClosePseudoConsole, que cierra un pseudoconsole desde el identificador especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola, conpty, pseudoconsole
topic_type:
- apiref
api_name:
- ClosePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 067fa732f5badfe46ee6391c892aa037613cb4dd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037293"
---
# <a name="closepseudoconsole-function"></a>ClosePseudoConsole función)

Cierra un pseudoconsole del identificador dado.

## <a name="syntax"></a>Sintaxis

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC
);
```

## <a name="parameters"></a>Parámetros

*hPC* \[ de\]  
Identificador de un pseudoconsole activo tal y como lo abre [CreatePseudoConsole](createpseudoconsole.md).

## <a name="return-value"></a>Valor devuelto

*Ninguna*

## <a name="remarks"></a>Comentarios

Al cerrar un pseudoconsole, las aplicaciones cliente adjuntas a la sesión también se terminarán.

Un marco pintado final puede llegar al `hOutput` identificador proporcionado originalmente a [CreatePsuedoConsole](createpseudoconsole.md) cuando se llama a esta API. Se espera que el autor de la llamada vacíe esta información del búfer del canal de comunicación y la presente o la descarte. Si no se agota el búfer, es posible que la llamada de cierre espere indefinidamente hasta que se vacíe o que los canales de comunicación se rompan de otra manera.

## <a name="requirements"></a>Requisitos

| &nbsp; | &nbsp; |
|-|-|
| Cliente mínimo compatible | Actualización 2018 de octubre de Windows 10 (versión 1809) \[ solo para aplicaciones de escritorio\] |
| Servidor mínimo compatible | Solo aplicaciones de escritorio de Windows Server 2019 \[\] |
| Encabezado | ConsoleApi. h (a través de WinCon. h, include Windows. h) |
| Biblioteca | Kernel32. lib |
| Archivo DLL | Kernel32.dll |

## <a name="see-also"></a>Consulte también

[Pseudoconsoles](pseudoconsoles.md)

[**ClosePseudoConsole**](createpseudoconsole.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)
