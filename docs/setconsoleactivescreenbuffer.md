---
title: SetConsoleActiveScreenBuffer función)
description: Establece el búfer de pantalla especificado para que sea el búfer de pantalla de la consola que se muestra actualmente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleActiveScreenBuffer
- wincon/SetConsoleActiveScreenBuffer
- SetConsoleActiveScreenBuffer
MS-HAID:
- '\_win32\_setconsoleactivescreenbuffer'
- base.setconsoleactivescreenbuffer
- consoles.setconsoleactivescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c026cb94-c8ec-44ee-b432-3870ae3006c2
topic_type:
- apiref
api_name:
- SetConsoleActiveScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 7eb27a383a0bdbfc985188eb477ab9a878f33274
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039443"
---
# <a name="setconsoleactivescreenbuffer-function"></a><span data-ttu-id="27f1a-104">SetConsoleActiveScreenBuffer función)</span><span class="sxs-lookup"><span data-stu-id="27f1a-104">SetConsoleActiveScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="27f1a-105">Establece el búfer de pantalla especificado para que sea el búfer de pantalla de la consola que se muestra actualmente.</span><span class="sxs-lookup"><span data-stu-id="27f1a-105">Sets the specified screen buffer to be the currently displayed console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="27f1a-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="27f1a-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleActiveScreenBuffer(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a><span data-ttu-id="27f1a-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27f1a-107">Parameters</span></span>

<span data-ttu-id="27f1a-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="27f1a-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="27f1a-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="27f1a-109">A handle to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="27f1a-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="27f1a-110">Return value</span></span>

<span data-ttu-id="27f1a-111">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="27f1a-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="27f1a-112">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="27f1a-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="27f1a-113">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="27f1a-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="27f1a-114">Comentarios</span><span class="sxs-lookup"><span data-stu-id="27f1a-114">Remarks</span></span>

<span data-ttu-id="27f1a-115">Una consola puede tener varios búferes de pantalla.</span><span class="sxs-lookup"><span data-stu-id="27f1a-115">A console can have multiple screen buffers.</span></span> <span data-ttu-id="27f1a-116">**SetConsoleActiveScreenBuffer** determina cuál de ellas se muestra.</span><span class="sxs-lookup"><span data-stu-id="27f1a-116">**SetConsoleActiveScreenBuffer** determines which one is displayed.</span></span> <span data-ttu-id="27f1a-117">Puede escribir en un búfer de pantalla inactivo y, a continuación, usar **SetConsoleActiveScreenBuffer** para mostrar el contenido del búfer.</span><span class="sxs-lookup"><span data-stu-id="27f1a-117">You can write to an inactive screen buffer and then use **SetConsoleActiveScreenBuffer** to display the buffer's contents.</span></span>

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a><span data-ttu-id="27f1a-118">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="27f1a-118">Examples</span></span>

<span data-ttu-id="27f1a-119">Para obtener un ejemplo, vea [lectura y escritura de bloques de caracteres y atributos](reading-and-writing-blocks-of-characters-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="27f1a-119">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="27f1a-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27f1a-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="27f1a-121">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="27f1a-121">Minimum supported client</span></span> | <span data-ttu-id="27f1a-122">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="27f1a-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="27f1a-123">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="27f1a-123">Minimum supported server</span></span> | <span data-ttu-id="27f1a-124">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="27f1a-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="27f1a-125">Encabezado</span><span class="sxs-lookup"><span data-stu-id="27f1a-125">Header</span></span> | <span data-ttu-id="27f1a-126">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="27f1a-126">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="27f1a-127">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="27f1a-127">Library</span></span> | <span data-ttu-id="27f1a-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="27f1a-128">Kernel32.lib</span></span> |
| <span data-ttu-id="27f1a-129">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="27f1a-129">DLL</span></span> | <span data-ttu-id="27f1a-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="27f1a-130">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="27f1a-131">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27f1a-131">See also</span></span>

[<span data-ttu-id="27f1a-132">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="27f1a-132">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="27f1a-133">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="27f1a-133">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="27f1a-134">**CreateConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="27f1a-134">**CreateConsoleScreenBuffer**</span></span>](createconsolescreenbuffer.md)
