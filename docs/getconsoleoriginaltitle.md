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
ms.openlocfilehash: 3c4fc202601cec9257b6cf95efdd460c64122b80
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359005"
---
# <a name="getconsoleoriginaltitle-function"></a><span data-ttu-id="4a9d0-104">GetConsoleOriginalTitle función)</span><span class="sxs-lookup"><span data-stu-id="4a9d0-104">GetConsoleOriginalTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="4a9d0-105">Recupera el título original de la ventana de la consola actual.</span><span class="sxs-lookup"><span data-stu-id="4a9d0-105">Retrieves the original title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="4a9d0-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4a9d0-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a><span data-ttu-id="4a9d0-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4a9d0-107">Parameters</span></span>

<span data-ttu-id="4a9d0-108">*lpConsoleTitle* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="4a9d0-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="4a9d0-109">Un puntero a un búfer que recibe una cadena terminada en null que contiene el título original.</span><span class="sxs-lookup"><span data-stu-id="4a9d0-109">A pointer to a buffer that receives a null-terminated string containing the original title.</span></span>

<span data-ttu-id="4a9d0-110">*nSize* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="4a9d0-110">*nSize* \[in\]</span></span>  
<span data-ttu-id="4a9d0-111">Tamaño del búfer de *lpConsoleTitle* , en caracteres.</span><span class="sxs-lookup"><span data-stu-id="4a9d0-111">The size of the *lpConsoleTitle* buffer, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="4a9d0-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4a9d0-112">Return value</span></span>

<span data-ttu-id="4a9d0-113">Si la función se ejecuta correctamente, el valor devuelto es la longitud de la cadena copiada en el búfer, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="4a9d0-113">If the function succeeds, the return value is the length of the string copied to the buffer, in characters.</span></span>

<span data-ttu-id="4a9d0-114">Si el búfer no es lo suficientemente grande como para almacenar el título, el valor devuelto es cero y [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) devuelve el **error \_ Success**.</span><span class="sxs-lookup"><span data-stu-id="4a9d0-114">If the buffer is not large enough to store the title, the return value is zero and [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) returns **ERROR\_SUCCESS**.</span></span>

<span data-ttu-id="4a9d0-115">Si se produce un error en la función, el valor devuelto es cero y [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) devuelve el código de error.</span><span class="sxs-lookup"><span data-stu-id="4a9d0-115">If the function fails, the return value is zero and [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) returns the error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a9d0-116">Comentarios</span><span class="sxs-lookup"><span data-stu-id="4a9d0-116">Remarks</span></span>

<span data-ttu-id="4a9d0-117">Para establecer el título de una ventana de la consola, use la función [**SetConsoleTitle**](setconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="4a9d0-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="4a9d0-118">Para recuperar la cadena de título actual, utilice la función [**GetConsoleTitle**](getconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="4a9d0-118">To retrieve the current title string, use the [**GetConsoleTitle**](getconsoletitle.md) function.</span></span>

<span data-ttu-id="4a9d0-119">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0600 o posterior.</span><span class="sxs-lookup"><span data-stu-id="4a9d0-119">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0600 or later.</span></span> <span data-ttu-id="4a9d0-120">Para obtener más información, consulte [uso de los encabezados de Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="4a9d0-120">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

> [!TIP]
> <span data-ttu-id="4a9d0-121">No se recomienda esta API y no tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente.</span><span class="sxs-lookup"><span data-stu-id="4a9d0-121">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="4a9d0-122">Esta decisión alinea intencionadamente la plataforma de Windows con otros sistemas operativos.</span><span class="sxs-lookup"><span data-stu-id="4a9d0-122">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="4a9d0-123">Es posible que las aplicaciones remotas mediante utilidades y transportes multiplataforma como SSH no funcionen según lo esperado si se usa esta API.</span><span class="sxs-lookup"><span data-stu-id="4a9d0-123">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="4a9d0-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a9d0-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4a9d0-125">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="4a9d0-125">Minimum supported client</span></span> | <span data-ttu-id="4a9d0-126">Solo aplicaciones de escritorio de Windows Vista \[\]</span><span class="sxs-lookup"><span data-stu-id="4a9d0-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="4a9d0-127">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="4a9d0-127">Minimum supported server</span></span> | <span data-ttu-id="4a9d0-128">Solo aplicaciones de escritorio de Windows Server 2008 \[\]</span><span class="sxs-lookup"><span data-stu-id="4a9d0-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="4a9d0-129">Encabezado</span><span class="sxs-lookup"><span data-stu-id="4a9d0-129">Header</span></span> | <span data-ttu-id="4a9d0-130">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="4a9d0-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="4a9d0-131">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="4a9d0-131">Library</span></span> | <span data-ttu-id="4a9d0-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="4a9d0-132">Kernel32.lib</span></span> |
| <span data-ttu-id="4a9d0-133">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="4a9d0-133">DLL</span></span> | <span data-ttu-id="4a9d0-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4a9d0-134">Kernel32.dll</span></span> |
| <span data-ttu-id="4a9d0-135">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="4a9d0-135">Unicode and ANSI names</span></span> | <span data-ttu-id="4a9d0-136">**GetConsoleOriginalTitleW** (Unicode) y **GetConsoleOriginalTitleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="4a9d0-136">**GetConsoleOriginalTitleW** (Unicode) and **GetConsoleOriginalTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="4a9d0-137">Vea también</span><span class="sxs-lookup"><span data-stu-id="4a9d0-137">See also</span></span>

[<span data-ttu-id="4a9d0-138">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="4a9d0-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4a9d0-139">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="4a9d0-139">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="4a9d0-140">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="4a9d0-140">**SetConsoleTitle**</span></span>](setconsoletitle.md)