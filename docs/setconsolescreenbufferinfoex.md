---
title: SetConsoleScreenBufferInfoEx función)
description: Establece la información extendida sobre el búfer de pantalla especificado en el búfer especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleScreenBufferInfoEx
- wincon/SetConsoleScreenBufferInfoEx
- SetConsoleScreenBufferInfoEx
MS-HAID:
- base.setconsolescreenbufferinfoex
- consoles.setconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ff851144-eee9-4410-8fd1-28aa24fc25f1
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 403ce6c3625aacdcc8b2eb498e7df1715d1e6b94
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061067"
---
# <a name="setconsolescreenbufferinfoex-function"></a><span data-ttu-id="71f5d-104">SetConsoleScreenBufferInfoEx función)</span><span class="sxs-lookup"><span data-stu-id="71f5d-104">SetConsoleScreenBufferInfoEx function</span></span>


<span data-ttu-id="71f5d-105">Establece la información extendida sobre el búfer de pantalla especificado.</span><span class="sxs-lookup"><span data-stu-id="71f5d-105">Sets extended information about the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="71f5d-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="71f5d-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleScreenBufferInfoEx(
  _In_ HANDLE                        hConsoleOutput,
  _In_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

<a name="parameters"></a><span data-ttu-id="71f5d-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="71f5d-107">Parameters</span></span>
----------

<span data-ttu-id="71f5d-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="71f5d-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="71f5d-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="71f5d-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="71f5d-110">El identificador debe tener el derecho de acceso de \*\* \_ escritura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="71f5d-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="71f5d-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="71f5d-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="71f5d-112">*lpConsoleScreenBufferInfoEx* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="71f5d-112">*lpConsoleScreenBufferInfoEx* \[in\]</span></span>  
<span data-ttu-id="71f5d-113">Una [**estructura \_ \_ \_ INFOEX de búfer de pantalla**](console-screen-buffer-infoex.md) de la consola que contiene la información del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="71f5d-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that contains the console screen buffer information.</span></span>

<a name="return-value"></a><span data-ttu-id="71f5d-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="71f5d-114">Return value</span></span>
------------

<span data-ttu-id="71f5d-115">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="71f5d-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="71f5d-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="71f5d-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="71f5d-117">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="71f5d-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="71f5d-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="71f5d-118">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="71f5d-119">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="71f5d-119">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="71f5d-120">Windows Vista [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="71f5d-120">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="71f5d-121">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="71f5d-121">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="71f5d-122">Windows Server 2008 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="71f5d-122">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="71f5d-123">Encabezado</span><span class="sxs-lookup"><span data-stu-id="71f5d-123">Header</span></span></p></td>
<td><span data-ttu-id="71f5d-124">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="71f5d-124">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="71f5d-125">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="71f5d-125">Library</span></span></p></td>
<td><span data-ttu-id="71f5d-126">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="71f5d-126">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="71f5d-127">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="71f5d-127">DLL</span></span></p></td>
<td><span data-ttu-id="71f5d-128">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="71f5d-128">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="71f5d-129"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="71f5d-129"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="71f5d-130">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="71f5d-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="71f5d-131">**búfer de pantalla de la consola \_ \_ \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="71f5d-131">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="71f5d-132">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="71f5d-132">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)

 

 




