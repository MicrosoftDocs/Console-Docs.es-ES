---
title: GetConsoleAliasExesLength función)
description: Recupera el tamaño necesario para el búfer usado por la función GetConsoleAliasExes.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapie/GetConsoleAliasExesLength
- wincon/GetConsoleAliasExesLength
- GetConsoleAliasExesLength
- consoleapie/GetConsoleAliasExesLengthA
- wincon/GetConsoleAliasExesLengthA
- GetConsoleAliasExesLengthA
- consoleapie/GetConsoleAliasExesLengthW
- wincon/GetConsoleAliasExesLengthW
- GetConsoleAliasExesLengthW
MS-HAID:
- base.getconsolealiasexeslength
- consoles.getconsolealiasexeslength
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 4f23bbb1-3e43-47a9-b91a-e91529b07fb5
topic_type:
- apiref
api_name:
- GetConsoleAliasExesLength
- GetConsoleAliasExesLengthA
- GetConsoleAliasExesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0f4459254e9382a0c784ceb2c214af056087ab1b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060705"
---
# <a name="getconsolealiasexeslength-function"></a><span data-ttu-id="ca109-104">GetConsoleAliasExesLength función)</span><span class="sxs-lookup"><span data-stu-id="ca109-104">GetConsoleAliasExesLength function</span></span>


<span data-ttu-id="ca109-105">Recupera el tamaño necesario para el búfer usado por la función [**GetConsoleAliasExes**](getconsolealiasexes.md) .</span><span class="sxs-lookup"><span data-stu-id="ca109-105">Retrieves the required size for the buffer used by the [**GetConsoleAliasExes**](getconsolealiasexes.md) function.</span></span>

<a name="syntax"></a><span data-ttu-id="ca109-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ca109-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliasExesLength(void);
```

<a name="parameters"></a><span data-ttu-id="ca109-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ca109-107">Parameters</span></span>
----------

<span data-ttu-id="ca109-108">Esta función no tiene parámetros.</span><span class="sxs-lookup"><span data-stu-id="ca109-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="ca109-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="ca109-109">Return value</span></span>
------------

<span data-ttu-id="ca109-110">Tamaño del búfer necesario para almacenar los nombres de todos los archivos ejecutables que tienen definidos alias de consola, en bytes.</span><span class="sxs-lookup"><span data-stu-id="ca109-110">The size of the buffer required to store the names of all executable files that have console aliases defined, in bytes.</span></span>

<a name="remarks"></a><span data-ttu-id="ca109-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="ca109-111">Remarks</span></span>
-------

<span data-ttu-id="ca109-112">Para compilar una aplicación que usa esta función, defina \*\* \_ Win32 \_ WinNT\*\* como 0x0501 o posterior.</span><span class="sxs-lookup"><span data-stu-id="ca109-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="ca109-113">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="ca109-113">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="ca109-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca109-114">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="ca109-115">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="ca109-115">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="ca109-116">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="ca109-116">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ca109-117">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="ca109-117">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="ca109-118">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="ca109-118">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ca109-119">Encabezado</span><span class="sxs-lookup"><span data-stu-id="ca109-119">Header</span></span></p></td>
<td><span data-ttu-id="ca109-120">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ca109-120">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ca109-121">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="ca109-121">Library</span></span></p></td>
<td><span data-ttu-id="ca109-122">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="ca109-122">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ca109-123">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="ca109-123">DLL</span></span></p></td>
<td><span data-ttu-id="ca109-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ca109-124">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ca109-125">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="ca109-125">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="ca109-126"><strong>GetConsoleAliasExesLengthW</strong> (Unicode) y <strong>GetConsoleAliasExesLengthA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="ca109-126"><strong>GetConsoleAliasExesLengthW</strong> (Unicode) and <strong>GetConsoleAliasExesLengthA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="ca109-127"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="ca109-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="ca109-128">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="ca109-128">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="ca109-129">Alias de la consola</span><span class="sxs-lookup"><span data-stu-id="ca109-129">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="ca109-130">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="ca109-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ca109-131">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="ca109-131">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="ca109-132">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="ca109-132">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="ca109-133">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="ca109-133">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




