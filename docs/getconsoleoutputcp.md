---
title: GetConsoleOutputCP función)
description: Recupera la página de códigos de salida utilizada por la consola asociada al proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi/GetConsoleOutputCP
- wincon/GetConsoleOutputCP
- GetConsoleOutputCP
MS-HAID:
- '\_win32\_getconsoleoutputcp'
- base.getconsoleoutputcp
- consoles.getconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c23706c7-ce17-4825-a494-20ca44534d45
topic_type:
- apiref
api_name:
- GetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 858b0de83c7b1c4678e992b5f9d0ca3d4876ba49
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358955"
---
# <a name="getconsoleoutputcp-function"></a><span data-ttu-id="c229d-104">GetConsoleOutputCP función)</span><span class="sxs-lookup"><span data-stu-id="c229d-104">GetConsoleOutputCP function</span></span>

<span data-ttu-id="c229d-105">Recupera la página de códigos de salida utilizada por la consola asociada al proceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="c229d-105">Retrieves the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="c229d-106">Una consola usa su página de códigos de salida para traducir los valores de caracteres escritos por las distintas funciones de salida en las imágenes que se muestran en la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="c229d-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="c229d-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c229d-107">Syntax</span></span>

```C
UINT WINAPI GetConsoleOutputCP(void);
```

## <a name="parameters"></a><span data-ttu-id="c229d-108">Parámetros</span><span class="sxs-lookup"><span data-stu-id="c229d-108">Parameters</span></span>

<span data-ttu-id="c229d-109">Esta función no tiene parámetros.</span><span class="sxs-lookup"><span data-stu-id="c229d-109">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="c229d-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="c229d-110">Return value</span></span>

<span data-ttu-id="c229d-111">El valor devuelto es un código que identifica la página de códigos.</span><span class="sxs-lookup"><span data-stu-id="c229d-111">The return value is a code that identifies the code page.</span></span> <span data-ttu-id="c229d-112">Para obtener una lista de identificadores, vea [identificadores de páginas de códigos](/windows/win32/intl/code-page-identifiers).</span><span class="sxs-lookup"><span data-stu-id="c229d-112">For a list of identifiers, see [Code Page Identifiers](/windows/win32/intl/code-page-identifiers).</span></span>

<span data-ttu-id="c229d-113">Si el valor devuelto es cero, se ha producido un error en la función.</span><span class="sxs-lookup"><span data-stu-id="c229d-113">If the return value is zero, the function has failed.</span></span> <span data-ttu-id="c229d-114">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="c229d-114">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="c229d-115">Comentarios</span><span class="sxs-lookup"><span data-stu-id="c229d-115">Remarks</span></span>

<span data-ttu-id="c229d-116">Una página de códigos asigna códigos de caracteres de 256 a caracteres individuales.</span><span class="sxs-lookup"><span data-stu-id="c229d-116">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="c229d-117">Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas.</span><span class="sxs-lookup"><span data-stu-id="c229d-117">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span> <span data-ttu-id="c229d-118">Para recuperar más información sobre una página de códigos, incluido su nombre, vea la función [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) .</span><span class="sxs-lookup"><span data-stu-id="c229d-118">To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) function.</span></span>

<span data-ttu-id="c229d-119">Para establecer la página de códigos de salida de la consola, use la función [**SetConsoleOutputCP**](setconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="c229d-119">To set a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) function.</span></span> <span data-ttu-id="c229d-120">Para establecer y consultar la página de códigos de entrada de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) y [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="c229d-120">To set and query a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="c229d-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c229d-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c229d-122">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="c229d-122">Minimum supported client</span></span> | <span data-ttu-id="c229d-123">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="c229d-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="c229d-124">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="c229d-124">Minimum supported server</span></span> | <span data-ttu-id="c229d-125">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="c229d-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="c229d-126">Encabezado</span><span class="sxs-lookup"><span data-stu-id="c229d-126">Header</span></span> | <span data-ttu-id="c229d-127">ConsoleApi.h (a través de WinCon.h, incluido Windows.h)</span><span class="sxs-lookup"><span data-stu-id="c229d-127">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c229d-128">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="c229d-128">Library</span></span> | <span data-ttu-id="c229d-129">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="c229d-129">Kernel32.lib</span></span> |
| <span data-ttu-id="c229d-130">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="c229d-130">DLL</span></span> | <span data-ttu-id="c229d-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c229d-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="c229d-132">Vea también</span><span class="sxs-lookup"><span data-stu-id="c229d-132">See also</span></span>

[<span data-ttu-id="c229d-133">Páginas de código de la consola</span><span class="sxs-lookup"><span data-stu-id="c229d-133">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="c229d-134">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="c229d-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c229d-135">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="c229d-135">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="c229d-136">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="c229d-136">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="c229d-137">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="c229d-137">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)