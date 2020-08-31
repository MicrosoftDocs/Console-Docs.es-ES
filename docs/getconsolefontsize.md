---
title: GetConsoleFontSize función)
description: Recupera el tamaño de la fuente utilizada por el búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetConsoleFontSize
- wincon/GetConsoleFontSize
- GetConsoleFontSize
MS-HAID:
- '\_win32\_getconsolefontsize'
- base.getconsolefontsize
- consoles.getconsolefontsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 51b1f58d-b3fb-4e09-8398-671b3959bb01
topic_type:
- apiref
api_name:
- GetConsoleFontSize
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: b992ddaab35cb5af25479426dca83ef6381e73dd
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060704"
---
# <a name="getconsolefontsize-function"></a><span data-ttu-id="a6daf-104">GetConsoleFontSize función)</span><span class="sxs-lookup"><span data-stu-id="a6daf-104">GetConsoleFontSize function</span></span>


<span data-ttu-id="a6daf-105">Recupera el tamaño de la fuente utilizada por el búfer de pantalla de la consola especificado.</span><span class="sxs-lookup"><span data-stu-id="a6daf-105">Retrieves the size of the font used by the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="a6daf-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="a6daf-106">Syntax</span></span>
------

```C
COORD WINAPI GetConsoleFontSize(
  _In_ HANDLE hConsoleOutput,
  _In_ DWORD  nFont
);
```

<a name="parameters"></a><span data-ttu-id="a6daf-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a6daf-107">Parameters</span></span>
----------

<span data-ttu-id="a6daf-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="a6daf-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="a6daf-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="a6daf-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="a6daf-110">El identificador debe tener el derecho de acceso de \*\* \_ lectura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="a6daf-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="a6daf-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="a6daf-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="a6daf-112">*nFont* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="a6daf-112">*nFont* \[in\]</span></span>  
<span data-ttu-id="a6daf-113">Índice de la fuente cuyo tamaño se va a recuperar.</span><span class="sxs-lookup"><span data-stu-id="a6daf-113">The index of the font whose size is to be retrieved.</span></span> <span data-ttu-id="a6daf-114">Este índice se obtiene mediante una llamada a la función [**GetCurrentConsoleFont**](getcurrentconsolefont.md) .</span><span class="sxs-lookup"><span data-stu-id="a6daf-114">This index is obtained by calling the [**GetCurrentConsoleFont**](getcurrentconsolefont.md) function.</span></span>

<a name="return-value"></a><span data-ttu-id="a6daf-115">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="a6daf-115">Return value</span></span>
------------

<span data-ttu-id="a6daf-116">Si la función se ejecuta correctamente, el valor devuelto es una estructura de [**coordenadas**](coord-str.md) que contiene el ancho y el alto de cada carácter de la fuente, en unidades lógicas.</span><span class="sxs-lookup"><span data-stu-id="a6daf-116">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="a6daf-117">El miembro **X** contiene el ancho, mientras que el miembro **Y** contiene el alto.</span><span class="sxs-lookup"><span data-stu-id="a6daf-117">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="a6daf-118">Si se produce un error en la función, el ancho y el alto son cero.</span><span class="sxs-lookup"><span data-stu-id="a6daf-118">If the function fails, the width and the height are zero.</span></span> <span data-ttu-id="a6daf-119">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="a6daf-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="a6daf-120">Para compilar una aplicación que usa esta función, defina \*\* \_ Win32 \_ WinNT\*\* como 0x0500 o posterior.</span><span class="sxs-lookup"><span data-stu-id="a6daf-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="a6daf-121">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="a6daf-121">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="a6daf-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a6daf-122">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="a6daf-123">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="a6daf-123">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="a6daf-124">Windows XP [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="a6daf-124">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a6daf-125">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="a6daf-125">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="a6daf-126">Windows Server 2003 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="a6daf-126">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a6daf-127">Encabezado</span><span class="sxs-lookup"><span data-stu-id="a6daf-127">Header</span></span></p></td>
<td><span data-ttu-id="a6daf-128">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="a6daf-128">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a6daf-129">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="a6daf-129">Library</span></span></p></td>
<td><span data-ttu-id="a6daf-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="a6daf-130">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a6daf-131">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="a6daf-131">DLL</span></span></p></td>
<td><span data-ttu-id="a6daf-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="a6daf-132">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="a6daf-133"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="a6daf-133"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="a6daf-134">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="a6daf-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="a6daf-135">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="a6daf-135">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="a6daf-136">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="a6daf-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="a6daf-137">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="a6daf-137">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)

 

 




