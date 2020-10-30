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
ms.openlocfilehash: 395acba39600fe1a98a80ed06ea23646b0b9f174
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038963"
---
# <a name="getconsolealiaseslength-function"></a><span data-ttu-id="b0b2a-104">GetConsoleAliasesLength función)</span><span class="sxs-lookup"><span data-stu-id="b0b2a-104">GetConsoleAliasesLength function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="b0b2a-105">Recupera el tamaño necesario para el búfer usado por la función [**GetConsoleAliases**](getconsolealiases.md) .</span><span class="sxs-lookup"><span data-stu-id="b0b2a-105">Retrieves the required size for the buffer used by the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0b2a-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b0b2a-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="b0b2a-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b0b2a-107">Parameters</span></span>

<span data-ttu-id="b0b2a-108">*lpExeName* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="b0b2a-108">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="b0b2a-109">Nombre del archivo ejecutable cuyos aliases de consola se van a recuperar.</span><span class="sxs-lookup"><span data-stu-id="b0b2a-109">The name of the executable file whose console aliases are to be retrieved.</span></span>

## <a name="return-value"></a><span data-ttu-id="b0b2a-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="b0b2a-110">Return value</span></span>

<span data-ttu-id="b0b2a-111">Tamaño del búfer necesario para almacenar todos los alias de la consola definidos para este archivo ejecutable, en bytes.</span><span class="sxs-lookup"><span data-stu-id="b0b2a-111">The size of the buffer required to store all console aliases defined for this executable file, in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0b2a-112">Comentarios</span><span class="sxs-lookup"><span data-stu-id="b0b2a-112">Remarks</span></span>

<span data-ttu-id="b0b2a-113">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0501 o posterior.</span><span class="sxs-lookup"><span data-stu-id="b0b2a-113">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="b0b2a-114">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="b0b2a-114">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="b0b2a-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b0b2a-115">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b0b2a-116">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="b0b2a-116">Minimum supported client</span></span> | <span data-ttu-id="b0b2a-117">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="b0b2a-117">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="b0b2a-118">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="b0b2a-118">Minimum supported server</span></span> | <span data-ttu-id="b0b2a-119">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="b0b2a-119">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="b0b2a-120">Encabezado</span><span class="sxs-lookup"><span data-stu-id="b0b2a-120">Header</span></span> | <span data-ttu-id="b0b2a-121">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b0b2a-121">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="b0b2a-122">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="b0b2a-122">Library</span></span> | <span data-ttu-id="b0b2a-123">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="b0b2a-123">Kernel32.lib</span></span> |
| <span data-ttu-id="b0b2a-124">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="b0b2a-124">DLL</span></span> | <span data-ttu-id="b0b2a-125">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b0b2a-125">Kernel32.dll</span></span> |
| <span data-ttu-id="b0b2a-126">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="b0b2a-126">Unicode and ANSI names</span></span> | <span data-ttu-id="b0b2a-127">**GetConsoleAliasesLengthW** (Unicode) y **GetConsoleAliasesLengthA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="b0b2a-127">**GetConsoleAliasesLengthW** (Unicode) and **GetConsoleAliasesLengthA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="b0b2a-128">Consulte también</span><span class="sxs-lookup"><span data-stu-id="b0b2a-128">See also</span></span>

[<span data-ttu-id="b0b2a-129">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="b0b2a-129">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="b0b2a-130">Alias de la consola</span><span class="sxs-lookup"><span data-stu-id="b0b2a-130">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="b0b2a-131">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="b0b2a-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b0b2a-132">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="b0b2a-132">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="b0b2a-133">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="b0b2a-133">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="b0b2a-134">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="b0b2a-134">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
