---
title: GetConsoleAliasExes función)
description: Recupera los nombres de todos los archivos ejecutables con alias de consola definidos.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleAliasExes
- wincon/GetConsoleAliasExes
- GetConsoleAliasExes
- consoleapi3/GetConsoleAliasExesA
- wincon/GetConsoleAliasExesA
- GetConsoleAliasExesA
- consoleapi3/GetConsoleAliasExesW
- wincon/GetConsoleAliasExesW
- GetConsoleAliasExesW
MS-HAID:
- base.getconsolealiasexes
- consoles.getconsolealiasexes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c229de09-cfa6-4829-9c9a-8ff63500eaf4
topic_type:
- apiref
api_name:
- GetConsoleAliasExes
- GetConsoleAliasExesA
- GetConsoleAliasExesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: e112112fc1510ab4c3f0a99ff9b208cc364e361a
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060716"
---
# <a name="getconsolealiasexes-function"></a><span data-ttu-id="c2bfb-104">GetConsoleAliasExes función)</span><span class="sxs-lookup"><span data-stu-id="c2bfb-104">GetConsoleAliasExes function</span></span>


<span data-ttu-id="c2bfb-105">Recupera los nombres de todos los archivos ejecutables con alias de consola definidos.</span><span class="sxs-lookup"><span data-stu-id="c2bfb-105">Retrieves the names of all executable files with console aliases defined.</span></span>

<a name="syntax"></a><span data-ttu-id="c2bfb-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c2bfb-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliasExes(
  _Out_ LPTSTR lpExeNameBuffer,
  _In_  DWORD  ExeNameBufferLength
);
```

<a name="parameters"></a><span data-ttu-id="c2bfb-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="c2bfb-107">Parameters</span></span>
----------

<span data-ttu-id="c2bfb-108">*lpExeNameBuffer* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="c2bfb-108">*lpExeNameBuffer* \[out\]</span></span>  
<span data-ttu-id="c2bfb-109">Un puntero a un búfer que recibe los nombres de los archivos ejecutables.</span><span class="sxs-lookup"><span data-stu-id="c2bfb-109">A pointer to a buffer that receives the names of the executable files.</span></span>

<span data-ttu-id="c2bfb-110">*ExeNameBufferLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="c2bfb-110">*ExeNameBufferLength* \[in\]</span></span>  
<span data-ttu-id="c2bfb-111">Tamaño del búfer al que apunta *lpExeNameBuffer*, en bytes.</span><span class="sxs-lookup"><span data-stu-id="c2bfb-111">The size of the buffer pointed to by *lpExeNameBuffer*, in bytes.</span></span>

<a name="return-value"></a><span data-ttu-id="c2bfb-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="c2bfb-112">Return value</span></span>
------------

<span data-ttu-id="c2bfb-113">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="c2bfb-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c2bfb-114">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="c2bfb-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c2bfb-115">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="c2bfb-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="c2bfb-116">Observaciones</span><span class="sxs-lookup"><span data-stu-id="c2bfb-116">Remarks</span></span>
-------

<span data-ttu-id="c2bfb-117">Para determinar el tamaño necesario para el búfer de *lpExeNameBuffer* , use la función [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) .</span><span class="sxs-lookup"><span data-stu-id="c2bfb-117">To determine the required size for the *lpExeNameBuffer* buffer, use the [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) function.</span></span>

<span data-ttu-id="c2bfb-118">Para compilar una aplicación que usa esta función, defina \*\* \_ Win32 \_ WinNT\*\* como 0x0501 o posterior.</span><span class="sxs-lookup"><span data-stu-id="c2bfb-118">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="c2bfb-119">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="c2bfb-119">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="c2bfb-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2bfb-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="c2bfb-121">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="c2bfb-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="c2bfb-122">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="c2bfb-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c2bfb-123">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="c2bfb-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="c2bfb-124">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="c2bfb-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c2bfb-125">Encabezado</span><span class="sxs-lookup"><span data-stu-id="c2bfb-125">Header</span></span></p></td>
<td><span data-ttu-id="c2bfb-126">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="c2bfb-126">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c2bfb-127">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="c2bfb-127">Library</span></span></p></td>
<td><span data-ttu-id="c2bfb-128">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="c2bfb-128">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c2bfb-129">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="c2bfb-129">DLL</span></span></p></td>
<td><span data-ttu-id="c2bfb-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c2bfb-130">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c2bfb-131">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="c2bfb-131">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="c2bfb-132"><strong>GetConsoleAliasExesW</strong> (Unicode) y <strong>GetConsoleAliasExesA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="c2bfb-132"><strong>GetConsoleAliasExesW</strong> (Unicode) and <strong>GetConsoleAliasExesA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="c2bfb-133"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="c2bfb-133"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="c2bfb-134">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="c2bfb-134">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="c2bfb-135">Alias de la consola</span><span class="sxs-lookup"><span data-stu-id="c2bfb-135">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="c2bfb-136">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="c2bfb-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c2bfb-137">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="c2bfb-137">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="c2bfb-138">**GetConsoleAliasExesLength**</span><span class="sxs-lookup"><span data-stu-id="c2bfb-138">**GetConsoleAliasExesLength**</span></span>](getconsolealiasexeslength.md)

[<span data-ttu-id="c2bfb-139">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="c2bfb-139">**GetConsoleAliases**</span></span>](getconsolealiases.md)

 

 




