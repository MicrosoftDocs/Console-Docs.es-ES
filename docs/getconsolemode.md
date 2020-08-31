---
title: GetConsoleMode función)
description: Recupera el modo de entrada actual del búfer de entrada de una consola o el modo de salida actual de un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/GetConsoleMode
- wincon/GetConsoleMode
- GetConsoleMode
MS-HAID:
- '\_win32\_getconsolemode'
- base.getconsolemode
- consoles.getconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 49adf618-196d-4490-93ca-cd177807f58e
topic_type:
- apiref
api_name:
- GetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a2d18ed191d1d82cc54c3277aa38badb0aedb630
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060676"
---
# <a name="getconsolemode-function"></a><span data-ttu-id="45ab8-104">GetConsoleMode función)</span><span class="sxs-lookup"><span data-stu-id="45ab8-104">GetConsoleMode function</span></span>


<span data-ttu-id="45ab8-105">Recupera el modo de entrada actual del búfer de entrada de una consola o el modo de salida actual de un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="45ab8-105">Retrieves the current input mode of a console's input buffer or the current output mode of a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="45ab8-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="45ab8-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleMode(
  _In_  HANDLE  hConsoleHandle,
  _Out_ LPDWORD lpMode
);
```

<a name="parameters"></a><span data-ttu-id="45ab8-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="45ab8-107">Parameters</span></span>
----------

<span data-ttu-id="45ab8-108">*hConsoleHandle* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="45ab8-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="45ab8-109">Identificador para el búfer de entrada de la consola o el búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="45ab8-109">A handle to the console input buffer or the console screen buffer.</span></span> <span data-ttu-id="45ab8-110">El identificador debe tener el derecho de acceso de \*\* \_ lectura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="45ab8-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="45ab8-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="45ab8-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="45ab8-112">*lpMode* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="45ab8-112">*lpMode* \[out\]</span></span>  
<span data-ttu-id="45ab8-113">Puntero a una variable que recibe el modo actual del búfer especificado.</span><span class="sxs-lookup"><span data-stu-id="45ab8-113">A pointer to a variable that receives the current mode of the specified buffer.</span></span>

<span data-ttu-id="45ab8-114">Si el parámetro *hConsoleHandle* es un identificador de entrada, el modo puede ser uno o varios de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="45ab8-114">If the *hConsoleHandle* parameter is an input handle, the mode can be one or more of the following values.</span></span> <span data-ttu-id="45ab8-115">Cuando se crea una consola, todos los modos de entrada excepto **habilitar \_ \_ entrada de ventana** están habilitados de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="45ab8-115">When a console is created, all input modes except **ENABLE\_WINDOW\_INPUT** are enabled by default.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="45ab8-116">Valor</span><span class="sxs-lookup"><span data-stu-id="45ab8-116">Value</span></span></th>
<th><span data-ttu-id="45ab8-117">Significado</span><span class="sxs-lookup"><span data-stu-id="45ab8-117">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="45ab8-118"><span id="ENABLE_ECHO_INPUT"></span><span id="enable_echo_input"></span>
<strong>ENABLE_ECHO_INPUT</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="45ab8-118"><span id="ENABLE_ECHO_INPUT"></span><span id="enable_echo_input"></span>
<strong>ENABLE_ECHO_INPUT</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="45ab8-119">Los caracteres leídos por la función <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>readfile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> se escriben en el búfer de pantalla activo mientras se leen.</span><span class="sxs-lookup"><span data-stu-id="45ab8-119">Characters read by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function are written to the active screen buffer as they are read.</span></span> <span data-ttu-id="45ab8-120">Este modo solo se puede usar si el modo de <strong>ENABLE_LINE_INPUT</strong> también está habilitado.</span><span class="sxs-lookup"><span data-stu-id="45ab8-120">This mode can be used only if the <strong>ENABLE_LINE_INPUT</strong> mode is also enabled.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="45ab8-121"><span id="ENABLE_INSERT_MODE"></span><span id="enable_insert_mode"></span>
<strong>ENABLE_INSERT_MODE</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="45ab8-121"><span id="ENABLE_INSERT_MODE"></span><span id="enable_insert_mode"></span>
<strong>ENABLE_INSERT_MODE</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="45ab8-122">Cuando está habilitado, el texto especificado en una ventana de la consola se insertará en la ubicación actual del cursor y no se sobrescribirá todo el texto que sigue a esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="45ab8-122">When enabled, text entered in a console window will be inserted at the current cursor location and all text following that location will not be overwritten.</span></span> <span data-ttu-id="45ab8-123">Cuando está deshabilitada, se sobrescribirá todo el texto siguiente.</span><span class="sxs-lookup"><span data-stu-id="45ab8-123">When disabled, all following text will be overwritten.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="45ab8-124"><span id="ENABLE_LINE_INPUT"></span><span id="enable_line_input"></span>
<strong>ENABLE_LINE_INPUT</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="45ab8-124"><span id="ENABLE_LINE_INPUT"></span><span id="enable_line_input"></span>
<strong>ENABLE_LINE_INPUT</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="45ab8-125">La función <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>readfile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> solo devuelve cuando se lee un carácter de retorno de carro.</span><span class="sxs-lookup"><span data-stu-id="45ab8-125">The <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function returns only when a carriage return character is read.</span></span> <span data-ttu-id="45ab8-126">Si este modo está deshabilitado, las funciones devuelven cuando uno o varios caracteres están disponibles.</span><span class="sxs-lookup"><span data-stu-id="45ab8-126">If this mode is disabled, the functions return when one or more characters are available.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="45ab8-127"><span id="ENABLE_MOUSE_INPUT"></span><span id="enable_mouse_input"></span>
<strong>ENABLE_MOUSE_INPUT</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="45ab8-127"><span id="ENABLE_MOUSE_INPUT"></span><span id="enable_mouse_input"></span>
<strong>ENABLE_MOUSE_INPUT</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="45ab8-128">Si el puntero del mouse está dentro de los bordes de la ventana de la consola y la ventana tiene el foco de teclado, los eventos del mouse generados por el movimiento del mouse y las pulsaciones de botón se colocan en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="45ab8-128">If the mouse pointer is within the borders of the console window and the window has the keyboard focus, mouse events generated by mouse movement and button presses are placed in the input buffer.</span></span> <span data-ttu-id="45ab8-129"><a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>Readfile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>descartan estos eventos, incluso cuando este modo está habilitado.</span><span class="sxs-lookup"><span data-stu-id="45ab8-129">These events are discarded by <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, even when this mode is enabled.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="45ab8-130"><span id="ENABLE_PROCESSED_INPUT"></span><span id="enable_processed_input"></span>
<strong>ENABLE_PROCESSED_INPUT</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="45ab8-130"><span id="ENABLE_PROCESSED_INPUT"></span><span id="enable_processed_input"></span>
<strong>ENABLE_PROCESSED_INPUT</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="45ab8-131">El sistema procesa CTRL + C y no se coloca en el búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="45ab8-131">CTRL+C is processed by the system and is not placed in the input buffer.</span></span> <span data-ttu-id="45ab8-132">Si <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>readfile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>leen el búfer de entrada, el sistema procesa otras claves de control y no se devuelven en el búfer <strong>readfile</strong> o <strong>ReadConsole</strong> .</span><span class="sxs-lookup"><span data-stu-id="45ab8-132">If the input buffer is being read by <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, other control keys are processed by the system and are not returned in the <strong>ReadFile</strong> or <strong>ReadConsole</strong> buffer.</span></span> <span data-ttu-id="45ab8-133">Si el modo de <strong>ENABLE_LINE_INPUT</strong> también está habilitado, el sistema controla el retroceso, el retorno de carro y los caracteres de avance de línea.</span><span class="sxs-lookup"><span data-stu-id="45ab8-133">If the <strong>ENABLE_LINE_INPUT</strong> mode is also enabled, backspace, carriage return, and line feed characters are handled by the system.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="45ab8-134"><span id="ENABLE_QUICK_EDIT_MODE"></span><span id="enable_quick_edit_mode"></span>
<strong>ENABLE_QUICK_EDIT_MODE</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="45ab8-134"><span id="ENABLE_QUICK_EDIT_MODE"></span><span id="enable_quick_edit_mode"></span>
<strong>ENABLE_QUICK_EDIT_MODE</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="45ab8-135">Esta marca permite al usuario utilizar el mouse para seleccionar y editar texto.</span><span class="sxs-lookup"><span data-stu-id="45ab8-135">This flag enables the user to use the mouse to select and edit text.</span></span></p>
<p><span data-ttu-id="45ab8-136">Para habilitar este modo, use <code>ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS</code> .</span><span class="sxs-lookup"><span data-stu-id="45ab8-136">To enable this mode, use <code>ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS</code>.</span></span> <span data-ttu-id="45ab8-137">Para deshabilitar este modo, utilice <strong>ENABLE_EXTENDED_FLAGS</strong> sin esta marca.</span><span class="sxs-lookup"><span data-stu-id="45ab8-137">To disable this mode, use <strong>ENABLE_EXTENDED_FLAGS</strong> without this flag.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="45ab8-138"><span id="ENABLE_WINDOW_INPUT"></span><span id="enable_window_input"></span>
<strong>ENABLE_WINDOW_INPUT</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="45ab8-138"><span id="ENABLE_WINDOW_INPUT"></span><span id="enable_window_input"></span>
<strong>ENABLE_WINDOW_INPUT</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="45ab8-139">Las interacciones de usuario que cambian el tamaño del búfer de pantalla de la consola se muestran en el búfer de entrada de la consola de&#39;s.</span><span class="sxs-lookup"><span data-stu-id="45ab8-139">User interactions that change the size of the console screen buffer are reported in the console&#39;s input buffer.</span></span> <span data-ttu-id="45ab8-140">La información sobre estos eventos se puede leer desde el búfer de entrada mediante aplicaciones que usan la función <a href="readconsoleinput.md" data-raw-source="[&lt;strong&gt;ReadConsoleInput&lt;/strong&gt;](readconsoleinput.md)"><strong>ReadConsoleInput</strong></a> , pero no para los que usan <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>readfile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>.</span><span class="sxs-lookup"><span data-stu-id="45ab8-140">Information about these events can be read from the input buffer by applications using the <a href="readconsoleinput.md" data-raw-source="[&lt;strong&gt;ReadConsoleInput&lt;/strong&gt;](readconsoleinput.md)"><strong>ReadConsoleInput</strong></a> function, but not by those using <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="45ab8-141"><span id="ENABLE_VIRTUAL_TERMINAL_INPUT"></span><span id="enable_virtual_terminal_input"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_INPUT</strong> 0x0200</span><span class="sxs-lookup"><span data-stu-id="45ab8-141"><span id="ENABLE_VIRTUAL_TERMINAL_INPUT"></span><span id="enable_virtual_terminal_input"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_INPUT</strong> 0x0200</span></span></td>
<td><p><span data-ttu-id="45ab8-142">Al establecer esta marca, se indica al motor de procesamiento de terminal virtuales que convierta las entradas de usuario recibidas por la ventana de la consola en <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">secuencias de terminal virtuales</a> de la consola que se pueden recuperar mediante una aplicación auxiliar a través de las funciones <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> .</span><span class="sxs-lookup"><span data-stu-id="45ab8-142">Setting this flag directs the Virtual Terminal processing engine to convert user input received by the console window into <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">Console Virtual Terminal Sequences</a> that can be retrieved by a supporting application through <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> functions.</span></span></p>
<p><span data-ttu-id="45ab8-143">El uso típico de esta marca está pensado junto con ENABLE_VIRTUAL_TERMINAL_PROCESSING en el identificador de salida para conectarse a una aplicación que se comunica exclusivamente a través de secuencias de terminales virtuales.</span><span class="sxs-lookup"><span data-stu-id="45ab8-143">The typical usage of this flag is intended in conjunction with ENABLE_VIRTUAL_TERMINAL_PROCESSING on the output handle to connect to an application that communicates exclusively via virtual terminal sequences.</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="45ab8-144">Si el parámetro *hConsoleHandle* es un controlador de búfer de pantalla, el modo puede ser uno o varios de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="45ab8-144">If the *hConsoleHandle* parameter is a screen buffer handle, the mode can be one or more of the following values.</span></span> <span data-ttu-id="45ab8-145">Cuando se crea un búfer de pantalla, ambos modos de salida están habilitados de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="45ab8-145">When a screen buffer is created, both output modes are enabled by default.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="45ab8-146">Valor</span><span class="sxs-lookup"><span data-stu-id="45ab8-146">Value</span></span></th>
<th><span data-ttu-id="45ab8-147">Significado</span><span class="sxs-lookup"><span data-stu-id="45ab8-147">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="45ab8-148"><span id="ENABLE_PROCESSED_OUTPUT"></span><span id="enable_processed_output"></span>
<strong>ENABLE_PROCESSED_OUTPUT</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="45ab8-148"><span id="ENABLE_PROCESSED_OUTPUT"></span><span id="enable_processed_output"></span>
<strong>ENABLE_PROCESSED_OUTPUT</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="45ab8-149">Los caracteres escritos por la función <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> o que se han devuelto por la función <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>readfile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> se analizan para las secuencias de control ASCII y se realiza la acción correcta.</span><span class="sxs-lookup"><span data-stu-id="45ab8-149">Characters written by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> function or echoed by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function are parsed for ASCII control sequences, and the correct action is performed.</span></span> <span data-ttu-id="45ab8-150">Se procesan los caracteres de retroceso, tabulación, campana, retorno de carro y avance de línea.</span><span class="sxs-lookup"><span data-stu-id="45ab8-150">Backspace, tab, bell, carriage return, and line feed characters are processed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="45ab8-151"><span id="ENABLE_WRAP_AT_EOL_OUTPUT"></span><span id="enable_wrap_at_eol_output"></span>
<strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="45ab8-151"><span id="ENABLE_WRAP_AT_EOL_OUTPUT"></span><span id="enable_wrap_at_eol_output"></span>
<strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="45ab8-152">Al escribir con <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> o al repetir con <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>readfile</strong></a> o <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, el cursor se desplaza al principio de la fila siguiente cuando llega al final de la fila actual.</span><span class="sxs-lookup"><span data-stu-id="45ab8-152">When writing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> or echoing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, the cursor moves to the beginning of the next row when it reaches the end of the current row.</span></span> <span data-ttu-id="45ab8-153">Esto hace que las filas mostradas en la ventana de la consola se desplacen automáticamente cuando el cursor avance más allá de la última fila de la ventana.</span><span class="sxs-lookup"><span data-stu-id="45ab8-153">This causes the rows displayed in the console window to scroll up automatically when the cursor advances beyond the last row in the window.</span></span> <span data-ttu-id="45ab8-154">También hace que el contenido del búfer de pantalla de la consola se desplace hacia arriba (descartando la fila superior del búfer de pantalla de la consola) cuando el cursor avanza más allá de la última fila del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="45ab8-154">It also causes the contents of the console screen buffer to scroll up (discarding the top row of the console screen buffer) when the cursor advances beyond the last row in the console screen buffer.</span></span> <span data-ttu-id="45ab8-155">Si este modo está deshabilitado, el último carácter de la fila se sobrescribe con los caracteres posteriores.</span><span class="sxs-lookup"><span data-stu-id="45ab8-155">If this mode is disabled, the last character in the row is overwritten with any subsequent characters.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="45ab8-156"><span id="ENABLE_VIRTUAL_TERMINAL_PROCESSING"></span><span id="enable_virtual_terminal_processing"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_PROCESSING</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="45ab8-156"><span id="ENABLE_VIRTUAL_TERMINAL_PROCESSING"></span><span id="enable_virtual_terminal_processing"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_PROCESSING</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="45ab8-157">Al escribir con <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, se analizan los caracteres de las secuencias de caracteres de control de VT100 y similares que controlan el movimiento del cursor, el modo de color/fuente y otras operaciones que también se pueden realizar a través de las API de consola existentes.</span><span class="sxs-lookup"><span data-stu-id="45ab8-157">When writing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, characters are parsed for VT100 and similar control character sequences that control cursor movement, color/font mode, and other operations that can also be performed via the existing Console APIs.</span></span> <span data-ttu-id="45ab8-158">Para obtener más información, vea <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">secuencias de terminal virtuales de consola</a>.</span><span class="sxs-lookup"><span data-stu-id="45ab8-158">For more information, see <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">Console Virtual Terminal Sequences</a>.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="45ab8-159"><span id="DISABLE_NEWLINE_AUTO_RETURN"></span><span id="disable_newline_auto_return"></span>
<strong>DISABLE_NEWLINE_AUTO_RETURN</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="45ab8-159"><span id="DISABLE_NEWLINE_AUTO_RETURN"></span><span id="disable_newline_auto_return"></span>
<strong>DISABLE_NEWLINE_AUTO_RETURN</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="45ab8-160">Al escribir con <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> o <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, se agrega un estado adicional al ajuste de final de línea que puede retrasar las operaciones de movimiento de cursor y desplazamiento de búfer.</span><span class="sxs-lookup"><span data-stu-id="45ab8-160">When writing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, this adds an additional state to end-of-line wrapping that can delay the cursor move and buffer scroll operations.</span></span></p>
<p><span data-ttu-id="45ab8-161">Normalmente, cuando se establece ENABLE_WRAP_AT_EOL_OUTPUT y el texto alcanza el final de la línea, el cursor se mueve inmediatamente a la línea siguiente y el contenido del búfer se desplaza hacia arriba una línea.</span><span class="sxs-lookup"><span data-stu-id="45ab8-161">Normally when ENABLE_WRAP_AT_EOL_OUTPUT is set and text reaches the end of the line, the cursor will immediately move to the next line and the contents of the buffer will scroll up by one line.</span></span> <span data-ttu-id="45ab8-162">A diferencia de este conjunto de marcadores, la operación de desplazamiento y el movimiento del cursor se retrasan hasta que llega el siguiente carácter.</span><span class="sxs-lookup"><span data-stu-id="45ab8-162">In contrast with this flag set, the scroll operation and cursor move is delayed until the next character arrives.</span></span> <span data-ttu-id="45ab8-163">El carácter escrito se imprimirá en la posición final de la línea y el cursor permanecerá por encima de este carácter como si ENABLE_WRAP_AT_EOL_OUTPUT fuera OFF, pero el siguiente carácter imprimible se imprimirá como si ENABLE_WRAP_AT_EOL_OUTPUT estuviera activada.</span><span class="sxs-lookup"><span data-stu-id="45ab8-163">The written character will be printed in the final position on the line and the cursor will remain above this character as if ENABLE_WRAP_AT_EOL_OUTPUT was off, but the next printable character will be printed as if ENABLE_WRAP_AT_EOL_OUTPUT is on.</span></span> <span data-ttu-id="45ab8-164">No se producirá ninguna sobrescritura.</span><span class="sxs-lookup"><span data-stu-id="45ab8-164">No overwrite will occur.</span></span> <span data-ttu-id="45ab8-165">En concreto, el cursor avanza rápidamente hasta la línea siguiente, se realiza un desplazamiento si es necesario, se imprime el carácter y el cursor se desplaza una posición más.</span><span class="sxs-lookup"><span data-stu-id="45ab8-165">Specifically, the cursor quickly advances down to the following line, a scroll is performed if necessary, the character is printed, and the cursor advances one more position.</span></span></p>
<p><span data-ttu-id="45ab8-166">El uso típico de esta marca está pensado junto con la configuración ENABLE_VIRTUAL_TERMINAL_PROCESSING para emular mejor un emulador de terminal en el que escribir el carácter final en la pantalla (en la esquina inferior derecha) sin desencadenar un desplazamiento inmediato es el comportamiento deseado.</span><span class="sxs-lookup"><span data-stu-id="45ab8-166">The typical usage of this flag is intended in conjunction with setting ENABLE_VIRTUAL_TERMINAL_PROCESSING to better emulate a terminal emulator where writing the final character on the screen (in the bottom right corner) without triggering an immediate scroll is the desired behavior.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="45ab8-167"><span id="ENABLE_LVB_GRID_WORLDWIDE"></span><span id="enable_lvb_grid_worldwide"></span>
<strong>ENABLE_LVB_GRID_WORLDWIDE</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="45ab8-167"><span id="ENABLE_LVB_GRID_WORLDWIDE"></span><span id="enable_lvb_grid_worldwide"></span>
<strong>ENABLE_LVB_GRID_WORLDWIDE</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="45ab8-168">Las API para escribir atributos de caracteres, incluidos <a href="writeconsoleoutput.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutput&lt;/strong&gt;](writeconsoleoutput.md)"><strong>WriteConsoleOutput</strong></a> y <a href="writeconsoleoutputattribute.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutputAttribute&lt;/strong&gt;](writeconsoleoutputattribute.md)"><strong>WriteConsoleOutputAttribute</strong></a> , permiten el uso de marcas de <a href="https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes" data-raw-source="[character attributes](https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes)">atributos de caracteres</a> para ajustar el color de primer plano y de fondo del texto.</span><span class="sxs-lookup"><span data-stu-id="45ab8-168">The APIs for writing character attributes including <a href="writeconsoleoutput.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutput&lt;/strong&gt;](writeconsoleoutput.md)"><strong>WriteConsoleOutput</strong></a> and <a href="writeconsoleoutputattribute.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutputAttribute&lt;/strong&gt;](writeconsoleoutputattribute.md)"><strong>WriteConsoleOutputAttribute</strong></a> allow the usage of flags from <a href="https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes" data-raw-source="[character attributes](https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes)">character attributes</a> to adjust the color of the foreground and background of text.</span></span> <span data-ttu-id="45ab8-169">Además, se especificó un intervalo de marcas DBCS con el prefijo COMMON_LVB.</span><span class="sxs-lookup"><span data-stu-id="45ab8-169">Additionally, a range of DBCS flags was specified with the COMMON_LVB prefix.</span></span> <span data-ttu-id="45ab8-170">Históricamente, estas marcas solo funcionaban en páginas de códigos DBCS para idiomas chinos, japoneses y coreanos.</span><span class="sxs-lookup"><span data-stu-id="45ab8-170">Historically, these flags only functioned in DBCS code pages for Chinese, Japanese, and Korean languages.</span></span></p>
<p><span data-ttu-id="45ab8-171">Con la excepción de las marcas de bytes iniciales y finales, los marcadores restantes que describen el dibujo de líneas y el vídeo inverso (cambiar los colores de primer plano y de fondo) pueden ser útiles para que otros lenguajes resalten partes de la salida.</span><span class="sxs-lookup"><span data-stu-id="45ab8-171">With exception of the leading byte and trailing byte flags, the remaining flags describing line drawing and reverse video (swap foreground and background colors) can be useful for other languages to emphasize portions of output.</span></span></p>
<p><span data-ttu-id="45ab8-172">Al establecer esta marca de modo de consola, se permitirá utilizar estos atributos en todas las páginas de códigos de todos los lenguajes.</span><span class="sxs-lookup"><span data-stu-id="45ab8-172">Setting this console mode flag will allow these attributes to be used in every code page on every language.</span></span></p>
<p><span data-ttu-id="45ab8-173">Está desactivada de forma predeterminada para mantener la compatibilidad con las aplicaciones conocidas que han aprovechado históricamente la consola y omitir estas marcas en máquinas no CJK para almacenar bits en estos campos por su propio propósito o por accidente.</span><span class="sxs-lookup"><span data-stu-id="45ab8-173">It is off by default to maintain compatibility with known applications that have historically taken advantage of the console ignoring these flags on non-CJK machines to store bits in these fields for their own purposes or by accident.</span></span></p>
<p><span data-ttu-id="45ab8-174">Tenga en cuenta que el uso del modo ENABLE_VIRTUAL_TERMINAL_PROCESSING puede dar lugar a la cuadrícula de LVB y a que se establezcan marcas de vídeo inverso, mientras que la aplicación conectada solicita el subrayado o el vídeo inverso a través de las <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">secuencias de terminal virtuales</a>de la consola.</span><span class="sxs-lookup"><span data-stu-id="45ab8-174">Note that using the ENABLE_VIRTUAL_TERMINAL_PROCESSING mode can result in LVB grid and reverse video flags being set while this flag is still off if the attached application requests underlining or inverse video via <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">Console Virtual Terminal Sequences</a>.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="45ab8-175">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="45ab8-175">Return value</span></span>
------------

<span data-ttu-id="45ab8-176">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="45ab8-176">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="45ab8-177">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="45ab8-177">If the function fails, the return value is zero.</span></span> <span data-ttu-id="45ab8-178">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="45ab8-178">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="45ab8-179">Observaciones</span><span class="sxs-lookup"><span data-stu-id="45ab8-179">Remarks</span></span>
-------

<span data-ttu-id="45ab8-180">Una consola de está formada por un búfer de entrada y uno o más búferes de pantalla.</span><span class="sxs-lookup"><span data-stu-id="45ab8-180">A console consists of an input buffer and one or more screen buffers.</span></span> <span data-ttu-id="45ab8-181">El modo de un búfer de consola determina cómo se comporta la consola durante las operaciones de entrada o salida (e/s).</span><span class="sxs-lookup"><span data-stu-id="45ab8-181">The mode of a console buffer determines how the console behaves during input or output (I/O) operations.</span></span> <span data-ttu-id="45ab8-182">Un conjunto de constantes de marca se usa con los identificadores de entrada y otro conjunto se utiliza con los identificadores de búfer de pantalla (salida).</span><span class="sxs-lookup"><span data-stu-id="45ab8-182">One set of flag constants is used with input handles, and another set is used with screen buffer (output) handles.</span></span> <span data-ttu-id="45ab8-183">La configuración de los modos de salida de un búfer de pantalla no afecta a los modos de salida de otros búferes de pantalla.</span><span class="sxs-lookup"><span data-stu-id="45ab8-183">Setting the output modes of one screen buffer does not affect the output modes of other screen buffers.</span></span>

<span data-ttu-id="45ab8-184">Los modos de entrada **habilitar \_ \_ entrada de línea** y \*\*habilitar \_ eco \_ \*\* solo afectan a los procesos que usan [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) para leer desde el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="45ab8-184">The **ENABLE\_LINE\_INPUT** and **ENABLE\_ECHO\_INPUT** modes only affect processes that use [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) to read from the console's input buffer.</span></span> <span data-ttu-id="45ab8-185">De forma similar, el modo **habilitar \_ \_ entrada procesada** afecta principalmente a los usuarios **readfile** y **ReadConsole** , salvo que también determina si la entrada Ctrl + C se indica en el búfer de entrada (que será leída por la función [**ReadConsoleInput**](readconsoleinput.md) ) o se pasa a una función definida por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="45ab8-185">Similarly, the **ENABLE\_PROCESSED\_INPUT** mode primarily affects **ReadFile** and **ReadConsole** users, except that it also determines whether CTRL+C input is reported in the input buffer (to be read by the [**ReadConsoleInput**](readconsoleinput.md) function) or is passed to a function defined by the application.</span></span>

<span data-ttu-id="45ab8-186">Los **modos \_ habilitar \_ entrada de ventana** y **habilitar \_ \_ entrada del mouse** determinan si las interacciones del usuario que implican el cambio de tamaño de las ventanas y las acciones del mouse se registran en el búfer de entrada o se descartan.</span><span class="sxs-lookup"><span data-stu-id="45ab8-186">The **ENABLE\_WINDOW\_INPUT** and **ENABLE\_MOUSE\_INPUT** modes determine whether user interactions involving window resizing and mouse actions are reported in the input buffer or discarded.</span></span> <span data-ttu-id="45ab8-187">Estos eventos pueden ser leídos por [**ReadConsoleInput**](readconsoleinput.md), pero siempre se filtran por [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) y [**ReadConsole**](readconsole.md).</span><span class="sxs-lookup"><span data-stu-id="45ab8-187">These events can be read by [**ReadConsoleInput**](readconsoleinput.md), but they are always filtered by [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md).</span></span>

<span data-ttu-id="45ab8-188">Los modos de salida **habilitar \_ \_ salida procesada** y **habilitar \_ encapsulado \_ en \_ \_ EOL** solo afectan a los procesos que usan [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) y [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md).</span><span class="sxs-lookup"><span data-stu-id="45ab8-188">The **ENABLE\_PROCESSED\_OUTPUT** and **ENABLE\_WRAP\_AT\_EOL\_OUTPUT** modes only affect processes using [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md).</span></span>

<span data-ttu-id="45ab8-189">Para cambiar los modos de e/s de una consola, llame a la función [**SetConsoleMode**](setconsolemode.md) .</span><span class="sxs-lookup"><span data-stu-id="45ab8-189">To change a console's I/O modes, call [**SetConsoleMode**](setconsolemode.md) function.</span></span>

<a name="examples"></a><span data-ttu-id="45ab8-190">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="45ab8-190">Examples</span></span>
--------

<span data-ttu-id="45ab8-191">Para obtener un ejemplo, vea [leer eventos de búfer de entrada](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="45ab8-191">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="45ab8-192">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45ab8-192">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="45ab8-193">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="45ab8-193">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="45ab8-194">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="45ab8-194">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="45ab8-195">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="45ab8-195">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="45ab8-196">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="45ab8-196">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="45ab8-197">Encabezado</span><span class="sxs-lookup"><span data-stu-id="45ab8-197">Header</span></span></p></td>
<td><span data-ttu-id="45ab8-198">ConsoleApi. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="45ab8-198">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="45ab8-199">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="45ab8-199">Library</span></span></p></td>
<td><span data-ttu-id="45ab8-200">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="45ab8-200">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="45ab8-201">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="45ab8-201">DLL</span></span></p></td>
<td><span data-ttu-id="45ab8-202">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="45ab8-202">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="45ab8-203"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="45ab8-203"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="45ab8-204">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="45ab8-204">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="45ab8-205">Modos de consola</span><span class="sxs-lookup"><span data-stu-id="45ab8-205">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="45ab8-206">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="45ab8-206">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="45ab8-207">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="45ab8-207">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="45ab8-208">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="45ab8-208">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="45ab8-209">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="45ab8-209">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="45ab8-210">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="45ab8-210">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="45ab8-211">**Escritura**</span><span class="sxs-lookup"><span data-stu-id="45ab8-211">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




