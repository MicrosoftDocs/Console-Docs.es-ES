---
title: 'Consolas: escritorio de Windows'
description: Una consola de es una aplicación que proporciona e/s a aplicaciones de línea de comandos.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: 7b447e3c1d6d72c58890797177f6668f5d835d35
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060777"
---
# <a name="consoles"></a>Consolas

Una *consola* (o *terminal*) es una aplicación que proporciona e/s a aplicaciones de modo de carácter. Este mecanismo independiente del procesador facilita el portabilidad de las aplicaciones en modo de carácter existentes o la creación de nuevas herramientas y aplicaciones de modo de carácter.

Una consola de está formada por un búfer de entrada y uno o más búferes de pantalla. El *búfer de entrada* contiene una cola de registros de entrada, cada uno de los cuales contiene información sobre un evento de entrada. La cola de entrada siempre incluye eventos de pulsación de teclas y de liberación de claves. También puede incluir eventos del mouse (movimientos de punteros y pulsaciones de botones y versiones) y eventos durante los que las acciones del usuario afectan al tamaño del búfer de pantalla activo. Un *búfer de pantalla* es una matriz bidimensional de datos de caracteres y colores para la salida en una ventana de la consola. Cualquier número de procesos puede compartir una consola de.

- [Creación de una consola](creation-of-a-console.md)
- [Asociar a una consola](attaching-to-a-console.md)
- [Cerrar una consola](closing-a-console.md)
- [Identificadores de consola](console-handles.md)
- [Búfer de entrada de la consola](console-input-buffer.md)
- [Búferes de pantalla de la consola](console-screen-buffers.md)
- [Tamaño de búfer de ventana y pantalla](window-and-screen-buffer-size.md)
- [Selección de la consola](console-selection.md)
- [Desplazarse por el búfer de pantalla](scrolling-the-screen-buffer.md)
