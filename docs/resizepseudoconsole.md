---
title: ResizePseudoConsole función)
description: Vea la información de referencia sobre la función ResizePseudoConsole, que cambia el tamaño de los búferes internos para un pseudoconsole al tamaño especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola, conpty, pseudoconsole
f1_keywords:
- consoleapi/ResizePseudoConsole
- ResizePseudoConsole
topic_type:
- apiref
api_name:
- ResizePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 0d5a4ff954c8ebea688573f23d3981ee9c5d7d2a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037543"
---
# <a name="resizepseudoconsole-function"></a>ResizePseudoConsole función)

Cambia el tamaño de los búferes internos de un pseudoconsole al tamaño especificado.

## <a name="syntax"></a>Sintaxis

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

## <a name="parameters"></a>Parámetros

*hPC* \[ de\]  
Identificador de un pseudoconsole activo tal y como lo abre [CreatePseudoConsole](createpseudoconsole.md).

*tamaño* \[ de de\]  
Dimensiones de la ventana o búfer en el recuento de caracteres que se usarán para el búfer interno de este pseudoconsole.

## <a name="return-value"></a>Valor devuelto

Tipo: **HRESULT**

Si este método se ejecuta correctamente, devuelve **S_OK** . De lo contrario, devuelve un código de error **HRESULT** .

## <a name="remarks"></a>Comentarios

Esta función puede cambiar el tamaño de los búferes internos en la sesión de pseudoconsole para que coincida con el tamaño de búfer o de ventana que se usa para la presentación en el extremo del terminal. Esto garantiza que las aplicaciones conectadas de la interfaz de Command-Line (CUI) que usan las funciones de la [consola](console-functions.md) para comunicarse tendrán las dimensiones correctas devueltas en sus llamadas.

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

[**ClosePseudoConsole**](closepseudoconsole.md)
