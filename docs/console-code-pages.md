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
# <a name="console-code-pages"></a>Páginas de códigos de la consola


Una *Página de códigos* es una asignación de códigos de caracteres 256 a caracteres individuales. Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas.

Los asociados a cada consola son dos páginas de códigos: una para la entrada y otra para la salida. Una consola usa su página de códigos de entrada para traducir la entrada del teclado en el valor de carácter correspondiente. Usa la página de códigos de salida para traducir los valores de caracteres escritos por las distintas funciones de salida en las imágenes que se muestran en la ventana de la consola. Una aplicación puede usar las funciones [**SetConsoleCP**](setconsolecp.md) y [**GetConsoleCP**](getconsolecp.md) para establecer y recuperar las páginas de códigos de entrada de una consola y las funciones [**SetConsoleOutputCP**](setconsoleoutputcp.md) y [**GetConsoleOutputCP**](getconsoleoutputcp.md) para establecer y recuperar sus páginas de códigos de salida.

Los identificadores de las páginas de códigos disponibles en el equipo local se almacenan en el registro con la siguiente clave.

**HKEY \_ local \_ Machine \\ System \\ CurrentControlSet \\ control de la página de \\ \\ códigos NLS**

Para obtener información sobre el uso de las funciones del registro para determinar las páginas de códigos disponibles, vea [**Registry**](https://msdn.microsoft.com/library/windows/desktop/ms724871).

 

 




