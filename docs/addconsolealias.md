---
title: AddConsoleAlias función)
description: Vea la información de referencia sobre la función AddConsoleAlias, que define un alias de consola para el ejecutable especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/AddConsoleAlias
- consoleapi3/AddConsoleAliasA
- consoleapi3/AddConsoleAliasW
- wincon/AddConsoleAlias
- wincon/AddConsoleAliasA
- wincon/AddConsoleAliasW
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
MS-HAID:
- base.addconsolealias
- consoles.addconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e4072c3c-cf32-4992-847e-efdb846e5784
topic_type:
- apiref
api_name:
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 108a77b3178e7695e7477ea198df616fa8bcb199
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060925"
---
# <a name="addconsolealias-function"></a><span data-ttu-id="b683a-104">AddConsoleAlias función)</span><span class="sxs-lookup"><span data-stu-id="b683a-104">AddConsoleAlias function</span></span>


<span data-ttu-id="b683a-105">Define un alias de consola para el ejecutable especificado.</span><span class="sxs-lookup"><span data-stu-id="b683a-105">Defines a console alias for the specified executable.</span></span>

<a name="syntax"></a><span data-ttu-id="b683a-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b683a-106">Syntax</span></span>
------

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

<a name="parameters"></a><span data-ttu-id="b683a-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b683a-107">Parameters</span></span>
----------

<span data-ttu-id="b683a-108">*Origen* \[ de de\]</span><span class="sxs-lookup"><span data-stu-id="b683a-108">*Source* \[in\]</span></span>  
<span data-ttu-id="b683a-109">El alias de la consola que se va a asignar al texto especificado por el *destino*.</span><span class="sxs-lookup"><span data-stu-id="b683a-109">The console alias to be mapped to the text specified by *Target*.</span></span>

<span data-ttu-id="b683a-110">*Destino* \[ de de\]</span><span class="sxs-lookup"><span data-stu-id="b683a-110">*Target* \[in\]</span></span>  
<span data-ttu-id="b683a-111">Texto que se va a sustituir por el *origen*.</span><span class="sxs-lookup"><span data-stu-id="b683a-111">The text to be substituted for *Source*.</span></span> <span data-ttu-id="b683a-112">Si este parámetro es **null**, se quita el alias de la consola.</span><span class="sxs-lookup"><span data-stu-id="b683a-112">If this parameter is **NULL**, then the console alias is removed.</span></span>

<span data-ttu-id="b683a-113">*ExeName* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="b683a-113">*ExeName* \[in\]</span></span>  
<span data-ttu-id="b683a-114">Nombre del archivo ejecutable para el que se va a definir el alias de la consola.</span><span class="sxs-lookup"><span data-stu-id="b683a-114">The name of the executable file for which the console alias is to be defined.</span></span>

<a name="return-value"></a><span data-ttu-id="b683a-115">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="b683a-115">Return value</span></span>
------------

<span data-ttu-id="b683a-116">Si la función se ejecuta correctamente, el valor devuelto es **true**.</span><span class="sxs-lookup"><span data-stu-id="b683a-116">If the function succeeds, the return value is **TRUE**.</span></span>

<span data-ttu-id="b683a-117">Si se produce un error en la función, el valor devuelto es **false**.</span><span class="sxs-lookup"><span data-stu-id="b683a-117">If the function fails, the return value is **FALSE**.</span></span> <span data-ttu-id="b683a-118">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="b683a-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="b683a-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b683a-119">Remarks</span></span>
-------

<span data-ttu-id="b683a-120">Para compilar una aplicación que usa esta función, defina \*\* \_ Win32 \_ WinNT\*\* como 0x0501 o posterior.</span><span class="sxs-lookup"><span data-stu-id="b683a-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="b683a-121">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="b683a-121">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="examples"></a><span data-ttu-id="b683a-122">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="b683a-122">Examples</span></span>
--------

<span data-ttu-id="b683a-123">Para obtener un ejemplo, vea [alias de consola](console-aliases.md).</span><span class="sxs-lookup"><span data-stu-id="b683a-123">For an example, see [Console Aliases](console-aliases.md).</span></span>

<a name="requirements"></a><span data-ttu-id="b683a-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b683a-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b683a-125">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="b683a-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="b683a-126">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="b683a-126">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b683a-127">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="b683a-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="b683a-128">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="b683a-128">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b683a-129">Encabezado</span><span class="sxs-lookup"><span data-stu-id="b683a-129">Header</span></span></p></td>
<td><span data-ttu-id="b683a-130">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b683a-130">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b683a-131">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="b683a-131">Library</span></span></p></td>
<td><span data-ttu-id="b683a-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="b683a-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b683a-133">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="b683a-133">DLL</span></span></p></td>
<td><span data-ttu-id="b683a-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b683a-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b683a-135">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="b683a-135">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="b683a-136"><strong>AddConsoleAliasW</strong> (Unicode) y <strong>AddConsoleAliasA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="b683a-136"><strong>AddConsoleAliasW</strong> (Unicode) and <strong>AddConsoleAliasA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="b683a-137"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="b683a-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="b683a-138">Alias de la consola</span><span class="sxs-lookup"><span data-stu-id="b683a-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="b683a-139">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="b683a-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b683a-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="b683a-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="b683a-141">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="b683a-141">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="b683a-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="b683a-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




