---
title: GetCurrentConsoleFontEx función)
description: Consulte la información de referencia sobre la función GetCurrentConsoleFontEx, que recupera información extendida sobre la fuente de consola usada actualmente.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetCurrentConsoleFontEx
- wincon/GetCurrentConsoleFontEx
- GetCurrentConsoleFontEx
MS-HAID:
- base.getcurrentconsolefontex
- consoles.getcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 97d8e730-4110-4be5-b099-0acc1b6f8eb5
topic_type:
- apiref
api_name:
- GetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: e499cdb51a5ca71948dd40ebd3d4d151f2d71a8a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038733"
---
# <a name="getcurrentconsolefontex-function"></a><span data-ttu-id="115b6-104">GetCurrentConsoleFontEx función)</span><span class="sxs-lookup"><span data-stu-id="115b6-104">GetCurrentConsoleFontEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="115b6-105">Recupera información extendida sobre la fuente de consola actual.</span><span class="sxs-lookup"><span data-stu-id="115b6-105">Retrieves extended information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="115b6-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="115b6-106">Syntax</span></span>

```C
BOOL WINAPI GetCurrentConsoleFontEx(
  _In_  HANDLE               hConsoleOutput,
  _In_  BOOL                 bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

## <a name="parameters"></a><span data-ttu-id="115b6-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="115b6-107">Parameters</span></span>

<span data-ttu-id="115b6-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="115b6-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="115b6-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="115b6-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="115b6-110">El identificador debe tener el derecho de acceso de **\_ lectura genérico** .</span><span class="sxs-lookup"><span data-stu-id="115b6-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="115b6-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="115b6-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="115b6-112">*bMaximumWindow* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="115b6-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="115b6-113">Si este parámetro es **true** , se recupera la información de fuente para el tamaño máximo de la ventana.</span><span class="sxs-lookup"><span data-stu-id="115b6-113">If this parameter is **TRUE** , font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="115b6-114">Si este parámetro es **false** , se recupera la información de fuente para el tamaño de la ventana actual.</span><span class="sxs-lookup"><span data-stu-id="115b6-114">If this parameter is **FALSE** , font information is retrieved for the current window size.</span></span>

<span data-ttu-id="115b6-115">*lpConsoleCurrentFontEx* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="115b6-115">*lpConsoleCurrentFontEx* \[out\]</span></span>  
<span data-ttu-id="115b6-116">Puntero a una estructura [**\_ \_ INFOEX de fuente de consola**](console-font-infoex.md) que recibe la información de fuente solicitada.</span><span class="sxs-lookup"><span data-stu-id="115b6-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that receives the requested font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="115b6-117">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="115b6-117">Return value</span></span>

<span data-ttu-id="115b6-118">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="115b6-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="115b6-119">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="115b6-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="115b6-120">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="115b6-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="115b6-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="115b6-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="115b6-122">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="115b6-122">Minimum supported client</span></span> | <span data-ttu-id="115b6-123">Solo aplicaciones de escritorio de Windows Vista \[\]</span><span class="sxs-lookup"><span data-stu-id="115b6-123">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="115b6-124">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="115b6-124">Minimum supported server</span></span> | <span data-ttu-id="115b6-125">Solo aplicaciones de escritorio de Windows Server 2008 \[\]</span><span class="sxs-lookup"><span data-stu-id="115b6-125">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="115b6-126">Encabezado</span><span class="sxs-lookup"><span data-stu-id="115b6-126">Header</span></span> | <span data-ttu-id="115b6-127">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="115b6-127">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="115b6-128">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="115b6-128">Library</span></span> | <span data-ttu-id="115b6-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="115b6-129">Kernel32.lib</span></span> |
| <span data-ttu-id="115b6-130">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="115b6-130">DLL</span></span> | <span data-ttu-id="115b6-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="115b6-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="115b6-132">Consulte también</span><span class="sxs-lookup"><span data-stu-id="115b6-132">See also</span></span>

[<span data-ttu-id="115b6-133">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="115b6-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="115b6-134">**fuente de consola \_ \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="115b6-134">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)
