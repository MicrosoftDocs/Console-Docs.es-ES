---
title: Funciones de entrada de la consola de Low-Level
description: Un búfer de funciones de entrada de la consola de bajo nivel contiene registros de entrada que pueden incluir información sobre el teclado, el mouse, el cambio de tamaño del búfer, el foco y los eventos de menú.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_low\_level\_console\_input\_functions'
- base.low\_level\_console\_input\_functions
- consoles.low\_level\_console\_input\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 41488614-ca7c-4207-b706-f7776423c7ba
ms.openlocfilehash: fc2969cb266479a0acdde890f4ad3710ca8d7e42
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357825"
---
# <a name="low-level-console-input-functions"></a>Funciones de entrada de la consola de Low-Level

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Un búfer de funciones de entrada de la consola de bajo nivel contiene registros de entrada que pueden incluir información sobre el teclado, el mouse, el cambio de tamaño del búfer, el foco y los eventos de menú. Las funciones de bajo nivel proporcionan acceso directo al búfer de entrada, a diferencia de las funciones de alto nivel que filtran y procesan los datos del búfer de entrada, descartando todo pero la entrada de teclado.

Hay cinco funciones de bajo nivel para tener acceso al búfer de entrada de la consola:

- [**PeekConsoleInput**](readconsoleinput.md)
- [**PeekConsoleInput**](peekconsoleinput.md)
- [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)
- [**WriteConsoleInput**](writeconsoleinput.md)
- [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

Las funciones [**ReadConsoleInput**](readconsoleinput.md), [**PeekConsoleInput**](peekconsoleinput.md)y [**WriteConsoleInput**](writeconsoleinput.md) usan la estructura [**de \_ registro de entrada**](input-record-str.md) para leer o escribir en un búfer de entrada.

A continuación se muestran las descripciones de las funciones de entrada de la consola de bajo nivel.

| Función | Descripción |
|-|-|
| [**PeekConsoleInput**](readconsoleinput.md) | Lee y quita registros de entrada de un búfer de entrada. La función no devuelve hasta que haya al menos un registro disponible para su lectura. A continuación, se transfieren todos los registros disponibles al búfer del proceso de llamada hasta que no haya más registros disponibles o se haya leído el número especificado de registros. Los registros no leídos permanecen en el búfer de entrada para la siguiente operación de lectura. La función informa del número total de registros que se han leído. Para obtener un ejemplo en el que se usa [**ReadConsoleInput**](readconsoleinput.md), vea [leer eventos de búfer de entrada](reading-input-buffer-events.md). |
| [**PeekConsoleInput**](peekconsoleinput.md) | Lee sin quitar los registros de entrada pendientes en un búfer de entrada. Todos los registros disponibles hasta el número especificado se copian en el búfer del proceso de llamada. Si no hay ningún registro disponible, la función se devuelve inmediatamente. La función informa del número total de registros que se han leído. |
| [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) | Determina el número de registros de entrada no leídos en un búfer de entrada. |
| [**WriteConsoleInput**](writeconsoleinput.md) | Coloca los registros de entrada en el búfer de entrada detrás de los registros pendientes en el búfer. El búfer de entrada crece dinámicamente, si es necesario, para contener tantos registros como se escriban. Para usar esta función, el identificador de búfer de entrada especificado debe tener el \_ derecho de acceso de escritura genérico. |
| [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) | Descarta todos los eventos no leídos en el búfer de entrada. Para usar esta función, el identificador de búfer de entrada especificado debe tener el \_ derecho de acceso de escritura genérico. |

Un subproceso del proceso de una aplicación puede realizar una operación de espera para esperar a que la entrada esté disponible en un búfer de entrada. Para iniciar una operación de espera, especifique un identificador para el búfer de entrada en una llamada a cualquiera de las [funciones de espera](/windows/win32/sync/wait-functions). Estas funciones pueden devolver cuando se señala el estado de uno o varios objetos. El estado de un identificador de entrada de la consola se señaliza cuando hay registros sin leer en su búfer de entrada. El estado se restablece a no señalizado cuando el búfer de entrada se vacía. Si no hay ninguna entrada disponible, el subproceso que realiza la llamada entra en un estado de espera eficaz, lo que consume muy poco tiempo de procesador mientras espera a que se cumplan las condiciones de la operación de espera.