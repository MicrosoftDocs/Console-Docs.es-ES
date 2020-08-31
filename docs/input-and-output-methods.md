---
title: Métodos de entrada y salida
description: Hay dos enfoques diferentes para la e/s de la consola, que depende de la flexibilidad y el control de las necesidades de la aplicación.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_input\_and\_output\_methods'
- base.input\_and\_output\_methods
- consoles.input\_and\_output\_methods
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 55a86d5d-d0b1-4d0c-b42f-7342809289ad
ms.openlocfilehash: 29f4ca8f4851c73f79d810f56b57f490995cad04
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061024"
---
# <a name="input-and-output-methods"></a><span data-ttu-id="7da13-104">Métodos de entrada y salida</span><span class="sxs-lookup"><span data-stu-id="7da13-104">Input and Output Methods</span></span>


<span data-ttu-id="7da13-105">Hay dos enfoques diferentes para la e/s de la consola, que depende de la flexibilidad y el control de las necesidades de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7da13-105">There are two different approaches to console I/O, the choice of which depends on how much flexibility and control an application needs.</span></span> <span data-ttu-id="7da13-106">El enfoque de alto nivel habilita la e/s de secuencia de caracteres simple, pero limita el acceso a los búferes de entrada y de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="7da13-106">The high-level approach enables simple character stream I/O, but it limits access to a console's input and screen buffers.</span></span> <span data-ttu-id="7da13-107">El enfoque de bajo nivel requiere que los desarrolladores escriban más código y elijan entre una gama mayor de funciones, pero también proporcionan más flexibilidad a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7da13-107">The low-level approach requires that developers write more code and choose among a greater range of functions, but it also gives an application more flexibility.</span></span>

<span data-ttu-id="7da13-108">Una aplicación puede usar las funciones de e/s de archivo, [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747), y las funciones de la consola, [**ReadConsole**](readconsole.md) y [**WriteConsole**](writeconsole.md), para la e/s de alto nivel que proporciona acceso indirecto a los búferes de entrada y de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="7da13-108">An application can use the file I/O functions, [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747), and the console functions, [**ReadConsole**](readconsole.md) and [**WriteConsole**](writeconsole.md), for high-level I/O that provides indirect access to a console's input and screen buffers.</span></span> <span data-ttu-id="7da13-109">Las funciones de entrada de alto nivel filtran y procesan los datos en el búfer de entrada de la consola para devolver la entrada como un flujo de caracteres, descartando la entrada de cambio de tamaño del mouse y del búfer.</span><span class="sxs-lookup"><span data-stu-id="7da13-109">The high-level input functions filter and process the data in a console's input buffer to return input as a stream of characters, discarding mouse and buffer-resizing input.</span></span> <span data-ttu-id="7da13-110">Del mismo modo, las funciones de salida de alto nivel escriben una secuencia de caracteres que se muestra en la ubicación actual del cursor en un búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="7da13-110">Similarly, the high-level output functions write a stream of characters that are displayed at the current cursor location in a screen buffer.</span></span> <span data-ttu-id="7da13-111">Una aplicación controla la manera en que funcionan estas funciones mediante el establecimiento de los modos de e/s de la consola.</span><span class="sxs-lookup"><span data-stu-id="7da13-111">An application controls the way these functions work by setting a console's I/O modes.</span></span>

<span data-ttu-id="7da13-112">Las funciones de e/s de bajo nivel proporcionan acceso directo a los búferes de entrada y de pantalla de una consola, lo que permite a una aplicación tener acceso a los eventos de entrada y de cambio de tamaño del búfer y a la información ampliada de los eventos de teclado.</span><span class="sxs-lookup"><span data-stu-id="7da13-112">The low-level I/O functions provide direct access to a console's input and screen buffers, enabling an application to access mouse and buffer-resizing input events and extended information for keyboard events.</span></span> <span data-ttu-id="7da13-113">Las funciones de salida de bajo nivel permiten a una aplicación leer o escribir en un número especificado de celdas de caracteres consecutivas en un búfer de pantalla, o para leer o escribir en bloques rectangulares de celdas de caracteres en una ubicación especificada de un búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="7da13-113">Low-level output functions enable an application to read from or write to a specified number of consecutive character cells in a screen buffer, or to read or write to rectangular blocks of character cells at a specified location in a screen buffer.</span></span> <span data-ttu-id="7da13-114">Los modos de entrada de una consola afectan a la entrada de bajo nivel al permitir que la aplicación determine si los eventos de cambio de tamaño del mouse y del búfer se colocan en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="7da13-114">A console's input modes affect low-level input by enabling the application to determine whether mouse and buffer-resizing events are placed in the input buffer.</span></span> <span data-ttu-id="7da13-115">Los modos de salida de una consola no tienen ningún efecto en la salida de bajo nivel.</span><span class="sxs-lookup"><span data-stu-id="7da13-115">A console's output modes have no effect on low-level output.</span></span>

<span data-ttu-id="7da13-116">Los métodos de e/s de nivel alto y bajo nivel no son mutuamente excluyentes, y una aplicación puede usar cualquier combinación de estas funciones.</span><span class="sxs-lookup"><span data-stu-id="7da13-116">The high-level and low-level I/O methods are not mutually exclusive, and an application can use any combination of these functions.</span></span> <span data-ttu-id="7da13-117">Sin embargo, normalmente, una aplicación usa un enfoque o el otro exclusivamente.</span><span class="sxs-lookup"><span data-stu-id="7da13-117">Typically, however, an application uses one approach or the other exclusively.</span></span>

<span data-ttu-id="7da13-118">En los temas siguientes se describen los modos de consola y las funciones de e/s de alto nivel y de bajo nivel.</span><span class="sxs-lookup"><span data-stu-id="7da13-118">The following topics describe the console modes and the high-level and low-level I/O functions.</span></span>

- [<span data-ttu-id="7da13-119">Modos de consola</span><span class="sxs-lookup"><span data-stu-id="7da13-119">Console Modes</span></span>](console-modes.md)
- [<span data-ttu-id="7da13-120">E/s de consola de alto nivel</span><span class="sxs-lookup"><span data-stu-id="7da13-120">High-Level Console I/O</span></span>](high-level-console-i-o.md)
- [<span data-ttu-id="7da13-121">Modos de consola de alto nivel</span><span class="sxs-lookup"><span data-stu-id="7da13-121">High-Level Console Modes</span></span>](high-level-console-modes.md)
- [<span data-ttu-id="7da13-122">Funciones de entrada y salida de la consola de alto nivel</span><span class="sxs-lookup"><span data-stu-id="7da13-122">High-Level Console Input and Output Functions</span></span>](high-level-console-input-and-output-functions.md)
- [<span data-ttu-id="7da13-123">E/s de consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="7da13-123">Low-Level Console I/O</span></span>](low-level-console-i-o.md)
- [<span data-ttu-id="7da13-124">Modos de consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="7da13-124">Low-Level Console Modes</span></span>](low-level-console-modes.md)
- [<span data-ttu-id="7da13-125">Funciones de entrada de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="7da13-125">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)
- [<span data-ttu-id="7da13-126">Funciones de salida de la consola de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="7da13-126">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

 

 




