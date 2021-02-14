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
ms.openlocfilehash: 1a97df0c22f084389e9bd6df1c4a2e8863090b45
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357501"
---
# <a name="getconsolealiasexes-function"></a><span data-ttu-id="b8ded-104">GetConsoleAliasExes función)</span><span class="sxs-lookup"><span data-stu-id="b8ded-104">GetConsoleAliasExes function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="b8ded-105">Recupera los nombres de todos los archivos ejecutables con alias de consola definidos.</span><span class="sxs-lookup"><span data-stu-id="b8ded-105">Retrieves the names of all executable files with console aliases defined.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8ded-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b8ded-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasExes(
  _Out_ LPTSTR lpExeNameBuffer,
  _In_  DWORD  ExeNameBufferLength
);
```

## <a name="parameters"></a><span data-ttu-id="b8ded-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b8ded-107">Parameters</span></span>

<span data-ttu-id="b8ded-108">*lpExeNameBuffer* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="b8ded-108">*lpExeNameBuffer* \[out\]</span></span>  
<span data-ttu-id="b8ded-109">Un puntero a un búfer que recibe los nombres de los archivos ejecutables.</span><span class="sxs-lookup"><span data-stu-id="b8ded-109">A pointer to a buffer that receives the names of the executable files.</span></span>

<span data-ttu-id="b8ded-110">*ExeNameBufferLength* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="b8ded-110">*ExeNameBufferLength* \[in\]</span></span>  
<span data-ttu-id="b8ded-111">Tamaño del búfer al que apunta *lpExeNameBuffer*, en bytes.</span><span class="sxs-lookup"><span data-stu-id="b8ded-111">The size of the buffer pointed to by *lpExeNameBuffer*, in bytes.</span></span>

## <a name="return-value"></a><span data-ttu-id="b8ded-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="b8ded-112">Return value</span></span>

<span data-ttu-id="b8ded-113">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="b8ded-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b8ded-114">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="b8ded-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b8ded-115">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="b8ded-115">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="b8ded-116">Comentarios</span><span class="sxs-lookup"><span data-stu-id="b8ded-116">Remarks</span></span>

<span data-ttu-id="b8ded-117">Para determinar el tamaño necesario para el búfer de *lpExeNameBuffer* , use la función [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) .</span><span class="sxs-lookup"><span data-stu-id="b8ded-117">To determine the required size for the *lpExeNameBuffer* buffer, use the [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) function.</span></span>

<span data-ttu-id="b8ded-118">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0501 o posterior.</span><span class="sxs-lookup"><span data-stu-id="b8ded-118">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="b8ded-119">Para obtener más información, consulte [uso de los encabezados de Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="b8ded-119">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="b8ded-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8ded-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b8ded-121">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="b8ded-121">Minimum supported client</span></span> | <span data-ttu-id="b8ded-122">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="b8ded-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="b8ded-123">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="b8ded-123">Minimum supported server</span></span> | <span data-ttu-id="b8ded-124">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="b8ded-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="b8ded-125">Encabezado</span><span class="sxs-lookup"><span data-stu-id="b8ded-125">Header</span></span> | <span data-ttu-id="b8ded-126">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b8ded-126">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="b8ded-127">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="b8ded-127">Library</span></span> | <span data-ttu-id="b8ded-128">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="b8ded-128">Kernel32.lib</span></span> |
| <span data-ttu-id="b8ded-129">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="b8ded-129">DLL</span></span> | <span data-ttu-id="b8ded-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b8ded-130">Kernel32.dll</span></span> |
| <span data-ttu-id="b8ded-131">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="b8ded-131">Unicode and ANSI names</span></span> | <span data-ttu-id="b8ded-132">**GetConsoleAliasExesW** (Unicode) y **GetConsoleAliasExesA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="b8ded-132">**GetConsoleAliasExesW** (Unicode) and **GetConsoleAliasExesA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="b8ded-133">Consulte también</span><span class="sxs-lookup"><span data-stu-id="b8ded-133">See also</span></span>

[<span data-ttu-id="b8ded-134">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="b8ded-134">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="b8ded-135">Alias de la consola</span><span class="sxs-lookup"><span data-stu-id="b8ded-135">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="b8ded-136">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="b8ded-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b8ded-137">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="b8ded-137">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="b8ded-138">**GetConsoleAliasExesLength**</span><span class="sxs-lookup"><span data-stu-id="b8ded-138">**GetConsoleAliasExesLength**</span></span>](getconsolealiasexeslength.md)

[<span data-ttu-id="b8ded-139">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="b8ded-139">**GetConsoleAliases**</span></span>](getconsolealiases.md)