---
title: E/s de la consola de High-Level
description: Las funciones de e/s de alto nivel proporcionan una manera sencilla de leer un flujo de caracteres de la entrada de la consola o de escribir un flujo de caracteres en la salida de la consola.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_high\_level\_console\_i\_o'
- base.high\_level\_console\_i\_o
- consoles.high\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6d191fee-87bb-4659-8056-910149e591f7
ms.openlocfilehash: d240a261ea555e0bfa506c96c1aaea9d6a933697
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358700"
---
# <a name="high-level-console-io"></a>E/s de la consola de High-Level

Las funciones de e/s de alto nivel proporcionan una manera sencilla de leer un flujo de caracteres de la entrada de la consola o de escribir un flujo de caracteres en la salida de la consola. Una operación de lectura de nivel superior obtiene los caracteres de entrada del búfer de entrada de la consola y los almacena en un búfer especificado. Una operación de escritura de alto nivel toma los caracteres de un búfer especificado y los escribe en un búfer de pantalla en la ubicación actual del cursor, adelantando el cursor a medida que se escribe cada carácter.

La e/s de alto nivel le permite elegir entre las funciones [**readfile**](/windows/win32/api/fileapi/nf-fileapi-readfile) y [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) y las funciones [**ReadConsole**](readconsole.md) y [**WriteConsole**](writeconsole.md) . Son idénticos, salvo por dos diferencias importantes. Las funciones de la consola de admiten el uso de caracteres Unicode o del juego de caracteres ANSI a través de las variantes A y W de cada función. las funciones de e/s de archivo no admiten Unicode salvo para UTF-8 establecida con la `CP_UTF8` constante en las funciones **[SetConsoleCP](setconsolecp.md)** y **[SetConsoleOutputCP](setconsoleoutputcp.md)** antes de su uso. Además, las funciones de e/s de archivo se pueden usar para tener acceso a archivos, canalizaciones y dispositivos de comunicaciones serie; las funciones de consola solo se pueden usar con los identificadores de consola. Esta distinción es importante si una aplicación se basa en identificadores estándar que pueden haberse redirigido.

Al utilizar cualquier conjunto de funciones de alto nivel, una aplicación puede controlar el texto y los colores de fondo usados para mostrar los caracteres que se escriben posteriormente en un búfer de pantalla con el mecanismo preferido a través de **[secuencias de terminal virtuales](console-virtual-terminal-sequences.md)**. Una aplicación también puede usar los modos de consola que afectan a la e/s de la consola de alto nivel para habilitar o deshabilitar las siguientes propiedades:

- Eco de la entrada del teclado en el búfer de pantalla activo
- Entrada de línea, en la que una operación de lectura no vuelve hasta que se presiona la tecla entrar.
- Procesamiento automático de entradas de teclado para controlar los retornos de carro, CTRL + C y otros detalles de entrada
- Procesamiento automático de la salida para controlar el ajuste de línea, los retornos de carro, los retroceso y otros detalles de salida

Para obtener más información, vea los temas siguientes:

- [Modos de consola](console-modes.md)
- [Modos de consola de alto nivel](high-level-console-modes.md)
- [Funciones de entrada y salida de la consola de alto nivel](high-level-console-input-and-output-functions.md)
- [API clásicas frente a secuencias de terminales virtuales](classic-vs-vt.md)