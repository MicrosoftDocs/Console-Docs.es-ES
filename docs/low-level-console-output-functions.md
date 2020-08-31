---
title: Funciones de salida de la consola de bajo nivel
description: Las funciones de salida de la consola de bajo nivel proporcionan acceso directo a las celdas de carácter de un búfer de pantalla.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_low\_level\_console\_output\_functions'
- base.low\_level\_console\_output\_functions
- consoles.low\_level\_console\_output\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 94185428-e8c7-4926-93ec-867b8c97b4ca
ms.openlocfilehash: 16441e318e7c0eed2de1125a2f7613cb4a105d44
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060616"
---
# <a name="low-level-console-output-functions"></a>Funciones de salida de la consola de bajo nivel


Las funciones de salida de la consola de bajo nivel proporcionan acceso directo a las celdas de carácter de un búfer de pantalla. Un conjunto de funciones lee o escribe en celdas consecutivas que comienzan en cualquier ubicación en el búfer de pantalla de la consola. Otro conjunto de funciones lee o escribe en bloques de celdas rectangulares.

Las siguientes funciones leen o escriben en un número especificado de celdas de caracteres consecutivas en un búfer de pantalla, comenzando por una celda especificada.


| Función                                                           | Descripción                                                                                                             |
|--------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| [**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)   | Copia una cadena de caracteres Unicode o ANSI de un búfer de pantalla.                                                     |
| [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md) | Escribe una cadena de caracteres Unicode o ANSI en un búfer de pantalla.                                                       |
| [**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)   | Copia una cadena de atributos de color de texto y de fondo de un búfer de pantalla.                                           |
| [**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md) | Escribe una cadena de atributos de texto y de color de fondo en un búfer de pantalla.                                             |
| [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)   | Escribe un único carácter Unicode o ANSI en un número especificado de celdas consecutivas en un búfer de pantalla.                |
| [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)   | Escribe una combinación de atributo de texto y de color de fondo en un número especificado de celdas consecutivas en un búfer de pantalla. |


Para todas estas funciones, cuando se encuentra la última celda de una fila, la lectura o escritura se ajusta a la primera celda de la fila siguiente. Cuando se encuentra el final de la última fila del búfer de pantalla de la consola, las funciones de escritura descartan todos los caracteres o atributos no escritos y las funciones de lectura informan del número de caracteres o atributos escritos realmente.

Las siguientes funciones leen o escriben en bloques rectangulares de celdas de caracteres en una ubicación especificada de un búfer de pantalla.


| Función                                         | Descripción                                                                                                               |
|--------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| [**ReadConsoleOutput**](readconsoleoutput.md)   | Copia los datos de caracteres y colores de un bloque especificado de celdas de búfer de pantalla en un bloque determinado en un búfer de destino. |
| [**WriteConsoleOutput**](writeconsoleoutput.md) | Escribe los datos de caracteres y colores en un bloque especificado de celdas de búfer de pantalla de un bloque determinado en un búfer de origen.        |



Estas funciones tratan los búferes de pantalla y los búferes de origen o de destino como matrices bidimensionales de estructuras de [** \_ información de char**](char-info-str.md) (que contienen datos de atributos de caracteres y colores para cada celda). Las funciones especifican el ancho y el alto, en las celdas de carácter, del búfer de origen o de destino, y el puntero al búfer se trata como un puntero a la celda de origen (0,0) de la matriz bidimensional. Las funciones usan una [**pequeña estructura \_ Rect**](small-rect-str.md) para especificar a qué rectángulo tener acceso en el búfer de pantalla de la consola, y las coordenadas de la celda superior izquierda en el búfer de origen o de destino determinan la ubicación del rectángulo correspondiente en ese búfer.

Estas funciones recortan automáticamente el rectángulo del búfer de pantalla especificado para ajustarse a los límites del búfer de pantalla de la consola. Por ejemplo, si el rectángulo especifica coordenadas inferiores a la derecha (columna 100, fila 50) y el búfer de pantalla de la consola tiene solo 80 columnas de ancho, las coordenadas se recortan de modo que sean (columna 79, fila 50). De forma similar, este rectángulo ajustado se vuelve a recortar para ajustarse a los límites del búfer de origen o de destino. Se especifican las coordenadas del búfer de pantalla del rectángulo real en el que se leyó o en el que se escribió. Para obtener un ejemplo en el que se usan estas funciones, vea [lectura y escritura de bloques de caracteres y atributos](reading-and-writing-blocks-of-characters-and-attributes.md).

En la ilustración se muestra una operación [**ReadConsoleOutput**](readconsoleoutput.md) en la que el recorte se produce cuando el bloque se lee desde el búfer de pantalla de la consola y de nuevo cuando el bloque se copia en el búfer de destino. La función informa del rectángulo de búfer de pantalla real del que copió.

![ventana de búfer de pantalla con búfer de destino](images/cscon-03.png)








