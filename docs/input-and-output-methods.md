---
title: Métodos de entrada y salida
description: Hay dos enfoques diferentes para la e/s de la consola, que depende de la flexibilidad y el control de las necesidades de la aplicación.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_input\_and\_output\_methods'
- base.input\_and\_output\_methods
- consoles.input\_and\_output\_methods
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 55a86d5d-d0b1-4d0c-b42f-7342809289ad
ms.openlocfilehash: 8ad03cc2be8cce2c174ac4a72f700cbb31b7fd94
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039563"
---
# <a name="input-and-output-methods"></a>Métodos de entrada y salida

Hay dos enfoques diferentes para la e/s de la consola, que depende de la flexibilidad y el control de las necesidades de la aplicación. El enfoque de alto nivel habilita la e/s de secuencia de caracteres simple, pero limita el acceso a los búferes de entrada y de pantalla de la consola. El enfoque de bajo nivel requiere que los desarrolladores escriban más código y elijan entre una gama mayor de funciones, pero también proporcionan más flexibilidad a la aplicación.

> [!NOTE]
> No se recomienda el enfoque de bajo nivel para el desarrollo nuevo y en curso. Se recomienda que las aplicaciones que necesitan la funcionalidad de las funciones de e/s de la consola de bajo nivel usen **[secuencias de terminal virtuales](console-virtual-terminal-sequences.md)** y exploren la documentación sobre **[las funciones clásicas en comparación con el terminal virtual](classic-vs-vt.md)** y **[la guía del ecosistema](ecosystem-roadmap.md)** .

Una aplicación puede usar las funciones de e/s de archivo, [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747), y las funciones de la consola, [**ReadConsole**](readconsole.md) y [**WriteConsole**](writeconsole.md), para la e/s de alto nivel que proporciona acceso indirecto a los búferes de entrada y de pantalla de la consola. Las funciones de entrada de alto nivel filtran y procesan los datos en el búfer de entrada de la consola para devolver la entrada como un flujo de caracteres, descartando la entrada de cambio de tamaño del mouse y del búfer. Del mismo modo, las funciones de salida de alto nivel escriben una secuencia de caracteres que se muestra en la ubicación actual del cursor en un búfer de pantalla. Una aplicación controla la manera en que funcionan estas funciones mediante el establecimiento de los modos de e/s de la consola.

Las funciones de e/s de bajo nivel proporcionan acceso directo a los búferes de entrada y de pantalla de una consola, lo que permite a una aplicación tener acceso a los eventos de entrada y de cambio de tamaño del búfer y a la información ampliada de los eventos de teclado. Las funciones de salida de bajo nivel permiten a una aplicación leer o escribir en un número especificado de celdas de caracteres consecutivas en un búfer de pantalla, o para leer o escribir en bloques rectangulares de celdas de caracteres en una ubicación especificada de un búfer de pantalla. Los modos de entrada de una consola afectan a la entrada de bajo nivel al permitir que la aplicación determine si los eventos de cambio de tamaño del mouse y del búfer se colocan en el búfer de entrada. Los modos de salida de una consola no tienen ningún efecto en la salida de bajo nivel.

Los métodos de e/s de nivel alto y bajo nivel no son mutuamente excluyentes, y una aplicación puede usar cualquier combinación de estas funciones. Sin embargo, normalmente, una aplicación usa un enfoque o el otro exclusivamente y se recomienda centrarse en un paradigma determinado para obtener unos resultados óptimos.

> [!TIP]
> La aplicación de búsqueda directa ideal se centrará en los métodos de alto nivel y aumentará las necesidades adicionales con las **[secuencias de terminal virtuales](console-virtual-terminal-sequences.md)** a través de los métodos de e/s de alto nivel cuando sea necesario evitando el uso completo de las funciones de e/s de bajo nivel.

En los temas siguientes se describen los modos de consola y las funciones de e/s de alto nivel y de bajo nivel.

- [Modos de consola](console-modes.md)
- [E/s de consola de alto nivel](high-level-console-i-o.md)
- [Modos de consola de alto nivel](high-level-console-modes.md)
- [Funciones de entrada y salida de la consola de alto nivel](high-level-console-input-and-output-functions.md)
- [Secuencias de terminal virtuales de la consola](console-virtual-terminal-sequences.md)
- [Funciones clásicas frente a secuencias de terminales virtuales](classic-vs-vt.md)
- [Guía del ecosistema](ecosystem-roadmap.md)
- [E/s de consola de bajo nivel](low-level-console-i-o.md)
- [Modos de consola de bajo nivel](low-level-console-modes.md)
- [Funciones de entrada de la consola de bajo nivel](low-level-console-input-functions.md)
- [Funciones de salida de la consola de bajo nivel](low-level-console-output-functions.md)
