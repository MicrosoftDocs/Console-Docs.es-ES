---
title: GetConsoleSelectionInfo función)
description: Consulte la información de referencia sobre la función GetConsoleSelectionInfo, que recupera información sobre la selección de la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleSelectionInfo
- wincon/GetConsoleSelectionInfo
- GetConsoleSelectionInfo
MS-HAID:
- '\_win32\_getconsoleselectioninfo'
- base.getconsoleselectioninfo
- consoles.getconsoleselectioninfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 912efe9d-75dd-43bd-8dca-08671b5ed79c
topic_type:
- apiref
api_name:
- GetConsoleSelectionInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 2f1052940b468455121cc363317c2b7cfa8246b3
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038853"
---
# <a name="getconsoleselectioninfo-function"></a><span data-ttu-id="887d0-104">GetConsoleSelectionInfo función)</span><span class="sxs-lookup"><span data-stu-id="887d0-104">GetConsoleSelectionInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="887d0-105">Recupera información sobre la selección de la consola actual.</span><span class="sxs-lookup"><span data-stu-id="887d0-105">Retrieves information about the current console selection.</span></span>

## <a name="syntax"></a><span data-ttu-id="887d0-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="887d0-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleSelectionInfo(
  _Out_ PCONSOLE_SELECTION_INFO lpConsoleSelectionInfo
);
```

## <a name="parameters"></a><span data-ttu-id="887d0-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="887d0-107">Parameters</span></span>

<span data-ttu-id="887d0-108">*lpConsoleSelectionInfo* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="887d0-108">*lpConsoleSelectionInfo* \[out\]</span></span>  
<span data-ttu-id="887d0-109">Un puntero a una estructura de [**\_ \_ información de selección de consola**](console-selection-info-str.md) que recibe la información de selección.</span><span class="sxs-lookup"><span data-stu-id="887d0-109">A pointer to a [**CONSOLE\_SELECTION\_INFO**](console-selection-info-str.md) structure that receives the selection information.</span></span>

## <a name="return-value"></a><span data-ttu-id="887d0-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="887d0-110">Return value</span></span>

<span data-ttu-id="887d0-111">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="887d0-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="887d0-112">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="887d0-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="887d0-113">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="887d0-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="887d0-114">Comentarios</span><span class="sxs-lookup"><span data-stu-id="887d0-114">Remarks</span></span>

<span data-ttu-id="887d0-115">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0500 o posterior.</span><span class="sxs-lookup"><span data-stu-id="887d0-115">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="887d0-116">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="887d0-116">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="887d0-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="887d0-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="887d0-118">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="887d0-118">Minimum supported client</span></span> | <span data-ttu-id="887d0-119">Solo aplicaciones de escritorio de Windows XP \[\]</span><span class="sxs-lookup"><span data-stu-id="887d0-119">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="887d0-120">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="887d0-120">Minimum supported server</span></span> | <span data-ttu-id="887d0-121">Solo aplicaciones de escritorio de Windows Server 2003 \[\]</span><span class="sxs-lookup"><span data-stu-id="887d0-121">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="887d0-122">Encabezado</span><span class="sxs-lookup"><span data-stu-id="887d0-122">Header</span></span> | <span data-ttu-id="887d0-123">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="887d0-123">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="887d0-124">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="887d0-124">Library</span></span> | <span data-ttu-id="887d0-125">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="887d0-125">Kernel32.lib</span></span> |
| <span data-ttu-id="887d0-126">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="887d0-126">DLL</span></span> | <span data-ttu-id="887d0-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="887d0-127">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="887d0-128">Consulte también</span><span class="sxs-lookup"><span data-stu-id="887d0-128">See also</span></span>

[<span data-ttu-id="887d0-129">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="887d0-129">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="887d0-130">Selección de la consola</span><span class="sxs-lookup"><span data-stu-id="887d0-130">Console Selection</span></span>](console-selection.md)

[<span data-ttu-id="887d0-131">**\_información de selección de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="887d0-131">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)
