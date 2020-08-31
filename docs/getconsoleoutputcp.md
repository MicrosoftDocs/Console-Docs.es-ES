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
ms.openlocfilehash: e80618ebd5c6b29f00e79594c55bfa15fab315ba
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060684"
---
# <a name="getconsoleoutputcp-function"></a><span data-ttu-id="bd9fe-104">GetConsoleOutputCP función)</span><span class="sxs-lookup"><span data-stu-id="bd9fe-104">GetConsoleOutputCP function</span></span>


<span data-ttu-id="bd9fe-105">Recupera la página de códigos de salida utilizada por la consola asociada al proceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="bd9fe-105">Retrieves the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="bd9fe-106">Una consola usa su página de códigos de salida para traducir los valores de caracteres escritos por las distintas funciones de salida en las imágenes que se muestran en la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="bd9fe-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

<a name="syntax"></a><span data-ttu-id="bd9fe-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="bd9fe-107">Syntax</span></span>
------

```C
UINT WINAPI GetConsoleOutputCP(void);
```

<a name="parameters"></a><span data-ttu-id="bd9fe-108">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bd9fe-108">Parameters</span></span>
----------

<span data-ttu-id="bd9fe-109">Esta función no tiene parámetros.</span><span class="sxs-lookup"><span data-stu-id="bd9fe-109">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="bd9fe-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="bd9fe-110">Return value</span></span>
------------

<span data-ttu-id="bd9fe-111">El valor devuelto es un código que identifica la página de códigos.</span><span class="sxs-lookup"><span data-stu-id="bd9fe-111">The return value is a code that identifies the code page.</span></span> <span data-ttu-id="bd9fe-112">Para obtener una lista de identificadores, vea [identificadores de páginas de códigos](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span><span class="sxs-lookup"><span data-stu-id="bd9fe-112">For a list of identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="bd9fe-113">Si el valor devuelto es cero, se ha producido un error en la función.</span><span class="sxs-lookup"><span data-stu-id="bd9fe-113">If the return value is zero, the function has failed.</span></span> <span data-ttu-id="bd9fe-114">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="bd9fe-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="bd9fe-115">Observaciones</span><span class="sxs-lookup"><span data-stu-id="bd9fe-115">Remarks</span></span>
-------

<span data-ttu-id="bd9fe-116">Una página de códigos asigna códigos de caracteres de 256 a caracteres individuales.</span><span class="sxs-lookup"><span data-stu-id="bd9fe-116">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="bd9fe-117">Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas.</span><span class="sxs-lookup"><span data-stu-id="bd9fe-117">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span> <span data-ttu-id="bd9fe-118">Para recuperar más información sobre una página de códigos, incluido su nombre, vea la función [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .</span><span class="sxs-lookup"><span data-stu-id="bd9fe-118">To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span>

<span data-ttu-id="bd9fe-119">Para establecer la página de códigos de salida de la consola, use la función [**SetConsoleOutputCP**](setconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="bd9fe-119">To set a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) function.</span></span> <span data-ttu-id="bd9fe-120">Para establecer y consultar la página de códigos de entrada de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) y [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="bd9fe-120">To set and query a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

<a name="requirements"></a><span data-ttu-id="bd9fe-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bd9fe-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="bd9fe-122">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="bd9fe-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="bd9fe-123">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="bd9fe-123">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bd9fe-124">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="bd9fe-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="bd9fe-125">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="bd9fe-125">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bd9fe-126">Encabezado</span><span class="sxs-lookup"><span data-stu-id="bd9fe-126">Header</span></span></p></td>
<td><span data-ttu-id="bd9fe-127">ConsoleApi. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="bd9fe-127">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="bd9fe-128">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="bd9fe-128">Library</span></span></p></td>
<td><span data-ttu-id="bd9fe-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="bd9fe-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="bd9fe-130">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="bd9fe-130">DLL</span></span></p></td>
<td><span data-ttu-id="bd9fe-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="bd9fe-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="bd9fe-132"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="bd9fe-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="bd9fe-133">Páginas de códigos de la consola</span><span class="sxs-lookup"><span data-stu-id="bd9fe-133">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="bd9fe-134">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="bd9fe-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="bd9fe-135">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="bd9fe-135">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="bd9fe-136">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="bd9fe-136">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="bd9fe-137">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="bd9fe-137">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

 

 




