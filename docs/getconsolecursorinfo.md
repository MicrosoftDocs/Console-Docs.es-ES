---
title: GetConsoleCursorInfo función)
description: Recupera información sobre el tamaño y la visibilidad del cursor para el búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/GetConsoleCursorInfo
- wincon/GetConsoleCursorInfo
- GetConsoleCursorInfo
MS-HAID:
- '\_win32\_getconsolecursorinfo'
- base.getconsolecursorinfo
- consoles.getconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6200577d-8d84-46bd-9330-d0b6cbbb3e52
topic_type:
- apiref
api_name:
- GetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c920e5dd279a23b07702fa12b80da4245561548f
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358455"
---
# <a name="getconsolecursorinfo-function"></a><span data-ttu-id="ad3e3-104">GetConsoleCursorInfo función)</span><span class="sxs-lookup"><span data-stu-id="ad3e3-104">GetConsoleCursorInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="ad3e3-105">Recupera información sobre el tamaño y la visibilidad del cursor para el búfer de pantalla de la consola especificado.</span><span class="sxs-lookup"><span data-stu-id="ad3e3-105">Retrieves information about the size and visibility of the cursor for the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="ad3e3-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ad3e3-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleCursorInfo(
  _In_  HANDLE               hConsoleOutput,
  _Out_ PCONSOLE_CURSOR_INFO lpConsoleCursorInfo
);
```

## <a name="parameters"></a><span data-ttu-id="ad3e3-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ad3e3-107">Parameters</span></span>

<span data-ttu-id="ad3e3-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="ad3e3-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="ad3e3-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="ad3e3-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="ad3e3-110">El identificador debe tener derecho de acceso de **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="ad3e3-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="ad3e3-111">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="ad3e3-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="ad3e3-112">*lpConsoleCursorInfo* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="ad3e3-112">*lpConsoleCursorInfo* \[out\]</span></span>  
<span data-ttu-id="ad3e3-113">Puntero a una estructura [**de \_ \_ información del cursor**](console-cursor-info-str.md) de la consola que recibe información sobre el cursor de la consola.</span><span class="sxs-lookup"><span data-stu-id="ad3e3-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that receives information about the console's cursor.</span></span>

## <a name="return-value"></a><span data-ttu-id="ad3e3-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="ad3e3-114">Return value</span></span>

<span data-ttu-id="ad3e3-115">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="ad3e3-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ad3e3-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="ad3e3-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ad3e3-117">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="ad3e3-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="ad3e3-118">Comentarios</span><span class="sxs-lookup"><span data-stu-id="ad3e3-118">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="ad3e3-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad3e3-119">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ad3e3-120">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="ad3e3-120">Minimum supported client</span></span> | <span data-ttu-id="ad3e3-121">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="ad3e3-121">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="ad3e3-122">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="ad3e3-122">Minimum supported server</span></span> | <span data-ttu-id="ad3e3-123">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="ad3e3-123">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="ad3e3-124">Encabezado</span><span class="sxs-lookup"><span data-stu-id="ad3e3-124">Header</span></span> | <span data-ttu-id="ad3e3-125">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="ad3e3-125">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="ad3e3-126">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="ad3e3-126">Library</span></span> | <span data-ttu-id="ad3e3-127">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="ad3e3-127">Kernel32.lib</span></span> |
| <span data-ttu-id="ad3e3-128">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="ad3e3-128">DLL</span></span> | <span data-ttu-id="ad3e3-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ad3e3-129">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="ad3e3-130">Vea también</span><span class="sxs-lookup"><span data-stu-id="ad3e3-130">See also</span></span>

[<span data-ttu-id="ad3e3-131">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="ad3e3-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ad3e3-132">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="ad3e3-132">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="ad3e3-133">**\_información del cursor de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="ad3e3-133">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="ad3e3-134">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="ad3e3-134">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)