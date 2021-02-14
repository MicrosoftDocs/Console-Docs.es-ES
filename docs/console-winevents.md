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
ms.openlocfilehash: 2cd48537ef79f09024a55b32a98e2aa85fe76f62
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358055"
---
# <a name="console-winevents"></a><span data-ttu-id="be96c-105">WinEvents de consola</span><span class="sxs-lookup"><span data-stu-id="be96c-105">Console WinEvents</span></span>

> [!IMPORTANT]
> <span data-ttu-id="be96c-106">WinEvents forman parte de **[Microsoft Active Accessibility](/windows/win32/winauto/microsoft-active-accessibility)** Framework heredado.</span><span class="sxs-lookup"><span data-stu-id="be96c-106">WinEvents are part of the legacy **[Microsoft Active Accessibility](/windows/win32/winauto/microsoft-active-accessibility)** framework.</span></span> <span data-ttu-id="be96c-107">No se recomienda el desarrollo mediante estos eventos en favor del marco de **[automatización](/windows/win32/winauto/entry-uiauto-win32)** de la interfaz de usuario de Microsoft, que proporciona un conjunto de interfaces más sólido y completo para que las aplicaciones de accesibilidad y automatización interactúen con la consola.</span><span class="sxs-lookup"><span data-stu-id="be96c-107">Development using these events is strongly discouraged in favor of the **[Microsoft UI Automation](/windows/win32/winauto/entry-uiauto-win32)** framework which provides a more robust and comprehensive suite of interfaces for accessibility and automation applications to interact with the console.</span></span> 

> [!WARNING]
> <span data-ttu-id="be96c-108">El registro de estos eventos es una actividad global y afecta significativamente al rendimiento de todas las aplicaciones de línea de comandos que se ejecutan en un sistema al mismo tiempo, incluidos los servicios y las utilidades en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="be96c-108">Registering for these events is a global activity and will significantly impact performance of all command-line applications running on a system at the same time, including services and background utilities.</span></span> <span data-ttu-id="be96c-109">El marco de automatización de la **interfaz de usuario de Microsoft** es específico de la sesión de consola y supera esta limitación.</span><span class="sxs-lookup"><span data-stu-id="be96c-109">The **Microsoft UI Automation** framework is console session specific and overcomes this limitation.</span></span>

<span data-ttu-id="be96c-110">Las constantes de eventos siguientes se usan en el parámetro *Event* de la función de devolución de llamada [*WinEventProc*](/windows/win32/api/winuser/nc-winuser-wineventproc) .</span><span class="sxs-lookup"><span data-stu-id="be96c-110">The following event constants are used in the *event* parameter of the [*WinEventProc*](/windows/win32/api/winuser/nc-winuser-wineventproc) callback function.</span></span> <span data-ttu-id="be96c-111">Para obtener más información, vea [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span><span class="sxs-lookup"><span data-stu-id="be96c-111">For more information, see [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span></span>

| <span data-ttu-id="be96c-112">Constante o valor</span><span class="sxs-lookup"><span data-stu-id="be96c-112">Constant/value</span></span> | <span data-ttu-id="be96c-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="be96c-113">Description</span></span> |
|-|-|
| <span data-ttu-id="be96c-114">**EVENT_CONSOLE_CARET** 0x4001</span><span class="sxs-lookup"><span data-stu-id="be96c-114">**EVENT_CONSOLE_CARET** 0x4001</span></span> | <span data-ttu-id="be96c-115">Se ha cambiado el símbolo de intercalación de la consola.</span><span class="sxs-lookup"><span data-stu-id="be96c-115">The console caret has moved.</span></span> <span data-ttu-id="be96c-116">El parámetro *idObject* es uno o varios de los siguientes valores: **CONSOLE_CARET_SELECTION** o **CONSOLE_CARET_VISIBLE**.</span><span class="sxs-lookup"><span data-stu-id="be96c-116">The *idObject* parameter is one or more of the following values: **CONSOLE_CARET_SELECTION** or **CONSOLE_CARET_VISIBLE**.</span></span> <span data-ttu-id="be96c-117">El parámetro *idChild* es una estructura de **[coordenadas](coord-str.md)** que especifica la posición actual del cursor.</span><span class="sxs-lookup"><span data-stu-id="be96c-117">The *idChild* parameter is a **[COORD](coord-str.md)** structure that specifies the cursor's current position.</span></span> |
| <span data-ttu-id="be96c-118">**EVENT_CONSOLE_END_APPLICATION** 0x4007</span><span class="sxs-lookup"><span data-stu-id="be96c-118">**EVENT_CONSOLE_END_APPLICATION** 0x4007</span></span> | <span data-ttu-id="be96c-119">Se ha salido de un proceso de consola.</span><span class="sxs-lookup"><span data-stu-id="be96c-119">A console process has exited.</span></span> <span data-ttu-id="be96c-120">El parámetro *idObject* contiene el identificador de proceso del proceso terminado.</span><span class="sxs-lookup"><span data-stu-id="be96c-120">The *idObject* parameter contains the process identifier of the terminated process.</span></span> |
| <span data-ttu-id="be96c-121">**EVENT_CONSOLE_LAYOUT** 0x4005</span><span class="sxs-lookup"><span data-stu-id="be96c-121">**EVENT_CONSOLE_LAYOUT** 0x4005</span></span> | <span data-ttu-id="be96c-122">El diseño de la consola ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="be96c-122">The console layout has changed.</span></span> |
| <span data-ttu-id="be96c-123">**EVENT_CONSOLE_START_APPLICATION** 0x4006</span><span class="sxs-lookup"><span data-stu-id="be96c-123">**EVENT_CONSOLE_START_APPLICATION** 0x4006</span></span> | <span data-ttu-id="be96c-124">Se ha iniciado un nuevo proceso de consola.</span><span class="sxs-lookup"><span data-stu-id="be96c-124">A new console process has started.</span></span> <span data-ttu-id="be96c-125">El parámetro *idObject* contiene el identificador de proceso del proceso recién creado.</span><span class="sxs-lookup"><span data-stu-id="be96c-125">The *idObject* parameter contains the process identifier of the newly created process.</span></span> <span data-ttu-id="be96c-126">Si la aplicación es una aplicación de 16 bits, el parámetro *idChild* es **CONSOLE_APPLICATION_16BIT** y *idObject* es el identificador de proceso de la sesión de NTVDM asociada a la consola.</span><span class="sxs-lookup"><span data-stu-id="be96c-126">If the application is a 16-bit application, the *idChild* parameter is **CONSOLE_APPLICATION_16BIT** and *idObject* is the process identifier of the NTVDM session associated with the console.</span></span> |
|<span data-ttu-id="be96c-127">**EVENT_CONSOLE_UPDATE_REGION** 0x4002</span><span class="sxs-lookup"><span data-stu-id="be96c-127">**EVENT_CONSOLE_UPDATE_REGION** 0x4002</span></span> | <span data-ttu-id="be96c-128">Ha cambiado más de un carácter.</span><span class="sxs-lookup"><span data-stu-id="be96c-128">More than one character has changed.</span></span> <span data-ttu-id="be96c-129">El parámetro  *idObject* es una estructura de **[coordenadas](coord-str.md)** que especifica el inicio de la región modificada.</span><span class="sxs-lookup"><span data-stu-id="be96c-129">The  *idObject* parameter is a **[COORD](coord-str.md)** structure that specifies the start of the changed region.</span></span> <span data-ttu-id="be96c-130">El parámetro *idChild* es una estructura de **coordenadas** que especifica el final de la región modificada.</span><span class="sxs-lookup"><span data-stu-id="be96c-130">The *idChild* parameter is a **COORD** structure that specifies the end of the changed region.</span></span> |
|<span data-ttu-id="be96c-131">**EVENT_CONSOLE_UPDATE_SCROLL** 0x4004</span><span class="sxs-lookup"><span data-stu-id="be96c-131">**EVENT_CONSOLE_UPDATE_SCROLL** 0x4004</span></span> | <span data-ttu-id="be96c-132">La consola se ha desplazado.</span><span class="sxs-lookup"><span data-stu-id="be96c-132">The console has scrolled.</span></span> <span data-ttu-id="be96c-133">El parámetro *idObject* es la distancia horizontal que se ha desplazado la consola.</span><span class="sxs-lookup"><span data-stu-id="be96c-133">The *idObject* parameter is the horizontal distance the console has scrolled.</span></span> <span data-ttu-id="be96c-134">El parámetro *idChild* es la distancia vertical que se ha desplazado la consola.</span><span class="sxs-lookup"><span data-stu-id="be96c-134">The *idChild* parameter is the vertical distance the console has scrolled.</span></span> |
|<span data-ttu-id="be96c-135">**EVENT_CONSOLE_UPDATE_SIMPLE** 0x4003</span><span class="sxs-lookup"><span data-stu-id="be96c-135">**EVENT_CONSOLE_UPDATE_SIMPLE** 0x4003</span></span> | <span data-ttu-id="be96c-136">Ha cambiado un solo carácter.</span><span class="sxs-lookup"><span data-stu-id="be96c-136">A single character has changed.</span></span> <span data-ttu-id="be96c-137">El parámetro *idObject* es una estructura de **[coordenadas](coord-str.md)** que especifica el carácter que ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="be96c-137">The *idObject* parameter is a **[COORD](coord-str.md)** structure that specifies the character that has changed.</span></span> <span data-ttu-id="be96c-138">El parámetro *idChild* especifica el carácter de la palabra baja y los **[atributos de carácter](console-screen-buffers.md#character-attributes)** de la palabra alta.</span><span class="sxs-lookup"><span data-stu-id="be96c-138">The *idChild* parameter specifies the character in the low word and the **[character attributes](console-screen-buffers.md#character-attributes)** in the high word.</span></span> |

## <a name="requirements"></a><span data-ttu-id="be96c-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="be96c-139">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="be96c-140">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="be96c-140">Minimum supported client</span></span> | <span data-ttu-id="be96c-141">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="be96c-141">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="be96c-142">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="be96c-142">Minimum supported server</span></span> | <span data-ttu-id="be96c-143">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="be96c-143">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="be96c-144">Encabezado</span><span class="sxs-lookup"><span data-stu-id="be96c-144">Header</span></span> | <span data-ttu-id="be96c-145">Winuser. h</span><span class="sxs-lookup"><span data-stu-id="be96c-145">Winuser.h</span></span> |