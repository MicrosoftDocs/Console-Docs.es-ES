---
title: SetConsoleOutputCP función)
description: Establece la página de códigos de salida utilizada por la consola asociada al proceso de llamada.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleOutputCP
- wincon/SetConsoleOutputCP
- SetConsoleOutputCP
MS-HAID:
- '\_win32\_setconsoleoutputcp'
- base.setconsoleoutputcp
- consoles.setconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0b41e66b-ca19-4d69-9f39-92da158344ef
topic_type:
- apiref
api_name:
- SetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: ae1f3970af6c8db1ebedc29e0644ed001258ecc5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061073"
---
# <a name="setconsoleoutputcp-function"></a><span data-ttu-id="9878b-104">SetConsoleOutputCP función)</span><span class="sxs-lookup"><span data-stu-id="9878b-104">SetConsoleOutputCP function</span></span>


<span data-ttu-id="9878b-105">Establece la página de códigos de salida utilizada por la consola asociada al proceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="9878b-105">Sets the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="9878b-106">Una consola usa su página de códigos de salida para traducir los valores de caracteres escritos por las distintas funciones de salida en las imágenes que se muestran en la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="9878b-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

<a name="syntax"></a><span data-ttu-id="9878b-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9878b-107">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleOutputCP(
  _In_ UINT wCodePageID
);
```

<a name="parameters"></a><span data-ttu-id="9878b-108">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9878b-108">Parameters</span></span>
----------

<span data-ttu-id="9878b-109">*wCodePageID* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="9878b-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="9878b-110">Identificador de la página de códigos que se va a establecer.</span><span class="sxs-lookup"><span data-stu-id="9878b-110">The identifier of the code page to set.</span></span> <span data-ttu-id="9878b-111">Para obtener más información, vea la sección Comentarios.</span><span class="sxs-lookup"><span data-stu-id="9878b-111">For more information, see Remarks.</span></span>

<a name="return-value"></a><span data-ttu-id="9878b-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="9878b-112">Return value</span></span>
------------

<span data-ttu-id="9878b-113">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="9878b-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="9878b-114">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="9878b-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="9878b-115">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="9878b-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="9878b-116">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9878b-116">Remarks</span></span>
-------

<span data-ttu-id="9878b-117">Una página de códigos asigna códigos de caracteres de 256 a caracteres individuales.</span><span class="sxs-lookup"><span data-stu-id="9878b-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="9878b-118">Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas.</span><span class="sxs-lookup"><span data-stu-id="9878b-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="9878b-119">Si la fuente actual es una fuente Unicode de punto fijo, **SetConsoleOutputCP** cambia la asignación de los valores de caracteres en el conjunto de glifos de la fuente, en lugar de cargar una fuente independiente cada vez que se llama.</span><span class="sxs-lookup"><span data-stu-id="9878b-119">If the current font is a fixed-pitch Unicode font, **SetConsoleOutputCP** changes the mapping of the character values into the glyph set of the font, rather than loading a separate font each time it is called.</span></span> <span data-ttu-id="9878b-120">Esto afecta al modo en que se muestran los caracteres extendidos (valor ASCII superior a 127) en una ventana de consola.</span><span class="sxs-lookup"><span data-stu-id="9878b-120">This affects how extended characters (ASCII value greater than 127) are displayed in a console window.</span></span> <span data-ttu-id="9878b-121">Sin embargo, si la fuente actual es una fuente de trama, **SetConsoleOutputCP** no afecta al modo en que se muestran los caracteres extendidos.</span><span class="sxs-lookup"><span data-stu-id="9878b-121">However, if the current font is a raster font, **SetConsoleOutputCP** does not affect how extended characters are displayed.</span></span>

<span data-ttu-id="9878b-122">Para buscar las páginas de códigos que el sistema operativo instala o admite, utilice la función [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) .</span><span class="sxs-lookup"><span data-stu-id="9878b-122">To find the code pages that are installed or supported by the operating system, use the [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) function.</span></span> <span data-ttu-id="9878b-123">Los identificadores de las páginas de códigos disponibles en el equipo local también se almacenan en el registro con la siguiente clave:</span><span class="sxs-lookup"><span data-stu-id="9878b-123">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

<span data-ttu-id="9878b-124">**HKEY \_ local \_ Machine \\ System \\ CurrentControlSet \\ control de la página de \\ \\ códigos NLS**</span><span class="sxs-lookup"><span data-stu-id="9878b-124">**HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Nls\\CodePage**</span></span>

<span data-ttu-id="9878b-125">Sin embargo, es mejor usar [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) para enumerar las páginas de códigos, ya que el registro puede diferir en diferentes versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="9878b-125">However, it is better to use [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>
<span data-ttu-id="9878b-126">Para determinar si una página de códigos determinada es válida, utilice la función [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) .</span><span class="sxs-lookup"><span data-stu-id="9878b-126">To determine whether a particular code page is valid, use the [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) function.</span></span> <span data-ttu-id="9878b-127">Para recuperar más información sobre una página de códigos, incluido su nombre, utilice la función [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .</span><span class="sxs-lookup"><span data-stu-id="9878b-127">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span> <span data-ttu-id="9878b-128">Para obtener una lista de los identificadores de página de códigos disponibles, vea [identificadores de páginas de códigos](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span><span class="sxs-lookup"><span data-stu-id="9878b-128">For a list of available code page identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="9878b-129">Para determinar la página de códigos de salida actual de la consola, use la función [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="9878b-129">To determine a console's current output code page, use the [**GetConsoleOutputCP**](getconsoleoutputcp.md) function.</span></span> <span data-ttu-id="9878b-130">Para establecer y recuperar una página de códigos de entrada de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) y [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="9878b-130">To set and retrieve a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

<a name="requirements"></a><span data-ttu-id="9878b-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9878b-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="9878b-132">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="9878b-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="9878b-133">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="9878b-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="9878b-134">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="9878b-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="9878b-135">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="9878b-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="9878b-136">Encabezado</span><span class="sxs-lookup"><span data-stu-id="9878b-136">Header</span></span></p></td>
<td><span data-ttu-id="9878b-137">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="9878b-137">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="9878b-138">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="9878b-138">Library</span></span></p></td>
<td><span data-ttu-id="9878b-139">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="9878b-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="9878b-140">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="9878b-140">DLL</span></span></p></td>
<td><span data-ttu-id="9878b-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9878b-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="9878b-142"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="9878b-142"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="9878b-143">Páginas de códigos de la consola</span><span class="sxs-lookup"><span data-stu-id="9878b-143">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="9878b-144">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="9878b-144">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="9878b-145">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="9878b-145">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="9878b-146">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="9878b-146">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="9878b-147">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="9878b-147">**SetConsoleCP**</span></span>](setconsolecp.md)

 

 




