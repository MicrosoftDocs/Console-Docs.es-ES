---
title: Secuencias de terminal virtuales de la consola
description: Las secuencias de terminal virtuales son secuencias de caracteres de control que pueden controlar el movimiento del cursor, el modo de color/fuente y otras operaciones cuando se escriben en el flujo de salida.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: A5C553A5-FD84-4D16-A814-EDB3B8699B91
ms.openlocfilehash: 45ee5518ec8ea2da840d2a4442efd9e0d4346526
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039153"
---
# <a name="console-virtual-terminal-sequences"></a><span data-ttu-id="23725-104">Secuencias de terminal virtuales de la consola</span><span class="sxs-lookup"><span data-stu-id="23725-104">Console Virtual Terminal Sequences</span></span>


<span data-ttu-id="23725-105">Las secuencias de terminal virtuales son secuencias de caracteres de control que pueden controlar el movimiento del cursor, el modo de color/fuente y otras operaciones cuando se escriben en el flujo de salida.</span><span class="sxs-lookup"><span data-stu-id="23725-105">Virtual terminal sequences are control character sequences that can control cursor movement, color/font mode, and other operations when written to the output stream.</span></span> <span data-ttu-id="23725-106">También se pueden recibir secuencias en el flujo de entrada en respuesta a una secuencia de información de consulta de flujo de salida o como codificación de datos proporcionados por el usuario cuando se establece el modo adecuado.</span><span class="sxs-lookup"><span data-stu-id="23725-106">Sequences may also be received on the input stream in response to an output stream query information sequence or as an encoding of user input when the appropriate mode is set.</span></span>

<span data-ttu-id="23725-107">Puede usar las funciones [**GetConsoleMode**](getconsolemode.md) y [**SetConsoleMode**](setconsolemode.md) para configurar este comportamiento.</span><span class="sxs-lookup"><span data-stu-id="23725-107">You can use [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions to configure this behavior.</span></span> <span data-ttu-id="23725-108">Al final de este documento, se incluye un ejemplo de la forma sugerida de habilitar los comportamientos de terminal virtual.</span><span class="sxs-lookup"><span data-stu-id="23725-108">A sample of the suggested way to enable virtual terminal behaviors is included at the end of this document.</span></span>

<span data-ttu-id="23725-109">El comportamiento de las secuencias siguientes se basa en las tecnologías de VT100 y de emulador de terminal derivado, especialmente en el emulador de terminal de xterm.</span><span class="sxs-lookup"><span data-stu-id="23725-109">The behavior of the following sequences is based on the VT100 and derived terminal emulator technologies, most specifically the xterm terminal emulator.</span></span> <span data-ttu-id="23725-110">Puede encontrar más información sobre las secuencias de terminal en <http://vt100.net> y en <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html> .</span><span class="sxs-lookup"><span data-stu-id="23725-110">More information about terminal sequences can be found at <http://vt100.net> and at <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span></span>

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span data-ttu-id="23725-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Secuencias de salida</span><span class="sxs-lookup"><span data-stu-id="23725-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Output Sequences</span></span>


<span data-ttu-id="23725-112">El host de consola intercepta las siguientes secuencias de terminal cuando se escriben en el flujo de salida, si la marca habilitar el \_ \_ \_ procesamiento de terminal virtual está establecida en el identificador de búfer de pantalla mediante la función [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="23725-112">The following terminal sequences are intercepted by the console host when written into the output stream, if the ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING flag is set on the screen buffer handle using the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="23725-113">Tenga en cuenta que la marca deshabilitar \_ \_ devolución automática de nueva línea \_ también puede ser útil para emular la posición del cursor y el comportamiento de desplazamiento de otros emuladores de terminal en relación con los caracteres escritos en la columna final de cualquier fila.</span><span class="sxs-lookup"><span data-stu-id="23725-113">Note that the DISABLE\_NEWLINE\_AUTO\_RETURN flag may also be useful in emulating the cursor positioning and scrolling behavior of other terminal emulators in relation to characters written to the final column in any row.</span></span>

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span data-ttu-id="23725-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Posición de cursor simple</span><span class="sxs-lookup"><span data-stu-id="23725-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Simple Cursor Positioning</span></span>


<span data-ttu-id="23725-115">En todas las descripciones siguientes, ESC siempre es el valor hexadecimal 0x1B.</span><span class="sxs-lookup"><span data-stu-id="23725-115">In all of the following descriptions, ESC is always the hexadecimal value 0x1B.</span></span> <span data-ttu-id="23725-116">No se incluirán espacios en las secuencias de terminal.</span><span class="sxs-lookup"><span data-stu-id="23725-116">No spaces are to be included in terminal sequences.</span></span> <span data-ttu-id="23725-117">Para obtener un ejemplo de cómo se usan estas secuencias en la práctica, vea el [ejemplo](#example) al final de este tema.</span><span class="sxs-lookup"><span data-stu-id="23725-117">For an example of how these sequences are used in practice, please see the [example](#example) at the end of this topic.</span></span>

<span data-ttu-id="23725-118">En la tabla siguiente se describen las secuencias de escape simples con un solo comando de acción directamente después del carácter ESC.</span><span class="sxs-lookup"><span data-stu-id="23725-118">The following table describes simple escape sequences with a single action command directly after the ESC character.</span></span> <span data-ttu-id="23725-119">Estas secuencias no tienen ningún parámetro y surten efecto inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="23725-119">These sequences have no parameters and take effect immediately.</span></span>

<span data-ttu-id="23725-120">Todos los comandos de esta tabla suelen ser equivalentes a llamar a la API de la consola de [**SetConsoleCursorPosition**](setconsolecursorposition.md) para colocar el cursor.</span><span class="sxs-lookup"><span data-stu-id="23725-120">All commands in this table are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API to place the cursor.</span></span>

<span data-ttu-id="23725-121">El movimiento del cursor estará limitado por la ventanilla actual en el búfer.</span><span class="sxs-lookup"><span data-stu-id="23725-121">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="23725-122">No se producirá el desplazamiento (si está disponible).</span><span class="sxs-lookup"><span data-stu-id="23725-122">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="23725-123">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-123">Sequence</span></span> | <span data-ttu-id="23725-124">Abreviada</span><span class="sxs-lookup"><span data-stu-id="23725-124">Shorthand</span></span> | <span data-ttu-id="23725-125">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-125">Behavior</span></span> |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="23725-126">ESC A</span><span class="sxs-lookup"><span data-stu-id="23725-126">ESC A</span></span> | <span data-ttu-id="23725-127">CUU</span><span class="sxs-lookup"><span data-stu-id="23725-127">CUU</span></span> | <span data-ttu-id="23725-128">Cursor hacia arriba en 1</span><span class="sxs-lookup"><span data-stu-id="23725-128">Cursor Up by 1</span></span> |
| <span data-ttu-id="23725-129">ESC B</span><span class="sxs-lookup"><span data-stu-id="23725-129">ESC B</span></span> | <span data-ttu-id="23725-130">CUD</span><span class="sxs-lookup"><span data-stu-id="23725-130">CUD</span></span> | <span data-ttu-id="23725-131">Cursor hacia abajo en 1</span><span class="sxs-lookup"><span data-stu-id="23725-131">Cursor Down by 1</span></span> |
| <span data-ttu-id="23725-132">ESC C</span><span class="sxs-lookup"><span data-stu-id="23725-132">ESC C</span></span> | <span data-ttu-id="23725-133">CUF</span><span class="sxs-lookup"><span data-stu-id="23725-133">CUF</span></span> | <span data-ttu-id="23725-134">Cursor hacia delante (derecha) en 1</span><span class="sxs-lookup"><span data-stu-id="23725-134">Cursor Forward (Right) by 1</span></span> |
| <span data-ttu-id="23725-135">ESC D</span><span class="sxs-lookup"><span data-stu-id="23725-135">ESC D</span></span> | <span data-ttu-id="23725-136">CUB</span><span class="sxs-lookup"><span data-stu-id="23725-136">CUB</span></span> | <span data-ttu-id="23725-137">Cursor hacia atrás (izquierda) en 1</span><span class="sxs-lookup"><span data-stu-id="23725-137">Cursor Backward (Left) by 1</span></span> |
| <span data-ttu-id="23725-138">ESC M</span><span class="sxs-lookup"><span data-stu-id="23725-138">ESC M</span></span> | <span data-ttu-id="23725-139">Instancia reservada</span><span class="sxs-lookup"><span data-stu-id="23725-139">RI</span></span> | <span data-ttu-id="23725-140">Reverse index: realiza la operación inversa de \\ n, mueve el cursor una línea hacia arriba, mantiene la posición horizontal y desplaza el búfer si es necesario.\*</span><span class="sxs-lookup"><span data-stu-id="23725-140">Reverse Index – Performs the reverse operation of \\n, moves cursor up one line, maintains horizontal position, scrolls buffer if necessary\*</span></span> |
| <span data-ttu-id="23725-141">ESC 7</span><span class="sxs-lookup"><span data-stu-id="23725-141">ESC 7</span></span> | <span data-ttu-id="23725-142">DECSC</span><span class="sxs-lookup"><span data-stu-id="23725-142">DECSC</span></span> | <span data-ttu-id="23725-143">Guardar la posición del cursor en la memoria\*\*</span><span class="sxs-lookup"><span data-stu-id="23725-143">Save Cursor Position in Memory\*\*</span></span> |
| <span data-ttu-id="23725-144">ESC 8</span><span class="sxs-lookup"><span data-stu-id="23725-144">ESC 8</span></span> | <span data-ttu-id="23725-145">DECSR</span><span class="sxs-lookup"><span data-stu-id="23725-145">DECSR</span></span> | <span data-ttu-id="23725-146">Restaurar la posición del cursor desde la memoria\*\*</span><span class="sxs-lookup"><span data-stu-id="23725-146">Restore Cursor Position from Memory\*\*</span></span> |



> [!NOTE]
><span data-ttu-id="23725-147">\* Si hay márgenes de desplazamiento establecidos, RI dentro de los márgenes solo se desplazará por el contenido de los márgenes y dejará la ventanilla sin cambios.</span><span class="sxs-lookup"><span data-stu-id="23725-147">\* If there are scroll margins set, RI inside the margins will scroll only the contents of the margins, and leave the viewport unchanged.</span></span> <span data-ttu-id="23725-148">(Consulte márgenes de desplazamiento)</span><span class="sxs-lookup"><span data-stu-id="23725-148">(See Scrolling Margins)</span></span>
>
><span data-ttu-id="23725-149">\*\*No habrá ningún valor guardado en la memoria hasta el primer uso del comando Guardar.</span><span class="sxs-lookup"><span data-stu-id="23725-149">\*\*There will be no value saved in memory until the first use of the save command.</span></span> <span data-ttu-id="23725-150">La única manera de tener acceso al valor guardado es con el comando restore.</span><span class="sxs-lookup"><span data-stu-id="23725-150">The only way to access the saved value is with the restore command.</span></span>

## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span data-ttu-id="23725-151"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Posición del cursor</span><span class="sxs-lookup"><span data-stu-id="23725-151"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursor Positioning</span></span>


<span data-ttu-id="23725-152">Las tablas siguientes abarcan las secuencias de tipo de presentador de secuencia de control (CSI).</span><span class="sxs-lookup"><span data-stu-id="23725-152">The following tables encompass Control Sequence Introducer (CSI) type sequences.</span></span> <span data-ttu-id="23725-153">Todas las secuencias CSI comienzan con ESC (0x1B) seguidos de \[ (corchete de apertura, 0x5B) y pueden contener parámetros de longitud variable para especificar más información para cada operación.</span><span class="sxs-lookup"><span data-stu-id="23725-153">All CSI sequences start with ESC (0x1B) followed by \[ (left bracket, 0x5B) and may contain parameters of variable length to specify more information for each operation.</span></span> <span data-ttu-id="23725-154">Esto se representará con la forma abreviada &lt; n &gt; .</span><span class="sxs-lookup"><span data-stu-id="23725-154">This will be represented by the shorthand &lt;n&gt;.</span></span> <span data-ttu-id="23725-155">Cada tabla siguiente está agrupada por funcionalidad con notas debajo de cada tabla en la que se explica cómo funciona el grupo.</span><span class="sxs-lookup"><span data-stu-id="23725-155">Each table below is grouped by functionality with notes below each table explaining how the group works.</span></span>

<span data-ttu-id="23725-156">En todos los parámetros, se aplican las reglas siguientes, a menos que se indique lo contrario:</span><span class="sxs-lookup"><span data-stu-id="23725-156">For all parameters, the following rules apply unless otherwise noted:</span></span>

- <span data-ttu-id="23725-157">&lt;n &gt; representa la distancia que se va a trasladar y es un parámetro opcional</span><span class="sxs-lookup"><span data-stu-id="23725-157">&lt;n&gt; represents the distance to move and is an optional parameter</span></span>
- <span data-ttu-id="23725-158">Si &lt; n &gt; se omite o es igual a 0, se tratará como 1</span><span class="sxs-lookup"><span data-stu-id="23725-158">If &lt;n&gt; is omitted or equals 0, it will be treated as a 1</span></span>
- <span data-ttu-id="23725-159">&lt;n &gt; no puede ser mayor que 32.767 (valor corto máximo)</span><span class="sxs-lookup"><span data-stu-id="23725-159">&lt;n&gt; cannot be larger than 32,767 (maximum short value)</span></span>
- <span data-ttu-id="23725-160">&lt;n &gt; no puede ser negativo</span><span class="sxs-lookup"><span data-stu-id="23725-160">&lt;n&gt; cannot be negative</span></span>

<span data-ttu-id="23725-161">Todos los comandos de esta sección suelen ser equivalentes a llamar a la API de la consola de [**SetConsoleCursorPosition**](setconsolecursorposition.md) .</span><span class="sxs-lookup"><span data-stu-id="23725-161">All commands in this section are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API.</span></span>

<span data-ttu-id="23725-162">El movimiento del cursor estará limitado por la ventanilla actual en el búfer.</span><span class="sxs-lookup"><span data-stu-id="23725-162">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="23725-163">No se producirá el desplazamiento (si está disponible).</span><span class="sxs-lookup"><span data-stu-id="23725-163">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="23725-164">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-164">Sequence</span></span> | <span data-ttu-id="23725-165">Código</span><span class="sxs-lookup"><span data-stu-id="23725-165">Code</span></span> | <span data-ttu-id="23725-166">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-166">Description</span></span> | <span data-ttu-id="23725-167">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-167">Behavior</span></span> |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="23725-168">ESC \[ &lt; n &gt; A</span><span class="sxs-lookup"><span data-stu-id="23725-168">ESC \[ &lt;n&gt; A</span></span> | <span data-ttu-id="23725-169">CUU</span><span class="sxs-lookup"><span data-stu-id="23725-169">CUU</span></span> | <span data-ttu-id="23725-170">Cursor hacia arriba</span><span class="sxs-lookup"><span data-stu-id="23725-170">Cursor Up</span></span> | <span data-ttu-id="23725-171">Cursor hacia arriba por &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="23725-171">Cursor up by &lt;n&gt;</span></span> |
| <span data-ttu-id="23725-172">ESC \[ &lt; n &gt; B</span><span class="sxs-lookup"><span data-stu-id="23725-172">ESC \[ &lt;n&gt; B</span></span> | <span data-ttu-id="23725-173">CUD</span><span class="sxs-lookup"><span data-stu-id="23725-173">CUD</span></span> | <span data-ttu-id="23725-174">Cursor hacia abajo</span><span class="sxs-lookup"><span data-stu-id="23725-174">Cursor Down</span></span> | <span data-ttu-id="23725-175">Cursor hacia abajo por &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="23725-175">Cursor down by &lt;n&gt;</span></span> |
| <span data-ttu-id="23725-176">ESC \[ &lt; n &gt; C</span><span class="sxs-lookup"><span data-stu-id="23725-176">ESC \[ &lt;n&gt; C</span></span> | <span data-ttu-id="23725-177">CUF</span><span class="sxs-lookup"><span data-stu-id="23725-177">CUF</span></span> | <span data-ttu-id="23725-178">Cursor hacia delante</span><span class="sxs-lookup"><span data-stu-id="23725-178">Cursor Forward</span></span> | <span data-ttu-id="23725-179">Cursor hacia delante (derecha) por &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="23725-179">Cursor forward (Right) by &lt;n&gt;</span></span> |
| <span data-ttu-id="23725-180">ESC \[ &lt; n &gt; D</span><span class="sxs-lookup"><span data-stu-id="23725-180">ESC \[ &lt;n&gt; D</span></span> | <span data-ttu-id="23725-181">CUB</span><span class="sxs-lookup"><span data-stu-id="23725-181">CUB</span></span> | <span data-ttu-id="23725-182">Cursor hacia atrás</span><span class="sxs-lookup"><span data-stu-id="23725-182">Cursor Backward</span></span> | <span data-ttu-id="23725-183">Cursor hacia atrás (izquierda) por &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="23725-183">Cursor backward (Left) by &lt;n&gt;</span></span> |
| <span data-ttu-id="23725-184">ESC \[ &lt; n &gt; E</span><span class="sxs-lookup"><span data-stu-id="23725-184">ESC \[ &lt;n&gt; E</span></span> | <span data-ttu-id="23725-185">CNL</span><span class="sxs-lookup"><span data-stu-id="23725-185">CNL</span></span> | <span data-ttu-id="23725-186">Cursor siguiente línea</span><span class="sxs-lookup"><span data-stu-id="23725-186">Cursor Next Line</span></span> | <span data-ttu-id="23725-187">Cursor hacia abajo &lt; n &gt; líneas desde la posición actual</span><span class="sxs-lookup"><span data-stu-id="23725-187">Cursor down &lt;n&gt; lines from current position</span></span> |
| <span data-ttu-id="23725-188">ESC \[ &lt; n &gt; F</span><span class="sxs-lookup"><span data-stu-id="23725-188">ESC \[ &lt;n&gt; F</span></span> | <span data-ttu-id="23725-189">CPL</span><span class="sxs-lookup"><span data-stu-id="23725-189">CPL</span></span> | <span data-ttu-id="23725-190">Línea de cursor anterior</span><span class="sxs-lookup"><span data-stu-id="23725-190">Cursor Previous Line</span></span> | <span data-ttu-id="23725-191">Cursor hacia arriba &lt; n &gt; líneas desde la posición actual</span><span class="sxs-lookup"><span data-stu-id="23725-191">Cursor up &lt;n&gt; lines from current position</span></span> |
| <span data-ttu-id="23725-192">ESC \[ &lt; n &gt; G</span><span class="sxs-lookup"><span data-stu-id="23725-192">ESC \[ &lt;n&gt; G</span></span> | <span data-ttu-id="23725-193">CHA</span><span class="sxs-lookup"><span data-stu-id="23725-193">CHA</span></span> | <span data-ttu-id="23725-194">Cursor horizontal absoluto</span><span class="sxs-lookup"><span data-stu-id="23725-194">Cursor Horizontal Absolute</span></span> | <span data-ttu-id="23725-195">El cursor se mueve a &lt; &gt; la posición n horizontalmente en la línea actual</span><span class="sxs-lookup"><span data-stu-id="23725-195">Cursor moves to &lt;n&gt;th position horizontally in the current line</span></span> |
| <span data-ttu-id="23725-196">ESC \[ &lt; n &gt; d</span><span class="sxs-lookup"><span data-stu-id="23725-196">ESC \[ &lt;n&gt; d</span></span> | <span data-ttu-id="23725-197">VPA</span><span class="sxs-lookup"><span data-stu-id="23725-197">VPA</span></span> | <span data-ttu-id="23725-198">Posición de línea vertical absoluta</span><span class="sxs-lookup"><span data-stu-id="23725-198">Vertical Line Position Absolute</span></span> | <span data-ttu-id="23725-199">El cursor se mueve a la &lt; &gt; posición n verticalmente en la columna actual</span><span class="sxs-lookup"><span data-stu-id="23725-199">Cursor moves to the &lt;n&gt;th position vertically in the current column</span></span> |
| <span data-ttu-id="23725-200">ESC \[ &lt; y &gt; ; &lt; x &gt; H</span><span class="sxs-lookup"><span data-stu-id="23725-200">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span></span> | <span data-ttu-id="23725-201">CUP</span><span class="sxs-lookup"><span data-stu-id="23725-201">CUP</span></span> | <span data-ttu-id="23725-202">Posición del cursor</span><span class="sxs-lookup"><span data-stu-id="23725-202">Cursor Position</span></span> | <span data-ttu-id="23725-203">\*El cursor se mueve a &lt; x &gt; ; &lt; coordenada y &gt; dentro de la ventanilla, donde &lt; x &gt; es la columna de la &lt; &gt; línea y</span><span class="sxs-lookup"><span data-stu-id="23725-203">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="23725-204">ESC \[ &lt; y &gt; ; &lt; x &gt; f</span><span class="sxs-lookup"><span data-stu-id="23725-204">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span></span> | <span data-ttu-id="23725-205">HVP</span><span class="sxs-lookup"><span data-stu-id="23725-205">HVP</span></span> | <span data-ttu-id="23725-206">Posición vertical horizontal</span><span class="sxs-lookup"><span data-stu-id="23725-206">Horizontal Vertical Position</span></span> | <span data-ttu-id="23725-207">\*El cursor se mueve a &lt; x &gt; ; &lt; coordenada y &gt; dentro de la ventanilla, donde &lt; x &gt; es la columna de la &lt; &gt; línea y</span><span class="sxs-lookup"><span data-stu-id="23725-207">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="23725-208">ESC \[ s</span><span class="sxs-lookup"><span data-stu-id="23725-208">ESC \[ s</span></span> | <span data-ttu-id="23725-209">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="23725-209">ANSISYSSC</span></span> | <span data-ttu-id="23725-210">Guardar cursor: emulación de Ansi.sys</span><span class="sxs-lookup"><span data-stu-id="23725-210">Save Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="23725-211">\*\*Sin parámetros, realiza una operación de guardar el cursor como DECSC</span><span class="sxs-lookup"><span data-stu-id="23725-211">\*\*With no parameters, performs a save cursor operation like DECSC</span></span> |
| <span data-ttu-id="23725-212">ESC \[ u</span><span class="sxs-lookup"><span data-stu-id="23725-212">ESC \[ u</span></span> | <span data-ttu-id="23725-213">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="23725-213">ANSISYSSC</span></span> | <span data-ttu-id="23725-214">Cursor de restauración: emulación de Ansi.sys</span><span class="sxs-lookup"><span data-stu-id="23725-214">Restore Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="23725-215">\*\*Sin parámetros, realiza una operación de restauración de cursor como DECRC</span><span class="sxs-lookup"><span data-stu-id="23725-215">\*\*With no parameters, performs a restore cursor operation like DECRC</span></span> |



> [!NOTE]
><span data-ttu-id="23725-216">\*&lt;los &gt; parámetros x e y &lt; &gt; tienen las mismas limitaciones que &lt; n &gt; anteriores.</span><span class="sxs-lookup"><span data-stu-id="23725-216">\*&lt;x&gt; and &lt;y&gt; parameters have the same limitations as &lt;n&gt; above.</span></span> <span data-ttu-id="23725-217">Si &lt; &gt; &lt; se omiten x e y, se &gt; establecerán en 1; 1.</span><span class="sxs-lookup"><span data-stu-id="23725-217">If &lt;x&gt; and &lt;y&gt; are omitted, they will be set to 1;1.</span></span>
>
><span data-ttu-id="23725-218">\*\*ANSI.sys documentación histórica puede encontrarse en <https://msdn.microsoft.com/library/cc722862.aspx> y se implementa por comodidad y compatibilidad.</span><span class="sxs-lookup"><span data-stu-id="23725-218">\*\*ANSI.sys historical documentation can be found at <https://msdn.microsoft.com/library/cc722862.aspx> and is implemented for convenience/compatibility.</span></span>



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span data-ttu-id="23725-219"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Visibilidad del cursor</span><span class="sxs-lookup"><span data-stu-id="23725-219"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursor Visibility</span></span>


<span data-ttu-id="23725-220">Los siguientes comandos controlan la visibilidad del cursor y su estado de parpadeo.</span><span class="sxs-lookup"><span data-stu-id="23725-220">The following commands control the visibility of the cursor and its blinking state.</span></span> <span data-ttu-id="23725-221">Las secuencias DECTCEM suelen ser equivalentes a llamar a la API de la consola de [**SetConsoleCursorInfo**](setconsolecursorinfo.md) para alternar la visibilidad del cursor.</span><span class="sxs-lookup"><span data-stu-id="23725-221">The DECTCEM sequences are generally equivalent to calling [**SetConsoleCursorInfo**](setconsolecursorinfo.md) console API to toggle cursor visibility.</span></span>


| <span data-ttu-id="23725-222">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-222">Sequence</span></span> | <span data-ttu-id="23725-223">Código</span><span class="sxs-lookup"><span data-stu-id="23725-223">Code</span></span> | <span data-ttu-id="23725-224">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-224">Description</span></span> | <span data-ttu-id="23725-225">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-225">Behavior</span></span> |
|---------------|---------|------------------------------|---------------------------|
| <span data-ttu-id="23725-226">\[¿ESC?</span><span class="sxs-lookup"><span data-stu-id="23725-226">ESC \[ ?</span></span> <span data-ttu-id="23725-227">12 h</span><span class="sxs-lookup"><span data-stu-id="23725-227">12 h</span></span> | <span data-ttu-id="23725-228">ATT160</span><span class="sxs-lookup"><span data-stu-id="23725-228">ATT160</span></span> | <span data-ttu-id="23725-229">Cursor de texto habilitar parpadeo</span><span class="sxs-lookup"><span data-stu-id="23725-229">Text Cursor Enable Blinking</span></span> | <span data-ttu-id="23725-230">Iniciar el parpadeo del cursor</span><span class="sxs-lookup"><span data-stu-id="23725-230">Start the cursor blinking</span></span> |
| <span data-ttu-id="23725-231">\[¿ESC?</span><span class="sxs-lookup"><span data-stu-id="23725-231">ESC \[ ?</span></span> <span data-ttu-id="23725-232">12 l</span><span class="sxs-lookup"><span data-stu-id="23725-232">12 l</span></span> | <span data-ttu-id="23725-233">ATT160</span><span class="sxs-lookup"><span data-stu-id="23725-233">ATT160</span></span> | <span data-ttu-id="23725-234">Deshabilitar parpadeo de cursor de texto</span><span class="sxs-lookup"><span data-stu-id="23725-234">Text Cursor Disable Blinking</span></span> | <span data-ttu-id="23725-235">Detener el parpadeo del cursor</span><span class="sxs-lookup"><span data-stu-id="23725-235">Stop blinking the cursor</span></span> |
| <span data-ttu-id="23725-236">\[¿ESC?</span><span class="sxs-lookup"><span data-stu-id="23725-236">ESC \[ ?</span></span> <span data-ttu-id="23725-237">25 h</span><span class="sxs-lookup"><span data-stu-id="23725-237">25 h</span></span> | <span data-ttu-id="23725-238">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="23725-238">DECTCEM</span></span> | <span data-ttu-id="23725-239">Modo de activación de cursor de texto, Mostrar</span><span class="sxs-lookup"><span data-stu-id="23725-239">Text Cursor Enable Mode Show</span></span> | <span data-ttu-id="23725-240">Mostrar el cursor</span><span class="sxs-lookup"><span data-stu-id="23725-240">Show the cursor</span></span> |
| <span data-ttu-id="23725-241">\[¿ESC?</span><span class="sxs-lookup"><span data-stu-id="23725-241">ESC \[ ?</span></span> <span data-ttu-id="23725-242">25 l</span><span class="sxs-lookup"><span data-stu-id="23725-242">25 l</span></span> | <span data-ttu-id="23725-243">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="23725-243">DECTCEM</span></span> | <span data-ttu-id="23725-244">Ocultar modo de cursor de texto</span><span class="sxs-lookup"><span data-stu-id="23725-244">Text Cursor Enable Mode Hide</span></span> | <span data-ttu-id="23725-245">Ocultar el cursor</span><span class="sxs-lookup"><span data-stu-id="23725-245">Hide the cursor</span></span> |

> [!TIP]
> <span data-ttu-id="23725-246">El final de las secuencias de la habilitación termina con un carácter H en minúscula ( `h` ) y el extremo de las secuencias deshabilitadas en un carácter L en minúscula ( `l` ).</span><span class="sxs-lookup"><span data-stu-id="23725-246">The enable sequences end in a lowercase H character (`h`) and the disable sequences end in a lowercase L character (`l`).</span></span>

## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span data-ttu-id="23725-247"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Posición de la ventanilla</span><span class="sxs-lookup"><span data-stu-id="23725-247"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Viewport Positioning</span></span>


<span data-ttu-id="23725-248">Todos los comandos de esta sección suelen ser equivalentes a llamar a la API de la consola de [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) para trasladar el contenido del búfer de la consola.</span><span class="sxs-lookup"><span data-stu-id="23725-248">All commands in this section are generally equivalent to calling [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console API to move the contents of the console buffer.</span></span>

<span data-ttu-id="23725-249">**PRECAUCIÓN** Los nombres de comando son engañosos.</span><span class="sxs-lookup"><span data-stu-id="23725-249">**Caution** The command names are misleading.</span></span> <span data-ttu-id="23725-250">Desplazar hace referencia a la dirección en la que se mueve el texto durante la operación, no a la manera en que la ventanilla parecería moverse.</span><span class="sxs-lookup"><span data-stu-id="23725-250">Scroll refers to which direction the text moves during the operation, not which way the viewport would seem to move.</span></span>




| <span data-ttu-id="23725-251">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-251">Sequence</span></span> | <span data-ttu-id="23725-252">Código</span><span class="sxs-lookup"><span data-stu-id="23725-252">Code</span></span> | <span data-ttu-id="23725-253">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-253">Description</span></span> | <span data-ttu-id="23725-254">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-254">Behavior</span></span> |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="23725-255">ESC \[ &lt; n &gt; S</span><span class="sxs-lookup"><span data-stu-id="23725-255">ESC \[ &lt;n&gt; S</span></span> | <span data-ttu-id="23725-256">SU</span><span class="sxs-lookup"><span data-stu-id="23725-256">SU</span></span> | <span data-ttu-id="23725-257">Desplazar hacia arriba</span><span class="sxs-lookup"><span data-stu-id="23725-257">Scroll Up</span></span> | <span data-ttu-id="23725-258">Desplazar texto hacia arriba por &lt; n &gt; .</span><span class="sxs-lookup"><span data-stu-id="23725-258">Scroll text up by &lt;n&gt;.</span></span> <span data-ttu-id="23725-259">También conocido como panorámica hacia abajo, las nuevas líneas se rellenan desde la parte inferior de la pantalla</span><span class="sxs-lookup"><span data-stu-id="23725-259">Also known as pan down, new lines fill in from the bottom of the screen</span></span> |
| <span data-ttu-id="23725-260">ESC \[ &lt; n &gt; T</span><span class="sxs-lookup"><span data-stu-id="23725-260">ESC \[ &lt;n&gt; T</span></span> | <span data-ttu-id="23725-261">SD</span><span class="sxs-lookup"><span data-stu-id="23725-261">SD</span></span> | <span data-ttu-id="23725-262">Desplazar hacia abajo</span><span class="sxs-lookup"><span data-stu-id="23725-262">Scroll Down</span></span> | <span data-ttu-id="23725-263">Desplácese hacia abajo por &lt; n &gt; .</span><span class="sxs-lookup"><span data-stu-id="23725-263">Scroll down by &lt;n&gt;.</span></span> <span data-ttu-id="23725-264">También conocido como pan up, nuevas líneas que se rellenan desde la parte superior de la pantalla</span><span class="sxs-lookup"><span data-stu-id="23725-264">Also known as pan up, new lines fill in from the top of the screen</span></span> |



<span data-ttu-id="23725-265">El texto se mueve a partir de la línea en la que se encuentra el cursor.</span><span class="sxs-lookup"><span data-stu-id="23725-265">The text is moved starting with the line the cursor is on.</span></span> <span data-ttu-id="23725-266">Si el cursor está en la fila central de la ventanilla, al desplazarse hacia arriba se moverá la mitad inferior de la ventanilla y se insertarán líneas en blanco en la parte inferior.</span><span class="sxs-lookup"><span data-stu-id="23725-266">If the cursor is on the middle row of the viewport, then scroll up would move the bottom half of the viewport, and insert blank lines at the bottom.</span></span> <span data-ttu-id="23725-267">Desplazarse hacia abajo moverá la mitad superior de las filas de la ventanilla e insertará nuevas líneas en la parte superior.</span><span class="sxs-lookup"><span data-stu-id="23725-267">Scroll down would move the top half of the viewport’s rows, and insert new lines at the top.</span></span>

<span data-ttu-id="23725-268">También es importante tener en cuenta que los márgenes de desplazamiento también afectan hacia arriba y hacia abajo.</span><span class="sxs-lookup"><span data-stu-id="23725-268">Also important to note is scroll up and down are also affected by the scrolling margins.</span></span> <span data-ttu-id="23725-269">Desplazarse hacia arriba y hacia abajo no afectará a las líneas fuera de los márgenes desplazados.</span><span class="sxs-lookup"><span data-stu-id="23725-269">Scroll up and down won’t affect any lines outside the scrolling margins.</span></span>

<span data-ttu-id="23725-270">El valor predeterminado de &lt; n &gt; es 1 y el valor se puede omitir opcionalmente.</span><span class="sxs-lookup"><span data-stu-id="23725-270">The default value for &lt;n&gt; is 1, and the value can be optionally omitted.</span></span>

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span data-ttu-id="23725-271"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Modificación de texto</span><span class="sxs-lookup"><span data-stu-id="23725-271"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Text Modification</span></span>


<span data-ttu-id="23725-272">Todos los comandos de esta sección suelen ser equivalentes a llamar a las API de consola [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)y [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) para modificar el contenido del búfer de texto.</span><span class="sxs-lookup"><span data-stu-id="23725-272">All commands in this section are generally equivalent to calling [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md), and [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console APIs to modify the text buffer contents.</span></span>


| <span data-ttu-id="23725-273">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-273">Sequence</span></span> | <span data-ttu-id="23725-274">Código</span><span class="sxs-lookup"><span data-stu-id="23725-274">Code</span></span> | <span data-ttu-id="23725-275">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-275">Description</span></span> | <span data-ttu-id="23725-276">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-276">Behavior</span></span> |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="23725-277">ESC \[ &lt; n&gt; @</span><span class="sxs-lookup"><span data-stu-id="23725-277">ESC \[ &lt;n&gt; @</span></span> | <span data-ttu-id="23725-278">ICH</span><span class="sxs-lookup"><span data-stu-id="23725-278">ICH</span></span> | <span data-ttu-id="23725-279">Insertar carácter</span><span class="sxs-lookup"><span data-stu-id="23725-279">Insert Character</span></span> | <span data-ttu-id="23725-280">Insertar &lt; n &gt; espacios en la posición actual del cursor, desplazando todo el texto existente a la derecha.</span><span class="sxs-lookup"><span data-stu-id="23725-280">Insert &lt;n&gt; spaces at the current cursor position, shifting all existing text to the right.</span></span> <span data-ttu-id="23725-281">Se quita el texto que sale de la pantalla hacia la derecha.</span><span class="sxs-lookup"><span data-stu-id="23725-281">Text exiting the screen to the right is removed.</span></span> |
| <span data-ttu-id="23725-282">ESC \[ &lt; n &gt; P</span><span class="sxs-lookup"><span data-stu-id="23725-282">ESC \[ &lt;n&gt; P</span></span> | <span data-ttu-id="23725-283">DCH</span><span class="sxs-lookup"><span data-stu-id="23725-283">DCH</span></span> | <span data-ttu-id="23725-284">Eliminar carácter</span><span class="sxs-lookup"><span data-stu-id="23725-284">Delete Character</span></span> | <span data-ttu-id="23725-285">Elimine &lt; n &gt; caracteres en la posición actual del cursor, desplazando los caracteres de espacio desde el borde derecho de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="23725-285">Delete &lt;n&gt; characters at the current cursor position, shifting in space characters from the right edge of the screen.</span></span> |
| <span data-ttu-id="23725-286">ESC \[ &lt; n &gt; X</span><span class="sxs-lookup"><span data-stu-id="23725-286">ESC \[ &lt;n&gt; X</span></span> | <span data-ttu-id="23725-287">ECH</span><span class="sxs-lookup"><span data-stu-id="23725-287">ECH</span></span> | <span data-ttu-id="23725-288">Borrar carácter</span><span class="sxs-lookup"><span data-stu-id="23725-288">Erase Character</span></span> | <span data-ttu-id="23725-289">Borrar &lt; n &gt; caracteres de la posición actual del cursor si se sobrescriben con un carácter de espacio.</span><span class="sxs-lookup"><span data-stu-id="23725-289">Erase &lt;n&gt; characters from the current cursor position by overwriting them with a space character.</span></span> |
| <span data-ttu-id="23725-290">ESC \[ &lt; n &gt; L</span><span class="sxs-lookup"><span data-stu-id="23725-290">ESC \[ &lt;n&gt; L</span></span> | <span data-ttu-id="23725-291">IL</span><span class="sxs-lookup"><span data-stu-id="23725-291">IL</span></span> | <span data-ttu-id="23725-292">Insertar línea</span><span class="sxs-lookup"><span data-stu-id="23725-292">Insert Line</span></span> | <span data-ttu-id="23725-293">Inserta &lt; n &gt; líneas en el búfer en la posición del cursor.</span><span class="sxs-lookup"><span data-stu-id="23725-293">Inserts &lt;n&gt; lines into the buffer at the cursor position.</span></span> <span data-ttu-id="23725-294">La línea en la que se encuentra el cursor y las líneas que hay debajo se desplazará hacia abajo.</span><span class="sxs-lookup"><span data-stu-id="23725-294">The line the cursor is on, and lines below it, will be shifted downwards.</span></span> |
| <span data-ttu-id="23725-295">ESC \[ &lt; n &gt; M</span><span class="sxs-lookup"><span data-stu-id="23725-295">ESC \[ &lt;n&gt; M</span></span> | <span data-ttu-id="23725-296">DL</span><span class="sxs-lookup"><span data-stu-id="23725-296">DL</span></span> | <span data-ttu-id="23725-297">Eliminar línea</span><span class="sxs-lookup"><span data-stu-id="23725-297">Delete Line</span></span> | <span data-ttu-id="23725-298">Elimina &lt; n &gt; líneas del búfer, comenzando por la fila en la que se encuentra el cursor.</span><span class="sxs-lookup"><span data-stu-id="23725-298">Deletes &lt;n&gt; lines from the buffer, starting with the row the cursor is on.</span></span> |



> [!NOTE]
><span data-ttu-id="23725-299">En el caso de IL y DL, solo se ven afectadas las líneas de los márgenes de desplazamiento (vea los márgenes de desplazamiento).</span><span class="sxs-lookup"><span data-stu-id="23725-299">For IL and DL, only the lines in the scrolling margins (see Scrolling Margins) are affected.</span></span> <span data-ttu-id="23725-300">Si no se establece ningún margen, los bordes de margen predeterminados son la ventanilla actual.</span><span class="sxs-lookup"><span data-stu-id="23725-300">If no margins are set, the default margin borders are the current viewport.</span></span> <span data-ttu-id="23725-301">Si se desplazan las líneas por debajo de los márgenes, se descartan.</span><span class="sxs-lookup"><span data-stu-id="23725-301">If lines would be shifted below the margins, they are discarded.</span></span> <span data-ttu-id="23725-302">Cuando se eliminan líneas, se insertan líneas en blanco en la parte inferior de los márgenes, mientras que las líneas desde fuera de la ventanilla nunca se ven afectadas.</span><span class="sxs-lookup"><span data-stu-id="23725-302">When lines are deleted, blank lines are inserted at the bottom of the margins, lines from outside the viewport are never affected.</span></span>

<span data-ttu-id="23725-303">Para cada una de las secuencias, el valor predeterminado de &lt; n &gt; si se omite es 0.</span><span class="sxs-lookup"><span data-stu-id="23725-303">For each of the sequences, the default value for &lt;n&gt; if it is omitted is 0.</span></span>



<span data-ttu-id="23725-304">En el caso de los siguientes comandos, el parámetro &lt; n &gt; tiene 3 valores válidos:</span><span class="sxs-lookup"><span data-stu-id="23725-304">For the following commands, the parameter &lt;n&gt; has 3 valid values:</span></span>

- <span data-ttu-id="23725-305">0 borra desde la posición actual del cursor (inclusivo) hasta el final de la línea o pantalla.</span><span class="sxs-lookup"><span data-stu-id="23725-305">0 erases from the current cursor position (inclusive) to the end of the line/display</span></span>
- <span data-ttu-id="23725-306">1 borra desde el principio de la línea/muestra hasta la posición actual del cursor, inclusive</span><span class="sxs-lookup"><span data-stu-id="23725-306">1 erases from the beginning of the line/display up to and including the current cursor position</span></span>
- <span data-ttu-id="23725-307">2 borra la línea o pantalla completa</span><span class="sxs-lookup"><span data-stu-id="23725-307">2 erases the entire line/display</span></span>


| <span data-ttu-id="23725-308">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-308">Sequence</span></span> | <span data-ttu-id="23725-309">Código</span><span class="sxs-lookup"><span data-stu-id="23725-309">Code</span></span> | <span data-ttu-id="23725-310">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-310">Description</span></span> | <span data-ttu-id="23725-311">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-311">Behavior</span></span> |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="23725-312">ESC \[ &lt; n &gt; J</span><span class="sxs-lookup"><span data-stu-id="23725-312">ESC \[ &lt;n&gt; J</span></span> | <span data-ttu-id="23725-313">ED</span><span class="sxs-lookup"><span data-stu-id="23725-313">ED</span></span> | <span data-ttu-id="23725-314">Borrar en pantalla</span><span class="sxs-lookup"><span data-stu-id="23725-314">Erase in Display</span></span> | <span data-ttu-id="23725-315">Reemplazar todo el texto de la ventanilla o pantalla actual especificada por &lt; n por &gt; caracteres de espacio</span><span class="sxs-lookup"><span data-stu-id="23725-315">Replace all text in the current viewport/screen specified by &lt;n&gt; with space characters</span></span> |
| <span data-ttu-id="23725-316">ESC \[ &lt; n &gt; K</span><span class="sxs-lookup"><span data-stu-id="23725-316">ESC \[ &lt;n&gt; K</span></span> | <span data-ttu-id="23725-317">Torito</span><span class="sxs-lookup"><span data-stu-id="23725-317">EL</span></span> | <span data-ttu-id="23725-318">Borrar en línea</span><span class="sxs-lookup"><span data-stu-id="23725-318">Erase in Line</span></span> | <span data-ttu-id="23725-319">Reemplazar todo el texto de la línea con el cursor especificado por &lt; n por &gt; caracteres de espacio</span><span class="sxs-lookup"><span data-stu-id="23725-319">Replace all text on the line with the cursor specified by &lt;n&gt; with space characters</span></span> |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span data-ttu-id="23725-320"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Formato de texto</span><span class="sxs-lookup"><span data-stu-id="23725-320"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Text Formatting</span></span>


<span data-ttu-id="23725-321">Todos los comandos de esta sección suelen ser equivalentes a llamar a las API de la consola de [**SetConsoleTextAttribute**](setconsoletextattribute.md) para ajustar el formato de todas las escrituras futuras en el búfer de texto de salida de la consola.</span><span class="sxs-lookup"><span data-stu-id="23725-321">All commands in this section are generally equivalent to calling [**SetConsoleTextAttribute**](setconsoletextattribute.md) console APIs to adjust the formatting of all future writes to the console output text buffer.</span></span>

<span data-ttu-id="23725-322">Este comando es especial, ya que &lt; la &gt; posición n siguiente puede aceptar entre 0 y 16 parámetros separados por punto y coma.</span><span class="sxs-lookup"><span data-stu-id="23725-322">This command is special in that the &lt;n&gt; position below can accept between 0 and 16 parameters separated by semicolons.</span></span>

<span data-ttu-id="23725-323">Cuando no se especifican parámetros, se trata igual que un solo parámetro 0.</span><span class="sxs-lookup"><span data-stu-id="23725-323">When no parameters are specified, it is treated the same as a single 0 parameter.</span></span>


| <span data-ttu-id="23725-324">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-324">Sequence</span></span> | <span data-ttu-id="23725-325">Código</span><span class="sxs-lookup"><span data-stu-id="23725-325">Code</span></span> | <span data-ttu-id="23725-326">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-326">Description</span></span> | <span data-ttu-id="23725-327">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-327">Behavior</span></span> |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| <span data-ttu-id="23725-328">ESC \[ &lt; n &gt; m</span><span class="sxs-lookup"><span data-stu-id="23725-328">ESC \[ &lt;n&gt; m</span></span> | <span data-ttu-id="23725-329">SGR</span><span class="sxs-lookup"><span data-stu-id="23725-329">SGR</span></span> | <span data-ttu-id="23725-330">Establecer copias de gráficos</span><span class="sxs-lookup"><span data-stu-id="23725-330">Set Graphics Rendition</span></span> | <span data-ttu-id="23725-331">Establezca el formato de la pantalla y el texto tal y como se especifica en &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="23725-331">Set the format of the screen and text as specified by &lt;n&gt;</span></span> |



<span data-ttu-id="23725-332">La siguiente tabla de valores se puede usar en &lt; n &gt; para representar diferentes modos de formato.</span><span class="sxs-lookup"><span data-stu-id="23725-332">The following table of values can be used in &lt;n&gt; to represent different formatting modes.</span></span>

<span data-ttu-id="23725-333">Los modos de formato se aplican de izquierda a derecha.</span><span class="sxs-lookup"><span data-stu-id="23725-333">Formatting modes are applied from left to right.</span></span> <span data-ttu-id="23725-334">La aplicación de las opciones de formato de la competencia dará lugar a que la opción más a la derecha tenga prioridad.</span><span class="sxs-lookup"><span data-stu-id="23725-334">Applying competing formatting options will result in the right-most option taking precedence.</span></span>

<span data-ttu-id="23725-335">En el caso de las opciones que especifican colores, se usarán los colores tal y como se definen en la tabla de colores de la consola, que se pueden modificar mediante la API de [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) .</span><span class="sxs-lookup"><span data-stu-id="23725-335">For options that specify colors, the colors will be used as defined in the console color table which can be modified using the [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) API.</span></span> <span data-ttu-id="23725-336">Si se modifica la tabla para que la posición "azul" en la tabla muestre un tono RGB de rojo, todas las llamadas al **azul de primer plano** mostrarán el color rojo hasta que cambien.</span><span class="sxs-lookup"><span data-stu-id="23725-336">If the table is modified to make the “blue” position in the table display an RGB shade of red, then all calls to **Foreground Blue** will display that red color until otherwise changed.</span></span>


| <span data-ttu-id="23725-337">Valor</span><span class="sxs-lookup"><span data-stu-id="23725-337">Value</span></span> | <span data-ttu-id="23725-338">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-338">Description</span></span> | <span data-ttu-id="23725-339">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-339">Behavior</span></span> |
|-------|---------------------------|--------------------------------------------------------------------|
| <span data-ttu-id="23725-340">0</span><span class="sxs-lookup"><span data-stu-id="23725-340">0</span></span> | <span data-ttu-id="23725-341">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="23725-341">Default</span></span> | <span data-ttu-id="23725-342">Devuelve todos los atributos al estado predeterminado antes de la modificación.</span><span class="sxs-lookup"><span data-stu-id="23725-342">Returns all attributes to the default state prior to modification</span></span> |
| <span data-ttu-id="23725-343">1</span><span class="sxs-lookup"><span data-stu-id="23725-343">1</span></span> | <span data-ttu-id="23725-344">Negrita/brillante</span><span class="sxs-lookup"><span data-stu-id="23725-344">Bold/Bright</span></span> | <span data-ttu-id="23725-345">Aplica la marca de brillo/intensidad al color de primer plano</span><span class="sxs-lookup"><span data-stu-id="23725-345">Applies brightness/intensity flag to foreground color</span></span> |
| <span data-ttu-id="23725-346">4</span><span class="sxs-lookup"><span data-stu-id="23725-346">4</span></span> | <span data-ttu-id="23725-347">Subrayado</span><span class="sxs-lookup"><span data-stu-id="23725-347">Underline</span></span> | <span data-ttu-id="23725-348">Agrega el subrayado</span><span class="sxs-lookup"><span data-stu-id="23725-348">Adds underline</span></span> |
| <span data-ttu-id="23725-349">24</span><span class="sxs-lookup"><span data-stu-id="23725-349">24</span></span> | <span data-ttu-id="23725-350">Sin subrayado</span><span class="sxs-lookup"><span data-stu-id="23725-350">No underline</span></span> | <span data-ttu-id="23725-351">Quita el subrayado</span><span class="sxs-lookup"><span data-stu-id="23725-351">Removes underline</span></span> |
| <span data-ttu-id="23725-352">7</span><span class="sxs-lookup"><span data-stu-id="23725-352">7</span></span> | <span data-ttu-id="23725-353">Negativo</span><span class="sxs-lookup"><span data-stu-id="23725-353">Negative</span></span> | <span data-ttu-id="23725-354">Intercambia los colores de primer plano y de fondo</span><span class="sxs-lookup"><span data-stu-id="23725-354">Swaps foreground and background colors</span></span> |
| <span data-ttu-id="23725-355">27</span><span class="sxs-lookup"><span data-stu-id="23725-355">27</span></span> | <span data-ttu-id="23725-356">Positivo (sin negativo)</span><span class="sxs-lookup"><span data-stu-id="23725-356">Positive (No negative)</span></span> | <span data-ttu-id="23725-357">Devuelve Foreground/Background a normal</span><span class="sxs-lookup"><span data-stu-id="23725-357">Returns foreground/background to normal</span></span> |
| <span data-ttu-id="23725-358">30</span><span class="sxs-lookup"><span data-stu-id="23725-358">30</span></span> | <span data-ttu-id="23725-359">Negro de primer plano</span><span class="sxs-lookup"><span data-stu-id="23725-359">Foreground Black</span></span> | <span data-ttu-id="23725-360">Se aplica a primer plano el negro brillante y no en negrita</span><span class="sxs-lookup"><span data-stu-id="23725-360">Applies non-bold/bright black to foreground</span></span> |
| <span data-ttu-id="23725-361">31</span><span class="sxs-lookup"><span data-stu-id="23725-361">31</span></span> | <span data-ttu-id="23725-362">Rojo de primer plano</span><span class="sxs-lookup"><span data-stu-id="23725-362">Foreground Red</span></span> | <span data-ttu-id="23725-363">Se aplica rojo a primer plano que no sea de negrita o brillante</span><span class="sxs-lookup"><span data-stu-id="23725-363">Applies non-bold/bright red to foreground</span></span> |
| <span data-ttu-id="23725-364">32</span><span class="sxs-lookup"><span data-stu-id="23725-364">32</span></span> | <span data-ttu-id="23725-365">Verde de primer plano</span><span class="sxs-lookup"><span data-stu-id="23725-365">Foreground Green</span></span> | <span data-ttu-id="23725-366">Se aplica de verde a primer plano que no sea de negrita o brillante</span><span class="sxs-lookup"><span data-stu-id="23725-366">Applies non-bold/bright green to foreground</span></span> |
| <span data-ttu-id="23725-367">33</span><span class="sxs-lookup"><span data-stu-id="23725-367">33</span></span> | <span data-ttu-id="23725-368">Amarillo de primer plano</span><span class="sxs-lookup"><span data-stu-id="23725-368">Foreground Yellow</span></span> | <span data-ttu-id="23725-369">Se aplica al primer plano un amarillo brillante o no en negrita</span><span class="sxs-lookup"><span data-stu-id="23725-369">Applies non-bold/bright yellow to foreground</span></span> |
| <span data-ttu-id="23725-370">34</span><span class="sxs-lookup"><span data-stu-id="23725-370">34</span></span> | <span data-ttu-id="23725-371">Azul de primer plano</span><span class="sxs-lookup"><span data-stu-id="23725-371">Foreground Blue</span></span> | <span data-ttu-id="23725-372">Se aplica a primer plano el azul brillante o no negrita</span><span class="sxs-lookup"><span data-stu-id="23725-372">Applies non-bold/bright blue to foreground</span></span> |
| <span data-ttu-id="23725-373">35</span><span class="sxs-lookup"><span data-stu-id="23725-373">35</span></span> | <span data-ttu-id="23725-374">Magenta de primer plano</span><span class="sxs-lookup"><span data-stu-id="23725-374">Foreground Magenta</span></span> | <span data-ttu-id="23725-375">Se aplica a primer plano el magenta brillante o no en negrita</span><span class="sxs-lookup"><span data-stu-id="23725-375">Applies non-bold/bright magenta to foreground</span></span> |
| <span data-ttu-id="23725-376">36</span><span class="sxs-lookup"><span data-stu-id="23725-376">36</span></span> | <span data-ttu-id="23725-377">Aguamarina de primer plano</span><span class="sxs-lookup"><span data-stu-id="23725-377">Foreground Cyan</span></span> | <span data-ttu-id="23725-378">Se aplica al primer plano un cian brillante o no en negrita.</span><span class="sxs-lookup"><span data-stu-id="23725-378">Applies non-bold/bright cyan to foreground</span></span> |
| <span data-ttu-id="23725-379">37</span><span class="sxs-lookup"><span data-stu-id="23725-379">37</span></span> | <span data-ttu-id="23725-380">Blanco de primer plano</span><span class="sxs-lookup"><span data-stu-id="23725-380">Foreground White</span></span> | <span data-ttu-id="23725-381">Se aplica a primer plano el blanco brillante o no negrita</span><span class="sxs-lookup"><span data-stu-id="23725-381">Applies non-bold/bright white to foreground</span></span> |
| <span data-ttu-id="23725-382">38</span><span class="sxs-lookup"><span data-stu-id="23725-382">38</span></span> | <span data-ttu-id="23725-383">Primer plano extendido</span><span class="sxs-lookup"><span data-stu-id="23725-383">Foreground Extended</span></span> | <span data-ttu-id="23725-384">Aplica el valor de color extendido al primer plano (vea los detalles a continuación).</span><span class="sxs-lookup"><span data-stu-id="23725-384">Applies extended color value to the foreground (see details below)</span></span> |
| <span data-ttu-id="23725-385">39</span><span class="sxs-lookup"><span data-stu-id="23725-385">39</span></span> | <span data-ttu-id="23725-386">Valor predeterminado de primer plano</span><span class="sxs-lookup"><span data-stu-id="23725-386">Foreground Default</span></span> | <span data-ttu-id="23725-387">Aplica solo la parte de primer plano de los valores predeterminados (vea 0)</span><span class="sxs-lookup"><span data-stu-id="23725-387">Applies only the foreground portion of the defaults (see 0)</span></span> |
| <span data-ttu-id="23725-388">40</span><span class="sxs-lookup"><span data-stu-id="23725-388">40</span></span> | <span data-ttu-id="23725-389">Fondo negro</span><span class="sxs-lookup"><span data-stu-id="23725-389">Background Black</span></span> | <span data-ttu-id="23725-390">Se aplica a fondo que no es de negrita o brillante</span><span class="sxs-lookup"><span data-stu-id="23725-390">Applies non-bold/bright black to background</span></span> |
| <span data-ttu-id="23725-391">41</span><span class="sxs-lookup"><span data-stu-id="23725-391">41</span></span> | <span data-ttu-id="23725-392">Rojo de fondo</span><span class="sxs-lookup"><span data-stu-id="23725-392">Background Red</span></span> | <span data-ttu-id="23725-393">Aplica rojo a fondo que no es de negrita o brillante</span><span class="sxs-lookup"><span data-stu-id="23725-393">Applies non-bold/bright red to background</span></span> |
| <span data-ttu-id="23725-394">42</span><span class="sxs-lookup"><span data-stu-id="23725-394">42</span></span> | <span data-ttu-id="23725-395">Verde de fondo</span><span class="sxs-lookup"><span data-stu-id="23725-395">Background Green</span></span> | <span data-ttu-id="23725-396">Se aplica a fondo que no es de negrita o brillante</span><span class="sxs-lookup"><span data-stu-id="23725-396">Applies non-bold/bright green to background</span></span> |
| <span data-ttu-id="23725-397">43</span><span class="sxs-lookup"><span data-stu-id="23725-397">43</span></span> | <span data-ttu-id="23725-398">Amarillo de fondo</span><span class="sxs-lookup"><span data-stu-id="23725-398">Background Yellow</span></span> | <span data-ttu-id="23725-399">Se aplica a fondo que no es de negrita o brillante</span><span class="sxs-lookup"><span data-stu-id="23725-399">Applies non-bold/bright yellow to background</span></span> |
| <span data-ttu-id="23725-400">44</span><span class="sxs-lookup"><span data-stu-id="23725-400">44</span></span> | <span data-ttu-id="23725-401">Azul de fondo</span><span class="sxs-lookup"><span data-stu-id="23725-401">Background Blue</span></span> | <span data-ttu-id="23725-402">Se aplica al fondo de color azul brillante o no negrita</span><span class="sxs-lookup"><span data-stu-id="23725-402">Applies non-bold/bright blue to background</span></span> |
| <span data-ttu-id="23725-403">45</span><span class="sxs-lookup"><span data-stu-id="23725-403">45</span></span> | <span data-ttu-id="23725-404">Magenta de fondo</span><span class="sxs-lookup"><span data-stu-id="23725-404">Background Magenta</span></span> | <span data-ttu-id="23725-405">Se aplica al fondo un magenta que no sea de negrita o brillante</span><span class="sxs-lookup"><span data-stu-id="23725-405">Applies non-bold/bright magenta to background</span></span> |
| <span data-ttu-id="23725-406">46</span><span class="sxs-lookup"><span data-stu-id="23725-406">46</span></span> | <span data-ttu-id="23725-407">Aguamarina de fondo</span><span class="sxs-lookup"><span data-stu-id="23725-407">Background Cyan</span></span> | <span data-ttu-id="23725-408">Se aplica el color aguamarina, no en negrita o brillante al fondo</span><span class="sxs-lookup"><span data-stu-id="23725-408">Applies non-bold/bright cyan to background</span></span> |
| <span data-ttu-id="23725-409">47</span><span class="sxs-lookup"><span data-stu-id="23725-409">47</span></span> | <span data-ttu-id="23725-410">Fondo blanco</span><span class="sxs-lookup"><span data-stu-id="23725-410">Background White</span></span> | <span data-ttu-id="23725-411">Se aplica a fondo que no está en negrita o brillante</span><span class="sxs-lookup"><span data-stu-id="23725-411">Applies non-bold/bright white to background</span></span> |
| <span data-ttu-id="23725-412">48</span><span class="sxs-lookup"><span data-stu-id="23725-412">48</span></span> | <span data-ttu-id="23725-413">En segundo plano</span><span class="sxs-lookup"><span data-stu-id="23725-413">Background Extended</span></span> | <span data-ttu-id="23725-414">Aplica el valor de color extendido al fondo (vea los detalles a continuación).</span><span class="sxs-lookup"><span data-stu-id="23725-414">Applies extended color value to the background (see details below)</span></span> |
| <span data-ttu-id="23725-415">49</span><span class="sxs-lookup"><span data-stu-id="23725-415">49</span></span> | <span data-ttu-id="23725-416">Valor predeterminado de fondo</span><span class="sxs-lookup"><span data-stu-id="23725-416">Background Default</span></span> | <span data-ttu-id="23725-417">Aplica solo la parte de fondo de los valores predeterminados (vea 0)</span><span class="sxs-lookup"><span data-stu-id="23725-417">Applies only the background portion of the defaults (see 0)</span></span> |
| <span data-ttu-id="23725-418">90</span><span class="sxs-lookup"><span data-stu-id="23725-418">90</span></span> | <span data-ttu-id="23725-419">Negro de primer plano brillante</span><span class="sxs-lookup"><span data-stu-id="23725-419">Bright Foreground Black</span></span> | <span data-ttu-id="23725-420">Aplica el negro de negrita o brillante al primer plano.</span><span class="sxs-lookup"><span data-stu-id="23725-420">Applies bold/bright black to foreground</span></span> |
| <span data-ttu-id="23725-421">91</span><span class="sxs-lookup"><span data-stu-id="23725-421">91</span></span> | <span data-ttu-id="23725-422">Rojo de primer plano brillante</span><span class="sxs-lookup"><span data-stu-id="23725-422">Bright Foreground Red</span></span> | <span data-ttu-id="23725-423">Aplica el color rojo de negrita o brillante al primer plano.</span><span class="sxs-lookup"><span data-stu-id="23725-423">Applies bold/bright red to foreground</span></span> |
| <span data-ttu-id="23725-424">92</span><span class="sxs-lookup"><span data-stu-id="23725-424">92</span></span> | <span data-ttu-id="23725-425">Verde en primer plano brillante</span><span class="sxs-lookup"><span data-stu-id="23725-425">Bright Foreground Green</span></span> | <span data-ttu-id="23725-426">Aplica el color verde de negrita o brillante al primer plano.</span><span class="sxs-lookup"><span data-stu-id="23725-426">Applies bold/bright green to foreground</span></span> |
| <span data-ttu-id="23725-427">93</span><span class="sxs-lookup"><span data-stu-id="23725-427">93</span></span> | <span data-ttu-id="23725-428">Amarillo de primer plano brillante</span><span class="sxs-lookup"><span data-stu-id="23725-428">Bright Foreground Yellow</span></span> | <span data-ttu-id="23725-429">Aplica el color amarillo de negrita o brillante al primer plano</span><span class="sxs-lookup"><span data-stu-id="23725-429">Applies bold/bright yellow to foreground</span></span> |
| <span data-ttu-id="23725-430">94</span><span class="sxs-lookup"><span data-stu-id="23725-430">94</span></span> | <span data-ttu-id="23725-431">Azul de primer plano brillante</span><span class="sxs-lookup"><span data-stu-id="23725-431">Bright Foreground Blue</span></span> | <span data-ttu-id="23725-432">Aplica el color azul oscuro o brillante al primer plano</span><span class="sxs-lookup"><span data-stu-id="23725-432">Applies bold/bright blue to foreground</span></span> |
| <span data-ttu-id="23725-433">95</span><span class="sxs-lookup"><span data-stu-id="23725-433">95</span></span> | <span data-ttu-id="23725-434">Magenta de primer plano brillante</span><span class="sxs-lookup"><span data-stu-id="23725-434">Bright Foreground Magenta</span></span> | <span data-ttu-id="23725-435">Aplica el magenta de negrita o brillante al primer plano.</span><span class="sxs-lookup"><span data-stu-id="23725-435">Applies bold/bright magenta to foreground</span></span> |
| <span data-ttu-id="23725-436">96</span><span class="sxs-lookup"><span data-stu-id="23725-436">96</span></span> | <span data-ttu-id="23725-437">Aguamarina de primer plano brillante</span><span class="sxs-lookup"><span data-stu-id="23725-437">Bright Foreground Cyan</span></span> | <span data-ttu-id="23725-438">Aplica el color aguamarina/aguamarina brillante al primer plano.</span><span class="sxs-lookup"><span data-stu-id="23725-438">Applies bold/bright cyan to foreground</span></span> |
| <span data-ttu-id="23725-439">97</span><span class="sxs-lookup"><span data-stu-id="23725-439">97</span></span> | <span data-ttu-id="23725-440">Blanco de primer plano brillante</span><span class="sxs-lookup"><span data-stu-id="23725-440">Bright Foreground White</span></span> | <span data-ttu-id="23725-441">Aplica negrita/blanco brillante al primer plano</span><span class="sxs-lookup"><span data-stu-id="23725-441">Applies bold/bright white to foreground</span></span> |
| <span data-ttu-id="23725-442">100</span><span class="sxs-lookup"><span data-stu-id="23725-442">100</span></span> | <span data-ttu-id="23725-443">Negro de fondo brillante</span><span class="sxs-lookup"><span data-stu-id="23725-443">Bright Background Black</span></span> | <span data-ttu-id="23725-444">Aplica el negro de negrita o brillante al fondo</span><span class="sxs-lookup"><span data-stu-id="23725-444">Applies bold/bright black to background</span></span> |
| <span data-ttu-id="23725-445">101</span><span class="sxs-lookup"><span data-stu-id="23725-445">101</span></span> | <span data-ttu-id="23725-446">Rojo de fondo brillante</span><span class="sxs-lookup"><span data-stu-id="23725-446">Bright Background Red</span></span> | <span data-ttu-id="23725-447">Aplica el color rojo de negrita o brillante al fondo</span><span class="sxs-lookup"><span data-stu-id="23725-447">Applies bold/bright red to background</span></span> |
| <span data-ttu-id="23725-448">102</span><span class="sxs-lookup"><span data-stu-id="23725-448">102</span></span> | <span data-ttu-id="23725-449">Verde de fondo brillante</span><span class="sxs-lookup"><span data-stu-id="23725-449">Bright Background Green</span></span> | <span data-ttu-id="23725-450">Aplica el color verde de negrita o brillante al fondo</span><span class="sxs-lookup"><span data-stu-id="23725-450">Applies bold/bright green to background</span></span> |
| <span data-ttu-id="23725-451">103</span><span class="sxs-lookup"><span data-stu-id="23725-451">103</span></span> | <span data-ttu-id="23725-452">Amarillo de fondo brillante</span><span class="sxs-lookup"><span data-stu-id="23725-452">Bright Background Yellow</span></span> | <span data-ttu-id="23725-453">Aplica el color amarillo de negrita o brillante al fondo</span><span class="sxs-lookup"><span data-stu-id="23725-453">Applies bold/bright yellow to background</span></span> |
| <span data-ttu-id="23725-454">104</span><span class="sxs-lookup"><span data-stu-id="23725-454">104</span></span> | <span data-ttu-id="23725-455">Azul de fondo brillante</span><span class="sxs-lookup"><span data-stu-id="23725-455">Bright Background Blue</span></span> | <span data-ttu-id="23725-456">Se aplica el color azul oscuro al fondo</span><span class="sxs-lookup"><span data-stu-id="23725-456">Applies bold/bright blue to background</span></span> |
| <span data-ttu-id="23725-457">105</span><span class="sxs-lookup"><span data-stu-id="23725-457">105</span></span> | <span data-ttu-id="23725-458">Magenta de fondo brillante</span><span class="sxs-lookup"><span data-stu-id="23725-458">Bright Background Magenta</span></span> | <span data-ttu-id="23725-459">Aplica el color magenta de negrita o brillante al fondo</span><span class="sxs-lookup"><span data-stu-id="23725-459">Applies bold/bright magenta to background</span></span> |
| <span data-ttu-id="23725-460">106</span><span class="sxs-lookup"><span data-stu-id="23725-460">106</span></span> | <span data-ttu-id="23725-461">Aguamarina de fondo brillante</span><span class="sxs-lookup"><span data-stu-id="23725-461">Bright Background Cyan</span></span> | <span data-ttu-id="23725-462">Aplica el color aguamarina/aguamarina brillante al fondo</span><span class="sxs-lookup"><span data-stu-id="23725-462">Applies bold/bright cyan to background</span></span> |
| <span data-ttu-id="23725-463">107</span><span class="sxs-lookup"><span data-stu-id="23725-463">107</span></span> | <span data-ttu-id="23725-464">Blanco de fondo brillante</span><span class="sxs-lookup"><span data-stu-id="23725-464">Bright Background White</span></span> | <span data-ttu-id="23725-465">Aplica negrita/blanco brillante al fondo</span><span class="sxs-lookup"><span data-stu-id="23725-465">Applies bold/bright white to background</span></span> |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span data-ttu-id="23725-466"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Colores extendidos</span><span class="sxs-lookup"><span data-stu-id="23725-466"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Extended Colors</span></span>

<span data-ttu-id="23725-467">Algunos emuladores de terminal virtuales admiten una paleta de colores mayores que los 16 colores proporcionados por la consola de Windows.</span><span class="sxs-lookup"><span data-stu-id="23725-467">Some virtual terminal emulators support a palette of colors greater than the 16 colors provided by the Windows Console.</span></span> <span data-ttu-id="23725-468">Para estos colores extendidos, la consola de Windows elegirá el color más cercano adecuado en la tabla de 16 colores existente para su presentación.</span><span class="sxs-lookup"><span data-stu-id="23725-468">For these extended colors, the Windows Console will choose the nearest appropriate color from the existing 16 color table for display.</span></span> <span data-ttu-id="23725-469">A diferencia de los valores de SGR típicos anteriores, los valores extendidos consumirán parámetros adicionales después del indicador inicial según la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="23725-469">Unlike typical SGR values above, the extended values will consume additional parameters after the initial indicator according to the table below.</span></span>


| <span data-ttu-id="23725-470">Subsecuencia SGR</span><span class="sxs-lookup"><span data-stu-id="23725-470">SGR Subsequence</span></span> | <span data-ttu-id="23725-471">Description</span><span class="sxs-lookup"><span data-stu-id="23725-471">Description</span></span> |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="23725-472">38; dos &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="23725-472">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="23725-473">Establecer el color de primer plano en el valor RGB especificado en &lt; &gt; &lt; los parámetros r, g &gt; , &lt; b &gt;\*</span><span class="sxs-lookup"><span data-stu-id="23725-473">Set foreground color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="23725-474">48; dos &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="23725-474">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="23725-475">Establecer el color de fondo en el valor RGB especificado en &lt; &gt; &lt; los parámetros r, g &gt; , &lt; b &gt;\*</span><span class="sxs-lookup"><span data-stu-id="23725-475">Set background color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="23725-476">38; 5 &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="23725-476">38 ; 5 ; &lt;s&gt;</span></span> | <span data-ttu-id="23725-477">Establecer el color de primer plano &lt; &gt; en el índice de s en la tabla de colores 88 o 256\*</span><span class="sxs-lookup"><span data-stu-id="23725-477">Set foreground color to &lt;s&gt; index in 88 or 256 color table\*</span></span> |
| <span data-ttu-id="23725-478">48; 5 &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="23725-478">48 ; 5 ; &lt;s&gt;</span></span> | <span data-ttu-id="23725-479">Establecer el color de fondo en el &lt; &gt; índice en la tabla de colores 88 o 256\*</span><span class="sxs-lookup"><span data-stu-id="23725-479">Set background color to &lt;s&gt; index in 88 or 256 color table\*</span></span> |



<span data-ttu-id="23725-480">\*Las paletas de colores 88 y 256 que se mantienen internamente para la comparación se basan en el emulador de terminal de xterm.</span><span class="sxs-lookup"><span data-stu-id="23725-480">\*The 88 and 256 color palettes maintained internally for comparison are based from the xterm terminal emulator.</span></span> <span data-ttu-id="23725-481">Las tablas de comparación o redondeo no se pueden modificar en este momento.</span><span class="sxs-lookup"><span data-stu-id="23725-481">The comparison/rounding tables cannot be modified at this time.</span></span>


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span data-ttu-id="23725-482"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Colores de pantalla</span><span class="sxs-lookup"><span data-stu-id="23725-482"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Screen Colors</span></span>


<span data-ttu-id="23725-483">El siguiente comando permite que la aplicación establezca los valores de la paleta de colores de pantalla en cualquier valor RGB.</span><span class="sxs-lookup"><span data-stu-id="23725-483">The following command allows the application to set the screen colors palette values to any RGB value.</span></span>

<span data-ttu-id="23725-484">Los valores RGB deben ser valores hexadecimales entre `0` y y `ff` separados por el carácter de barra diagonal (por ejemplo, `rgb:1/24/86` ).</span><span class="sxs-lookup"><span data-stu-id="23725-484">The RGB values should be hexadecimal values between `0` and `ff`, and separated by the forward-slash character (e.g. `rgb:1/24/86`).</span></span>

<span data-ttu-id="23725-485">Tenga en cuenta que esta secuencia es una secuencia del "comando del sistema operativo" OSC y no un CSI como muchas de las otras secuencias enumeradas, y como tal comienza con " \\ X1b \] ", no con " \\ X1b \[ ".</span><span class="sxs-lookup"><span data-stu-id="23725-485">Note that this sequence is an OSC “Operating system command” sequence, and not a CSI like many of the other sequences listed, and as such start with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="23725-486">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-486">Sequence</span></span> | <span data-ttu-id="23725-487">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-487">Description</span></span> | <span data-ttu-id="23725-488">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-488">Behavior</span></span> |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="23725-489">ESC \] 4; &lt; i &gt; ; RGB: &lt; r &gt;  /  &lt; g &gt;  /  &lt; b &gt; ESC</span><span class="sxs-lookup"><span data-stu-id="23725-489">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span></span> | <span data-ttu-id="23725-490">Modificar los colores de la pantalla</span><span class="sxs-lookup"><span data-stu-id="23725-490">Modify Screen Colors</span></span> | <span data-ttu-id="23725-491">Establece el índice de paleta de &lt; colores &gt; de pantalla i en los valores RGB especificados en &lt; r &gt; , &lt; g &gt; , &lt; b&gt;</span><span class="sxs-lookup"><span data-stu-id="23725-491">Sets the screen color palette index &lt;i&gt; to the RGB values specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt;</span></span> |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span data-ttu-id="23725-492"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Cambios de modo</span><span class="sxs-lookup"><span data-stu-id="23725-492"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Mode Changes</span></span>


<span data-ttu-id="23725-493">Se trata de secuencias que controlan los modos de entrada.</span><span class="sxs-lookup"><span data-stu-id="23725-493">These are sequences that control the input modes.</span></span> <span data-ttu-id="23725-494">Hay dos conjuntos diferentes de modos de entrada, el modo de teclas de cursor y el modo de teclas del teclado.</span><span class="sxs-lookup"><span data-stu-id="23725-494">There are two different sets of input modes, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="23725-495">El modo de teclas de cursor controla las secuencias emitidas por las teclas de dirección, así como el inicio y el final, mientras que el modo de teclas del teclado controla las secuencias emitidas por las teclas en el teclado numérico principalmente, así como las teclas de función.</span><span class="sxs-lookup"><span data-stu-id="23725-495">The Cursor Keys Mode controls the sequences that are emitted by the arrow keys as well as Home and End, while the Keypad Keys Mode controls the sequences emitted by the keys on the numpad primarily, as well as the function keys.</span></span>

<span data-ttu-id="23725-496">Cada uno de estos modos es una configuración booleana simple: el modo de teclas de cursor es normal (predeterminado) o aplicación, y el modo de teclas del teclado es numérico (predeterminado) o aplicación.</span><span class="sxs-lookup"><span data-stu-id="23725-496">Each of these modes are simple boolean settings – the Cursor Keys Mode is either Normal (default) or Application, and the Keypad Keys Mode is either Numeric (default) or Application.</span></span>

<span data-ttu-id="23725-497">Vea las secciones teclas de cursor y teclado numérico & las de las secuencias emitidas en estos modos.</span><span class="sxs-lookup"><span data-stu-id="23725-497">See the Cursor Keys and Numpad & Function Keys sections for the sequences emitted in these modes.</span></span>


| <span data-ttu-id="23725-498">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-498">Sequence</span></span> | <span data-ttu-id="23725-499">Código</span><span class="sxs-lookup"><span data-stu-id="23725-499">Code</span></span> | <span data-ttu-id="23725-500">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-500">Description</span></span> | <span data-ttu-id="23725-501">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-501">Behavior</span></span> |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| <span data-ttu-id="23725-502">ESC =</span><span class="sxs-lookup"><span data-stu-id="23725-502">ESC =</span></span> | <span data-ttu-id="23725-503">DECKPAM</span><span class="sxs-lookup"><span data-stu-id="23725-503">DECKPAM</span></span> | <span data-ttu-id="23725-504">Habilitar el modo de aplicación de teclado</span><span class="sxs-lookup"><span data-stu-id="23725-504">Enable Keypad Application Mode</span></span> | <span data-ttu-id="23725-505">Las teclas del teclado emitirán sus secuencias en modo de aplicación.</span><span class="sxs-lookup"><span data-stu-id="23725-505">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="23725-506">ESC &gt;</span><span class="sxs-lookup"><span data-stu-id="23725-506">ESC &gt;</span></span> | <span data-ttu-id="23725-507">DECKPNM</span><span class="sxs-lookup"><span data-stu-id="23725-507">DECKPNM</span></span> | <span data-ttu-id="23725-508">Habilitar el modo numérico del teclado</span><span class="sxs-lookup"><span data-stu-id="23725-508">Enable Keypad Numeric Mode</span></span> | <span data-ttu-id="23725-509">Las teclas del teclado emitirán sus secuencias en modo numérico.</span><span class="sxs-lookup"><span data-stu-id="23725-509">Keypad keys will emit their Numeric Mode sequences.</span></span> |
| <span data-ttu-id="23725-510">\[¿ESC?</span><span class="sxs-lookup"><span data-stu-id="23725-510">ESC \[ ?</span></span> <span data-ttu-id="23725-511">1 h</span><span class="sxs-lookup"><span data-stu-id="23725-511">1 h</span></span> | <span data-ttu-id="23725-512">DECCKM</span><span class="sxs-lookup"><span data-stu-id="23725-512">DECCKM</span></span> | <span data-ttu-id="23725-513">Habilitar el modo de aplicación de teclas de cursor</span><span class="sxs-lookup"><span data-stu-id="23725-513">Enable Cursor Keys Application Mode</span></span> | <span data-ttu-id="23725-514">Las teclas del teclado emitirán sus secuencias en modo de aplicación.</span><span class="sxs-lookup"><span data-stu-id="23725-514">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="23725-515">\[¿ESC?</span><span class="sxs-lookup"><span data-stu-id="23725-515">ESC \[ ?</span></span> <span data-ttu-id="23725-516">1 l</span><span class="sxs-lookup"><span data-stu-id="23725-516">1 l</span></span> | <span data-ttu-id="23725-517">DECCKM</span><span class="sxs-lookup"><span data-stu-id="23725-517">DECCKM</span></span> | <span data-ttu-id="23725-518">Deshabilitar el modo de aplicación de teclas de cursor (usar el modo normal)</span><span class="sxs-lookup"><span data-stu-id="23725-518">Disable Cursor Keys Application Mode (use Normal Mode)</span></span> | <span data-ttu-id="23725-519">Las teclas del teclado emitirán sus secuencias en modo numérico.</span><span class="sxs-lookup"><span data-stu-id="23725-519">Keypad keys will emit their Numeric Mode sequences.</span></span> |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span data-ttu-id="23725-520"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Estado de la consulta</span><span class="sxs-lookup"><span data-stu-id="23725-520"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Query State</span></span>


<span data-ttu-id="23725-521">Todos los comandos de esta sección suelen ser equivalentes a llamar a get \* Console API para recuperar información de estado sobre el estado actual del búfer de la consola.</span><span class="sxs-lookup"><span data-stu-id="23725-521">All commands in this section are generally equivalent to calling Get\* console APIs to retrieve status information about the current console buffer state.</span></span>

> [!NOTE]
><span data-ttu-id="23725-522">Estas consultas emitirán sus respuestas en el flujo de entrada de la consola inmediatamente después de que se reconozcan en el flujo de salida mientras \_ \_ se establece habilitar el procesamiento de terminal virtual \_ .</span><span class="sxs-lookup"><span data-stu-id="23725-522">These queries will emit their responses into the console input stream immediately after being recognized on the output stream while ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING is set.</span></span> <span data-ttu-id="23725-523">El \_ indicador habilitar \_ entrada de terminal virtual \_ no se aplica a los comandos de consulta, ya que se supone que una aplicación que realiza la consulta siempre querrá recibir la respuesta.</span><span class="sxs-lookup"><span data-stu-id="23725-523">The ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag does not apply to query commands as it is assumed that an application making the query will always want to receive the reply.</span></span>




| <span data-ttu-id="23725-524">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-524">Sequence</span></span> | <span data-ttu-id="23725-525">Código</span><span class="sxs-lookup"><span data-stu-id="23725-525">Code</span></span> | <span data-ttu-id="23725-526">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-526">Description</span></span> | <span data-ttu-id="23725-527">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-527">Behavior</span></span> |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="23725-528">ESC \[ 6 n</span><span class="sxs-lookup"><span data-stu-id="23725-528">ESC \[ 6 n</span></span> | <span data-ttu-id="23725-529">DECXCPR</span><span class="sxs-lookup"><span data-stu-id="23725-529">DECXCPR</span></span> | <span data-ttu-id="23725-530">Posición del cursor de informe</span><span class="sxs-lookup"><span data-stu-id="23725-530">Report Cursor Position</span></span> | <span data-ttu-id="23725-531">Emita la posición del cursor como: ESC \[ &lt; r &gt; ; &lt; c &gt; r donde &lt; R &gt; = cursor Row y &lt; c &gt; = columna cursor</span><span class="sxs-lookup"><span data-stu-id="23725-531">Emit the cursor position as: ESC \[ &lt;r&gt; ; &lt;c&gt; R Where &lt;r&gt; = cursor row and &lt;c&gt; = cursor column</span></span> |
| <span data-ttu-id="23725-532">ESC \[ 0 c</span><span class="sxs-lookup"><span data-stu-id="23725-532">ESC \[ 0 c</span></span> | <span data-ttu-id="23725-533">&</span><span class="sxs-lookup"><span data-stu-id="23725-533">DA</span></span> | <span data-ttu-id="23725-534">Atributos de dispositivo</span><span class="sxs-lookup"><span data-stu-id="23725-534">Device Attributes</span></span> | <span data-ttu-id="23725-535">Notificar la identidad del terminal.</span><span class="sxs-lookup"><span data-stu-id="23725-535">Report the terminal identity.</span></span> <span data-ttu-id="23725-536">Emitirá " \\ X1b \[ ? 1; 0C", que indica "VT101 sin opciones".</span><span class="sxs-lookup"><span data-stu-id="23725-536">Will emit “\\x1b\[?1;0c”, indicating "VT101 with No Options".</span></span> |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span data-ttu-id="23725-537"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Columnas</span><span class="sxs-lookup"><span data-stu-id="23725-537"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabs</span></span>


<span data-ttu-id="23725-538">Aunque la consola de Windows normalmente espera que las pestañas tengan exclusivamente ocho caracteres de ancho, \* las aplicaciones de Nix que usan ciertas secuencias pueden manipular dónde se detienen las tabulaciones en las ventanas de la consola para optimizar el movimiento del cursor por parte de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="23725-538">While the windows console traditionally expects tabs to be exclusively eight characters wide, \*nix applications utilizing certain sequences can manipulate where the tab stops are within the console windows to optimize cursor movement by the application.</span></span>

<span data-ttu-id="23725-539">Las secuencias siguientes permiten a una aplicación establecer las ubicaciones de tabulación dentro de la ventana de la consola, quitarlas y desplazarse entre ellas.</span><span class="sxs-lookup"><span data-stu-id="23725-539">The following sequences allow an application to set the tab stop locations within the console window, remove them, and navigate between them.</span></span>


| <span data-ttu-id="23725-540">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-540">Sequence</span></span> | <span data-ttu-id="23725-541">Código</span><span class="sxs-lookup"><span data-stu-id="23725-541">Code</span></span> | <span data-ttu-id="23725-542">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-542">Description</span></span> | <span data-ttu-id="23725-543">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-543">Behavior</span></span> |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="23725-544">ESC H</span><span class="sxs-lookup"><span data-stu-id="23725-544">ESC H</span></span> | <span data-ttu-id="23725-545">HTS</span><span class="sxs-lookup"><span data-stu-id="23725-545">HTS</span></span> | <span data-ttu-id="23725-546">Conjunto de pestañas horizontal</span><span class="sxs-lookup"><span data-stu-id="23725-546">Horizontal Tab Set</span></span> | <span data-ttu-id="23725-547">Establece un punto de tabulación en la columna actual en la que se encuentra el cursor.</span><span class="sxs-lookup"><span data-stu-id="23725-547">Sets a tab stop in the current column the cursor is in.</span></span> |
| <span data-ttu-id="23725-548">ESC \[ &lt; n &gt; I</span><span class="sxs-lookup"><span data-stu-id="23725-548">ESC \[ &lt;n&gt; I</span></span> | <span data-ttu-id="23725-549">CHT</span><span class="sxs-lookup"><span data-stu-id="23725-549">CHT</span></span> | <span data-ttu-id="23725-550">Cursor horizontal (hacia delante)</span><span class="sxs-lookup"><span data-stu-id="23725-550">Cursor Horizontal (Forward) Tab</span></span> | <span data-ttu-id="23725-551">Avanzar el cursor hasta la columna siguiente (en la misma fila) con una tabulación.</span><span class="sxs-lookup"><span data-stu-id="23725-551">Advance the cursor to the next column (in the same row) with a tab stop.</span></span> <span data-ttu-id="23725-552">Si no hay más tabulaciones, desplácese a la última columna de la fila.</span><span class="sxs-lookup"><span data-stu-id="23725-552">If there are no more tab stops, move to the last column in the row.</span></span> <span data-ttu-id="23725-553">Si el cursor está en la última columna, desplácese a la primera columna de la fila siguiente.</span><span class="sxs-lookup"><span data-stu-id="23725-553">If the cursor is in the last column, move to the first column of the next row.</span></span> |
| <span data-ttu-id="23725-554">ESC \[ &lt; n &gt; Z</span><span class="sxs-lookup"><span data-stu-id="23725-554">ESC \[ &lt;n&gt; Z</span></span> | <span data-ttu-id="23725-555">ORDENADOR</span><span class="sxs-lookup"><span data-stu-id="23725-555">CBT</span></span> | <span data-ttu-id="23725-556">Tabulador hacia atrás de cursor</span><span class="sxs-lookup"><span data-stu-id="23725-556">Cursor Backwards Tab</span></span> | <span data-ttu-id="23725-557">Mueve el cursor a la columna anterior (en la misma fila) con una tabulación.</span><span class="sxs-lookup"><span data-stu-id="23725-557">Move the cursor to the previous column (in the same row) with a tab stop.</span></span> <span data-ttu-id="23725-558">Si no hay más tabulaciones, mueve el cursor a la primera columna.</span><span class="sxs-lookup"><span data-stu-id="23725-558">If there are no more tab stops, moves the cursor to the first column.</span></span> <span data-ttu-id="23725-559">Si el cursor está en la primera columna, no mueve el cursor.</span><span class="sxs-lookup"><span data-stu-id="23725-559">If the cursor is in the first column, doesn’t move the cursor.</span></span> |
| <span data-ttu-id="23725-560">ESC \[ 0 g</span><span class="sxs-lookup"><span data-stu-id="23725-560">ESC \[ 0 g</span></span> | <span data-ttu-id="23725-561">TBC</span><span class="sxs-lookup"><span data-stu-id="23725-561">TBC</span></span> | <span data-ttu-id="23725-562">Borrado de tabulación (columna actual)</span><span class="sxs-lookup"><span data-stu-id="23725-562">Tab Clear (current column)</span></span> | <span data-ttu-id="23725-563">Borra la tabulación de la columna actual, si hay alguna.</span><span class="sxs-lookup"><span data-stu-id="23725-563">Clears the tab stop in the current column, if there is one.</span></span> <span data-ttu-id="23725-564">En caso contrario, no hace nada.</span><span class="sxs-lookup"><span data-stu-id="23725-564">Otherwise does nothing.</span></span> |
| <span data-ttu-id="23725-565">ESC \[ 3 g</span><span class="sxs-lookup"><span data-stu-id="23725-565">ESC \[ 3 g</span></span> | <span data-ttu-id="23725-566">TBC</span><span class="sxs-lookup"><span data-stu-id="23725-566">TBC</span></span> | <span data-ttu-id="23725-567">Borrado de tabulación (todas las columnas)</span><span class="sxs-lookup"><span data-stu-id="23725-567">Tab Clear (all columns)</span></span> | <span data-ttu-id="23725-568">Borra todas las tabulaciones establecidas actualmente.</span><span class="sxs-lookup"><span data-stu-id="23725-568">Clears all currently set tab stops.</span></span> |



- <span data-ttu-id="23725-569">En el caso de CHT y CBT, &lt; n &gt; es un parámetro opcional que (valor predeterminado = 1) que indica el número de veces que se debe avanzar el cursor en la dirección especificada.</span><span class="sxs-lookup"><span data-stu-id="23725-569">For both CHT and CBT, &lt;n&gt; is an optional parameter that (default=1) indicating how many times to advance the cursor in the specified direction.</span></span>
- <span data-ttu-id="23725-570">Si no se establece ninguna detención de tabulación a través de HTS, CHT y CBT tratarán la primera y la última columna de la ventana como las dos primeras tabulaciones.</span><span class="sxs-lookup"><span data-stu-id="23725-570">If there are no tab stops set via HTS, CHT and CBT will treat the first and last columns of the window as the only two tab stops.</span></span>
- <span data-ttu-id="23725-571">El uso de HTS para establecer una detención de tabulación también hará que la consola navegue hasta la siguiente detención de tabulación en el resultado de un carácter de TABULAción (0x09, ' \\ t '), de la misma manera que CHT.</span><span class="sxs-lookup"><span data-stu-id="23725-571">Using HTS to set a tab stop will also cause the console to navigate to the next tab stop on the output of a TAB (0x09, ‘\\t’) character, in the same manner as CHT.</span></span>

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span data-ttu-id="23725-572"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designación del juego de caracteres</span><span class="sxs-lookup"><span data-stu-id="23725-572"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designate Character Set</span></span>


<span data-ttu-id="23725-573">Las secuencias siguientes permiten que un programa cambie la asignación del juego de caracteres activo.</span><span class="sxs-lookup"><span data-stu-id="23725-573">The following sequences allow a program to change the active character set mapping.</span></span> <span data-ttu-id="23725-574">Esto permite que un programa emita caracteres ASCII de 7 bits, pero que se muestren como otros glifos en la pantalla del terminal.</span><span class="sxs-lookup"><span data-stu-id="23725-574">This allows a program to emit 7-bit ASCII characters, but have them displayed as other glyphs on the terminal screen itself.</span></span> <span data-ttu-id="23725-575">Actualmente, los únicos dos juegos de caracteres admitidos son ASCII (valor predeterminado) y el juego de caracteres de gráficos especiales DEC.</span><span class="sxs-lookup"><span data-stu-id="23725-575">Currently, the only two supported character sets are ASCII (default) and the DEC Special Graphics Character Set.</span></span> <span data-ttu-id="23725-576">Vea <http://vt100.net/docs/vt220-rm/table2-4.html> para obtener una lista de todos los caracteres representados por el juego de caracteres de gráficos especiales Dec.</span><span class="sxs-lookup"><span data-stu-id="23725-576">See <http://vt100.net/docs/vt220-rm/table2-4.html> for a listing of all of the characters represented by the DEC Special Graphics Character Set.</span></span>


| <span data-ttu-id="23725-577">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-577">Sequence</span></span> | <span data-ttu-id="23725-578">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-578">Description</span></span> | <span data-ttu-id="23725-579">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-579">Behavior</span></span> |
|----------|--------------------------------------------|-------------------------------|
| <span data-ttu-id="23725-580">ESC (0</span><span class="sxs-lookup"><span data-stu-id="23725-580">ESC ( 0</span></span> | <span data-ttu-id="23725-581">Designar juego de caracteres: DEC line Drawing</span><span class="sxs-lookup"><span data-stu-id="23725-581">Designate Character Set – DEC Line Drawing</span></span> | <span data-ttu-id="23725-582">Habilita el modo de dibujo de línea DEC</span><span class="sxs-lookup"><span data-stu-id="23725-582">Enables DEC Line Drawing Mode</span></span> |
| <span data-ttu-id="23725-583">ESC (B</span><span class="sxs-lookup"><span data-stu-id="23725-583">ESC ( B</span></span> | <span data-ttu-id="23725-584">Designar juego de caracteres: ASCII de EE. UU.</span><span class="sxs-lookup"><span data-stu-id="23725-584">Designate Character Set – US ASCII</span></span> | <span data-ttu-id="23725-585">Habilita el modo ASCII (valor predeterminado)</span><span class="sxs-lookup"><span data-stu-id="23725-585">Enables ASCII Mode (Default)</span></span> |



<span data-ttu-id="23725-586">En particular, el modo de dibujo de línea DEC se usa para dibujar los bordes en las aplicaciones de consola.</span><span class="sxs-lookup"><span data-stu-id="23725-586">Notably, the DEC Line Drawing mode is used for drawing borders in console applications.</span></span> <span data-ttu-id="23725-587">En la tabla siguiente se muestra qué caracteres ASCII se asignan al carácter de dibujo de línea.</span><span class="sxs-lookup"><span data-stu-id="23725-587">The following table shows what ASCII character maps to which line drawing character.</span></span>


| <span data-ttu-id="23725-588">Hex</span><span class="sxs-lookup"><span data-stu-id="23725-588">Hex</span></span> | <span data-ttu-id="23725-589">ASCII</span><span class="sxs-lookup"><span data-stu-id="23725-589">ASCII</span></span> | <span data-ttu-id="23725-590">Dibujo de línea DEC</span><span class="sxs-lookup"><span data-stu-id="23725-590">DEC Line Drawing</span></span> |
|------|-------|------------------|
| <span data-ttu-id="23725-591">0x6a</span><span class="sxs-lookup"><span data-stu-id="23725-591">0x6a</span></span> | <span data-ttu-id="23725-592">j</span><span class="sxs-lookup"><span data-stu-id="23725-592">j</span></span> | <span data-ttu-id="23725-593">┘</span><span class="sxs-lookup"><span data-stu-id="23725-593">┘</span></span> |
| <span data-ttu-id="23725-594">0x6b</span><span class="sxs-lookup"><span data-stu-id="23725-594">0x6b</span></span> | <span data-ttu-id="23725-595">k</span><span class="sxs-lookup"><span data-stu-id="23725-595">k</span></span> | <span data-ttu-id="23725-596">┐</span><span class="sxs-lookup"><span data-stu-id="23725-596">┐</span></span> |
| <span data-ttu-id="23725-597">0x6c</span><span class="sxs-lookup"><span data-stu-id="23725-597">0x6c</span></span> | <span data-ttu-id="23725-598">l</span><span class="sxs-lookup"><span data-stu-id="23725-598">l</span></span> | <span data-ttu-id="23725-599">┌</span><span class="sxs-lookup"><span data-stu-id="23725-599">┌</span></span> |
| <span data-ttu-id="23725-600">0x6d</span><span class="sxs-lookup"><span data-stu-id="23725-600">0x6d</span></span> | <span data-ttu-id="23725-601">m</span><span class="sxs-lookup"><span data-stu-id="23725-601">m</span></span> | <span data-ttu-id="23725-602">└</span><span class="sxs-lookup"><span data-stu-id="23725-602">└</span></span> |
| <span data-ttu-id="23725-603">0x6e</span><span class="sxs-lookup"><span data-stu-id="23725-603">0x6e</span></span> | <span data-ttu-id="23725-604">n</span><span class="sxs-lookup"><span data-stu-id="23725-604">n</span></span> | <span data-ttu-id="23725-605">┼</span><span class="sxs-lookup"><span data-stu-id="23725-605">┼</span></span> |
| <span data-ttu-id="23725-606">0x71</span><span class="sxs-lookup"><span data-stu-id="23725-606">0x71</span></span> | <span data-ttu-id="23725-607">q</span><span class="sxs-lookup"><span data-stu-id="23725-607">q</span></span> | <span data-ttu-id="23725-608">─</span><span class="sxs-lookup"><span data-stu-id="23725-608">─</span></span> |
| <span data-ttu-id="23725-609">0x74</span><span class="sxs-lookup"><span data-stu-id="23725-609">0x74</span></span> | <span data-ttu-id="23725-610">t</span><span class="sxs-lookup"><span data-stu-id="23725-610">t</span></span> | <span data-ttu-id="23725-611">├</span><span class="sxs-lookup"><span data-stu-id="23725-611">├</span></span> |
| <span data-ttu-id="23725-612">0x75</span><span class="sxs-lookup"><span data-stu-id="23725-612">0x75</span></span> | <span data-ttu-id="23725-613">u</span><span class="sxs-lookup"><span data-stu-id="23725-613">u</span></span> | <span data-ttu-id="23725-614">┤</span><span class="sxs-lookup"><span data-stu-id="23725-614">┤</span></span> |
| <span data-ttu-id="23725-615">0x76</span><span class="sxs-lookup"><span data-stu-id="23725-615">0x76</span></span> | <span data-ttu-id="23725-616">v</span><span class="sxs-lookup"><span data-stu-id="23725-616">v</span></span> | <span data-ttu-id="23725-617">┴</span><span class="sxs-lookup"><span data-stu-id="23725-617">┴</span></span> |
| <span data-ttu-id="23725-618">0x77</span><span class="sxs-lookup"><span data-stu-id="23725-618">0x77</span></span> | <span data-ttu-id="23725-619">w</span><span class="sxs-lookup"><span data-stu-id="23725-619">w</span></span> | <span data-ttu-id="23725-620">┬</span><span class="sxs-lookup"><span data-stu-id="23725-620">┬</span></span> |
| <span data-ttu-id="23725-621">0x78</span><span class="sxs-lookup"><span data-stu-id="23725-621">0x78</span></span> | <span data-ttu-id="23725-622">x</span><span class="sxs-lookup"><span data-stu-id="23725-622">x</span></span> | <span data-ttu-id="23725-623">│</span><span class="sxs-lookup"><span data-stu-id="23725-623">│</span></span> |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span data-ttu-id="23725-624"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Márgenes de desplazamiento</span><span class="sxs-lookup"><span data-stu-id="23725-624"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scrolling Margins</span></span>


<span data-ttu-id="23725-625">Las secuencias siguientes permiten a un programa configurar la "región de desplazamiento" de la pantalla que se ve afectada por las operaciones de desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="23725-625">The following sequences allow a program to configure the “scrolling region” of the screen that is affected by scrolling operations.</span></span> <span data-ttu-id="23725-626">Este es un subconjunto de las filas que se ajustan cuando la pantalla se desplazaría de otro modo, por ejemplo, en una ' \\ n ' o RI.</span><span class="sxs-lookup"><span data-stu-id="23725-626">This is a subset of the rows that are adjusted when the screen would otherwise scroll, for example, on a ‘\\n’ or RI.</span></span> <span data-ttu-id="23725-627">Estos márgenes también afectan a las filas modificadas por la inserción de línea (IL) y la línea de eliminación (DL), se desplazan hacia arriba (SU) y se desplazan hacia abajo (SD).</span><span class="sxs-lookup"><span data-stu-id="23725-627">These margins also affect the rows modified by Insert Line (IL) and Delete Line (DL), Scroll Up (SU) and Scroll Down (SD).</span></span>

<span data-ttu-id="23725-628">Los márgenes de desplazamiento pueden ser especialmente útiles para tener una parte de la pantalla que no se desplaza cuando se rellena el resto de la pantalla, como tener una barra de título en la parte superior o una barra de estado en la parte inferior de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="23725-628">The scrolling margins can be especially useful for having a portion of the screen that doesn’t scroll when the rest of the screen is filled, such as having a title bar at the top or a status bar at the bottom of your application.</span></span>

<span data-ttu-id="23725-629">En el caso de DECSTBM, hay dos parámetros opcionales, &lt; t &gt; y &lt; b &gt; , que se usan para especificar las filas que representan las líneas superior e inferior de la región de desplazamiento, ambos incluidos.</span><span class="sxs-lookup"><span data-stu-id="23725-629">For DECSTBM, there are two optional parameters, &lt;t&gt; and &lt;b&gt;, which are used to specify the rows that represent the top and bottom lines of the scroll region, inclusive.</span></span> <span data-ttu-id="23725-630">Si se omiten los parámetros, el &lt; &gt; valor predeterminado de t es 1 y &lt; b se toma de &gt; forma predeterminada en el alto de la ventanilla actual.</span><span class="sxs-lookup"><span data-stu-id="23725-630">If the parameters are omitted, &lt;t&gt; defaults to 1 and &lt;b&gt; defaults to the current viewport height.</span></span>

<span data-ttu-id="23725-631">Los márgenes de desplazamiento son por búfer, por lo que, lo que es importante, el búfer alternativo y el búfer principal mantienen configuraciones de márgenes de desplazamiento independientes (por lo que una aplicación de pantalla completa en el búfer alternativo no conseguirá los márgenes del búfer principal).</span><span class="sxs-lookup"><span data-stu-id="23725-631">Scrolling margins are per-buffer, so importantly, the Alternate Buffer and Main Buffer maintain separate scrolling margins settings (so a full screen application in the alternate buffer will not poison the main buffer’s margins).</span></span>


| <span data-ttu-id="23725-632">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-632">Sequence</span></span> | <span data-ttu-id="23725-633">Código</span><span class="sxs-lookup"><span data-stu-id="23725-633">Code</span></span> | <span data-ttu-id="23725-634">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-634">Description</span></span> | <span data-ttu-id="23725-635">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-635">Behavior</span></span> |
|--------------------------------|---------|----------------------|------------------------------------------------|
| <span data-ttu-id="23725-636">ESC \[ &lt; t &gt; ; &lt; b &gt; r</span><span class="sxs-lookup"><span data-stu-id="23725-636">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span></span> | <span data-ttu-id="23725-637">DECSTBM</span><span class="sxs-lookup"><span data-stu-id="23725-637">DECSTBM</span></span> | <span data-ttu-id="23725-638">Establecer región de desplazamiento</span><span class="sxs-lookup"><span data-stu-id="23725-638">Set Scrolling Region</span></span> | <span data-ttu-id="23725-639">Establece los márgenes de desplazamiento de VT de la ventanilla.</span><span class="sxs-lookup"><span data-stu-id="23725-639">Sets the VT scrolling margins of the viewport.</span></span> |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span data-ttu-id="23725-640"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Título de ventana</span><span class="sxs-lookup"><span data-stu-id="23725-640"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Window Title</span></span>


<span data-ttu-id="23725-641">Los siguientes comandos permiten que la aplicación establezca el título de la ventana de la consola en el &lt; parámetro de cadena especificado &gt; .</span><span class="sxs-lookup"><span data-stu-id="23725-641">The following commands allows the application to set the title of the console window to the given &lt;string&gt; parameter.</span></span> <span data-ttu-id="23725-642">La cadena debe tener menos de 255 caracteres para aceptar.</span><span class="sxs-lookup"><span data-stu-id="23725-642">The string must be less than 255 characters to be accepted.</span></span> <span data-ttu-id="23725-643">Esto es equivalente a llamar a SetConsoleTitle con la cadena especificada.</span><span class="sxs-lookup"><span data-stu-id="23725-643">This is equivalent to calling SetConsoleTitle with the given string.</span></span>

<span data-ttu-id="23725-644">Tenga en cuenta que estas secuencias son secuencias del OSC "comando del sistema operativo" y no un CSI como muchas de las otras secuencias enumeradas, y como tal comienza por " \\ X1b \] ", no por " \\ X1b \[ ".</span><span class="sxs-lookup"><span data-stu-id="23725-644">Note that these sequences are OSC “Operating system command” sequences, and not a CSI like many of the other sequences listed, and as such starts with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="23725-645">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-645">Sequence</span></span> | <span data-ttu-id="23725-646">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-646">Description</span></span> | <span data-ttu-id="23725-647">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-647">Behavior</span></span> |
|-------------------------------|---------------------------|----------------------------------------------------|
| <span data-ttu-id="23725-648">ESC \] 0; &lt; cadena &gt; Bel</span><span class="sxs-lookup"><span data-stu-id="23725-648">ESC \] 0 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="23725-649">Establecer el título de la ventana y el icono</span><span class="sxs-lookup"><span data-stu-id="23725-649">Set Icon and Window Title</span></span> | <span data-ttu-id="23725-650">Establece el título de la ventana de la consola en &lt; cadena &gt; .</span><span class="sxs-lookup"><span data-stu-id="23725-650">Sets the console window’s title to &lt;string&gt;.</span></span> |
| <span data-ttu-id="23725-651">ESC \] 2; &lt; cadena &gt; Bel</span><span class="sxs-lookup"><span data-stu-id="23725-651">ESC \] 2 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="23725-652">Establecer el título de la ventana</span><span class="sxs-lookup"><span data-stu-id="23725-652">Set Window Title</span></span> | <span data-ttu-id="23725-653">Establece el título de la ventana de la consola en &lt; cadena &gt; .</span><span class="sxs-lookup"><span data-stu-id="23725-653">Sets the console window’s title to &lt;string&gt;.</span></span> |



<span data-ttu-id="23725-654">El carácter de terminación aquí es el carácter "campana", " \\ x07".</span><span class="sxs-lookup"><span data-stu-id="23725-654">The terminating character here is the “Bell” character, ‘\\x07’</span></span>

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span data-ttu-id="23725-655"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Búfer de pantalla alternativo</span><span class="sxs-lookup"><span data-stu-id="23725-655"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternate Screen Buffer</span></span>


<span data-ttu-id="23725-656">\*Las aplicaciones de estilo Nix suelen utilizar un búfer de pantalla alternativo para que puedan modificar todo el contenido del búfer, sin que ello afecte a la aplicación que los inició.</span><span class="sxs-lookup"><span data-stu-id="23725-656">\*Nix style applications often utilize an alternate screen buffer, so that they can modify the entire contents of the buffer, without affecting the application that started them.</span></span> <span data-ttu-id="23725-657">El búfer alternativo es exactamente las dimensiones de la ventana, sin ninguna región desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="23725-657">The alternate buffer is exactly the dimensions of the window, without any scrollback region.</span></span>

<span data-ttu-id="23725-658">Para obtener un ejemplo de este comportamiento, tenga en cuenta Cuándo se inicia VIM desde bash.</span><span class="sxs-lookup"><span data-stu-id="23725-658">For an example of this behavior, consider when vim is launched from bash.</span></span> <span data-ttu-id="23725-659">VIM usa el completo de la pantalla para editar el archivo y, a continuación, si se vuelve a bash, el búfer original no se modifica.</span><span class="sxs-lookup"><span data-stu-id="23725-659">Vim uses the entirety of the screen to edit the file, then returning to bash leaves the original buffer unchanged.</span></span>


| <span data-ttu-id="23725-660">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-660">Sequence</span></span> | <span data-ttu-id="23725-661">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-661">Description</span></span> | <span data-ttu-id="23725-662">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-662">Behavior</span></span> |
|--------------------|-----------------------------|--------------------------------------------|
| <span data-ttu-id="23725-663">\[¿ESC?</span><span class="sxs-lookup"><span data-stu-id="23725-663">ESC \[ ?</span></span> <span data-ttu-id="23725-664">1 0 4 9 h</span><span class="sxs-lookup"><span data-stu-id="23725-664">1 0 4 9 h</span></span> | <span data-ttu-id="23725-665">Usar búfer de pantalla alternativo</span><span class="sxs-lookup"><span data-stu-id="23725-665">Use Alternate Screen Buffer</span></span> | <span data-ttu-id="23725-666">Cambia a un nuevo búfer de pantalla alternativo.</span><span class="sxs-lookup"><span data-stu-id="23725-666">Switches to a new alternate screen buffer.</span></span> |
| <span data-ttu-id="23725-667">\[¿ESC?</span><span class="sxs-lookup"><span data-stu-id="23725-667">ESC \[ ?</span></span> <span data-ttu-id="23725-668">1 0 4 9 l</span><span class="sxs-lookup"><span data-stu-id="23725-668">1 0 4 9 l</span></span> | <span data-ttu-id="23725-669">Usar búfer de pantalla principal</span><span class="sxs-lookup"><span data-stu-id="23725-669">Use Main Screen Buffer</span></span> | <span data-ttu-id="23725-670">Cambia al búfer principal.</span><span class="sxs-lookup"><span data-stu-id="23725-670">Switches to the main buffer.</span></span> |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span data-ttu-id="23725-671"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Ancho de la ventana</span><span class="sxs-lookup"><span data-stu-id="23725-671"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Window Width</span></span>


<span data-ttu-id="23725-672">Las secuencias siguientes se pueden usar para controlar el ancho de la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="23725-672">The following sequences can be used to control the width of the console window.</span></span> <span data-ttu-id="23725-673">Son aproximadamente equivalentes a la llamada a la API de la consola de SetConsoleScreenBufferInfoEx para establecer el ancho de la ventana.</span><span class="sxs-lookup"><span data-stu-id="23725-673">They are roughly equivalent to the calling the SetConsoleScreenBufferInfoEx console API to set the window width.</span></span>


| <span data-ttu-id="23725-674">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-674">Sequence</span></span> | <span data-ttu-id="23725-675">Código</span><span class="sxs-lookup"><span data-stu-id="23725-675">Code</span></span> | <span data-ttu-id="23725-676">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-676">Description</span></span> | <span data-ttu-id="23725-677">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-677">Behavior</span></span> |
|--------------|---------|------------------------------|---------------------------------------------|
| <span data-ttu-id="23725-678">\[¿ESC?</span><span class="sxs-lookup"><span data-stu-id="23725-678">ESC \[ ?</span></span> <span data-ttu-id="23725-679">3 h</span><span class="sxs-lookup"><span data-stu-id="23725-679">3 h</span></span> | <span data-ttu-id="23725-680">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="23725-680">DECCOLM</span></span> | <span data-ttu-id="23725-681">Establecer el número de columnas en 132</span><span class="sxs-lookup"><span data-stu-id="23725-681">Set Number of Columns to 132</span></span> | <span data-ttu-id="23725-682">Establece el ancho de la consola en 132 columnas de ancho.</span><span class="sxs-lookup"><span data-stu-id="23725-682">Sets the console width to 132 columns wide.</span></span> |
| <span data-ttu-id="23725-683">\[¿ESC?</span><span class="sxs-lookup"><span data-stu-id="23725-683">ESC \[ ?</span></span> <span data-ttu-id="23725-684">3 l</span><span class="sxs-lookup"><span data-stu-id="23725-684">3 l</span></span> | <span data-ttu-id="23725-685">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="23725-685">DECCOLM</span></span> | <span data-ttu-id="23725-686">Establecer el número de columnas en 80</span><span class="sxs-lookup"><span data-stu-id="23725-686">Set Number of Columns to 80</span></span> | <span data-ttu-id="23725-687">Establece el ancho de la consola en 80 columnas de ancho.</span><span class="sxs-lookup"><span data-stu-id="23725-687">Sets the console width to 80 columns wide.</span></span> |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span data-ttu-id="23725-688"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Restablecimiento parcial</span><span class="sxs-lookup"><span data-stu-id="23725-688"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Soft Reset</span></span>


<span data-ttu-id="23725-689">La siguiente secuencia se puede usar para restablecer los valores predeterminados de algunas propiedades. Las siguientes propiedades se restablecen a los siguientes valores predeterminados (también se muestran las secuencias que controlan esas propiedades):</span><span class="sxs-lookup"><span data-stu-id="23725-689">The following sequence can be used to reset certain properties to their default values.The following properties are reset to the following default values (also listed are the sequences that control those properties):</span></span>

- <span data-ttu-id="23725-690">Visibilidad del cursor: visible (DECTEM)</span><span class="sxs-lookup"><span data-stu-id="23725-690">Cursor visibility: visible (DECTEM)</span></span>
- <span data-ttu-id="23725-691">Teclado numérico: modo numérico (DECNKM)</span><span class="sxs-lookup"><span data-stu-id="23725-691">Numeric Keypad: Numeric Mode (DECNKM)</span></span>
- <span data-ttu-id="23725-692">Modo de teclas de cursor: modo normal (DECCKM)</span><span class="sxs-lookup"><span data-stu-id="23725-692">Cursor Keys Mode: Normal Mode (DECCKM)</span></span>
- <span data-ttu-id="23725-693">Márgenes superior e inferior: superior = 1, inferior = alto de la consola (DECSTBM)</span><span class="sxs-lookup"><span data-stu-id="23725-693">Top and Bottom Margins: Top=1, Bottom=Console height (DECSTBM)</span></span>
- <span data-ttu-id="23725-694">Juego de caracteres: ASCII de EE. UU.</span><span class="sxs-lookup"><span data-stu-id="23725-694">Character Set: US ASCII</span></span>
- <span data-ttu-id="23725-695">Representación de gráficos: predeterminada/desactivada (SGR)</span><span class="sxs-lookup"><span data-stu-id="23725-695">Graphics Rendition: Default/Off (SGR)</span></span>
- <span data-ttu-id="23725-696">Guardar estado del cursor: posición inicial (0,0) (DECSC)</span><span class="sxs-lookup"><span data-stu-id="23725-696">Save cursor state: Home position (0,0) (DECSC)</span></span>


| <span data-ttu-id="23725-697">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-697">Sequence</span></span> | <span data-ttu-id="23725-698">Código</span><span class="sxs-lookup"><span data-stu-id="23725-698">Code</span></span> | <span data-ttu-id="23725-699">Descripción</span><span class="sxs-lookup"><span data-stu-id="23725-699">Description</span></span> | <span data-ttu-id="23725-700">Comportamiento</span><span class="sxs-lookup"><span data-stu-id="23725-700">Behavior</span></span> |
|------------|--------|-------------|----------------------------------------------------|
| <span data-ttu-id="23725-701">ESC \[ !</span><span class="sxs-lookup"><span data-stu-id="23725-701">ESC \[ !</span></span> <span data-ttu-id="23725-702">p</span><span class="sxs-lookup"><span data-stu-id="23725-702">p</span></span> | <span data-ttu-id="23725-703">DECSTR</span><span class="sxs-lookup"><span data-stu-id="23725-703">DECSTR</span></span> | <span data-ttu-id="23725-704">Restablecimiento parcial</span><span class="sxs-lookup"><span data-stu-id="23725-704">Soft Reset</span></span> | <span data-ttu-id="23725-705">Restablezca los valores predeterminados de ciertas opciones de terminal.</span><span class="sxs-lookup"><span data-stu-id="23725-705">Reset certain terminal settings to their defaults.</span></span> |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span data-ttu-id="23725-706"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Secuencias de entrada</span><span class="sxs-lookup"><span data-stu-id="23725-706"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Input Sequences</span></span>


<span data-ttu-id="23725-707">El host de consola emite las siguientes secuencias de terminal en el flujo de entrada si el \_ \_ indicador de entrada habilitar terminal virtual \_ está establecido en el identificador de búfer de entrada mediante la marca SetConsoleMode.</span><span class="sxs-lookup"><span data-stu-id="23725-707">The following terminal sequences are emitted by the console host on the input stream if the ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag is set on the input buffer handle using the SetConsoleMode flag.</span></span>

<span data-ttu-id="23725-708">Hay dos modos internos que controlan qué secuencias se emiten para las teclas de entrada dadas, el modo de teclas de cursor y el modo de teclas del teclado.</span><span class="sxs-lookup"><span data-stu-id="23725-708">There are two internal modes that control which sequences are emitted for the given input keys, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="23725-709">Estos se describen en la sección cambios en el modo.</span><span class="sxs-lookup"><span data-stu-id="23725-709">These are described in the Mode Changes section.</span></span>

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span data-ttu-id="23725-710"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Teclas de cursor</span><span class="sxs-lookup"><span data-stu-id="23725-710"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Cursor Keys</span></span>


| <span data-ttu-id="23725-711">Clave</span><span class="sxs-lookup"><span data-stu-id="23725-711">Key</span></span> | <span data-ttu-id="23725-712">Modo normal</span><span class="sxs-lookup"><span data-stu-id="23725-712">Normal Mode</span></span> | <span data-ttu-id="23725-713">Modo de aplicación</span><span class="sxs-lookup"><span data-stu-id="23725-713">Application Mode</span></span> |
|-------------|-------------|------------------|
| <span data-ttu-id="23725-714">Flecha arriba</span><span class="sxs-lookup"><span data-stu-id="23725-714">Up Arrow</span></span> | <span data-ttu-id="23725-715">ESC \[ A</span><span class="sxs-lookup"><span data-stu-id="23725-715">ESC \[ A</span></span> | <span data-ttu-id="23725-716">ESC O A</span><span class="sxs-lookup"><span data-stu-id="23725-716">ESC O A</span></span> |
| <span data-ttu-id="23725-717">Flecha abajo</span><span class="sxs-lookup"><span data-stu-id="23725-717">Down Arrow</span></span> | <span data-ttu-id="23725-718">ESC \[ B</span><span class="sxs-lookup"><span data-stu-id="23725-718">ESC \[ B</span></span> | <span data-ttu-id="23725-719">ESC O B</span><span class="sxs-lookup"><span data-stu-id="23725-719">ESC O B</span></span> |
| <span data-ttu-id="23725-720">Flecha derecha</span><span class="sxs-lookup"><span data-stu-id="23725-720">Right Arrow</span></span> | <span data-ttu-id="23725-721">ESC \[ C</span><span class="sxs-lookup"><span data-stu-id="23725-721">ESC \[ C</span></span> | <span data-ttu-id="23725-722">ESC O C</span><span class="sxs-lookup"><span data-stu-id="23725-722">ESC O C</span></span> |
| <span data-ttu-id="23725-723">Flecha izquierda</span><span class="sxs-lookup"><span data-stu-id="23725-723">Left Arrow</span></span> | <span data-ttu-id="23725-724">ESC \[ D</span><span class="sxs-lookup"><span data-stu-id="23725-724">ESC \[ D</span></span> | <span data-ttu-id="23725-725">ESC O D</span><span class="sxs-lookup"><span data-stu-id="23725-725">ESC O D</span></span> |
| <span data-ttu-id="23725-726">Página principal</span><span class="sxs-lookup"><span data-stu-id="23725-726">Home</span></span> | <span data-ttu-id="23725-727">ESC \[ H</span><span class="sxs-lookup"><span data-stu-id="23725-727">ESC \[ H</span></span> | <span data-ttu-id="23725-728">ESC O H</span><span class="sxs-lookup"><span data-stu-id="23725-728">ESC O H</span></span> |
| <span data-ttu-id="23725-729">End</span><span class="sxs-lookup"><span data-stu-id="23725-729">End</span></span> | <span data-ttu-id="23725-730">ESC \[ F</span><span class="sxs-lookup"><span data-stu-id="23725-730">ESC \[ F</span></span> | <span data-ttu-id="23725-731">ESC O F</span><span class="sxs-lookup"><span data-stu-id="23725-731">ESC O F</span></span> |



<span data-ttu-id="23725-732">Además, si se presiona Ctrl con cualquiera de estas teclas, se emiten las secuencias siguientes en su lugar, independientemente del modo de teclas de cursor:</span><span class="sxs-lookup"><span data-stu-id="23725-732">Additionally, if Ctrl is pressed with any of these keys, the following sequences are emitted instead, regardless of the Cursor Keys Mode:</span></span>


| <span data-ttu-id="23725-733">Clave</span><span class="sxs-lookup"><span data-stu-id="23725-733">Key</span></span> | <span data-ttu-id="23725-734">Cualquier modo</span><span class="sxs-lookup"><span data-stu-id="23725-734">Any Mode</span></span> |
|--------------------|----------------|
| <span data-ttu-id="23725-735">Ctrl + flecha arriba</span><span class="sxs-lookup"><span data-stu-id="23725-735">Ctrl + Up Arrow</span></span> | <span data-ttu-id="23725-736">ESC \[ 1; 5 A</span><span class="sxs-lookup"><span data-stu-id="23725-736">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="23725-737">Ctrl + flecha abajo</span><span class="sxs-lookup"><span data-stu-id="23725-737">Ctrl + Down Arrow</span></span> | <span data-ttu-id="23725-738">ESC \[ 1; 5 B</span><span class="sxs-lookup"><span data-stu-id="23725-738">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="23725-739">Ctrl + flecha derecha</span><span class="sxs-lookup"><span data-stu-id="23725-739">Ctrl + Right Arrow</span></span> | <span data-ttu-id="23725-740">ESC \[ 1; 5 C</span><span class="sxs-lookup"><span data-stu-id="23725-740">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="23725-741">Ctrl + flecha izquierda</span><span class="sxs-lookup"><span data-stu-id="23725-741">Ctrl + Left Arrow</span></span> | <span data-ttu-id="23725-742">ESC \[ 1; 5 D</span><span class="sxs-lookup"><span data-stu-id="23725-742">ESC \[ 1 ; 5 D</span></span> |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span data-ttu-id="23725-743"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Teclas de función de & de teclado</span><span class="sxs-lookup"><span data-stu-id="23725-743"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad & Function Keys</span></span>


| <span data-ttu-id="23725-744">Clave</span><span class="sxs-lookup"><span data-stu-id="23725-744">Key</span></span> | <span data-ttu-id="23725-745">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-745">Sequence</span></span> |
|-----------|--------------|
| <span data-ttu-id="23725-746">Retroceso</span><span class="sxs-lookup"><span data-stu-id="23725-746">Backspace</span></span> | <span data-ttu-id="23725-747">0x7F (DEL)</span><span class="sxs-lookup"><span data-stu-id="23725-747">0x7f (DEL)</span></span> |
| <span data-ttu-id="23725-748">Pausar</span><span class="sxs-lookup"><span data-stu-id="23725-748">Pause</span></span> | <span data-ttu-id="23725-749">0x1A (SUB)</span><span class="sxs-lookup"><span data-stu-id="23725-749">0x1a (SUB)</span></span> |
| <span data-ttu-id="23725-750">Escape</span><span class="sxs-lookup"><span data-stu-id="23725-750">Escape</span></span> | <span data-ttu-id="23725-751">0x1b (ESC)</span><span class="sxs-lookup"><span data-stu-id="23725-751">0x1b (ESC)</span></span> |
| <span data-ttu-id="23725-752">Insertar</span><span class="sxs-lookup"><span data-stu-id="23725-752">Insert</span></span> | <span data-ttu-id="23725-753">ESC \[ 2 ~</span><span class="sxs-lookup"><span data-stu-id="23725-753">ESC \[ 2 ~</span></span> |
| <span data-ttu-id="23725-754">Eliminar</span><span class="sxs-lookup"><span data-stu-id="23725-754">Delete</span></span> | <span data-ttu-id="23725-755">ESC \[ 3 ~</span><span class="sxs-lookup"><span data-stu-id="23725-755">ESC \[ 3 ~</span></span> |
| <span data-ttu-id="23725-756">Re Pág</span><span class="sxs-lookup"><span data-stu-id="23725-756">Page Up</span></span> | <span data-ttu-id="23725-757">ESC \[ 5 ~</span><span class="sxs-lookup"><span data-stu-id="23725-757">ESC \[ 5 ~</span></span> |
| <span data-ttu-id="23725-758">Av Pág</span><span class="sxs-lookup"><span data-stu-id="23725-758">Page Down</span></span> | <span data-ttu-id="23725-759">ESC \[ 6 ~</span><span class="sxs-lookup"><span data-stu-id="23725-759">ESC \[ 6 ~</span></span> |
| <span data-ttu-id="23725-760">F1</span><span class="sxs-lookup"><span data-stu-id="23725-760">F1</span></span> | <span data-ttu-id="23725-761">ESC O P</span><span class="sxs-lookup"><span data-stu-id="23725-761">ESC O P</span></span> |
| <span data-ttu-id="23725-762">F2</span><span class="sxs-lookup"><span data-stu-id="23725-762">F2</span></span> | <span data-ttu-id="23725-763">ESC O Q</span><span class="sxs-lookup"><span data-stu-id="23725-763">ESC O Q</span></span> |
| <span data-ttu-id="23725-764">F3</span><span class="sxs-lookup"><span data-stu-id="23725-764">F3</span></span> | <span data-ttu-id="23725-765">ESC O R</span><span class="sxs-lookup"><span data-stu-id="23725-765">ESC O R</span></span> |
| <span data-ttu-id="23725-766">F4</span><span class="sxs-lookup"><span data-stu-id="23725-766">F4</span></span> | <span data-ttu-id="23725-767">ESC O S</span><span class="sxs-lookup"><span data-stu-id="23725-767">ESC O S</span></span> |
| <span data-ttu-id="23725-768">F5</span><span class="sxs-lookup"><span data-stu-id="23725-768">F5</span></span> | <span data-ttu-id="23725-769">ESC \[ 1 5 ~</span><span class="sxs-lookup"><span data-stu-id="23725-769">ESC \[ 1 5 ~</span></span> |
| <span data-ttu-id="23725-770">F6</span><span class="sxs-lookup"><span data-stu-id="23725-770">F6</span></span> | <span data-ttu-id="23725-771">ESC \[ 1 7 ~</span><span class="sxs-lookup"><span data-stu-id="23725-771">ESC \[ 1 7 ~</span></span> |
| <span data-ttu-id="23725-772">F7</span><span class="sxs-lookup"><span data-stu-id="23725-772">F7</span></span> | <span data-ttu-id="23725-773">ESC \[ 1 8 ~</span><span class="sxs-lookup"><span data-stu-id="23725-773">ESC \[ 1 8 ~</span></span> |
| <span data-ttu-id="23725-774">F8</span><span class="sxs-lookup"><span data-stu-id="23725-774">F8</span></span> | <span data-ttu-id="23725-775">ESC \[ 1 9 ~</span><span class="sxs-lookup"><span data-stu-id="23725-775">ESC \[ 1 9 ~</span></span> |
| <span data-ttu-id="23725-776">F9</span><span class="sxs-lookup"><span data-stu-id="23725-776">F9</span></span> | <span data-ttu-id="23725-777">ESC \[ 2 0 ~</span><span class="sxs-lookup"><span data-stu-id="23725-777">ESC \[ 2 0 ~</span></span> |
| <span data-ttu-id="23725-778">F10</span><span class="sxs-lookup"><span data-stu-id="23725-778">F10</span></span> | <span data-ttu-id="23725-779">ESC \[ 2 1 ~</span><span class="sxs-lookup"><span data-stu-id="23725-779">ESC \[ 2 1 ~</span></span> |
| <span data-ttu-id="23725-780">F11</span><span class="sxs-lookup"><span data-stu-id="23725-780">F11</span></span> | <span data-ttu-id="23725-781">ESC \[ 2 3 ~</span><span class="sxs-lookup"><span data-stu-id="23725-781">ESC \[ 2 3 ~</span></span> |
| <span data-ttu-id="23725-782">F12</span><span class="sxs-lookup"><span data-stu-id="23725-782">F12</span></span> | <span data-ttu-id="23725-783">ESC \[ 2 4 ~</span><span class="sxs-lookup"><span data-stu-id="23725-783">ESC \[ 2 4 ~</span></span> |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span data-ttu-id="23725-784"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modificadores</span><span class="sxs-lookup"><span data-stu-id="23725-784"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifiers</span></span>

<span data-ttu-id="23725-785">Alt se trata al prefijar la secuencia con un escape: ESC &lt; c, &gt; donde &lt; c &gt; es el carácter que pasa el sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="23725-785">Alt is treated by prefixing the sequence with an escape: ESC &lt;c&gt; where &lt;c&gt; is the character passed by the operating system.</span></span> <span data-ttu-id="23725-786">Alt + Ctrl se administra de la misma manera, salvo que el sistema operativo habrá desplazado la &lt; &gt; tecla c al carácter de control adecuado, que se retransmitirá a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="23725-786">Alt+Ctrl is handled the same way except that the operating system will have pre-shifted the &lt;c&gt; key to the appropriate control character which will be relayed to the application.</span></span>

<span data-ttu-id="23725-787">Ctrl suele pasar exactamente como se recibe del sistema.</span><span class="sxs-lookup"><span data-stu-id="23725-787">Ctrl is generally passed through exactly as received from the system.</span></span> <span data-ttu-id="23725-788">Suele ser un carácter único desplazado hacia abajo en el espacio reservado de carácter de control (0X0-0x1F).</span><span class="sxs-lookup"><span data-stu-id="23725-788">This is typically a single character shifted down into the control character reserved space (0x0-0x1f).</span></span> <span data-ttu-id="23725-789">Por ejemplo, Ctrl + @ (0x40) se convierte en NUL (0x00), Ctrl + \[ (0x5b) se convierte en ESC (0x1b), etc. Algunas combinaciones de teclas Ctrl se tratan de forma especial según la tabla siguiente:</span><span class="sxs-lookup"><span data-stu-id="23725-789">For example, Ctrl+@ (0x40) becomes NUL (0x00), Ctrl+\[ (0x5b) becomes ESC (0x1b), etc. A few Ctrl key combinations are treated specially according to the following table:</span></span>


| <span data-ttu-id="23725-790">Clave</span><span class="sxs-lookup"><span data-stu-id="23725-790">Key</span></span> | <span data-ttu-id="23725-791">Secuencia</span><span class="sxs-lookup"><span data-stu-id="23725-791">Sequence</span></span> |
|--------------------|----------------|
| <span data-ttu-id="23725-792">Ctrl + Espacio</span><span class="sxs-lookup"><span data-stu-id="23725-792">Ctrl + Space</span></span> | <span data-ttu-id="23725-793">0x00 (NUL)</span><span class="sxs-lookup"><span data-stu-id="23725-793">0x00 (NUL)</span></span> |
| <span data-ttu-id="23725-794">Ctrl + flecha arriba</span><span class="sxs-lookup"><span data-stu-id="23725-794">Ctrl + Up Arrow</span></span> | <span data-ttu-id="23725-795">ESC \[ 1; 5 A</span><span class="sxs-lookup"><span data-stu-id="23725-795">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="23725-796">Ctrl + flecha abajo</span><span class="sxs-lookup"><span data-stu-id="23725-796">Ctrl + Down Arrow</span></span> | <span data-ttu-id="23725-797">ESC \[ 1; 5 B</span><span class="sxs-lookup"><span data-stu-id="23725-797">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="23725-798">Ctrl + flecha derecha</span><span class="sxs-lookup"><span data-stu-id="23725-798">Ctrl + Right Arrow</span></span> | <span data-ttu-id="23725-799">ESC \[ 1; 5 C</span><span class="sxs-lookup"><span data-stu-id="23725-799">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="23725-800">Ctrl + flecha izquierda</span><span class="sxs-lookup"><span data-stu-id="23725-800">Ctrl + Left Arrow</span></span> | <span data-ttu-id="23725-801">ESC \[ 1; 5 D</span><span class="sxs-lookup"><span data-stu-id="23725-801">ESC \[ 1 ; 5 D</span></span> |



> [!NOTE]
><span data-ttu-id="23725-802">Left <kbd>Ctrl</kbd> + derecha <kbd>Alt</kbd> se trata como altgr.</span><span class="sxs-lookup"><span data-stu-id="23725-802">Left <kbd>Ctrl</kbd> + Right <kbd>Alt</kbd> is treated as AltGr.</span></span> <span data-ttu-id="23725-803">Cuando ambos se ven juntos, se eliminarán y el valor Unicode del carácter presentado por el sistema se pasará al destino.</span><span class="sxs-lookup"><span data-stu-id="23725-803">When both are seen together, they will be stripped and the Unicode value of the character presented by the system will be passed into the target.</span></span> <span data-ttu-id="23725-804">El sistema traducirá previamente los valores de AltGr según la configuración de entrada del sistema actual.</span><span class="sxs-lookup"><span data-stu-id="23725-804">The system will pre-translate AltGr values according to the current system input settings.</span></span>



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span data-ttu-id="23725-805"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Assembl</span><span class="sxs-lookup"><span data-stu-id="23725-805"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Samples</span></span>


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span data-ttu-id="23725-806"><span id="example"></span><span id="EXAMPLE"></span>Ejemplo de secuencias terminales de SGR</span><span class="sxs-lookup"><span data-stu-id="23725-806"><span id="example"></span><span id="EXAMPLE"></span>Example of SGR terminal sequences</span></span>

<span data-ttu-id="23725-807">En el código siguiente se proporcionan varios ejemplos de formato de texto.</span><span class="sxs-lookup"><span data-stu-id="23725-807">The following code provides several examples of text formatting.</span></span>

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
><span data-ttu-id="23725-808">En el ejemplo anterior, la cadena ' `\x1b[31m` ' es la implementación de **Esc \[ &lt; n &gt; m** con &lt; n &gt; siendo 31.</span><span class="sxs-lookup"><span data-stu-id="23725-808">In the previous example, the string '`\x1b[31m`' is the implementation of **ESC \[ &lt;n&gt; m** with &lt;n&gt; being 31.</span></span>



<span data-ttu-id="23725-809">En el gráfico siguiente se muestra la salida del ejemplo de código anterior.</span><span class="sxs-lookup"><span data-stu-id="23725-809">The following graphic shows the output of the previous code example.</span></span>

![salida de la consola con el comando SGR](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span data-ttu-id="23725-811"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Ejemplo de cómo habilitar el procesamiento de terminal virtual</span><span class="sxs-lookup"><span data-stu-id="23725-811"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Example of Enabling Virtual Terminal Processing</span></span>

<span data-ttu-id="23725-812">El código siguiente proporciona un ejemplo de la manera recomendada de habilitar el procesamiento de terminal virtual para una aplicación.</span><span class="sxs-lookup"><span data-stu-id="23725-812">The following code provides an example of the recommended way to enable virtual terminal processing for an application.</span></span> <span data-ttu-id="23725-813">El propósito del ejemplo es mostrar:</span><span class="sxs-lookup"><span data-stu-id="23725-813">The intent of the sample is to demonstrate:</span></span>

1. <span data-ttu-id="23725-814">El modo existente siempre debe recuperarse a través de GetConsoleMode y analizarse antes de establecerse con SetConsoleMode.</span><span class="sxs-lookup"><span data-stu-id="23725-814">The existing mode should always be retrieved via GetConsoleMode and analyzed before being set with SetConsoleMode.</span></span>

2. <span data-ttu-id="23725-815">Comprobando si SetConsoleMode devuelve `0` y GetLastError devuelve \_ \_ el estado el parámetro no válido es el mecanismo actual para determinar cuándo se ejecuta en un sistema de nivel inferior.</span><span class="sxs-lookup"><span data-stu-id="23725-815">Checking whether SetConsoleMode returns `0` and GetLastError returns STATUS\_INVALID\_PARAMETER is the current mechanism to determine when running on a down-level system.</span></span> <span data-ttu-id="23725-816">Un \_ parámetro no válido de estado de recepción de \_ la aplicación con una de las marcas de modo de consola más recientes del campo de bits debe degradar el comportamiento correctamente e intentarlo de nuevo.</span><span class="sxs-lookup"><span data-stu-id="23725-816">An application receiving STATUS\_INVALID\_PARAMETER with one of the newer console mode flags in the bit field should gracefully degrade behavior and try again.</span></span>

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

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span data-ttu-id="23725-817"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Ejemplo de características de selección de actualización de aniversario</span><span class="sxs-lookup"><span data-stu-id="23725-817"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Example of Select Anniversary Update Features</span></span>

<span data-ttu-id="23725-818">El ejemplo siguiente pretende ser un ejemplo más sólido de código que usa una variedad de secuencias de escape para manipular el búfer, con énfasis en las características agregadas en la actualización de aniversario para Windows 10.</span><span class="sxs-lookup"><span data-stu-id="23725-818">The following example is intended to be a more robust example of code using a variety of escape sequences to manipulate the buffer, with an emphasis on the features added in the Anniversary Update for Windows 10.</span></span>

<span data-ttu-id="23725-819">En este ejemplo se usa el búfer de pantalla alternativo, se manipulan las tabulaciones, se establecen los márgenes de desplazamiento y se cambia el juego de caracteres.</span><span class="sxs-lookup"><span data-stu-id="23725-819">This example makes use of the alternate screen buffer, manipulating tab stops, setting scrolling margins, and changing the character set.</span></span>

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








