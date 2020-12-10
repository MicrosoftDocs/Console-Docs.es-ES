---
title: Función SetConsoleMode
description: Establece el modo de entrada del búfer de entrada de una consola o el modo de salida de un búfer de pantalla de la consola.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/SetConsoleMode
- wincon/SetConsoleMode
- SetConsoleMode
MS-HAID:
- '\_win32\_setconsolemode'
- base.setconsolemode
- consoles.setconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 77508d58-8a7a-4c47-9ec5-dc61e5c4beac
topic_type:
- apiref
api_name:
- SetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 2af598f465be6e1a33f5a8f9a2c9abe98d6ed0d2
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420304"
---
# <a name="setconsolemode-function"></a><span data-ttu-id="272da-104">Función SetConsoleMode</span><span class="sxs-lookup"><span data-stu-id="272da-104">SetConsoleMode function</span></span>

<span data-ttu-id="272da-105">Establece el modo de entrada del búfer de entrada de una consola o el modo de salida de un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="272da-105">Sets the input mode of a console's input buffer or the output mode of a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="272da-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="272da-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

## <a name="parameters"></a><span data-ttu-id="272da-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="272da-107">Parameters</span></span>

<span data-ttu-id="272da-108">*hConsoleHandle* \[in\]</span><span class="sxs-lookup"><span data-stu-id="272da-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="272da-109">Identificador para el búfer de entrada de la consola o un búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="272da-109">A handle to the console input buffer or a console screen buffer.</span></span> <span data-ttu-id="272da-110">El identificador debe tener derecho de acceso de **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="272da-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="272da-111">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="272da-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="272da-112">*dwMode* \[in\]</span><span class="sxs-lookup"><span data-stu-id="272da-112">*dwMode* \[in\]</span></span>  
<span data-ttu-id="272da-113">Modo de entrada o de salida que se va a establecer.</span><span class="sxs-lookup"><span data-stu-id="272da-113">The input or output mode to be set.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a><span data-ttu-id="272da-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="272da-114">Return value</span></span>

<span data-ttu-id="272da-115">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="272da-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="272da-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="272da-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="272da-117">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="272da-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="272da-118">Comentarios</span><span class="sxs-lookup"><span data-stu-id="272da-118">Remarks</span></span>

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

<span data-ttu-id="272da-119">Para determinar el modo actual de un búfer de entrada o un búfer de pantalla de la consola, utilice la función [**GetConsoleMode**](getconsolemode.md).</span><span class="sxs-lookup"><span data-stu-id="272da-119">To determine the current mode of a console input buffer or a screen buffer, use the [**GetConsoleMode**](getconsolemode.md) function.</span></span>

## <a name="examples"></a><span data-ttu-id="272da-120">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="272da-120">Examples</span></span>

<span data-ttu-id="272da-121">Para un ejemplo, vea [Lectura de eventos de búfer de entrada](reading-input-buffer-events.md).</span><span class="sxs-lookup"><span data-stu-id="272da-121">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="272da-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="272da-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="272da-123">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="272da-123">Minimum supported client</span></span> | <span data-ttu-id="272da-124">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="272da-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="272da-125">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="272da-125">Minimum supported server</span></span> | <span data-ttu-id="272da-126">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="272da-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="272da-127">Encabezado</span><span class="sxs-lookup"><span data-stu-id="272da-127">Header</span></span> | <span data-ttu-id="272da-128">ConsoleApi.h (a través de WinCon.h, incluido Windows.h)</span><span class="sxs-lookup"><span data-stu-id="272da-128">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="272da-129">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="272da-129">Library</span></span> | <span data-ttu-id="272da-130">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="272da-130">Kernel32.lib</span></span> |
| <span data-ttu-id="272da-131">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="272da-131">DLL</span></span> | <span data-ttu-id="272da-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="272da-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="272da-133">Vea también</span><span class="sxs-lookup"><span data-stu-id="272da-133">See also</span></span>

[<span data-ttu-id="272da-134">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="272da-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="272da-135">Modos de consola</span><span class="sxs-lookup"><span data-stu-id="272da-135">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="272da-136">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="272da-136">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="272da-137">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="272da-137">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="272da-138">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="272da-138">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="272da-139">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="272da-139">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="272da-140">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="272da-140">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="272da-141">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="272da-141">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="272da-142">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="272da-142">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)
