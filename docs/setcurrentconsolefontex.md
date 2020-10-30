---
title: SetCurrentConsoleFontEx función)
description: Consulte la información de referencia sobre la función SetCurrentConsoleFontEx, que establece la información extendida sobre la fuente de consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/SetCurrentConsoleFontEx
- wincon/SetCurrentConsoleFontEx
- SetCurrentConsoleFontEx
MS-HAID:
- base.setcurrentconsolefontex
- consoles.setcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: fbc31e2a-31df-4e9e-9f61-35a4ff812f8f
topic_type:
- apiref
api_name:
- SetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 1ba89b90a0362261aafbe5ac6462224b3c0172dc
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037060"
---
# <a name="setcurrentconsolefontex-function"></a><span data-ttu-id="af95a-104">SetCurrentConsoleFontEx función)</span><span class="sxs-lookup"><span data-stu-id="af95a-104">SetCurrentConsoleFontEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="af95a-105">Establece la información extendida sobre la fuente de consola actual.</span><span class="sxs-lookup"><span data-stu-id="af95a-105">Sets extended information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="af95a-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="af95a-106">Syntax</span></span>

```C
BOOL WINAPI SetCurrentConsoleFontEx(
  _In_ HANDLE               hConsoleOutput,
  _In_ BOOL                 bMaximumWindow,
  _In_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

## <a name="parameters"></a><span data-ttu-id="af95a-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af95a-107">Parameters</span></span>

<span data-ttu-id="af95a-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="af95a-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="af95a-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="af95a-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="af95a-110">El identificador debe tener el derecho de acceso de **\_ escritura genérico** .</span><span class="sxs-lookup"><span data-stu-id="af95a-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="af95a-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="af95a-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="af95a-112">*bMaximumWindow* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="af95a-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="af95a-113">Si este parámetro es **true** , la información de fuente se establece para el tamaño máximo de la ventana.</span><span class="sxs-lookup"><span data-stu-id="af95a-113">If this parameter is **TRUE** , font information is set for the maximum window size.</span></span> <span data-ttu-id="af95a-114">Si este parámetro es **false** , se establece la información de fuente para el tamaño de la ventana actual.</span><span class="sxs-lookup"><span data-stu-id="af95a-114">If this parameter is **FALSE** , font information is set for the current window size.</span></span>

<span data-ttu-id="af95a-115">*lpConsoleCurrentFontEx* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="af95a-115">*lpConsoleCurrentFontEx* \[in\]</span></span>  
<span data-ttu-id="af95a-116">Puntero a una estructura [**\_ \_ INFOEX**](console-font-infoex.md) de la fuente de la consola que contiene la información de la fuente.</span><span class="sxs-lookup"><span data-stu-id="af95a-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that contains the font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="af95a-117">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="af95a-117">Return value</span></span>

<span data-ttu-id="af95a-118">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="af95a-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="af95a-119">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="af95a-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="af95a-120">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="af95a-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="af95a-121">Comentarios</span><span class="sxs-lookup"><span data-stu-id="af95a-121">Remarks</span></span>

<span data-ttu-id="af95a-122">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0500 o posterior.</span><span class="sxs-lookup"><span data-stu-id="af95a-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="af95a-123">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="af95a-123">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="af95a-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af95a-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="af95a-125">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="af95a-125">Minimum supported client</span></span> | <span data-ttu-id="af95a-126">Solo aplicaciones de escritorio de Windows Vista \[\]</span><span class="sxs-lookup"><span data-stu-id="af95a-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="af95a-127">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="af95a-127">Minimum supported server</span></span> | <span data-ttu-id="af95a-128">Solo aplicaciones de escritorio de Windows Server 2008 \[\]</span><span class="sxs-lookup"><span data-stu-id="af95a-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="af95a-129">Encabezado</span><span class="sxs-lookup"><span data-stu-id="af95a-129">Header</span></span> | <span data-ttu-id="af95a-130">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="af95a-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="af95a-131">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="af95a-131">Library</span></span> | <span data-ttu-id="af95a-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="af95a-132">Kernel32.lib</span></span> |
| <span data-ttu-id="af95a-133">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="af95a-133">DLL</span></span> | <span data-ttu-id="af95a-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="af95a-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="af95a-135">Consulte también</span><span class="sxs-lookup"><span data-stu-id="af95a-135">See also</span></span>

[<span data-ttu-id="af95a-136">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="af95a-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="af95a-137">**fuente de consola \_ \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="af95a-137">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)
