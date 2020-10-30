---
title: Acerca de las consolas
description: Las consolas proporcionan compatibilidad de alto nivel para las aplicaciones de modo de carácter simple que interactúan con el usuario mediante el uso de funciones que leen la entrada estándar y escriben en la salida estándar o en un error estándar.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: e20fa54434b4121abd3f77ee530945bf9aa590f2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037533"
---
# <a name="about-character-mode-applications"></a>Acerca de las aplicaciones de modo de carácter

Modo de carácter (o "línea de comandos"):

1. \[Opcionalmente, \] leer datos de la entrada estándar (stdin)
2. "Trabajar"
3. \[Opcionalmente, puede \] escribir datos en la salida estándar (stdout) o en un error estándar (stderr).

Las aplicaciones en modo de carácter se comunican con el usuario final a través de una aplicación de "consola" (o "terminal"). Una consola de convierte los datos proporcionados por el usuario desde el teclado, el mouse, la pantalla táctil, el lápiz, etc., y lo envía a la stdin de una aplicación en modo de carácter. Una consola también puede mostrar la salida de texto de una aplicación en modo de carácter en la pantalla del usuario.

En Windows, la consola está integrada y proporciona una API enriquecida a través de la cual las aplicaciones en modo de carácter pueden interactuar con el usuario. Sin embargo, en la era reciente, el equipo de la consola está fomentando el desarrollo de todas las aplicaciones en modo de carácter con [secuencias de terminal virtuales](console-virtual-terminal-sequences.md) a través de las llamadas de API clásicas para ofrecer compatibilidad máxima entre Windows y otros sistemas operativos. Puede encontrar más información sobre esta transición y las ventajas y desventajas en nuestro debate sobre las [API clásicas frente a las secuencias de terminales virtuales](classic-vs-vt.md).

- [Consolas](consoles.md)
- [Métodos de entrada y salida](input-and-output-methods.md)
- [Páginas de código de la consola](console-code-pages.md)
- [Identificadores de control de la consola](console-control-handlers.md)
- [Alias de la consola](console-aliases.md)
- [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md)
- [Problemas de la aplicación de consola](console-application-issues.md)
