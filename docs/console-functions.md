---
title: Funciones de la consola
description: Describe una lista completa de todas las funciones que se usan para tener acceso a una consola de.
author: miniksa
ms.author: miniksa
ms.topic: hub-page
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_functions'
- base.console\_functions
- consoles.console\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2a0e5dcc-be48-42ab-a05a-96f68d012a67
ms.openlocfilehash: 0ee2dde2c14a3d827aa2bc5e14f3cc65cf5fdc0f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039243"
---
# <a name="console-functions"></a>Funciones de la consola

Las siguientes funciones se usan para tener acceso a una consola de.

| Función | Descripción |
|-|-|
| [**AddConsoleAlias**](addconsolealias.md) | Define un alias de consola para el ejecutable especificado. |
| [**AllocConsole**](allocconsole.md) | Asigna una nueva consola para el proceso de llamada. |
| [**AttachConsole**](attachconsole.md) | Asocia el proceso de llamada a la consola del proceso especificado. |
| [**ClosePseudoConsole**](closepseudoconsole.md) | Cierra un pseudoconsole del identificador dado. |
| [**ClosePseudoConsole**](createpseudoconsole.md) | Asigna un nuevo pseudoconsole para el proceso de llamada. |
| [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) | Crea un búfer de pantalla de la consola. |
| [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) | Establece los atributos de color de fondo y de texto para un número especificado de celdas de caracteres. |
| [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md) | Escribe un carácter en el búfer de la pantalla de la consola un número especificado de veces. |
| [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) | Vacía el búfer de entrada de la consola. |
| [**FreeConsole**](freeconsole.md) | Desasocia el proceso de llamada de su consola. |
| [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) | Envía una señal especificada a un grupo de procesos de consola que comparte la consola asociada al proceso de llamada. |
| [**GetConsoleAlias**](getconsolealias.md) | Recupera el alias especificado para el ejecutable especificado. |
| [**GetConsoleAliases**](getconsolealiases.md) | Recupera todos los alias de consola definidos para el ejecutable especificado. |
| [**GetConsoleAliasesLength**](getconsolealiaseslength.md) | Devuelve el tamaño, en bytes, del búfer necesario para almacenar todos los alias de la consola del archivo ejecutable especificado. |
| [**GetConsoleAliasExes**](getconsolealiasexes.md) | Recupera los nombres de todos los ejecutables con alias de consola definidos. |
| [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) | Devuelve el tamaño, en bytes, del búfer necesario para almacenar los nombres de todos los ejecutables que tienen definidos alias de consola. |
| [**GetConsoleCP**](getconsolecp.md) | Recupera la página de códigos de entrada utilizada por la consola asociada al proceso de llamada. |
| [**GetConsoleCursorInfo**](getconsolecursorinfo.md) | Recupera información sobre el tamaño y la visibilidad del cursor para el búfer de pantalla de la consola especificado. |
| [**GetConsoleDisplayMode**](getconsoledisplaymode.md) | Recupera el modo de presentación de la consola actual. |
| [**GetConsoleFontSize**](getconsolefontsize.md) | Recupera el tamaño de la fuente utilizada por el búfer de pantalla de la consola especificado. |
| [**GetConsoleHistoryInfo**](getconsolehistoryinfo.md) | Recupera la configuración del historial de la consola del proceso que realiza la llamada. |
| [**GetConsoleMode**](getconsolemode.md) | Recupera el modo de entrada actual del búfer de entrada de una consola o el modo de salida actual de un búfer de pantalla de la consola. |
| [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) | Recupera el título original de la ventana de la consola actual. |
| [**GetConsoleOutputCP**](getconsoleoutputcp.md) | Recupera la página de códigos de salida utilizada por la consola asociada al proceso de llamada. |
| [**GetConsoleProcessList**](getconsoleprocesslist.md) | Recupera una lista de los procesos adjuntos a la consola actual. |
| [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) | Recupera información sobre el búfer de pantalla de la consola especificado. |
| [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) | Recupera información extendida sobre el búfer de pantalla de la consola especificado. |
| [**GetConsoleSelectionInfo**](getconsoleselectioninfo.md) | Recupera información sobre la selección de la consola actual. |
| [**GetConsoleTitle**](getconsoletitle.md) | Recupera el título de la ventana de la consola actual. |
| [**GetConsoleWindow**](getconsolewindow.md) | Recupera el identificador de ventana que usa la consola asociada al proceso de llamada. |
| [**GetCurrentConsoleFont**](getcurrentconsolefont.md) | Recupera información sobre la fuente de consola actual. |
| [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) | Recupera información extendida sobre la fuente de consola actual. |
| [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) | Recupera el tamaño de la ventana de la consola más grande posible. |
| [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) | Recupera el número de registros de entrada no leídos en el búfer de entrada de la consola. |
| [**GetNumberOfConsoleMouseButtons**](getnumberofconsolemousebuttons.md) | Recupera el número de botones del mouse que usa la consola actual. |
| [**GetStdHandle**](getstdhandle.md) | Recupera un identificador para la entrada estándar, la salida estándar o el dispositivo de error estándar. |
| [**HandlerRoutine**](handlerroutine.md) | Una función definida por la aplicación que se usa con la función [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) . |
| [**PeekConsoleInput**](peekconsoleinput.md) | Lee datos del búfer de entrada de la consola especificado sin quitarlo del búfer. |
| [**ReadConsole**](readconsole.md) | Lee la entrada de caracteres del búfer de entrada de la consola y lo quita del búfer. |
| [**PeekConsoleInput**](readconsoleinput.md) | Lee datos de un búfer de entrada de la consola y lo quita del búfer. |
| [**ReadConsoleOutput**](readconsoleoutput.md) | Lee los datos de atributos de caracteres y colores de un bloque rectangular de celdas de caracteres en un búfer de pantalla de la consola. |
| [**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md) | Copia un número especificado de atributos de color de primer plano y de fondo de las celdas consecutivas de un búfer de pantalla de la consola. |
| [**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md) | Copia un número de caracteres de las celdas consecutivas de un búfer de pantalla de la consola. |
| [**ResizePseudoConsole**](resizepseudoconsole.md) | Cambia el tamaño de los búferes internos de un pseudoconsole al tamaño especificado. |
| [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) | Mueve un bloque de datos en un búfer de pantalla. |
| [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) | Establece el búfer de pantalla especificado para que sea el búfer de pantalla de la consola que se muestra actualmente. |
| [**SetConsoleCP**](setconsolecp.md) | Establece la página de códigos de entrada utilizada por la consola asociada al proceso de llamada. |
| [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) | Agrega o quita un [**HandlerRoutine**](handlerroutine.md) definido por la aplicación de la lista de funciones de controlador para el proceso que realiza la llamada. |
| [**SetConsoleCursorInfo**](setconsolecursorinfo.md) | Establece el tamaño y la visibilidad del cursor para el búfer de pantalla de la consola especificado. |
| [**SetConsoleCursorPosition**](setconsolecursorposition.md) | Establece la posición del cursor en el búfer de pantalla especificado. |
| [**SetConsoleDisplayMode**](setconsoledisplaymode.md) | Establece el modo de presentación del búfer de pantalla de la consola especificado. |
| [**SetConsoleHistoryInfo**](setconsolehistoryinfo.md) | Establece la configuración del historial de la consola del proceso que realiza la llamada. |
| [**SetConsoleMode**](setconsolemode.md) | Establece el modo de entrada del búfer de entrada de una consola o el modo de salida de un búfer de pantalla de la consola. |
| [**SetConsoleOutputCP**](setconsoleoutputcp.md) | Establece la página de códigos de salida utilizada por la consola asociada al proceso de llamada. |
| [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) | Establece la información extendida sobre el búfer de pantalla especificado. |
| [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) | Cambia el tamaño del búfer de pantalla de la consola especificado. |
| [**SetConsoleTextAttribute**](setconsoletextattribute.md) | Establece los atributos de primer plano (texto) y color de fondo de los caracteres escritos en el búfer de pantalla de la consola. |
| [**SetConsoleTitle**](setconsoletitle.md) | Establece el título de la ventana de la consola actual. |
| [**SetConsoleWindowInfo**](setconsolewindowinfo.md) | Establece el tamaño y la posición actuales de la ventana de un búfer de pantalla de la consola. |
| [**SetCurrentConsoleFontEx**](setcurrentconsolefontex.md) | Establece la información extendida sobre la fuente de consola actual. |
| [**SetStdHandle**](setstdhandle.md) | Establece el identificador de la entrada estándar, la salida estándar o el dispositivo de error estándar. |
| [**WriteConsole**](writeconsole.md) | Escribe una cadena de caracteres en un búfer de pantalla de la consola a partir de la ubicación actual del cursor. |
| [**WriteConsoleInput**](writeconsoleinput.md) | Escribe los datos directamente en el búfer de entrada de la consola. |
| [**WriteConsoleOutput**](writeconsoleoutput.md) | Escribe datos de atributos de caracteres y colores en un bloque rectangular especificado de celdas de caracteres en un búfer de pantalla de la consola. |
| [**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md) | Copia varios atributos de color de primer plano y de fondo en celdas consecutivas de un búfer de pantalla de la consola. |
| [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md) | Copia un número de caracteres en las celdas consecutivas de un búfer de pantalla de la consola. |
