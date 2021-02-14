---
title: Desplazarse por el búfer de pantalla
description: Describe cómo la ventana de la consola muestra una parte del búfer de pantalla activo.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_scrolling\_the\_screen\_buffer'
- base.scrolling\_the\_screen\_buffer
- consoles.scrolling\_the\_screen\_buffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c8404e78-9807-4bed-bc12-25377fa96151
ms.openlocfilehash: 4c55a40f43827deeacfd1302d507732ec9bcc248
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358665"
---
# <a name="scrolling-the-screen-buffer"></a>Desplazarse por el búfer de pantalla

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

La ventana de la consola muestra una parte del búfer de pantalla activo. Cada búfer de pantalla mantiene su propio rectángulo de ventana actual que especifica las coordenadas de las celdas del carácter superior izquierda e inferior derecha que se mostrarán en la ventana de la consola. Para determinar el rectángulo de ventana actual de un búfer de pantalla, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md). Cuando se crea un búfer de pantalla, la esquina superior izquierda de su ventana se encuentra en la esquina superior izquierda del búfer de pantalla de la consola en (0,0).

El rectángulo de la ventana puede cambiar para mostrar diferentes partes del búfer de pantalla de la consola. El rectángulo de ventana de un búfer de pantalla puede cambiar en las siguientes situaciones:

- Cuando se llama a [**SetConsoleWindowInfo**](setconsolewindowinfo.md) para especificar un nuevo rectángulo de ventana, desplaza la vista del búfer de pantalla de la consola cambiando la posición del rectángulo de la ventana sin cambiar el tamaño de la ventana. Para obtener ejemplos de Cómo desplazarse por el contenido de la ventana, vea [desplazarse por la ventana de un búfer de pantalla](scrolling-a-screen-buffer-s-window.md).

  ![movimiento panorámico de la ventana del búfer de pantalla alrededor del búfer grande](images/cscon-01.png)

- Cuando se usa la función [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) para escribir en un búfer de pantalla con Wrap en el modo de salida de final de línea (EOL) habilitado, el rectángulo de la ventana se desplaza automáticamente, por lo que siempre se muestra el cursor.
- Cuando la función [**SetConsoleCursorPosition**](setconsolecursorposition.md) especifica una nueva posición del cursor que está fuera de los límites del rectángulo de la ventana actual, el rectángulo de la ventana se desplaza automáticamente para mostrar el cursor.
- Cuando el usuario cambia el tamaño de la ventana de la consola o usa las barras de desplazamiento de la ventana, puede cambiar el rectángulo de la ventana del búfer de pantalla activo. Este cambio no se registra como un evento de cambio de tamaño de ventana en el búfer de entrada.

En cada una de estas situaciones, el rectángulo de la ventana se desplaza para mostrar una parte diferente del búfer de pantalla de la consola, pero el contenido del búfer de pantalla de la consola permanece en la misma posición. Las siguientes situaciones pueden hacer que el contenido del búfer de la pantalla de la consola cambie:

- Cuando se llama a la función [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) , se copia un bloque rectangular de una parte de un búfer de pantalla en otro.
- Cuando se usa [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) para escribir en un búfer de pantalla con Wrap en el modo de salida EOL habilitado, el contenido del búfer de pantalla de la consola se desplaza automáticamente cuando se encuentra el final del búfer de pantalla de la consola. Este desplazamiento descarta la fila superior del búfer de pantalla de la consola.

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) especifica el rectángulo del búfer de pantalla de la consola que se mueve y las nuevas coordenadas de la esquina superior izquierda en la que se copia el rectángulo. Esta función puede desplazar una parte o todo el contenido del búfer de pantalla de la consola.

En la ilustración se muestra una operación [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) que desplaza todo el contenido del búfer de la pantalla de la consola en varias filas. Se descartan los contenidos de las primeras filas y las filas inferiores se rellenan con el carácter y el color especificados.

![desplazar el contenido de la ventana del búfer de pantalla hacia arriba para descartar](images/cscon-02.png)

Los efectos de [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) se pueden limitar especificando un rectángulo de recorte opcional para que el contenido del búfer de pantalla de la consola fuera del rectángulo de recorte no se modifique. El efecto del recorte es crear una subventana (el rectángulo de recorte) cuyo contenido se desplaza sin afectar al resto del búfer de la pantalla de la consola. Para obtener un ejemplo en el que se usa **ScrollConsoleScreenBuffer**, vea [desplazarse por el contenido de un búfer de pantalla](scrolling-a-screen-buffer-s-contents.md).