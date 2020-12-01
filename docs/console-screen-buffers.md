---
title: Búferes de pantalla de la consola
description: Un búfer de pantalla es una matriz bidimensional de datos de caracteres y colores para la salida en una ventana de la consola.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_screen\_buffers'
- base.console\_screen\_buffers
- consoles.console\_screen\_buffers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f94995fc-5f5f-4fcd-969d-7e10020634c2
ms.localizationpriority: high
ms.openlocfilehash: 4c5740be3b60d54f9e7b586b41e962a4102222a0
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420204"
---
# <a name="console-screen-buffers"></a>Búferes de pantalla de la consola

Un *búfer de pantalla* es una matriz bidimensional de datos de caracteres y colores para la salida en una ventana de la consola. Una consola puede tener varios búferes de pantalla. El *búfer de pantalla activo* es el que se muestra en la pantalla.

El sistema crea un búfer de pantalla cada vez que crea una nueva consola. Para abrir un identificador en el búfer de pantalla activo de la consola, especifique el valor **CONOUT $** en una llamada a la función [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) . Un proceso puede usar la función [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) para crear búferes de pantalla adicionales para su consola. Un nuevo búfer de pantalla no está activo hasta que su identificador se especifica en una llamada a la función [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) . Sin embargo, se puede tener acceso a los búferes de pantalla para leer y escribir si están activos o inactivos.

Cada búfer de pantalla tiene su propia matriz bidimensional de registros de información de caracteres. Los datos de cada carácter se almacenan en una estructura [**Char \_ info**](char-info-str.md) que especifica el carácter Unicode o ANSI, y los colores de primer plano y de fondo en los que se muestra ese carácter.

Una serie de propiedades asociadas a un búfer de pantalla se puede establecer de forma independiente para cada búfer de pantalla. Esto significa que cambiar el búfer de pantalla activo puede tener un efecto drástico en la apariencia de la ventana de la consola. Las propiedades asociadas a un búfer de pantalla incluyen:

- Tamaño del búfer de pantalla, en filas y columnas de caracteres.
- Atributos de texto (colores de primer plano y de fondo para mostrar el texto que va a escribir la función [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md) ).
- Tamaño y ubicación de la ventana (la región rectangular del búfer de pantalla de la consola que se muestra en la ventana de la consola).
- Posición del cursor, apariencia y visibilidad.
- Modos de salida (**Habilitar la \_ \_ salida procesada** y **habilitar \_ Wrap en la \_ \_ \_ salida de EOL**). Para obtener más información sobre los modos de salida de la consola, consulte [modos de consola de alto nivel](high-level-console-modes.md).

Cuando se crea un búfer de pantalla, contiene caracteres de espacio en todas las posiciones. Su cursor está visible y colocado en el origen del búfer (0,0) y la ventana se coloca con su esquina superior izquierda en el origen del búfer. El tamaño del búfer de pantalla de la consola, el tamaño de la ventana, los atributos de texto y la apariencia del cursor vienen determinados por el usuario o por los valores predeterminados del sistema. Para recuperar los valores actuales de las distintas propiedades asociadas al búfer de pantalla de la consola, use las funciones [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md), [**GetConsoleCursorInfo**](getconsolecursorinfo.md)y [**GetConsoleMode**](getconsolemode.md) .

Las aplicaciones que cambian cualquiera de las propiedades del búfer de pantalla de la consola deben crear su propio búfer de pantalla o guardar el estado del búfer de pantalla heredado durante el inicio y restaurarlo al salir. Este comportamiento cooperativo es necesario para garantizar que las demás aplicaciones que comparten la misma sesión de consola no se vean afectadas por los cambios.

> [!TIP]
> Se recomienda usar el modo de [**búfer alternativo**](console-virtual-terminal-sequences.md#alternate-screen-buffer) en adelante, si es posible, en lugar de crear un segundo búfer de pantalla para este fin. El **modo de búfer alternativo** ofrece mayor compatibilidad entre dispositivos remotos y otras plataformas. Para obtener más información, consulte la explicación sobre las [**API de consola clásica frente a terminal virtual**](classic-vs-vt.md) .

## <a name="cursor-appearance-and-position"></a>Apariencia y posición del cursor

El cursor de un búfer de pantalla puede estar visible u oculto. Cuando está visible, su apariencia puede variar, desde llenar completamente una celda de caracteres hasta que aparezca como una línea horizontal en la parte inferior de la celda. Para recuperar información sobre la apariencia y visibilidad del cursor, utilice la función [**GetConsoleCursorInfo**](getconsolecursorinfo.md) . Esta función notifica si el cursor está visible y describe la apariencia del cursor como el porcentaje de la celda de un carácter que se rellena. Para establecer la apariencia y visibilidad del cursor, utilice la función [**SetConsoleCursorInfo**](setconsolecursorinfo.md) .

Los caracteres escritos por las [funciones de e/s de la consola de alto nivel](high-level-console-i-o.md) se escriben en la ubicación actual del cursor, pasando el cursor a la siguiente ubicación. Para determinar la posición actual del cursor en el sistema de coordenadas de un búfer de pantalla, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md). Puede usar [**SetConsoleCursorPosition**](setconsolecursorposition.md) para establecer la posición del cursor y, por lo tanto, controlar la posición del texto escrito o devuelto por las funciones de e/s de alto nivel. Si mueve el cursor, se sobrescribe el texto en la nueva ubicación del cursor.

> [!NOTE]
> No se recomienda el uso de las funciones de bajo nivel para buscar la posición del cursor. Se recomienda usar secuencias de [terminal virtuales](console-virtual-terminal-sequences.md) para consultar esta posición si es necesario para los diseños avanzados. Puede encontrar más información sobre la preferencia de secuencias de terminal virtuales en el documento **[funciones clásicas frente a terminal virtual](classic-vs-vt.md)** .

La posición, la apariencia y la visibilidad del cursor se establecen de forma independiente para cada búfer de pantalla.

## <a name="character-attributes"></a>Atributos de caracteres

Los atributos de caracteres se pueden dividir en dos clases: color y DBCS. Los atributos siguientes se definen en el `WinCon.h` archivo de encabezado.

| Atributo | Significado |
|-|-|
| **azul de primer plano \_** | El color del texto contiene el azul. |
| **verde de primer plano \_** | El color del texto contiene verde. |
| **rojo de primer plano \_** | El color del texto contiene rojo. |
| **intensidad de primer plano \_** | El color del texto se intensifica. |
| **azul de fondo \_** | El color de fondo contiene el azul. |
| **verde de fondo \_** | El color de fondo contiene verde. |
| **rojo de fondo \_** | El color de fondo contiene rojo. |
| **intensidad de fondo \_** | Se intensifica el color de fondo. |
| **\_ \_ byte inicial de LVB común \_** | Byte inicial. |
| **\_ \_ byte final de LVB \_ común** | Byte final. |
| **\_ \_ cuadrícula horizontal común \_ LVB** | Horizontal superior. |
| **\_LVB de \_ cuadrícula común \_ LVERTICAL** | Vertical izquierda. |
| **\_LVB de \_ cuadrícula común \_ RVERTICAL** | Vertical derecha. |
| **\_ \_ vídeo inverso de LVB común \_** | Atributos de primer plano y de fondo inversos. |
| **\_carácter de \_ subrayado LVB común** | Subrayado. |

Los atributos de primer plano especifican el color del texto. Los atributos de fondo especifican el color utilizado para rellenar el fondo de la celda. Los demás atributos se utilizan con [DBCS](https://msdn.microsoft.com/library/windows/desktop/dd317794).

Una aplicación puede combinar las constantes de primer plano y de fondo para lograr distintos colores. Por ejemplo, la combinación siguiente produce texto aguamarina brillante sobre un fondo azul.

`FOREGROUND_BLUE | FOREGROUND_GREEN | FOREGROUND_INTENSITY | BACKGROUND_BLUE`

Si no se especifica ninguna constante de fondo, el fondo es negro y, si no se especifica ninguna constante de primer plano, el texto es negro. Por ejemplo, la combinación siguiente produce texto en negro sobre un fondo blanco.

`BACKGROUND_BLUE | BACKGROUND_GREEN | BACKGROUND_RED`

Cada celda de carácter de búfer de pantalla almacena los atributos de color de los colores utilizados en el dibujo del primer plano (texto) y el fondo de esa celda. Una aplicación puede establecer los datos de color para cada celda de carácter individualmente, almacenando los datos en el miembro **attributes** de la estructura [**Char \_ info**](char-info-str.md) de cada celda. Los atributos de texto actuales de cada búfer de pantalla se utilizan para los caracteres que posteriormente se escriben o se repiten por las funciones de alto nivel.

Una aplicación puede utilizar [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) para determinar los atributos de texto actuales de un búfer de pantalla y la función [**SetConsoleTextAttribute**](setconsoletextattribute.md) para establecer los atributos de caracteres. El cambio de los atributos de un búfer de pantalla no afecta a la presentación de caracteres escritos previamente. Estos atributos de texto no afectan a los caracteres escritos por las funciones de e/s de la consola de bajo nivel (como la función [**WriteConsoleOutput**](writeconsoleoutput.md) o [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md) ), que especifican explícitamente los atributos de cada celda que se escriben o dejan los atributos sin modificar.

> [!NOTE]
> No se recomienda el uso de las funciones de bajo nivel para manipular atributos de texto predeterminados y específicos. Se recomienda usar secuencias de [terminal virtuales](console-virtual-terminal-sequences.md) para establecer atributos de texto. Puede encontrar más información sobre la preferencia de secuencias de terminal virtuales en el documento **[funciones clásicas frente a terminal virtual](classic-vs-vt.md)** .

## <a name="font-attributes"></a>Atributos de fuente

La función [**GetCurrentConsoleFont**](getcurrentconsolefont.md) recupera información sobre la fuente de consola actual. La información almacenada en la estructura de [**\_ \_ información**](console-font-info-str.md) de la fuente de la consola incluye el ancho y el alto de cada carácter de la fuente.

La función [**GetConsoleFontSize**](getconsolefontsize.md) recupera el tamaño de la fuente utilizada por el búfer de pantalla de la consola especificado.

> [!NOTE]
> No se recomienda el uso de funciones para buscar y manipular la información de fuentes. Se recomienda que las aplicaciones de línea de comandos funcionen de una manera neutra para garantizar la compatibilidad entre plataformas, así como la compatibilidad con entornos de host que permiten al usuario personalizar la fuente. Más información sobre las preferencias de usuario y los entornos de host, incluidos los terminales, consulte la **[Guía del ecosistema](ecosystem-roadmap.md)**.
