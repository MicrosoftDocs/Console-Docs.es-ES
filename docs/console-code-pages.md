---
title: Páginas de código de la consola
description: Una página de códigos es una asignación de códigos de caracteres 256 a caracteres individuales. Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_code\_pages'
- base.console\_code\_pages
- consoles.console\_code\_pages
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98d56bb1-83d2-40aa-adac-fc2e8beab337
ms.openlocfilehash: 0ab9152c2be3f7487f43aee2a0a5c19766a433be
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358255"
---
# <a name="console-code-pages"></a><span data-ttu-id="cd005-105">Páginas de código de la consola</span><span class="sxs-lookup"><span data-stu-id="cd005-105">Console Code Pages</span></span>

<span data-ttu-id="cd005-106">Una *Página de códigos* es una asignación de códigos de caracteres 256 a caracteres individuales.</span><span class="sxs-lookup"><span data-stu-id="cd005-106">A *code page* is a mapping of 256 character codes to individual characters.</span></span> <span data-ttu-id="cd005-107">Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas.</span><span class="sxs-lookup"><span data-stu-id="cd005-107">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="cd005-108">Los asociados a cada consola son dos páginas de códigos: una para la entrada y otra para la salida.</span><span class="sxs-lookup"><span data-stu-id="cd005-108">Associated with each console are two code pages: one for input and one for output.</span></span> <span data-ttu-id="cd005-109">Una consola usa su página de códigos de entrada para traducir la entrada del teclado en el valor de carácter correspondiente.</span><span class="sxs-lookup"><span data-stu-id="cd005-109">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span> <span data-ttu-id="cd005-110">Usa la página de códigos de salida para traducir los valores de caracteres escritos por las distintas funciones de salida en las imágenes que se muestran en la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="cd005-110">It uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span> <span data-ttu-id="cd005-111">Una aplicación puede usar las funciones [**SetConsoleCP**](setconsolecp.md) y [**GetConsoleCP**](getconsolecp.md) para establecer y recuperar las páginas de códigos de entrada de una consola y las funciones [**SetConsoleOutputCP**](setconsoleoutputcp.md) y [**GetConsoleOutputCP**](getconsoleoutputcp.md) para establecer y recuperar sus páginas de códigos de salida.</span><span class="sxs-lookup"><span data-stu-id="cd005-111">An application can use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions to set and retrieve a console's input code pages and the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions to set and retrieve its output code pages.</span></span>

<span data-ttu-id="cd005-112">Los identificadores de las páginas de códigos disponibles en el equipo local se almacenan en el registro con la siguiente clave: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`</span><span class="sxs-lookup"><span data-stu-id="cd005-112">The identifiers of the code pages available on the local computer are stored in the registry under the following key: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`</span></span>

<span data-ttu-id="cd005-113">Para obtener información sobre el uso de las funciones del registro para determinar las páginas de códigos disponibles, vea [**Registry**](/windows/win32/sysinfo/registry).</span><span class="sxs-lookup"><span data-stu-id="cd005-113">For information about using the registry functions to determine the available code pages, see [**Registry**](/windows/win32/sysinfo/registry).</span></span>

> [!TIP]
> <span data-ttu-id="cd005-114">Se recomienda para todas las aplicaciones de línea de comandos nuevas y actualizadas para evitar páginas de códigos y usar **[Unicode](/windows/win32/intl/unicode)**.</span><span class="sxs-lookup"><span data-stu-id="cd005-114">It is recommended for all new and updated command-line applications to avoid code pages and use **[Unicode](/windows/win32/intl/unicode)**.</span></span> <span data-ttu-id="cd005-115">El texto con formato UTF-16 se puede enviar a la familia *W* de API de consola.</span><span class="sxs-lookup"><span data-stu-id="cd005-115">UTF-16 formatted text can be sent to the *W* family of console APIs.</span></span> <span data-ttu-id="cd005-116">El texto con formato UTF-8 se puede enviar a *una* familia de API de consola después de asegurarse de que la página de códigos se establece primero en **[65001 (CP_UTF8)](/windows/win32/intl/code-page-identifiers)** con las funciones [**SetConsoleCP**](setconsolecp.md) y [**SetConsoleOutputCP**](setconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="cd005-116">UTF-8 formatted text can be sent to the *A* family of console APIs after ensuring the code page is first set to **[65001 (CP_UTF8)](/windows/win32/intl/code-page-identifiers)** with the [**SetConsoleCP**](setconsolecp.md) and [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions.</span></span>