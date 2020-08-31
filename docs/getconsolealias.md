---
title: GetConsoleAlias función)
description: Recupera el texto para el alias de consola especificado y el nombre del archivo ejecutable.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleAlias
- wincon/GetConsoleAlias
- GetConsoleAlias
- consoleapi3/GetConsoleAliasA
- wincon/GetConsoleAliasA
- GetConsoleAliasA
- consoleapi3/GetConsoleAliasW
- wincon/GetConsoleAliasW
- GetConsoleAliasW
MS-HAID:
- base.getconsolealias
- consoles.getconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e8514f24-8121-4fad-94bb-c9eedf7a700d
topic_type:
- apiref
api_name:
- GetConsoleAlias
- GetConsoleAliasA
- GetConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 3a7797db4b559e66c1ec30f72e148ff00e79e7aa
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060717"
---
# <a name="getconsolealias-function"></a><span data-ttu-id="56cee-104">GetConsoleAlias función)</span><span class="sxs-lookup"><span data-stu-id="56cee-104">GetConsoleAlias function</span></span>


<span data-ttu-id="56cee-105">Recupera el texto para el archivo ejecutable y el alias de consola especificados.</span><span class="sxs-lookup"><span data-stu-id="56cee-105">Retrieves the text for the specified console alias and executable.</span></span>

<a name="syntax"></a><span data-ttu-id="56cee-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="56cee-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAlias(
  _In_  LPTSTR lpSource,
  _Out_ LPTSTR lpTargetBuffer,
  _In_  DWORD  TargetBufferLength,
  _In_  LPTSTR lpExeName
);
```

<a name="parameters"></a><span data-ttu-id="56cee-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="56cee-107">Parameters</span></span>
----------

<span data-ttu-id="56cee-108">*lpSource* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="56cee-108">*lpSource* \[in\]</span></span>  
<span data-ttu-id="56cee-109">El alias de la consola cuyo texto se va a recuperar.</span><span class="sxs-lookup"><span data-stu-id="56cee-109">The console alias whose text is to be retrieved.</span></span>

<span data-ttu-id="56cee-110">*lpTargetBuffer* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="56cee-110">*lpTargetBuffer* \[out\]</span></span>  
<span data-ttu-id="56cee-111">Un puntero a un búfer que recibe el texto asociado al alias de la consola.</span><span class="sxs-lookup"><span data-stu-id="56cee-111">A pointer to a buffer that receives the text associated with the console alias.</span></span>

<span data-ttu-id="56cee-112">*TargetBufferLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="56cee-112">*TargetBufferLength* \[in\]</span></span>  
<span data-ttu-id="56cee-113">Tamaño del búfer al que apunta *lpTargetBuffer*, en bytes.</span><span class="sxs-lookup"><span data-stu-id="56cee-113">The size of the buffer pointed to by *lpTargetBuffer*, in bytes.</span></span>

<span data-ttu-id="56cee-114">*lpExeName* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="56cee-114">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="56cee-115">Nombre del archivo ejecutable.</span><span class="sxs-lookup"><span data-stu-id="56cee-115">The name of the executable file.</span></span>

<a name="return-value"></a><span data-ttu-id="56cee-116">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="56cee-116">Return value</span></span>
------------

<span data-ttu-id="56cee-117">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="56cee-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="56cee-118">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="56cee-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="56cee-119">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="56cee-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="56cee-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="56cee-120">Remarks</span></span>
-------

<span data-ttu-id="56cee-121">Para compilar una aplicación que usa esta función, defina \*\* \_ Win32 \_ WinNT\*\* como 0x0501 o posterior.</span><span class="sxs-lookup"><span data-stu-id="56cee-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="56cee-122">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="56cee-122">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="56cee-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="56cee-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="56cee-124">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="56cee-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="56cee-125">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="56cee-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="56cee-126">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="56cee-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="56cee-127">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="56cee-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="56cee-128">Encabezado</span><span class="sxs-lookup"><span data-stu-id="56cee-128">Header</span></span></p></td>
<td><span data-ttu-id="56cee-129">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="56cee-129">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="56cee-130">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="56cee-130">Library</span></span></p></td>
<td><span data-ttu-id="56cee-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="56cee-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="56cee-132">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="56cee-132">DLL</span></span></p></td>
<td><span data-ttu-id="56cee-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="56cee-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="56cee-134">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="56cee-134">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="56cee-135"><strong>GetConsoleAliasW</strong> (Unicode) y <strong>GetConsoleAliasA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="56cee-135"><strong>GetConsoleAliasW</strong> (Unicode) and <strong>GetConsoleAliasA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="56cee-136"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="56cee-136"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="56cee-137">Alias de la consola</span><span class="sxs-lookup"><span data-stu-id="56cee-137">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="56cee-138">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="56cee-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="56cee-139">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="56cee-139">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="56cee-140">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="56cee-140">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="56cee-141">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="56cee-141">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 




