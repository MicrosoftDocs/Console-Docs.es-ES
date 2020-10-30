---
title: Tamaño de búfer de ventana y pantalla
description: El tamaño de un búfer de pantalla se expresa en términos de una cuadrícula de coordenadas basada en celdas de caracteres.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_window\_and\_screen\_buffer\_size'
- base.window\_and\_screen\_buffer\_size
- consoles.window\_and\_screen\_buffer\_size
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 55246039-31eb-41ca-ad8e-d314cb508644
ms.openlocfilehash: 91fed765b76ebfb8b9dde318d8f76eff9a72d862
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037113"
---
# <a name="window-and-screen-buffer-size"></a>Tamaño de búfer de ventana y pantalla

El tamaño de un búfer de pantalla se expresa en términos de una cuadrícula de coordenadas basada en celdas de caracteres. El ancho es el número de celdas de caracteres de cada fila y el alto es el número de filas. Asociado a cada búfer de pantalla hay una ventana que determina el tamaño y la ubicación de la parte rectangular del búfer de pantalla de la consola que se muestra en la ventana de la consola. Para definir la ventana de un búfer de pantalla, se especifican las coordenadas de la celda de caracteres de las celdas superior izquierda e inferior derecha del rectángulo de la ventana.

> [!NOTE]
> En el mundo de las **[secuencias de terminal virtuales](console-virtual-terminal-sequences.md)** , el tamaño de la ventana y el tamaño del búfer de pantalla se fijan en el mismo valor. El terminal controla cualquier región desplazamiento que sea equivalente a una consola con un tamaño de búfer de pantalla mayor que el tamaño de la ventana. Ese contenido pertenece al terminal y, por lo general, ya no forma parte del área direccionable. Para obtener más información, consulte nuestra comparación entre las **[funciones de la consola clásica y las secuencias de terminal virtuales](classic-vs-vt.md)** .

Un búfer de pantalla puede tener cualquier tamaño, limitado solo por la memoria disponible. Las dimensiones de la ventana de un búfer de pantalla no pueden superar las dimensiones correspondientes del búfer de pantalla de la consola o la ventana máxima que cabe en la pantalla basándose en el tamaño de fuente actual (controlado exclusivamente por el usuario).

La función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) devuelve la siguiente información sobre un búfer de pantalla y su ventana:

- Tamaño actual del búfer de la pantalla de la consola
- Ubicación actual de la ventana
- Tamaño máximo de la ventana dado el tamaño actual del búfer de pantalla, el tamaño de fuente actual y el tamaño de la pantalla.

La función [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) devuelve el tamaño máximo de la ventana de la consola en función de la fuente y los tamaños de pantalla actuales. Este tamaño difiere del tamaño de ventana máximo devuelto por [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) en que se omite el tamaño del búfer de la pantalla de la consola.

Para cambiar el tamaño de un búfer de pantalla, utilice la función [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) . Esta función genera un error si alguna de las dimensiones del tamaño especificado es menor que la dimensión correspondiente de la ventana de la consola.

Para cambiar el tamaño o la ubicación de la ventana de un búfer de pantalla, utilice la función [**SetConsoleWindowInfo**](setconsolewindowinfo.md) . Esta función genera un error si las coordenadas de la esquina de la ventana especificada superan los límites del búfer de pantalla de la consola o de la pantalla. Cambiar el tamaño de la ventana del búfer de pantalla activo cambia el tamaño de la ventana de la consola que se muestra en la pantalla.

Un proceso puede cambiar el modo de entrada de la consola para habilitar la entrada de ventana, de modo que el proceso pueda recibir entradas cuando el usuario cambie el tamaño del búfer de la pantalla de la consola. Si una aplicación habilita la entrada de ventana, puede utilizar [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) para recuperar el tamaño del búfer de pantalla y de pantalla al iniciar. Esta información se puede usar para determinar la forma en que se muestran los datos en la ventana. Si el usuario cambia el tamaño del búfer de la pantalla de la consola, la aplicación puede responder cambiando la forma en que se muestran los datos. Por ejemplo, una aplicación puede ajustar la manera en que el texto se ajusta al final de la línea si cambia el número de caracteres por fila. Si una aplicación no habilita la entrada de ventana, debe usar los tamaños de ventana heredada y de búfer de pantalla, o bien establecerlos en el tamaño deseado durante el inicio y restaurar los tamaños heredados en la salida. Para obtener más información sobre el modo de entrada de ventana, vea [modos de consola de bajo nivel](low-level-console-modes.md).
