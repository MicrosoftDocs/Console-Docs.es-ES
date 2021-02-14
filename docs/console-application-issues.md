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
ms.openlocfilehash: e81a2b8f6e3b7ba17a7fd704aac868425c86d52c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358275"
---
# <a name="console-application-issues"></a><span data-ttu-id="30ad2-104">Problemas de la aplicación de consola</span><span class="sxs-lookup"><span data-stu-id="30ad2-104">Console Application Issues</span></span>

<span data-ttu-id="30ad2-105">Las funciones de la consola de 8 bits usan la página de códigos OEM.</span><span class="sxs-lookup"><span data-stu-id="30ad2-105">The 8-bit console functions use the OEM code page.</span></span> <span data-ttu-id="30ad2-106">Todas las demás funciones usan la página de códigos ANSI de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="30ad2-106">All other functions use the ANSI code page by default.</span></span> <span data-ttu-id="30ad2-107">Esto significa que las demás funciones no pueden procesar correctamente las cadenas devueltas por las funciones de la consola y viceversa.</span><span class="sxs-lookup"><span data-stu-id="30ad2-107">This means that strings returned by the console functions may not be processed correctly by the other functions and vice versa.</span></span> <span data-ttu-id="30ad2-108">Por ejemplo, si **FindFirstFileA** devuelve una cadena que contiene ciertos caracteres ANSI extendidos, **WriteConsoleA** no mostrará la cadena correctamente.</span><span class="sxs-lookup"><span data-stu-id="30ad2-108">For example, if **FindFirstFileA** returns a string that contains certain extended ANSI characters, **WriteConsoleA** will not display the string properly.</span></span>

<span data-ttu-id="30ad2-109">La mejor solución a largo plazo para una aplicación de consola es usar **[Unicode](/windows/win32/intl/unicode)**.</span><span class="sxs-lookup"><span data-stu-id="30ad2-109">The best long-term solution for a console application is to use **[Unicode](/windows/win32/intl/unicode)**.</span></span> <span data-ttu-id="30ad2-110">La consola aceptará la codificación UTF-16 en la variante W de las API o la codificación UTF-8 en la variante de las API después de usar **[SetConsoleCP](setconsolecp.md)** y **[SetConsoleOutputCP](setconsoleoutputcp.md)** en `65001` ( `CP_UTF8` Constant) para la página de códigos UTF-8.</span><span class="sxs-lookup"><span data-stu-id="30ad2-110">The console will accept UTF-16 encoding on the W variant of the APIs or UTF-8 encoding on the A variant of the APIs after using **[SetConsoleCP](setconsolecp.md)** and **[SetConsoleOutputCP](setconsoleoutputcp.md)** to `65001` (`CP_UTF8` constant) for the UTF-8 code page.</span></span>

<span data-ttu-id="30ad2-111">Al excluir esa solución, una aplicación de consola debe usar la función [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) .</span><span class="sxs-lookup"><span data-stu-id="30ad2-111">Barring that solution, a console application should use the [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) function.</span></span> <span data-ttu-id="30ad2-112">Esa función cambia las funciones de archivo relevantes para que generen cadenas de juego de caracteres OEM en lugar de cadenas de juego de caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="30ad2-112">That function changes relevant file functions so that they produce OEM character set strings rather than ANSI character set strings.</span></span>

<span data-ttu-id="30ad2-113">Las siguientes son funciones de archivo:</span><span class="sxs-lookup"><span data-stu-id="30ad2-113">The following are file functions:</span></span>

:::row:::
    :::column:::
        [<span data-ttu-id="30ad2-114">CopyFile</span><span class="sxs-lookup"><span data-stu-id="30ad2-114">CopyFile</span></span>](/windows/win32/api/winbase/nf-winbase-copyfile)  
        [<span data-ttu-id="30ad2-115">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="30ad2-115">CreateDirectory</span></span>](/windows/win32/api/fileapi/nf-fileapi-createdirectorya)  
        [<span data-ttu-id="30ad2-116">CreateFile</span><span class="sxs-lookup"><span data-stu-id="30ad2-116">CreateFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-createfilea)  
        [<span data-ttu-id="30ad2-117">CreateProcess</span><span class="sxs-lookup"><span data-stu-id="30ad2-117">CreateProcess</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)  
        [<span data-ttu-id="30ad2-118">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="30ad2-118">DeleteFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-deletefilea)  
        [<span data-ttu-id="30ad2-119">FindFirstFile</span><span class="sxs-lookup"><span data-stu-id="30ad2-119">FindFirstFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-findfirstfilea)  
        [<span data-ttu-id="30ad2-120">FindNextFile</span><span class="sxs-lookup"><span data-stu-id="30ad2-120">FindNextFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-findnextfilea)  
        [<span data-ttu-id="30ad2-121">GetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="30ad2-121">GetCurrentDirectory</span></span>](/windows/win32/api/winbase/nf-winbase-getcurrentdirectory)  
        [<span data-ttu-id="30ad2-122">GetDiskFreeSpace</span><span class="sxs-lookup"><span data-stu-id="30ad2-122">GetDiskFreeSpace</span></span>](/windows/win32/api/fileapi/nf-fileapi-getdiskfreespacea)  
        [<span data-ttu-id="30ad2-123">GetDriveType</span><span class="sxs-lookup"><span data-stu-id="30ad2-123">GetDriveType</span></span>](/windows/win32/api/fileapi/nf-fileapi-getdrivetypea)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="30ad2-124">GetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="30ad2-124">GetFileAttributes</span></span>](/windows/win32/api/fileapi/nf-fileapi-getfileattributesa)  
        [<span data-ttu-id="30ad2-125">GetFullPathName</span><span class="sxs-lookup"><span data-stu-id="30ad2-125">GetFullPathName</span></span>](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamea)  
        [<span data-ttu-id="30ad2-126">GetModuleFileName</span><span class="sxs-lookup"><span data-stu-id="30ad2-126">GetModuleFileName</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamea)  
        [<span data-ttu-id="30ad2-127">GetModuleHandle</span><span class="sxs-lookup"><span data-stu-id="30ad2-127">GetModuleHandle</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulehandlea)  
        [<span data-ttu-id="30ad2-128">GetSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="30ad2-128">GetSystemDirectory</span></span>](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemdirectorya)  
        [<span data-ttu-id="30ad2-129">GetTempFileName</span><span class="sxs-lookup"><span data-stu-id="30ad2-129">GetTempFileName</span></span>](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamea)  
        [<span data-ttu-id="30ad2-130">GetTempPath</span><span class="sxs-lookup"><span data-stu-id="30ad2-130">GetTempPath</span></span>](/windows/win32/api/fileapi/nf-fileapi-gettemppatha)  
        [<span data-ttu-id="30ad2-131">GetVolumeInformation</span><span class="sxs-lookup"><span data-stu-id="30ad2-131">GetVolumeInformation</span></span>](/windows/win32/api/fileapi/nf-fileapi-getvolumeinformationa)  
        [<span data-ttu-id="30ad2-132">GetWindowsDirectory</span><span class="sxs-lookup"><span data-stu-id="30ad2-132">GetWindowsDirectory</span></span>](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getwindowsdirectorya)  
        [<span data-ttu-id="30ad2-133">LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="30ad2-133">LoadLibrary</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibrarya)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="30ad2-134">LoadLibraryEx</span><span class="sxs-lookup"><span data-stu-id="30ad2-134">LoadLibraryEx</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa)  
        [<span data-ttu-id="30ad2-135">MoveFile</span><span class="sxs-lookup"><span data-stu-id="30ad2-135">MoveFile</span></span>](/windows/win32/api/winbase/nf-winbase-movefile)  
        [<span data-ttu-id="30ad2-136">MoveFileEx</span><span class="sxs-lookup"><span data-stu-id="30ad2-136">MoveFileEx</span></span>](/windows/win32/api/winbase/nf-winbase-movefileexa)  
        [<span data-ttu-id="30ad2-137">OpenFile</span><span class="sxs-lookup"><span data-stu-id="30ad2-137">OpenFile</span></span>](/windows/win32/api/winbase/nf-winbase-openfile)  
        [<span data-ttu-id="30ad2-138">RemoveDirectory</span><span class="sxs-lookup"><span data-stu-id="30ad2-138">RemoveDirectory</span></span>](/windows/win32/api/fileapi/nf-fileapi-removedirectorya)  
        [<span data-ttu-id="30ad2-139">SearchPath</span><span class="sxs-lookup"><span data-stu-id="30ad2-139">SearchPath</span></span>](/windows/win32/api/processenv/nf-processenv-searchpatha)  
        [<span data-ttu-id="30ad2-140">SetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="30ad2-140">SetCurrentDirectory</span></span>](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory)  
        [<span data-ttu-id="30ad2-141">SetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="30ad2-141">SetFileAttributes</span></span>](/windows/win32/api/fileapi/nf-fileapi-setfileattributesa)  
    :::column-end:::
:::row-end:::

<span data-ttu-id="30ad2-142">Cuando se trabaja con líneas de comandos, una aplicación de consola debe obtener la línea de comandos en formato Unicode y convertirla al formato de OEM, con las funciones de carácter a OEM pertinentes.</span><span class="sxs-lookup"><span data-stu-id="30ad2-142">When dealing with command lines, a console application should obtain the command line in Unicode form and convert it to OEM form, using the relevant character-to-OEM functions.</span></span> <span data-ttu-id="30ad2-143">Tenga en cuenta también que *argv* usa el juego de caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="30ad2-143">Note, also, that *argv* uses the ANSI character set.</span></span>