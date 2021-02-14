---
title: SetConsoleHistoryInfo función)
description: Establece la configuración del historial para la consola de Windows del proceso que realiza la llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/SetConsoleHistoryInfo
- wincon/SetConsoleHistoryInfo
- SetConsoleHistoryInfo
MS-HAID:
- base.setconsolehistoryinfo
- consoles.setconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: db180f53-aa3c-4a91-bc3e-9f3f0bb7ab01
topic_type:
- apiref
api_name:
- SetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 3c2dcce41994929292253793fe94512ab7bc5a01
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357655"
---
# <a name="setconsolehistoryinfo-function"></a><span data-ttu-id="141c1-104">SetConsoleHistoryInfo función)</span><span class="sxs-lookup"><span data-stu-id="141c1-104">SetConsoleHistoryInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="141c1-105">Establece la configuración del historial de la consola del proceso que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="141c1-105">Sets the history settings for the calling process's console.</span></span>

## <a name="syntax"></a><span data-ttu-id="141c1-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="141c1-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleHistoryInfo(
  _In_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a><span data-ttu-id="141c1-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="141c1-107">Parameters</span></span>

<span data-ttu-id="141c1-108">*lpConsoleHistoryInfo* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="141c1-108">*lpConsoleHistoryInfo* \[in\]</span></span>  
<span data-ttu-id="141c1-109">Un puntero a una estructura de [**\_ \_ información del historial**](console-history-info.md) de la consola que contiene la configuración del historial de la consola del proceso.</span><span class="sxs-lookup"><span data-stu-id="141c1-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that contains the history settings for the process's console.</span></span>

## <a name="return-value"></a><span data-ttu-id="141c1-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="141c1-110">Return value</span></span>

<span data-ttu-id="141c1-111">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="141c1-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="141c1-112">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="141c1-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="141c1-113">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="141c1-113">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="141c1-114">Comentarios</span><span class="sxs-lookup"><span data-stu-id="141c1-114">Remarks</span></span>

<span data-ttu-id="141c1-115">Si el proceso de llamada no es un proceso de consola, se produce un error en la función y se establece el último código de error en **\_ acceso \_ denegado**.</span><span class="sxs-lookup"><span data-stu-id="141c1-115">If the calling process is not a console process, the function fails and sets the last error code to **ERROR\_ACCESS\_DENIED**.</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="141c1-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="141c1-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="141c1-117">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="141c1-117">Minimum supported client</span></span> | <span data-ttu-id="141c1-118">Solo aplicaciones de escritorio de Windows Vista \[\]</span><span class="sxs-lookup"><span data-stu-id="141c1-118">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="141c1-119">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="141c1-119">Minimum supported server</span></span> | <span data-ttu-id="141c1-120">Solo aplicaciones de escritorio de Windows Server 2008 \[\]</span><span class="sxs-lookup"><span data-stu-id="141c1-120">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="141c1-121">Encabezado</span><span class="sxs-lookup"><span data-stu-id="141c1-121">Header</span></span> | <span data-ttu-id="141c1-122">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="141c1-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="141c1-123">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="141c1-123">Library</span></span> | <span data-ttu-id="141c1-124">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="141c1-124">Kernel32.lib</span></span> |
| <span data-ttu-id="141c1-125">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="141c1-125">DLL</span></span> | <span data-ttu-id="141c1-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="141c1-126">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="141c1-127">Vea también</span><span class="sxs-lookup"><span data-stu-id="141c1-127">See also</span></span>

[<span data-ttu-id="141c1-128">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="141c1-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="141c1-129">**\_información del historial de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="141c1-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="141c1-130">**GetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="141c1-130">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)