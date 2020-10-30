---
title: Aplicaciones en modo de carácter
description: Las consolas de administran la entrada y salida (e/s) para aplicaciones en modo de caracteres (aplicaciones que no proporcionan su propia interfaz gráfica de usuario).
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_character\_mode\_applications'
- base.character\_mode\_applications
- consoles.character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ea3ea214-892c-4953-bc22-7905efbc173f
ms.openlocfilehash: 5e1b0b2b5162360122580f3ea7a100750b96272e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037353"
---
# <a name="character-mode-applications"></a><span data-ttu-id="e2409-104">Aplicaciones en modo de carácter</span><span class="sxs-lookup"><span data-stu-id="e2409-104">Character Mode Applications</span></span>

<span data-ttu-id="e2409-105">Las consolas de administran la entrada y salida (e/s) para aplicaciones en modo de caracteres (aplicaciones que no proporcionan su propia interfaz gráfica de usuario).</span><span class="sxs-lookup"><span data-stu-id="e2409-105">Consoles manage input and output (I/O) for character-mode applications (applications that do not provide their own graphical user interface).</span></span>

<span data-ttu-id="e2409-106">Las funciones de la consola de permiten distintos niveles de acceso a una consola de.</span><span class="sxs-lookup"><span data-stu-id="e2409-106">The console functions enable different levels of access to a console.</span></span> <span data-ttu-id="e2409-107">Las funciones de e/s de la consola de alto nivel permiten a una aplicación leer la entrada estándar para recuperar la entrada del teclado almacenada en el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="e2409-107">The high-level console I/O functions enable an application to read from standard input to retrieve keyboard input stored in a console's input buffer.</span></span> <span data-ttu-id="e2409-108">Las funciones también permiten que una aplicación escriba en una salida estándar o un error estándar para mostrar texto en el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="e2409-108">The functions also enable an application to write to standard output or standard error to display text in the console's screen buffer.</span></span> <span data-ttu-id="e2409-109">Las funciones de alto nivel también admiten la redirección de los identificadores estándar y el control de los modos de la consola para la funcionalidad de e/s diferente.</span><span class="sxs-lookup"><span data-stu-id="e2409-109">The high-level functions also support redirection of standard handles and control of console modes for different I/O functionality.</span></span> <span data-ttu-id="e2409-110">Las funciones de e/s de la consola de bajo nivel permiten que las aplicaciones reciban información detallada sobre los eventos del teclado y del mouse, así como los eventos que afectan a las interacciones del usuario con la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="e2409-110">The low-level console I/O functions enable applications to receive detailed input about keyboard and mouse events, as well as events involving user interactions with the console window.</span></span> <span data-ttu-id="e2409-111">Las funciones de bajo nivel también permiten un mayor control de la salida en la pantalla.</span><span class="sxs-lookup"><span data-stu-id="e2409-111">The low-level functions also enable greater control of output to the screen.</span></span>

<span data-ttu-id="e2409-112">En esta información general se describe la compatibilidad con aplicaciones de modo de carácter.</span><span class="sxs-lookup"><span data-stu-id="e2409-112">This overview describes support for character-mode applications.</span></span>

- [<span data-ttu-id="e2409-113">Acerca de las consolas</span><span class="sxs-lookup"><span data-stu-id="e2409-113">About Consoles</span></span>](about-character-mode-applications.md)
- [<span data-ttu-id="e2409-114">Uso de la consola</span><span class="sxs-lookup"><span data-stu-id="e2409-114">Using the Console</span></span>](using-the-console.md)
- [<span data-ttu-id="e2409-115">Referencia de la consola</span><span class="sxs-lookup"><span data-stu-id="e2409-115">Console Reference</span></span>](console-reference.md)
