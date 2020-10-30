---
title: 'Pseudoconsoles: escritorio de Windows'
description: Un pseudoconsole es un concepto que se usa para proporcionar el aspecto de hospedaje o servicio de una aplicación en modo de carácter.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola, conpty, pseudoconsole
ms.openlocfilehash: 2b2d28065ec4f0e4121decb906e76b34ac1871fc
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039483"
---
# <a name="pseudoconsoles"></a><span data-ttu-id="a2f2b-104">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="a2f2b-104">Pseudoconsoles</span></span>

<span data-ttu-id="a2f2b-105">Un *pseudoconsole* es un tipo de dispositivo que permite que las aplicaciones se conviertan en el host para las aplicaciones en modo de carácter.</span><span class="sxs-lookup"><span data-stu-id="a2f2b-105">A *pseudoconsole* is a device type that allows applications to become the host for character-mode applications.</span></span>

<span data-ttu-id="a2f2b-106">Esto contrasta con una sesión de consola típica en la que el sistema operativo creará una ventana de hospedaje en nombre de la aplicación de modo de carácter para controlar la salida gráfica y los datos proporcionados por el usuario.</span><span class="sxs-lookup"><span data-stu-id="a2f2b-106">This is in contrast to a typical console session where the operating system will create a hosting window on behalf of the character-mode application to handle graphical output and user input.</span></span>

<span data-ttu-id="a2f2b-107">Con un pseudoconsole, no se crea la ventana de hospedaje.</span><span class="sxs-lookup"><span data-stu-id="a2f2b-107">With a pseudoconsole, the hosting window is not created.</span></span> <span data-ttu-id="a2f2b-108">La aplicación que realiza el pseudoconsole debe ser responsable de mostrar la salida gráfica y recopilar los datos proporcionados por el usuario.</span><span class="sxs-lookup"><span data-stu-id="a2f2b-108">The application that makes the pseudoconsole must become responsible for displaying the graphical output and collecting user input.</span></span> <span data-ttu-id="a2f2b-109">Como alternativa, la información se puede retransmitir más a otra aplicación responsable de estas actividades en un punto posterior de la cadena.</span><span class="sxs-lookup"><span data-stu-id="a2f2b-109">Alternatively, the information can be relayed further to another application responsible for these activities at a later point in the chain.</span></span>

<span data-ttu-id="a2f2b-110">Esta funcionalidad está diseñada para que las aplicaciones de "ventana de terminal" de terceros existan en la plataforma o para el redireccionamiento de las actividades de modo de carácter a una sesión de "ventana de terminal" remota en otra máquina o incluso en otra plataforma.</span><span class="sxs-lookup"><span data-stu-id="a2f2b-110">This functionality is designed for third-party "terminal window" applications to exist on the platform or for redirection of character-mode activities to a remote "terminal window" session on another machine or even on another platform.</span></span>

<span data-ttu-id="a2f2b-111">Tenga en cuenta que la sesión de la consola subyacente todavía se creará en nombre de la aplicación que solicita el pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="a2f2b-111">Note that the underlying console session will still be created on behalf of the application requesting the pseudoconsole.</span></span> <span data-ttu-id="a2f2b-112">Todas las reglas de las [sesiones de consola](consoles.md) se siguen aplicando, lo que incluye la posibilidad de que varias aplicaciones de modo de caracteres de cliente se conecten a la sesión.</span><span class="sxs-lookup"><span data-stu-id="a2f2b-112">All the rules of [console sessions](consoles.md) still apply including the ability for multiple client character-mode applications to connect to the session.</span></span>

<span data-ttu-id="a2f2b-113">Para proporcionar la máxima compatibilidad con el mundo existente de la funcionalidad de pseudoterminal, la información proporcionada a través del canal de pseudoconsole siempre se codificará en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="a2f2b-113">To provide maximum compatibility with the existing world of pseudoterminal functionality, the information provided over the pseudoconsole channel will always be encoded in UTF-8.</span></span> <span data-ttu-id="a2f2b-114">Esto no afecta a la página de códigos o la codificación de las aplicaciones cliente que están conectadas.</span><span class="sxs-lookup"><span data-stu-id="a2f2b-114">This does not affect the codepage or encoding of the client applications that are attached.</span></span> <span data-ttu-id="a2f2b-115">La traducción se producirá dentro del sistema pseudoconsole según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="a2f2b-115">Translation will happen inside the pseudoconsole system as necessary.</span></span>

<span data-ttu-id="a2f2b-116">Puede encontrar un ejemplo de introducción en creación de [una sesión de Pseudoconsole](creating-a-pseudoconsole-session.md).</span><span class="sxs-lookup"><span data-stu-id="a2f2b-116">An example for getting started can be found at [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).</span></span>

<span data-ttu-id="a2f2b-117">Puede encontrar información general adicional sobre pseudoconsoles en la entrada de blog del anuncio: [línea de comandos de Windows: Introducción a la pseudo consola de Windows (ConPTY)](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span><span class="sxs-lookup"><span data-stu-id="a2f2b-117">Some additional background information on pseudoconsoles can be found at the announcement blog post: [Windows Command-Line: Introducing the Windows Pseudo Console (ConPTY)](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span></span>
