---
title: Cierre de una consola
description: Un proceso puede usar la función FreeConsole para desasociarse de su consola.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_closing\_a\_console'
- base.closing\_a\_console
- consoles.closing\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 254b7cfc-4dee-452f-a409-4fc90d20d4c1
ms.openlocfilehash: db424e6d9fc91a7a3b6cff3b5fc5028833d208f9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037323"
---
# <a name="closing-a-console"></a>Cierre de una consola

Un proceso puede usar la función [**FreeConsole**](freeconsole.md) para desasociarse de su consola. Si otros procesos comparten la consola, la consola no se destruye, pero el proceso que llamó a **FreeConsole** no puede hacer referencia a ella. Después de llamar a **FreeConsole** , el proceso puede usar [**AllocConsole**](allocconsole.md) para crear una nueva consola o [**AttachConsole**](attachconsole.md) para adjuntar a otra consola.

Una consola se cierra cuando el último proceso asociado a ella finaliza o llama a [**FreeConsole**](freeconsole.md).
