---
title: SetConsoleScreenBufferSize función)
description: Vea la información de referencia sobre la función SetConsoleScreenBufferSize, que cambia el tamaño del búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleScreenBufferSize
- wincon/SetConsoleScreenBufferSize
- SetConsoleScreenBufferSize
MS-HAID:
- '\_win32\_setconsolescreenbuffersize'
- base.setconsolescreenbuffersize
- consoles.setconsolescreenbuffersize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 50bf1973-5604-42fe-bbeb-611ddc240bdd
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 46c412ccb41ac17a8e7cf327c80d7f8330738d65
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039333"
---
# <a name="setconsolescreenbuffersize-function"></a><span data-ttu-id="9cfec-104">SetConsoleScreenBufferSize función)</span><span class="sxs-lookup"><span data-stu-id="9cfec-104">SetConsoleScreenBufferSize function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="9cfec-105">Cambia el tamaño del búfer de pantalla de la consola especificado.</span><span class="sxs-lookup"><span data-stu-id="9cfec-105">Changes the size of the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="9cfec-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9cfec-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleScreenBufferSize(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwSize
);
```

## <a name="parameters"></a><span data-ttu-id="9cfec-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9cfec-107">Parameters</span></span>

<span data-ttu-id="9cfec-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="9cfec-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="9cfec-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="9cfec-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="9cfec-110">El identificador debe tener el derecho de acceso de **\_ lectura genérico** .</span><span class="sxs-lookup"><span data-stu-id="9cfec-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="9cfec-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="9cfec-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="9cfec-112">*dwSize* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="9cfec-112">*dwSize* \[in\]</span></span>  
<span data-ttu-id="9cfec-113">Estructura de [**coordenadas**](coord-str.md) que especifica el nuevo tamaño del búfer de pantalla de la consola, en filas y columnas de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9cfec-113">A [**COORD**](coord-str.md) structure that specifies the new size of the console screen buffer, in character rows and columns.</span></span> <span data-ttu-id="9cfec-114">El ancho y el alto especificados no pueden ser menores que el ancho y el alto de la ventana del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="9cfec-114">The specified width and height cannot be less than the width and height of the console screen buffer's window.</span></span> <span data-ttu-id="9cfec-115">Las dimensiones especificadas tampoco pueden ser menores que el tamaño mínimo permitido por el sistema.</span><span class="sxs-lookup"><span data-stu-id="9cfec-115">The specified dimensions also cannot be less than the minimum size allowed by the system.</span></span> <span data-ttu-id="9cfec-116">Este mínimo depende del tamaño de la fuente actual para la consola (seleccionada por el usuario) y los valores **SM \_ CXMIN** y **SM \_ CYMIN** devueltos por la función [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) .</span><span class="sxs-lookup"><span data-stu-id="9cfec-116">This minimum depends on the current font size for the console (selected by the user) and the **SM\_CXMIN** and **SM\_CYMIN** values returned by the [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) function.</span></span>

## <a name="return-value"></a><span data-ttu-id="9cfec-117">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="9cfec-117">Return value</span></span>

<span data-ttu-id="9cfec-118">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="9cfec-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="9cfec-119">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="9cfec-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="9cfec-120">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="9cfec-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="9cfec-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9cfec-121">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="9cfec-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9cfec-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="9cfec-123">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="9cfec-123">Minimum supported client</span></span> | <span data-ttu-id="9cfec-124">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="9cfec-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="9cfec-125">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="9cfec-125">Minimum supported server</span></span> | <span data-ttu-id="9cfec-126">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="9cfec-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="9cfec-127">Encabezado</span><span class="sxs-lookup"><span data-stu-id="9cfec-127">Header</span></span> | <span data-ttu-id="9cfec-128">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9cfec-128">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="9cfec-129">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="9cfec-129">Library</span></span> | <span data-ttu-id="9cfec-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="9cfec-130">Kernel32.lib</span></span> |
| <span data-ttu-id="9cfec-131">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="9cfec-131">DLL</span></span> | <span data-ttu-id="9cfec-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9cfec-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="9cfec-133">Consulte también</span><span class="sxs-lookup"><span data-stu-id="9cfec-133">See also</span></span>

[<span data-ttu-id="9cfec-134">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="9cfec-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="9cfec-135">Búfer de entrada de la consola</span><span class="sxs-lookup"><span data-stu-id="9cfec-135">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="9cfec-136">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="9cfec-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="9cfec-137">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="9cfec-137">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="9cfec-138">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="9cfec-138">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)
