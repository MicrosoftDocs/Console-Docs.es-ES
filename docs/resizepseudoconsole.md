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
ms.openlocfilehash: a4f6ff773538eda4d4c84c4b0bac2e647f6b80d8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060980"
---
# <a name="resizepseudoconsole-function"></a><span data-ttu-id="06787-104">ResizePseudoConsole función)</span><span class="sxs-lookup"><span data-stu-id="06787-104">ResizePseudoConsole function</span></span>


<span data-ttu-id="06787-105">Cambia el tamaño de los búferes internos de un pseudoconsole al tamaño especificado.</span><span class="sxs-lookup"><span data-stu-id="06787-105">Resizes the internal buffers for a pseudoconsole to the given size.</span></span>

<a name="syntax"></a><span data-ttu-id="06787-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="06787-106">Syntax</span></span>
------

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

<a name="parameters"></a><span data-ttu-id="06787-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="06787-107">Parameters</span></span>
----------

<span data-ttu-id="06787-108">*hPC* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="06787-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="06787-109">Identificador de un psuedoconsole activo tal y como lo abre [CreatePseudoConsole](createpseudoconsole.md).</span><span class="sxs-lookup"><span data-stu-id="06787-109">A handle to an active psuedoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

<span data-ttu-id="06787-110">*tamaño* \[ de de\]</span><span class="sxs-lookup"><span data-stu-id="06787-110">*size* \[in\]</span></span>  
<span data-ttu-id="06787-111">Dimensiones de la ventana o búfer en el recuento de caracteres que se usarán para el búfer interno de este pseudoconsole.</span><span class="sxs-lookup"><span data-stu-id="06787-111">The dimensions of the window/buffer in count of characters that will be used for the internal buffer of this pseudoconsole.</span></span> 

<a name="return-value"></a><span data-ttu-id="06787-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="06787-112">Return value</span></span>
------------

<span data-ttu-id="06787-113">Tipo: **HRESULT**</span><span class="sxs-lookup"><span data-stu-id="06787-113">Type: **HRESULT**</span></span>

<span data-ttu-id="06787-114">Si este método se ejecuta correctamente, devuelve **S_OK**.</span><span class="sxs-lookup"><span data-stu-id="06787-114">If this method succeeds, it returns **S_OK**.</span></span> <span data-ttu-id="06787-115">De lo contrario, devuelve un código de error **HRESULT** .</span><span class="sxs-lookup"><span data-stu-id="06787-115">Otherwise, it returns an **HRESULT** error code.</span></span>

<a name="remarks"></a><span data-ttu-id="06787-116">Observaciones</span><span class="sxs-lookup"><span data-stu-id="06787-116">Remarks</span></span>
-------

<span data-ttu-id="06787-117">Esta función puede cambiar el tamaño de los búferes internos en la sesión de pseudoconsole para que coincida con el tamaño de búfer o de ventana que se usa para la presentación en el extremo del terminal.</span><span class="sxs-lookup"><span data-stu-id="06787-117">This function can resize the internal buffers in the pseudoconsole session to match the window/buffer size being used for display on the terminal end.</span></span> <span data-ttu-id="06787-118">Esto garantiza que las aplicaciones de la interfaz de línea de comandos (CUI) conectadas que usan las funciones de la [consola](console-functions.md) para comunicarse tendrán las dimensiones correctas devueltas en sus llamadas.</span><span class="sxs-lookup"><span data-stu-id="06787-118">This ensures that attached Command-Line Interface (CUI) applications using the [Console Functions](console-functions.md) to communicate will have the correct dimensions returned in their calls.</span></span>

<a name="requirements"></a><span data-ttu-id="06787-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="06787-119">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="06787-120">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="06787-120">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="06787-121">Windows 10 1809 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="06787-121">Windows 10 1809 [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="06787-122">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="06787-122">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="06787-123">Windows Server 2019 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="06787-123">Windows Server 2019 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="06787-124">Encabezado</span><span class="sxs-lookup"><span data-stu-id="06787-124">Header</span></span></p></td>
<td><span data-ttu-id="06787-125">ConsoleApi. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="06787-125">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="06787-126">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="06787-126">Library</span></span></p></td>
<td><span data-ttu-id="06787-127">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="06787-127">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="06787-128">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="06787-128">DLL</span></span></p></td>
<td><span data-ttu-id="06787-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="06787-129">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="06787-130"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="06787-130"><span id="see_also"></span>See also</span></span>

[<span data-ttu-id="06787-131">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="06787-131">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="06787-132">**CreatePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="06787-132">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="06787-133">**ClosePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="06787-133">**ClosePseudoConsole**</span></span>](closepseudoconsole.md)
