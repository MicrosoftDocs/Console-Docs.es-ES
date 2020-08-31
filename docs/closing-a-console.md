---
title: Cerrar una consola
description: Un proceso puede usar la función FreeConsole para desasociarse de su consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_closing\_a\_console'
- base.closing\_a\_console
- consoles.closing\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 254b7cfc-4dee-452f-a409-4fc90d20d4c1
ms.openlocfilehash: bdd6b98f96f4ecb64aa6750396c30ef2dd6d0f74
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060893"
---
# <a name="closing-a-console"></a>Cerrar una consola


Un proceso puede usar la función [**FreeConsole**](freeconsole.md) para desasociarse de su consola. Si otros procesos comparten la consola, la consola no se destruye, pero el proceso que llamó a **FreeConsole** no puede hacer referencia a ella. Después de llamar a **FreeConsole**, el proceso puede usar [**AllocConsole**](allocconsole.md) para crear una nueva consola o [**AttachConsole**](attachconsole.md) para adjuntar a otra consola.

Una consola se cierra cuando el último proceso asociado a ella finaliza o llama a [**FreeConsole**](freeconsole.md).

 

 




