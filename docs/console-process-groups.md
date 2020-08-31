---
title: Grupos de procesos de la consola
description: Cuando un proceso utiliza la función CreateProcess para crear un nuevo proceso de consola, puede especificar la \_ marca crear \_ nuevo \_ grupo de procesos para que el nuevo proceso sea el proceso raíz de un grupo de procesos de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_process\_groups'
- base.console\_process\_groups
- consoles.console\_process\_groups
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6cfe5b4b-d677-4747-bbf2-c7243db2346e
ms.openlocfilehash: 467959e651f7e0806742ca3920ca0d441d5543cc
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060849"
---
# <a name="console-process-groups"></a>Grupos de procesos de la consola


Cuando un proceso utiliza la función [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) para crear un nuevo proceso de consola, puede especificar la **marca \_ crear \_ nuevo \_ grupo de procesos** para que el nuevo proceso sea el proceso raíz de un grupo de procesos de la consola. El grupo de procesos incluye todos los procesos que son descendientes del proceso raíz.

Un proceso puede usar la función [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) para enviar una señal CTRL + C o Ctrl + Inter a todos los procesos de un grupo de procesos de la consola. La señal solo la reciben los procesos del grupo que están conectados a la misma consola que el proceso que llamó a **GenerateConsoleCtrlEvent**.

 

 




