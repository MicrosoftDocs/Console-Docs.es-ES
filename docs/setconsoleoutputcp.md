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
ms.openlocfilehash: abe04e2be5256097e19742bfbc8566c3ab613c4d
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357525"
---
# <a name="setconsoleoutputcp-function"></a><span data-ttu-id="13efd-104">SetConsoleOutputCP función)</span><span class="sxs-lookup"><span data-stu-id="13efd-104">SetConsoleOutputCP function</span></span>

<span data-ttu-id="13efd-105">Establece la página de códigos de salida utilizada por la consola asociada al proceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="13efd-105">Sets the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="13efd-106">Una consola usa su página de códigos de salida para traducir los valores de caracteres escritos por las distintas funciones de salida en las imágenes que se muestran en la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="13efd-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="13efd-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="13efd-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleOutputCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a><span data-ttu-id="13efd-108">Parámetros</span><span class="sxs-lookup"><span data-stu-id="13efd-108">Parameters</span></span>

<span data-ttu-id="13efd-109">*wCodePageID* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="13efd-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="13efd-110">Identificador de la página de códigos que se va a establecer.</span><span class="sxs-lookup"><span data-stu-id="13efd-110">The identifier of the code page to set.</span></span> <span data-ttu-id="13efd-111">Para obtener más información, vea la sección Comentarios.</span><span class="sxs-lookup"><span data-stu-id="13efd-111">For more information, see Remarks.</span></span>

## <a name="return-value"></a><span data-ttu-id="13efd-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="13efd-112">Return value</span></span>

<span data-ttu-id="13efd-113">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="13efd-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="13efd-114">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="13efd-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="13efd-115">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="13efd-115">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="13efd-116">Comentarios</span><span class="sxs-lookup"><span data-stu-id="13efd-116">Remarks</span></span>

<span data-ttu-id="13efd-117">Una página de códigos asigna códigos de caracteres de 256 a caracteres individuales.</span><span class="sxs-lookup"><span data-stu-id="13efd-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="13efd-118">Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas.</span><span class="sxs-lookup"><span data-stu-id="13efd-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="13efd-119">Si la fuente actual es una fuente Unicode de punto fijo, **SetConsoleOutputCP** cambia la asignación de los valores de caracteres en el conjunto de glifos de la fuente, en lugar de cargar una fuente independiente cada vez que se llama.</span><span class="sxs-lookup"><span data-stu-id="13efd-119">If the current font is a fixed-pitch Unicode font, **SetConsoleOutputCP** changes the mapping of the character values into the glyph set of the font, rather than loading a separate font each time it is called.</span></span> <span data-ttu-id="13efd-120">Esto afecta al modo en que se muestran los caracteres extendidos (valor ASCII superior a 127) en una ventana de consola.</span><span class="sxs-lookup"><span data-stu-id="13efd-120">This affects how extended characters (ASCII value greater than 127) are displayed in a console window.</span></span> <span data-ttu-id="13efd-121">Sin embargo, si la fuente actual es una fuente de trama, **SetConsoleOutputCP** no afecta al modo en que se muestran los caracteres extendidos.</span><span class="sxs-lookup"><span data-stu-id="13efd-121">However, if the current font is a raster font, **SetConsoleOutputCP** does not affect how extended characters are displayed.</span></span>

<span data-ttu-id="13efd-122">Para buscar las páginas de códigos que el sistema operativo instala o admite, utilice la función [EnumSystemCodePages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) .</span><span class="sxs-lookup"><span data-stu-id="13efd-122">To find the code pages that are installed or supported by the operating system, use the [EnumSystemCodePages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) function.</span></span> <span data-ttu-id="13efd-123">Los identificadores de las páginas de códigos disponibles en el equipo local también se almacenan en el registro con la siguiente clave:</span><span class="sxs-lookup"><span data-stu-id="13efd-123">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

<span data-ttu-id="13efd-124">Sin embargo, es mejor usar [EnumSystemCodePages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) para enumerar las páginas de códigos, ya que el registro puede diferir en diferentes versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="13efd-124">However, it is better to use [EnumSystemCodePages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>
<span data-ttu-id="13efd-125">Para determinar si una página de códigos determinada es válida, utilice la función [IsValidCodePage](/windows/win32/api/winnls/nf-winnls-isvalidcodepage) .</span><span class="sxs-lookup"><span data-stu-id="13efd-125">To determine whether a particular code page is valid, use the [IsValidCodePage](/windows/win32/api/winnls/nf-winnls-isvalidcodepage) function.</span></span> <span data-ttu-id="13efd-126">Para recuperar más información sobre una página de códigos, incluido su nombre, utilice la función [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) .</span><span class="sxs-lookup"><span data-stu-id="13efd-126">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) function.</span></span> <span data-ttu-id="13efd-127">Para obtener una lista de los identificadores de página de códigos disponibles, vea [identificadores de páginas de códigos](/windows/win32/intl/code-page-identifiers).</span><span class="sxs-lookup"><span data-stu-id="13efd-127">For a list of available code page identifiers, see [Code Page Identifiers](/windows/win32/intl/code-page-identifiers).</span></span>

<span data-ttu-id="13efd-128">Para determinar la página de códigos de salida actual de la consola, use la función [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="13efd-128">To determine a console's current output code page, use the [**GetConsoleOutputCP**](getconsoleoutputcp.md) function.</span></span> <span data-ttu-id="13efd-129">Para establecer y recuperar una página de códigos de entrada de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) y [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="13efd-129">To set and retrieve a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="13efd-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13efd-130">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="13efd-131">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="13efd-131">Minimum supported client</span></span> | <span data-ttu-id="13efd-132">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="13efd-132">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="13efd-133">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="13efd-133">Minimum supported server</span></span> | <span data-ttu-id="13efd-134">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="13efd-134">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="13efd-135">Encabezado</span><span class="sxs-lookup"><span data-stu-id="13efd-135">Header</span></span> | <span data-ttu-id="13efd-136">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="13efd-136">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="13efd-137">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="13efd-137">Library</span></span> | <span data-ttu-id="13efd-138">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="13efd-138">Kernel32.lib</span></span> |
| <span data-ttu-id="13efd-139">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="13efd-139">DLL</span></span> | <span data-ttu-id="13efd-140">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="13efd-140">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="13efd-141">Vea también</span><span class="sxs-lookup"><span data-stu-id="13efd-141">See also</span></span>

[<span data-ttu-id="13efd-142">Páginas de código de la consola</span><span class="sxs-lookup"><span data-stu-id="13efd-142">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="13efd-143">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="13efd-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="13efd-144">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="13efd-144">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="13efd-145">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="13efd-145">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="13efd-146">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="13efd-146">**SetConsoleCP**</span></span>](setconsolecp.md)