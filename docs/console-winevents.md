---
title: WinEvents de consola
description: Las constantes de eventos siguientes se usan en el parámetro Event de la función de devolución de llamada WinEventProc. Para obtener más información, vea WinEvents.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- winuser/EVENT_CONSOLE_CARET
- winuser/EVENT_CONSOLE_END_APPLICATION
- winuser/EVENT_CONSOLE_LAYOUT
- winuser/EVENT_CONSOLE_START_APPLICATION
- winuser/EVENT_CONSOLE_UPDATE_REGION
- winuser/EVENT_CONSOLE_UPDATE_SCROLL
- winuser/EVENT_CONSOLE_UPDATE_SIMPLE
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
MS-HAID:
- '\_win32\_console\_winevents'
- base.console\_winevents
- consoles.console\_winevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b7078b2d-5508-4e42-bac2-34b70f1856e2
topic_type:
- apiref
api_name:
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
api_location:
- Winuser.h
api_type:
- HeaderDef
ms.openlocfilehash: ab58df01b3fb29e6efea3ecd0aab145fe2f298c2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060780"
---
# <a name="console-winevents"></a><span data-ttu-id="55e76-105">WinEvents de consola</span><span class="sxs-lookup"><span data-stu-id="55e76-105">Console WinEvents</span></span>


<span data-ttu-id="55e76-106">Las constantes de eventos siguientes se usan en el parámetro *Event* de la función de devolución de llamada [*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) .</span><span class="sxs-lookup"><span data-stu-id="55e76-106">The following event constants are used in the *event* parameter of the [*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) callback function.</span></span> <span data-ttu-id="55e76-107">Para obtener más información, vea [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span><span class="sxs-lookup"><span data-stu-id="55e76-107">For more information, see [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="55e76-108">Constante o valor</span><span class="sxs-lookup"><span data-stu-id="55e76-108">Constant/value</span></span></th>
<th><span data-ttu-id="55e76-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="55e76-109">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="55e76-110"><span id="EVENT_CONSOLE_CARET"></span><span id="event_console_caret"></span>
<strong>EVENT_CONSOLE_CARET</strong> 0x4001</span><span class="sxs-lookup"><span data-stu-id="55e76-110"><span id="EVENT_CONSOLE_CARET"></span><span id="event_console_caret"></span>
<strong>EVENT_CONSOLE_CARET</strong> 0x4001</span></span></td>
<td><p><span data-ttu-id="55e76-111">Se ha cambiado el símbolo de intercalación de la consola.</span><span class="sxs-lookup"><span data-stu-id="55e76-111">The console caret has moved.</span></span> <span data-ttu-id="55e76-112">El parámetro <em>idObject</em> es uno o varios de los siguientes valores: <strong>CONSOLE_CARET_SELECTION</strong> o <strong>CONSOLE_CARET_VISIBLE</strong>.</span><span class="sxs-lookup"><span data-stu-id="55e76-112">The <em>idObject</em> parameter is one or more of the following values: <strong>CONSOLE_CARET_SELECTION</strong> or <strong>CONSOLE_CARET_VISIBLE</strong>.</span></span></p>
<p><span data-ttu-id="55e76-113">El parámetro <em>idChild</em> es una estructura de <strong><a href="https://docs.microsoft.com/windows/console/coord-str">coordenadas</a></strong> que especifica la posición actual del cursor.</span><span class="sxs-lookup"><span data-stu-id="55e76-113">The <em>idChild</em> parameter is a <strong><a href="https://docs.microsoft.com/windows/console/coord-str">COORD</a></strong> structure that specifies the cursor's current position.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="55e76-114"><span id="EVENT_CONSOLE_END_APPLICATION"></span><span id="event_console_end_application"></span>
<strong>EVENT_CONSOLE_END_APPLICATION</strong> 0x4007</span><span class="sxs-lookup"><span data-stu-id="55e76-114"><span id="EVENT_CONSOLE_END_APPLICATION"></span><span id="event_console_end_application"></span>
<strong>EVENT_CONSOLE_END_APPLICATION</strong> 0x4007</span></span></td>
<td><p><span data-ttu-id="55e76-115">Se ha salido de un proceso de consola.</span><span class="sxs-lookup"><span data-stu-id="55e76-115">A console process has exited.</span></span> <span data-ttu-id="55e76-116">El parámetro <em>idObject</em> contiene el identificador de proceso del proceso terminado.</span><span class="sxs-lookup"><span data-stu-id="55e76-116">The <em>idObject</em> parameter contains the process identifier of the terminated process.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="55e76-117"><span id="EVENT_CONSOLE_LAYOUT"></span><span id="event_console_layout"></span>
<strong>EVENT_CONSOLE_LAYOUT</strong> 0x4005</span><span class="sxs-lookup"><span data-stu-id="55e76-117"><span id="EVENT_CONSOLE_LAYOUT"></span><span id="event_console_layout"></span>
<strong>EVENT_CONSOLE_LAYOUT</strong> 0x4005</span></span></td>
<td><p><span data-ttu-id="55e76-118">El diseño de la consola ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="55e76-118">The console layout has changed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="55e76-119"><span id="EVENT_CONSOLE_START_APPLICATION"></span><span id="event_console_start_application"></span>
<strong>EVENT_CONSOLE_START_APPLICATION</strong> 0x4006</span><span class="sxs-lookup"><span data-stu-id="55e76-119"><span id="EVENT_CONSOLE_START_APPLICATION"></span><span id="event_console_start_application"></span>
<strong>EVENT_CONSOLE_START_APPLICATION</strong> 0x4006</span></span></td>
<td><p><span data-ttu-id="55e76-120">Se ha iniciado un nuevo proceso de consola.</span><span class="sxs-lookup"><span data-stu-id="55e76-120">A new console process has started.</span></span> <span data-ttu-id="55e76-121">El parámetro <em>idObject</em> contiene el identificador de proceso del proceso recién creado.</span><span class="sxs-lookup"><span data-stu-id="55e76-121">The <em>idObject</em> parameter contains the process identifier of the newly created process.</span></span> <span data-ttu-id="55e76-122">Si la aplicación es una aplicación de 16 bits, el parámetro <em>idChild</em> es <strong>CONSOLE_APPLICATION_16BIT</strong> y <em>idObject</em> es el identificador de proceso de la sesión de NTVDM asociada a la consola.</span><span class="sxs-lookup"><span data-stu-id="55e76-122">If the application is a 16-bit application, the <em>idChild</em> parameter is <strong>CONSOLE_APPLICATION_16BIT</strong> and <em>idObject</em> is the process identifier of the NTVDM session associated with the console.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="55e76-123"><span id="EVENT_CONSOLE_UPDATE_REGION"></span><span id="event_console_update_region"></span>
<strong>EVENT_CONSOLE_UPDATE_REGION</strong> 0x4002</span><span class="sxs-lookup"><span data-stu-id="55e76-123"><span id="EVENT_CONSOLE_UPDATE_REGION"></span><span id="event_console_update_region"></span>
<strong>EVENT_CONSOLE_UPDATE_REGION</strong> 0x4002</span></span></td>
<td><p><span data-ttu-id="55e76-124">Ha cambiado más de un carácter.</span><span class="sxs-lookup"><span data-stu-id="55e76-124">More than one character has changed.</span></span> <span data-ttu-id="55e76-125">El parámetro <em>idObject</em> es una estructura de <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>coordenadas</strong></a> que especifica el inicio de la región modificada.</span><span class="sxs-lookup"><span data-stu-id="55e76-125">The <em>idObject</em> parameter is a <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>COORD</strong></a> structure that specifies the start of the changed region.</span></span> <span data-ttu-id="55e76-126">El parámetro <em>idChild</em> es una estructura de <strong>coordenadas</strong> que especifica el final de la región modificada.</span><span class="sxs-lookup"><span data-stu-id="55e76-126">The <em>idChild</em> parameter is a <strong>COORD</strong> structure that specifies the end of the changed region.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="55e76-127"><span id="EVENT_CONSOLE_UPDATE_SCROLL"></span><span id="event_console_update_scroll"></span>
<strong>EVENT_CONSOLE_UPDATE_SCROLL</strong> 0x4004</span><span class="sxs-lookup"><span data-stu-id="55e76-127"><span id="EVENT_CONSOLE_UPDATE_SCROLL"></span><span id="event_console_update_scroll"></span>
<strong>EVENT_CONSOLE_UPDATE_SCROLL</strong> 0x4004</span></span></td>
<td><p><span data-ttu-id="55e76-128">La consola se ha desplazado.</span><span class="sxs-lookup"><span data-stu-id="55e76-128">The console has scrolled.</span></span> <span data-ttu-id="55e76-129">El parámetro <em>idObject</em> es la distancia horizontal que se ha desplazado la consola.</span><span class="sxs-lookup"><span data-stu-id="55e76-129">The <em>idObject</em> parameter is the horizontal distance the console has scrolled.</span></span> <span data-ttu-id="55e76-130">El parámetro <em>idChild</em> es la distancia vertical que se ha desplazado la consola.</span><span class="sxs-lookup"><span data-stu-id="55e76-130">The <em>idChild</em> parameter is the vertical distance the console has scrolled.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="55e76-131"><span id="EVENT_CONSOLE_UPDATE_SIMPLE"></span><span id="event_console_update_simple"></span>
<strong>EVENT_CONSOLE_UPDATE_SIMPLE</strong> 0x4003</span><span class="sxs-lookup"><span data-stu-id="55e76-131"><span id="EVENT_CONSOLE_UPDATE_SIMPLE"></span><span id="event_console_update_simple"></span>
<strong>EVENT_CONSOLE_UPDATE_SIMPLE</strong> 0x4003</span></span></td>
<td><p><span data-ttu-id="55e76-132">Ha cambiado un solo carácter.</span><span class="sxs-lookup"><span data-stu-id="55e76-132">A single character has changed.</span></span> <span data-ttu-id="55e76-133">El parámetro <em>idObject</em> es una estructura de <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>coordenadas</strong></a> que especifica el carácter que ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="55e76-133">The <em>idObject</em> parameter is a <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>COORD</strong></a> structure that specifies the character that has changed.</span></span> <span data-ttu-id="55e76-134">El parámetro <em>idChild</em> especifica el carácter de la palabra baja y los <a href="console-screen-buffers.md#_win32_font_attributes" data-raw-source="[character attributes](console-screen-buffers.md#_win32_font_attributes)">atributos de carácter</a> de la palabra alta.</span><span class="sxs-lookup"><span data-stu-id="55e76-134">The <em>idChild</em> parameter specifies the character in the low word and the <a href="console-screen-buffers.md#_win32_font_attributes" data-raw-source="[character attributes](console-screen-buffers.md#_win32_font_attributes)">character attributes</a> in the high word.</span></span></p></td>
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

<a name="requirements"></a><span data-ttu-id="55e76-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="55e76-135">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="55e76-136">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="55e76-136">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="55e76-137">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="55e76-137">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="55e76-138">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="55e76-138">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="55e76-139">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="55e76-139">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="55e76-140">Encabezado</span><span class="sxs-lookup"><span data-stu-id="55e76-140">Header</span></span></p></td>
<td><span data-ttu-id="55e76-141">Winuser. h</span><span class="sxs-lookup"><span data-stu-id="55e76-141">Winuser.h</span></span></td>
</tr>
</tbody>
</table>
