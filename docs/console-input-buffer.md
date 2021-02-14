---
title: Búfer de entrada de la consola
description: Cada consola tiene un búfer de entrada que contiene una cola de registros de eventos de entrada.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_input\_buffer'
- base.console\_input\_buffer
- consoles.console\_input\_buffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6e536658-8a27-478e-82ee-d1e11f351301
ms.openlocfilehash: d5d3604d3d4f2738af01ae1bc051c10af6249c62
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358116"
---
# <a name="console-input-buffer"></a>Búfer de entrada de la consola

Cada consola tiene un búfer de entrada que contiene una cola de registros de eventos de entrada. Cuando la ventana de la consola tiene el foco de teclado, una consola da formato a cada evento de entrada (por ejemplo, una sola pulsación de tecla, un movimiento del mouse o un clic del botón del mouse) como un registro de entrada que coloca en el búfer de entrada de la consola.

Las aplicaciones pueden acceder indirectamente a un búfer de entrada de la consola mediante las [funciones de e/s de la consola de alto nivel](high-level-console-input-and-output-functions.md), o directamente mediante las funciones de entrada de la [consola de bajo nivel](low-level-console-input-functions.md). Las funciones de entrada de alto nivel filtran y procesan los datos en el búfer de entrada, devolviendo solo una secuencia de caracteres de entrada. Las funciones de entrada de nivel inferior permiten a las aplicaciones leer registros de entrada directamente desde el búfer de entrada de una consola o colocar registros de entrada en el búfer de entrada. Para abrir un identificador de un búfer de entrada de la consola, especifique el valor de **CONIN $** en una llamada a la función [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) .

Un registro de entrada es una estructura que contiene información sobre el tipo de evento que se ha producido (teclado, Mouse, cambio de tamaño de ventana, foco o evento de menú), así como detalles específicos sobre el evento. El miembro **EventType** en una estructura de [**\_ registro de entrada**](input-record-str.md) indica qué tipo de evento se incluye en el registro.

Los eventos de foco y de menú se colocan en el búfer de entrada de la consola para uso interno del sistema y las aplicaciones deben omitirlos.

## <a name="keyboard-events"></a>Eventos de teclado

Los eventos de teclado se generan cuando se presiona o se suelta una tecla. Esto incluye las teclas de control. Sin embargo, la tecla ALT tiene un significado especial para el sistema cuando se presiona y se suelta sin combinarse con otro carácter y no se pasa a la aplicación. Además, la combinación de teclas CTRL + C no se pasa si el identificador de entrada está en modo procesado.

Si el evento de entrada es una pulsación de tecla, el miembro de **evento** del [**\_ registro de entrada**](input-record-str.md) es una estructura de [**\_ \_ registro de eventos clave**](key-event-record-str.md) que contiene la información siguiente:

- Valor booleano que indica si se presionó o se liberó la tecla.
- Un recuento de repetición que puede ser mayor que uno cuando se mantiene presionada una tecla.
- El código de la clave virtual, que identifica la clave especificada de forma independiente del dispositivo.
- Código de análisis virtual, que indica el valor dependiente del dispositivo generado por el hardware del teclado.
- ™ Unicode traducido o carácter ANSI.
- Una variable de marca que indica el estado de las teclas de control (las teclas ALT, CTRL, Mayús, BLOQ NUM, Bloq Despl y Bloq Mayús) e indica si se presionó una tecla mejorada. Las claves mejoradas para los teclados de IBM® 101-Key y 102-Key son las teclas INS, SUPR, Inicio, fin, Re Pág, Av Pág y flecha en los clústeres a la izquierda del teclado numérico y la división (/) y escriba las teclas en el teclado numérico.

## <a name="mouse-events"></a>Eventos del mouse

Los eventos del mouse se generan cada vez que el usuario mueve el mouse o presiona o suelta uno de los botones del mouse. Los eventos del mouse se colocan en el búfer de entrada solo si se cumplen las condiciones siguientes:

- El modo de entrada de la consola se establece para **Habilitar la \_ \_ entrada del mouse** (el modo predeterminado).
- La ventana de la consola tiene el foco de teclado.
- El puntero del mouse está dentro de los bordes de la ventana de la consola.

Si el evento de entrada es un evento del mouse, el miembro del **evento** en el [**\_ registro de entrada**](input-record-str.md) es una estructura de [**\_ \_ registro de eventos del mouse**](mouse-event-record-str.md) que contiene la información siguiente:

- Coordenadas del puntero del mouse en términos de la fila y columna de la celda de caracteres en el sistema de coordenadas del búfer de pantalla de la consola.
- Una variable de marca que indica el estado de los botones del mouse.
- Una variable de marca que indica el estado de las teclas de control (ALT, CTRL, Mayús, BLOQ NUM, Bloq Despl y Bloq Mayús) e indica si se presionó una tecla mejorada. Las claves mejoradas para los teclados IBM 101-Key y 102-Key son las teclas INS, SUPR, Inicio, fin, Re Pág, Av Pág y flecha en los clústeres a la izquierda del teclado numérico y la división (/) y escriba las teclas en el teclado numérico.
- Una variable de marca que indica si el evento era un evento normal de presionar un botón o un botón de liberación, un evento de movimiento del mouse o el segundo clic de un evento de doble clic.

> [!NOTE]
>Las coordenadas de la posición del mouse están en términos del búfer de pantalla de la consola, no de la ventana de la consola. El búfer de pantalla puede haberse desplazado con respecto a la ventana, por lo que la esquina superior izquierda de la ventana no es necesariamente la coordenada (0,0) del búfer de pantalla de la consola. Para determinar las coordenadas del mouse en relación con el sistema de coordenadas de la ventana, reste las coordenadas de origen de la ventana de las coordenadas de posición del mouse. Utilice la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) para determinar las coordenadas de origen de la ventana.

El miembro **dwButtonState** de la estructura del [**\_ \_ registro de eventos del mouse**](mouse-event-record-str.md) tiene un bit que corresponde a cada botón del mouse. El bit es 1 si el botón está presionado y 0 si el botón está activo. Un evento de versión de botón se detecta mediante un valor 0 para el miembro **dwEventFlags** del **\_ \_ registro de eventos del mouse** y un cambio en el bit de un botón de 1 a 0. La función [**GetNumberOfConsoleMouseButtons**](getnumberofconsolemousebuttons.md) recupera el número de botones del mouse.

## <a name="buffer-resizing-events"></a>Eventos de Buffer-Resizing

El menú de la ventana de la consola permite al usuario cambiar el tamaño del búfer de pantalla activo. Este cambio genera un evento de cambio de tamaño del búfer. Los eventos de cambio de tamaño de búfer se colocan en el búfer de entrada si el modo de entrada de la consola está establecido para **Habilitar la \_ \_ entrada de ventana** (es decir, el modo predeterminado está deshabilitado).

Si el evento de entrada es un evento de cambio de tamaño de búfer, el miembro de **evento** del [**\_ registro de entrada**](input-record-str.md) es una estructura de [**\_ \_ \_ registro de tamaño de búfer de ventana**](window-buffer-size-record-str.md) que contiene el nuevo tamaño del búfer de pantalla de la consola, expresado en columnas y filas de celda de caracteres.

Si el usuario reduce el tamaño del búfer de pantalla de la consola, se perderán todos los datos de la parte descartada del búfer.

Los cambios en el tamaño del búfer de la pantalla de la consola como resultado de las llamadas a la función [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) no se generan como eventos de cambio de tamaño del búfer.