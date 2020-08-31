---
title: Acerca de las consolas
description: Las consolas proporcionan compatibilidad de alto nivel para las aplicaciones de modo de carácter simple que interactúan con el usuario mediante el uso de funciones que leen la entrada estándar y escriben en la salida estándar o en un error estándar.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: 0a738c72ec45a68817fae6dbfa9d6b3e45beb53e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060929"
---
# <a name="about-character-mode-applications"></a>Acerca de las aplicaciones en modo de carácter

Modo de carácter (o "línea de comandos"):

1. Opcionalmente Leer datos de la entrada estándar (stdin)
2. "Trabajar"
3. Opcionalmente Escribir datos en la salida estándar (stdout) o en el error estándar (stderr)

Las aplicaciones en modo de carácter se comunican con el usuario final a través de una aplicación de "consola" (o "terminal"). Una consola de convierte los datos proporcionados por el usuario desde el teclado, el mouse, la pantalla táctil, el lápiz, etc., y lo envía a la stdin de una aplicación en modo de carácter. Una consola también puede mostrar la salida de texto de una aplicación en modo de carácter en la pantalla del usuario.

En Windows, la consola está integrada y proporciona una API enriquecida a través de la cual las aplicaciones en modo de carácter pueden interactuar con el usuario.

- [Consolas](consoles.md)
- [Métodos de entrada y salida](input-and-output-methods.md)
- [Páginas de códigos de la consola](console-code-pages.md)
- [Controladores de control de consola](console-control-handlers.md)
- [Alias de la consola](console-aliases.md)
- [Seguridad y derechos de acceso de búfer de la consola](console-buffer-security-and-access-rights.md)
- [Problemas de la aplicación de consola](console-application-issues.md)

 

 




