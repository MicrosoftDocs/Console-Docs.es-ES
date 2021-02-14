---
title: SetConsoleCursorInfo función)
description: Establece el tamaño y la visibilidad del cursor para el búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleCursorInfo
- wincon/SetConsoleCursorInfo
- SetConsoleCursorInfo
MS-HAID:
- '\_win32\_setconsolecursorinfo'
- base.setconsolecursorinfo
- consoles.setconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c98cbffb-18de-41e8-bba7-5fb46a0c5d25
topic_type:
- apiref
api_name:
- SetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 565ed3bda8bd864fb52aac0106f01cee96eb78ba
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357695"
---
# <a name="setconsolecursorinfo-function"></a><span data-ttu-id="467b8-104">SetConsoleCursorInfo función)</span><span class="sxs-lookup"><span data-stu-id="467b8-104">SetConsoleCursorInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="467b8-105">Establece el tamaño y la visibilidad del cursor para el búfer de pantalla de la consola especificado.</span><span class="sxs-lookup"><span data-stu-id="467b8-105">Sets the size and visibility of the cursor for the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="467b8-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="467b8-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

## <a name="parameters"></a><span data-ttu-id="467b8-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="467b8-107">Parameters</span></span>

<span data-ttu-id="467b8-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="467b8-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="467b8-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="467b8-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="467b8-110">El identificador debe tener derecho de acceso de **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="467b8-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="467b8-111">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="467b8-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="467b8-112">*lpConsoleCursorInfo* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="467b8-112">*lpConsoleCursorInfo* \[in\]</span></span>  
<span data-ttu-id="467b8-113">Puntero a una estructura [**de \_ \_ información del cursor**](console-cursor-info-str.md) de la consola que proporciona las nuevas especificaciones del cursor del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="467b8-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that provides the new specifications for the console screen buffer's cursor.</span></span>

## <a name="return-value"></a><span data-ttu-id="467b8-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="467b8-114">Return value</span></span>

<span data-ttu-id="467b8-115">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="467b8-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="467b8-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="467b8-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="467b8-117">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="467b8-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="467b8-118">Comentarios</span><span class="sxs-lookup"><span data-stu-id="467b8-118">Remarks</span></span>

<span data-ttu-id="467b8-119">Cuando el cursor de un búfer de pantalla está visible, su apariencia puede variar, desde llenar completamente una celda de carácter hasta que aparezca como una línea horizontal en la parte inferior de la celda.</span><span class="sxs-lookup"><span data-stu-id="467b8-119">When a screen buffer's cursor is visible, its appearance can vary, ranging from completely filling a character cell to showing up as a horizontal line at the bottom of the cell.</span></span> <span data-ttu-id="467b8-120">El miembro **dwSize** de la estructura de [**\_ \_ información del cursor**](console-cursor-info-str.md) de la consola especifica el porcentaje de una celda de caracteres que se rellena con el cursor.</span><span class="sxs-lookup"><span data-stu-id="467b8-120">The **dwSize** member of the [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure specifies the percentage of a character cell that is filled by the cursor.</span></span> <span data-ttu-id="467b8-121">Si este miembro es menor que 1 o mayor que 100, **SetConsoleCursorInfo** produce un error.</span><span class="sxs-lookup"><span data-stu-id="467b8-121">If this member is less than 1 or greater than 100, **SetConsoleCursorInfo** fails.</span></span>

> [!TIP]
> <span data-ttu-id="467b8-122">Esta API tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente en la sección de **[visibilidad del cursor](console-virtual-terminal-sequences.md#cursor-visibility)** con las `^[[?25h` `^[[?25l` secuencias y.</span><span class="sxs-lookup"><span data-stu-id="467b8-122">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[cursor visibility](console-virtual-terminal-sequences.md#cursor-visibility)** section with the `^[[?25h` and `^[[?25l` sequences.</span></span> 

## <a name="requirements"></a><span data-ttu-id="467b8-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="467b8-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="467b8-124">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="467b8-124">Minimum supported client</span></span> | <span data-ttu-id="467b8-125">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="467b8-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="467b8-126">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="467b8-126">Minimum supported server</span></span> | <span data-ttu-id="467b8-127">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="467b8-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="467b8-128">Encabezado</span><span class="sxs-lookup"><span data-stu-id="467b8-128">Header</span></span> | <span data-ttu-id="467b8-129">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="467b8-129">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="467b8-130">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="467b8-130">Library</span></span> | <span data-ttu-id="467b8-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="467b8-131">Kernel32.lib</span></span> |
| <span data-ttu-id="467b8-132">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="467b8-132">DLL</span></span> | <span data-ttu-id="467b8-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="467b8-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="467b8-134">Vea también</span><span class="sxs-lookup"><span data-stu-id="467b8-134">See also</span></span>

[<span data-ttu-id="467b8-135">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="467b8-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="467b8-136">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="467b8-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="467b8-137">**\_información del cursor de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="467b8-137">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="467b8-138">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="467b8-138">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="467b8-139">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="467b8-139">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)