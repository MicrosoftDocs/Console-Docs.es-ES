---
title: GetConsoleDisplayMode función)
description: Vea la información de referencia sobre la función GetConsoleDisplayMode, que recupera el modo de presentación de la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 74dc06cbb7ecadb0f86c4c4a992e3526be8ab74d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038063"
---
# <a name="getconsoledisplaymode-function"></a><span data-ttu-id="40bea-104">GetConsoleDisplayMode función)</span><span class="sxs-lookup"><span data-stu-id="40bea-104">GetConsoleDisplayMode function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="40bea-105">Recupera el modo de presentación de la consola actual.</span><span class="sxs-lookup"><span data-stu-id="40bea-105">Retrieves the display mode of the current console.</span></span>

## <a name="syntax"></a><span data-ttu-id="40bea-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="40bea-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

## <a name="parameters"></a><span data-ttu-id="40bea-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="40bea-107">Parameters</span></span>

<span data-ttu-id="40bea-108">*lpModeFlags* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="40bea-108">*lpModeFlags* \[out\]</span></span>  
<span data-ttu-id="40bea-109">Modo de presentación de la consola.</span><span class="sxs-lookup"><span data-stu-id="40bea-109">The display mode of the console.</span></span> <span data-ttu-id="40bea-110">Este parámetro puede ser uno o varios de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="40bea-110">This parameter can be one or more of the following values.</span></span>

| <span data-ttu-id="40bea-111">Valor</span><span class="sxs-lookup"><span data-stu-id="40bea-111">Value</span></span> | <span data-ttu-id="40bea-112">Significado</span><span class="sxs-lookup"><span data-stu-id="40bea-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="40bea-113">**CONSOLE_FULLSCREEN** 1</span><span class="sxs-lookup"><span data-stu-id="40bea-113">**CONSOLE_FULLSCREEN** 1</span></span> | <span data-ttu-id="40bea-114">Consola de pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="40bea-114">Full-screen console.</span></span> <span data-ttu-id="40bea-115">La consola está en este modo en cuanto se maximiza la ventana.</span><span class="sxs-lookup"><span data-stu-id="40bea-115">The console is in this mode as soon as the window is maximized.</span></span> <span data-ttu-id="40bea-116">En este momento, se puede producir un error en la transición al modo de pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="40bea-116">At this point, the transition to full-screen mode can still fail.</span></span> |
| <span data-ttu-id="40bea-117">**CONSOLE_FULLSCREEN_HARDWARE** 2</span><span class="sxs-lookup"><span data-stu-id="40bea-117">**CONSOLE_FULLSCREEN_HARDWARE** 2</span></span> | <span data-ttu-id="40bea-118">Consola de pantalla completa que se comunica directamente con el hardware de vídeo.</span><span class="sxs-lookup"><span data-stu-id="40bea-118">Full-screen console communicating directly with the video hardware.</span></span> <span data-ttu-id="40bea-119">Este modo se establece después de que la consola esté en modo de **CONSOLE_FULLSCREEN** para indicar que se ha completado la transición al modo de pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="40bea-119">This mode is set after the console is in **CONSOLE_FULLSCREEN** mode to indicate that the transition to full-screen mode has completed.</span></span> |

> [!NOTE]
> <span data-ttu-id="40bea-120">La transición al modo de hardware de vídeo de pantalla completa del 100% se quitó en Windows Vista con la replataforma de la pila de gráficos a [WDDM](https://docs.microsoft.com//windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model).</span><span class="sxs-lookup"><span data-stu-id="40bea-120">The transition to a 100% full screen video hardware mode was removed in Windows Vista with the replatforming of the graphics stack to [WDDM](https://docs.microsoft.com//windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model).</span></span> <span data-ttu-id="40bea-121">En versiones posteriores de Windows, el estado máximo resultante es **CONSOLE_FULLSCREEN** que representa una ventana frameless que aparece como pantalla completa, pero que no está en el control exclusivo del hardware.</span><span class="sxs-lookup"><span data-stu-id="40bea-121">On later versions of Windows, the maximum resulting state is **CONSOLE_FULLSCREEN** representing a frameless window that appears full screen but isn't in exclusive control of the hardware.</span></span>

## <a name="return-value"></a><span data-ttu-id="40bea-122">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="40bea-122">Return value</span></span>

<span data-ttu-id="40bea-123">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="40bea-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="40bea-124">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="40bea-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="40bea-125">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="40bea-125">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="40bea-126">Comentarios</span><span class="sxs-lookup"><span data-stu-id="40bea-126">Remarks</span></span>

<span data-ttu-id="40bea-127">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0500 o posterior.</span><span class="sxs-lookup"><span data-stu-id="40bea-127">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="40bea-128">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="40bea-128">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="40bea-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="40bea-129">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="40bea-130">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="40bea-130">Minimum supported client</span></span> | <span data-ttu-id="40bea-131">Solo aplicaciones de escritorio de Windows XP \[\]</span><span class="sxs-lookup"><span data-stu-id="40bea-131">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="40bea-132">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="40bea-132">Minimum supported server</span></span> | <span data-ttu-id="40bea-133">Solo aplicaciones de escritorio de Windows Server 2003 \[\]</span><span class="sxs-lookup"><span data-stu-id="40bea-133">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="40bea-134">Encabezado</span><span class="sxs-lookup"><span data-stu-id="40bea-134">Header</span></span> | <span data-ttu-id="40bea-135">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="40bea-135">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="40bea-136">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="40bea-136">Library</span></span> | <span data-ttu-id="40bea-137">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="40bea-137">Kernel32.lib</span></span> |
| <span data-ttu-id="40bea-138">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="40bea-138">DLL</span></span> | <span data-ttu-id="40bea-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="40bea-139">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="40bea-140">Consulte también</span><span class="sxs-lookup"><span data-stu-id="40bea-140">See also</span></span>

[<span data-ttu-id="40bea-141">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="40bea-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="40bea-142">Modos de consola</span><span class="sxs-lookup"><span data-stu-id="40bea-142">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="40bea-143">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="40bea-143">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)
