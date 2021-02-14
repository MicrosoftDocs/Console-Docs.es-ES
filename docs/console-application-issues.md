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
# <a name="console-application-issues"></a>Problemas de la aplicación de consola

Las funciones de la consola de 8 bits usan la página de códigos OEM. Todas las demás funciones usan la página de códigos ANSI de forma predeterminada. Esto significa que las demás funciones no pueden procesar correctamente las cadenas devueltas por las funciones de la consola y viceversa. Por ejemplo, si **FindFirstFileA** devuelve una cadena que contiene ciertos caracteres ANSI extendidos, **WriteConsoleA** no mostrará la cadena correctamente.

La mejor solución a largo plazo para una aplicación de consola es usar **[Unicode](/windows/win32/intl/unicode)**. La consola aceptará la codificación UTF-16 en la variante W de las API o la codificación UTF-8 en la variante de las API después de usar **[SetConsoleCP](setconsolecp.md)** y **[SetConsoleOutputCP](setconsoleoutputcp.md)** en `65001` ( `CP_UTF8` Constant) para la página de códigos UTF-8.

Al excluir esa solución, una aplicación de consola debe usar la función [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) . Esa función cambia las funciones de archivo relevantes para que generen cadenas de juego de caracteres OEM en lugar de cadenas de juego de caracteres ANSI.

Las siguientes son funciones de archivo:

:::row:::
    :::column:::
        [CopyFile](/windows/win32/api/winbase/nf-winbase-copyfile)  
        [CreateDirectory](/windows/win32/api/fileapi/nf-fileapi-createdirectorya)  
        [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilea)  
        [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)  
        [DeleteFile](/windows/win32/api/fileapi/nf-fileapi-deletefilea)  
        [FindFirstFile](/windows/win32/api/fileapi/nf-fileapi-findfirstfilea)  
        [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilea)  
        [GetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-getcurrentdirectory)  
        [GetDiskFreeSpace](/windows/win32/api/fileapi/nf-fileapi-getdiskfreespacea)  
        [GetDriveType](/windows/win32/api/fileapi/nf-fileapi-getdrivetypea)  
    :::column-end:::
    :::column:::
        [GetFileAttributes](/windows/win32/api/fileapi/nf-fileapi-getfileattributesa)  
        [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamea)  
        [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamea)  
        [GetModuleHandle](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulehandlea)  
        [GetSystemDirectory](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemdirectorya)  
        [GetTempFileName](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamea)  
        [GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppatha)  
        [GetVolumeInformation](/windows/win32/api/fileapi/nf-fileapi-getvolumeinformationa)  
        [GetWindowsDirectory](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getwindowsdirectorya)  
        [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibrarya)  
    :::column-end:::
    :::column:::
        [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa)  
        [MoveFile](/windows/win32/api/winbase/nf-winbase-movefile)  
        [MoveFileEx](/windows/win32/api/winbase/nf-winbase-movefileexa)  
        [OpenFile](/windows/win32/api/winbase/nf-winbase-openfile)  
        [RemoveDirectory](/windows/win32/api/fileapi/nf-fileapi-removedirectorya)  
        [SearchPath](/windows/win32/api/processenv/nf-processenv-searchpatha)  
        [SetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory)  
        [SetFileAttributes](/windows/win32/api/fileapi/nf-fileapi-setfileattributesa)  
    :::column-end:::
:::row-end:::

Cuando se trabaja con líneas de comandos, una aplicación de consola debe obtener la línea de comandos en formato Unicode y convertirla al formato de OEM, con las funciones de carácter a OEM pertinentes. Tenga en cuenta también que *argv* usa el juego de caracteres ANSI.