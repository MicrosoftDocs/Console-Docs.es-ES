---
title: Grupos de procesos de la consola
description: Cuando un proceso utiliza la función CreateProcess para crear un nuevo proceso de consola, puede especificar la \_ marca crear \_ nuevo \_ grupo de procesos para que el nuevo proceso sea el proceso raíz de un grupo de procesos de la consola.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_process\_groups'
- base.console\_process\_groups
- consoles.console\_process\_groups
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6cfe5b4b-d677-4747-bbf2-c7243db2346e
ms.openlocfilehash: 8df877eca9a52ef9072685c673461723dda78a0b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358105"
---
# <a name="console-process-groups"></a>Grupos de procesos de la consola

Cuando un proceso utiliza la función [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) para crear un nuevo proceso de consola, puede especificar la **marca \_ crear \_ nuevo \_ grupo de procesos** para que el nuevo proceso sea el proceso raíz de un grupo de procesos de la consola. El grupo de procesos incluye todos los procesos que son descendientes del proceso raíz.

Un proceso puede usar la función [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) para enviar una señal CTRL + C o Ctrl + Inter a todos los procesos de un grupo de procesos de la consola. La señal solo la reciben los procesos del grupo que están conectados a la misma consola que el proceso que llamó a **GenerateConsoleCtrlEvent**.