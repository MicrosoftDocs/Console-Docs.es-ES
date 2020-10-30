---
title: CreatePseudoConsole función)
description: Vea la información de referencia sobre la función CreatePseudoConsole, que asigna un nuevo pseudoconsole para el proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola, conpty, pseudoconsole
f1_keywords:
- consoleapi/CreatePseudoConsole
- CreatePseudoConsole
topic_type:
- apiref
api_name:
- CreatePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: f10a77781d555a76fdfcea8c8f10ae6bc1f72047
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038303"
---
# <a name="createpseudoconsole-function"></a>CreatePseudoConsole función)

Crea un nuevo objeto pseudoconsole para el proceso que realiza la llamada.

## <a name="syntax"></a>Sintaxis

```C
HRESULT WINAPI CreatePseudoConsole(
    _In_ COORD size,
    _In_ HANDLE hInput,
    _In_ HANDLE hOutput,
    _In_ DWORD dwFlags,
    _Out_ HPCON* phPC
);
```

## <a name="parameters"></a>Parámetros

*tamaño* \[ de de\]  
Dimensiones de la ventana o búfer en el recuento de caracteres que se usarán para la creación inicial de pseudoconsole. Se puede ajustar más adelante con [ResizePseudoConsole](resizepseudoconsole.md).

*hInput* \[ de\]  
Identificador abierto de un flujo de datos que representa la entrada del usuario en el dispositivo. Esto está restringido actualmente a la e/s [sincrónica](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .

*hOutput* \[ de\]  
Identificador abierto de un flujo de datos que representa la salida de la aplicación del dispositivo. Esto está restringido actualmente a la e/s [sincrónica](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) .

*dwFlags* \[ de\]  
El valor puede ser uno de los siguientes:

| Valor | Significado |
|-|-|
| **0** | Realice una creación de pseudoconsole estándar. |
| **PSEUDOCONSOLE_INHERIT_CURSOR** (DWORD) 1 | La sesión de pseudoconsole creada intentará heredar la posición del cursor de la consola de paernt. |

*phPC* \[ enuncia\]  
Puntero a una ubicación que recibirá un identificador para el nuevo dispositivo pseudoconsole.

## <a name="return-value"></a>Valor devuelto

Tipo: **HRESULT**

Si este método se ejecuta correctamente, devuelve **S_OK** . De lo contrario, devuelve un código de error **HRESULT** .

## <a name="remarks"></a>Comentarios

Esta función la usan principalmente las aplicaciones que intentan ser una ventana de terminal para una aplicación de la interfaz de usuario de línea de comandos (CUI). Los llamadores se convierten en responsables de la presentación de la información en el flujo de salida y de la recopilación de datos proporcionados por el usuario y su serialización en el flujo de entrada.

Los flujos de entrada y salida codificados como UTF-8 contienen texto sin formato intercalado con [secuencias de terminales virtuales](console-virtual-terminal-sequences.md).

En el flujo de salida, la aplicación que realiza la llamada puede descodificar las [secuencias de terminal virtuales](console-virtual-terminal-sequences.md) para diseñar y presentar el texto sin formato en una ventana de presentación.

En el flujo de entrada, el texto sin formato representa las teclas de teclado estándar que introduce un usuario. Las operaciones más complicadas se representan mediante claves de control de codificación y movimientos del mouse como [secuencias de terminales virtuales](console-virtual-terminal-sequences.md) incrustadas en esta secuencia.

El identificador creado por esta función debe cerrarse con [ClosePseudoConsole](closepseudoconsole.md) cuando se completen las operaciones.

Si usa `PSEUDOCONSOLE_INHERIT_CURSOR` , la aplicación que realiza la llamada debe estar preparada para responder a la solicitud del estado del cursor de forma asincrónica en un subproceso en segundo plano reenviando o interpretando la solicitud de información de cursor que se recibirá en `hOutput` y responderá `hInput` . Si no lo hace, es posible que la aplicación que llama se bloquee mientras realiza otra solicitud del sistema pseudoconsole.

## <a name="examples"></a>Ejemplos

Para ver un tutorial completo sobre el uso de esta función para establecer una sesión de pseudoconsole, consulte [creación de una sesión de pseudoconsole](creating-a-pseudoconsole-session.md).

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

[Creación de una sesión de pseudoconsola](creating-a-pseudoconsole-session.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)

[**ClosePseudoConsole**](closepseudoconsole.md)
