---
title: GetConsoleAliasesLength función)
description: Recupera el tamaño necesario para el búfer usado por la función GetConsoleAliases.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleAliasesLength
- wincon/GetConsoleAliasesLength
- GetConsoleAliasesLength
- consoleapi3/GetConsoleAliasesLengthA
- wincon/GetConsoleAliasesLengthA
- GetConsoleAliasesLengthA
- consoleapi3/GetConsoleAliasesLengthW
- wincon/GetConsoleAliasesLengthW
- GetConsoleAliasesLengthW
MS-HAID:
- base.getconsolealiaseslength
- consoles.getconsolealiaseslength
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 29e49eba-0864-4ed7-af82-1ba639261c40
topic_type:
- apiref
api_name:
- GetConsoleAliasesLength
- GetConsoleAliasesLengthA
- GetConsoleAliasesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 23d820574aab837c89f2598e9934536b91715426
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060709"
---
# <a name="getconsolealiaseslength-function"></a><span data-ttu-id="91717-104">GetConsoleAliasesLength función)</span><span class="sxs-lookup"><span data-stu-id="91717-104">GetConsoleAliasesLength function</span></span>


<span data-ttu-id="91717-105">Recupera el tamaño necesario para el búfer usado por la función [**GetConsoleAliases**](getconsolealiases.md) .</span><span class="sxs-lookup"><span data-stu-id="91717-105">Retrieves the required size for the buffer used by the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span>

<a name="syntax"></a><span data-ttu-id="91717-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="91717-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

<a name="parameters"></a><span data-ttu-id="91717-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="91717-107">Parameters</span></span>
----------

<span data-ttu-id="91717-108">*lpExeName* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="91717-108">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="91717-109">Nombre del archivo ejecutable cuyos aliases de consola se van a recuperar.</span><span class="sxs-lookup"><span data-stu-id="91717-109">The name of the executable file whose console aliases are to be retrieved.</span></span>

<a name="return-value"></a><span data-ttu-id="91717-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="91717-110">Return value</span></span>
------------

<span data-ttu-id="91717-111">Tamaño del búfer necesario para almacenar todos los alias de la consola definidos para este archivo ejecutable, en bytes.</span><span class="sxs-lookup"><span data-stu-id="91717-111">The size of the buffer required to store all console aliases defined for this executable file, in bytes.</span></span>

<a name="remarks"></a><span data-ttu-id="91717-112">Observaciones</span><span class="sxs-lookup"><span data-stu-id="91717-112">Remarks</span></span>
-------

<span data-ttu-id="91717-113">Para compilar una aplicación que usa esta función, defina \*\* \_ Win32 \_ WinNT\*\* como 0x0501 o posterior.</span><span class="sxs-lookup"><span data-stu-id="91717-113">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="91717-114">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="91717-114">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="91717-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="91717-115">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="91717-116">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="91717-116">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="91717-117">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="91717-117">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="91717-118">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="91717-118">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="91717-119">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="91717-119">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="91717-120">Encabezado</span><span class="sxs-lookup"><span data-stu-id="91717-120">Header</span></span></p></td>
<td><span data-ttu-id="91717-121">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="91717-121">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="91717-122">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="91717-122">Library</span></span></p></td>
<td><span data-ttu-id="91717-123">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="91717-123">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="91717-124">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="91717-124">DLL</span></span></p></td>
<td><span data-ttu-id="91717-125">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="91717-125">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="91717-126">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="91717-126">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="91717-127"><strong>GetConsoleAliasesLengthW</strong> (Unicode) y <strong>GetConsoleAliasesLengthA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="91717-127"><strong>GetConsoleAliasesLengthW</strong> (Unicode) and <strong>GetConsoleAliasesLengthA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="91717-128"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="91717-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="91717-129">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="91717-129">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="91717-130">Alias de la consola</span><span class="sxs-lookup"><span data-stu-id="91717-130">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="91717-131">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="91717-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="91717-132">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="91717-132">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="91717-133">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="91717-133">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="91717-134">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="91717-134">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




