---
title: GetConsoleAliases función)
description: Recupera todos los alias de consola definidos para el ejecutable especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleAliases
- wincon/GetConsoleAliases
- GetConsoleAliases
- consoleapi3/GetConsoleAliasesA
- wincon/GetConsoleAliasesA
- GetConsoleAliasesA
- consoleapi3/GetConsoleAliasesW
- wincon/GetConsoleAliasesW
- GetConsoleAliasesW
MS-HAID:
- base.getconsolealiases
- consoles.getconsolealiases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 92eefa4e-ffde-4886-afde-5aecf450b425
topic_type:
- apiref
api_name:
- GetConsoleAliases
- GetConsoleAliasesA
- GetConsoleAliasesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 9e8e28323d5b696390d574a86561d7414f419bcc
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060713"
---
# <a name="getconsolealiases-function"></a><span data-ttu-id="1e779-104">GetConsoleAliases función)</span><span class="sxs-lookup"><span data-stu-id="1e779-104">GetConsoleAliases function</span></span>


<span data-ttu-id="1e779-105">Recupera todos los alias de consola definidos para el ejecutable especificado.</span><span class="sxs-lookup"><span data-stu-id="1e779-105">Retrieves all defined console aliases for the specified executable.</span></span>

<a name="syntax"></a><span data-ttu-id="1e779-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1e779-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliases(
  _Out_ LPTSTR lpAliasBuffer,
  _In_  DWORD  AliasBufferLength,
  _In_  LPTSTR lpExeName
);
```

<a name="parameters"></a><span data-ttu-id="1e779-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1e779-107">Parameters</span></span>
----------

<span data-ttu-id="1e779-108">*lpAliasBuffer* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="1e779-108">*lpAliasBuffer* \[out\]</span></span>  
<span data-ttu-id="1e779-109">Un puntero a un búfer que recibe los alias.</span><span class="sxs-lookup"><span data-stu-id="1e779-109">A pointer to a buffer that receives the aliases.</span></span>

<span data-ttu-id="1e779-110">El formato de los datos es el siguiente: *Source1* = *Target1* \\ 0*source2* = *TARGET2* \\ 0... *Código fuente* = *Destino* \\ 0, donde *N* es el número de alias de consola definidos.</span><span class="sxs-lookup"><span data-stu-id="1e779-110">The format of the data is as follows: *Source1*=*Target1*\\0*Source2*=*Target2*\\0... *SourceN*=*TargetN*\\0, where *N* is the number of console aliases defined.</span></span>

<span data-ttu-id="1e779-111">*AliasBufferLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="1e779-111">*AliasBufferLength* \[in\]</span></span>  
<span data-ttu-id="1e779-112">Tamaño del búfer al que apunta *lpAliasBuffer*, en bytes.</span><span class="sxs-lookup"><span data-stu-id="1e779-112">The size of the buffer pointed to by *lpAliasBuffer*, in bytes.</span></span>

<span data-ttu-id="1e779-113">*lpExeName* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="1e779-113">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="1e779-114">Archivo ejecutable cuyos alias se van a recuperar.</span><span class="sxs-lookup"><span data-stu-id="1e779-114">The executable file whose aliases are to be retrieved.</span></span>

<a name="return-value"></a><span data-ttu-id="1e779-115">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1e779-115">Return value</span></span>
------------

<span data-ttu-id="1e779-116">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="1e779-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="1e779-117">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="1e779-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="1e779-118">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="1e779-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="1e779-119">Observaciones</span><span class="sxs-lookup"><span data-stu-id="1e779-119">Remarks</span></span>
-------

<span data-ttu-id="1e779-120">Para determinar el tamaño necesario para el búfer de *lpExeName* , use la función [**GetConsoleAliasesLength**](getconsolealiaseslength.md) .</span><span class="sxs-lookup"><span data-stu-id="1e779-120">To determine the required size for the *lpExeName* buffer, use the [**GetConsoleAliasesLength**](getconsolealiaseslength.md) function.</span></span>

<span data-ttu-id="1e779-121">Para compilar una aplicación que usa esta función, defina \*\* \_ Win32 \_ WinNT\*\* como 0x0501 o posterior.</span><span class="sxs-lookup"><span data-stu-id="1e779-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="1e779-122">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="1e779-122">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="1e779-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1e779-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="1e779-124">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="1e779-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="1e779-125">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="1e779-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1e779-126">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="1e779-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="1e779-127">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="1e779-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1e779-128">Encabezado</span><span class="sxs-lookup"><span data-stu-id="1e779-128">Header</span></span></p></td>
<td><span data-ttu-id="1e779-129">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="1e779-129">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1e779-130">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="1e779-130">Library</span></span></p></td>
<td><span data-ttu-id="1e779-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="1e779-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="1e779-132">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="1e779-132">DLL</span></span></p></td>
<td><span data-ttu-id="1e779-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1e779-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="1e779-134">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="1e779-134">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="1e779-135"><strong>GetConsoleAliasesW</strong> (Unicode) y <strong>GetConsoleAliasesA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="1e779-135"><strong>GetConsoleAliasesW</strong> (Unicode) and <strong>GetConsoleAliasesA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="1e779-136"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="1e779-136"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="1e779-137">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="1e779-137">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="1e779-138">Alias de la consola</span><span class="sxs-lookup"><span data-stu-id="1e779-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="1e779-139">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="1e779-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1e779-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="1e779-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="1e779-141">**GetConsoleAliasesLength**</span><span class="sxs-lookup"><span data-stu-id="1e779-141">**GetConsoleAliasesLength**</span></span>](getconsolealiaseslength.md)

[<span data-ttu-id="1e779-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="1e779-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




