---
title: GetConsoleWindow función)
description: Recupera el identificador de ventana que usa la consola asociada al proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleWindow
- wincon/GetConsoleWindow
- GetConsoleWindow
MS-HAID:
- '\_win32\_getconsolewindow'
- base.getconsolewindow
- consoles.getconsolewindow
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a5ab0b37-45ac-4413-b6ff-73876556ad38
topic_type:
- apiref
api_name:
- GetConsoleWindow
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: dd356bab4674da0cc090e42911829dee994fa8b1
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060644"
---
# <a name="getconsolewindow-function"></a><span data-ttu-id="2a1fe-104">GetConsoleWindow función)</span><span class="sxs-lookup"><span data-stu-id="2a1fe-104">GetConsoleWindow function</span></span>


<span data-ttu-id="2a1fe-105">Recupera el identificador de ventana que usa la consola asociada al proceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="2a1fe-105">Retrieves the window handle used by the console associated with the calling process.</span></span>

<a name="syntax"></a><span data-ttu-id="2a1fe-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2a1fe-106">Syntax</span></span>
------

```C
HWND WINAPI GetConsoleWindow(void);
```

<a name="parameters"></a><span data-ttu-id="2a1fe-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="2a1fe-107">Parameters</span></span>
----------

<span data-ttu-id="2a1fe-108">Esta función no tiene parámetros.</span><span class="sxs-lookup"><span data-stu-id="2a1fe-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="2a1fe-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="2a1fe-109">Return value</span></span>
------------

<span data-ttu-id="2a1fe-110">El valor devuelto es un identificador de la ventana que usa la consola asociada al proceso de llamada o **null** si no existe tal consola asociada.</span><span class="sxs-lookup"><span data-stu-id="2a1fe-110">The return value is a handle to the window used by the console associated with the calling process or **NULL** if there is no such associated console.</span></span>

<a name="remarks"></a><span data-ttu-id="2a1fe-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="2a1fe-111">Remarks</span></span>
-------

<span data-ttu-id="2a1fe-112">Para compilar una aplicación que usa esta función, defina \*\* \_ Win32 \_ WinNT\*\* como 0x0500 o posterior.</span><span class="sxs-lookup"><span data-stu-id="2a1fe-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="2a1fe-113">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="2a1fe-113">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="2a1fe-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a1fe-114">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="2a1fe-115">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="2a1fe-115">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="2a1fe-116">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="2a1fe-116">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2a1fe-117">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="2a1fe-117">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="2a1fe-118">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="2a1fe-118">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2a1fe-119">Encabezado</span><span class="sxs-lookup"><span data-stu-id="2a1fe-119">Header</span></span></p></td>
<td><span data-ttu-id="2a1fe-120">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="2a1fe-120">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="2a1fe-121">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="2a1fe-121">Library</span></span></p></td>
<td><span data-ttu-id="2a1fe-122">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="2a1fe-122">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="2a1fe-123">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="2a1fe-123">DLL</span></span></p></td>
<td><span data-ttu-id="2a1fe-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2a1fe-124">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="2a1fe-125"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="2a1fe-125"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="2a1fe-126">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="2a1fe-126">Console Functions</span></span>](console-functions.md)

 

 




