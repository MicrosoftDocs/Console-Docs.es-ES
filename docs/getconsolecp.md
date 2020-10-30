---
title: GetConsoleCP función)
description: Recupera la página de códigos de entrada utilizada por la consola asociada al proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/GetConsoleCP
- wincon/GetConsoleCP
- GetConsoleCP
MS-HAID:
- '\_win32\_getconsolecp'
- base.getconsolecp
- consoles.getconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9e0af6d9-0f5c-45b3-a686-22449d26de47
topic_type:
- apiref
api_name:
- GetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 75570acba7d8572d1bd3f132ac379598d82ec73f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038023"
---
# <a name="getconsolecp-function"></a><span data-ttu-id="c3646-104">GetConsoleCP función)</span><span class="sxs-lookup"><span data-stu-id="c3646-104">GetConsoleCP function</span></span>

<span data-ttu-id="c3646-105">Recupera la página de códigos de entrada utilizada por la consola asociada al proceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="c3646-105">Retrieves the input code page used by the console associated with the calling process.</span></span> <span data-ttu-id="c3646-106">Una consola usa su página de códigos de entrada para traducir la entrada del teclado en el valor de carácter correspondiente.</span><span class="sxs-lookup"><span data-stu-id="c3646-106">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span>

## <a name="syntax"></a><span data-ttu-id="c3646-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c3646-107">Syntax</span></span>

```C
UINT WINAPI GetConsoleCP(void);
```

## <a name="parameters"></a><span data-ttu-id="c3646-108">Parámetros</span><span class="sxs-lookup"><span data-stu-id="c3646-108">Parameters</span></span>

<span data-ttu-id="c3646-109">Esta función no tiene parámetros.</span><span class="sxs-lookup"><span data-stu-id="c3646-109">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="c3646-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="c3646-110">Return value</span></span>

<span data-ttu-id="c3646-111">El valor devuelto es un código que identifica la página de códigos.</span><span class="sxs-lookup"><span data-stu-id="c3646-111">The return value is a code that identifies the code page.</span></span> <span data-ttu-id="c3646-112">Para obtener una lista de identificadores, vea [identificadores de páginas de códigos](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span><span class="sxs-lookup"><span data-stu-id="c3646-112">For a list of identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="c3646-113">Si el valor devuelto es cero, se ha producido un error en la función.</span><span class="sxs-lookup"><span data-stu-id="c3646-113">If the return value is zero, the function has failed.</span></span> <span data-ttu-id="c3646-114">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="c3646-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="c3646-115">Comentarios</span><span class="sxs-lookup"><span data-stu-id="c3646-115">Remarks</span></span>

<span data-ttu-id="c3646-116">Una página de códigos asigna códigos de caracteres de 256 a caracteres individuales.</span><span class="sxs-lookup"><span data-stu-id="c3646-116">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="c3646-117">Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas.</span><span class="sxs-lookup"><span data-stu-id="c3646-117">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span> <span data-ttu-id="c3646-118">Para recuperar más información sobre una página de códigos, incluido su nombre, vea la función [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .</span><span class="sxs-lookup"><span data-stu-id="c3646-118">To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span>

<span data-ttu-id="c3646-119">Para establecer la página de códigos de entrada de la consola, use la función [**SetConsoleCP**](setconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="c3646-119">To set a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) function.</span></span> <span data-ttu-id="c3646-120">Para establecer y consultar la página de códigos de salida de la consola, use las funciones [**SetConsoleOutputCP**](setconsoleoutputcp.md) y [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="c3646-120">To set and query a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="c3646-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3646-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c3646-122">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="c3646-122">Minimum supported client</span></span> | <span data-ttu-id="c3646-123">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="c3646-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="c3646-124">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="c3646-124">Minimum supported server</span></span> | <span data-ttu-id="c3646-125">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="c3646-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="c3646-126">Encabezado</span><span class="sxs-lookup"><span data-stu-id="c3646-126">Header</span></span> | <span data-ttu-id="c3646-127">ConsoleApi. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c3646-127">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c3646-128">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="c3646-128">Library</span></span> | <span data-ttu-id="c3646-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="c3646-129">Kernel32.lib</span></span> |
| <span data-ttu-id="c3646-130">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="c3646-130">DLL</span></span> | <span data-ttu-id="c3646-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c3646-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="c3646-132">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c3646-132">See also</span></span>

[<span data-ttu-id="c3646-133">Páginas de código de la consola</span><span class="sxs-lookup"><span data-stu-id="c3646-133">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="c3646-134">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="c3646-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c3646-135">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="c3646-135">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="c3646-136">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="c3646-136">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="c3646-137">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="c3646-137">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)
