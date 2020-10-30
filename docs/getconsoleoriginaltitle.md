---
title: GetConsoleOriginalTitle función)
description: Vea la información de referencia sobre la función GetConsoleOriginalTitle, que recupera el título original de la ventana de la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: ad12ff7b931b6bbc36a7fb0e9e0ee2ac3512a1f5
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038003"
---
# <a name="getconsoleoriginaltitle-function"></a><span data-ttu-id="5d1ac-104">GetConsoleOriginalTitle función)</span><span class="sxs-lookup"><span data-stu-id="5d1ac-104">GetConsoleOriginalTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="5d1ac-105">Recupera el título original de la ventana de la consola actual.</span><span class="sxs-lookup"><span data-stu-id="5d1ac-105">Retrieves the original title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d1ac-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5d1ac-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a><span data-ttu-id="5d1ac-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5d1ac-107">Parameters</span></span>

<span data-ttu-id="5d1ac-108">*lpConsoleTitle* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="5d1ac-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="5d1ac-109">Un puntero a un búfer que recibe una cadena terminada en null que contiene el título original.</span><span class="sxs-lookup"><span data-stu-id="5d1ac-109">A pointer to a buffer that receives a null-terminated string containing the original title.</span></span>

<span data-ttu-id="5d1ac-110">*nSize* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="5d1ac-110">*nSize* \[in\]</span></span>  
<span data-ttu-id="5d1ac-111">Tamaño del búfer de *lpConsoleTitle* , en caracteres.</span><span class="sxs-lookup"><span data-stu-id="5d1ac-111">The size of the *lpConsoleTitle* buffer, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="5d1ac-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="5d1ac-112">Return value</span></span>

<span data-ttu-id="5d1ac-113">Si la función se ejecuta correctamente, el valor devuelto es la longitud de la cadena copiada en el búfer, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="5d1ac-113">If the function succeeds, the return value is the length of the string copied to the buffer, in characters.</span></span>

<span data-ttu-id="5d1ac-114">Si el búfer no es lo suficientemente grande como para almacenar el título, el valor devuelto es cero y [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) devuelve el **error \_ Success** .</span><span class="sxs-lookup"><span data-stu-id="5d1ac-114">If the buffer is not large enough to store the title, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns **ERROR\_SUCCESS** .</span></span>

<span data-ttu-id="5d1ac-115">Si se produce un error en la función, el valor devuelto es cero y [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) devuelve el código de error.</span><span class="sxs-lookup"><span data-stu-id="5d1ac-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5d1ac-116">Comentarios</span><span class="sxs-lookup"><span data-stu-id="5d1ac-116">Remarks</span></span>

<span data-ttu-id="5d1ac-117">Para establecer el título de una ventana de la consola, use la función [**SetConsoleTitle**](setconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="5d1ac-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="5d1ac-118">Para recuperar la cadena de título actual, utilice la función [**GetConsoleTitle**](getconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="5d1ac-118">To retrieve the current title string, use the [**GetConsoleTitle**](getconsoletitle.md) function.</span></span>

<span data-ttu-id="5d1ac-119">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0600 o posterior.</span><span class="sxs-lookup"><span data-stu-id="5d1ac-119">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0600 or later.</span></span> <span data-ttu-id="5d1ac-120">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="5d1ac-120">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

> [!TIP]
> <span data-ttu-id="5d1ac-121">No se recomienda esta API y no tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente.</span><span class="sxs-lookup"><span data-stu-id="5d1ac-121">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="5d1ac-122">Esta decisión alinea intencionadamente la plataforma de Windows con otros sistemas operativos.</span><span class="sxs-lookup"><span data-stu-id="5d1ac-122">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="5d1ac-123">Es posible que las aplicaciones remotas mediante utilidades y transportes multiplataforma como SSH no funcionen según lo esperado si se usa esta API.</span><span class="sxs-lookup"><span data-stu-id="5d1ac-123">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="5d1ac-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d1ac-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="5d1ac-125">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="5d1ac-125">Minimum supported client</span></span> | <span data-ttu-id="5d1ac-126">Solo aplicaciones de escritorio de Windows Vista \[\]</span><span class="sxs-lookup"><span data-stu-id="5d1ac-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="5d1ac-127">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="5d1ac-127">Minimum supported server</span></span> | <span data-ttu-id="5d1ac-128">Solo aplicaciones de escritorio de Windows Server 2008 \[\]</span><span class="sxs-lookup"><span data-stu-id="5d1ac-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="5d1ac-129">Encabezado</span><span class="sxs-lookup"><span data-stu-id="5d1ac-129">Header</span></span> | <span data-ttu-id="5d1ac-130">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="5d1ac-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="5d1ac-131">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="5d1ac-131">Library</span></span> | <span data-ttu-id="5d1ac-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="5d1ac-132">Kernel32.lib</span></span> |
| <span data-ttu-id="5d1ac-133">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="5d1ac-133">DLL</span></span> | <span data-ttu-id="5d1ac-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="5d1ac-134">Kernel32.dll</span></span> |
| <span data-ttu-id="5d1ac-135">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="5d1ac-135">Unicode and ANSI names</span></span> | <span data-ttu-id="5d1ac-136">**GetConsoleOriginalTitleW** (Unicode) y **GetConsoleOriginalTitleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="5d1ac-136">**GetConsoleOriginalTitleW** (Unicode) and **GetConsoleOriginalTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="5d1ac-137">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5d1ac-137">See also</span></span>

[<span data-ttu-id="5d1ac-138">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="5d1ac-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="5d1ac-139">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="5d1ac-139">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="5d1ac-140">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="5d1ac-140">**SetConsoleTitle**</span></span>](setconsoletitle.md)
