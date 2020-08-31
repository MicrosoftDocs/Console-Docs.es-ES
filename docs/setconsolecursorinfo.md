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
ms.openlocfilehash: 81f16e8c9d9cf90008bbd2e8619c2fa105d04212
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060949"
---
# <a name="setconsolecursorinfo-function"></a><span data-ttu-id="7a165-104">SetConsoleCursorInfo función)</span><span class="sxs-lookup"><span data-stu-id="7a165-104">SetConsoleCursorInfo function</span></span>


<span data-ttu-id="7a165-105">Establece el tamaño y la visibilidad del cursor para el búfer de pantalla de la consola especificado.</span><span class="sxs-lookup"><span data-stu-id="7a165-105">Sets the size and visibility of the cursor for the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="7a165-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7a165-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

<a name="parameters"></a><span data-ttu-id="7a165-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7a165-107">Parameters</span></span>
----------

<span data-ttu-id="7a165-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="7a165-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="7a165-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="7a165-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="7a165-110">El identificador debe tener el derecho de acceso de \*\* \_ lectura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="7a165-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="7a165-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="7a165-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="7a165-112">*lpConsoleCursorInfo* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="7a165-112">*lpConsoleCursorInfo* \[in\]</span></span>  
<span data-ttu-id="7a165-113">Puntero a una estructura [**de \_ \_ información del cursor**](console-cursor-info-str.md) de la consola que proporciona las nuevas especificaciones del cursor del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="7a165-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that provides the new specifications for the console screen buffer's cursor.</span></span>

<a name="return-value"></a><span data-ttu-id="7a165-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="7a165-114">Return value</span></span>
------------

<span data-ttu-id="7a165-115">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="7a165-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="7a165-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="7a165-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="7a165-117">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="7a165-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="7a165-118">Observaciones</span><span class="sxs-lookup"><span data-stu-id="7a165-118">Remarks</span></span>
-------

<span data-ttu-id="7a165-119">Cuando el cursor de un búfer de pantalla está visible, su apariencia puede variar, desde llenar completamente una celda de carácter hasta que aparezca como una línea horizontal en la parte inferior de la celda.</span><span class="sxs-lookup"><span data-stu-id="7a165-119">When a screen buffer's cursor is visible, its appearance can vary, ranging from completely filling a character cell to showing up as a horizontal line at the bottom of the cell.</span></span> <span data-ttu-id="7a165-120">El miembro **dwSize** de la estructura de [\*\* \_ \_ información del cursor\*\*](console-cursor-info-str.md) de la consola especifica el porcentaje de una celda de caracteres que se rellena con el cursor.</span><span class="sxs-lookup"><span data-stu-id="7a165-120">The **dwSize** member of the [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure specifies the percentage of a character cell that is filled by the cursor.</span></span> <span data-ttu-id="7a165-121">Si este miembro es menor que 1 o mayor que 100, **SetConsoleCursorInfo** produce un error.</span><span class="sxs-lookup"><span data-stu-id="7a165-121">If this member is less than 1 or greater than 100, **SetConsoleCursorInfo** fails.</span></span>

<a name="requirements"></a><span data-ttu-id="7a165-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a165-122">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="7a165-123">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="7a165-123">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="7a165-124">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="7a165-124">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7a165-125">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="7a165-125">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="7a165-126">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="7a165-126">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7a165-127">Encabezado</span><span class="sxs-lookup"><span data-stu-id="7a165-127">Header</span></span></p></td>
<td><span data-ttu-id="7a165-128">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="7a165-128">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7a165-129">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="7a165-129">Library</span></span></p></td>
<td><span data-ttu-id="7a165-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="7a165-130">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7a165-131">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="7a165-131">DLL</span></span></p></td>
<td><span data-ttu-id="7a165-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7a165-132">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="7a165-133"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="7a165-133"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="7a165-134">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="7a165-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="7a165-135">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="7a165-135">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="7a165-136">**\_información del cursor de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="7a165-136">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="7a165-137">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="7a165-137">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="7a165-138">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="7a165-138">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

 

 




