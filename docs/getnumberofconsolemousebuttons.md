---
title: GetNumberOfConsoleMouseButtons función)
description: Recupera el número de botones del mouse que usa la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetNumberOfConsoleMouseButtons
- wincon/GetNumberOfConsoleMouseButtons
- GetNumberOfConsoleMouseButtons
MS-HAID:
- '\_win32\_getnumberofconsolemousebuttons'
- base.getnumberofconsolemousebuttons
- consoles.getnumberofconsolemousebuttons
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2
topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 4a2f936ac778b13985aa0c1d237c59e9f993d995
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358855"
---
# <a name="getnumberofconsolemousebuttons-function"></a><span data-ttu-id="152f8-104">GetNumberOfConsoleMouseButtons función)</span><span class="sxs-lookup"><span data-stu-id="152f8-104">GetNumberOfConsoleMouseButtons function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="152f8-105">Recupera el número de botones del mouse que usa la consola actual.</span><span class="sxs-lookup"><span data-stu-id="152f8-105">Retrieves the number of buttons on the mouse used by the current console.</span></span>

## <a name="syntax"></a><span data-ttu-id="152f8-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="152f8-106">Syntax</span></span>

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

## <a name="parameters"></a><span data-ttu-id="152f8-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="152f8-107">Parameters</span></span>

<span data-ttu-id="152f8-108">*lpNumberOfMouseButtons* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="152f8-108">*lpNumberOfMouseButtons* \[out\]</span></span>  
<span data-ttu-id="152f8-109">Puntero a una variable que recibe el número de botones del mouse.</span><span class="sxs-lookup"><span data-stu-id="152f8-109">A pointer to a variable that receives the number of mouse buttons.</span></span>

## <a name="return-value"></a><span data-ttu-id="152f8-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="152f8-110">Return value</span></span>

<span data-ttu-id="152f8-111">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="152f8-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="152f8-112">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="152f8-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="152f8-113">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="152f8-113">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="152f8-114">Comentarios</span><span class="sxs-lookup"><span data-stu-id="152f8-114">Remarks</span></span>

<span data-ttu-id="152f8-115">Cuando una consola recibe la entrada del mouse, una estructura de [**\_ registro de entrada**](input-record-str.md) que contiene una estructura de [**\_ \_ registro de eventos del mouse**](mouse-event-record-str.md) se coloca en el búfer de entrada de la consola.</span><span class="sxs-lookup"><span data-stu-id="152f8-115">When a console receives mouse input, an [**INPUT\_RECORD**](input-record-str.md) structure containing a [**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md) structure is placed in the console's input buffer.</span></span> <span data-ttu-id="152f8-116">El miembro **dwButtonState** del **\_ \_ registro de eventos del mouse** tiene un bit que indica el estado de cada botón del mouse.</span><span class="sxs-lookup"><span data-stu-id="152f8-116">The **dwButtonState** member of **MOUSE\_EVENT\_RECORD** has a bit indicating the state of each mouse button.</span></span> <span data-ttu-id="152f8-117">El bit es 1 si el botón está presionado y 0 si el botón está activo.</span><span class="sxs-lookup"><span data-stu-id="152f8-117">The bit is 1 if the button is down and 0 if the button is up.</span></span> <span data-ttu-id="152f8-118">Para determinar el número de bits que son significativos, use **GetNumberOfConsoleMouseButtons**.</span><span class="sxs-lookup"><span data-stu-id="152f8-118">To determine the number of bits that are significant, use **GetNumberOfConsoleMouseButtons**.</span></span>

> [!TIP]
> <span data-ttu-id="152f8-119">No se recomienda esta API y no tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente.</span><span class="sxs-lookup"><span data-stu-id="152f8-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="152f8-120">Esta decisión alinea intencionadamente la plataforma de Windows con otros sistemas operativos.</span><span class="sxs-lookup"><span data-stu-id="152f8-120">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="152f8-121">Este estado solo es relevante para el usuario local, la sesión y el contexto de privilegios.</span><span class="sxs-lookup"><span data-stu-id="152f8-121">This state is only relevant to the local user, session, and privilege context.</span></span> <span data-ttu-id="152f8-122">Es posible que las aplicaciones remotas mediante utilidades y transportes multiplataforma como SSH no funcionen según lo esperado si se usa esta API.</span><span class="sxs-lookup"><span data-stu-id="152f8-122">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="152f8-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="152f8-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="152f8-124">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="152f8-124">Minimum supported client</span></span> | <span data-ttu-id="152f8-125">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="152f8-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="152f8-126">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="152f8-126">Minimum supported server</span></span> | <span data-ttu-id="152f8-127">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="152f8-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="152f8-128">Encabezado</span><span class="sxs-lookup"><span data-stu-id="152f8-128">Header</span></span> | <span data-ttu-id="152f8-129">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="152f8-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="152f8-130">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="152f8-130">Library</span></span> | <span data-ttu-id="152f8-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="152f8-131">Kernel32.lib</span></span> |
| <span data-ttu-id="152f8-132">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="152f8-132">DLL</span></span> | <span data-ttu-id="152f8-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="152f8-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="152f8-134">Vea también</span><span class="sxs-lookup"><span data-stu-id="152f8-134">See also</span></span>

[<span data-ttu-id="152f8-135">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="152f8-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="152f8-136">Búfer de entrada de la consola</span><span class="sxs-lookup"><span data-stu-id="152f8-136">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="152f8-137">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="152f8-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="152f8-138">**registro de entrada \_**</span><span class="sxs-lookup"><span data-stu-id="152f8-138">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="152f8-139">**\_registro de eventos del mouse \_**</span><span class="sxs-lookup"><span data-stu-id="152f8-139">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)