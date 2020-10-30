---
title: GetCurrentConsoleFont función)
description: Recupera información sobre la fuente de consola actual para un búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetCurrentConsoleFont
- wincon/GetCurrentConsoleFont
- GetCurrentConsoleFont
MS-HAID:
- '\_win32\_getcurrentconsolefont'
- base.getcurrentconsolefont
- consoles.getcurrentconsolefont
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 347508ea-5c15-4568-b99f-1e7f5cdac8c1
topic_type:
- apiref
api_name:
- GetCurrentConsoleFont
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: b394f116a75e3c8fb7fddbdc3335e89fbca96652
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037863"
---
# <a name="getcurrentconsolefont-function"></a><span data-ttu-id="fe7ca-104">GetCurrentConsoleFont función)</span><span class="sxs-lookup"><span data-stu-id="fe7ca-104">GetCurrentConsoleFont function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="fe7ca-105">Recupera información sobre la fuente de consola actual.</span><span class="sxs-lookup"><span data-stu-id="fe7ca-105">Retrieves information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="fe7ca-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fe7ca-106">Syntax</span></span>

```C
BOOL WINAPI GetCurrentConsoleFont(
  _In_  HANDLE             hConsoleOutput,
  _In_  BOOL               bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFO lpConsoleCurrentFont
);
```

## <a name="parameters"></a><span data-ttu-id="fe7ca-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="fe7ca-107">Parameters</span></span>

<span data-ttu-id="fe7ca-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="fe7ca-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="fe7ca-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="fe7ca-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="fe7ca-110">El identificador debe tener el derecho de acceso de **\_ lectura genérico** .</span><span class="sxs-lookup"><span data-stu-id="fe7ca-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="fe7ca-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="fe7ca-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="fe7ca-112">*bMaximumWindow* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="fe7ca-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="fe7ca-113">Si este parámetro es **true** , se recupera la información de fuente para el tamaño máximo de la ventana.</span><span class="sxs-lookup"><span data-stu-id="fe7ca-113">If this parameter is **TRUE** , font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="fe7ca-114">Si este parámetro es **false** , se recupera la información de fuente para el tamaño de la ventana actual.</span><span class="sxs-lookup"><span data-stu-id="fe7ca-114">If this parameter is **FALSE** , font information is retrieved for the current window size.</span></span>

<span data-ttu-id="fe7ca-115">*lpConsoleCurrentFont* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="fe7ca-115">*lpConsoleCurrentFont* \[out\]</span></span>  
<span data-ttu-id="fe7ca-116">Puntero a una estructura [**de \_ \_ información de fuente de consola**](console-font-info-str.md) que recibe la información de fuente solicitada.</span><span class="sxs-lookup"><span data-stu-id="fe7ca-116">A pointer to a [**CONSOLE\_FONT\_INFO**](console-font-info-str.md) structure that receives the requested font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="fe7ca-117">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="fe7ca-117">Return value</span></span>

<span data-ttu-id="fe7ca-118">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="fe7ca-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="fe7ca-119">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="fe7ca-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="fe7ca-120">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="fe7ca-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="fe7ca-121">Comentarios</span><span class="sxs-lookup"><span data-stu-id="fe7ca-121">Remarks</span></span>

<span data-ttu-id="fe7ca-122">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0500 o posterior.</span><span class="sxs-lookup"><span data-stu-id="fe7ca-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="fe7ca-123">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="fe7ca-123">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="fe7ca-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fe7ca-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="fe7ca-125">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="fe7ca-125">Minimum supported client</span></span> | <span data-ttu-id="fe7ca-126">Solo aplicaciones de escritorio de Windows XP \[\]</span><span class="sxs-lookup"><span data-stu-id="fe7ca-126">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="fe7ca-127">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="fe7ca-127">Minimum supported server</span></span> | <span data-ttu-id="fe7ca-128">Solo aplicaciones de escritorio de Windows Server 2003 \[\]</span><span class="sxs-lookup"><span data-stu-id="fe7ca-128">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="fe7ca-129">Encabezado</span><span class="sxs-lookup"><span data-stu-id="fe7ca-129">Header</span></span> | <span data-ttu-id="fe7ca-130">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="fe7ca-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="fe7ca-131">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="fe7ca-131">Library</span></span> | <span data-ttu-id="fe7ca-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="fe7ca-132">Kernel32.lib</span></span> |
| <span data-ttu-id="fe7ca-133">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="fe7ca-133">DLL</span></span> | <span data-ttu-id="fe7ca-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="fe7ca-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="fe7ca-135">Consulte también</span><span class="sxs-lookup"><span data-stu-id="fe7ca-135">See also</span></span>

[<span data-ttu-id="fe7ca-136">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="fe7ca-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="fe7ca-137">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="fe7ca-137">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="fe7ca-138">**\_información de fuente de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="fe7ca-138">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="fe7ca-139">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="fe7ca-139">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)
