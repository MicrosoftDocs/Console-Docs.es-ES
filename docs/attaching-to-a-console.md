---
title: Conexión a una consola
description: Un proceso puede usar la función AttachConsole para adjuntar a una consola. Un proceso se puede adjuntar a una consola.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_attaching\_to\_a\_console'
- base.attaching\_to\_a\_console
- consoles.attaching\_to\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 348e572f-2448-4384-9822-fab01d4ba255
ms.openlocfilehash: 793cc83c0af1f8b0ae4be026f966a79dd034250e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037463"
---
# <a name="attaching-to-a-console"></a>Conexión a una consola

Un proceso puede usar la función [**AttachConsole**](attachconsole.md) para adjuntar a una consola como cliente. Un proceso se puede adjuntar a una consola.

Una consola de puede tener muchos procesos asociados. Para recuperar una lista de los procesos adjuntos a una consola, llame a la función [**GetConsoleProcessList**](getconsoleprocesslist.md) .

Para adjuntar como servidor, consulte la información sobre [**Pseudoconsoles**](pseudoconsoles.md).
