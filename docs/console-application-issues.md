---
title: Problemas de la aplicación de consola
description: Revise los problemas de la aplicación de consola, como las funciones que toman o devuelven cadenas de juego de caracteres OEM frente a funciones que toman o devuelven cadenas de juego de caracteres ANSI.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_application\_issues'
- base.console\_application\_issues
- consoles.console\_application\_issues
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a561fbdd-b50d-4687-92d7-735377a7991d
ms.openlocfilehash: 4bf0d6792a991d8ae141ec0b1b9c940311e00ab9
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060889"
---
# <a name="console-application-issues"></a><span data-ttu-id="9014e-104">Problemas de la aplicación de consola</span><span class="sxs-lookup"><span data-stu-id="9014e-104">Console Application Issues</span></span>

<span data-ttu-id="9014e-105">Las funciones de la consola de 8 bits usan la página de códigos OEM.</span><span class="sxs-lookup"><span data-stu-id="9014e-105">The 8-bit console functions use the OEM code page.</span></span> <span data-ttu-id="9014e-106">Todas las demás funciones usan la página de códigos ANSI de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="9014e-106">All other functions use the ANSI code page by default.</span></span> <span data-ttu-id="9014e-107">Esto significa que las demás funciones no pueden procesar correctamente las cadenas devueltas por las funciones de la consola y viceversa.</span><span class="sxs-lookup"><span data-stu-id="9014e-107">This means that strings returned by the console functions may not be processed correctly by the other functions and vice versa.</span></span> <span data-ttu-id="9014e-108">Por ejemplo, si **FindFirstFileA** devuelve una cadena que contiene ciertos caracteres ANSI extendidos, **WriteConsoleA** no mostrará la cadena correctamente.</span><span class="sxs-lookup"><span data-stu-id="9014e-108">For example, if **FindFirstFileA** returns a string that contains certain extended ANSI characters, **WriteConsoleA** will not display the string properly.</span></span>

<span data-ttu-id="9014e-109">La mejor solución a largo plazo para una aplicación de consola es usar Unicode.</span><span class="sxs-lookup"><span data-stu-id="9014e-109">The best long-term solution for a console application is to use Unicode.</span></span> <span data-ttu-id="9014e-110">Al excluir esa solución, una aplicación de consola debe usar la función [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) .</span><span class="sxs-lookup"><span data-stu-id="9014e-110">Barring that solution, a console application should use the [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) function.</span></span> <span data-ttu-id="9014e-111">Esa función cambia las funciones de archivo relevantes para que generen cadenas de juego de caracteres OEM en lugar de cadenas de juego de caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="9014e-111">That function changes relevant file functions so that they produce OEM character set strings rather than ANSI character set strings.</span></span>

<span data-ttu-id="9014e-112">Las siguientes son funciones de archivo:</span><span class="sxs-lookup"><span data-stu-id="9014e-112">The following are file functions:</span></span>

:::row:::
    :::column:::
        [<span data-ttu-id="9014e-113">CopyFile</span><span class="sxs-lookup"><span data-stu-id="9014e-113">CopyFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363851)  
        [<span data-ttu-id="9014e-114">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="9014e-114">CreateDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363855)  
        [<span data-ttu-id="9014e-115">CreateFile</span><span class="sxs-lookup"><span data-stu-id="9014e-115">CreateFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)  
        [<span data-ttu-id="9014e-116">CreateProcess</span><span class="sxs-lookup"><span data-stu-id="9014e-116">CreateProcess</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)  
        [<span data-ttu-id="9014e-117">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="9014e-117">DeleteFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363915)  
        [<span data-ttu-id="9014e-118">FindFirstFile</span><span class="sxs-lookup"><span data-stu-id="9014e-118">FindFirstFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364418)  
        [<span data-ttu-id="9014e-119">FindNextFile</span><span class="sxs-lookup"><span data-stu-id="9014e-119">FindNextFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364428)  
        [<span data-ttu-id="9014e-120">GetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="9014e-120">GetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364934)  
        [<span data-ttu-id="9014e-121">GetDiskFreeSpace</span><span class="sxs-lookup"><span data-stu-id="9014e-121">GetDiskFreeSpace</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364935)  
        [<span data-ttu-id="9014e-122">GetDriveType</span><span class="sxs-lookup"><span data-stu-id="9014e-122">GetDriveType</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364939)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="9014e-123">GetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="9014e-123">GetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364944)  
        [<span data-ttu-id="9014e-124">GetFullPathName</span><span class="sxs-lookup"><span data-stu-id="9014e-124">GetFullPathName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364963)  
        [<span data-ttu-id="9014e-125">GetModuleFileName</span><span class="sxs-lookup"><span data-stu-id="9014e-125">GetModuleFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683197)  
        [<span data-ttu-id="9014e-126">GetModuleHandle</span><span class="sxs-lookup"><span data-stu-id="9014e-126">GetModuleHandle</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683199)  
        [<span data-ttu-id="9014e-127">GetSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="9014e-127">GetSystemDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724373)  
        [<span data-ttu-id="9014e-128">GetTempFileName</span><span class="sxs-lookup"><span data-stu-id="9014e-128">GetTempFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364991)  
        [<span data-ttu-id="9014e-129">GetTempPath</span><span class="sxs-lookup"><span data-stu-id="9014e-129">GetTempPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364992)  
        [<span data-ttu-id="9014e-130">GetVolumeInformation</span><span class="sxs-lookup"><span data-stu-id="9014e-130">GetVolumeInformation</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364993)  
        [<span data-ttu-id="9014e-131">GetWindowsDirectory</span><span class="sxs-lookup"><span data-stu-id="9014e-131">GetWindowsDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724454)  
        [<span data-ttu-id="9014e-132">LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="9014e-132">LoadLibrary</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684175)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="9014e-133">LoadLibraryEx</span><span class="sxs-lookup"><span data-stu-id="9014e-133">LoadLibraryEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684179)  
        [<span data-ttu-id="9014e-134">MoveFile</span><span class="sxs-lookup"><span data-stu-id="9014e-134">MoveFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365239)  
        [<span data-ttu-id="9014e-135">MoveFileEx</span><span class="sxs-lookup"><span data-stu-id="9014e-135">MoveFileEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365240)  
        [<span data-ttu-id="9014e-136">OpenFile</span><span class="sxs-lookup"><span data-stu-id="9014e-136">OpenFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365430)  
        [<span data-ttu-id="9014e-137">RemoveDirectory</span><span class="sxs-lookup"><span data-stu-id="9014e-137">RemoveDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365488)  
        [<span data-ttu-id="9014e-138">SearchPath</span><span class="sxs-lookup"><span data-stu-id="9014e-138">SearchPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365527)  
        [<span data-ttu-id="9014e-139">SetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="9014e-139">SetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365530)  
        [<span data-ttu-id="9014e-140">SetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="9014e-140">SetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365535)  
    :::column-end:::
:::row-end:::

<span data-ttu-id="9014e-141">Cuando se trabaja con líneas de comandos, una aplicación de consola debe obtener la línea de comandos en formato Unicode y convertirla al formato de OEM, con las funciones de carácter a OEM pertinentes.</span><span class="sxs-lookup"><span data-stu-id="9014e-141">When dealing with command lines, a console application should obtain the command line in Unicode form and convert it to OEM form, using the relevant character-to-OEM functions.</span></span> <span data-ttu-id="9014e-142">Tenga en cuenta también que *argv* usa el juego de caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="9014e-142">Note, also, that *argv* uses the ANSI character set.</span></span>
