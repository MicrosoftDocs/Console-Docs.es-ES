---
title: Secuencias de terminal virtuales de la consola
description: Las secuencias de terminal virtuales son secuencias de caracteres de control que pueden controlar el movimiento del cursor, el modo del color y la fuente y otras operaciones cuando se escriben en el flujo de salida.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: A5C553A5-FD84-4D16-A814-EDB3B8699B91
ms.openlocfilehash: 45ee5518ec8ea2da840d2a4442efd9e0d4346526
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "93039153"
---
# <a name="console-virtual-terminal-sequences"></a><span data-ttu-id="ecfab-104">Secuencias de terminal virtuales de la consola</span><span class="sxs-lookup"><span data-stu-id="ecfab-104">Console Virtual Terminal Sequences</span></span>


<span data-ttu-id="ecfab-105">Las secuencias de terminal virtuales son secuencias de caracteres de control que pueden controlar el movimiento del cursor, el modo del color y la fuente y otras operaciones cuando se escriben en el flujo de salida.</span><span class="sxs-lookup"><span data-stu-id="ecfab-105">Virtual terminal sequences are control character sequences that can control cursor movement, color/font mode, and other operations when written to the output stream.</span></span> <span data-ttu-id="ecfab-106">Asimismo, también se pueden recibir secuencias en el flujo de entrada en respuesta a una secuencia de información de consulta del flujo de salida o como codificación de aquellos datos proporcionados por el usuario cuando se establece el modo adecuado.</span><span class="sxs-lookup"><span data-stu-id="ecfab-106">Sequences may also be received on the input stream in response to an output stream query information sequence or as an encoding of user input when the appropriate mode is set.</span></span>

<span data-ttu-id="ecfab-107">Puede usar las funciones [**GetConsoleMode**](getconsolemode.md) y [**SetConsoleMode**](setconsolemode.md) para configurar este comportamiento.</span><span class="sxs-lookup"><span data-stu-id="ecfab-107">You can use [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions to configure this behavior.</span></span> <span data-ttu-id="ecfab-108">Al final de este documento, se incluye un ejemplo con el método sugerido para habilitar los comportamientos de terminal virtual.</span><span class="sxs-lookup"><span data-stu-id="ecfab-108">A sample of the suggested way to enable virtual terminal behaviors is included at the end of this document.</span></span>

<span data-ttu-id="ecfab-109">El comportamiento de las siguientes secuencias se basa en las tecnologías de VT100 y de emulador de terminal derivado, especialmente en tecnologías del emulador de terminal xterm.</span><span class="sxs-lookup"><span data-stu-id="ecfab-109">The behavior of the following sequences is based on the VT100 and derived terminal emulator technologies, most specifically the xterm terminal emulator.</span></span> <span data-ttu-id="ecfab-110">Puede encontrar más información sobre las secuencias de terminal en <http://vt100.net> y en <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span><span class="sxs-lookup"><span data-stu-id="ecfab-110">More information about terminal sequences can be found at <http://vt100.net> and at <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span></span>

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span data-ttu-id="ecfab-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Secuencias de salida</span><span class="sxs-lookup"><span data-stu-id="ecfab-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Output Sequences</span></span>


<span data-ttu-id="ecfab-112">El host de consola intercepta las siguientes secuencias de terminal cuando se escriben en el flujo de salida, si se establece la marca ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING en el identificador del búfer de pantalla mediante la función [**SetConsoleMode**](setconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="ecfab-112">The following terminal sequences are intercepted by the console host when written into the output stream, if the ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING flag is set on the screen buffer handle using the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="ecfab-113">Tenga en cuenta que la marca DISABLE\_NEWLINE\_AUTO\_RETURN también puede serle útil para emular la posición del cursor y el comportamiento de desplazamiento de otros emuladores de terminal, en relación con los caracteres que se hayan escrito en la columna final de cualquier fila.</span><span class="sxs-lookup"><span data-stu-id="ecfab-113">Note that the DISABLE\_NEWLINE\_AUTO\_RETURN flag may also be useful in emulating the cursor positioning and scrolling behavior of other terminal emulators in relation to characters written to the final column in any row.</span></span>

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span data-ttu-id="ecfab-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Posición de cursor simple</span><span class="sxs-lookup"><span data-stu-id="ecfab-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Simple Cursor Positioning</span></span>


<span data-ttu-id="ecfab-115">En todas las descripciones que se proporcionan a continuación, ESC siempre es el valor hexadecimal 0x1B.</span><span class="sxs-lookup"><span data-stu-id="ecfab-115">In all of the following descriptions, ESC is always the hexadecimal value 0x1B.</span></span> <span data-ttu-id="ecfab-116">No se incluirán espacios en las secuencias de terminal.</span><span class="sxs-lookup"><span data-stu-id="ecfab-116">No spaces are to be included in terminal sequences.</span></span> <span data-ttu-id="ecfab-117">Para obtener un ejemplo de cómo se usan estas secuencias en la práctica, consulte el [ejemplo](#example) que se encuentra al final de este tema.</span><span class="sxs-lookup"><span data-stu-id="ecfab-117">For an example of how these sequences are used in practice, please see the [example](#example) at the end of this topic.</span></span>

<span data-ttu-id="ecfab-118">En la siguiente tabla se describen las secuencias de escape simples que cuentan con un solo comando de acción directamente después del carácter ESC.</span><span class="sxs-lookup"><span data-stu-id="ecfab-118">The following table describes simple escape sequences with a single action command directly after the ESC character.</span></span> <span data-ttu-id="ecfab-119">Estas secuencias no tienen ningún parámetro y surten efecto inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="ecfab-119">These sequences have no parameters and take effect immediately.</span></span>

<span data-ttu-id="ecfab-120">En general, todos los comandos de esta tabla son equivalentes a la llamada que se realiza a la API de consola [**SetConsoleCursorPosition**](setconsolecursorposition.md) para colocar el cursor.</span><span class="sxs-lookup"><span data-stu-id="ecfab-120">All commands in this table are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API to place the cursor.</span></span>

<span data-ttu-id="ecfab-121">La ventanilla actual del búfer se encargará de limitar el movimiento del cursor.</span><span class="sxs-lookup"><span data-stu-id="ecfab-121">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="ecfab-122">No se producirá el desplazamiento (si está disponible).</span><span class="sxs-lookup"><span data-stu-id="ecfab-122">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="ecfab-123">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-123">Sequence</span></span> | <span data-ttu-id="ecfab-124">Abreviatura</span><span class="sxs-lookup"><span data-stu-id="ecfab-124">Shorthand</span></span> | <span data-ttu-id="ecfab-125">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-125">Behavior</span></span> |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ecfab-126">ESC A</span><span class="sxs-lookup"><span data-stu-id="ecfab-126">ESC A</span></span> | <span data-ttu-id="ecfab-127">CUU</span><span class="sxs-lookup"><span data-stu-id="ecfab-127">CUU</span></span> | <span data-ttu-id="ecfab-128">Cursor hacia arriba en 1.</span><span class="sxs-lookup"><span data-stu-id="ecfab-128">Cursor Up by 1</span></span> |
| <span data-ttu-id="ecfab-129">ESC B</span><span class="sxs-lookup"><span data-stu-id="ecfab-129">ESC B</span></span> | <span data-ttu-id="ecfab-130">CUD</span><span class="sxs-lookup"><span data-stu-id="ecfab-130">CUD</span></span> | <span data-ttu-id="ecfab-131">Cursor hacia abajo en 1.</span><span class="sxs-lookup"><span data-stu-id="ecfab-131">Cursor Down by 1</span></span> |
| <span data-ttu-id="ecfab-132">ESC C</span><span class="sxs-lookup"><span data-stu-id="ecfab-132">ESC C</span></span> | <span data-ttu-id="ecfab-133">CUF</span><span class="sxs-lookup"><span data-stu-id="ecfab-133">CUF</span></span> | <span data-ttu-id="ecfab-134">Cursor hacia delante (derecha) en 1.</span><span class="sxs-lookup"><span data-stu-id="ecfab-134">Cursor Forward (Right) by 1</span></span> |
| <span data-ttu-id="ecfab-135">ESC D</span><span class="sxs-lookup"><span data-stu-id="ecfab-135">ESC D</span></span> | <span data-ttu-id="ecfab-136">CUB</span><span class="sxs-lookup"><span data-stu-id="ecfab-136">CUB</span></span> | <span data-ttu-id="ecfab-137">Cursor hacia atrás (izquierda) en 1.</span><span class="sxs-lookup"><span data-stu-id="ecfab-137">Cursor Backward (Left) by 1</span></span> |
| <span data-ttu-id="ecfab-138">ESC M</span><span class="sxs-lookup"><span data-stu-id="ecfab-138">ESC M</span></span> | <span data-ttu-id="ecfab-139">Instancia reservada</span><span class="sxs-lookup"><span data-stu-id="ecfab-139">RI</span></span> | <span data-ttu-id="ecfab-140">Índice inverso: realiza la operación inversa de \\n, mueve el cursor una línea hacia arriba, mantiene la posición horizontal y desplaza el búfer si es necesario\*.</span><span class="sxs-lookup"><span data-stu-id="ecfab-140">Reverse Index – Performs the reverse operation of \\n, moves cursor up one line, maintains horizontal position, scrolls buffer if necessary\*</span></span> |
| <span data-ttu-id="ecfab-141">ESC 7</span><span class="sxs-lookup"><span data-stu-id="ecfab-141">ESC 7</span></span> | <span data-ttu-id="ecfab-142">DECSC</span><span class="sxs-lookup"><span data-stu-id="ecfab-142">DECSC</span></span> | <span data-ttu-id="ecfab-143">Permite guardar la posición del cursor en la memoria\*\*.</span><span class="sxs-lookup"><span data-stu-id="ecfab-143">Save Cursor Position in Memory\*\*</span></span> |
| <span data-ttu-id="ecfab-144">ESC 8</span><span class="sxs-lookup"><span data-stu-id="ecfab-144">ESC 8</span></span> | <span data-ttu-id="ecfab-145">DECSR</span><span class="sxs-lookup"><span data-stu-id="ecfab-145">DECSR</span></span> | <span data-ttu-id="ecfab-146">Permite restaurar la posición del cursor de la memoria\*\*.</span><span class="sxs-lookup"><span data-stu-id="ecfab-146">Restore Cursor Position from Memory\*\*</span></span> |



> [!NOTE]
><span data-ttu-id="ecfab-147">\* Si hay márgenes de desplazamiento establecidos, la secuencia RI dentro de los márgenes solo desplazará el contenido de los márgenes y dejará la ventanilla sin cambios.</span><span class="sxs-lookup"><span data-stu-id="ecfab-147">\* If there are scroll margins set, RI inside the margins will scroll only the contents of the margins, and leave the viewport unchanged.</span></span> <span data-ttu-id="ecfab-148">(Consulte los márgenes de desplazamiento)</span><span class="sxs-lookup"><span data-stu-id="ecfab-148">(See Scrolling Margins)</span></span>
>
><span data-ttu-id="ecfab-149">\*\*No habrá ningún valor guardado en la memoria hasta que no se use por primera vez el comando save.</span><span class="sxs-lookup"><span data-stu-id="ecfab-149">\*\*There will be no value saved in memory until the first use of the save command.</span></span> <span data-ttu-id="ecfab-150">La única manera de obtener acceso al valor guardado es con el comando restore.</span><span class="sxs-lookup"><span data-stu-id="ecfab-150">The only way to access the saved value is with the restore command.</span></span>

## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span data-ttu-id="ecfab-151"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Posición del cursor</span><span class="sxs-lookup"><span data-stu-id="ecfab-151"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursor Positioning</span></span>


<span data-ttu-id="ecfab-152">En las tablas siguientes se indican las secuencias de tipo Control Sequence Introducer (CSI).</span><span class="sxs-lookup"><span data-stu-id="ecfab-152">The following tables encompass Control Sequence Introducer (CSI) type sequences.</span></span> <span data-ttu-id="ecfab-153">Todas las secuencias CSI comienzan con el valor ESC (0x1B), seguido de \[ (corchete de apertura, 0x5B), y pueden contener parámetros de longitud variable para especificar más información de cada operación.</span><span class="sxs-lookup"><span data-stu-id="ecfab-153">All CSI sequences start with ESC (0x1B) followed by \[ (left bracket, 0x5B) and may contain parameters of variable length to specify more information for each operation.</span></span> <span data-ttu-id="ecfab-154">Esto se representará con la abreviatura &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="ecfab-154">This will be represented by the shorthand &lt;n&gt;.</span></span> <span data-ttu-id="ecfab-155">Cada una de las tablas siguientes está agrupada según la funcionalidad, y debajo de cada tabla encontrará una serie de notas en las que se explica cómo funciona el grupo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-155">Each table below is grouped by functionality with notes below each table explaining how the group works.</span></span>

<span data-ttu-id="ecfab-156">En todos los parámetros se aplican las reglas siguientes, a menos que se indique lo contrario:</span><span class="sxs-lookup"><span data-stu-id="ecfab-156">For all parameters, the following rules apply unless otherwise noted:</span></span>

- <span data-ttu-id="ecfab-157">&lt;n&gt; representa la distancia de traslado y es un parámetro opcional.</span><span class="sxs-lookup"><span data-stu-id="ecfab-157">&lt;n&gt; represents the distance to move and is an optional parameter</span></span>
- <span data-ttu-id="ecfab-158">Si &lt;n&gt; se omite o es igual a 0, se tratará como 1.</span><span class="sxs-lookup"><span data-stu-id="ecfab-158">If &lt;n&gt; is omitted or equals 0, it will be treated as a 1</span></span>
- <span data-ttu-id="ecfab-159">&lt;n&gt; no puede ser mayor que 32.767 (valor corto máximo).</span><span class="sxs-lookup"><span data-stu-id="ecfab-159">&lt;n&gt; cannot be larger than 32,767 (maximum short value)</span></span>
- <span data-ttu-id="ecfab-160">&lt;n&gt; no puede ser negativo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-160">&lt;n&gt; cannot be negative</span></span>

<span data-ttu-id="ecfab-161">En general, todos los comandos de esta sección son equivalentes a la llamada que se realiza a la API de consola [**SetConsoleCursorPosition**](setconsolecursorposition.md).</span><span class="sxs-lookup"><span data-stu-id="ecfab-161">All commands in this section are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API.</span></span>

<span data-ttu-id="ecfab-162">La ventanilla actual del búfer se encargará de limitar el movimiento del cursor.</span><span class="sxs-lookup"><span data-stu-id="ecfab-162">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="ecfab-163">No se producirá el desplazamiento (si está disponible).</span><span class="sxs-lookup"><span data-stu-id="ecfab-163">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="ecfab-164">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-164">Sequence</span></span> | <span data-ttu-id="ecfab-165">Código</span><span class="sxs-lookup"><span data-stu-id="ecfab-165">Code</span></span> | <span data-ttu-id="ecfab-166">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-166">Description</span></span> | <span data-ttu-id="ecfab-167">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-167">Behavior</span></span> |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ecfab-168">ESC \[ &lt;n&gt; A</span><span class="sxs-lookup"><span data-stu-id="ecfab-168">ESC \[ &lt;n&gt; A</span></span> | <span data-ttu-id="ecfab-169">CUU</span><span class="sxs-lookup"><span data-stu-id="ecfab-169">CUU</span></span> | <span data-ttu-id="ecfab-170">Cursor hacia arriba</span><span class="sxs-lookup"><span data-stu-id="ecfab-170">Cursor Up</span></span> | <span data-ttu-id="ecfab-171">Cursor hacia arriba en &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="ecfab-171">Cursor up by &lt;n&gt;</span></span> |
| <span data-ttu-id="ecfab-172">ESC \[ &lt;n&gt; B</span><span class="sxs-lookup"><span data-stu-id="ecfab-172">ESC \[ &lt;n&gt; B</span></span> | <span data-ttu-id="ecfab-173">CUD</span><span class="sxs-lookup"><span data-stu-id="ecfab-173">CUD</span></span> | <span data-ttu-id="ecfab-174">Cursor hacia abajo</span><span class="sxs-lookup"><span data-stu-id="ecfab-174">Cursor Down</span></span> | <span data-ttu-id="ecfab-175">Cursor hacia abajo en &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="ecfab-175">Cursor down by &lt;n&gt;</span></span> |
| <span data-ttu-id="ecfab-176">ESC \[ &lt;n&gt; C</span><span class="sxs-lookup"><span data-stu-id="ecfab-176">ESC \[ &lt;n&gt; C</span></span> | <span data-ttu-id="ecfab-177">CUF</span><span class="sxs-lookup"><span data-stu-id="ecfab-177">CUF</span></span> | <span data-ttu-id="ecfab-178">Cursor hacia delante</span><span class="sxs-lookup"><span data-stu-id="ecfab-178">Cursor Forward</span></span> | <span data-ttu-id="ecfab-179">Cursor hacia delante (derecha) en &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="ecfab-179">Cursor forward (Right) by &lt;n&gt;</span></span> |
| <span data-ttu-id="ecfab-180">ESC \[ &lt;n&gt; D</span><span class="sxs-lookup"><span data-stu-id="ecfab-180">ESC \[ &lt;n&gt; D</span></span> | <span data-ttu-id="ecfab-181">CUB</span><span class="sxs-lookup"><span data-stu-id="ecfab-181">CUB</span></span> | <span data-ttu-id="ecfab-182">Cursor hacia atrás</span><span class="sxs-lookup"><span data-stu-id="ecfab-182">Cursor Backward</span></span> | <span data-ttu-id="ecfab-183">Cursor hacia atrás (izquierda) en &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="ecfab-183">Cursor backward (Left) by &lt;n&gt;</span></span> |
| <span data-ttu-id="ecfab-184">ESC \[ &lt;n&gt; E</span><span class="sxs-lookup"><span data-stu-id="ecfab-184">ESC \[ &lt;n&gt; E</span></span> | <span data-ttu-id="ecfab-185">CNL</span><span class="sxs-lookup"><span data-stu-id="ecfab-185">CNL</span></span> | <span data-ttu-id="ecfab-186">Siguiente línea del cursor</span><span class="sxs-lookup"><span data-stu-id="ecfab-186">Cursor Next Line</span></span> | <span data-ttu-id="ecfab-187">El cursor se desplaza hacia abajo &lt;n&gt; líneas desde la posición actual.</span><span class="sxs-lookup"><span data-stu-id="ecfab-187">Cursor down &lt;n&gt; lines from current position</span></span> |
| <span data-ttu-id="ecfab-188">ESC \[ &lt;n&gt; F</span><span class="sxs-lookup"><span data-stu-id="ecfab-188">ESC \[ &lt;n&gt; F</span></span> | <span data-ttu-id="ecfab-189">CPL</span><span class="sxs-lookup"><span data-stu-id="ecfab-189">CPL</span></span> | <span data-ttu-id="ecfab-190">Línea anterior al cursor</span><span class="sxs-lookup"><span data-stu-id="ecfab-190">Cursor Previous Line</span></span> | <span data-ttu-id="ecfab-191">El cursor se desplaza hacia arriba &lt;n&gt; líneas desde la posición actual.</span><span class="sxs-lookup"><span data-stu-id="ecfab-191">Cursor up &lt;n&gt; lines from current position</span></span> |
| <span data-ttu-id="ecfab-192">ESC \[ &lt;n&gt; G</span><span class="sxs-lookup"><span data-stu-id="ecfab-192">ESC \[ &lt;n&gt; G</span></span> | <span data-ttu-id="ecfab-193">CHA</span><span class="sxs-lookup"><span data-stu-id="ecfab-193">CHA</span></span> | <span data-ttu-id="ecfab-194">Horizontal absoluto del cursor</span><span class="sxs-lookup"><span data-stu-id="ecfab-194">Cursor Horizontal Absolute</span></span> | <span data-ttu-id="ecfab-195">El cursor se mueve a la &lt;n&gt;ª posición horizontal en la línea actual.</span><span class="sxs-lookup"><span data-stu-id="ecfab-195">Cursor moves to &lt;n&gt;th position horizontally in the current line</span></span> |
| <span data-ttu-id="ecfab-196">ESC \[ &lt;n&gt; d</span><span class="sxs-lookup"><span data-stu-id="ecfab-196">ESC \[ &lt;n&gt; d</span></span> | <span data-ttu-id="ecfab-197">VPA</span><span class="sxs-lookup"><span data-stu-id="ecfab-197">VPA</span></span> | <span data-ttu-id="ecfab-198">Posición de línea vertical absoluta</span><span class="sxs-lookup"><span data-stu-id="ecfab-198">Vertical Line Position Absolute</span></span> | <span data-ttu-id="ecfab-199">El cursor se desplaza a la &lt;n&gt;ª posición vertical en la columna actual.</span><span class="sxs-lookup"><span data-stu-id="ecfab-199">Cursor moves to the &lt;n&gt;th position vertically in the current column</span></span> |
| <span data-ttu-id="ecfab-200">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span><span class="sxs-lookup"><span data-stu-id="ecfab-200">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span></span> | <span data-ttu-id="ecfab-201">CUP</span><span class="sxs-lookup"><span data-stu-id="ecfab-201">CUP</span></span> | <span data-ttu-id="ecfab-202">Posición del cursor</span><span class="sxs-lookup"><span data-stu-id="ecfab-202">Cursor Position</span></span> | <span data-ttu-id="ecfab-203">\*El cursor se mueve a la coordenada &lt;x&gt;; &lt;y&gt; dentro de la ventanilla, donde &lt;x&gt; es la columna de la línea &lt;y&gt;.</span><span class="sxs-lookup"><span data-stu-id="ecfab-203">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="ecfab-204">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span><span class="sxs-lookup"><span data-stu-id="ecfab-204">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span></span> | <span data-ttu-id="ecfab-205">HVP</span><span class="sxs-lookup"><span data-stu-id="ecfab-205">HVP</span></span> | <span data-ttu-id="ecfab-206">Posición vertical horizontal</span><span class="sxs-lookup"><span data-stu-id="ecfab-206">Horizontal Vertical Position</span></span> | <span data-ttu-id="ecfab-207">\*El cursor se mueve a la coordenada &lt;x&gt;; &lt;y&gt; dentro de la ventanilla, donde &lt;x&gt; es la columna de la línea &lt;y&gt;.</span><span class="sxs-lookup"><span data-stu-id="ecfab-207">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="ecfab-208">ESC \[ s</span><span class="sxs-lookup"><span data-stu-id="ecfab-208">ESC \[ s</span></span> | <span data-ttu-id="ecfab-209">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="ecfab-209">ANSISYSSC</span></span> | <span data-ttu-id="ecfab-210">Permite guardar el cursor: emulación Ansi.sys</span><span class="sxs-lookup"><span data-stu-id="ecfab-210">Save Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="ecfab-211">\*\*Sin parámetros; realiza una operación para guardar el cursor como DECSC.</span><span class="sxs-lookup"><span data-stu-id="ecfab-211">\*\*With no parameters, performs a save cursor operation like DECSC</span></span> |
| <span data-ttu-id="ecfab-212">ESC \[ u</span><span class="sxs-lookup"><span data-stu-id="ecfab-212">ESC \[ u</span></span> | <span data-ttu-id="ecfab-213">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="ecfab-213">ANSISYSSC</span></span> | <span data-ttu-id="ecfab-214">Permite restaurar el cursor: emulación Ansi.sys</span><span class="sxs-lookup"><span data-stu-id="ecfab-214">Restore Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="ecfab-215">\*\*Sin parámetros; realiza una operación para restaurar el cursor como DECRC.</span><span class="sxs-lookup"><span data-stu-id="ecfab-215">\*\*With no parameters, performs a restore cursor operation like DECRC</span></span> |



> [!NOTE]
><span data-ttu-id="ecfab-216">\*Los parámetros &lt;x&gt; e &lt;y&gt; tienen las mismas limitaciones que el valor &lt;n&gt; anterior.</span><span class="sxs-lookup"><span data-stu-id="ecfab-216">\*&lt;x&gt; and &lt;y&gt; parameters have the same limitations as &lt;n&gt; above.</span></span> <span data-ttu-id="ecfab-217">Si &lt;x&gt; e &lt;y&gt; se omiten, los valores se establecerán en 1;1.</span><span class="sxs-lookup"><span data-stu-id="ecfab-217">If &lt;x&gt; and &lt;y&gt; are omitted, they will be set to 1;1.</span></span>
>
><span data-ttu-id="ecfab-218">\*\*La documentación histórica de ANSI.sys se puede encontrar en <https://msdn.microsoft.com/library/cc722862.aspx> y se implementa en función de la comodidad y la compatibilidad.</span><span class="sxs-lookup"><span data-stu-id="ecfab-218">\*\*ANSI.sys historical documentation can be found at <https://msdn.microsoft.com/library/cc722862.aspx> and is implemented for convenience/compatibility.</span></span>



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span data-ttu-id="ecfab-219"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Visibilidad del cursor</span><span class="sxs-lookup"><span data-stu-id="ecfab-219"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursor Visibility</span></span>


<span data-ttu-id="ecfab-220">Los siguientes comandos controlan la visibilidad del cursor y su estado de parpadeo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-220">The following commands control the visibility of the cursor and its blinking state.</span></span> <span data-ttu-id="ecfab-221">Las secuencias DECTCEM suelen ser equivalentes a llamar a la API de consola [**SetConsoleCursorInfo**](setconsolecursorinfo.md) para alternar la visibilidad del cursor.</span><span class="sxs-lookup"><span data-stu-id="ecfab-221">The DECTCEM sequences are generally equivalent to calling [**SetConsoleCursorInfo**](setconsolecursorinfo.md) console API to toggle cursor visibility.</span></span>


| <span data-ttu-id="ecfab-222">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-222">Sequence</span></span> | <span data-ttu-id="ecfab-223">Código</span><span class="sxs-lookup"><span data-stu-id="ecfab-223">Code</span></span> | <span data-ttu-id="ecfab-224">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-224">Description</span></span> | <span data-ttu-id="ecfab-225">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-225">Behavior</span></span> |
|---------------|---------|------------------------------|---------------------------|
| <span data-ttu-id="ecfab-226">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="ecfab-226">ESC \[ ?</span></span> <span data-ttu-id="ecfab-227">12 h</span><span class="sxs-lookup"><span data-stu-id="ecfab-227">12 h</span></span> | <span data-ttu-id="ecfab-228">ATT160</span><span class="sxs-lookup"><span data-stu-id="ecfab-228">ATT160</span></span> | <span data-ttu-id="ecfab-229">Cursor de texto para habilitar el parpadeo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-229">Text Cursor Enable Blinking</span></span> | <span data-ttu-id="ecfab-230">Permite iniciar el parpadeo del cursor.</span><span class="sxs-lookup"><span data-stu-id="ecfab-230">Start the cursor blinking</span></span> |
| <span data-ttu-id="ecfab-231">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="ecfab-231">ESC \[ ?</span></span> <span data-ttu-id="ecfab-232">12 l</span><span class="sxs-lookup"><span data-stu-id="ecfab-232">12 l</span></span> | <span data-ttu-id="ecfab-233">ATT160</span><span class="sxs-lookup"><span data-stu-id="ecfab-233">ATT160</span></span> | <span data-ttu-id="ecfab-234">Cursor de texto para deshabilitar el parpadeo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-234">Text Cursor Disable Blinking</span></span> | <span data-ttu-id="ecfab-235">Permite detener el parpadeo del cursor.</span><span class="sxs-lookup"><span data-stu-id="ecfab-235">Stop blinking the cursor</span></span> |
| <span data-ttu-id="ecfab-236">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="ecfab-236">ESC \[ ?</span></span> <span data-ttu-id="ecfab-237">25 h</span><span class="sxs-lookup"><span data-stu-id="ecfab-237">25 h</span></span> | <span data-ttu-id="ecfab-238">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="ecfab-238">DECTCEM</span></span> | <span data-ttu-id="ecfab-239">Cursor de texto para habilitar el modo para mostrarlo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-239">Text Cursor Enable Mode Show</span></span> | <span data-ttu-id="ecfab-240">Permite mostrar el cursor.</span><span class="sxs-lookup"><span data-stu-id="ecfab-240">Show the cursor</span></span> |
| <span data-ttu-id="ecfab-241">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="ecfab-241">ESC \[ ?</span></span> <span data-ttu-id="ecfab-242">25 l</span><span class="sxs-lookup"><span data-stu-id="ecfab-242">25 l</span></span> | <span data-ttu-id="ecfab-243">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="ecfab-243">DECTCEM</span></span> | <span data-ttu-id="ecfab-244">Cursor de texto para habilitar el modo para ocultarlo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-244">Text Cursor Enable Mode Hide</span></span> | <span data-ttu-id="ecfab-245">Permite ocultar el cursor.</span><span class="sxs-lookup"><span data-stu-id="ecfab-245">Hide the cursor</span></span> |

> [!TIP]
> <span data-ttu-id="ecfab-246">Las secuencias de habilitación terminan en un carácter H en minúscula (`h`) y las secuencias de deshabilitación terminan en un carácter L en minúscula (`l`).</span><span class="sxs-lookup"><span data-stu-id="ecfab-246">The enable sequences end in a lowercase H character (`h`) and the disable sequences end in a lowercase L character (`l`).</span></span>

## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span data-ttu-id="ecfab-247"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Posición de la ventanilla</span><span class="sxs-lookup"><span data-stu-id="ecfab-247"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Viewport Positioning</span></span>


<span data-ttu-id="ecfab-248">En general, todos los comandos de esta sección son equivalentes a llamar a la API de consola [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) para trasladar el contenido del búfer de la consola.</span><span class="sxs-lookup"><span data-stu-id="ecfab-248">All commands in this section are generally equivalent to calling [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console API to move the contents of the console buffer.</span></span>

<span data-ttu-id="ecfab-249">**Precaución**: los nombres de comando son engañosos.</span><span class="sxs-lookup"><span data-stu-id="ecfab-249">**Caution** The command names are misleading.</span></span> <span data-ttu-id="ecfab-250">"Desplazar" hace referencia a la dirección en la que se mueve el texto durante la operación, no a la manera en que la ventanilla se debería mover.</span><span class="sxs-lookup"><span data-stu-id="ecfab-250">Scroll refers to which direction the text moves during the operation, not which way the viewport would seem to move.</span></span>




| <span data-ttu-id="ecfab-251">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-251">Sequence</span></span> | <span data-ttu-id="ecfab-252">Código</span><span class="sxs-lookup"><span data-stu-id="ecfab-252">Code</span></span> | <span data-ttu-id="ecfab-253">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-253">Description</span></span> | <span data-ttu-id="ecfab-254">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-254">Behavior</span></span> |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ecfab-255">ESC \[ &lt;n&gt; S</span><span class="sxs-lookup"><span data-stu-id="ecfab-255">ESC \[ &lt;n&gt; S</span></span> | <span data-ttu-id="ecfab-256">SU</span><span class="sxs-lookup"><span data-stu-id="ecfab-256">SU</span></span> | <span data-ttu-id="ecfab-257">Desplazar hacia arriba</span><span class="sxs-lookup"><span data-stu-id="ecfab-257">Scroll Up</span></span> | <span data-ttu-id="ecfab-258">Desplazar el texto hacia arriba en &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="ecfab-258">Scroll text up by &lt;n&gt;.</span></span> <span data-ttu-id="ecfab-259">Opción también conocida como "Movimiento panorámico hacia abajo", las nuevas líneas se rellenan desde la parte inferior de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="ecfab-259">Also known as pan down, new lines fill in from the bottom of the screen</span></span> |
| <span data-ttu-id="ecfab-260">ESC \[ &lt;n&gt; T</span><span class="sxs-lookup"><span data-stu-id="ecfab-260">ESC \[ &lt;n&gt; T</span></span> | <span data-ttu-id="ecfab-261">SD</span><span class="sxs-lookup"><span data-stu-id="ecfab-261">SD</span></span> | <span data-ttu-id="ecfab-262">Desplazar hacia abajo</span><span class="sxs-lookup"><span data-stu-id="ecfab-262">Scroll Down</span></span> | <span data-ttu-id="ecfab-263">Desplazarse hacia abajo en &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="ecfab-263">Scroll down by &lt;n&gt;.</span></span> <span data-ttu-id="ecfab-264">Opción también conocida como "Movimiento panorámico hacia arriba", las nuevas líneas se rellenan desde la parte superior de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="ecfab-264">Also known as pan up, new lines fill in from the top of the screen</span></span> |



<span data-ttu-id="ecfab-265">El texto se mueve a partir de la línea en la que se encuentra el cursor.</span><span class="sxs-lookup"><span data-stu-id="ecfab-265">The text is moved starting with the line the cursor is on.</span></span> <span data-ttu-id="ecfab-266">Si el cursor está en la fila central de la ventanilla, al desplazarse hacia arriba se moverá la mitad inferior de la ventanilla y se insertarán líneas en blanco en la parte inferior.</span><span class="sxs-lookup"><span data-stu-id="ecfab-266">If the cursor is on the middle row of the viewport, then scroll up would move the bottom half of the viewport, and insert blank lines at the bottom.</span></span> <span data-ttu-id="ecfab-267">En cambio, si se desplaza hacia abajo, se moverá la mitad superior de las filas de la ventanilla y se insertarán nuevas líneas en la parte superior.</span><span class="sxs-lookup"><span data-stu-id="ecfab-267">Scroll down would move the top half of the viewport’s rows, and insert new lines at the top.</span></span>

<span data-ttu-id="ecfab-268">También es importante tener en cuenta que los márgenes de desplazamiento también afectan a las opciones para desplazarse hacia arriba y hacia abajo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-268">Also important to note is scroll up and down are also affected by the scrolling margins.</span></span> <span data-ttu-id="ecfab-269">En cambio, desplazarse hacia arriba y hacia abajo no afectará a las líneas que estén fuera de los márgenes desplazados.</span><span class="sxs-lookup"><span data-stu-id="ecfab-269">Scroll up and down won’t affect any lines outside the scrolling margins.</span></span>

<span data-ttu-id="ecfab-270">El valor predeterminado de &lt;n&gt; es 1, aunque este valor se puede omitir opcionalmente.</span><span class="sxs-lookup"><span data-stu-id="ecfab-270">The default value for &lt;n&gt; is 1, and the value can be optionally omitted.</span></span>

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span data-ttu-id="ecfab-271"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Modificación de texto</span><span class="sxs-lookup"><span data-stu-id="ecfab-271"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Text Modification</span></span>


<span data-ttu-id="ecfab-272">Todos los comandos de esta sección suelen ser equivalentes a llamar a las API de consola [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) y [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) para modificar el contenido del búfer de texto.</span><span class="sxs-lookup"><span data-stu-id="ecfab-272">All commands in this section are generally equivalent to calling [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md), and [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console APIs to modify the text buffer contents.</span></span>


| <span data-ttu-id="ecfab-273">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-273">Sequence</span></span> | <span data-ttu-id="ecfab-274">Código</span><span class="sxs-lookup"><span data-stu-id="ecfab-274">Code</span></span> | <span data-ttu-id="ecfab-275">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-275">Description</span></span> | <span data-ttu-id="ecfab-276">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-276">Behavior</span></span> |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ecfab-277">ESC \[ &lt;n&gt; @</span><span class="sxs-lookup"><span data-stu-id="ecfab-277">ESC \[ &lt;n&gt; @</span></span> | <span data-ttu-id="ecfab-278">ICH</span><span class="sxs-lookup"><span data-stu-id="ecfab-278">ICH</span></span> | <span data-ttu-id="ecfab-279">Insertar carácter</span><span class="sxs-lookup"><span data-stu-id="ecfab-279">Insert Character</span></span> | <span data-ttu-id="ecfab-280">Inserte &lt;n&gt; espacios en la posición actual del cursor, desplazando todo el texto existente a la derecha.</span><span class="sxs-lookup"><span data-stu-id="ecfab-280">Insert &lt;n&gt; spaces at the current cursor position, shifting all existing text to the right.</span></span> <span data-ttu-id="ecfab-281">Asimismo, se quita el texto que sale de la pantalla hacia la derecha.</span><span class="sxs-lookup"><span data-stu-id="ecfab-281">Text exiting the screen to the right is removed.</span></span> |
| <span data-ttu-id="ecfab-282">ESC \[ &lt;n&gt; P</span><span class="sxs-lookup"><span data-stu-id="ecfab-282">ESC \[ &lt;n&gt; P</span></span> | <span data-ttu-id="ecfab-283">DCH</span><span class="sxs-lookup"><span data-stu-id="ecfab-283">DCH</span></span> | <span data-ttu-id="ecfab-284">Eliminar carácter</span><span class="sxs-lookup"><span data-stu-id="ecfab-284">Delete Character</span></span> | <span data-ttu-id="ecfab-285">Elimine &lt;n&gt; caracteres en la posición actual del cursor, desplazando los caracteres de espacio desde el borde derecho de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="ecfab-285">Delete &lt;n&gt; characters at the current cursor position, shifting in space characters from the right edge of the screen.</span></span> |
| <span data-ttu-id="ecfab-286">ESC \[ &lt;n&gt; X</span><span class="sxs-lookup"><span data-stu-id="ecfab-286">ESC \[ &lt;n&gt; X</span></span> | <span data-ttu-id="ecfab-287">ECH</span><span class="sxs-lookup"><span data-stu-id="ecfab-287">ECH</span></span> | <span data-ttu-id="ecfab-288">Borrar carácter</span><span class="sxs-lookup"><span data-stu-id="ecfab-288">Erase Character</span></span> | <span data-ttu-id="ecfab-289">Borre &lt;n&gt; caracteres de la posición actual del cursor sobrescribiéndolos con un carácter de espacio.</span><span class="sxs-lookup"><span data-stu-id="ecfab-289">Erase &lt;n&gt; characters from the current cursor position by overwriting them with a space character.</span></span> |
| <span data-ttu-id="ecfab-290">ESC \[ &lt;n&gt; L</span><span class="sxs-lookup"><span data-stu-id="ecfab-290">ESC \[ &lt;n&gt; L</span></span> | <span data-ttu-id="ecfab-291">IL</span><span class="sxs-lookup"><span data-stu-id="ecfab-291">IL</span></span> | <span data-ttu-id="ecfab-292">Insertar línea</span><span class="sxs-lookup"><span data-stu-id="ecfab-292">Insert Line</span></span> | <span data-ttu-id="ecfab-293">Inserta &lt;n&gt; líneas en el búfer en la posición del cursor.</span><span class="sxs-lookup"><span data-stu-id="ecfab-293">Inserts &lt;n&gt; lines into the buffer at the cursor position.</span></span> <span data-ttu-id="ecfab-294">La línea en la que se encuentra el cursor y las líneas que tiene debajo se desplazarán hacia abajo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-294">The line the cursor is on, and lines below it, will be shifted downwards.</span></span> |
| <span data-ttu-id="ecfab-295">ESC \[ &lt;n&gt; M</span><span class="sxs-lookup"><span data-stu-id="ecfab-295">ESC \[ &lt;n&gt; M</span></span> | <span data-ttu-id="ecfab-296">DL</span><span class="sxs-lookup"><span data-stu-id="ecfab-296">DL</span></span> | <span data-ttu-id="ecfab-297">Eliminar línea</span><span class="sxs-lookup"><span data-stu-id="ecfab-297">Delete Line</span></span> | <span data-ttu-id="ecfab-298">Elimina &lt;n&gt; líneas del búfer, comenzando por la fila en la que se encuentra el cursor.</span><span class="sxs-lookup"><span data-stu-id="ecfab-298">Deletes &lt;n&gt; lines from the buffer, starting with the row the cursor is on.</span></span> |



> [!NOTE]
><span data-ttu-id="ecfab-299">En el caso de IL y DL, solo se ven afectadas las líneas de los márgenes de desplazamiento (consulte los márgenes de desplazamiento).</span><span class="sxs-lookup"><span data-stu-id="ecfab-299">For IL and DL, only the lines in the scrolling margins (see Scrolling Margins) are affected.</span></span> <span data-ttu-id="ecfab-300">Si no se establece ningún margen, los bordes de margen predeterminados formarán la ventanilla actual.</span><span class="sxs-lookup"><span data-stu-id="ecfab-300">If no margins are set, the default margin borders are the current viewport.</span></span> <span data-ttu-id="ecfab-301">Si se desplazan las líneas por debajo de los márgenes, estas se descartan.</span><span class="sxs-lookup"><span data-stu-id="ecfab-301">If lines would be shifted below the margins, they are discarded.</span></span> <span data-ttu-id="ecfab-302">Cuando se eliminan líneas, se insertan líneas en blanco en la parte inferior de los márgenes, pero las líneas de fuera de la ventanilla nunca se ven afectadas.</span><span class="sxs-lookup"><span data-stu-id="ecfab-302">When lines are deleted, blank lines are inserted at the bottom of the margins, lines from outside the viewport are never affected.</span></span>

<span data-ttu-id="ecfab-303">Para cada una de las secuencias, el valor predeterminado de &lt;n&gt; es 0 si se omite.</span><span class="sxs-lookup"><span data-stu-id="ecfab-303">For each of the sequences, the default value for &lt;n&gt; if it is omitted is 0.</span></span>



<span data-ttu-id="ecfab-304">En el caso de los siguientes comandos, el parámetro &lt;n&gt; tiene 3 valores válidos:</span><span class="sxs-lookup"><span data-stu-id="ecfab-304">For the following commands, the parameter &lt;n&gt; has 3 valid values:</span></span>

- <span data-ttu-id="ecfab-305">0: borra contenido desde la posición actual del cursor (inclusive) hasta el final de la línea o pantalla.</span><span class="sxs-lookup"><span data-stu-id="ecfab-305">0 erases from the current cursor position (inclusive) to the end of the line/display</span></span>
- <span data-ttu-id="ecfab-306">1: borra contenido desde el principio de la línea o la pantalla hasta la posición actual del cursor (inclusive).</span><span class="sxs-lookup"><span data-stu-id="ecfab-306">1 erases from the beginning of the line/display up to and including the current cursor position</span></span>
- <span data-ttu-id="ecfab-307">2: borra la línea o pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="ecfab-307">2 erases the entire line/display</span></span>


| <span data-ttu-id="ecfab-308">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-308">Sequence</span></span> | <span data-ttu-id="ecfab-309">Código</span><span class="sxs-lookup"><span data-stu-id="ecfab-309">Code</span></span> | <span data-ttu-id="ecfab-310">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-310">Description</span></span> | <span data-ttu-id="ecfab-311">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-311">Behavior</span></span> |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="ecfab-312">ESC \[ &lt;n&gt; J</span><span class="sxs-lookup"><span data-stu-id="ecfab-312">ESC \[ &lt;n&gt; J</span></span> | <span data-ttu-id="ecfab-313">ED</span><span class="sxs-lookup"><span data-stu-id="ecfab-313">ED</span></span> | <span data-ttu-id="ecfab-314">Borrar en pantalla</span><span class="sxs-lookup"><span data-stu-id="ecfab-314">Erase in Display</span></span> | <span data-ttu-id="ecfab-315">Se reemplaza todo el texto de la ventanilla o pantalla actual especificada según &lt;n&gt;, con caracteres de espacio.</span><span class="sxs-lookup"><span data-stu-id="ecfab-315">Replace all text in the current viewport/screen specified by &lt;n&gt; with space characters</span></span> |
| <span data-ttu-id="ecfab-316">ESC \[ &lt;n&gt; K</span><span class="sxs-lookup"><span data-stu-id="ecfab-316">ESC \[ &lt;n&gt; K</span></span> | <span data-ttu-id="ecfab-317">EL</span><span class="sxs-lookup"><span data-stu-id="ecfab-317">EL</span></span> | <span data-ttu-id="ecfab-318">Borrar en línea</span><span class="sxs-lookup"><span data-stu-id="ecfab-318">Erase in Line</span></span> | <span data-ttu-id="ecfab-319">Se reemplaza todo el texto de la línea con el cursor especificado según &lt;n&gt;, con caracteres de espacio.</span><span class="sxs-lookup"><span data-stu-id="ecfab-319">Replace all text on the line with the cursor specified by &lt;n&gt; with space characters</span></span> |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span data-ttu-id="ecfab-320"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Formato de texto</span><span class="sxs-lookup"><span data-stu-id="ecfab-320"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Text Formatting</span></span>


<span data-ttu-id="ecfab-321">Todos los comandos de esta sección suelen ser equivalentes a llamar a la API de consola [**SetConsoleTextAttribute**](setconsoletextattribute.md) para ajustar el formato de todas las escrituras futuras que se realicen en el búfer de texto de la salida de consola.</span><span class="sxs-lookup"><span data-stu-id="ecfab-321">All commands in this section are generally equivalent to calling [**SetConsoleTextAttribute**](setconsoletextattribute.md) console APIs to adjust the formatting of all future writes to the console output text buffer.</span></span>

<span data-ttu-id="ecfab-322">Este comando es especial, ya que la posición &lt;n&gt; siguiente puede aceptar entre 0 y 16 parámetros separados por puntos y comas.</span><span class="sxs-lookup"><span data-stu-id="ecfab-322">This command is special in that the &lt;n&gt; position below can accept between 0 and 16 parameters separated by semicolons.</span></span>

<span data-ttu-id="ecfab-323">Cuando no se especifican parámetros, este valor se administra igual que un solo parámetro 0.</span><span class="sxs-lookup"><span data-stu-id="ecfab-323">When no parameters are specified, it is treated the same as a single 0 parameter.</span></span>


| <span data-ttu-id="ecfab-324">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-324">Sequence</span></span> | <span data-ttu-id="ecfab-325">Código</span><span class="sxs-lookup"><span data-stu-id="ecfab-325">Code</span></span> | <span data-ttu-id="ecfab-326">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-326">Description</span></span> | <span data-ttu-id="ecfab-327">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-327">Behavior</span></span> |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| <span data-ttu-id="ecfab-328">ESC \[ &lt;n&gt; m</span><span class="sxs-lookup"><span data-stu-id="ecfab-328">ESC \[ &lt;n&gt; m</span></span> | <span data-ttu-id="ecfab-329">SGR</span><span class="sxs-lookup"><span data-stu-id="ecfab-329">SGR</span></span> | <span data-ttu-id="ecfab-330">Establecer representaciones de gráficos</span><span class="sxs-lookup"><span data-stu-id="ecfab-330">Set Graphics Rendition</span></span> | <span data-ttu-id="ecfab-331">Se establece el formato de la pantalla y el texto tal como se especifica en &lt;n&gt;.</span><span class="sxs-lookup"><span data-stu-id="ecfab-331">Set the format of the screen and text as specified by &lt;n&gt;</span></span> |



<span data-ttu-id="ecfab-332">La siguiente tabla de valores se puede usar en &lt;n&gt; para representar diferentes modos de formato.</span><span class="sxs-lookup"><span data-stu-id="ecfab-332">The following table of values can be used in &lt;n&gt; to represent different formatting modes.</span></span>

<span data-ttu-id="ecfab-333">Recuerde que los modos de formato se aplican de izquierda a derecha.</span><span class="sxs-lookup"><span data-stu-id="ecfab-333">Formatting modes are applied from left to right.</span></span> <span data-ttu-id="ecfab-334">Si aplica opciones de formato paralelas, la opción que esté más a la derecha tendrá prioridad.</span><span class="sxs-lookup"><span data-stu-id="ecfab-334">Applying competing formatting options will result in the right-most option taking precedence.</span></span>

<span data-ttu-id="ecfab-335">En el caso de las opciones que especifican colores, se usarán los colores tal y como se define en la tabla de colores de la consola; estos que se pueden modificar con la API [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md).</span><span class="sxs-lookup"><span data-stu-id="ecfab-335">For options that specify colors, the colors will be used as defined in the console color table which can be modified using the [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) API.</span></span> <span data-ttu-id="ecfab-336">Si se modifica la tabla para que la posición "azul" de la tabla muestre un tono RGB rojo, todas las llamadas de tipo **Primer plano azul** mostrarán el color rojo hasta que las cambie.</span><span class="sxs-lookup"><span data-stu-id="ecfab-336">If the table is modified to make the “blue” position in the table display an RGB shade of red, then all calls to **Foreground Blue** will display that red color until otherwise changed.</span></span>


| <span data-ttu-id="ecfab-337">Valor</span><span class="sxs-lookup"><span data-stu-id="ecfab-337">Value</span></span> | <span data-ttu-id="ecfab-338">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-338">Description</span></span> | <span data-ttu-id="ecfab-339">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-339">Behavior</span></span> |
|-------|---------------------------|--------------------------------------------------------------------|
| <span data-ttu-id="ecfab-340">0</span><span class="sxs-lookup"><span data-stu-id="ecfab-340">0</span></span> | <span data-ttu-id="ecfab-341">Predeterminado</span><span class="sxs-lookup"><span data-stu-id="ecfab-341">Default</span></span> | <span data-ttu-id="ecfab-342">Devuelve todos los atributos al estado predeterminado antes de la modificación.</span><span class="sxs-lookup"><span data-stu-id="ecfab-342">Returns all attributes to the default state prior to modification</span></span> |
| <span data-ttu-id="ecfab-343">1</span><span class="sxs-lookup"><span data-stu-id="ecfab-343">1</span></span> | <span data-ttu-id="ecfab-344">Negrita/Brillo</span><span class="sxs-lookup"><span data-stu-id="ecfab-344">Bold/Bright</span></span> | <span data-ttu-id="ecfab-345">Aplica la marca de brillo o intensidad al color del primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-345">Applies brightness/intensity flag to foreground color</span></span> |
| <span data-ttu-id="ecfab-346">4</span><span class="sxs-lookup"><span data-stu-id="ecfab-346">4</span></span> | <span data-ttu-id="ecfab-347">Subrayado</span><span class="sxs-lookup"><span data-stu-id="ecfab-347">Underline</span></span> | <span data-ttu-id="ecfab-348">Agrega un subrayado.</span><span class="sxs-lookup"><span data-stu-id="ecfab-348">Adds underline</span></span> |
| <span data-ttu-id="ecfab-349">24</span><span class="sxs-lookup"><span data-stu-id="ecfab-349">24</span></span> | <span data-ttu-id="ecfab-350">Sin subrayado</span><span class="sxs-lookup"><span data-stu-id="ecfab-350">No underline</span></span> | <span data-ttu-id="ecfab-351">Quita el subrayado.</span><span class="sxs-lookup"><span data-stu-id="ecfab-351">Removes underline</span></span> |
| <span data-ttu-id="ecfab-352">7</span><span class="sxs-lookup"><span data-stu-id="ecfab-352">7</span></span> | <span data-ttu-id="ecfab-353">Negativo</span><span class="sxs-lookup"><span data-stu-id="ecfab-353">Negative</span></span> | <span data-ttu-id="ecfab-354">Intercambia los colores de primer plano y de fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-354">Swaps foreground and background colors</span></span> |
| <span data-ttu-id="ecfab-355">27</span><span class="sxs-lookup"><span data-stu-id="ecfab-355">27</span></span> | <span data-ttu-id="ecfab-356">Positivo (sin negativo)</span><span class="sxs-lookup"><span data-stu-id="ecfab-356">Positive (No negative)</span></span> | <span data-ttu-id="ecfab-357">Devuelve el primer plano y el fondo a su estado normal.</span><span class="sxs-lookup"><span data-stu-id="ecfab-357">Returns foreground/background to normal</span></span> |
| <span data-ttu-id="ecfab-358">30</span><span class="sxs-lookup"><span data-stu-id="ecfab-358">30</span></span> | <span data-ttu-id="ecfab-359">Primer plano negro</span><span class="sxs-lookup"><span data-stu-id="ecfab-359">Foreground Black</span></span> | <span data-ttu-id="ecfab-360">Aplica un color negro brillante y sin negrita al primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-360">Applies non-bold/bright black to foreground</span></span> |
| <span data-ttu-id="ecfab-361">31</span><span class="sxs-lookup"><span data-stu-id="ecfab-361">31</span></span> | <span data-ttu-id="ecfab-362">Primer plano rojo</span><span class="sxs-lookup"><span data-stu-id="ecfab-362">Foreground Red</span></span> | <span data-ttu-id="ecfab-363">Aplica un color rojo brillante y sin negrita al primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-363">Applies non-bold/bright red to foreground</span></span> |
| <span data-ttu-id="ecfab-364">32</span><span class="sxs-lookup"><span data-stu-id="ecfab-364">32</span></span> | <span data-ttu-id="ecfab-365">Primer plano verde</span><span class="sxs-lookup"><span data-stu-id="ecfab-365">Foreground Green</span></span> | <span data-ttu-id="ecfab-366">Aplica un color verde brillante y sin negrita al primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-366">Applies non-bold/bright green to foreground</span></span> |
| <span data-ttu-id="ecfab-367">33</span><span class="sxs-lookup"><span data-stu-id="ecfab-367">33</span></span> | <span data-ttu-id="ecfab-368">Primer plano amarillo</span><span class="sxs-lookup"><span data-stu-id="ecfab-368">Foreground Yellow</span></span> | <span data-ttu-id="ecfab-369">Aplica un color amarillo brillante y sin negrita al primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-369">Applies non-bold/bright yellow to foreground</span></span> |
| <span data-ttu-id="ecfab-370">34</span><span class="sxs-lookup"><span data-stu-id="ecfab-370">34</span></span> | <span data-ttu-id="ecfab-371">Primer plano azul</span><span class="sxs-lookup"><span data-stu-id="ecfab-371">Foreground Blue</span></span> | <span data-ttu-id="ecfab-372">Aplica un color azul brillante y sin negrita al primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-372">Applies non-bold/bright blue to foreground</span></span> |
| <span data-ttu-id="ecfab-373">35</span><span class="sxs-lookup"><span data-stu-id="ecfab-373">35</span></span> | <span data-ttu-id="ecfab-374">Primer plano magenta</span><span class="sxs-lookup"><span data-stu-id="ecfab-374">Foreground Magenta</span></span> | <span data-ttu-id="ecfab-375">Aplica un color magenta brillante y sin negrita al primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-375">Applies non-bold/bright magenta to foreground</span></span> |
| <span data-ttu-id="ecfab-376">36</span><span class="sxs-lookup"><span data-stu-id="ecfab-376">36</span></span> | <span data-ttu-id="ecfab-377">Primer plano cian</span><span class="sxs-lookup"><span data-stu-id="ecfab-377">Foreground Cyan</span></span> | <span data-ttu-id="ecfab-378">Aplica un color cian brillante y sin negrita al primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-378">Applies non-bold/bright cyan to foreground</span></span> |
| <span data-ttu-id="ecfab-379">37</span><span class="sxs-lookup"><span data-stu-id="ecfab-379">37</span></span> | <span data-ttu-id="ecfab-380">Primer plano blanco</span><span class="sxs-lookup"><span data-stu-id="ecfab-380">Foreground White</span></span> | <span data-ttu-id="ecfab-381">Aplica un color blanco brillante y sin negrita al primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-381">Applies non-bold/bright white to foreground</span></span> |
| <span data-ttu-id="ecfab-382">38</span><span class="sxs-lookup"><span data-stu-id="ecfab-382">38</span></span> | <span data-ttu-id="ecfab-383">Primer plano extendido</span><span class="sxs-lookup"><span data-stu-id="ecfab-383">Foreground Extended</span></span> | <span data-ttu-id="ecfab-384">Aplica el valor del color extendido al primer plano (consulte los detalles a continuación).</span><span class="sxs-lookup"><span data-stu-id="ecfab-384">Applies extended color value to the foreground (see details below)</span></span> |
| <span data-ttu-id="ecfab-385">39</span><span class="sxs-lookup"><span data-stu-id="ecfab-385">39</span></span> | <span data-ttu-id="ecfab-386">Valor predeterminado del primer plano</span><span class="sxs-lookup"><span data-stu-id="ecfab-386">Foreground Default</span></span> | <span data-ttu-id="ecfab-387">Aplica solo la parte del primer plano que corresponde a los valores predeterminados (consulte 0).</span><span class="sxs-lookup"><span data-stu-id="ecfab-387">Applies only the foreground portion of the defaults (see 0)</span></span> |
| <span data-ttu-id="ecfab-388">40</span><span class="sxs-lookup"><span data-stu-id="ecfab-388">40</span></span> | <span data-ttu-id="ecfab-389">Fondo negro</span><span class="sxs-lookup"><span data-stu-id="ecfab-389">Background Black</span></span> | <span data-ttu-id="ecfab-390">Aplica un color negro brillante y sin negrita al fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-390">Applies non-bold/bright black to background</span></span> |
| <span data-ttu-id="ecfab-391">41</span><span class="sxs-lookup"><span data-stu-id="ecfab-391">41</span></span> | <span data-ttu-id="ecfab-392">Fondo rojo</span><span class="sxs-lookup"><span data-stu-id="ecfab-392">Background Red</span></span> | <span data-ttu-id="ecfab-393">Aplica un color rojo brillante y sin negrita al fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-393">Applies non-bold/bright red to background</span></span> |
| <span data-ttu-id="ecfab-394">42</span><span class="sxs-lookup"><span data-stu-id="ecfab-394">42</span></span> | <span data-ttu-id="ecfab-395">Fondo verde</span><span class="sxs-lookup"><span data-stu-id="ecfab-395">Background Green</span></span> | <span data-ttu-id="ecfab-396">Aplica un color verde brillante y sin negrita al fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-396">Applies non-bold/bright green to background</span></span> |
| <span data-ttu-id="ecfab-397">43</span><span class="sxs-lookup"><span data-stu-id="ecfab-397">43</span></span> | <span data-ttu-id="ecfab-398">Fondo amarillo</span><span class="sxs-lookup"><span data-stu-id="ecfab-398">Background Yellow</span></span> | <span data-ttu-id="ecfab-399">Aplica un color amarillo brillante y sin negrita al fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-399">Applies non-bold/bright yellow to background</span></span> |
| <span data-ttu-id="ecfab-400">44</span><span class="sxs-lookup"><span data-stu-id="ecfab-400">44</span></span> | <span data-ttu-id="ecfab-401">Fondo azul</span><span class="sxs-lookup"><span data-stu-id="ecfab-401">Background Blue</span></span> | <span data-ttu-id="ecfab-402">Aplica un color azul brillante y sin negrita al fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-402">Applies non-bold/bright blue to background</span></span> |
| <span data-ttu-id="ecfab-403">45</span><span class="sxs-lookup"><span data-stu-id="ecfab-403">45</span></span> | <span data-ttu-id="ecfab-404">Fondo magenta</span><span class="sxs-lookup"><span data-stu-id="ecfab-404">Background Magenta</span></span> | <span data-ttu-id="ecfab-405">Aplica un color magenta brillante y sin negrita al fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-405">Applies non-bold/bright magenta to background</span></span> |
| <span data-ttu-id="ecfab-406">46</span><span class="sxs-lookup"><span data-stu-id="ecfab-406">46</span></span> | <span data-ttu-id="ecfab-407">Fondo cian</span><span class="sxs-lookup"><span data-stu-id="ecfab-407">Background Cyan</span></span> | <span data-ttu-id="ecfab-408">Aplica un color cian brillante y sin negrita al fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-408">Applies non-bold/bright cyan to background</span></span> |
| <span data-ttu-id="ecfab-409">47</span><span class="sxs-lookup"><span data-stu-id="ecfab-409">47</span></span> | <span data-ttu-id="ecfab-410">Fondo blanco</span><span class="sxs-lookup"><span data-stu-id="ecfab-410">Background White</span></span> | <span data-ttu-id="ecfab-411">Aplica un color blanco brillante y sin negrita al fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-411">Applies non-bold/bright white to background</span></span> |
| <span data-ttu-id="ecfab-412">48</span><span class="sxs-lookup"><span data-stu-id="ecfab-412">48</span></span> | <span data-ttu-id="ecfab-413">Fondo extendido</span><span class="sxs-lookup"><span data-stu-id="ecfab-413">Background Extended</span></span> | <span data-ttu-id="ecfab-414">Aplica el valor del color extendido al fondo (consulte los detalles a continuación).</span><span class="sxs-lookup"><span data-stu-id="ecfab-414">Applies extended color value to the background (see details below)</span></span> |
| <span data-ttu-id="ecfab-415">49</span><span class="sxs-lookup"><span data-stu-id="ecfab-415">49</span></span> | <span data-ttu-id="ecfab-416">Fondo predeterminado</span><span class="sxs-lookup"><span data-stu-id="ecfab-416">Background Default</span></span> | <span data-ttu-id="ecfab-417">Aplica solo la parte del fondo que corresponde a los valores predeterminados (consulte 0).</span><span class="sxs-lookup"><span data-stu-id="ecfab-417">Applies only the background portion of the defaults (see 0)</span></span> |
| <span data-ttu-id="ecfab-418">90</span><span class="sxs-lookup"><span data-stu-id="ecfab-418">90</span></span> | <span data-ttu-id="ecfab-419">Primer plano negro brillante</span><span class="sxs-lookup"><span data-stu-id="ecfab-419">Bright Foreground Black</span></span> | <span data-ttu-id="ecfab-420">Aplica un color negro brillante y con negrita al primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-420">Applies bold/bright black to foreground</span></span> |
| <span data-ttu-id="ecfab-421">91</span><span class="sxs-lookup"><span data-stu-id="ecfab-421">91</span></span> | <span data-ttu-id="ecfab-422">Primer plano rojo brillante</span><span class="sxs-lookup"><span data-stu-id="ecfab-422">Bright Foreground Red</span></span> | <span data-ttu-id="ecfab-423">Aplica un color rojo brillante y con negrita al primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-423">Applies bold/bright red to foreground</span></span> |
| <span data-ttu-id="ecfab-424">92</span><span class="sxs-lookup"><span data-stu-id="ecfab-424">92</span></span> | <span data-ttu-id="ecfab-425">Primer plano verde brillante</span><span class="sxs-lookup"><span data-stu-id="ecfab-425">Bright Foreground Green</span></span> | <span data-ttu-id="ecfab-426">Aplica un color verde brillante y con negrita al primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-426">Applies bold/bright green to foreground</span></span> |
| <span data-ttu-id="ecfab-427">93</span><span class="sxs-lookup"><span data-stu-id="ecfab-427">93</span></span> | <span data-ttu-id="ecfab-428">Primer plano amarillo brillante</span><span class="sxs-lookup"><span data-stu-id="ecfab-428">Bright Foreground Yellow</span></span> | <span data-ttu-id="ecfab-429">Aplica un color amarillo brillante y con negrita al primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-429">Applies bold/bright yellow to foreground</span></span> |
| <span data-ttu-id="ecfab-430">94</span><span class="sxs-lookup"><span data-stu-id="ecfab-430">94</span></span> | <span data-ttu-id="ecfab-431">Primer plano azul brillante</span><span class="sxs-lookup"><span data-stu-id="ecfab-431">Bright Foreground Blue</span></span> | <span data-ttu-id="ecfab-432">Aplica un color azul brillante y con negrita al primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-432">Applies bold/bright blue to foreground</span></span> |
| <span data-ttu-id="ecfab-433">95</span><span class="sxs-lookup"><span data-stu-id="ecfab-433">95</span></span> | <span data-ttu-id="ecfab-434">Primer plano magenta brillante</span><span class="sxs-lookup"><span data-stu-id="ecfab-434">Bright Foreground Magenta</span></span> | <span data-ttu-id="ecfab-435">Aplica un color magenta brillante y con negrita al primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-435">Applies bold/bright magenta to foreground</span></span> |
| <span data-ttu-id="ecfab-436">96</span><span class="sxs-lookup"><span data-stu-id="ecfab-436">96</span></span> | <span data-ttu-id="ecfab-437">Primer plano cian brillante</span><span class="sxs-lookup"><span data-stu-id="ecfab-437">Bright Foreground Cyan</span></span> | <span data-ttu-id="ecfab-438">Aplica un color cian brillante y con negrita al primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-438">Applies bold/bright cyan to foreground</span></span> |
| <span data-ttu-id="ecfab-439">97</span><span class="sxs-lookup"><span data-stu-id="ecfab-439">97</span></span> | <span data-ttu-id="ecfab-440">Primer plano blanco brillante</span><span class="sxs-lookup"><span data-stu-id="ecfab-440">Bright Foreground White</span></span> | <span data-ttu-id="ecfab-441">Aplica un color blanco brillante y con negrita al primer plano.</span><span class="sxs-lookup"><span data-stu-id="ecfab-441">Applies bold/bright white to foreground</span></span> |
| <span data-ttu-id="ecfab-442">100</span><span class="sxs-lookup"><span data-stu-id="ecfab-442">100</span></span> | <span data-ttu-id="ecfab-443">Fondo negro brillante</span><span class="sxs-lookup"><span data-stu-id="ecfab-443">Bright Background Black</span></span> | <span data-ttu-id="ecfab-444">Aplica un color negro brillante y con negrita al fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-444">Applies bold/bright black to background</span></span> |
| <span data-ttu-id="ecfab-445">101</span><span class="sxs-lookup"><span data-stu-id="ecfab-445">101</span></span> | <span data-ttu-id="ecfab-446">Fondo rojo brillante</span><span class="sxs-lookup"><span data-stu-id="ecfab-446">Bright Background Red</span></span> | <span data-ttu-id="ecfab-447">Aplica un color rojo brillante y con negrita al fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-447">Applies bold/bright red to background</span></span> |
| <span data-ttu-id="ecfab-448">102</span><span class="sxs-lookup"><span data-stu-id="ecfab-448">102</span></span> | <span data-ttu-id="ecfab-449">Fondo verde brillante</span><span class="sxs-lookup"><span data-stu-id="ecfab-449">Bright Background Green</span></span> | <span data-ttu-id="ecfab-450">Aplica un color verde brillante y con negrita al fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-450">Applies bold/bright green to background</span></span> |
| <span data-ttu-id="ecfab-451">103</span><span class="sxs-lookup"><span data-stu-id="ecfab-451">103</span></span> | <span data-ttu-id="ecfab-452">Fondo amarillo brillante</span><span class="sxs-lookup"><span data-stu-id="ecfab-452">Bright Background Yellow</span></span> | <span data-ttu-id="ecfab-453">Aplica un color amarillo brillante y con negrita al fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-453">Applies bold/bright yellow to background</span></span> |
| <span data-ttu-id="ecfab-454">104</span><span class="sxs-lookup"><span data-stu-id="ecfab-454">104</span></span> | <span data-ttu-id="ecfab-455">Fondo azul brillante</span><span class="sxs-lookup"><span data-stu-id="ecfab-455">Bright Background Blue</span></span> | <span data-ttu-id="ecfab-456">Aplica un color azul brillante y con negrita al fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-456">Applies bold/bright blue to background</span></span> |
| <span data-ttu-id="ecfab-457">105</span><span class="sxs-lookup"><span data-stu-id="ecfab-457">105</span></span> | <span data-ttu-id="ecfab-458">Fondo magenta brillante</span><span class="sxs-lookup"><span data-stu-id="ecfab-458">Bright Background Magenta</span></span> | <span data-ttu-id="ecfab-459">Aplica un color magenta brillante y con negrita al fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-459">Applies bold/bright magenta to background</span></span> |
| <span data-ttu-id="ecfab-460">106</span><span class="sxs-lookup"><span data-stu-id="ecfab-460">106</span></span> | <span data-ttu-id="ecfab-461">Fondo cian brillante</span><span class="sxs-lookup"><span data-stu-id="ecfab-461">Bright Background Cyan</span></span> | <span data-ttu-id="ecfab-462">Aplica un color cian brillante y con negrita al fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-462">Applies bold/bright cyan to background</span></span> |
| <span data-ttu-id="ecfab-463">107</span><span class="sxs-lookup"><span data-stu-id="ecfab-463">107</span></span> | <span data-ttu-id="ecfab-464">Fondo blanco brillante</span><span class="sxs-lookup"><span data-stu-id="ecfab-464">Bright Background White</span></span> | <span data-ttu-id="ecfab-465">Aplica un color blanco brillante y con negrita al fondo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-465">Applies bold/bright white to background</span></span> |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span data-ttu-id="ecfab-466"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Colores extendidos</span><span class="sxs-lookup"><span data-stu-id="ecfab-466"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Extended Colors</span></span>

<span data-ttu-id="ecfab-467">Algunos emuladores de terminal virtuales admiten una paleta que cuenta con más colores que los 16 colores que proporciona la consola de Windows.</span><span class="sxs-lookup"><span data-stu-id="ecfab-467">Some virtual terminal emulators support a palette of colors greater than the 16 colors provided by the Windows Console.</span></span> <span data-ttu-id="ecfab-468">Al usar estos colores extendidos, la consola de Windows elegirá en la tabla de 16 colores existente el color que más se acerque a su elección y lo mostrará.</span><span class="sxs-lookup"><span data-stu-id="ecfab-468">For these extended colors, the Windows Console will choose the nearest appropriate color from the existing 16 color table for display.</span></span> <span data-ttu-id="ecfab-469">A diferencia de los valores de SGR típicos anteriores, los valores extendidos consumirán parámetros adicionales después del indicador inicial, según la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="ecfab-469">Unlike typical SGR values above, the extended values will consume additional parameters after the initial indicator according to the table below.</span></span>


| <span data-ttu-id="ecfab-470">Subsecuencia SGR</span><span class="sxs-lookup"><span data-stu-id="ecfab-470">SGR Subsequence</span></span> | <span data-ttu-id="ecfab-471">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-471">Description</span></span> |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="ecfab-472">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="ecfab-472">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="ecfab-473">Permite establecer el color del primer plano a un valor RGB especificado en los parámetros &lt;r&gt;, &lt;g&gt;, &lt;b&gt;\*.</span><span class="sxs-lookup"><span data-stu-id="ecfab-473">Set foreground color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="ecfab-474">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="ecfab-474">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="ecfab-475">Permite establecer el color del fondo a un valor RGB especificado en los parámetros &lt;r&gt;, &lt;g&gt;, &lt;b&gt;\*.</span><span class="sxs-lookup"><span data-stu-id="ecfab-475">Set background color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="ecfab-476">38 ; 5 ; &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="ecfab-476">38 ; 5 ; &lt;s&gt;</span></span> | <span data-ttu-id="ecfab-477">Permite establecer el color del primer plano en el índice &lt;s&gt; en la tabla de 88 o 256 colores\*.</span><span class="sxs-lookup"><span data-stu-id="ecfab-477">Set foreground color to &lt;s&gt; index in 88 or 256 color table\*</span></span> |
| <span data-ttu-id="ecfab-478">48 ; 5 ; &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="ecfab-478">48 ; 5 ; &lt;s&gt;</span></span> | <span data-ttu-id="ecfab-479">Permite establecer el color del fondo en el índice &lt;s&gt; en la tabla de 88 o 256 colores\*.</span><span class="sxs-lookup"><span data-stu-id="ecfab-479">Set background color to &lt;s&gt; index in 88 or 256 color table\*</span></span> |



<span data-ttu-id="ecfab-480">\*Las paletas de 88 y 256 colores que se mantienen de forma interna para la comparación se basan en el emulador de terminal xterm.</span><span class="sxs-lookup"><span data-stu-id="ecfab-480">\*The 88 and 256 color palettes maintained internally for comparison are based from the xterm terminal emulator.</span></span> <span data-ttu-id="ecfab-481">Las tablas de comparación o redondeo no se pueden modificar en este momento.</span><span class="sxs-lookup"><span data-stu-id="ecfab-481">The comparison/rounding tables cannot be modified at this time.</span></span>


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span data-ttu-id="ecfab-482"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Colores de pantalla</span><span class="sxs-lookup"><span data-stu-id="ecfab-482"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Screen Colors</span></span>


<span data-ttu-id="ecfab-483">El siguiente comando permite que la aplicación establezca los valores de la paleta de colores de la pantalla en cualquier valor RGB.</span><span class="sxs-lookup"><span data-stu-id="ecfab-483">The following command allows the application to set the screen colors palette values to any RGB value.</span></span>

<span data-ttu-id="ecfab-484">Los valores RGB deben ser valores hexadecimales entre `0` y `ff`, y están separados por el carácter de barra diagonal (por ejemplo, `rgb:1/24/86`).</span><span class="sxs-lookup"><span data-stu-id="ecfab-484">The RGB values should be hexadecimal values between `0` and `ff`, and separated by the forward-slash character (e.g. `rgb:1/24/86`).</span></span>

<span data-ttu-id="ecfab-485">Tenga en cuenta que esta secuencia es una secuencia OSC de tipo "comando del sistema operativo" y no un elemento CSI como muchas de las otras secuencias enumeradas; asimismo, esta secuencia comienza por "\\x1b\]" y no por "\\x1b\[".</span><span class="sxs-lookup"><span data-stu-id="ecfab-485">Note that this sequence is an OSC “Operating system command” sequence, and not a CSI like many of the other sequences listed, and as such start with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="ecfab-486">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-486">Sequence</span></span> | <span data-ttu-id="ecfab-487">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-487">Description</span></span> | <span data-ttu-id="ecfab-488">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-488">Behavior</span></span> |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ecfab-489">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span><span class="sxs-lookup"><span data-stu-id="ecfab-489">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span></span> | <span data-ttu-id="ecfab-490">Modificar los colores de la pantalla</span><span class="sxs-lookup"><span data-stu-id="ecfab-490">Modify Screen Colors</span></span> | <span data-ttu-id="ecfab-491">Establece el índice &lt;i&gt; de la paleta de colores de la pantalla a los valores RGB especificados en &lt;r&gt;, &lt;g&gt;, &lt;b&gt;.</span><span class="sxs-lookup"><span data-stu-id="ecfab-491">Sets the screen color palette index &lt;i&gt; to the RGB values specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt;</span></span> |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span data-ttu-id="ecfab-492"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Cambios de modo</span><span class="sxs-lookup"><span data-stu-id="ecfab-492"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Mode Changes</span></span>


<span data-ttu-id="ecfab-493">Estas secuencias controlan los modos de entrada.</span><span class="sxs-lookup"><span data-stu-id="ecfab-493">These are sequences that control the input modes.</span></span> <span data-ttu-id="ecfab-494">Existen dos conjuntos diferentes de modos de entrada: el modo de teclas del cursor y el modo de teclas del teclado.</span><span class="sxs-lookup"><span data-stu-id="ecfab-494">There are two different sets of input modes, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="ecfab-495">El modo de teclas del cursor controla las secuencias que emiten las teclas de dirección, así como el inicio y el final, mientras que el modo de teclas del teclado controla principalmente las secuencias que emiten las teclas en el teclado numérico, así como las teclas de función.</span><span class="sxs-lookup"><span data-stu-id="ecfab-495">The Cursor Keys Mode controls the sequences that are emitted by the arrow keys as well as Home and End, while the Keypad Keys Mode controls the sequences emitted by the keys on the numpad primarily, as well as the function keys.</span></span>

<span data-ttu-id="ecfab-496">Cada uno de estos modos es una configuración booleana simple; esto es, el modo de teclas del cursor puede ser de tipo "normal" (predeterminado) o de tipo "aplicación", y el modo de teclas del teclado puede ser de tipo "numérico" (predeterminado) o de tipo "aplicación".</span><span class="sxs-lookup"><span data-stu-id="ecfab-496">Each of these modes are simple boolean settings – the Cursor Keys Mode is either Normal (default) or Application, and the Keypad Keys Mode is either Numeric (default) or Application.</span></span>

<span data-ttu-id="ecfab-497">Consulte las secciones acerca de las teclas del cursor y las teclas numéricas y de función, para conocer las secuencias emitidas en estos modos.</span><span class="sxs-lookup"><span data-stu-id="ecfab-497">See the Cursor Keys and Numpad & Function Keys sections for the sequences emitted in these modes.</span></span>


| <span data-ttu-id="ecfab-498">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-498">Sequence</span></span> | <span data-ttu-id="ecfab-499">Código</span><span class="sxs-lookup"><span data-stu-id="ecfab-499">Code</span></span> | <span data-ttu-id="ecfab-500">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-500">Description</span></span> | <span data-ttu-id="ecfab-501">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-501">Behavior</span></span> |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| <span data-ttu-id="ecfab-502">ESC =</span><span class="sxs-lookup"><span data-stu-id="ecfab-502">ESC =</span></span> | <span data-ttu-id="ecfab-503">DECKPAM</span><span class="sxs-lookup"><span data-stu-id="ecfab-503">DECKPAM</span></span> | <span data-ttu-id="ecfab-504">Permite habilitar el modo de aplicación del teclado.</span><span class="sxs-lookup"><span data-stu-id="ecfab-504">Enable Keypad Application Mode</span></span> | <span data-ttu-id="ecfab-505">Las teclas del teclado emitirán sus secuencias en el modo de aplicación.</span><span class="sxs-lookup"><span data-stu-id="ecfab-505">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="ecfab-506">ESC &gt;</span><span class="sxs-lookup"><span data-stu-id="ecfab-506">ESC &gt;</span></span> | <span data-ttu-id="ecfab-507">DECKPNM</span><span class="sxs-lookup"><span data-stu-id="ecfab-507">DECKPNM</span></span> | <span data-ttu-id="ecfab-508">Permite habilitar el modo numérico del teclado</span><span class="sxs-lookup"><span data-stu-id="ecfab-508">Enable Keypad Numeric Mode</span></span> | <span data-ttu-id="ecfab-509">Las teclas del teclado emitirán sus secuencias en el modo numérico.</span><span class="sxs-lookup"><span data-stu-id="ecfab-509">Keypad keys will emit their Numeric Mode sequences.</span></span> |
| <span data-ttu-id="ecfab-510">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="ecfab-510">ESC \[ ?</span></span> <span data-ttu-id="ecfab-511">1 h</span><span class="sxs-lookup"><span data-stu-id="ecfab-511">1 h</span></span> | <span data-ttu-id="ecfab-512">DECCKM</span><span class="sxs-lookup"><span data-stu-id="ecfab-512">DECCKM</span></span> | <span data-ttu-id="ecfab-513">Permite habilitar el modo de aplicación de las teclas del cursor.</span><span class="sxs-lookup"><span data-stu-id="ecfab-513">Enable Cursor Keys Application Mode</span></span> | <span data-ttu-id="ecfab-514">Las teclas del teclado emitirán sus secuencias en el modo de aplicación.</span><span class="sxs-lookup"><span data-stu-id="ecfab-514">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="ecfab-515">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="ecfab-515">ESC \[ ?</span></span> <span data-ttu-id="ecfab-516">1 l</span><span class="sxs-lookup"><span data-stu-id="ecfab-516">1 l</span></span> | <span data-ttu-id="ecfab-517">DECCKM</span><span class="sxs-lookup"><span data-stu-id="ecfab-517">DECCKM</span></span> | <span data-ttu-id="ecfab-518">Permite deshabilitar el modo de aplicación de las teclas del cursor (esto es, permite usar el modo normal).</span><span class="sxs-lookup"><span data-stu-id="ecfab-518">Disable Cursor Keys Application Mode (use Normal Mode)</span></span> | <span data-ttu-id="ecfab-519">Las teclas del teclado emitirán sus secuencias en el modo numérico.</span><span class="sxs-lookup"><span data-stu-id="ecfab-519">Keypad keys will emit their Numeric Mode sequences.</span></span> |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span data-ttu-id="ecfab-520"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Estado de la consulta</span><span class="sxs-lookup"><span data-stu-id="ecfab-520"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Query State</span></span>


<span data-ttu-id="ecfab-521">Todos los comandos de esta sección suelen ser equivalentes a llamar a la API de la consola Get\* para recuperar información sobre el estado actual del búfer de la consola.</span><span class="sxs-lookup"><span data-stu-id="ecfab-521">All commands in this section are generally equivalent to calling Get\* console APIs to retrieve status information about the current console buffer state.</span></span>

> [!NOTE]
><span data-ttu-id="ecfab-522">Estas consultas emitirán sus respuestas en el flujo de entrada de la consola inmediatamente después de que se reconozcan en el flujo de salida mientras se establece la marca ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING.</span><span class="sxs-lookup"><span data-stu-id="ecfab-522">These queries will emit their responses into the console input stream immediately after being recognized on the output stream while ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING is set.</span></span> <span data-ttu-id="ecfab-523">La marca ENABLE\_VIRTUAL\_TERMINAL\_INPUT no se aplica a los comandos de la consulta, ya que se supone que una aplicación que realiza la consulta siempre querrá recibir la respuesta.</span><span class="sxs-lookup"><span data-stu-id="ecfab-523">The ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag does not apply to query commands as it is assumed that an application making the query will always want to receive the reply.</span></span>




| <span data-ttu-id="ecfab-524">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-524">Sequence</span></span> | <span data-ttu-id="ecfab-525">Código</span><span class="sxs-lookup"><span data-stu-id="ecfab-525">Code</span></span> | <span data-ttu-id="ecfab-526">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-526">Description</span></span> | <span data-ttu-id="ecfab-527">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-527">Behavior</span></span> |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ecfab-528">ESC \[ 6 n</span><span class="sxs-lookup"><span data-stu-id="ecfab-528">ESC \[ 6 n</span></span> | <span data-ttu-id="ecfab-529">DECXCPR</span><span class="sxs-lookup"><span data-stu-id="ecfab-529">DECXCPR</span></span> | <span data-ttu-id="ecfab-530">Indicar la posición del cursor</span><span class="sxs-lookup"><span data-stu-id="ecfab-530">Report Cursor Position</span></span> | <span data-ttu-id="ecfab-531">Emite la posición del cursor como: ESC \[ &lt;r&gt; ; &lt;c&gt; R, donde &lt;r&gt; = fila del cursor y &lt;c&gt; = columna del cursor.</span><span class="sxs-lookup"><span data-stu-id="ecfab-531">Emit the cursor position as: ESC \[ &lt;r&gt; ; &lt;c&gt; R Where &lt;r&gt; = cursor row and &lt;c&gt; = cursor column</span></span> |
| <span data-ttu-id="ecfab-532">ESC \[ 0 c</span><span class="sxs-lookup"><span data-stu-id="ecfab-532">ESC \[ 0 c</span></span> | <span data-ttu-id="ecfab-533">DA</span><span class="sxs-lookup"><span data-stu-id="ecfab-533">DA</span></span> | <span data-ttu-id="ecfab-534">Atributos de dispositivo</span><span class="sxs-lookup"><span data-stu-id="ecfab-534">Device Attributes</span></span> | <span data-ttu-id="ecfab-535">Permite notificar la identidad del terminal.</span><span class="sxs-lookup"><span data-stu-id="ecfab-535">Report the terminal identity.</span></span> <span data-ttu-id="ecfab-536">Emitirá "\\x1b\[?1;0c", lo que indica "VT101 sin opciones".</span><span class="sxs-lookup"><span data-stu-id="ecfab-536">Will emit “\\x1b\[?1;0c”, indicating "VT101 with No Options".</span></span> |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span data-ttu-id="ecfab-537"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Pestañas</span><span class="sxs-lookup"><span data-stu-id="ecfab-537"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabs</span></span>


<span data-ttu-id="ecfab-538">Aunque la consola de Windows normalmente espera a que las pestañas tengan exclusivamente ocho caracteres de ancho, las \*aplicaciones de Nix que utilicen ciertas secuencias pueden saber dónde están las tabulaciones en las ventanas de la consola para optimizar el movimiento del cursor por parte de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ecfab-538">While the windows console traditionally expects tabs to be exclusively eight characters wide, \*nix applications utilizing certain sequences can manipulate where the tab stops are within the console windows to optimize cursor movement by the application.</span></span>

<span data-ttu-id="ecfab-539">Las secuencias siguientes permiten que una aplicación establezca las ubicaciones de las tabulaciones dentro de la ventana de la consola, así como quitarlas y desplazarse entre ellas.</span><span class="sxs-lookup"><span data-stu-id="ecfab-539">The following sequences allow an application to set the tab stop locations within the console window, remove them, and navigate between them.</span></span>


| <span data-ttu-id="ecfab-540">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-540">Sequence</span></span> | <span data-ttu-id="ecfab-541">Código</span><span class="sxs-lookup"><span data-stu-id="ecfab-541">Code</span></span> | <span data-ttu-id="ecfab-542">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-542">Description</span></span> | <span data-ttu-id="ecfab-543">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-543">Behavior</span></span> |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ecfab-544">ESC H</span><span class="sxs-lookup"><span data-stu-id="ecfab-544">ESC H</span></span> | <span data-ttu-id="ecfab-545">HTS</span><span class="sxs-lookup"><span data-stu-id="ecfab-545">HTS</span></span> | <span data-ttu-id="ecfab-546">Conjunto de tabulación horizontal</span><span class="sxs-lookup"><span data-stu-id="ecfab-546">Horizontal Tab Set</span></span> | <span data-ttu-id="ecfab-547">Establece una tabulación en la columna actual en la que se encuentra el cursor.</span><span class="sxs-lookup"><span data-stu-id="ecfab-547">Sets a tab stop in the current column the cursor is in.</span></span> |
| <span data-ttu-id="ecfab-548">ESC \[ &lt;n&gt; I</span><span class="sxs-lookup"><span data-stu-id="ecfab-548">ESC \[ &lt;n&gt; I</span></span> | <span data-ttu-id="ecfab-549">CHT</span><span class="sxs-lookup"><span data-stu-id="ecfab-549">CHT</span></span> | <span data-ttu-id="ecfab-550">Tabulación horizontal del cursor (hacia delante)</span><span class="sxs-lookup"><span data-stu-id="ecfab-550">Cursor Horizontal (Forward) Tab</span></span> | <span data-ttu-id="ecfab-551">Permite avanzar el cursor hasta la columna siguiente (en la misma fila) con una tabulación.</span><span class="sxs-lookup"><span data-stu-id="ecfab-551">Advance the cursor to the next column (in the same row) with a tab stop.</span></span> <span data-ttu-id="ecfab-552">Si no hay más tabulaciones, puede desplazarse a la última columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="ecfab-552">If there are no more tab stops, move to the last column in the row.</span></span> <span data-ttu-id="ecfab-553">En cambio, si el cursor está en la última columna, puede desplazarse a la primera columna de la fila siguiente.</span><span class="sxs-lookup"><span data-stu-id="ecfab-553">If the cursor is in the last column, move to the first column of the next row.</span></span> |
| <span data-ttu-id="ecfab-554">ESC \[ &lt;n&gt; Z</span><span class="sxs-lookup"><span data-stu-id="ecfab-554">ESC \[ &lt;n&gt; Z</span></span> | <span data-ttu-id="ecfab-555">CBT</span><span class="sxs-lookup"><span data-stu-id="ecfab-555">CBT</span></span> | <span data-ttu-id="ecfab-556">Tabulación hacia atrás del cursor</span><span class="sxs-lookup"><span data-stu-id="ecfab-556">Cursor Backwards Tab</span></span> | <span data-ttu-id="ecfab-557">Permite mover el cursor hasta la columna anterior (en la misma fila) con una tabulación.</span><span class="sxs-lookup"><span data-stu-id="ecfab-557">Move the cursor to the previous column (in the same row) with a tab stop.</span></span> <span data-ttu-id="ecfab-558">Si no hay más tabulaciones, mueve el cursor a la primera columna.</span><span class="sxs-lookup"><span data-stu-id="ecfab-558">If there are no more tab stops, moves the cursor to the first column.</span></span> <span data-ttu-id="ecfab-559">En cambio, si el cursor está en la primera columna, no mueve el cursor.</span><span class="sxs-lookup"><span data-stu-id="ecfab-559">If the cursor is in the first column, doesn’t move the cursor.</span></span> |
| <span data-ttu-id="ecfab-560">ESC \[ 0 g</span><span class="sxs-lookup"><span data-stu-id="ecfab-560">ESC \[ 0 g</span></span> | <span data-ttu-id="ecfab-561">TBC</span><span class="sxs-lookup"><span data-stu-id="ecfab-561">TBC</span></span> | <span data-ttu-id="ecfab-562">Borrado de la tabulación (columna actual)</span><span class="sxs-lookup"><span data-stu-id="ecfab-562">Tab Clear (current column)</span></span> | <span data-ttu-id="ecfab-563">Borra la tabulación de la columna actual, si hay alguna.</span><span class="sxs-lookup"><span data-stu-id="ecfab-563">Clears the tab stop in the current column, if there is one.</span></span> <span data-ttu-id="ecfab-564">En caso contrario, no hace nada.</span><span class="sxs-lookup"><span data-stu-id="ecfab-564">Otherwise does nothing.</span></span> |
| <span data-ttu-id="ecfab-565">ESC \[ 3 g</span><span class="sxs-lookup"><span data-stu-id="ecfab-565">ESC \[ 3 g</span></span> | <span data-ttu-id="ecfab-566">TBC</span><span class="sxs-lookup"><span data-stu-id="ecfab-566">TBC</span></span> | <span data-ttu-id="ecfab-567">Borrado de la tabulación (todas las columnas)</span><span class="sxs-lookup"><span data-stu-id="ecfab-567">Tab Clear (all columns)</span></span> | <span data-ttu-id="ecfab-568">Borra todas las tabulaciones establecidas.</span><span class="sxs-lookup"><span data-stu-id="ecfab-568">Clears all currently set tab stops.</span></span> |



- <span data-ttu-id="ecfab-569">En el caso de CHT y CBT, &lt;n&gt; es un parámetro opcional (valor predeterminado=1) que indica el número de veces que se debe avanzar el cursor en la dirección especificada.</span><span class="sxs-lookup"><span data-stu-id="ecfab-569">For both CHT and CBT, &lt;n&gt; is an optional parameter that (default=1) indicating how many times to advance the cursor in the specified direction.</span></span>
- <span data-ttu-id="ecfab-570">Si no se establece ninguna tabulación a través de HTS, CHT y CBT, la primera y la última columna de la ventana serán las dos únicas tabulaciones.</span><span class="sxs-lookup"><span data-stu-id="ecfab-570">If there are no tab stops set via HTS, CHT and CBT will treat the first and last columns of the window as the only two tab stops.</span></span>
- <span data-ttu-id="ecfab-571">De la misma manera que sucede con CHT, al usar HTS para establecer una tabulación, la consola también navegará hasta la siguiente tabulación en el resultado de un carácter TAB (0x09, ‘\\t’).</span><span class="sxs-lookup"><span data-stu-id="ecfab-571">Using HTS to set a tab stop will also cause the console to navigate to the next tab stop on the output of a TAB (0x09, ‘\\t’) character, in the same manner as CHT.</span></span>

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span data-ttu-id="ecfab-572"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designación del juego de caracteres</span><span class="sxs-lookup"><span data-stu-id="ecfab-572"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designate Character Set</span></span>


<span data-ttu-id="ecfab-573">Las secuencias siguientes permiten que un programa cambie la asignación del juego de caracteres activo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-573">The following sequences allow a program to change the active character set mapping.</span></span> <span data-ttu-id="ecfab-574">Esto permite que un programa emita caracteres ASCII de 7 bits, pero que se muestren como otros glifos en la pantalla del terminal.</span><span class="sxs-lookup"><span data-stu-id="ecfab-574">This allows a program to emit 7-bit ASCII characters, but have them displayed as other glyphs on the terminal screen itself.</span></span> <span data-ttu-id="ecfab-575">Actualmente, los únicos dos juegos de caracteres admitidos son ASCII (valor predeterminado) y el juego de caracteres de gráficos especiales DEC.</span><span class="sxs-lookup"><span data-stu-id="ecfab-575">Currently, the only two supported character sets are ASCII (default) and the DEC Special Graphics Character Set.</span></span> <span data-ttu-id="ecfab-576">Consulte <http://vt100.net/docs/vt220-rm/table2-4.html> para obtener una lista de todos los caracteres que representa el juego de caracteres de gráficos especiales DEC.</span><span class="sxs-lookup"><span data-stu-id="ecfab-576">See <http://vt100.net/docs/vt220-rm/table2-4.html> for a listing of all of the characters represented by the DEC Special Graphics Character Set.</span></span>


| <span data-ttu-id="ecfab-577">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-577">Sequence</span></span> | <span data-ttu-id="ecfab-578">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-578">Description</span></span> | <span data-ttu-id="ecfab-579">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-579">Behavior</span></span> |
|----------|--------------------------------------------|-------------------------------|
| <span data-ttu-id="ecfab-580">ESC ( 0</span><span class="sxs-lookup"><span data-stu-id="ecfab-580">ESC ( 0</span></span> | <span data-ttu-id="ecfab-581">Permite designar el juego de caracteres: trazado de líneas DEC.</span><span class="sxs-lookup"><span data-stu-id="ecfab-581">Designate Character Set – DEC Line Drawing</span></span> | <span data-ttu-id="ecfab-582">Habilita el modo de trazado de líneas DEC.</span><span class="sxs-lookup"><span data-stu-id="ecfab-582">Enables DEC Line Drawing Mode</span></span> |
| <span data-ttu-id="ecfab-583">ESC ( B</span><span class="sxs-lookup"><span data-stu-id="ecfab-583">ESC ( B</span></span> | <span data-ttu-id="ecfab-584">Permite designar el juego de caracteres ASCII de EE. UU.</span><span class="sxs-lookup"><span data-stu-id="ecfab-584">Designate Character Set – US ASCII</span></span> | <span data-ttu-id="ecfab-585">Habilita el modo ASCII (valor predeterminado).</span><span class="sxs-lookup"><span data-stu-id="ecfab-585">Enables ASCII Mode (Default)</span></span> |



<span data-ttu-id="ecfab-586">En particular, el modo de trazado de líneas DEC se usa para trazar los bordes en las aplicaciones de consola.</span><span class="sxs-lookup"><span data-stu-id="ecfab-586">Notably, the DEC Line Drawing mode is used for drawing borders in console applications.</span></span> <span data-ttu-id="ecfab-587">En la tabla siguiente se muestra qué caracteres ASCII se asignan a los caracteres de trazado de líneas.</span><span class="sxs-lookup"><span data-stu-id="ecfab-587">The following table shows what ASCII character maps to which line drawing character.</span></span>


| <span data-ttu-id="ecfab-588">Hex</span><span class="sxs-lookup"><span data-stu-id="ecfab-588">Hex</span></span> | <span data-ttu-id="ecfab-589">ASCII</span><span class="sxs-lookup"><span data-stu-id="ecfab-589">ASCII</span></span> | <span data-ttu-id="ecfab-590">Trazado de líneas DEC</span><span class="sxs-lookup"><span data-stu-id="ecfab-590">DEC Line Drawing</span></span> |
|------|-------|------------------|
| <span data-ttu-id="ecfab-591">0x6a</span><span class="sxs-lookup"><span data-stu-id="ecfab-591">0x6a</span></span> | <span data-ttu-id="ecfab-592">j</span><span class="sxs-lookup"><span data-stu-id="ecfab-592">j</span></span> | <span data-ttu-id="ecfab-593">┘</span><span class="sxs-lookup"><span data-stu-id="ecfab-593">┘</span></span> |
| <span data-ttu-id="ecfab-594">0x6b</span><span class="sxs-lookup"><span data-stu-id="ecfab-594">0x6b</span></span> | <span data-ttu-id="ecfab-595">k</span><span class="sxs-lookup"><span data-stu-id="ecfab-595">k</span></span> | <span data-ttu-id="ecfab-596">┐</span><span class="sxs-lookup"><span data-stu-id="ecfab-596">┐</span></span> |
| <span data-ttu-id="ecfab-597">0x6c</span><span class="sxs-lookup"><span data-stu-id="ecfab-597">0x6c</span></span> | <span data-ttu-id="ecfab-598">l</span><span class="sxs-lookup"><span data-stu-id="ecfab-598">l</span></span> | <span data-ttu-id="ecfab-599">┌</span><span class="sxs-lookup"><span data-stu-id="ecfab-599">┌</span></span> |
| <span data-ttu-id="ecfab-600">0x6d</span><span class="sxs-lookup"><span data-stu-id="ecfab-600">0x6d</span></span> | <span data-ttu-id="ecfab-601">m</span><span class="sxs-lookup"><span data-stu-id="ecfab-601">m</span></span> | <span data-ttu-id="ecfab-602">└</span><span class="sxs-lookup"><span data-stu-id="ecfab-602">└</span></span> |
| <span data-ttu-id="ecfab-603">0x6e</span><span class="sxs-lookup"><span data-stu-id="ecfab-603">0x6e</span></span> | <span data-ttu-id="ecfab-604">n</span><span class="sxs-lookup"><span data-stu-id="ecfab-604">n</span></span> | <span data-ttu-id="ecfab-605">┼</span><span class="sxs-lookup"><span data-stu-id="ecfab-605">┼</span></span> |
| <span data-ttu-id="ecfab-606">0x71</span><span class="sxs-lookup"><span data-stu-id="ecfab-606">0x71</span></span> | <span data-ttu-id="ecfab-607">q</span><span class="sxs-lookup"><span data-stu-id="ecfab-607">q</span></span> | <span data-ttu-id="ecfab-608">─</span><span class="sxs-lookup"><span data-stu-id="ecfab-608">─</span></span> |
| <span data-ttu-id="ecfab-609">0x74</span><span class="sxs-lookup"><span data-stu-id="ecfab-609">0x74</span></span> | <span data-ttu-id="ecfab-610">t</span><span class="sxs-lookup"><span data-stu-id="ecfab-610">t</span></span> | <span data-ttu-id="ecfab-611">├</span><span class="sxs-lookup"><span data-stu-id="ecfab-611">├</span></span> |
| <span data-ttu-id="ecfab-612">0x75</span><span class="sxs-lookup"><span data-stu-id="ecfab-612">0x75</span></span> | <span data-ttu-id="ecfab-613">u</span><span class="sxs-lookup"><span data-stu-id="ecfab-613">u</span></span> | <span data-ttu-id="ecfab-614">┤</span><span class="sxs-lookup"><span data-stu-id="ecfab-614">┤</span></span> |
| <span data-ttu-id="ecfab-615">0x76</span><span class="sxs-lookup"><span data-stu-id="ecfab-615">0x76</span></span> | <span data-ttu-id="ecfab-616">v</span><span class="sxs-lookup"><span data-stu-id="ecfab-616">v</span></span> | <span data-ttu-id="ecfab-617">┴</span><span class="sxs-lookup"><span data-stu-id="ecfab-617">┴</span></span> |
| <span data-ttu-id="ecfab-618">0x77</span><span class="sxs-lookup"><span data-stu-id="ecfab-618">0x77</span></span> | <span data-ttu-id="ecfab-619">w</span><span class="sxs-lookup"><span data-stu-id="ecfab-619">w</span></span> | <span data-ttu-id="ecfab-620">┬</span><span class="sxs-lookup"><span data-stu-id="ecfab-620">┬</span></span> |
| <span data-ttu-id="ecfab-621">0x78</span><span class="sxs-lookup"><span data-stu-id="ecfab-621">0x78</span></span> | <span data-ttu-id="ecfab-622">x</span><span class="sxs-lookup"><span data-stu-id="ecfab-622">x</span></span> | <span data-ttu-id="ecfab-623">│</span><span class="sxs-lookup"><span data-stu-id="ecfab-623">│</span></span> |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span data-ttu-id="ecfab-624"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Márgenes de desplazamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-624"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scrolling Margins</span></span>


<span data-ttu-id="ecfab-625">Las siguientes secuencias permiten que un programa configure la "región de desplazamiento" de la pantalla que se ve afectada por las operaciones de desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="ecfab-625">The following sequences allow a program to configure the “scrolling region” of the screen that is affected by scrolling operations.</span></span> <span data-ttu-id="ecfab-626">Este es un subconjunto de las filas que se ajustan cuando la pantalla se desplaza; por ejemplo, en "\\n" o RI.</span><span class="sxs-lookup"><span data-stu-id="ecfab-626">This is a subset of the rows that are adjusted when the screen would otherwise scroll, for example, on a ‘\\n’ or RI.</span></span> <span data-ttu-id="ecfab-627">Asimismo, estos márgenes también afectan a las filas que hayan modificado las opciones Inserción de línea (IL) y Eliminación de línea (DL), Desplazamiento hacia arriba (SU) y Desplazamiento hacia abajo (SD).</span><span class="sxs-lookup"><span data-stu-id="ecfab-627">These margins also affect the rows modified by Insert Line (IL) and Delete Line (DL), Scroll Up (SU) and Scroll Down (SD).</span></span>

<span data-ttu-id="ecfab-628">Los márgenes de desplazamiento pueden ser especialmente útiles si quiere tener una parte de la pantalla que no se desplace cuando quiera rellenar el resto; por ejemplo, tener una barra de título en la parte superior o una barra de estado en la parte inferior de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ecfab-628">The scrolling margins can be especially useful for having a portion of the screen that doesn’t scroll when the rest of the screen is filled, such as having a title bar at the top or a status bar at the bottom of your application.</span></span>

<span data-ttu-id="ecfab-629">En el caso de DECSTBM, existen dos parámetros opcionales, &lt;t&gt; y &lt;b&gt;, que se usan para especificar las filas que representan las líneas superior e inferior de la región de desplazamiento, ambas inclusive.</span><span class="sxs-lookup"><span data-stu-id="ecfab-629">For DECSTBM, there are two optional parameters, &lt;t&gt; and &lt;b&gt;, which are used to specify the rows that represent the top and bottom lines of the scroll region, inclusive.</span></span> <span data-ttu-id="ecfab-630">Si se omiten los parámetros, &lt;t&gt; convierte el valor predeterminado en 1 y &lt;b&gt; se establece en el alto de la ventanilla actual.</span><span class="sxs-lookup"><span data-stu-id="ecfab-630">If the parameters are omitted, &lt;t&gt; defaults to 1 and &lt;b&gt; defaults to the current viewport height.</span></span>

<span data-ttu-id="ecfab-631">Los márgenes de desplazamiento son por búfer, por lo que debe tener en cuenta que el búfer alternativo y el búfer principal mantienen configuraciones de márgenes de desplazamiento independientes; por ello, una aplicación de pantalla completa en el búfer alternativo no afectará a los márgenes del búfer principal.</span><span class="sxs-lookup"><span data-stu-id="ecfab-631">Scrolling margins are per-buffer, so importantly, the Alternate Buffer and Main Buffer maintain separate scrolling margins settings (so a full screen application in the alternate buffer will not poison the main buffer’s margins).</span></span>


| <span data-ttu-id="ecfab-632">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-632">Sequence</span></span> | <span data-ttu-id="ecfab-633">Código</span><span class="sxs-lookup"><span data-stu-id="ecfab-633">Code</span></span> | <span data-ttu-id="ecfab-634">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-634">Description</span></span> | <span data-ttu-id="ecfab-635">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-635">Behavior</span></span> |
|--------------------------------|---------|----------------------|------------------------------------------------|
| <span data-ttu-id="ecfab-636">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span><span class="sxs-lookup"><span data-stu-id="ecfab-636">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span></span> | <span data-ttu-id="ecfab-637">DECSTBM</span><span class="sxs-lookup"><span data-stu-id="ecfab-637">DECSTBM</span></span> | <span data-ttu-id="ecfab-638">Permite establecer la región de desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="ecfab-638">Set Scrolling Region</span></span> | <span data-ttu-id="ecfab-639">Establece los márgenes de desplazamiento de VT de la ventanilla.</span><span class="sxs-lookup"><span data-stu-id="ecfab-639">Sets the VT scrolling margins of the viewport.</span></span> |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span data-ttu-id="ecfab-640"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Título de ventana</span><span class="sxs-lookup"><span data-stu-id="ecfab-640"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Window Title</span></span>


<span data-ttu-id="ecfab-641">Los siguientes comandos permiten que la aplicación establezca el título de la ventana de la consola en el parámetro &lt;string&gt; especificado.</span><span class="sxs-lookup"><span data-stu-id="ecfab-641">The following commands allows the application to set the title of the console window to the given &lt;string&gt; parameter.</span></span> <span data-ttu-id="ecfab-642">La cadena debe tener menos de 255 caracteres para que pueda aceptarse.</span><span class="sxs-lookup"><span data-stu-id="ecfab-642">The string must be less than 255 characters to be accepted.</span></span> <span data-ttu-id="ecfab-643">Esto equivale a llamar al elemento SetConsoleTitle con la cadena especificada.</span><span class="sxs-lookup"><span data-stu-id="ecfab-643">This is equivalent to calling SetConsoleTitle with the given string.</span></span>

<span data-ttu-id="ecfab-644">Tenga en cuenta que esta secuencia es una secuencia OSC de tipo "Comando del sistema operativo" y no un elemento CSI como muchas de las otras secuencias enumeradas; asimismo, esta secuencia comienza por "\\x1b\]" y no por "\\x1b\[".</span><span class="sxs-lookup"><span data-stu-id="ecfab-644">Note that these sequences are OSC “Operating system command” sequences, and not a CSI like many of the other sequences listed, and as such starts with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="ecfab-645">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-645">Sequence</span></span> | <span data-ttu-id="ecfab-646">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-646">Description</span></span> | <span data-ttu-id="ecfab-647">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-647">Behavior</span></span> |
|-------------------------------|---------------------------|----------------------------------------------------|
| <span data-ttu-id="ecfab-648">ESC \] 0 ; &lt;string&gt; BEL</span><span class="sxs-lookup"><span data-stu-id="ecfab-648">ESC \] 0 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="ecfab-649">Permite establecer el título de la ventana y el icono.</span><span class="sxs-lookup"><span data-stu-id="ecfab-649">Set Icon and Window Title</span></span> | <span data-ttu-id="ecfab-650">Establece el título de la ventana de la consola en &lt;string&gt;.</span><span class="sxs-lookup"><span data-stu-id="ecfab-650">Sets the console window’s title to &lt;string&gt;.</span></span> |
| <span data-ttu-id="ecfab-651">ESC \] 2 ; &lt;string&gt; BEL</span><span class="sxs-lookup"><span data-stu-id="ecfab-651">ESC \] 2 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="ecfab-652">Permite establecer el título de la ventana.</span><span class="sxs-lookup"><span data-stu-id="ecfab-652">Set Window Title</span></span> | <span data-ttu-id="ecfab-653">Establece el título de la ventana de la consola en &lt;string&gt;.</span><span class="sxs-lookup"><span data-stu-id="ecfab-653">Sets the console window’s title to &lt;string&gt;.</span></span> |



<span data-ttu-id="ecfab-654">El carácter final que se indica aquí es el carácter "Bell", "\\x07".</span><span class="sxs-lookup"><span data-stu-id="ecfab-654">The terminating character here is the “Bell” character, ‘\\x07’</span></span>

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span data-ttu-id="ecfab-655"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Búfer de pantalla alternativo</span><span class="sxs-lookup"><span data-stu-id="ecfab-655"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternate Screen Buffer</span></span>


<span data-ttu-id="ecfab-656">\*Las aplicaciones de estilo Nix suelen usar un búfer de pantalla alternativo para que puedan modificar todo el contenido del búfer, sin que ello afecte a la aplicación que inició ese contenido.</span><span class="sxs-lookup"><span data-stu-id="ecfab-656">\*Nix style applications often utilize an alternate screen buffer, so that they can modify the entire contents of the buffer, without affecting the application that started them.</span></span> <span data-ttu-id="ecfab-657">El búfer alternativo tiene exactamente las dimensiones de la ventana, sin ninguna región desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="ecfab-657">The alternate buffer is exactly the dimensions of the window, without any scrollback region.</span></span>

<span data-ttu-id="ecfab-658">Para obtener un ejemplo de este comportamiento, tenga en cuenta cuándo se inicia VIM desde Bash.</span><span class="sxs-lookup"><span data-stu-id="ecfab-658">For an example of this behavior, consider when vim is launched from bash.</span></span> <span data-ttu-id="ecfab-659">VIM usa toda la pantalla para editar el archivo, por lo que si vuelve a Bash, el búfer original no se modifica.</span><span class="sxs-lookup"><span data-stu-id="ecfab-659">Vim uses the entirety of the screen to edit the file, then returning to bash leaves the original buffer unchanged.</span></span>


| <span data-ttu-id="ecfab-660">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-660">Sequence</span></span> | <span data-ttu-id="ecfab-661">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-661">Description</span></span> | <span data-ttu-id="ecfab-662">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-662">Behavior</span></span> |
|--------------------|-----------------------------|--------------------------------------------|
| <span data-ttu-id="ecfab-663">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="ecfab-663">ESC \[ ?</span></span> <span data-ttu-id="ecfab-664">1 0 4 9 h</span><span class="sxs-lookup"><span data-stu-id="ecfab-664">1 0 4 9 h</span></span> | <span data-ttu-id="ecfab-665">Permite usar el búfer de pantalla alternativo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-665">Use Alternate Screen Buffer</span></span> | <span data-ttu-id="ecfab-666">Cambia a un nuevo búfer de pantalla alternativo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-666">Switches to a new alternate screen buffer.</span></span> |
| <span data-ttu-id="ecfab-667">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="ecfab-667">ESC \[ ?</span></span> <span data-ttu-id="ecfab-668">1 0 4 9 l</span><span class="sxs-lookup"><span data-stu-id="ecfab-668">1 0 4 9 l</span></span> | <span data-ttu-id="ecfab-669">Permite usar el búfer de pantalla principal.</span><span class="sxs-lookup"><span data-stu-id="ecfab-669">Use Main Screen Buffer</span></span> | <span data-ttu-id="ecfab-670">Cambia al búfer principal.</span><span class="sxs-lookup"><span data-stu-id="ecfab-670">Switches to the main buffer.</span></span> |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span data-ttu-id="ecfab-671"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Ancho de la ventana</span><span class="sxs-lookup"><span data-stu-id="ecfab-671"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Window Width</span></span>


<span data-ttu-id="ecfab-672">Las secuencias siguientes se pueden usar para controlar el ancho de la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="ecfab-672">The following sequences can be used to control the width of the console window.</span></span> <span data-ttu-id="ecfab-673">Son aproximadamente equivalentes a la llamada a la API de la consola SetConsoleScreenBufferInfoEx, que se realiza para establecer el ancho de la ventana.</span><span class="sxs-lookup"><span data-stu-id="ecfab-673">They are roughly equivalent to the calling the SetConsoleScreenBufferInfoEx console API to set the window width.</span></span>


| <span data-ttu-id="ecfab-674">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-674">Sequence</span></span> | <span data-ttu-id="ecfab-675">Código</span><span class="sxs-lookup"><span data-stu-id="ecfab-675">Code</span></span> | <span data-ttu-id="ecfab-676">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-676">Description</span></span> | <span data-ttu-id="ecfab-677">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-677">Behavior</span></span> |
|--------------|---------|------------------------------|---------------------------------------------|
| <span data-ttu-id="ecfab-678">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="ecfab-678">ESC \[ ?</span></span> <span data-ttu-id="ecfab-679">3 h</span><span class="sxs-lookup"><span data-stu-id="ecfab-679">3 h</span></span> | <span data-ttu-id="ecfab-680">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="ecfab-680">DECCOLM</span></span> | <span data-ttu-id="ecfab-681">Permite establecer el número de columnas en 132.</span><span class="sxs-lookup"><span data-stu-id="ecfab-681">Set Number of Columns to 132</span></span> | <span data-ttu-id="ecfab-682">Establece el ancho de la consola en 132 columnas de ancho.</span><span class="sxs-lookup"><span data-stu-id="ecfab-682">Sets the console width to 132 columns wide.</span></span> |
| <span data-ttu-id="ecfab-683">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="ecfab-683">ESC \[ ?</span></span> <span data-ttu-id="ecfab-684">3 l</span><span class="sxs-lookup"><span data-stu-id="ecfab-684">3 l</span></span> | <span data-ttu-id="ecfab-685">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="ecfab-685">DECCOLM</span></span> | <span data-ttu-id="ecfab-686">Permite establecer el número de columnas en 80.</span><span class="sxs-lookup"><span data-stu-id="ecfab-686">Set Number of Columns to 80</span></span> | <span data-ttu-id="ecfab-687">Establece el ancho de la consola en 80 columnas de ancho.</span><span class="sxs-lookup"><span data-stu-id="ecfab-687">Sets the console width to 80 columns wide.</span></span> |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span data-ttu-id="ecfab-688"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Restablecimiento parcial</span><span class="sxs-lookup"><span data-stu-id="ecfab-688"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Soft Reset</span></span>


<span data-ttu-id="ecfab-689">Puede usar la siguiente secuencia para restablecer los valores predeterminados de algunas propiedades. Las siguientes propiedades se restablecen a los siguientes valores predeterminados (también se muestran las secuencias que controlan esas propiedades):</span><span class="sxs-lookup"><span data-stu-id="ecfab-689">The following sequence can be used to reset certain properties to their default values.The following properties are reset to the following default values (also listed are the sequences that control those properties):</span></span>

- <span data-ttu-id="ecfab-690">Visibilidad del cursor: visible (DECTEM)</span><span class="sxs-lookup"><span data-stu-id="ecfab-690">Cursor visibility: visible (DECTEM)</span></span>
- <span data-ttu-id="ecfab-691">Teclado numérico: Modo numérico (DECNKM)</span><span class="sxs-lookup"><span data-stu-id="ecfab-691">Numeric Keypad: Numeric Mode (DECNKM)</span></span>
- <span data-ttu-id="ecfab-692">Modo de teclas del cursor: Modo normal (DECCKM)</span><span class="sxs-lookup"><span data-stu-id="ecfab-692">Cursor Keys Mode: Normal Mode (DECCKM)</span></span>
- <span data-ttu-id="ecfab-693">Márgenes superior e inferior: Superior=1, Inferior=alto de la consola (DECSTBM)</span><span class="sxs-lookup"><span data-stu-id="ecfab-693">Top and Bottom Margins: Top=1, Bottom=Console height (DECSTBM)</span></span>
- <span data-ttu-id="ecfab-694">Juego de caracteres: ASCII (EE. UU.)</span><span class="sxs-lookup"><span data-stu-id="ecfab-694">Character Set: US ASCII</span></span>
- <span data-ttu-id="ecfab-695">Representación de gráficos: Predeterminado/Desactivado (SGR)</span><span class="sxs-lookup"><span data-stu-id="ecfab-695">Graphics Rendition: Default/Off (SGR)</span></span>
- <span data-ttu-id="ecfab-696">Guardar el estado del cursor: Posición de inicio (0,0) (DECSC)</span><span class="sxs-lookup"><span data-stu-id="ecfab-696">Save cursor state: Home position (0,0) (DECSC)</span></span>


| <span data-ttu-id="ecfab-697">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-697">Sequence</span></span> | <span data-ttu-id="ecfab-698">Código</span><span class="sxs-lookup"><span data-stu-id="ecfab-698">Code</span></span> | <span data-ttu-id="ecfab-699">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecfab-699">Description</span></span> | <span data-ttu-id="ecfab-700">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="ecfab-700">Behavior</span></span> |
|------------|--------|-------------|----------------------------------------------------|
| <span data-ttu-id="ecfab-701">ESC \[ !</span><span class="sxs-lookup"><span data-stu-id="ecfab-701">ESC \[ !</span></span> <span data-ttu-id="ecfab-702">p</span><span class="sxs-lookup"><span data-stu-id="ecfab-702">p</span></span> | <span data-ttu-id="ecfab-703">DECSTR</span><span class="sxs-lookup"><span data-stu-id="ecfab-703">DECSTR</span></span> | <span data-ttu-id="ecfab-704">Restablecimiento parcial</span><span class="sxs-lookup"><span data-stu-id="ecfab-704">Soft Reset</span></span> | <span data-ttu-id="ecfab-705">Permite restablecer los valores predeterminados de ciertas opciones de terminal.</span><span class="sxs-lookup"><span data-stu-id="ecfab-705">Reset certain terminal settings to their defaults.</span></span> |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span data-ttu-id="ecfab-706"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Secuencias de entrada</span><span class="sxs-lookup"><span data-stu-id="ecfab-706"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Input Sequences</span></span>


<span data-ttu-id="ecfab-707">El host de consola emite las siguientes secuencias de terminal en el flujo de entrada si se establece la marca ENABLE\_VIRTUAL\_TERMINAL\_INPUT en el identificador del búfer de entrada mediante la marca SetConsoleMode.</span><span class="sxs-lookup"><span data-stu-id="ecfab-707">The following terminal sequences are emitted by the console host on the input stream if the ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag is set on the input buffer handle using the SetConsoleMode flag.</span></span>

<span data-ttu-id="ecfab-708">Existen dos modos internos que controlan qué secuencias se emiten para las teclas de entrada dadas: el modo de teclas del cursor y el modo de teclas del teclado.</span><span class="sxs-lookup"><span data-stu-id="ecfab-708">There are two internal modes that control which sequences are emitted for the given input keys, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="ecfab-709">Ambos modos se describen en la sección de Cambios en el modo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-709">These are described in the Mode Changes section.</span></span>

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span data-ttu-id="ecfab-710"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Teclas del cursor</span><span class="sxs-lookup"><span data-stu-id="ecfab-710"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Cursor Keys</span></span>


| <span data-ttu-id="ecfab-711">Clave</span><span class="sxs-lookup"><span data-stu-id="ecfab-711">Key</span></span> | <span data-ttu-id="ecfab-712">Modo normal</span><span class="sxs-lookup"><span data-stu-id="ecfab-712">Normal Mode</span></span> | <span data-ttu-id="ecfab-713">Modo de la aplicación</span><span class="sxs-lookup"><span data-stu-id="ecfab-713">Application Mode</span></span> |
|-------------|-------------|------------------|
| <span data-ttu-id="ecfab-714">Flecha arriba</span><span class="sxs-lookup"><span data-stu-id="ecfab-714">Up Arrow</span></span> | <span data-ttu-id="ecfab-715">ESC \[ A</span><span class="sxs-lookup"><span data-stu-id="ecfab-715">ESC \[ A</span></span> | <span data-ttu-id="ecfab-716">ESC O A</span><span class="sxs-lookup"><span data-stu-id="ecfab-716">ESC O A</span></span> |
| <span data-ttu-id="ecfab-717">Flecha abajo</span><span class="sxs-lookup"><span data-stu-id="ecfab-717">Down Arrow</span></span> | <span data-ttu-id="ecfab-718">ESC \[ B</span><span class="sxs-lookup"><span data-stu-id="ecfab-718">ESC \[ B</span></span> | <span data-ttu-id="ecfab-719">ESC O B</span><span class="sxs-lookup"><span data-stu-id="ecfab-719">ESC O B</span></span> |
| <span data-ttu-id="ecfab-720">Flecha derecha</span><span class="sxs-lookup"><span data-stu-id="ecfab-720">Right Arrow</span></span> | <span data-ttu-id="ecfab-721">ESC \[ C</span><span class="sxs-lookup"><span data-stu-id="ecfab-721">ESC \[ C</span></span> | <span data-ttu-id="ecfab-722">ESC O C</span><span class="sxs-lookup"><span data-stu-id="ecfab-722">ESC O C</span></span> |
| <span data-ttu-id="ecfab-723">Flecha izquierda</span><span class="sxs-lookup"><span data-stu-id="ecfab-723">Left Arrow</span></span> | <span data-ttu-id="ecfab-724">ESC \[ D</span><span class="sxs-lookup"><span data-stu-id="ecfab-724">ESC \[ D</span></span> | <span data-ttu-id="ecfab-725">ESC O D</span><span class="sxs-lookup"><span data-stu-id="ecfab-725">ESC O D</span></span> |
| <span data-ttu-id="ecfab-726">Inicio</span><span class="sxs-lookup"><span data-stu-id="ecfab-726">Home</span></span> | <span data-ttu-id="ecfab-727">ESC \[ H</span><span class="sxs-lookup"><span data-stu-id="ecfab-727">ESC \[ H</span></span> | <span data-ttu-id="ecfab-728">ESC O H</span><span class="sxs-lookup"><span data-stu-id="ecfab-728">ESC O H</span></span> |
| <span data-ttu-id="ecfab-729">End</span><span class="sxs-lookup"><span data-stu-id="ecfab-729">End</span></span> | <span data-ttu-id="ecfab-730">ESC \[ F</span><span class="sxs-lookup"><span data-stu-id="ecfab-730">ESC \[ F</span></span> | <span data-ttu-id="ecfab-731">ESC O F</span><span class="sxs-lookup"><span data-stu-id="ecfab-731">ESC O F</span></span> |



<span data-ttu-id="ecfab-732">Asimismo, si se presiona Ctrl con cualquiera de estas teclas, se emiten las secuencias siguientes en su lugar, independientemente del modo de teclas del cursor:</span><span class="sxs-lookup"><span data-stu-id="ecfab-732">Additionally, if Ctrl is pressed with any of these keys, the following sequences are emitted instead, regardless of the Cursor Keys Mode:</span></span>


| <span data-ttu-id="ecfab-733">Clave</span><span class="sxs-lookup"><span data-stu-id="ecfab-733">Key</span></span> | <span data-ttu-id="ecfab-734">Cualquier modo</span><span class="sxs-lookup"><span data-stu-id="ecfab-734">Any Mode</span></span> |
|--------------------|----------------|
| <span data-ttu-id="ecfab-735">Ctrl + Flecha arriba</span><span class="sxs-lookup"><span data-stu-id="ecfab-735">Ctrl + Up Arrow</span></span> | <span data-ttu-id="ecfab-736">ESC \[ 1 ; 5 A</span><span class="sxs-lookup"><span data-stu-id="ecfab-736">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="ecfab-737">Ctrl + Flecha abajo</span><span class="sxs-lookup"><span data-stu-id="ecfab-737">Ctrl + Down Arrow</span></span> | <span data-ttu-id="ecfab-738">ESC \[ 1 ; 5 B</span><span class="sxs-lookup"><span data-stu-id="ecfab-738">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="ecfab-739">Ctrl + Flecha derecha</span><span class="sxs-lookup"><span data-stu-id="ecfab-739">Ctrl + Right Arrow</span></span> | <span data-ttu-id="ecfab-740">ESC \[ 1 ; 5 C</span><span class="sxs-lookup"><span data-stu-id="ecfab-740">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="ecfab-741">Ctrl + Flecha izquierda</span><span class="sxs-lookup"><span data-stu-id="ecfab-741">Ctrl + Left Arrow</span></span> | <span data-ttu-id="ecfab-742">ESC \[ 1 ; 5 D</span><span class="sxs-lookup"><span data-stu-id="ecfab-742">ESC \[ 1 ; 5 D</span></span> |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span data-ttu-id="ecfab-743"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Teclas de función y teclado</span><span class="sxs-lookup"><span data-stu-id="ecfab-743"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad & Function Keys</span></span>


| <span data-ttu-id="ecfab-744">Clave</span><span class="sxs-lookup"><span data-stu-id="ecfab-744">Key</span></span> | <span data-ttu-id="ecfab-745">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-745">Sequence</span></span> |
|-----------|--------------|
| <span data-ttu-id="ecfab-746">Retroceso</span><span class="sxs-lookup"><span data-stu-id="ecfab-746">Backspace</span></span> | <span data-ttu-id="ecfab-747">0x7f (DEL)</span><span class="sxs-lookup"><span data-stu-id="ecfab-747">0x7f (DEL)</span></span> |
| <span data-ttu-id="ecfab-748">Pausar</span><span class="sxs-lookup"><span data-stu-id="ecfab-748">Pause</span></span> | <span data-ttu-id="ecfab-749">0x1a (SUB)</span><span class="sxs-lookup"><span data-stu-id="ecfab-749">0x1a (SUB)</span></span> |
| <span data-ttu-id="ecfab-750">Escape</span><span class="sxs-lookup"><span data-stu-id="ecfab-750">Escape</span></span> | <span data-ttu-id="ecfab-751">0x1b (ESC)</span><span class="sxs-lookup"><span data-stu-id="ecfab-751">0x1b (ESC)</span></span> |
| <span data-ttu-id="ecfab-752">Insertar</span><span class="sxs-lookup"><span data-stu-id="ecfab-752">Insert</span></span> | <span data-ttu-id="ecfab-753">ESC \[ 2 ~</span><span class="sxs-lookup"><span data-stu-id="ecfab-753">ESC \[ 2 ~</span></span> |
| <span data-ttu-id="ecfab-754">Eliminar</span><span class="sxs-lookup"><span data-stu-id="ecfab-754">Delete</span></span> | <span data-ttu-id="ecfab-755">ESC \[ 3 ~</span><span class="sxs-lookup"><span data-stu-id="ecfab-755">ESC \[ 3 ~</span></span> |
| <span data-ttu-id="ecfab-756">Re Pág</span><span class="sxs-lookup"><span data-stu-id="ecfab-756">Page Up</span></span> | <span data-ttu-id="ecfab-757">ESC \[ 5 ~</span><span class="sxs-lookup"><span data-stu-id="ecfab-757">ESC \[ 5 ~</span></span> |
| <span data-ttu-id="ecfab-758">Av Pág</span><span class="sxs-lookup"><span data-stu-id="ecfab-758">Page Down</span></span> | <span data-ttu-id="ecfab-759">ESC \[ 6 ~</span><span class="sxs-lookup"><span data-stu-id="ecfab-759">ESC \[ 6 ~</span></span> |
| <span data-ttu-id="ecfab-760">F1</span><span class="sxs-lookup"><span data-stu-id="ecfab-760">F1</span></span> | <span data-ttu-id="ecfab-761">ESC O P</span><span class="sxs-lookup"><span data-stu-id="ecfab-761">ESC O P</span></span> |
| <span data-ttu-id="ecfab-762">F2</span><span class="sxs-lookup"><span data-stu-id="ecfab-762">F2</span></span> | <span data-ttu-id="ecfab-763">ESC O Q</span><span class="sxs-lookup"><span data-stu-id="ecfab-763">ESC O Q</span></span> |
| <span data-ttu-id="ecfab-764">F3</span><span class="sxs-lookup"><span data-stu-id="ecfab-764">F3</span></span> | <span data-ttu-id="ecfab-765">ESC O R</span><span class="sxs-lookup"><span data-stu-id="ecfab-765">ESC O R</span></span> |
| <span data-ttu-id="ecfab-766">F4</span><span class="sxs-lookup"><span data-stu-id="ecfab-766">F4</span></span> | <span data-ttu-id="ecfab-767">ESC O S</span><span class="sxs-lookup"><span data-stu-id="ecfab-767">ESC O S</span></span> |
| <span data-ttu-id="ecfab-768">F5</span><span class="sxs-lookup"><span data-stu-id="ecfab-768">F5</span></span> | <span data-ttu-id="ecfab-769">ESC \[ 1 5 ~</span><span class="sxs-lookup"><span data-stu-id="ecfab-769">ESC \[ 1 5 ~</span></span> |
| <span data-ttu-id="ecfab-770">F6</span><span class="sxs-lookup"><span data-stu-id="ecfab-770">F6</span></span> | <span data-ttu-id="ecfab-771">ESC \[ 1 7 ~</span><span class="sxs-lookup"><span data-stu-id="ecfab-771">ESC \[ 1 7 ~</span></span> |
| <span data-ttu-id="ecfab-772">F7</span><span class="sxs-lookup"><span data-stu-id="ecfab-772">F7</span></span> | <span data-ttu-id="ecfab-773">ESC \[ 1 8 ~</span><span class="sxs-lookup"><span data-stu-id="ecfab-773">ESC \[ 1 8 ~</span></span> |
| <span data-ttu-id="ecfab-774">F8</span><span class="sxs-lookup"><span data-stu-id="ecfab-774">F8</span></span> | <span data-ttu-id="ecfab-775">ESC \[ 1 9 ~</span><span class="sxs-lookup"><span data-stu-id="ecfab-775">ESC \[ 1 9 ~</span></span> |
| <span data-ttu-id="ecfab-776">F9</span><span class="sxs-lookup"><span data-stu-id="ecfab-776">F9</span></span> | <span data-ttu-id="ecfab-777">ESC \[ 2 0 ~</span><span class="sxs-lookup"><span data-stu-id="ecfab-777">ESC \[ 2 0 ~</span></span> |
| <span data-ttu-id="ecfab-778">F10</span><span class="sxs-lookup"><span data-stu-id="ecfab-778">F10</span></span> | <span data-ttu-id="ecfab-779">ESC \[ 2 1 ~</span><span class="sxs-lookup"><span data-stu-id="ecfab-779">ESC \[ 2 1 ~</span></span> |
| <span data-ttu-id="ecfab-780">F11</span><span class="sxs-lookup"><span data-stu-id="ecfab-780">F11</span></span> | <span data-ttu-id="ecfab-781">ESC \[ 2 3 ~</span><span class="sxs-lookup"><span data-stu-id="ecfab-781">ESC \[ 2 3 ~</span></span> |
| <span data-ttu-id="ecfab-782">F12</span><span class="sxs-lookup"><span data-stu-id="ecfab-782">F12</span></span> | <span data-ttu-id="ecfab-783">ESC \[ 2 4 ~</span><span class="sxs-lookup"><span data-stu-id="ecfab-783">ESC \[ 2 4 ~</span></span> |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span data-ttu-id="ecfab-784"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modificadores</span><span class="sxs-lookup"><span data-stu-id="ecfab-784"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifiers</span></span>

<span data-ttu-id="ecfab-785">Alt se trata al prefijar la secuencia con un escape: ESC &lt;c&gt;, donde &lt;c&gt; es el carácter que pasa el sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-785">Alt is treated by prefixing the sequence with an escape: ESC &lt;c&gt; where &lt;c&gt; is the character passed by the operating system.</span></span> <span data-ttu-id="ecfab-786">Alt+Ctrl se usa de la misma manera, salvo que el sistema operativo habrá desplazado la tecla &lt;c&gt; al carácter de control adecuado que se retransmitirá a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ecfab-786">Alt+Ctrl is handled the same way except that the operating system will have pre-shifted the &lt;c&gt; key to the appropriate control character which will be relayed to the application.</span></span>

<span data-ttu-id="ecfab-787">Ctrl suele pasar tal como se recibe del sistema.</span><span class="sxs-lookup"><span data-stu-id="ecfab-787">Ctrl is generally passed through exactly as received from the system.</span></span> <span data-ttu-id="ecfab-788">Este suele ser un carácter único que se ha desplazado hacia abajo en el espacio reservado del carácter de control (0x0-0x1f).</span><span class="sxs-lookup"><span data-stu-id="ecfab-788">This is typically a single character shifted down into the control character reserved space (0x0-0x1f).</span></span> <span data-ttu-id="ecfab-789">Por ejemplo, Ctrl+@ (0x40) se convierte en NUL (0x00), Ctrl+\[ (0x5b) se convierte en ESC (0x1b), etc. Algunas combinaciones de teclas Ctrl se tratan de forma especial según la tabla siguiente:</span><span class="sxs-lookup"><span data-stu-id="ecfab-789">For example, Ctrl+@ (0x40) becomes NUL (0x00), Ctrl+\[ (0x5b) becomes ESC (0x1b), etc. A few Ctrl key combinations are treated specially according to the following table:</span></span>


| <span data-ttu-id="ecfab-790">Clave</span><span class="sxs-lookup"><span data-stu-id="ecfab-790">Key</span></span> | <span data-ttu-id="ecfab-791">Secuencia</span><span class="sxs-lookup"><span data-stu-id="ecfab-791">Sequence</span></span> |
|--------------------|----------------|
| <span data-ttu-id="ecfab-792">Ctrl + Espacio</span><span class="sxs-lookup"><span data-stu-id="ecfab-792">Ctrl + Space</span></span> | <span data-ttu-id="ecfab-793">0x00 (NUL)</span><span class="sxs-lookup"><span data-stu-id="ecfab-793">0x00 (NUL)</span></span> |
| <span data-ttu-id="ecfab-794">Ctrl + Flecha arriba</span><span class="sxs-lookup"><span data-stu-id="ecfab-794">Ctrl + Up Arrow</span></span> | <span data-ttu-id="ecfab-795">ESC \[ 1 ; 5 A</span><span class="sxs-lookup"><span data-stu-id="ecfab-795">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="ecfab-796">Ctrl + Flecha abajo</span><span class="sxs-lookup"><span data-stu-id="ecfab-796">Ctrl + Down Arrow</span></span> | <span data-ttu-id="ecfab-797">ESC \[ 1 ; 5 B</span><span class="sxs-lookup"><span data-stu-id="ecfab-797">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="ecfab-798">Ctrl + Flecha derecha</span><span class="sxs-lookup"><span data-stu-id="ecfab-798">Ctrl + Right Arrow</span></span> | <span data-ttu-id="ecfab-799">ESC \[ 1 ; 5 C</span><span class="sxs-lookup"><span data-stu-id="ecfab-799">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="ecfab-800">Ctrl + Flecha izquierda</span><span class="sxs-lookup"><span data-stu-id="ecfab-800">Ctrl + Left Arrow</span></span> | <span data-ttu-id="ecfab-801">ESC \[ 1 ; 5 D</span><span class="sxs-lookup"><span data-stu-id="ecfab-801">ESC \[ 1 ; 5 D</span></span> |



> [!NOTE]
><span data-ttu-id="ecfab-802"><kbd>Ctrl</kbd> izquierdo + <kbd>Alt</kbd> derecho se trata como AltGr.</span><span class="sxs-lookup"><span data-stu-id="ecfab-802">Left <kbd>Ctrl</kbd> + Right <kbd>Alt</kbd> is treated as AltGr.</span></span> <span data-ttu-id="ecfab-803">Cuando ambos se usan juntos, se eliminarán y el valor Unicode del carácter que haya presentado el sistema se pasará al destino.</span><span class="sxs-lookup"><span data-stu-id="ecfab-803">When both are seen together, they will be stripped and the Unicode value of the character presented by the system will be passed into the target.</span></span> <span data-ttu-id="ecfab-804">El sistema traducirá previamente los valores de AltGr según la configuración de entrada del sistema actual.</span><span class="sxs-lookup"><span data-stu-id="ecfab-804">The system will pre-translate AltGr values according to the current system input settings.</span></span>



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span data-ttu-id="ecfab-805"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Ejemplos</span><span class="sxs-lookup"><span data-stu-id="ecfab-805"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Samples</span></span>


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span data-ttu-id="ecfab-806"><span id="example"></span><span id="EXAMPLE"></span>Ejemplo de secuencias de terminales de SGR</span><span class="sxs-lookup"><span data-stu-id="ecfab-806"><span id="example"></span><span id="EXAMPLE"></span>Example of SGR terminal sequences</span></span>

<span data-ttu-id="ecfab-807">En el código siguiente se proporcionan varios ejemplos de formato de texto.</span><span class="sxs-lookup"><span data-stu-id="ecfab-807">The following code provides several examples of text formatting.</span></span>

```C
#include <stdio.h>
#include <wchar.h>
#include <windows.h>

int main()
{
 // Set output mode to handle virtual terminal sequences
 HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
 if (hOut == INVALID_HANDLE_VALUE)
 {
 return GetLastError();
 }

 DWORD dwMode = 0;
 if (!GetConsoleMode(hOut, &dwMode))
 {
 return GetLastError();
 }

 dwMode |= ENABLE_VIRTUAL_TERMINAL_PROCESSING;
 if (!SetConsoleMode(hOut, dwMode))
 {
 return GetLastError();
 }

 // Try some Set Graphics Rendition (SGR) terminal escape sequences
 wprintf(L"\x1b[31mThis text has a red foreground using SGR.31.\r\n");
 wprintf(L"\x1b[1mThis text has a bright (bold) red foreground using SGR.1 to affect the previous color setting.\r\n");
 wprintf(L"\x1b[mThis text has returned to default colors using SGR.0 implicitly.\r\n");
 wprintf(L"\x1b[34;46mThis text shows the foreground and background change at the same time.\r\n");
 wprintf(L"\x1b[0mThis text has returned to default colors using SGR.0 explicitly.\r\n");
 wprintf(L"\x1b[31;32;33;34;35;36;101;102;103;104;105;106;107mThis text attempts to apply many colors in the same command. Note the colors are applied from left to right so only the right-most option of foreground cyan (SGR.36) and background bright white (SGR.107) is effective.\r\n");
 wprintf(L"\x1b[39mThis text has restored the foreground color only.\r\n");
 wprintf(L"\x1b[49mThis text has restored the background color only.\r\n");

 return 0;
}
```

> [!NOTE]
><span data-ttu-id="ecfab-808">En el ejemplo anterior, la cadena "`\x1b[31m`" es la implementación de **ESC \[ &lt;n&gt; m**, donde &lt;n&gt; es 31.</span><span class="sxs-lookup"><span data-stu-id="ecfab-808">In the previous example, the string '`\x1b[31m`' is the implementation of **ESC \[ &lt;n&gt; m** with &lt;n&gt; being 31.</span></span>



<span data-ttu-id="ecfab-809">En el gráfico siguiente se muestra la salida del ejemplo de código anterior.</span><span class="sxs-lookup"><span data-stu-id="ecfab-809">The following graphic shows the output of the previous code example.</span></span>

![salida de la consola mediante el comando SGR](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span data-ttu-id="ecfab-811"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Ejemplo para habilitar el procesamiento del terminal virtual</span><span class="sxs-lookup"><span data-stu-id="ecfab-811"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Example of Enabling Virtual Terminal Processing</span></span>

<span data-ttu-id="ecfab-812">El código siguiente proporciona un ejemplo de la manera recomendada para habilitar el procesamiento del terminal virtual de una aplicación.</span><span class="sxs-lookup"><span data-stu-id="ecfab-812">The following code provides an example of the recommended way to enable virtual terminal processing for an application.</span></span> <span data-ttu-id="ecfab-813">El propósito de este ejemplo es mostrar lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="ecfab-813">The intent of the sample is to demonstrate:</span></span>

1. <span data-ttu-id="ecfab-814">Que el modo existente siempre debe recuperarse a través de GetConsoleMode y analizarse antes de establecerlo con SetConsoleMode.</span><span class="sxs-lookup"><span data-stu-id="ecfab-814">The existing mode should always be retrieved via GetConsoleMode and analyzed before being set with SetConsoleMode.</span></span>

2. <span data-ttu-id="ecfab-815">Que comprobar si SetConsoleMode devuelve `0` y si GetLastError devuelve STATUS\_INVALID\_PARAMETER resulta ser el mecanismo actual para determinar cuándo se ejecuta en un sistema de nivel inferior.</span><span class="sxs-lookup"><span data-stu-id="ecfab-815">Checking whether SetConsoleMode returns `0` and GetLastError returns STATUS\_INVALID\_PARAMETER is the current mechanism to determine when running on a down-level system.</span></span> <span data-ttu-id="ecfab-816">Una aplicación que recibe la marca STATUS\_INVALID\_PARAMETER con una de las marcas de modo de consola más recientes en el campo de bits, debe degradar correctamente el comportamiento e intentarlo de nuevo.</span><span class="sxs-lookup"><span data-stu-id="ecfab-816">An application receiving STATUS\_INVALID\_PARAMETER with one of the newer console mode flags in the bit field should gracefully degrade behavior and try again.</span></span>

```C
#include <stdio.h>
#include <wchar.h>
#include <windows.h>

int main()
{
 // Set output mode to handle virtual terminal sequences
 HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
 if (hOut == INVALID_HANDLE_VALUE)
 {
 return false;
 }
 HANDLE hIn = GetStdHandle(STD_INPUT_HANDLE);
 if (hIn == INVALID_HANDLE_VALUE)
 {
 return false;
 }

 DWORD dwOriginalOutMode = 0;
 DWORD dwOriginalInMode = 0;
 if (!GetConsoleMode(hOut, &dwOriginalOutMode))
 {
 return false;
 }
 if (!GetConsoleMode(hIn, &dwOriginalInMode))
 {
 return false;
 }

 DWORD dwRequestedOutModes = ENABLE_VIRTUAL_TERMINAL_PROCESSING | DISABLE_NEWLINE_AUTO_RETURN;
 DWORD dwRequestedInModes = ENABLE_VIRTUAL_TERMINAL_INPUT;

 DWORD dwOutMode = dwOriginalOutMode | dwRequestedOutModes;
 if (!SetConsoleMode(hOut, dwOutMode))
 {
 // we failed to set both modes, try to step down mode gracefully.
 dwRequestedOutModes = ENABLE_VIRTUAL_TERMINAL_PROCESSING;
 dwOutMode = dwOriginalOutMode | dwRequestedOutModes;
 if (!SetConsoleMode(hOut, dwOutMode))
 {
 // Failed to set any VT mode, can't do anything here.
 return -1;
 }
 }

 DWORD dwInMode = dwOriginalInMode | ENABLE_VIRTUAL_TERMINAL_INPUT;
 if (!SetConsoleMode(hIn, dwInMode))
 {
 // Failed to set VT input mode, can't do anything here.
 return -1;
 }

 return 0;
}
```

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span data-ttu-id="ecfab-817"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Ejemplo para seleccionar las características de actualización de aniversario</span><span class="sxs-lookup"><span data-stu-id="ecfab-817"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Example of Select Anniversary Update Features</span></span>

<span data-ttu-id="ecfab-818">En el ejemplo siguiente se pretende proporcionar un ejemplo más sólido de código, usando para ello una variedad de secuencias de escape para manipular el búfer, poniendo énfasis en las características agregadas en la Actualización de aniversario de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="ecfab-818">The following example is intended to be a more robust example of code using a variety of escape sequences to manipulate the buffer, with an emphasis on the features added in the Anniversary Update for Windows 10.</span></span>

<span data-ttu-id="ecfab-819">En este ejemplo se usa el búfer de pantalla alternativo, se manipulan las tabulaciones, se establecen los márgenes de desplazamiento y se cambia el juego de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ecfab-819">This example makes use of the alternate screen buffer, manipulating tab stops, setting scrolling margins, and changing the character set.</span></span>

```C
//
// Copyright (C) Microsoft. All rights reserved.
//
#define DEFINE_CONSOLEV2_PROPERTIES

// System headers
#include <windows.h>

// Standard library C-style
#include <wchar.h>
#include <stdlib.h>
#include <stdio.h>

#define ESC "\x1b"
#define CSI "\x1b["

bool EnableVTMode()
{
 // Set output mode to handle virtual terminal sequences
 HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
 if (hOut == INVALID_HANDLE_VALUE)
 {
 return false;
 }

 DWORD dwMode = 0;
 if (!GetConsoleMode(hOut, &dwMode))
 {
 return false;
 }

 dwMode |= ENABLE_VIRTUAL_TERMINAL_PROCESSING;
 if (!SetConsoleMode(hOut, dwMode))
 {
 return false;
 }
 return true;
}

void PrintVerticalBorder()
{
 printf(ESC "(0"); // Enter Line drawing mode
 printf(CSI "104;93m"); // bright yellow on bright blue
 printf("x"); // in line drawing mode, \x78 -> \u2502 "Vertical Bar"
 printf(CSI "0m"); // restore color
 printf(ESC "(B"); // exit line drawing mode
}

void PrintHorizontalBorder(COORD const Size, bool fIsTop)
{
 printf(ESC "(0"); // Enter Line drawing mode
 printf(CSI "104;93m"); // Make the border bright yellow on bright blue
 printf(fIsTop? "l" : "m"); // print left corner 

 for (int i = 1; i < Size.X - 1; i++) 
 printf("q"); // in line drawing mode, \x71 -> \u2500 "HORIZONTAL SCAN LINE-5"

 printf(fIsTop? "k" : "j"); // print right corner
 printf(CSI "0m");
 printf(ESC "(B"); // exit line drawing mode
}

void PrintStatusLine(char* const pszMessage, COORD const Size)
{
 printf(CSI "%d;1H", Size.Y);
 printf(CSI "K"); // clear the line
 printf(pszMessage); 
}

int __cdecl wmain(int argc, WCHAR* argv[])
{ 
 argc; // unused
 argv; // unused
 //First, enable VT mode
 bool fSuccess = EnableVTMode();
 if (!fSuccess)
 {
 printf("Unable to enter VT processing mode. Quitting.\n");
 return -1;
 }
 HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
 if (hOut == INVALID_HANDLE_VALUE)
 {
 printf("Couldn't get the console handle. Quitting.\n");
 return -1;
 }

 CONSOLE_SCREEN_BUFFER_INFO ScreenBufferInfo;
 GetConsoleScreenBufferInfo(hOut, &ScreenBufferInfo);
 COORD Size;
 Size.X = ScreenBufferInfo.srWindow.Right - ScreenBufferInfo.srWindow.Left + 1;
 Size.Y = ScreenBufferInfo.srWindow.Bottom - ScreenBufferInfo.srWindow.Top + 1;

 // Enter the alternate buffer
 printf(CSI "?1049h");

 // Clear screen, tab stops, set, stop at columns 16, 32
 printf(CSI "1;1H");
 printf(CSI "2J"); // Clear screen

 int iNumTabStops = 4; // (0, 20, 40, width)
 printf(CSI "3g"); // clear all tab stops
 printf(CSI "1;20H"); // Move to column 20
 printf(ESC "H"); // set a tab stop

 printf(CSI "1;40H"); // Move to column 40
 printf(ESC "H"); // set a tab stop

 // Set scrolling margins to 3, h-2
 printf(CSI "3;%dr", Size.Y-2);
 int iNumLines = Size.Y - 4;

 printf(CSI "1;1H");
 printf(CSI "102;30m");
 printf("Windows 10 Anniversary Update - VT Example"); 
 printf(CSI "0m");

 // Print a top border - Yellow
 printf(CSI "2;1H");
 PrintHorizontalBorder(Size, true);

 // // Print a bottom border
 printf(CSI "%d;1H", Size.Y-1);
 PrintHorizontalBorder(Size, false);

 wchar_t wch;

 // draw columns
 printf(CSI "3;1H"); 
 int line = 0;
 for (line = 0; line < iNumLines * iNumTabStops; line++)
 {
 PrintVerticalBorder();
 if (line + 1 != iNumLines * iNumTabStops) // don't advance to next line if this is the last line
 printf("\t"); // advance to next tab stop

 }

 PrintStatusLine("Press any key to see text printed between tab stops.", Size);
 wch = _getwch();

 // Fill columns with output
 printf(CSI "3;1H"); 
 for (line = 0; line < iNumLines; line++)
 {
 int tab = 0;
 for (tab = 0; tab < iNumTabStops-1; tab++)
 {
 PrintVerticalBorder();
 printf("line=%d", line);
 printf("\t"); // advance to next tab stop
 }
 PrintVerticalBorder();// print border at right side
 if (line+1 != iNumLines)
 printf("\t"); // advance to next tab stop, (on the next line)
 }

 PrintStatusLine("Press any key to demonstrate scroll margins", Size);
 wch = _getwch();

 printf(CSI "3;1H"); 
 for (line = 0; line < iNumLines * 2; line++)
 {
 printf(CSI "K"); // clear the line
 int tab = 0;
 for (tab = 0; tab < iNumTabStops-1; tab++)
 {
 PrintVerticalBorder();
 printf("line=%d", line);
 printf("\t"); // advance to next tab stop
 }
 PrintVerticalBorder(); // print border at right side
 if (line+1 != iNumLines * 2)
 {
 printf("\n"); //Advance to next line. If we're at the bottom of the margins, the text will scroll.
 printf("\r"); //return to first col in buffer
 }
 }

 PrintStatusLine("Press any key to exit", Size);
 wch = _getwch();

 // Exit the alternate buffer
 printf(CSI "?1049l");

}
```








