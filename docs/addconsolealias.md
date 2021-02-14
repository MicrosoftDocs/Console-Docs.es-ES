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
ms.openlocfilehash: 9ff901615fa2a17ee9902bd028a2f63ee6b7a4b4
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357875"
---
# <a name="addconsolealias-function"></a><span data-ttu-id="3713d-104">AddConsoleAlias función)</span><span class="sxs-lookup"><span data-stu-id="3713d-104">AddConsoleAlias function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="3713d-105">Define un alias de consola para el ejecutable especificado.</span><span class="sxs-lookup"><span data-stu-id="3713d-105">Defines a console alias for the specified executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="3713d-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3713d-106">Syntax</span></span>

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

## <a name="parameters"></a><span data-ttu-id="3713d-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3713d-107">Parameters</span></span>

<span data-ttu-id="3713d-108">*Origen* \[ de de\]</span><span class="sxs-lookup"><span data-stu-id="3713d-108">*Source* \[in\]</span></span>  
<span data-ttu-id="3713d-109">El alias de la consola que se va a asignar al texto especificado por el *destino*.</span><span class="sxs-lookup"><span data-stu-id="3713d-109">The console alias to be mapped to the text specified by *Target*.</span></span>

<span data-ttu-id="3713d-110">*Destino* \[ de de\]</span><span class="sxs-lookup"><span data-stu-id="3713d-110">*Target* \[in\]</span></span>  
<span data-ttu-id="3713d-111">Texto que se va a sustituir por el *origen*.</span><span class="sxs-lookup"><span data-stu-id="3713d-111">The text to be substituted for *Source*.</span></span> <span data-ttu-id="3713d-112">Si este parámetro es **null**, se quita el alias de la consola.</span><span class="sxs-lookup"><span data-stu-id="3713d-112">If this parameter is **NULL**, then the console alias is removed.</span></span>

<span data-ttu-id="3713d-113">*ExeName* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="3713d-113">*ExeName* \[in\]</span></span>  
<span data-ttu-id="3713d-114">Nombre del archivo ejecutable para el que se va a definir el alias de la consola.</span><span class="sxs-lookup"><span data-stu-id="3713d-114">The name of the executable file for which the console alias is to be defined.</span></span>

## <a name="return-value"></a><span data-ttu-id="3713d-115">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="3713d-115">Return value</span></span>

<span data-ttu-id="3713d-116">Si la función se ejecuta correctamente, el valor devuelto es **true**.</span><span class="sxs-lookup"><span data-stu-id="3713d-116">If the function succeeds, the return value is **TRUE**.</span></span>

<span data-ttu-id="3713d-117">Si se produce un error en la función, el valor devuelto es **false**.</span><span class="sxs-lookup"><span data-stu-id="3713d-117">If the function fails, the return value is **FALSE**.</span></span> <span data-ttu-id="3713d-118">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="3713d-118">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="3713d-119">Comentarios</span><span class="sxs-lookup"><span data-stu-id="3713d-119">Remarks</span></span>

<span data-ttu-id="3713d-120">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0501 o posterior.</span><span class="sxs-lookup"><span data-stu-id="3713d-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="3713d-121">Para obtener más información, consulte [uso de los encabezados de Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="3713d-121">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="examples"></a><span data-ttu-id="3713d-122">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="3713d-122">Examples</span></span>

<span data-ttu-id="3713d-123">Para obtener un ejemplo, vea [alias de consola](console-aliases.md).</span><span class="sxs-lookup"><span data-stu-id="3713d-123">For an example, see [Console Aliases](console-aliases.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="3713d-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3713d-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="3713d-125">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="3713d-125">Minimum supported client</span></span> | <span data-ttu-id="3713d-126">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="3713d-126">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="3713d-127">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="3713d-127">Minimum supported server</span></span> | <span data-ttu-id="3713d-128">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="3713d-128">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="3713d-129">Encabezado</span><span class="sxs-lookup"><span data-stu-id="3713d-129">Header</span></span> | <span data-ttu-id="3713d-130">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="3713d-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="3713d-131">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="3713d-131">Library</span></span> | <span data-ttu-id="3713d-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="3713d-132">Kernel32.lib</span></span> |
| <span data-ttu-id="3713d-133">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="3713d-133">DLL</span></span> | <span data-ttu-id="3713d-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3713d-134">Kernel32.dll</span></span> |
| <span data-ttu-id="3713d-135">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="3713d-135">Unicode and ANSI names</span></span> | <span data-ttu-id="3713d-136">**AddConsoleAliasW** (Unicode) y **AddConsoleAliasA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="3713d-136">**AddConsoleAliasW** (Unicode) and **AddConsoleAliasA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="3713d-137">Consulte también</span><span class="sxs-lookup"><span data-stu-id="3713d-137">See also</span></span>

[<span data-ttu-id="3713d-138">Alias de la consola</span><span class="sxs-lookup"><span data-stu-id="3713d-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="3713d-139">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="3713d-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3713d-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="3713d-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="3713d-141">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="3713d-141">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="3713d-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="3713d-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)