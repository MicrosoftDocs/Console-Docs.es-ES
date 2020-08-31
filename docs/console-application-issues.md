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
# <a name="console-application-issues"></a>Problemas de la aplicación de consola

Las funciones de la consola de 8 bits usan la página de códigos OEM. Todas las demás funciones usan la página de códigos ANSI de forma predeterminada. Esto significa que las demás funciones no pueden procesar correctamente las cadenas devueltas por las funciones de la consola y viceversa. Por ejemplo, si **FindFirstFileA** devuelve una cadena que contiene ciertos caracteres ANSI extendidos, **WriteConsoleA** no mostrará la cadena correctamente.

La mejor solución a largo plazo para una aplicación de consola es usar Unicode. Al excluir esa solución, una aplicación de consola debe usar la función [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) . Esa función cambia las funciones de archivo relevantes para que generen cadenas de juego de caracteres OEM en lugar de cadenas de juego de caracteres ANSI.

Las siguientes son funciones de archivo:

:::row:::
    :::column:::
        [CopyFile](https://msdn.microsoft.com/library/windows/desktop/aa363851)  
        [CreateDirectory](https://msdn.microsoft.com/library/windows/desktop/aa363855)  
        [CreateFile](https://msdn.microsoft.com/library/windows/desktop/aa363858)  
        [CreateProcess](https://msdn.microsoft.com/library/windows/desktop/ms682425)  
        [DeleteFile](https://msdn.microsoft.com/library/windows/desktop/aa363915)  
        [FindFirstFile](https://msdn.microsoft.com/library/windows/desktop/aa364418)  
        [FindNextFile](https://msdn.microsoft.com/library/windows/desktop/aa364428)  
        [GetCurrentDirectory](https://msdn.microsoft.com/library/windows/desktop/aa364934)  
        [GetDiskFreeSpace](https://msdn.microsoft.com/library/windows/desktop/aa364935)  
        [GetDriveType](https://msdn.microsoft.com/library/windows/desktop/aa364939)  
    :::column-end:::
    :::column:::
        [GetFileAttributes](https://msdn.microsoft.com/library/windows/desktop/aa364944)  
        [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963)  
        [GetModuleFileName](https://msdn.microsoft.com/library/windows/desktop/ms683197)  
        [GetModuleHandle](https://msdn.microsoft.com/library/windows/desktop/ms683199)  
        [GetSystemDirectory](https://msdn.microsoft.com/library/windows/desktop/ms724373)  
        [GetTempFileName](https://msdn.microsoft.com/library/windows/desktop/aa364991)  
        [GetTempPath](https://msdn.microsoft.com/library/windows/desktop/aa364992)  
        [GetVolumeInformation](https://msdn.microsoft.com/library/windows/desktop/aa364993)  
        [GetWindowsDirectory](https://msdn.microsoft.com/library/windows/desktop/ms724454)  
        [LoadLibrary](https://msdn.microsoft.com/library/windows/desktop/ms684175)  
    :::column-end:::
    :::column:::
        [LoadLibraryEx](https://msdn.microsoft.com/library/windows/desktop/ms684179)  
        [MoveFile](https://msdn.microsoft.com/library/windows/desktop/aa365239)  
        [MoveFileEx](https://msdn.microsoft.com/library/windows/desktop/aa365240)  
        [OpenFile](https://msdn.microsoft.com/library/windows/desktop/aa365430)  
        [RemoveDirectory](https://msdn.microsoft.com/library/windows/desktop/aa365488)  
        [SearchPath](https://msdn.microsoft.com/library/windows/desktop/aa365527)  
        [SetCurrentDirectory](https://msdn.microsoft.com/library/windows/desktop/aa365530)  
        [SetFileAttributes](https://msdn.microsoft.com/library/windows/desktop/aa365535)  
    :::column-end:::
:::row-end:::

Cuando se trabaja con líneas de comandos, una aplicación de consola debe obtener la línea de comandos en formato Unicode y convertirla al formato de OEM, con las funciones de carácter a OEM pertinentes. Tenga en cuenta también que *argv* usa el juego de caracteres ANSI.
