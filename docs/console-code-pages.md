---
title: Páginas de códigos de la consola
description: Una página de códigos es una asignación de códigos de caracteres 256 a caracteres individuales. Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_code\_pages'
- base.console\_code\_pages
- consoles.console\_code\_pages
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98d56bb1-83d2-40aa-adac-fc2e8beab337
ms.openlocfilehash: cacc4cb1d88a7d2aa01c35e0f0d94b44c393d28c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060877"
---
# <a name="console-code-pages"></a><span data-ttu-id="d02be-105">Páginas de códigos de la consola</span><span class="sxs-lookup"><span data-stu-id="d02be-105">Console Code Pages</span></span>


<span data-ttu-id="d02be-106">Una *Página de códigos* es una asignación de códigos de caracteres 256 a caracteres individuales.</span><span class="sxs-lookup"><span data-stu-id="d02be-106">A *code page* is a mapping of 256 character codes to individual characters.</span></span> <span data-ttu-id="d02be-107">Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas.</span><span class="sxs-lookup"><span data-stu-id="d02be-107">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="d02be-108">Los asociados a cada consola son dos páginas de códigos: una para la entrada y otra para la salida.</span><span class="sxs-lookup"><span data-stu-id="d02be-108">Associated with each console are two code pages: one for input and one for output.</span></span> <span data-ttu-id="d02be-109">Una consola usa su página de códigos de entrada para traducir la entrada del teclado en el valor de carácter correspondiente.</span><span class="sxs-lookup"><span data-stu-id="d02be-109">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span> <span data-ttu-id="d02be-110">Usa la página de códigos de salida para traducir los valores de caracteres escritos por las distintas funciones de salida en las imágenes que se muestran en la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="d02be-110">It uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span> <span data-ttu-id="d02be-111">Una aplicación puede usar las funciones [**SetConsoleCP**](setconsolecp.md) y [**GetConsoleCP**](getconsolecp.md) para establecer y recuperar las páginas de códigos de entrada de una consola y las funciones [**SetConsoleOutputCP**](setconsoleoutputcp.md) y [**GetConsoleOutputCP**](getconsoleoutputcp.md) para establecer y recuperar sus páginas de códigos de salida.</span><span class="sxs-lookup"><span data-stu-id="d02be-111">An application can use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions to set and retrieve a console's input code pages and the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions to set and retrieve its output code pages.</span></span>

<span data-ttu-id="d02be-112">Los identificadores de las páginas de códigos disponibles en el equipo local se almacenan en el registro con la siguiente clave.</span><span class="sxs-lookup"><span data-stu-id="d02be-112">The identifiers of the code pages available on the local computer are stored in the registry under the following key.</span></span>

<span data-ttu-id="d02be-113">**HKEY \_ local \_ Machine \\ System \\ CurrentControlSet \\ control de la página de \\ \\ códigos NLS**</span><span class="sxs-lookup"><span data-stu-id="d02be-113">**HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Nls\\CodePage**</span></span>

<span data-ttu-id="d02be-114">Para obtener información sobre el uso de las funciones del registro para determinar las páginas de códigos disponibles, vea [**Registry**](https://msdn.microsoft.com/library/windows/desktop/ms724871).</span><span class="sxs-lookup"><span data-stu-id="d02be-114">For information about using the registry functions to determine the available code pages, see [**Registry**](https://msdn.microsoft.com/library/windows/desktop/ms724871).</span></span>

 

 




