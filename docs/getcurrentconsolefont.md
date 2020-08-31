---
title: GetCurrentConsoleFont función)
description: Recupera información sobre la fuente de consola actual para un búfer de pantalla de la consola especificado.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi3/GetCurrentConsoleFont
- wincon/GetCurrentConsoleFont
- GetCurrentConsoleFont
MS-HAID:
- '\_win32\_getcurrentconsolefont'
- base.getcurrentconsolefont
- consoles.getcurrentconsolefont
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 347508ea-5c15-4568-b99f-1e7f5cdac8c1
topic_type:
- apiref
api_name:
- GetCurrentConsoleFont
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 4116dcf034c619544ed1689e3161f4eca4250a81
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060645"
---
# <a name="getcurrentconsolefont-function"></a><span data-ttu-id="d0a57-104">GetCurrentConsoleFont función)</span><span class="sxs-lookup"><span data-stu-id="d0a57-104">GetCurrentConsoleFont function</span></span>


<span data-ttu-id="d0a57-105">Recupera información sobre la fuente de consola actual.</span><span class="sxs-lookup"><span data-stu-id="d0a57-105">Retrieves information about the current console font.</span></span>

<a name="syntax"></a><span data-ttu-id="d0a57-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d0a57-106">Syntax</span></span>
------

```C
BOOL WINAPI GetCurrentConsoleFont(
  _In_  HANDLE             hConsoleOutput,
  _In_  BOOL               bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFO lpConsoleCurrentFont
);
```

<a name="parameters"></a><span data-ttu-id="d0a57-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="d0a57-107">Parameters</span></span>
----------

<span data-ttu-id="d0a57-108">*hConsoleOutput* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="d0a57-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="d0a57-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="d0a57-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="d0a57-110">El identificador debe tener el derecho de acceso de \*\* \_ lectura genérico\*\* .</span><span class="sxs-lookup"><span data-stu-id="d0a57-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="d0a57-111">Para obtener más información, consulte [seguridad y derechos de acceso de búfer](console-buffer-security-and-access-rights.md)de la consola.</span><span class="sxs-lookup"><span data-stu-id="d0a57-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="d0a57-112">*bMaximumWindow* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="d0a57-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="d0a57-113">Si este parámetro es **true**, se recupera la información de fuente para el tamaño máximo de la ventana.</span><span class="sxs-lookup"><span data-stu-id="d0a57-113">If this parameter is **TRUE**, font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="d0a57-114">Si este parámetro es **false**, se recupera la información de fuente para el tamaño de la ventana actual.</span><span class="sxs-lookup"><span data-stu-id="d0a57-114">If this parameter is **FALSE**, font information is retrieved for the current window size.</span></span>

<span data-ttu-id="d0a57-115">*lpConsoleCurrentFont* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="d0a57-115">*lpConsoleCurrentFont* \[out\]</span></span>  
<span data-ttu-id="d0a57-116">Puntero a una estructura [**de \_ \_ información de fuente de consola**](console-font-info-str.md) que recibe la información de fuente solicitada.</span><span class="sxs-lookup"><span data-stu-id="d0a57-116">A pointer to a [**CONSOLE\_FONT\_INFO**](console-font-info-str.md) structure that receives the requested font information.</span></span>

<a name="return-value"></a><span data-ttu-id="d0a57-117">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="d0a57-117">Return value</span></span>
------------

<span data-ttu-id="d0a57-118">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="d0a57-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d0a57-119">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="d0a57-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d0a57-120">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="d0a57-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="d0a57-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="d0a57-121">Remarks</span></span>
-------

<span data-ttu-id="d0a57-122">Para compilar una aplicación que usa esta función, defina \*\* \_ Win32 \_ WinNT\*\* como 0x0500 o posterior.</span><span class="sxs-lookup"><span data-stu-id="d0a57-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="d0a57-123">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="d0a57-123">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="d0a57-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d0a57-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="d0a57-125">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="d0a57-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="d0a57-126">Windows XP [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="d0a57-126">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d0a57-127">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="d0a57-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="d0a57-128">Windows Server 2003 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="d0a57-128">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d0a57-129">Encabezado</span><span class="sxs-lookup"><span data-stu-id="d0a57-129">Header</span></span></p></td>
<td><span data-ttu-id="d0a57-130">ConsoleApi3. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d0a57-130">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d0a57-131">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="d0a57-131">Library</span></span></p></td>
<td><span data-ttu-id="d0a57-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="d0a57-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d0a57-133">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="d0a57-133">DLL</span></span></p></td>
<td><span data-ttu-id="d0a57-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d0a57-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="d0a57-135"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="d0a57-135"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="d0a57-136">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="d0a57-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d0a57-137">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="d0a57-137">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="d0a57-138">**\_información de fuente de la consola \_**</span><span class="sxs-lookup"><span data-stu-id="d0a57-138">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="d0a57-139">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="d0a57-139">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)

 

 




