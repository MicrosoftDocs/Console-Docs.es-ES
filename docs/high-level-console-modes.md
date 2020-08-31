---
title: Modos de consola de alto nivel
description: El comportamiento de las funciones de la consola de alto nivel se ve afectado por los modos de entrada y salida de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_high\_level\_console\_modes'
- base.high\_level\_console\_modes
- consoles.high\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3ec915eb-333d-484d-a14d-46377b503ecc
ms.openlocfilehash: b5b24056a1283d46cbfe21737bd930318042c039
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060620"
---
# <a name="high-level-console-modes"></a><span data-ttu-id="f5cfd-104">Modos de consola de alto nivel</span><span class="sxs-lookup"><span data-stu-id="f5cfd-104">High-Level Console Modes</span></span>


<span data-ttu-id="f5cfd-105">El comportamiento de las funciones de la consola de alto nivel se ve afectado por los modos de entrada y salida de la consola.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-105">The behavior of the high-level console functions is affected by the console input and output modes.</span></span> <span data-ttu-id="f5cfd-106">Todos los siguientes modos de entrada de la consola están habilitados para el búfer de entrada de la consola cuando se crea una consola:</span><span class="sxs-lookup"><span data-stu-id="f5cfd-106">All of the following console input modes are enabled for a console's input buffer when a console is created:</span></span>

- <span data-ttu-id="f5cfd-107">Modo de entrada de línea</span><span class="sxs-lookup"><span data-stu-id="f5cfd-107">Line input mode</span></span>
- <span data-ttu-id="f5cfd-108">Modo de entrada procesado</span><span class="sxs-lookup"><span data-stu-id="f5cfd-108">Processed input mode</span></span>
- <span data-ttu-id="f5cfd-109">Modo de entrada de eco</span><span class="sxs-lookup"><span data-stu-id="f5cfd-109">Echo input mode</span></span>

<span data-ttu-id="f5cfd-110">Los dos modos de salida de la consola siguientes están habilitados para un búfer de pantalla de la consola cuando se crea:</span><span class="sxs-lookup"><span data-stu-id="f5cfd-110">Both of the following console output modes are enabled for a console screen buffer when it is created:</span></span>

- <span data-ttu-id="f5cfd-111">Modo de salida procesado</span><span class="sxs-lookup"><span data-stu-id="f5cfd-111">Processed output mode</span></span>
- <span data-ttu-id="f5cfd-112">Encapsulado en modo de salida EOL</span><span class="sxs-lookup"><span data-stu-id="f5cfd-112">Wrapping at EOL output mode</span></span>

<span data-ttu-id="f5cfd-113">Los tres modos de entrada, junto con el modo de salida procesado, están diseñados para funcionar juntos.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-113">All three input modes, along with processed output mode, are designed to work together.</span></span> <span data-ttu-id="f5cfd-114">Es mejor habilitar o deshabilitar todos estos modos como un grupo.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-114">It is best to either enable or disable all of these modes as a group.</span></span> <span data-ttu-id="f5cfd-115">Cuando todos están habilitados, se dice que la aplicación está en modo "cocido", lo que significa que la mayor parte del procesamiento se controla para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-115">When all are enabled, the application is said to be in "cooked" mode, which means that most of the processing is handled for the application.</span></span> <span data-ttu-id="f5cfd-116">Cuando se deshabilitan todos, la aplicación está en modo "sin procesar", lo que significa que la entrada no se filtra y se deja cualquier procesamiento en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-116">When all are disabled, the application is in "raw" mode, which means that input is unfiltered and any processing is left to the application.</span></span>

<span data-ttu-id="f5cfd-117">Una aplicación puede usar la función [**GetConsoleMode**](getconsolemode.md) para determinar el modo actual del búfer de entrada o el búfer de pantalla de una consola.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-117">An application can use the [**GetConsoleMode**](getconsolemode.md) function to determine the current mode of a console's input buffer or screen buffer.</span></span> <span data-ttu-id="f5cfd-118">Puede habilitar o deshabilitar cualquiera de estos modos con los siguientes valores en la función [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="f5cfd-118">You can enable or disable any of these modes by using the following values in the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="f5cfd-119">Tenga en cuenta que al establecer el modo de salida de un búfer de pantalla no se ve afectado el modo de salida de otros búferes de pantalla.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-119">Note that setting the output mode of one screen buffer does not affect the output mode of other screen buffers.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="f5cfd-120">Mode</span><span class="sxs-lookup"><span data-stu-id="f5cfd-120">Mode</span></span></th>
<th><span data-ttu-id="f5cfd-121">Descripción</span><span class="sxs-lookup"><span data-stu-id="f5cfd-121">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="f5cfd-122"><strong>ENABLE_PROCESSED_INPUT</strong></span><span class="sxs-lookup"><span data-stu-id="f5cfd-122"><strong>ENABLE_PROCESSED_INPUT</strong></span></span></td>
<td><span data-ttu-id="f5cfd-123">Se usa con un identificador de entrada de consola para hacer que el sistema procese cualquier entrada de tecla de control o de edición del sistema en lugar de devolverla como entrada en la operación de lectura&#39;búfer s.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-123">Used with a console input handle to cause the system to process any system editing or control key input rather than returning it as input in the read operation&#39;s buffer.</span></span> <span data-ttu-id="f5cfd-124">Si la entrada de línea también está habilitada, los retroceso y los retornos de carro se controlan correctamente.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-124">If line input is also enabled, backspaces and carriage returns are handled correctly.</span></span> <span data-ttu-id="f5cfd-125">Un retroceso hace que el cursor se desplace un espacio sin que afecte al carácter situado en la posición del cursor.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-125">A backspace causes the cursor to move back one space without affecting the character at the cursor position.</span></span> <span data-ttu-id="f5cfd-126">Un retorno de carro se convierte en combinación de caracteres de retorno de carro y avance de línea.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-126">A carriage return is converted to carriage return – line feed character combination.</span></span> <span data-ttu-id="f5cfd-127">Si el modo de entrada de eco está habilitado y la salida debe reflejar la edición del sistema, la salida procesada debe estar habilitada para el búfer de pantalla activo.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-127">If echo input mode is enabled and the output should reflect system editing, processed output must be enabled for the active screen buffer.</span></span> <span data-ttu-id="f5cfd-128">Si está habilitada la entrada procesada, la combinación de teclas CTRL + C se pasa al controlador adecuado independientemente de si está habilitada la entrada de línea.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-128">If processed input is enabled, the CTRL+C key combination is passed on to the appropriate handler regardless of whether line input is enabled.</span></span> <span data-ttu-id="f5cfd-129">Para obtener más información sobre los controladores de control, vea <a href="console-control-handlers.md" data-raw-source="[Console Control Handlers](console-control-handlers.md)">controladores de control de consola</a>.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-129">For more information about control handlers, see <a href="console-control-handlers.md" data-raw-source="[Console Control Handlers](console-control-handlers.md)">Console Control Handlers</a>.</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="f5cfd-130"><strong>ENABLE_LINE_INPUT</strong></span><span class="sxs-lookup"><span data-stu-id="f5cfd-130"><strong>ENABLE_LINE_INPUT</strong></span></span></td>
<td><span data-ttu-id="f5cfd-131">Se usa con un identificador de entrada de consola para hacer que las funciones <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>readfile</strong></a> y <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> devuelvan cuando se presiona la tecla entrar.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-131">Used with a console input handle to cause the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> and <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> functions to return when the ENTER key is pressed.</span></span> <span data-ttu-id="f5cfd-132">Si el modo de entrada de línea está deshabilitado, las funciones devuelven cuando uno o varios caracteres están disponibles en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-132">If line input mode is disabled, the functions return when one or more characters are available in the input buffer.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="f5cfd-133"><strong>ENABLE_ECHO_INPUT</strong></span><span class="sxs-lookup"><span data-stu-id="f5cfd-133"><strong>ENABLE_ECHO_INPUT</strong></span></span></td>
<td><span data-ttu-id="f5cfd-134">Se usa con un identificador de entrada de consola para hacer que la entrada de teclado leída por la función <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>readfile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> se repita en el búfer de pantalla activo.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-134">Used with a console input handle to cause keyboard input read by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function to be echoed to the active screen buffer.</span></span> <span data-ttu-id="f5cfd-135">Los caracteres se repiten solo si el proceso que llama a <strong>readfile</strong> o <strong>ReadConsole</strong> tiene un identificador abierto para el búfer de pantalla activo.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-135">Characters are echoed only if the process that calls <strong>ReadFile</strong> or <strong>ReadConsole</strong> has an open handle to the active screen buffer.</span></span> <span data-ttu-id="f5cfd-136">No se puede habilitar el modo de eco a menos que la entrada de línea también esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-136">Echo mode cannot be enabled unless line input is also enabled.</span></span> <span data-ttu-id="f5cfd-137">El modo de salida del búfer de pantalla activo afecta a la forma en que se muestra la entrada en eco.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-137">The output mode of the active screen buffer affects the way echoed input is displayed.</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="f5cfd-138"><strong>ENABLE_PROCESSED_OUTPUT</strong></span><span class="sxs-lookup"><span data-stu-id="f5cfd-138"><strong>ENABLE_PROCESSED_OUTPUT</strong></span></span></td>
<td><span data-ttu-id="f5cfd-139">Se usa con un identificador de búfer de pantalla de la consola para hacer que el sistema realice la acción adecuada para los caracteres de control ANSI que se escriben en un búfer de pantalla.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-139">Used with a console screen buffer handle to cause the system to perform the appropriate action for ANSI control characters that are written to a screen buffer.</span></span> <span data-ttu-id="f5cfd-140">Se procesan los caracteres de retroceso, tabulación, campana, retorno de carro y avance de línea.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-140">The backspace, tab, bell, carriage return, and line feed characters are processed.</span></span> <span data-ttu-id="f5cfd-141">Un carácter de tabulación mueve el cursor a la siguiente tabulación, que se produce cada ocho caracteres.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-141">A tab character moves the cursor to the next tab stop, which occurs every eight characters.</span></span> <span data-ttu-id="f5cfd-142">Un carácter de campana emite un tono breve.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-142">A bell character sounds a short tone.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="f5cfd-143"><strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong></span><span class="sxs-lookup"><span data-stu-id="f5cfd-143"><strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong></span></span></td>
<td><span data-ttu-id="f5cfd-144">Se usa con un identificador de búfer de pantalla de la consola para hacer que la posición de salida actual (posición del cursor) se mueva a la primera columna de la fila siguiente (línea) cuando se alcanza el final de la fila actual.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-144">Used with a console screen buffer handle to cause the current output position (cursor position) to move to the first column in the next row (line) when the end of the current row is reached.</span></span> <span data-ttu-id="f5cfd-145">Si se alcanza la parte inferior de la región de la ventana, el origen de la ventana se mueve una fila hacia abajo.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-145">If the bottom of the window region is reached, the window origin is moved down one row.</span></span> <span data-ttu-id="f5cfd-146">Este movimiento tiene el efecto de desplazar el contenido de la ventana hacia arriba una fila.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-146">This movement has the effect of scrolling the contents of the window up one row.</span></span> <span data-ttu-id="f5cfd-147">Si se alcanza la parte inferior del búfer de pantalla de la consola, el contenido del búfer de pantalla se desplaza una fila hacia arriba y se descarta la fila superior del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-147">If the bottom of the console screen buffer is reached, the contents of the console screen buffer are scrolled up one row, and the top row of the console screen buffer is discarded.</span></span>
<p><span data-ttu-id="f5cfd-148">Si este modo está deshabilitado, el último carácter de la fila se sobrescribe con los caracteres posteriores.</span><span class="sxs-lookup"><span data-stu-id="f5cfd-148">If this mode is disabled, the last character in the row is overwritten with any subsequent characters.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

 

 




