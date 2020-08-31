---
title: SetConsoleCP función)
description: Establece la página de códigos de entrada utilizada por la consola asociada al proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleCP
- wincon/SetConsoleCP
- SetConsoleCP
MS-HAID:
- '\_win32\_setconsolecp'
- base.setconsolecp
- consoles.setconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a1a9ba5-c792-491d-ae51-979f462dcb53
topic_type:
- apiref
api_name:
- SetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: cf7048f9042b6c516c6d8e7a6e0544fdc2ac7533
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060953"
---
# <a name="setconsolecp-function"></a><span data-ttu-id="f285a-104">SetConsoleCP función)</span><span class="sxs-lookup"><span data-stu-id="f285a-104">SetConsoleCP function</span></span>


<span data-ttu-id="f285a-105">Establece la página de códigos de entrada utilizada por la consola asociada al proceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="f285a-105">Sets the input code page used by the console associated with the calling process.</span></span> <span data-ttu-id="f285a-106">Una consola usa su página de códigos de entrada para traducir la entrada del teclado en el valor de carácter correspondiente.</span><span class="sxs-lookup"><span data-stu-id="f285a-106">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span>

<a name="syntax"></a><span data-ttu-id="f285a-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f285a-107">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleCP(
  _In_ UINT wCodePageID
);
```

<a name="parameters"></a><span data-ttu-id="f285a-108">Parámetros</span><span class="sxs-lookup"><span data-stu-id="f285a-108">Parameters</span></span>
----------

<span data-ttu-id="f285a-109">*wCodePageID* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="f285a-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="f285a-110">Identificador de la página de códigos que se va a establecer.</span><span class="sxs-lookup"><span data-stu-id="f285a-110">The identifier of the code page to be set.</span></span> <span data-ttu-id="f285a-111">Para obtener más información, vea la sección Comentarios.</span><span class="sxs-lookup"><span data-stu-id="f285a-111">For more information, see Remarks.</span></span>

<a name="return-value"></a><span data-ttu-id="f285a-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="f285a-112">Return value</span></span>
------------

<span data-ttu-id="f285a-113">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="f285a-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="f285a-114">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="f285a-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="f285a-115">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="f285a-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="f285a-116">Observaciones</span><span class="sxs-lookup"><span data-stu-id="f285a-116">Remarks</span></span>
-------

<span data-ttu-id="f285a-117">Una página de códigos asigna códigos de caracteres de 256 a caracteres individuales.</span><span class="sxs-lookup"><span data-stu-id="f285a-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="f285a-118">Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas.</span><span class="sxs-lookup"><span data-stu-id="f285a-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="f285a-119">Para buscar las páginas de códigos que el sistema operativo instala o admite, utilice la función [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) .</span><span class="sxs-lookup"><span data-stu-id="f285a-119">To find the code pages that are installed or supported by the operating system, use the [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) function.</span></span> <span data-ttu-id="f285a-120">Los identificadores de las páginas de códigos disponibles en el equipo local también se almacenan en el registro con la siguiente clave:</span><span class="sxs-lookup"><span data-stu-id="f285a-120">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

<span data-ttu-id="f285a-121">**HKEY \_ local \_ Machine \\ System \\ CurrentControlSet \\ control de la página de \\ \\ códigos NLS**</span><span class="sxs-lookup"><span data-stu-id="f285a-121">**HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Nls\\CodePage**</span></span>

<span data-ttu-id="f285a-122">Sin embargo, es mejor usar [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) para enumerar las páginas de códigos, ya que el registro puede diferir en diferentes versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="f285a-122">However, it is better to use [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>

<span data-ttu-id="f285a-123">Para determinar si una página de códigos determinada es válida, utilice la función [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) .</span><span class="sxs-lookup"><span data-stu-id="f285a-123">To determine whether a particular code page is valid, use the [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) function.</span></span> <span data-ttu-id="f285a-124">Para recuperar más información sobre una página de códigos, incluido su nombre, utilice la función [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .</span><span class="sxs-lookup"><span data-stu-id="f285a-124">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span> <span data-ttu-id="f285a-125">Para obtener una lista de los identificadores de página de códigos disponibles, vea [identificadores de páginas de códigos](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span><span class="sxs-lookup"><span data-stu-id="f285a-125">For a list of available code page identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="f285a-126">Para determinar la página de códigos de entrada actual de la consola, use la función [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="f285a-126">To determine a console's current input code page, use the [**GetConsoleCP**](getconsolecp.md) function.</span></span> <span data-ttu-id="f285a-127">Para establecer y recuperar la página de códigos de salida de una consola, use las funciones [**SetConsoleOutputCP**](setconsoleoutputcp.md) y [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="f285a-127">To set and retrieve a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions.</span></span>

<a name="requirements"></a><span data-ttu-id="f285a-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f285a-128">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f285a-129">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="f285a-129">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="f285a-130">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="f285a-130">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f285a-131">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="f285a-131">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="f285a-132">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="f285a-132">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f285a-133">Encabezado</span><span class="sxs-lookup"><span data-stu-id="f285a-133">Header</span></span></p></td>
<td><span data-ttu-id="f285a-134">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="f285a-134">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f285a-135">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="f285a-135">Library</span></span></p></td>
<td><span data-ttu-id="f285a-136">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="f285a-136">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f285a-137">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="f285a-137">DLL</span></span></p></td>
<td><span data-ttu-id="f285a-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f285a-138">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="f285a-139"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="f285a-139"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="f285a-140">Páginas de códigos de la consola</span><span class="sxs-lookup"><span data-stu-id="f285a-140">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="f285a-141">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="f285a-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f285a-142">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="f285a-142">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="f285a-143">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="f285a-143">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="f285a-144">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="f285a-144">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

 

 




