---
title: 'Pseudoconsoles: escritorio de Windows'
description: Un pseudoconsole es un concepto que se usa para proporcionar el aspecto de hospedaje o servicio de una aplicación en modo de carácter.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola, conpty, pseudoconsole
ms.openlocfilehash: 2b2d28065ec4f0e4121decb906e76b34ac1871fc
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039483"
---
# <a name="pseudoconsoles"></a>Pseudoconsoles

Un *pseudoconsole* es un tipo de dispositivo que permite que las aplicaciones se conviertan en el host para las aplicaciones en modo de carácter.

Esto contrasta con una sesión de consola típica en la que el sistema operativo creará una ventana de hospedaje en nombre de la aplicación de modo de carácter para controlar la salida gráfica y los datos proporcionados por el usuario.

Con un pseudoconsole, no se crea la ventana de hospedaje. La aplicación que realiza el pseudoconsole debe ser responsable de mostrar la salida gráfica y recopilar los datos proporcionados por el usuario. Como alternativa, la información se puede retransmitir más a otra aplicación responsable de estas actividades en un punto posterior de la cadena.

Esta funcionalidad está diseñada para que las aplicaciones de "ventana de terminal" de terceros existan en la plataforma o para el redireccionamiento de las actividades de modo de carácter a una sesión de "ventana de terminal" remota en otra máquina o incluso en otra plataforma.

Tenga en cuenta que la sesión de la consola subyacente todavía se creará en nombre de la aplicación que solicita el pseudoconsole. Todas las reglas de las [sesiones de consola](consoles.md) se siguen aplicando, lo que incluye la posibilidad de que varias aplicaciones de modo de caracteres de cliente se conecten a la sesión.

Para proporcionar la máxima compatibilidad con el mundo existente de la funcionalidad de pseudoterminal, la información proporcionada a través del canal de pseudoconsole siempre se codificará en UTF-8. Esto no afecta a la página de códigos o la codificación de las aplicaciones cliente que están conectadas. La traducción se producirá dentro del sistema pseudoconsole según sea necesario.

Puede encontrar un ejemplo de introducción en creación de [una sesión de Pseudoconsole](creating-a-pseudoconsole-session.md).

Puede encontrar información general adicional sobre pseudoconsoles en la entrada de blog del anuncio: [línea de comandos de Windows: Introducción a la pseudo consola de Windows (ConPTY)](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).
