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
ms.openlocfilehash: 26a1b0b9001f64ea2dc7465fa298b1383f30aa61
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038453"
---
# <a name="console-process-groups"></a><span data-ttu-id="7c56d-104">Grupos de procesos de la consola</span><span class="sxs-lookup"><span data-stu-id="7c56d-104">Console Process Groups</span></span>

<span data-ttu-id="7c56d-105">Cuando un proceso utiliza la función [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) para crear un nuevo proceso de consola, puede especificar la **marca \_ crear \_ nuevo \_ grupo de procesos** para que el nuevo proceso sea el proceso raíz de un grupo de procesos de la consola.</span><span class="sxs-lookup"><span data-stu-id="7c56d-105">When a process uses the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function to create a new console process, it can specify the **CREATE\_NEW\_PROCESS\_GROUP** flag to make the new process the root process of a console process group.</span></span> <span data-ttu-id="7c56d-106">El grupo de procesos incluye todos los procesos que son descendientes del proceso raíz.</span><span class="sxs-lookup"><span data-stu-id="7c56d-106">The process group includes all processes that are descendants of the root process.</span></span>

<span data-ttu-id="7c56d-107">Un proceso puede usar la función [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) para enviar una señal CTRL + C o Ctrl + Inter a todos los procesos de un grupo de procesos de la consola.</span><span class="sxs-lookup"><span data-stu-id="7c56d-107">A process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a CTRL+C or CTRL+BREAK signal to all processes in a console process group.</span></span> <span data-ttu-id="7c56d-108">La señal solo la reciben los procesos del grupo que están conectados a la misma consola que el proceso que llamó a **GenerateConsoleCtrlEvent** .</span><span class="sxs-lookup"><span data-stu-id="7c56d-108">The signal is only received by those processes in the group that are attached to the same console as the process that called **GenerateConsoleCtrlEvent** .</span></span>
