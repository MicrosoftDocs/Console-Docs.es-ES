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
ms.openlocfilehash: d3706ddb86c270aeaf22f46e08e5381c79fea0bb
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357545"
---
# <a name="getconsolealias-function"></a><span data-ttu-id="7dc13-104">GetConsoleAlias función)</span><span class="sxs-lookup"><span data-stu-id="7dc13-104">GetConsoleAlias function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="7dc13-105">Recupera el texto para el archivo ejecutable y el alias de consola especificados.</span><span class="sxs-lookup"><span data-stu-id="7dc13-105">Retrieves the text for the specified console alias and executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="7dc13-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7dc13-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAlias(
  _In_  LPTSTR lpSource,
  _Out_ LPTSTR lpTargetBuffer,
  _In_  DWORD  TargetBufferLength,
  _In_  LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="7dc13-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7dc13-107">Parameters</span></span>

<span data-ttu-id="7dc13-108">*lpSource* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="7dc13-108">*lpSource* \[in\]</span></span>  
<span data-ttu-id="7dc13-109">El alias de la consola cuyo texto se va a recuperar.</span><span class="sxs-lookup"><span data-stu-id="7dc13-109">The console alias whose text is to be retrieved.</span></span>

<span data-ttu-id="7dc13-110">*lpTargetBuffer* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="7dc13-110">*lpTargetBuffer* \[out\]</span></span>  
<span data-ttu-id="7dc13-111">Un puntero a un búfer que recibe el texto asociado al alias de la consola.</span><span class="sxs-lookup"><span data-stu-id="7dc13-111">A pointer to a buffer that receives the text associated with the console alias.</span></span>

<span data-ttu-id="7dc13-112">*TargetBufferLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="7dc13-112">*TargetBufferLength* \[in\]</span></span>  
<span data-ttu-id="7dc13-113">Tamaño del búfer al que apunta *lpTargetBuffer*, en bytes.</span><span class="sxs-lookup"><span data-stu-id="7dc13-113">The size of the buffer pointed to by *lpTargetBuffer*, in bytes.</span></span>

<span data-ttu-id="7dc13-114">*lpExeName* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="7dc13-114">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="7dc13-115">Nombre del archivo ejecutable.</span><span class="sxs-lookup"><span data-stu-id="7dc13-115">The name of the executable file.</span></span>

## <a name="return-value"></a><span data-ttu-id="7dc13-116">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="7dc13-116">Return value</span></span>

<span data-ttu-id="7dc13-117">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="7dc13-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="7dc13-118">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="7dc13-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="7dc13-119">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="7dc13-119">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="7dc13-120">Comentarios</span><span class="sxs-lookup"><span data-stu-id="7dc13-120">Remarks</span></span>

<span data-ttu-id="7dc13-121">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0501 o posterior.</span><span class="sxs-lookup"><span data-stu-id="7dc13-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="7dc13-122">Para obtener más información, consulte [uso de los encabezados de Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="7dc13-122">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="7dc13-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7dc13-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="7dc13-124">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="7dc13-124">Minimum supported client</span></span> | <span data-ttu-id="7dc13-125">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="7dc13-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="7dc13-126">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="7dc13-126">Minimum supported server</span></span> | <span data-ttu-id="7dc13-127">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="7dc13-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="7dc13-128">Encabezado</span><span class="sxs-lookup"><span data-stu-id="7dc13-128">Header</span></span> | <span data-ttu-id="7dc13-129">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="7dc13-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="7dc13-130">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="7dc13-130">Library</span></span> | <span data-ttu-id="7dc13-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="7dc13-131">Kernel32.lib</span></span> |
| <span data-ttu-id="7dc13-132">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="7dc13-132">DLL</span></span> | <span data-ttu-id="7dc13-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7dc13-133">Kernel32.dll</span></span> |
| <span data-ttu-id="7dc13-134">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="7dc13-134">Unicode and ANSI names</span></span> | <span data-ttu-id="7dc13-135">**GetConsoleAliasW** (Unicode) y **GetConsoleAliasA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="7dc13-135">**GetConsoleAliasW** (Unicode) and **GetConsoleAliasA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="7dc13-136">Consulte también</span><span class="sxs-lookup"><span data-stu-id="7dc13-136">See also</span></span>

[<span data-ttu-id="7dc13-137">Alias de la consola</span><span class="sxs-lookup"><span data-stu-id="7dc13-137">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="7dc13-138">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="7dc13-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="7dc13-139">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="7dc13-139">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="7dc13-140">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="7dc13-140">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="7dc13-141">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="7dc13-141">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)