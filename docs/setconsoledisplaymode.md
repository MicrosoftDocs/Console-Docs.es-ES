---
title: SetConsoleDisplayMode función)
description: Vea la información de referencia sobre la función SetConsoleDisplayMode, que establece el modo de presentación del búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- base.setconsoledisplaymode
- consoles.setconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744
topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 52d7e50d7ced5615cb296c0590876e4604057e42
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039393"
---
# <a name="setconsoledisplaymode-function"></a><span data-ttu-id="8d968-104">SetConsoleDisplayMode función)</span><span class="sxs-lookup"><span data-stu-id="8d968-104">SetConsoleDisplayMode function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="8d968-105">Establece el modo de presentación del búfer de pantalla de la consola especificado.</span><span class="sxs-lookup"><span data-stu-id="8d968-105">Sets the display mode of the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="8d968-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8d968-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

## <a name="parameters"></a><span data-ttu-id="8d968-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="8d968-107">Parameters</span></span>

<span data-ttu-id="8d968-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="8d968-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="8d968-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="8d968-109">A handle to the console screen buffer.</span></span>

<span data-ttu-id="8d968-110">*dwFlags* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="8d968-110">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="8d968-111">Modo de presentación de la consola.</span><span class="sxs-lookup"><span data-stu-id="8d968-111">The display mode of the console.</span></span> <span data-ttu-id="8d968-112">Este parámetro puede ser uno o varios de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="8d968-112">This parameter can be one or more of the following values.</span></span>

| <span data-ttu-id="8d968-113">Valor</span><span class="sxs-lookup"><span data-stu-id="8d968-113">Value</span></span> | <span data-ttu-id="8d968-114">Significado</span><span class="sxs-lookup"><span data-stu-id="8d968-114">Meaning</span></span> |
|-|-|
| <span data-ttu-id="8d968-115">**CONSOLE_FULLSCREEN_MODE** 1</span><span class="sxs-lookup"><span data-stu-id="8d968-115">**CONSOLE_FULLSCREEN_MODE** 1</span></span> | <span data-ttu-id="8d968-116">El texto se muestra en el modo de pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="8d968-116">Text is displayed in full-screen mode.</span></span> |
| <span data-ttu-id="8d968-117">**CONSOLE_WINDOWED_MODE** 2</span><span class="sxs-lookup"><span data-stu-id="8d968-117">**CONSOLE_WINDOWED_MODE** 2</span></span> | <span data-ttu-id="8d968-118">El texto se muestra en una ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="8d968-118">Text is displayed in a console window.</span></span> |

<span data-ttu-id="8d968-119">*lpNewScreenBufferDimensions* \[ out, opcional\]</span><span class="sxs-lookup"><span data-stu-id="8d968-119">*lpNewScreenBufferDimensions* \[out, optional\]</span></span>  
<span data-ttu-id="8d968-120">Puntero a una estructura de [**coordenadas**](coord-str.md) que recibe las nuevas dimensiones del búfer de pantalla, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="8d968-120">A pointer to a [**COORD**](coord-str.md) structure that receives the new dimensions of the screen buffer, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="8d968-121">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="8d968-121">Return value</span></span>

<span data-ttu-id="8d968-122">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="8d968-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="8d968-123">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="8d968-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="8d968-124">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="8d968-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="8d968-125">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8d968-125">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="8d968-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8d968-126">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="8d968-127">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="8d968-127">Minimum supported client</span></span> | <span data-ttu-id="8d968-128">Solo aplicaciones de escritorio de Windows XP \[\]</span><span class="sxs-lookup"><span data-stu-id="8d968-128">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="8d968-129">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="8d968-129">Minimum supported server</span></span> | <span data-ttu-id="8d968-130">Solo aplicaciones de escritorio de Windows Server 2003 \[\]</span><span class="sxs-lookup"><span data-stu-id="8d968-130">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="8d968-131">Encabezado</span><span class="sxs-lookup"><span data-stu-id="8d968-131">Header</span></span> | <span data-ttu-id="8d968-132">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="8d968-132">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="8d968-133">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="8d968-133">Library</span></span> | <span data-ttu-id="8d968-134">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="8d968-134">Kernel32.lib</span></span> |
| <span data-ttu-id="8d968-135">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="8d968-135">DLL</span></span> | <span data-ttu-id="8d968-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="8d968-136">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="8d968-137">Consulte también</span><span class="sxs-lookup"><span data-stu-id="8d968-137">See also</span></span>

[<span data-ttu-id="8d968-138">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="8d968-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="8d968-139">Modos de consola</span><span class="sxs-lookup"><span data-stu-id="8d968-139">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="8d968-140">**GetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="8d968-140">**GetConsoleDisplayMode**</span></span>](getconsoledisplaymode.md)
