---
title: E/s de la consola de Low-Level
description: Las funciones de e/s de la consola de bajo nivel expanden el control de una aplicación a través de e/s de consola, habilitando el acceso directo a los búferes de entrada y de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_low\_level\_console\_i\_o'
- base.low\_level\_console\_i\_o
- consoles.low\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c874aff4-6129-4dbc-8949-24d46382d81c
ms.openlocfilehash: b4ec834e44f7ff291466cfe1714442bc17ca7aca
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039553"
---
# <a name="low-level-console-io"></a>E/s de la consola de Low-Level

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Las funciones de e/s de la consola de bajo nivel expanden el control de una aplicación a través de e/s de consola, habilitando el acceso directo a los búferes de entrada y de pantalla de la consola. Estas funciones permiten a una aplicación realizar las tareas siguientes:

- Recibir entradas sobre eventos de cambio de tamaño del mouse y del búfer
- Recibir información extendida sobre los eventos de entrada de teclado
- Escribir registros de entrada en el búfer de entrada
- Leer registros de entrada sin quitarlos del búfer de entrada
- Determinar el número de eventos pendientes en el búfer de entrada
- Vaciar el búfer de entrada
- Leer y escribir cadenas de caracteres Unicode o ANSI en una ubicación especificada en un búfer de pantalla
- Leer y escribir cadenas de texto y atributos de color de fondo en una ubicación de búfer de pantalla especificada
- Leer y escribir bloques rectangulares de datos de caracteres y colores en una ubicación de búfer de pantalla especificada
- Escribe un solo carácter Unicode o ANSI, o una combinación de atributos de texto y de color de fondo, en un número especificado de celdas consecutivas que comienzan en una ubicación de búfer de pantalla especificada

Para obtener más información, consulte los temas siguientes:

- [Modos de consola](console-modes.md)
- [Modos de consola de bajo nivel](low-level-console-modes.md)
- [Funciones de entrada de la consola de bajo nivel](low-level-console-input-functions.md)
- [Funciones de salida de la consola de bajo nivel](low-level-console-output-functions.md)
