---
title: ResizePseudoConsole función)
description: Vea la información de referencia sobre la función ResizePseudoConsole, que cambia el tamaño de los búferes internos para un pseudoconsole al tamaño especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola, conpty, pseudoconsole
f1_keywords:
- consoleapi/ResizePseudoConsole
- ResizePseudoConsole
topic_type:
- apiref
api_name:
- ResizePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 0d5a4ff954c8ebea688573f23d3981ee9c5d7d2a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037543"
---
# <a name="resizepseudoconsole-function"></a><span data-ttu-id="40ee6-104">ResizePseudoConsole función)</span><span class="sxs-lookup"><span data-stu-id="40ee6-104">ResizePseudoConsole function</span></span>

<span data-ttu-id="40ee6-105">Cambia el tamaño de los búferes internos de un pseudoconsole al tamaño especificado.</span><span class="sxs-lookup"><span data-stu-id="40ee6-105">Resizes the internal buffers for a pseudoconsole to the given size.</span></span>

## <a name="syntax"></a><span data-ttu-id="40ee6-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="40ee6-106">Syntax</span></span>

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

## <a name="parameters"></a><span data-ttu-id="40ee6-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="40ee6-107">Parameters</span></span>

<span data-ttu-id="40ee6-108">*hPC* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="40ee6-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="40ee6-109">Identificador de un pseudoconsole activo tal y como lo abre [CreatePseudoConsole](createpseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="40ee6-109">A handle to an active pseudoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

<span data-ttu-id="40ee6-110">*tamaño* \[ de de\]</span><span class="sxs-lookup"><span data-stu-id="40ee6-110">*size* \[in\]</span></span>  
<span data-ttu-id="40ee6-111">Dimensiones de la ventana o búfer en el recuento de caracteres que se usarán para el búfer interno de este pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="40ee6-111">The dimensions of the window/buffer in count of characters that will be used for the internal buffer of this pseudoconsole.</span></span>

## <a name="return-value"></a><span data-ttu-id="40ee6-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="40ee6-112">Return value</span></span>

<span data-ttu-id="40ee6-113">Tipo: **HRESULT**</span><span class="sxs-lookup"><span data-stu-id="40ee6-113">Type: **HRESULT**</span></span>

<span data-ttu-id="40ee6-114">Si este método se ejecuta correctamente, devuelve **S_OK** .</span><span class="sxs-lookup"><span data-stu-id="40ee6-114">If this method succeeds, it returns **S_OK** .</span></span> <span data-ttu-id="40ee6-115">De lo contrario, devuelve un código de error **HRESULT** .</span><span class="sxs-lookup"><span data-stu-id="40ee6-115">Otherwise, it returns an **HRESULT** error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="40ee6-116">Comentarios</span><span class="sxs-lookup"><span data-stu-id="40ee6-116">Remarks</span></span>

<span data-ttu-id="40ee6-117">Esta función puede cambiar el tamaño de los búferes internos en la sesión de pseudoconsole para que coincida con el tamaño de búfer o de ventana que se usa para la presentación en el extremo del terminal.</span><span class="sxs-lookup"><span data-stu-id="40ee6-117">This function can resize the internal buffers in the pseudoconsole session to match the window/buffer size being used for display on the terminal end.</span></span> <span data-ttu-id="40ee6-118">Esto garantiza que las aplicaciones conectadas de la interfaz de Command-Line (CUI) que usan las funciones de la [consola](console-functions.md) para comunicarse tendrán las dimensiones correctas devueltas en sus llamadas.</span><span class="sxs-lookup"><span data-stu-id="40ee6-118">This ensures that attached Command-Line Interface (CUI) applications using the [Console Functions](console-functions.md) to communicate will have the correct dimensions returned in their calls.</span></span>

## <a name="requirements"></a><span data-ttu-id="40ee6-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="40ee6-119">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="40ee6-120">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="40ee6-120">Minimum supported client</span></span> | <span data-ttu-id="40ee6-121">Actualización 2018 de octubre de Windows 10 (versión 1809) \[ solo para aplicaciones de escritorio\]</span><span class="sxs-lookup"><span data-stu-id="40ee6-121">Windows 10 October 2018 Update (version 1809) \[desktop apps only\]</span></span> |
| <span data-ttu-id="40ee6-122">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="40ee6-122">Minimum supported server</span></span> | <span data-ttu-id="40ee6-123">Solo aplicaciones de escritorio de Windows Server 2019 \[\]</span><span class="sxs-lookup"><span data-stu-id="40ee6-123">Windows Server 2019 \[desktop apps only\]</span></span> |
| <span data-ttu-id="40ee6-124">Encabezado</span><span class="sxs-lookup"><span data-stu-id="40ee6-124">Header</span></span> | <span data-ttu-id="40ee6-125">ConsoleApi. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="40ee6-125">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="40ee6-126">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="40ee6-126">Library</span></span> | <span data-ttu-id="40ee6-127">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="40ee6-127">Kernel32.lib</span></span> |
| <span data-ttu-id="40ee6-128">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="40ee6-128">DLL</span></span> | <span data-ttu-id="40ee6-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="40ee6-129">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="40ee6-130">Consulte también</span><span class="sxs-lookup"><span data-stu-id="40ee6-130">See also</span></span>

[<span data-ttu-id="40ee6-131">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="40ee6-131">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="40ee6-132">**ClosePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="40ee6-132">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="40ee6-133">**ClosePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="40ee6-133">**ClosePseudoConsole**</span></span>](closepseudoconsole.md)
