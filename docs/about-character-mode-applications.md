---
title: Acerca de las consolas
description: Las consolas proporcionan compatibilidad de alto nivel para las aplicaciones de modo de carácter simple que interactúan con el usuario mediante el uso de funciones que leen la entrada estándar y escriben en la salida estándar o en un error estándar.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: e20fa54434b4121abd3f77ee530945bf9aa590f2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037533"
---
# <a name="about-character-mode-applications"></a><span data-ttu-id="4e31a-104">Acerca de las aplicaciones de modo de carácter</span><span class="sxs-lookup"><span data-stu-id="4e31a-104">About Character Mode Applications</span></span>

<span data-ttu-id="4e31a-105">Modo de carácter (o "línea de comandos"):</span><span class="sxs-lookup"><span data-stu-id="4e31a-105">Character mode (or "command-line") applications:</span></span>

1. <span data-ttu-id="4e31a-106">\[Opcionalmente, \] leer datos de la entrada estándar (stdin)</span><span class="sxs-lookup"><span data-stu-id="4e31a-106">\[Optionally\] Read data from standard input (stdin)</span></span>
2. <span data-ttu-id="4e31a-107">"Trabajar"</span><span class="sxs-lookup"><span data-stu-id="4e31a-107">Do "work"</span></span>
3. <span data-ttu-id="4e31a-108">\[Opcionalmente, puede \] escribir datos en la salida estándar (stdout) o en un error estándar (stderr).</span><span class="sxs-lookup"><span data-stu-id="4e31a-108">\[Optionally\] Write data to standard output (stdout) or standard error (stderr)</span></span>

<span data-ttu-id="4e31a-109">Las aplicaciones en modo de carácter se comunican con el usuario final a través de una aplicación de "consola" (o "terminal").</span><span class="sxs-lookup"><span data-stu-id="4e31a-109">Character mode applications communicate with the end-user through a "console" (or "terminal") application.</span></span> <span data-ttu-id="4e31a-110">Una consola de convierte los datos proporcionados por el usuario desde el teclado, el mouse, la pantalla táctil, el lápiz, etc., y lo envía a la stdin de una aplicación en modo de carácter.</span><span class="sxs-lookup"><span data-stu-id="4e31a-110">A console converts user input from keyboard, mouse, touch-screen, pen, etc., and sends it to a character mode application's stdin.</span></span> <span data-ttu-id="4e31a-111">Una consola también puede mostrar la salida de texto de una aplicación en modo de carácter en la pantalla del usuario.</span><span class="sxs-lookup"><span data-stu-id="4e31a-111">A console may also display a character mode application's text output on the user's screen.</span></span>

<span data-ttu-id="4e31a-112">En Windows, la consola está integrada y proporciona una API enriquecida a través de la cual las aplicaciones en modo de carácter pueden interactuar con el usuario.</span><span class="sxs-lookup"><span data-stu-id="4e31a-112">In Windows, the console is built-in and provides a rich API through which character mode applications can interact with the user.</span></span> <span data-ttu-id="4e31a-113">Sin embargo, en la era reciente, el equipo de la consola está fomentando el desarrollo de todas las aplicaciones en modo de carácter con [secuencias de terminal virtuales](console-virtual-terminal-sequences.md) a través de las llamadas de API clásicas para ofrecer compatibilidad máxima entre Windows y otros sistemas operativos.</span><span class="sxs-lookup"><span data-stu-id="4e31a-113">However, in the recent era, the console team is encouraging all character mode applications to be developed with [virtual terminal sequences](console-virtual-terminal-sequences.md) over the classic API calls for maximum compatibility between Windows and other operating systems.</span></span> <span data-ttu-id="4e31a-114">Puede encontrar más información sobre esta transición y las ventajas y desventajas en nuestro debate sobre las [API clásicas frente a las secuencias de terminales virtuales](classic-vs-vt.md).</span><span class="sxs-lookup"><span data-stu-id="4e31a-114">More details on this transition and the trade offs involved can be found in our discussion of [classic APIs versus virtual terminal sequences](classic-vs-vt.md).</span></span>

- [<span data-ttu-id="4e31a-115">Consolas</span><span class="sxs-lookup"><span data-stu-id="4e31a-115">Consoles</span></span>](consoles.md)
- [<span data-ttu-id="4e31a-116">Métodos de entrada y salida</span><span class="sxs-lookup"><span data-stu-id="4e31a-116">Input and Output Methods</span></span>](input-and-output-methods.md)
- [<span data-ttu-id="4e31a-117">Páginas de código de la consola</span><span class="sxs-lookup"><span data-stu-id="4e31a-117">Console Code Pages</span></span>](console-code-pages.md)
- [<span data-ttu-id="4e31a-118">Identificadores de control de la consola</span><span class="sxs-lookup"><span data-stu-id="4e31a-118">Console Control Handlers</span></span>](console-control-handlers.md)
- [<span data-ttu-id="4e31a-119">Alias de la consola</span><span class="sxs-lookup"><span data-stu-id="4e31a-119">Console Aliases</span></span>](console-aliases.md)
- [<span data-ttu-id="4e31a-120">Seguridad y derechos de acceso del búfer de la consola</span><span class="sxs-lookup"><span data-stu-id="4e31a-120">Console Buffer Security and Access Rights</span></span>](console-buffer-security-and-access-rights.md)
- [<span data-ttu-id="4e31a-121">Problemas de la aplicación de consola</span><span class="sxs-lookup"><span data-stu-id="4e31a-121">Console Application Issues</span></span>](console-application-issues.md)
