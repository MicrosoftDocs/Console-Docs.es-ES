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
ms.openlocfilehash: 644f4d925b31da94f42a465d4bce21bb2dc2ecf9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039413"
---
# <a name="setconsolecp-function"></a><span data-ttu-id="cbb3d-104">SetConsoleCP función)</span><span class="sxs-lookup"><span data-stu-id="cbb3d-104">SetConsoleCP function</span></span>

<span data-ttu-id="cbb3d-105">Establece la página de códigos de entrada utilizada por la consola asociada al proceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="cbb3d-105">Sets the input code page used by the console associated with the calling process.</span></span> <span data-ttu-id="cbb3d-106">Una consola usa su página de códigos de entrada para traducir la entrada del teclado en el valor de carácter correspondiente.</span><span class="sxs-lookup"><span data-stu-id="cbb3d-106">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span>

## <a name="syntax"></a><span data-ttu-id="cbb3d-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="cbb3d-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a><span data-ttu-id="cbb3d-108">Parámetros</span><span class="sxs-lookup"><span data-stu-id="cbb3d-108">Parameters</span></span>

<span data-ttu-id="cbb3d-109">*wCodePageID* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="cbb3d-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="cbb3d-110">Identificador de la página de códigos que se va a establecer.</span><span class="sxs-lookup"><span data-stu-id="cbb3d-110">The identifier of the code page to be set.</span></span> <span data-ttu-id="cbb3d-111">Para obtener más información, vea la sección Comentarios.</span><span class="sxs-lookup"><span data-stu-id="cbb3d-111">For more information, see Remarks.</span></span>

## <a name="return-value"></a><span data-ttu-id="cbb3d-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="cbb3d-112">Return value</span></span>

<span data-ttu-id="cbb3d-113">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="cbb3d-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="cbb3d-114">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="cbb3d-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="cbb3d-115">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="cbb3d-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="cbb3d-116">Comentarios</span><span class="sxs-lookup"><span data-stu-id="cbb3d-116">Remarks</span></span>

<span data-ttu-id="cbb3d-117">Una página de códigos asigna códigos de caracteres de 256 a caracteres individuales.</span><span class="sxs-lookup"><span data-stu-id="cbb3d-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="cbb3d-118">Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas.</span><span class="sxs-lookup"><span data-stu-id="cbb3d-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="cbb3d-119">Para buscar las páginas de códigos que el sistema operativo instala o admite, utilice la función [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) .</span><span class="sxs-lookup"><span data-stu-id="cbb3d-119">To find the code pages that are installed or supported by the operating system, use the [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) function.</span></span> <span data-ttu-id="cbb3d-120">Los identificadores de las páginas de códigos disponibles en el equipo local también se almacenan en el registro con la siguiente clave:</span><span class="sxs-lookup"><span data-stu-id="cbb3d-120">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

<span data-ttu-id="cbb3d-121">Sin embargo, es mejor usar [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) para enumerar las páginas de códigos, ya que el registro puede diferir en diferentes versiones de Windows.</span><span class="sxs-lookup"><span data-stu-id="cbb3d-121">However, it is better to use [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>

<span data-ttu-id="cbb3d-122">Para determinar si una página de códigos determinada es válida, utilice la función [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) .</span><span class="sxs-lookup"><span data-stu-id="cbb3d-122">To determine whether a particular code page is valid, use the [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) function.</span></span> <span data-ttu-id="cbb3d-123">Para recuperar más información sobre una página de códigos, incluido su nombre, utilice la función [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) .</span><span class="sxs-lookup"><span data-stu-id="cbb3d-123">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span> <span data-ttu-id="cbb3d-124">Para obtener una lista de los identificadores de página de códigos disponibles, vea [identificadores de páginas de códigos](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span><span class="sxs-lookup"><span data-stu-id="cbb3d-124">For a list of available code page identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="cbb3d-125">Para determinar la página de códigos de entrada actual de la consola, use la función [**GetConsoleCP**](getconsolecp.md) .</span><span class="sxs-lookup"><span data-stu-id="cbb3d-125">To determine a console's current input code page, use the [**GetConsoleCP**](getconsolecp.md) function.</span></span> <span data-ttu-id="cbb3d-126">Para establecer y recuperar la página de códigos de salida de una consola, use las funciones [**SetConsoleOutputCP**](setconsoleoutputcp.md) y [**GetConsoleOutputCP**](getconsoleoutputcp.md) .</span><span class="sxs-lookup"><span data-stu-id="cbb3d-126">To set and retrieve a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="cbb3d-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cbb3d-127">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="cbb3d-128">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="cbb3d-128">Minimum supported client</span></span> | <span data-ttu-id="cbb3d-129">Solo aplicaciones de escritorio de Windows 2000 Professional \[\]</span><span class="sxs-lookup"><span data-stu-id="cbb3d-129">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="cbb3d-130">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="cbb3d-130">Minimum supported server</span></span> | <span data-ttu-id="cbb3d-131">Solo aplicaciones de escritorio de Windows 2000 Server \[\]</span><span class="sxs-lookup"><span data-stu-id="cbb3d-131">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="cbb3d-132">Encabezado</span><span class="sxs-lookup"><span data-stu-id="cbb3d-132">Header</span></span> | <span data-ttu-id="cbb3d-133">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="cbb3d-133">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="cbb3d-134">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="cbb3d-134">Library</span></span> | <span data-ttu-id="cbb3d-135">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="cbb3d-135">Kernel32.lib</span></span> |
| <span data-ttu-id="cbb3d-136">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="cbb3d-136">DLL</span></span> | <span data-ttu-id="cbb3d-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="cbb3d-137">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="cbb3d-138">Consulte también</span><span class="sxs-lookup"><span data-stu-id="cbb3d-138">See also</span></span>

[<span data-ttu-id="cbb3d-139">Páginas de código de la consola</span><span class="sxs-lookup"><span data-stu-id="cbb3d-139">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="cbb3d-140">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="cbb3d-140">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="cbb3d-141">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="cbb3d-141">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="cbb3d-142">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="cbb3d-142">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="cbb3d-143">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="cbb3d-143">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)
