---
title: 'Consolas: escritorio de Windows'
description: Una consola de es una aplicación que proporciona e/s a aplicaciones de línea de comandos.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: b50ccd3d38b70ce67498451c8272b832c59fcef9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039123"
---
# <a name="consoles"></a><span data-ttu-id="12e34-104">Consolas</span><span class="sxs-lookup"><span data-stu-id="12e34-104">Consoles</span></span>

<span data-ttu-id="12e34-105">Una *consola* de es una aplicación que proporciona servicios de e/s a aplicaciones de modo de carácter.</span><span class="sxs-lookup"><span data-stu-id="12e34-105">A *console* is an application that provides I/O services to character-mode applications.</span></span>

<span data-ttu-id="12e34-106">Una consola de está formada por un búfer de entrada y uno o más búferes de pantalla.</span><span class="sxs-lookup"><span data-stu-id="12e34-106">A console consists of an input buffer and one or more screen buffers.</span></span> <span data-ttu-id="12e34-107">El *búfer de entrada* contiene una cola de registros de entrada, cada uno de los cuales contiene información sobre un evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="12e34-107">The *input buffer* contains a queue of input records, each of which contains information about an input event.</span></span> <span data-ttu-id="12e34-108">La cola de entrada siempre incluye eventos de pulsación de teclas y de liberación de claves.</span><span class="sxs-lookup"><span data-stu-id="12e34-108">The input queue always includes key-press and key-release events.</span></span> <span data-ttu-id="12e34-109">También puede incluir eventos del mouse (movimientos de punteros y pulsaciones de botones y versiones) y eventos durante los que las acciones del usuario afectan al tamaño del búfer de pantalla activo.</span><span class="sxs-lookup"><span data-stu-id="12e34-109">It may also include mouse events (pointer movements and button presses and releases) and events during which user actions affect the size of the active screen buffer.</span></span> <span data-ttu-id="12e34-110">Un *búfer de pantalla* es una matriz bidimensional de datos de caracteres y colores para la salida en una ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="12e34-110">A *screen buffer* is a two-dimensional array of character and color data for output in a console window.</span></span> <span data-ttu-id="12e34-111">Cualquier número de procesos puede compartir una consola de.</span><span class="sxs-lookup"><span data-stu-id="12e34-111">Any number of processes can share a console.</span></span>

> [!TIP]
><span data-ttu-id="12e34-112">En la **[Guía del ecosistema](ecosystem-roadmap.md)** encontrará una idea más amplia de las consolas y cómo se relacionan con los terminales y las aplicaciones cliente de línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="12e34-112">A broader idea of consoles and how they relate to terminals and command-line client applications can be found in the **[ecosystem roadmap](ecosystem-roadmap.md)** .</span></span>

- [<span data-ttu-id="12e34-113">Creación de una consola</span><span class="sxs-lookup"><span data-stu-id="12e34-113">Creation of a Console</span></span>](creation-of-a-console.md)
- [<span data-ttu-id="12e34-114">Conexión a una consola</span><span class="sxs-lookup"><span data-stu-id="12e34-114">Attaching to a Console</span></span>](attaching-to-a-console.md)
- [<span data-ttu-id="12e34-115">Cierre de una consola</span><span class="sxs-lookup"><span data-stu-id="12e34-115">Closing a Console</span></span>](closing-a-console.md)
- [<span data-ttu-id="12e34-116">Identificadores de consola</span><span class="sxs-lookup"><span data-stu-id="12e34-116">Console Handles</span></span>](console-handles.md)
- [<span data-ttu-id="12e34-117">Búfer de entrada de la consola</span><span class="sxs-lookup"><span data-stu-id="12e34-117">Console Input Buffer</span></span>](console-input-buffer.md)
- [<span data-ttu-id="12e34-118">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="12e34-118">Console Screen Buffers</span></span>](console-screen-buffers.md)
- [<span data-ttu-id="12e34-119">Tamaño de búfer de ventana y pantalla</span><span class="sxs-lookup"><span data-stu-id="12e34-119">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)
- [<span data-ttu-id="12e34-120">Selección de la consola</span><span class="sxs-lookup"><span data-stu-id="12e34-120">Console Selection</span></span>](console-selection.md)
- [<span data-ttu-id="12e34-121">Desplazarse por el búfer de pantalla</span><span class="sxs-lookup"><span data-stu-id="12e34-121">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)
