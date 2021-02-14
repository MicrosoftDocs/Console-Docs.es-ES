---
title: SetConsoleScreenBufferInfoEx función)
description: Establece la información extendida sobre el búfer de pantalla especificado en el búfer especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleScreenBufferInfoEx
- wincon/SetConsoleScreenBufferInfoEx
- SetConsoleScreenBufferInfoEx
MS-HAID:
- base.setconsolescreenbufferinfoex
- consoles.setconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ff851144-eee9-4410-8fd1-28aa24fc25f1
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 677df94d6397c1515ad96757788c9a044b6ed87e
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358655"
---
# <a name="setconsolescreenbufferinfoex-function"></a><span data-ttu-id="3de9d-104">SetConsoleScreenBufferInfoEx función)</span><span class="sxs-lookup"><span data-stu-id="3de9d-104">SetConsoleScreenBufferInfoEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="3de9d-105">Establece la información extendida sobre el búfer de pantalla especificado.</span><span class="sxs-lookup"><span data-stu-id="3de9d-105">Sets extended information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="3de9d-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3de9d-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleScreenBufferInfoEx(
  _In_ HANDLE                        hConsoleOutput,
  _In_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a><span data-ttu-id="3de9d-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3de9d-107">Parameters</span></span>

<span data-ttu-id="3de9d-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="3de9d-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="3de9d-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="3de9d-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="3de9d-110">El identificador debe tener derecho de acceso de **GENERIC\_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="3de9d-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="3de9d-111">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="3de9d-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="3de9d-112">*lpConsoleScreenBufferInfoEx* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="3de9d-112">*lpConsoleScreenBufferInfoEx* \[in\]</span></span>  
<span data-ttu-id="3de9d-113">Una [**estructura \_ \_ \_ INFOEX de búfer de pantalla**](console-screen-buffer-infoex.md) de la consola que contiene la información del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="3de9d-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that contains the console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="3de9d-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="3de9d-114">Return value</span></span>

<span data-ttu-id="3de9d-115">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="3de9d-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="3de9d-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="3de9d-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="3de9d-117">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="3de9d-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="3de9d-118">Comentarios</span><span class="sxs-lookup"><span data-stu-id="3de9d-118">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="3de9d-119">Esta API tiene un equivalente de **[terminal virtual](console-virtual-terminal-sequences.md)** parcial.</span><span class="sxs-lookup"><span data-stu-id="3de9d-119">This API has a partial **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="3de9d-120">El **[búfer de posición del cursor](console-virtual-terminal-sequences.md#cursor-positioning)** y **[los atributos de texto](console-virtual-terminal-sequences.md#text-formatting)** tienen equivalentes de secuencia específicos.</span><span class="sxs-lookup"><span data-stu-id="3de9d-120">**[Cursor positioning buffer](console-virtual-terminal-sequences.md#cursor-positioning)** and **[text attributes](console-virtual-terminal-sequences.md#text-formatting)** have specific sequence equivalents.</span></span> <span data-ttu-id="3de9d-121">La tabla de colores no es configurable, pero los **[colores extendidos](console-virtual-terminal-sequences.md#extended-colors)** están disponibles más allá de lo que suele estar disponible a través de **[las funciones](console-functions.md)** de la consola.</span><span class="sxs-lookup"><span data-stu-id="3de9d-121">The color table is not configurable, but **[extended colors](console-virtual-terminal-sequences.md#extended-colors)** are available beyond what is normally available through **[console functions](console-functions.md)**.</span></span> <span data-ttu-id="3de9d-122">Los atributos emergentes no tienen ningún equivalente en los menús emergentes es responsabilidad de la aplicación cliente de línea de comandos en el mundo de **terminal virtual** .</span><span class="sxs-lookup"><span data-stu-id="3de9d-122">Popup attributes have no equivalent as popup menus are the responsibility of the command-line client application in the **virtual terminal** world.</span></span> <span data-ttu-id="3de9d-123">Por último, el tamaño de la ventana y el estado de la pantalla completa se consideran los privilegios que posee el usuario en el mundo del **terminal virtual** y no tienen ninguna secuencia equivalente.</span><span class="sxs-lookup"><span data-stu-id="3de9d-123">Finally, the size of the window and the full screen status are considered privileges owned by the user in the **virtual terminal** world and have no equivalent sequence.</span></span>

## <a name="requirements"></a><span data-ttu-id="3de9d-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3de9d-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="3de9d-125">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="3de9d-125">Minimum supported client</span></span> | <span data-ttu-id="3de9d-126">Solo aplicaciones de escritorio de Windows Vista \[\]</span><span class="sxs-lookup"><span data-stu-id="3de9d-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="3de9d-127">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="3de9d-127">Minimum supported server</span></span> | <span data-ttu-id="3de9d-128">Solo aplicaciones de escritorio de Windows Server 2008 \[\]</span><span class="sxs-lookup"><span data-stu-id="3de9d-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="3de9d-129">Encabezado</span><span class="sxs-lookup"><span data-stu-id="3de9d-129">Header</span></span> | <span data-ttu-id="3de9d-130">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="3de9d-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="3de9d-131">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="3de9d-131">Library</span></span> | <span data-ttu-id="3de9d-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="3de9d-132">Kernel32.lib</span></span> |
| <span data-ttu-id="3de9d-133">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="3de9d-133">DLL</span></span> | <span data-ttu-id="3de9d-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3de9d-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="3de9d-135">Vea también</span><span class="sxs-lookup"><span data-stu-id="3de9d-135">See also</span></span>

[<span data-ttu-id="3de9d-136">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="3de9d-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3de9d-137">**búfer de pantalla de la consola \_ \_ \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="3de9d-137">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="3de9d-138">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="3de9d-138">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)