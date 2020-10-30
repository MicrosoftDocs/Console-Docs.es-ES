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
# <a name="low-level-console-io"></a><span data-ttu-id="15c03-104">E/s de la consola de Low-Level</span><span class="sxs-lookup"><span data-stu-id="15c03-104">Low-Level Console I/O</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="15c03-105">Las funciones de e/s de la consola de bajo nivel expanden el control de una aplicación a través de e/s de consola, habilitando el acceso directo a los búferes de entrada y de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="15c03-105">The low-level console I/O functions expand an application's control over console I/O by enabling direct access to a console's input and screen buffers.</span></span> <span data-ttu-id="15c03-106">Estas funciones permiten a una aplicación realizar las tareas siguientes:</span><span class="sxs-lookup"><span data-stu-id="15c03-106">These functions enable an application to perform the following tasks:</span></span>

- <span data-ttu-id="15c03-107">Recibir entradas sobre eventos de cambio de tamaño del mouse y del búfer</span><span class="sxs-lookup"><span data-stu-id="15c03-107">Receive input about mouse and buffer-resizing events</span></span>
- <span data-ttu-id="15c03-108">Recibir información extendida sobre los eventos de entrada de teclado</span><span class="sxs-lookup"><span data-stu-id="15c03-108">Receive extended information about keyboard input events</span></span>
- <span data-ttu-id="15c03-109">Escribir registros de entrada en el búfer de entrada</span><span class="sxs-lookup"><span data-stu-id="15c03-109">Write input records to the input buffer</span></span>
- <span data-ttu-id="15c03-110">Leer registros de entrada sin quitarlos del búfer de entrada</span><span class="sxs-lookup"><span data-stu-id="15c03-110">Read input records without removing them from the input buffer</span></span>
- <span data-ttu-id="15c03-111">Determinar el número de eventos pendientes en el búfer de entrada</span><span class="sxs-lookup"><span data-stu-id="15c03-111">Determine the number of pending events in the input buffer</span></span>
- <span data-ttu-id="15c03-112">Vaciar el búfer de entrada</span><span class="sxs-lookup"><span data-stu-id="15c03-112">Flush the input buffer</span></span>
- <span data-ttu-id="15c03-113">Leer y escribir cadenas de caracteres Unicode o ANSI en una ubicación especificada en un búfer de pantalla</span><span class="sxs-lookup"><span data-stu-id="15c03-113">Read and write strings of Unicode or ANSI characters at a specified location in a screen buffer</span></span>
- <span data-ttu-id="15c03-114">Leer y escribir cadenas de texto y atributos de color de fondo en una ubicación de búfer de pantalla especificada</span><span class="sxs-lookup"><span data-stu-id="15c03-114">Read and write strings of text and background color attributes at a specified screen buffer location</span></span>
- <span data-ttu-id="15c03-115">Leer y escribir bloques rectangulares de datos de caracteres y colores en una ubicación de búfer de pantalla especificada</span><span class="sxs-lookup"><span data-stu-id="15c03-115">Read and write rectangular blocks of character and color data at a specified screen buffer location</span></span>
- <span data-ttu-id="15c03-116">Escribe un solo carácter Unicode o ANSI, o una combinación de atributos de texto y de color de fondo, en un número especificado de celdas consecutivas que comienzan en una ubicación de búfer de pantalla especificada</span><span class="sxs-lookup"><span data-stu-id="15c03-116">Write a single Unicode or ANSI character, or a text and background color attribute combination, to a specified number of consecutive cells beginning at a specified screen buffer location</span></span>

<span data-ttu-id="15c03-117">Para obtener más información, consulte los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="15c03-117">For more information, see the following topics:</span></span>

- [<span data-ttu-id="15c03-118">Modos de consola</span><span class="sxs-lookup"><span data-stu-id="15c03-118">Console Modes</span></span>](console-modes.md)
- [<span data-ttu-id="15c03-119">Modos de consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="15c03-119">Low-Level Console Modes</span></span>](low-level-console-modes.md)
- [<span data-ttu-id="15c03-120">Funciones de entrada de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="15c03-120">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)
- [<span data-ttu-id="15c03-121">Funciones de salida de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="15c03-121">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)
