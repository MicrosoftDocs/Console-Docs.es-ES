---
title: GetConsoleOriginalTitle función)
description: Vea la información de referencia sobre la función GetConsoleOriginalTitle, que recupera el título original de la ventana de la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 109d41a141083fc4691ebaf2546ec8f412f7b861
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060673"
---
# <a name="getconsoleoriginaltitle-function"></a><span data-ttu-id="8a7d8-104">GetConsoleOriginalTitle función)</span><span class="sxs-lookup"><span data-stu-id="8a7d8-104">GetConsoleOriginalTitle function</span></span>


<span data-ttu-id="8a7d8-105">Recupera el título original de la ventana de la consola actual.</span><span class="sxs-lookup"><span data-stu-id="8a7d8-105">Retrieves the original title for the current console window.</span></span>

<a name="syntax"></a><span data-ttu-id="8a7d8-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8a7d8-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a><span data-ttu-id="8a7d8-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="8a7d8-107">Parameters</span></span>
----------

<span data-ttu-id="8a7d8-108">*lpConsoleTitle* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="8a7d8-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="8a7d8-109">Un puntero a un búfer que recibe una cadena terminada en null que contiene el título original.</span><span class="sxs-lookup"><span data-stu-id="8a7d8-109">A pointer to a buffer that receives a null-terminated string containing the original title.</span></span>

<span data-ttu-id="8a7d8-110">*nSize* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="8a7d8-110">*nSize* \[in\]</span></span>  
<span data-ttu-id="8a7d8-111">Tamaño del búfer de *lpConsoleTitle* , en caracteres.</span><span class="sxs-lookup"><span data-stu-id="8a7d8-111">The size of the *lpConsoleTitle* buffer, in characters.</span></span>

<a name="return-value"></a><span data-ttu-id="8a7d8-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="8a7d8-112">Return value</span></span>
------------

<span data-ttu-id="8a7d8-113">Si la función se ejecuta correctamente, el valor devuelto es la longitud de la cadena copiada en el búfer, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="8a7d8-113">If the function succeeds, the return value is the length of the string copied to the buffer, in characters.</span></span>

<span data-ttu-id="8a7d8-114">Si el búfer no es lo suficientemente grande como para almacenar el título, el valor devuelto es cero y [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) devuelve el **error \_ Success**.</span><span class="sxs-lookup"><span data-stu-id="8a7d8-114">If the buffer is not large enough to store the title, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns **ERROR\_SUCCESS**.</span></span>

<span data-ttu-id="8a7d8-115">Si se produce un error en la función, el valor devuelto es cero y [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) devuelve el código de error.</span><span class="sxs-lookup"><span data-stu-id="8a7d8-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

<a name="remarks"></a><span data-ttu-id="8a7d8-116">Observaciones</span><span class="sxs-lookup"><span data-stu-id="8a7d8-116">Remarks</span></span>
-------

<span data-ttu-id="8a7d8-117">Para establecer el título de una ventana de la consola, use la función [**SetConsoleTitle**](setconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="8a7d8-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="8a7d8-118">Para recuperar la cadena de título actual, utilice la función [**GetConsoleTitle**](getconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="8a7d8-118">To retrieve the current title string, use the [**GetConsoleTitle**](getconsoletitle.md) function.</span></span>

<span data-ttu-id="8a7d8-119">Para compilar una aplicación que usa esta función, defina \*\* \_ Win32 \_ WinNT\*\* como 0x0600 o posterior.</span><span class="sxs-lookup"><span data-stu-id="8a7d8-119">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0600 or later.</span></span> <span data-ttu-id="8a7d8-120">Para obtener más información, consulte [uso de los encabezados de Windows](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span><span class="sxs-lookup"><span data-stu-id="8a7d8-120">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="8a7d8-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a7d8-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="8a7d8-122">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="8a7d8-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="8a7d8-123">Windows Vista [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="8a7d8-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="8a7d8-124">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="8a7d8-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="8a7d8-125">Windows Server 2008 [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="8a7d8-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="8a7d8-126">Encabezado</span><span class="sxs-lookup"><span data-stu-id="8a7d8-126">Header</span></span></p></td>
<td><span data-ttu-id="8a7d8-127">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="8a7d8-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="8a7d8-128">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="8a7d8-128">Library</span></span></p></td>
<td><span data-ttu-id="8a7d8-129">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="8a7d8-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="8a7d8-130">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="8a7d8-130">DLL</span></span></p></td>
<td><span data-ttu-id="8a7d8-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="8a7d8-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="8a7d8-132">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="8a7d8-132">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="8a7d8-133"><strong>GetConsoleOriginalTitleW</strong> (Unicode) y <strong>GetConsoleOriginalTitleA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="8a7d8-133"><strong>GetConsoleOriginalTitleW</strong> (Unicode) and <strong>GetConsoleOriginalTitleA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="8a7d8-134"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="8a7d8-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="8a7d8-135">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="8a7d8-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="8a7d8-136">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="8a7d8-136">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="8a7d8-137">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="8a7d8-137">**SetConsoleTitle**</span></span>](setconsoletitle.md)

 

 




