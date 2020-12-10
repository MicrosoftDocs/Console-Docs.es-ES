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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420204"
---
# <a name="console-screen-buffers"></a>Búferes de pantalla de la consola

Un *búfer de pantalla* es una matriz bidimensional de datos de caracteres y colores para la salida en una ventana de la consola. Una consola puede tener varios búferes de pantalla. El *búfer de pantalla activo* es el que se muestra en la pantalla.

El sistema crea un búfer de pantalla cada vez que crea una nueva consola. Para abrir un identificador en el búfer de pantalla activo de la consola, especifique el valor **CONOUT$** en una llamada a la función [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858). Un proceso puede usar la función [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) para crear búferes de pantalla adicionales para su consola. Un búfer de pantalla nuevo no está activo hasta que su identificador se especifica en una llamada a la función [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md). Sin embargo, se puede tener acceso a los búferes de pantalla para leer y escribir, independientemente de si están activos o inactivos.

Cada búfer de pantalla tiene su propia matriz bidimensional de registros de información de caracteres. Los datos de cada carácter se almacenan en una estructura [**CHAR\_INFO**](char-info-str.md) que especifica el carácter Unicode o ANSI, y los colores de primer plano y de fondo en los que se muestra ese carácter.

Se puede establecer una serie de propiedades asociadas a un búfer de pantalla, de forma independiente para cada búfer de pantalla. Esto significa que cambiar el búfer de pantalla activo puede tener un efecto drástico en la apariencia de la ventana de la consola. Las propiedades asociadas a un búfer de pantalla incluyen:

- Tamaño del búfer de pantalla, en filas y columnas de caracteres.
- Atributos de texto (colores de primer plano y de fondo para mostrar el texto que las funciones [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md) van a escribir).
- Tamaño y ubicación de la ventana (la región rectangular del búfer de pantalla de la consola que se muestra en la ventana de la consola).
- Posición del cursor, apariencia y visibilidad.
- Modos de salida (**ENABLE\_PROCESSED\_OUTPUT** y **ENABLE\_WRAP\_AT\_EOL\_OUTPUT**). Para más información sobre los modos de salida de la consola, consulte [Modos de consola de nivel superior](high-level-console-modes.md).

Cuando se crea un búfer de pantalla, contiene caracteres de espacio en todas las posiciones. Su cursor está visible y colocado en el origen del búfer (0,0) y la ventana se coloca con su esquina superior izquierda en el origen del búfer. El tamaño del búfer de pantalla de la consola, el tamaño de la ventana, los atributos de texto y la apariencia del cursor vienen determinados por el usuario o por los valores predeterminados del sistema. Para recuperar los valores actuales de las distintas propiedades asociadas al búfer de pantalla de la consola, use las funciones [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md), [**GetConsoleCursorInfo**](getconsolecursorinfo.md) y [**GetConsoleMode**](getconsolemode.md).

Las aplicaciones que cambian cualquiera de las propiedades del búfer de pantalla de la consola deben crear su propio búfer de pantalla o guardar el estado del búfer de pantalla heredado durante el inicio y restaurarlo al salir. Este comportamiento cooperativo es necesario para garantizar que las demás aplicaciones que comparten la misma sesión de consola no se vean afectadas por los cambios.

> [!TIP]
> Se recomienda usar el [**modo de búfer alternativo**](console-virtual-terminal-sequences.md#alternate-screen-buffer) en adelante, si es posible, en lugar de crear un segundo búfer de pantalla para este fin. El **modo de búfer alternativo** ofrece mayor compatibilidad entre dispositivos remotos y con otras plataformas. Consulte la explicación sobre las [**API de consola clásica frente a la terminal virtual**](classic-vs-vt.md) para obtener más información.

## <a name="cursor-appearance-and-position"></a>Apariencia y posición del cursor

El cursor de un búfer de pantalla puede estar visible u oculto. Cuando está visible, su apariencia puede variar, desde llenar completamente una celda de carácter hasta que aparezca como una línea horizontal en la parte inferior de la celda. Para recuperar información sobre la apariencia y visibilidad del cursor, utilice la función [**GetConsoleCursorInfo**](getconsolecursorinfo.md). Esta función notifica si el cursor está visible y describe la apariencia del cursor como el porcentaje que rellena de una celda de carácter. Para establecer la apariencia y visibilidad del cursor, utilice la función [**GetConsoleCursorInfo**](setconsolecursorinfo.md).

Los caracteres escritos por las [funciones de E/S de consola de nivel superior](high-level-console-i-o.md) se escriben en la ubicación actual del cursor y el cursor avanza a la siguiente ubicación. Para determinar la posición actual del cursor en el sistema de coordenadas de un búfer de pantalla, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md). Puede usar [**SetConsoleCursorPosition**](setconsolecursorposition.md) para establecer la posición del cursor y, por lo tanto, controlar la selección de ubicación del texto escrito o repetido por las funciones de E/S de nivel superior. Si mueve el cursor, se sobrescribe el texto en la nueva ubicación del cursor.

> [!NOTE]
> No se recomienda el uso de las funciones de nivel inferior para buscar la posición del cursor. Se recomienda usar [secuencias de terminal virtual](console-virtual-terminal-sequences.md) para consultar esta posición si es necesario para los diseños avanzados. Puede encontrar más información sobre la preferencia de secuencias de terminal virtual en el documento sobre **[funciones clásicas frente a terminal virtual](classic-vs-vt.md)** .

La posición, la apariencia y la visibilidad del cursor se establecen de forma independiente para cada búfer de pantalla.

## <a name="character-attributes"></a>Atributos de caracteres

Los atributos de caracteres se pueden dividir en dos clases: color y DBCS. Los siguientes atributos se definen en el archivo de encabezado `WinCon.h`.

| Atributo | Significado |
|-|-|
| **FOREGROUND\_BLUE** | El color del texto contiene azul. |
| **FOREGROUND\_GREEN** | El color del texto contiene verde. |
| **FOREGROUND\_RED** | El color del texto contiene rojo. |
| **FOREGROUND\_INTENSITY** | El color del texto se intensifica. |
| **BACKGROUND\_BLUE** | El color de fondo contiene azul. |
| **BACKGROUND\_GREEN** | El color de fondo contiene verde. |
| **BACKGROUND\_RED** | El color de fondo contiene rojo. |
| **BACKGROUND\_INTENSITY** | El color de fondo se intensifica. |
| **COMMON\_LVB\_LEADING\_BYTE** | Byte inicial. |
| **COMMON\_LVB\_TRAILING\_BYTE** | Byte final. |
| **COMMON\_LVB\_GRID\_HORIZONTAL** | Horizontal superior. |
| **COMMON\_LVB\_GRID\_LVERTICAL** | Vertical izquierda. |
| **COMMON\_LVB\_GRID\_RVERTICAL** | Vertical derecha. |
| **COMMON\_LVB\_REVERSE\_VIDEO** | Invierte atributos de primer plano y de fondo. |
| **COMMON\_LVB\_UNDERSCORE** | Guion bajo. |

Los atributos de primer plano especifican el color de texto. Los atributos de fondo especifican el color utilizado para rellenar el fondo de la celda. Los demás atributos se usan con [DBCS](https://msdn.microsoft.com/library/windows/desktop/dd317794).

Una aplicación puede combinar las constantes de primer plano y de fondo para lograr distintos colores. Por ejemplo, la combinación siguiente produce texto cian brillante sobre un fondo azul.

`FOREGROUND_BLUE | FOREGROUND_GREEN | FOREGROUND_INTENSITY | BACKGROUND_BLUE`

Si no se especifica ninguna constante de fondo, este es negro y, si no se especifica ninguna constante de primer plano, el texto es negro. Por ejemplo, la combinación siguiente produce texto en negro sobre un fondo blanco.

`BACKGROUND_BLUE | BACKGROUND_GREEN | BACKGROUND_RED`

Cada celda de carácter de búfer de pantalla almacena los atributos de color de los colores utilizados en el dibujo del primer plano (texto) y el fondo de esa celda. Una aplicación puede establecer los datos de color para cada celda de caracteres individualmente, almacenando los datos en los miembros **Atributos** de la estructura [**CHAR\_INFO**](char-info-str.md) de cada celda. Los atributos de texto actuales de cada búfer de pantalla se utilizan para los caracteres que posteriormente se escriben o se repiten por las funciones de nivel superior.

Una aplicación puede usar [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) para determinar los atributos de texto actuales de un búfer de pantalla y la función [**SetConsoleTextAttribute**](setconsoletextattribute.md) para establecer los atributos de caracteres. El cambio de los atributos de un búfer de pantalla no afecta a la visualización de los caracteres escritos previamente. Estos atributos de texto no afectan a los caracteres escritos por las funciones de E/S de la consola de nivel inferior (por ejemplo, las funciones [**WriteConsoleOutput**](writeconsoleoutput.md) o [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)), que especifican explícitamente los atributos para cada celda que se escribe o dejan los atributos sin modificar.

> [!NOTE]
> No se recomienda el uso de las funciones de nivel inferior para manipular atributos de texto predeterminados y específicos. Se recomienda usar [secuencias de terminal virtual](console-virtual-terminal-sequences.md) para establecer atributos de texto. Puede encontrar más información sobre la preferencia de secuencias de terminal virtual en el documento sobre **[funciones clásicas frente a terminal virtual](classic-vs-vt.md)** .

## <a name="font-attributes"></a>Atributos de fuente

La función [**GetCurrentConsoleFont**](getcurrentconsolefont.md) recupera información sobre la fuente de consola actual. La información almacenada en la estructura [**CONSOLE\_FONT\_INFO**](console-font-info-str.md) incluye el ancho y el alto de cada carácter de la fuente.

La función [**GetConsoleFontSize**](getconsolefontsize.md) recupera el tamaño de la fuente utilizada por el búfer de pantalla de la consola especificado.

> [!NOTE]
> No se recomienda el uso de funciones para buscar y manipular la información de fuentes. Se recomienda utilizar las aplicaciones de línea de comandos en manera de fuente neutra para garantizar la compatibilidad entre plataformas, así como la compatibilidad con entornos de host que permiten al usuario personalizar la fuente. Para más información sobre las preferencias del usuario y los entornos de host, incluidos los terminales, consulte el **[mapa de ruta del ecosistema](ecosystem-roadmap.md)** .
