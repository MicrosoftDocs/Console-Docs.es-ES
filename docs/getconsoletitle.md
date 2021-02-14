---
title: GetConsoleTitle función)
description: Recupera el título y el tamaño del título de la ventana de la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/GetConsoleTitle
- wincon/GetConsoleTitle
- GetConsoleTitle
- consoleapi2/GetConsoleTitleA
- wincon/GetConsoleTitleA
- GetConsoleTitleA
- consoleapi2/GetConsoleTitleW
- wincon/GetConsoleTitleW
- GetConsoleTitleW
MS-HAID:
- '\_win32\_getconsoletitle'
- base.getconsoletitle
- consoles.getconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c58bba36-9813-4bdc-83bf-30d55f8d7d79
topic_type:
- apiref
api_name:
- GetConsoleTitle
- GetConsoleTitleA
- GetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-Ms-Win-Core-Console-Ansi-L2-1-0.dll
- Kernel32Legacy.dll
api_type:
- DllExport
ms.openlocfilehash: 6a4c4634316442ac2b03602b6c931b05385d77df
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358335"
---
# <a name="getconsoletitle-function"></a><span data-ttu-id="0fe61-104">GetConsoleTitle función)</span><span class="sxs-lookup"><span data-stu-id="0fe61-104">GetConsoleTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="0fe61-105">Recupera el título de la ventana de la consola actual.</span><span class="sxs-lookup"><span data-stu-id="0fe61-105">Retrieves the title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="0fe61-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0fe61-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a><span data-ttu-id="0fe61-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0fe61-107">Parameters</span></span>

<span data-ttu-id="0fe61-108">*lpConsoleTitle* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="0fe61-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="0fe61-109">Un puntero a un búfer que recibe una cadena terminada en null que contiene el título.</span><span class="sxs-lookup"><span data-stu-id="0fe61-109">A pointer to a buffer that receives a null-terminated string containing the title.</span></span> <span data-ttu-id="0fe61-110">Si el búfer es demasiado pequeño para almacenar el título, la función almacena tantos caracteres del título como quepan en el búfer, terminando con un terminador null.</span><span class="sxs-lookup"><span data-stu-id="0fe61-110">If the buffer is too small to store the title, the function stores as many characters of the title as will fit in the buffer, ending with a null terminator.</span></span>

<span data-ttu-id="0fe61-111">*nSize* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="0fe61-111">*nSize* \[in\]</span></span>  
<span data-ttu-id="0fe61-112">Tamaño del búfer al que apunta el parámetro *lpConsoleTitle* , en caracteres.</span><span class="sxs-lookup"><span data-stu-id="0fe61-112">The size of the buffer pointed to by the *lpConsoleTitle* parameter, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="0fe61-113">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0fe61-113">Return value</span></span>

<span data-ttu-id="0fe61-114">Si la función se ejecuta correctamente, el valor devuelto es la longitud del título de la ventana de la consola, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="0fe61-114">If the function succeeds, the return value is the length of the console window's title, in characters.</span></span>

<span data-ttu-id="0fe61-115">Si se produce un error en la función, el valor devuelto es cero y [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) devuelve el código de error.</span><span class="sxs-lookup"><span data-stu-id="0fe61-115">If the function fails, the return value is zero and [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) returns the error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0fe61-116">Comentarios</span><span class="sxs-lookup"><span data-stu-id="0fe61-116">Remarks</span></span>

<span data-ttu-id="0fe61-117">Para establecer el título de una ventana de la consola, use la función [**SetConsoleTitle**](setconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="0fe61-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="0fe61-118">Para recuperar la cadena de título original, utilice la función [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) .</span><span class="sxs-lookup"><span data-stu-id="0fe61-118">To retrieve the original title string, use the [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="0fe61-119">No se recomienda esta API y no tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente.</span><span class="sxs-lookup"><span data-stu-id="0fe61-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="0fe61-120">Esta decisión alinea intencionadamente la plataforma de Windows con otros sistemas operativos.</span><span class="sxs-lookup"><span data-stu-id="0fe61-120">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="0fe61-121">Es posible que las aplicaciones remotas mediante utilidades y transportes multiplataforma como SSH no funcionen según lo esperado si se usa esta API.</span><span class="sxs-lookup"><span data-stu-id="0fe61-121">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="examples"></a><span data-ttu-id="0fe61-122">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="0fe61-122">Examples</span></span>

<span data-ttu-id="0fe61-123">Para obtener un ejemplo, vea [**SetConsoleTitle**](setconsoletitle.md).</span><span class="sxs-lookup"><span data-stu-id="0fe61-123">For an example, see [**SetConsoleTitle**](setconsoletitle.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="0fe61-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0fe61-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="0fe61-125">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="0fe61-125">Minimum supported client</span></span> | <span data-ttu-id="0fe61-126">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="0fe61-126">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="0fe61-127">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="0fe61-127">Minimum supported server</span></span> | <span data-ttu-id="0fe61-128">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="0fe61-128">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="0fe61-129">Encabezado</span><span class="sxs-lookup"><span data-stu-id="0fe61-129">Header</span></span> | <span data-ttu-id="0fe61-130">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="0fe61-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="0fe61-131">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="0fe61-131">Library</span></span> | <span data-ttu-id="0fe61-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="0fe61-132">Kernel32.lib</span></span> |
| <span data-ttu-id="0fe61-133">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="0fe61-133">DLL</span></span> | <span data-ttu-id="0fe61-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0fe61-134">Kernel32.dll</span></span> |
| <span data-ttu-id="0fe61-135">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="0fe61-135">Unicode and ANSI names</span></span> | <span data-ttu-id="0fe61-136">**GetConsoleTitleW** (Unicode) y **GetConsoleTitleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="0fe61-136">**GetConsoleTitleW** (Unicode) and **GetConsoleTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="0fe61-137">Vea también</span><span class="sxs-lookup"><span data-stu-id="0fe61-137">See also</span></span>

[<span data-ttu-id="0fe61-138">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="0fe61-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0fe61-139">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="0fe61-139">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="0fe61-140">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="0fe61-140">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="0fe61-141">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="0fe61-141">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="0fe61-142">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="0fe61-142">**SetConsoleTitle**</span></span>](setconsoletitle.md)