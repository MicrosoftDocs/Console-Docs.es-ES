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
ms.openlocfilehash: d87fe0828451615e837c1c6c809a0160f15cf018
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060701"
---
# <a name="getconsolecursorinfo-function"></a><span data-ttu-id="f65c6-104">GetConsoleCursorInfo función)</span><span class="sxs-lookup"><span data-stu-id="f65c6-104">GetConsoleCursorInfo function</span></span>


<span data-ttu-id="f65c6-105">Recupera información sobre el tamaño y la visibilidad del cursor para el búfer de pantalla de la consola especificado.</span><span class="sxs-lookup"><span data-stu-id="f65c6-105">Retrieves information about the size and visibility of the cursor for the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="f65c6-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f65c6-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleCursorInfo(
  _In_  HANDLE               hConsoleOutput,
  _Out_ PCONSOLE_CURSOR_INFO lpConsoleCursorInfo
);
```

<a name="parameters"></a><span data-ttu-id="f65c6-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="f65c6-107">Parameters</span></span>
----------

<span data-ttu-id="f65c6-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="f65c6-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="f65c6-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="f65c6-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="f65c6-110">El identificador debe tener el derecho de acceso de \*\* \_ lectura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="f65c6-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="f65c6-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="f65c6-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="f65c6-112">*lpConsoleCursorInfo* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="f65c6-112">*lpConsoleCursorInfo* \[out\]</span></span>  
<span data-ttu-id="f65c6-113">Puntero a una estructura [**de \_ \_ información del cursor**](console-cursor-info-str.md) de la consola que recibe información sobre el cursor de la consola.</span><span class="sxs-lookup"><span data-stu-id="f65c6-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that receives information about the console's cursor.</span></span>

<a name="return-value"></a><span data-ttu-id="f65c6-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="f65c6-114">Return value</span></span>
------------

<span data-ttu-id="f65c6-115">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="f65c6-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="f65c6-116">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="f65c6-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="f65c6-117">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="f65c6-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="f65c6-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f65c6-118">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f65c6-119">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="f65c6-119">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="f65c6-120">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="f65c6-120">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f65c6-121">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="f65c6-121">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="f65c6-122">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="f65c6-122">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f65c6-123">Encabezado</span><span class="sxs-lookup"><span data-stu-id="f65c6-123">Header</span></span></p></td>
<td><span data-ttu-id="f65c6-124">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f65c6-124">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f65c6-125">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="f65c6-125">Library</span></span></p></td>
<td><span data-ttu-id="f65c6-126">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="f65c6-126">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f65c6-127">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="f65c6-127">DLL</span></span></p></td>
<td><span data-ttu-id="f65c6-128">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f65c6-128">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="f65c6-129"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="f65c6-129"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="f65c6-130">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="f65c6-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f65c6-131">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="f65c6-131">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="f65c6-132">**\_información del cursor de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="f65c6-132">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="f65c6-133">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="f65c6-133">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

 

 




