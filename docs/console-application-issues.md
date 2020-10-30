---
title: Problemas de la aplicación de consola
description: Revise los problemas de la aplicación de consola, como las funciones que toman o devuelven cadenas de juego de caracteres OEM frente a funciones que toman o devuelven cadenas de juego de caracteres ANSI.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_application\_issues'
- base.console\_application\_issues
- consoles.console\_application\_issues
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a561fbdd-b50d-4687-92d7-735377a7991d
ms.openlocfilehash: a1e49e605d1379984ebff7d1737db5ef96c4ff0f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038463"
---
# <a name="console-application-issues"></a><span data-ttu-id="5dd02-104">Problemas de la aplicación de consola</span><span class="sxs-lookup"><span data-stu-id="5dd02-104">Console Application Issues</span></span>

<span data-ttu-id="5dd02-105">Las funciones de la consola de 8 bits usan la página de códigos OEM.</span><span class="sxs-lookup"><span data-stu-id="5dd02-105">The 8-bit console functions use the OEM code page.</span></span> <span data-ttu-id="5dd02-106">Todas las demás funciones usan la página de códigos ANSI de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="5dd02-106">All other functions use the ANSI code page by default.</span></span> <span data-ttu-id="5dd02-107">Esto significa que las demás funciones no pueden procesar correctamente las cadenas devueltas por las funciones de la consola y viceversa.</span><span class="sxs-lookup"><span data-stu-id="5dd02-107">This means that strings returned by the console functions may not be processed correctly by the other functions and vice versa.</span></span> <span data-ttu-id="5dd02-108">Por ejemplo, si **FindFirstFileA** devuelve una cadena que contiene ciertos caracteres ANSI extendidos, **WriteConsoleA** no mostrará la cadena correctamente.</span><span class="sxs-lookup"><span data-stu-id="5dd02-108">For example, if **FindFirstFileA** returns a string that contains certain extended ANSI characters, **WriteConsoleA** will not display the string properly.</span></span>

<span data-ttu-id="5dd02-109">La mejor solución a largo plazo para una aplicación de consola es usar **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** .</span><span class="sxs-lookup"><span data-stu-id="5dd02-109">The best long-term solution for a console application is to use **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** .</span></span> <span data-ttu-id="5dd02-110">La consola aceptará la codificación UTF-16 en la variante W de las API o la codificación UTF-8 en la variante de las API después de usar **[SetConsoleCP](setconsolecp.md)** y **[SetConsoleOutputCP](setconsoleoutputcp.md)** en `65001` ( `CP_UTF8` Constant) para la página de códigos UTF-8.</span><span class="sxs-lookup"><span data-stu-id="5dd02-110">The console will accept UTF-16 encoding on the W variant of the APIs or UTF-8 encoding on the A variant of the APIs after using **[SetConsoleCP](setconsolecp.md)** and **[SetConsoleOutputCP](setconsoleoutputcp.md)** to `65001` (`CP_UTF8` constant) for the UTF-8 code page.</span></span>

<span data-ttu-id="5dd02-111">Al excluir esa solución, una aplicación de consola debe usar la función [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) .</span><span class="sxs-lookup"><span data-stu-id="5dd02-111">Barring that solution, a console application should use the [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) function.</span></span> <span data-ttu-id="5dd02-112">Esa función cambia las funciones de archivo relevantes para que generen cadenas de juego de caracteres OEM en lugar de cadenas de juego de caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="5dd02-112">That function changes relevant file functions so that they produce OEM character set strings rather than ANSI character set strings.</span></span>

<span data-ttu-id="5dd02-113">Las siguientes son funciones de archivo:</span><span class="sxs-lookup"><span data-stu-id="5dd02-113">The following are file functions:</span></span>

:::row:::
    :::column:::
        [<span data-ttu-id="5dd02-114">CopyFile</span><span class="sxs-lookup"><span data-stu-id="5dd02-114">CopyFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363851)  
        [<span data-ttu-id="5dd02-115">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="5dd02-115">CreateDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363855)  
        [<span data-ttu-id="5dd02-116">CreateFile</span><span class="sxs-lookup"><span data-stu-id="5dd02-116">CreateFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)  
        [<span data-ttu-id="5dd02-117">CreateProcess</span><span class="sxs-lookup"><span data-stu-id="5dd02-117">CreateProcess</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)  
        [<span data-ttu-id="5dd02-118">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="5dd02-118">DeleteFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363915)  
        [<span data-ttu-id="5dd02-119">FindFirstFile</span><span class="sxs-lookup"><span data-stu-id="5dd02-119">FindFirstFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364418)  
        [<span data-ttu-id="5dd02-120">FindNextFile</span><span class="sxs-lookup"><span data-stu-id="5dd02-120">FindNextFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364428)  
        [<span data-ttu-id="5dd02-121">GetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="5dd02-121">GetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364934)  
        [<span data-ttu-id="5dd02-122">GetDiskFreeSpace</span><span class="sxs-lookup"><span data-stu-id="5dd02-122">GetDiskFreeSpace</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364935)  
        [<span data-ttu-id="5dd02-123">GetDriveType</span><span class="sxs-lookup"><span data-stu-id="5dd02-123">GetDriveType</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364939)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="5dd02-124">GetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="5dd02-124">GetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364944)  
        [<span data-ttu-id="5dd02-125">GetFullPathName</span><span class="sxs-lookup"><span data-stu-id="5dd02-125">GetFullPathName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364963)  
        [<span data-ttu-id="5dd02-126">GetModuleFileName</span><span class="sxs-lookup"><span data-stu-id="5dd02-126">GetModuleFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683197)  
        [<span data-ttu-id="5dd02-127">GetModuleHandle</span><span class="sxs-lookup"><span data-stu-id="5dd02-127">GetModuleHandle</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683199)  
        [<span data-ttu-id="5dd02-128">GetSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="5dd02-128">GetSystemDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724373)  
        [<span data-ttu-id="5dd02-129">GetTempFileName</span><span class="sxs-lookup"><span data-stu-id="5dd02-129">GetTempFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364991)  
        [<span data-ttu-id="5dd02-130">GetTempPath</span><span class="sxs-lookup"><span data-stu-id="5dd02-130">GetTempPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364992)  
        [<span data-ttu-id="5dd02-131">GetVolumeInformation</span><span class="sxs-lookup"><span data-stu-id="5dd02-131">GetVolumeInformation</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364993)  
        [<span data-ttu-id="5dd02-132">GetWindowsDirectory</span><span class="sxs-lookup"><span data-stu-id="5dd02-132">GetWindowsDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724454)  
        [<span data-ttu-id="5dd02-133">LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="5dd02-133">LoadLibrary</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684175)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="5dd02-134">LoadLibraryEx</span><span class="sxs-lookup"><span data-stu-id="5dd02-134">LoadLibraryEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684179)  
        [<span data-ttu-id="5dd02-135">MoveFile</span><span class="sxs-lookup"><span data-stu-id="5dd02-135">MoveFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365239)  
        [<span data-ttu-id="5dd02-136">MoveFileEx</span><span class="sxs-lookup"><span data-stu-id="5dd02-136">MoveFileEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365240)  
        [<span data-ttu-id="5dd02-137">OpenFile</span><span class="sxs-lookup"><span data-stu-id="5dd02-137">OpenFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365430)  
        [<span data-ttu-id="5dd02-138">RemoveDirectory</span><span class="sxs-lookup"><span data-stu-id="5dd02-138">RemoveDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365488)  
        [<span data-ttu-id="5dd02-139">SearchPath</span><span class="sxs-lookup"><span data-stu-id="5dd02-139">SearchPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365527)  
        [<span data-ttu-id="5dd02-140">SetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="5dd02-140">SetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365530)  
        [<span data-ttu-id="5dd02-141">SetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="5dd02-141">SetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365535)  
    :::column-end:::
:::row-end:::

<span data-ttu-id="5dd02-142">Cuando se trabaja con líneas de comandos, una aplicación de consola debe obtener la línea de comandos en formato Unicode y convertirla al formato de OEM, con las funciones de carácter a OEM pertinentes.</span><span class="sxs-lookup"><span data-stu-id="5dd02-142">When dealing with command lines, a console application should obtain the command line in Unicode form and convert it to OEM form, using the relevant character-to-OEM functions.</span></span> <span data-ttu-id="5dd02-143">Tenga en cuenta también que *argv* usa el juego de caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="5dd02-143">Note, also, that *argv* uses the ANSI character set.</span></span>
