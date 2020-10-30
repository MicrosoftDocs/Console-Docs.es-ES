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
ms.openlocfilehash: 4bbb14dd501d483f35fbce5e1a729eaf002b1579
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039403"
---
# <a name="setconsolecursorinfo-function"></a><span data-ttu-id="b3980-104">SetConsoleCursorInfo función)</span><span class="sxs-lookup"><span data-stu-id="b3980-104">SetConsoleCursorInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="b3980-105">Establece el tamaño y la visibilidad del cursor para el búfer de pantalla de la consola especificado.</span><span class="sxs-lookup"><span data-stu-id="b3980-105">Sets the size and visibility of the cursor for the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="b3980-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b3980-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

## <a name="parameters"></a><span data-ttu-id="b3980-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b3980-107">Parameters</span></span>

<span data-ttu-id="b3980-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="b3980-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="b3980-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="b3980-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="b3980-110">El identificador debe tener el derecho de acceso de **\_ lectura genérico** .</span><span class="sxs-lookup"><span data-stu-id="b3980-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="b3980-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="b3980-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="b3980-112">*lpConsoleCursorInfo* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="b3980-112">*lpConsoleCursorInfo* \[in\]</span></span>  
<span data-ttu-id="b3980-113">Puntero a una estructura [**de \_ \_ información del cursor**](console-cursor-info-str.md) de la consola que proporciona las nuevas especificaciones del cursor del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="b3980-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that provides the new specifications for the console screen buffer's cursor.</span></span>

## <a name="return-value"></a><span data-ttu-id="b3980-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="b3980-114">Return value</span></span>

<span data-ttu-id="b3980-115">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="b3980-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b3980-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="b3980-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b3980-117">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="b3980-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="b3980-118">Comentarios</span><span class="sxs-lookup"><span data-stu-id="b3980-118">Remarks</span></span>

<span data-ttu-id="b3980-119">Cuando el cursor de un búfer de pantalla está visible, su apariencia puede variar, desde llenar completamente una celda de carácter hasta que aparezca como una línea horizontal en la parte inferior de la celda.</span><span class="sxs-lookup"><span data-stu-id="b3980-119">When a screen buffer's cursor is visible, its appearance can vary, ranging from completely filling a character cell to showing up as a horizontal line at the bottom of the cell.</span></span> <span data-ttu-id="b3980-120">El miembro **dwSize** de la estructura de [**\_ \_ información del cursor**](console-cursor-info-str.md) de la consola especifica el porcentaje de una celda de caracteres que se rellena con el cursor.</span><span class="sxs-lookup"><span data-stu-id="b3980-120">The **dwSize** member of the [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure specifies the percentage of a character cell that is filled by the cursor.</span></span> <span data-ttu-id="b3980-121">Si este miembro es menor que 1 o mayor que 100, **SetConsoleCursorInfo** produce un error.</span><span class="sxs-lookup"><span data-stu-id="b3980-121">If this member is less than 1 or greater than 100, **SetConsoleCursorInfo** fails.</span></span>

> [!TIP]
> <span data-ttu-id="b3980-122">Esta API tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente en la sección de **[visibilidad del cursor](console-virtual-terminal-sequences.md#cursor-visibility)** con las `^[[?25h` `^[[?25l` secuencias y.</span><span class="sxs-lookup"><span data-stu-id="b3980-122">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[cursor visibility](console-virtual-terminal-sequences.md#cursor-visibility)** section with the `^[[?25h` and `^[[?25l` sequences.</span></span> 

## <a name="requirements"></a><span data-ttu-id="b3980-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b3980-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b3980-124">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="b3980-124">Minimum supported client</span></span> | <span data-ttu-id="b3980-125">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="b3980-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="b3980-126">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="b3980-126">Minimum supported server</span></span> | <span data-ttu-id="b3980-127">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="b3980-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="b3980-128">Encabezado</span><span class="sxs-lookup"><span data-stu-id="b3980-128">Header</span></span> | <span data-ttu-id="b3980-129">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="b3980-129">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="b3980-130">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="b3980-130">Library</span></span> | <span data-ttu-id="b3980-131">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="b3980-131">Kernel32.lib</span></span> |
| <span data-ttu-id="b3980-132">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="b3980-132">DLL</span></span> | <span data-ttu-id="b3980-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b3980-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="b3980-134">Consulte también</span><span class="sxs-lookup"><span data-stu-id="b3980-134">See also</span></span>

[<span data-ttu-id="b3980-135">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="b3980-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b3980-136">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="b3980-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="b3980-137">**\_información del cursor de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="b3980-137">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="b3980-138">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="b3980-138">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="b3980-139">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="b3980-139">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)
