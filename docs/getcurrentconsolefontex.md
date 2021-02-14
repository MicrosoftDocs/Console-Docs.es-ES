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
ms.openlocfilehash: e7932d286723886f671be051294fcffb23155bf6
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358885"
---
# <a name="getcurrentconsolefontex-function"></a><span data-ttu-id="4cd79-104">GetCurrentConsoleFontEx función)</span><span class="sxs-lookup"><span data-stu-id="4cd79-104">GetCurrentConsoleFontEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="4cd79-105">Recupera información extendida sobre la fuente de consola actual.</span><span class="sxs-lookup"><span data-stu-id="4cd79-105">Retrieves extended information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="4cd79-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4cd79-106">Syntax</span></span>

```C
BOOL WINAPI GetCurrentConsoleFontEx(
  _In_  HANDLE               hConsoleOutput,
  _In_  BOOL                 bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

## <a name="parameters"></a><span data-ttu-id="4cd79-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4cd79-107">Parameters</span></span>

<span data-ttu-id="4cd79-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4cd79-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="4cd79-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="4cd79-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="4cd79-110">El identificador debe tener derecho de acceso de **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="4cd79-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="4cd79-111">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="4cd79-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="4cd79-112">*bMaximumWindow* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="4cd79-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="4cd79-113">Si este parámetro es **true**, se recupera la información de fuente para el tamaño máximo de la ventana.</span><span class="sxs-lookup"><span data-stu-id="4cd79-113">If this parameter is **TRUE**, font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="4cd79-114">Si este parámetro es **false**, se recupera la información de fuente para el tamaño de la ventana actual.</span><span class="sxs-lookup"><span data-stu-id="4cd79-114">If this parameter is **FALSE**, font information is retrieved for the current window size.</span></span>

<span data-ttu-id="4cd79-115">*lpConsoleCurrentFontEx* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="4cd79-115">*lpConsoleCurrentFontEx* \[out\]</span></span>  
<span data-ttu-id="4cd79-116">Puntero a una estructura [**\_ \_ INFOEX de fuente de consola**](console-font-infoex.md) que recibe la información de fuente solicitada.</span><span class="sxs-lookup"><span data-stu-id="4cd79-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that receives the requested font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="4cd79-117">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4cd79-117">Return value</span></span>

<span data-ttu-id="4cd79-118">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="4cd79-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4cd79-119">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="4cd79-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4cd79-120">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="4cd79-120">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="4cd79-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4cd79-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4cd79-122">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="4cd79-122">Minimum supported client</span></span> | <span data-ttu-id="4cd79-123">Solo aplicaciones de escritorio de Windows Vista \[\]</span><span class="sxs-lookup"><span data-stu-id="4cd79-123">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="4cd79-124">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="4cd79-124">Minimum supported server</span></span> | <span data-ttu-id="4cd79-125">Solo aplicaciones de escritorio de Windows Server 2008 \[\]</span><span class="sxs-lookup"><span data-stu-id="4cd79-125">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="4cd79-126">Encabezado</span><span class="sxs-lookup"><span data-stu-id="4cd79-126">Header</span></span> | <span data-ttu-id="4cd79-127">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4cd79-127">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="4cd79-128">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="4cd79-128">Library</span></span> | <span data-ttu-id="4cd79-129">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="4cd79-129">Kernel32.lib</span></span> |
| <span data-ttu-id="4cd79-130">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="4cd79-130">DLL</span></span> | <span data-ttu-id="4cd79-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4cd79-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="4cd79-132">Vea también</span><span class="sxs-lookup"><span data-stu-id="4cd79-132">See also</span></span>

[<span data-ttu-id="4cd79-133">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="4cd79-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4cd79-134">**fuente de consola \_ \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="4cd79-134">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)