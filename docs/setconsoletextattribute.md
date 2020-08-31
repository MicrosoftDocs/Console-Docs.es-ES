---
title: SetConsoleTextAttribute función)
description: Establece los atributos de caracteres que se escriben en el búfer de pantalla de la consola mediante la función WriteFile o WriteConsole, o que se han devuelto por la función ReadFile o ReadConsole.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleTextAttribute
- wincon/SetConsoleTextAttribute
- SetConsoleTextAttribute
MS-HAID:
- '\_win32\_setconsoletextattribute'
- base.setconsoletextattribute
- consoles.setconsoletextattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9fba5bb5-b999-4abd-ab39-7a63d58b8074
topic_type:
- apiref
api_name:
- SetConsoleTextAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 2242466e4255b0d92c9bb1d1eac5431b59346e7b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061079"
---
# <a name="setconsoletextattribute-function"></a><span data-ttu-id="4d4c1-104">SetConsoleTextAttribute función)</span><span class="sxs-lookup"><span data-stu-id="4d4c1-104">SetConsoleTextAttribute function</span></span>


<span data-ttu-id="4d4c1-105">Establece los atributos de caracteres que se escriben en el búfer de pantalla de la consola mediante la función [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) o [**WriteConsole**](writeconsole.md) , o que se han devuelto por la función [**readfile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) o [**ReadConsole**](readconsole.md) .</span><span class="sxs-lookup"><span data-stu-id="4d4c1-105">Sets the attributes of characters written to the console screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="4d4c1-106">Esta función afecta al texto escrito después de la llamada de función.</span><span class="sxs-lookup"><span data-stu-id="4d4c1-106">This function affects text written after the function call.</span></span>

<a name="syntax"></a><span data-ttu-id="4d4c1-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4d4c1-107">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleTextAttribute(
  _In_ HANDLE hConsoleOutput,
  _In_ WORD   wAttributes
);
```

<a name="parameters"></a><span data-ttu-id="4d4c1-108">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d4c1-108">Parameters</span></span>
----------

<span data-ttu-id="4d4c1-109">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="4d4c1-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="4d4c1-110">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="4d4c1-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="4d4c1-111">El identificador debe tener el derecho de acceso de \*\* \_ lectura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="4d4c1-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="4d4c1-112">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="4d4c1-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="4d4c1-113">*wAttributes* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="4d4c1-113">*wAttributes* \[in\]</span></span>  
<span data-ttu-id="4d4c1-114">[Atributos de carácter](console-screen-buffers.md#_win32_font_attributes).</span><span class="sxs-lookup"><span data-stu-id="4d4c1-114">The [character attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<a name="return-value"></a><span data-ttu-id="4d4c1-115">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4d4c1-115">Return value</span></span>
------------

<span data-ttu-id="4d4c1-116">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="4d4c1-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4d4c1-117">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="4d4c1-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4d4c1-118">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="4d4c1-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="4d4c1-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="4d4c1-119">Remarks</span></span>
-------

<span data-ttu-id="4d4c1-120">Para determinar los atributos de color actuales de un búfer de pantalla, llame a la función [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="4d4c1-120">To determine the current color attributes of a screen buffer, call the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<a name="examples"></a><span data-ttu-id="4d4c1-121">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="4d4c1-121">Examples</span></span>
--------

<span data-ttu-id="4d4c1-122">Para obtener un ejemplo, vea [usar las funciones de entrada y salida de alto nivel](using-the-high-level-input-and-output-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4d4c1-122">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

<a name="requirements"></a><span data-ttu-id="4d4c1-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4d4c1-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="4d4c1-124">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="4d4c1-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="4d4c1-125">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="4d4c1-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4d4c1-126">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="4d4c1-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="4d4c1-127">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="4d4c1-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4d4c1-128">Encabezado</span><span class="sxs-lookup"><span data-stu-id="4d4c1-128">Header</span></span></p></td>
<td><span data-ttu-id="4d4c1-129">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4d4c1-129">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4d4c1-130">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="4d4c1-130">Library</span></span></p></td>
<td><span data-ttu-id="4d4c1-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="4d4c1-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4d4c1-132">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="4d4c1-132">DLL</span></span></p></td>
<td><span data-ttu-id="4d4c1-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4d4c1-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="4d4c1-134"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="4d4c1-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="4d4c1-135">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="4d4c1-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4d4c1-136">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="4d4c1-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="4d4c1-137">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="4d4c1-137">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="4d4c1-138">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="4d4c1-138">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="4d4c1-139">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="4d4c1-139">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="4d4c1-140">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="4d4c1-140">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="4d4c1-141">**Escritura**</span><span class="sxs-lookup"><span data-stu-id="4d4c1-141">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 




