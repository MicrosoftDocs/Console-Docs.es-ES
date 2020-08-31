---
title: 'Consolas: escritorio de Windows'
description: Una consola de es una aplicación que proporciona e/s a aplicaciones de línea de comandos.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: 7b447e3c1d6d72c58890797177f6668f5d835d35
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060777"
---
# <a name="consoles"></a><span data-ttu-id="e6367-104">Consolas</span><span class="sxs-lookup"><span data-stu-id="e6367-104">Consoles</span></span>

<span data-ttu-id="e6367-105">Una *consola* (o *terminal*) es una aplicación que proporciona e/s a aplicaciones de modo de carácter.</span><span class="sxs-lookup"><span data-stu-id="e6367-105">A *console* (or *terminal*) is an application that provides I/O to character-mode applications.</span></span> <span data-ttu-id="e6367-106">Este mecanismo independiente del procesador facilita el portabilidad de las aplicaciones en modo de carácter existentes o la creación de nuevas herramientas y aplicaciones de modo de carácter.</span><span class="sxs-lookup"><span data-stu-id="e6367-106">This processor-independent mechanism makes it easy to port existing character-mode applications or to create new character-mode tools and applications.</span></span>

<span data-ttu-id="e6367-107">Una consola de está formada por un búfer de entrada y uno o más búferes de pantalla.</span><span class="sxs-lookup"><span data-stu-id="e6367-107">A console consists of an input buffer and one or more screen buffers.</span></span> <span data-ttu-id="e6367-108">El *búfer de entrada* contiene una cola de registros de entrada, cada uno de los cuales contiene información sobre un evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="e6367-108">The *input buffer* contains a queue of input records, each of which contains information about an input event.</span></span> <span data-ttu-id="e6367-109">La cola de entrada siempre incluye eventos de pulsación de teclas y de liberación de claves.</span><span class="sxs-lookup"><span data-stu-id="e6367-109">The input queue always includes key-press and key-release events.</span></span> <span data-ttu-id="e6367-110">También puede incluir eventos del mouse (movimientos de punteros y pulsaciones de botones y versiones) y eventos durante los que las acciones del usuario afectan al tamaño del búfer de pantalla activo.</span><span class="sxs-lookup"><span data-stu-id="e6367-110">It may also include mouse events (pointer movements and button presses and releases) and events during which user actions affect the size of the active screen buffer.</span></span> <span data-ttu-id="e6367-111">Un *búfer de pantalla* es una matriz bidimensional de datos de caracteres y colores para la salida en una ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="e6367-111">A *screen buffer* is a two-dimensional array of character and color data for output in a console window.</span></span> <span data-ttu-id="e6367-112">Cualquier número de procesos puede compartir una consola de.</span><span class="sxs-lookup"><span data-stu-id="e6367-112">Any number of processes can share a console.</span></span>

- [<span data-ttu-id="e6367-113">Creación de una consola</span><span class="sxs-lookup"><span data-stu-id="e6367-113">Creation of a Console</span></span>](creation-of-a-console.md)
- [<span data-ttu-id="e6367-114">Asociar a una consola</span><span class="sxs-lookup"><span data-stu-id="e6367-114">Attaching to a Console</span></span>](attaching-to-a-console.md)
- [<span data-ttu-id="e6367-115">Cerrar una consola</span><span class="sxs-lookup"><span data-stu-id="e6367-115">Closing a Console</span></span>](closing-a-console.md)
- [<span data-ttu-id="e6367-116">Identificadores de consola</span><span class="sxs-lookup"><span data-stu-id="e6367-116">Console Handles</span></span>](console-handles.md)
- [<span data-ttu-id="e6367-117">Búfer de entrada de la consola</span><span class="sxs-lookup"><span data-stu-id="e6367-117">Console Input Buffer</span></span>](console-input-buffer.md)
- [<span data-ttu-id="e6367-118">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="e6367-118">Console Screen Buffers</span></span>](console-screen-buffers.md)
- [<span data-ttu-id="e6367-119">Tamaño de búfer de ventana y pantalla</span><span class="sxs-lookup"><span data-stu-id="e6367-119">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)
- [<span data-ttu-id="e6367-120">Selección de la consola</span><span class="sxs-lookup"><span data-stu-id="e6367-120">Console Selection</span></span>](console-selection.md)
- [<span data-ttu-id="e6367-121">Desplazarse por el búfer de pantalla</span><span class="sxs-lookup"><span data-stu-id="e6367-121">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)
