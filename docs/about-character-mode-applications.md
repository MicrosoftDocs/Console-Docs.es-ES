---
title: Acerca de las consolas
description: Las consolas proporcionan compatibilidad de alto nivel para las aplicaciones de modo de carácter simple que interactúan con el usuario mediante el uso de funciones que leen la entrada estándar y escriben en la salida estándar o en un error estándar.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: 0a738c72ec45a68817fae6dbfa9d6b3e45beb53e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060929"
---
# <a name="about-character-mode-applications"></a><span data-ttu-id="8f473-104">Acerca de las aplicaciones en modo de carácter</span><span class="sxs-lookup"><span data-stu-id="8f473-104">About Character Mode Applications</span></span>

<span data-ttu-id="8f473-105">Modo de carácter (o "línea de comandos"):</span><span class="sxs-lookup"><span data-stu-id="8f473-105">Character mode (or "command-line") applications:</span></span>

1. <span data-ttu-id="8f473-106">Opcionalmente Leer datos de la entrada estándar (stdin)</span><span class="sxs-lookup"><span data-stu-id="8f473-106">[Optionally] Read data from standard input (stdin)</span></span>
2. <span data-ttu-id="8f473-107">"Trabajar"</span><span class="sxs-lookup"><span data-stu-id="8f473-107">Do "work"</span></span>
3. <span data-ttu-id="8f473-108">Opcionalmente Escribir datos en la salida estándar (stdout) o en el error estándar (stderr)</span><span class="sxs-lookup"><span data-stu-id="8f473-108">[Optionally] Write data to standard output (stdout) or standard error (stderr)</span></span>

<span data-ttu-id="8f473-109">Las aplicaciones en modo de carácter se comunican con el usuario final a través de una aplicación de "consola" (o "terminal").</span><span class="sxs-lookup"><span data-stu-id="8f473-109">Character mode applications communicate with the end-user through a "console" (or "terminal") application.</span></span> <span data-ttu-id="8f473-110">Una consola de convierte los datos proporcionados por el usuario desde el teclado, el mouse, la pantalla táctil, el lápiz, etc., y lo envía a la stdin de una aplicación en modo de carácter.</span><span class="sxs-lookup"><span data-stu-id="8f473-110">A console converts user input from keyboard, mouse, touch-screen, pen, etc., and sends it to a character mode application's stdin.</span></span> <span data-ttu-id="8f473-111">Una consola también puede mostrar la salida de texto de una aplicación en modo de carácter en la pantalla del usuario.</span><span class="sxs-lookup"><span data-stu-id="8f473-111">A console may also display a character mode application's text output on the user's screen.</span></span>

<span data-ttu-id="8f473-112">En Windows, la consola está integrada y proporciona una API enriquecida a través de la cual las aplicaciones en modo de carácter pueden interactuar con el usuario.</span><span class="sxs-lookup"><span data-stu-id="8f473-112">In Windows, the console is built-in and provides a rich API through which character mode applications can interact with the user.</span></span>

- [<span data-ttu-id="8f473-113">Consolas</span><span class="sxs-lookup"><span data-stu-id="8f473-113">Consoles</span></span>](consoles.md)
- [<span data-ttu-id="8f473-114">Métodos de entrada y salida</span><span class="sxs-lookup"><span data-stu-id="8f473-114">Input and Output Methods</span></span>](input-and-output-methods.md)
- [<span data-ttu-id="8f473-115">Páginas de códigos de la consola</span><span class="sxs-lookup"><span data-stu-id="8f473-115">Console Code Pages</span></span>](console-code-pages.md)
- [<span data-ttu-id="8f473-116">Controladores de control de consola</span><span class="sxs-lookup"><span data-stu-id="8f473-116">Console Control Handlers</span></span>](console-control-handlers.md)
- [<span data-ttu-id="8f473-117">Alias de la consola</span><span class="sxs-lookup"><span data-stu-id="8f473-117">Console Aliases</span></span>](console-aliases.md)
- [<span data-ttu-id="8f473-118">Seguridad y derechos de acceso de búfer de la consola</span><span class="sxs-lookup"><span data-stu-id="8f473-118">Console Buffer Security and Access Rights</span></span>](console-buffer-security-and-access-rights.md)
- [<span data-ttu-id="8f473-119">Problemas de la aplicación de consola</span><span class="sxs-lookup"><span data-stu-id="8f473-119">Console Application Issues</span></span>](console-application-issues.md)

 

 




