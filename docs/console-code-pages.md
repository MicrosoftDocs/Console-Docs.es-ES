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
ms.openlocfilehash: 931e882306c1aaff521b7b78c2b99cf1a5479da1
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039253"
---
# <a name="console-code-pages"></a>Páginas de código de la consola

Una *Página de códigos* es una asignación de códigos de caracteres 256 a caracteres individuales. Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas.

Los asociados a cada consola son dos páginas de códigos: una para la entrada y otra para la salida. Una consola usa su página de códigos de entrada para traducir la entrada del teclado en el valor de carácter correspondiente. Usa la página de códigos de salida para traducir los valores de caracteres escritos por las distintas funciones de salida en las imágenes que se muestran en la ventana de la consola. Una aplicación puede usar las funciones [**SetConsoleCP**](setconsolecp.md) y [**GetConsoleCP**](getconsolecp.md) para establecer y recuperar las páginas de códigos de entrada de una consola y las funciones [**SetConsoleOutputCP**](setconsoleoutputcp.md) y [**GetConsoleOutputCP**](getconsoleoutputcp.md) para establecer y recuperar sus páginas de códigos de salida.

Los identificadores de las páginas de códigos disponibles en el equipo local se almacenan en el registro con la siguiente clave: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

Para obtener información sobre el uso de las funciones del registro para determinar las páginas de códigos disponibles, vea [**Registry**](https://msdn.microsoft.com/library/windows/desktop/ms724871).

> [!TIP]
> Se recomienda para todas las aplicaciones de línea de comandos nuevas y actualizadas para evitar páginas de códigos y usar **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** . El texto con formato UTF-16 se puede enviar a la familia *W* de API de consola. El texto con formato UTF-8 se puede enviar a *una* familia de API de consola después de asegurarse de que la página de códigos se establece primero en **[65001 (CP_UTF8)](https://docs.microsoft.com/windows/win32/intl/code-page-identifiers)** con las funciones [**SetConsoleCP**](setconsolecp.md) y [**SetConsoleOutputCP**](setconsoleoutputcp.md) .
