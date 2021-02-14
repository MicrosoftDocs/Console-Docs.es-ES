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
ms.openlocfilehash: 4285bb64e919851a38494383a440afa6b94c8032
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358475"
---
# <a name="getconsolealiasexeslength-function"></a><span data-ttu-id="3bdfc-104">GetConsoleAliasExesLength función)</span><span class="sxs-lookup"><span data-stu-id="3bdfc-104">GetConsoleAliasExesLength function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="3bdfc-105">Recupera el tamaño necesario para el búfer usado por la función [**GetConsoleAliasExes**](getconsolealiasexes.md) .</span><span class="sxs-lookup"><span data-stu-id="3bdfc-105">Retrieves the required size for the buffer used by the [**GetConsoleAliasExes**](getconsolealiasexes.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="3bdfc-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3bdfc-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasExesLength(void);
```

## <a name="parameters"></a><span data-ttu-id="3bdfc-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3bdfc-107">Parameters</span></span>

<span data-ttu-id="3bdfc-108">Esta función no tiene parámetros.</span><span class="sxs-lookup"><span data-stu-id="3bdfc-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="3bdfc-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="3bdfc-109">Return value</span></span>

<span data-ttu-id="3bdfc-110">Tamaño del búfer necesario para almacenar los nombres de todos los archivos ejecutables que tienen definidos alias de consola, en bytes.</span><span class="sxs-lookup"><span data-stu-id="3bdfc-110">The size of the buffer required to store the names of all executable files that have console aliases defined, in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="3bdfc-111">Comentarios</span><span class="sxs-lookup"><span data-stu-id="3bdfc-111">Remarks</span></span>

<span data-ttu-id="3bdfc-112">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0501 o posterior.</span><span class="sxs-lookup"><span data-stu-id="3bdfc-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="3bdfc-113">Para obtener más información, consulte [uso de los encabezados de Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="3bdfc-113">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="3bdfc-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3bdfc-114">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="3bdfc-115">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="3bdfc-115">Minimum supported client</span></span> | <span data-ttu-id="3bdfc-116">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="3bdfc-116">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="3bdfc-117">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="3bdfc-117">Minimum supported server</span></span> | <span data-ttu-id="3bdfc-118">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="3bdfc-118">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="3bdfc-119">Encabezado</span><span class="sxs-lookup"><span data-stu-id="3bdfc-119">Header</span></span> | <span data-ttu-id="3bdfc-120">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="3bdfc-120">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="3bdfc-121">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="3bdfc-121">Library</span></span> | <span data-ttu-id="3bdfc-122">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="3bdfc-122">Kernel32.lib</span></span> |
| <span data-ttu-id="3bdfc-123">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="3bdfc-123">DLL</span></span> | <span data-ttu-id="3bdfc-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3bdfc-124">Kernel32.dll</span></span> |
| <span data-ttu-id="3bdfc-125">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="3bdfc-125">Unicode and ANSI names</span></span> | <span data-ttu-id="3bdfc-126">**GetConsoleAliasExesLengthW** (Unicode) y **GetConsoleAliasExesLengthA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="3bdfc-126">**GetConsoleAliasExesLengthW** (Unicode) and **GetConsoleAliasExesLengthA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="3bdfc-127">Consulte también</span><span class="sxs-lookup"><span data-stu-id="3bdfc-127">See also</span></span>

[<span data-ttu-id="3bdfc-128">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="3bdfc-128">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="3bdfc-129">Alias de la consola</span><span class="sxs-lookup"><span data-stu-id="3bdfc-129">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="3bdfc-130">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="3bdfc-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3bdfc-131">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="3bdfc-131">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="3bdfc-132">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="3bdfc-132">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="3bdfc-133">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="3bdfc-133">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)