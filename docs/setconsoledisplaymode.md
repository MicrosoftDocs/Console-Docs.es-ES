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
ms.openlocfilehash: af61d897269311ccfa9db336083e898f6d75da80
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357705"
---
# <a name="setconsoledisplaymode-function"></a><span data-ttu-id="c24b4-104">SetConsoleDisplayMode función)</span><span class="sxs-lookup"><span data-stu-id="c24b4-104">SetConsoleDisplayMode function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="c24b4-105">Establece el modo de presentación del búfer de pantalla de la consola especificado.</span><span class="sxs-lookup"><span data-stu-id="c24b4-105">Sets the display mode of the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="c24b4-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c24b4-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

## <a name="parameters"></a><span data-ttu-id="c24b4-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="c24b4-107">Parameters</span></span>

<span data-ttu-id="c24b4-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c24b4-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="c24b4-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="c24b4-109">A handle to the console screen buffer.</span></span>

<span data-ttu-id="c24b4-110">*dwFlags* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="c24b4-110">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="c24b4-111">Modo de presentación de la consola.</span><span class="sxs-lookup"><span data-stu-id="c24b4-111">The display mode of the console.</span></span> <span data-ttu-id="c24b4-112">Este parámetro puede ser uno o varios de los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="c24b4-112">This parameter can be one or more of the following values.</span></span>

| <span data-ttu-id="c24b4-113">Valor</span><span class="sxs-lookup"><span data-stu-id="c24b4-113">Value</span></span> | <span data-ttu-id="c24b4-114">Significado</span><span class="sxs-lookup"><span data-stu-id="c24b4-114">Meaning</span></span> |
|-|-|
| <span data-ttu-id="c24b4-115">**CONSOLE_FULLSCREEN_MODE** 1</span><span class="sxs-lookup"><span data-stu-id="c24b4-115">**CONSOLE_FULLSCREEN_MODE** 1</span></span> | <span data-ttu-id="c24b4-116">El texto se muestra en el modo de pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="c24b4-116">Text is displayed in full-screen mode.</span></span> |
| <span data-ttu-id="c24b4-117">**CONSOLE_WINDOWED_MODE** 2</span><span class="sxs-lookup"><span data-stu-id="c24b4-117">**CONSOLE_WINDOWED_MODE** 2</span></span> | <span data-ttu-id="c24b4-118">El texto se muestra en una ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="c24b4-118">Text is displayed in a console window.</span></span> |

<span data-ttu-id="c24b4-119">*lpNewScreenBufferDimensions* \[ out, opcional\]</span><span class="sxs-lookup"><span data-stu-id="c24b4-119">*lpNewScreenBufferDimensions* \[out, optional\]</span></span>  
<span data-ttu-id="c24b4-120">Puntero a una estructura de [**coordenadas**](coord-str.md) que recibe las nuevas dimensiones del búfer de pantalla, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="c24b4-120">A pointer to a [**COORD**](coord-str.md) structure that receives the new dimensions of the screen buffer, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="c24b4-121">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="c24b4-121">Return value</span></span>

<span data-ttu-id="c24b4-122">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="c24b4-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c24b4-123">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="c24b4-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c24b4-124">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="c24b4-124">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="c24b4-125">Comentarios</span><span class="sxs-lookup"><span data-stu-id="c24b4-125">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="c24b4-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c24b4-126">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c24b4-127">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="c24b4-127">Minimum supported client</span></span> | <span data-ttu-id="c24b4-128">Solo aplicaciones de escritorio de Windows XP \[\]</span><span class="sxs-lookup"><span data-stu-id="c24b4-128">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="c24b4-129">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="c24b4-129">Minimum supported server</span></span> | <span data-ttu-id="c24b4-130">Solo aplicaciones de escritorio de Windows Server 2003 \[\]</span><span class="sxs-lookup"><span data-stu-id="c24b4-130">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="c24b4-131">Encabezado</span><span class="sxs-lookup"><span data-stu-id="c24b4-131">Header</span></span> | <span data-ttu-id="c24b4-132">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c24b4-132">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c24b4-133">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="c24b4-133">Library</span></span> | <span data-ttu-id="c24b4-134">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="c24b4-134">Kernel32.lib</span></span> |
| <span data-ttu-id="c24b4-135">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="c24b4-135">DLL</span></span> | <span data-ttu-id="c24b4-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c24b4-136">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="c24b4-137">Vea también</span><span class="sxs-lookup"><span data-stu-id="c24b4-137">See also</span></span>

[<span data-ttu-id="c24b4-138">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="c24b4-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c24b4-139">Modos de consola</span><span class="sxs-lookup"><span data-stu-id="c24b4-139">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="c24b4-140">**GetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="c24b4-140">**GetConsoleDisplayMode**</span></span>](getconsoledisplaymode.md)