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
ms.openlocfilehash: 96086720ee2c4ae787d2b52eee5439d54f081b8e
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358345"
---
# <a name="getconsolefontsize-function"></a><span data-ttu-id="898dc-104">GetConsoleFontSize función)</span><span class="sxs-lookup"><span data-stu-id="898dc-104">GetConsoleFontSize function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="898dc-105">Recupera el tamaño de la fuente utilizada por el búfer de pantalla de la consola especificado.</span><span class="sxs-lookup"><span data-stu-id="898dc-105">Retrieves the size of the font used by the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="898dc-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="898dc-106">Syntax</span></span>

```C
COORD WINAPI GetConsoleFontSize(
  _In_ HANDLE hConsoleOutput,
  _In_ DWORD  nFont
);
```

## <a name="parameters"></a><span data-ttu-id="898dc-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="898dc-107">Parameters</span></span>

<span data-ttu-id="898dc-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="898dc-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="898dc-109">Identificador del búfer de pantalla de la consola.</span><span class="sxs-lookup"><span data-stu-id="898dc-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="898dc-110">El identificador debe tener derecho de acceso de **GENERIC\_READ**.</span><span class="sxs-lookup"><span data-stu-id="898dc-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="898dc-111">Para obtener más información, consulte [Seguridad y derechos de acceso del búfer de la consola](console-buffer-security-and-access-rights.md).</span><span class="sxs-lookup"><span data-stu-id="898dc-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="898dc-112">*nFont* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="898dc-112">*nFont* \[in\]</span></span>  
<span data-ttu-id="898dc-113">Índice de la fuente cuyo tamaño se va a recuperar.</span><span class="sxs-lookup"><span data-stu-id="898dc-113">The index of the font whose size is to be retrieved.</span></span> <span data-ttu-id="898dc-114">Este índice se obtiene mediante una llamada a la función [**GetCurrentConsoleFont**](getcurrentconsolefont.md) .</span><span class="sxs-lookup"><span data-stu-id="898dc-114">This index is obtained by calling the [**GetCurrentConsoleFont**](getcurrentconsolefont.md) function.</span></span>

## <a name="return-value"></a><span data-ttu-id="898dc-115">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="898dc-115">Return value</span></span>

<span data-ttu-id="898dc-116">Si la función se ejecuta correctamente, el valor devuelto es una estructura de [**coordenadas**](coord-str.md) que contiene el ancho y el alto de cada carácter de la fuente, en unidades lógicas.</span><span class="sxs-lookup"><span data-stu-id="898dc-116">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="898dc-117">El miembro **X** contiene el ancho, mientras que el miembro **Y** contiene el alto.</span><span class="sxs-lookup"><span data-stu-id="898dc-117">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="898dc-118">Si se produce un error en la función, el ancho y el alto son cero.</span><span class="sxs-lookup"><span data-stu-id="898dc-118">If the function fails, the width and the height are zero.</span></span> <span data-ttu-id="898dc-119">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="898dc-119">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="898dc-120">Comentarios</span><span class="sxs-lookup"><span data-stu-id="898dc-120">Remarks</span></span>

<span data-ttu-id="898dc-121">Para compilar una aplicación que usa esta función, defina **\_ Win32 \_ WinNT** como 0x0500 o posterior.</span><span class="sxs-lookup"><span data-stu-id="898dc-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="898dc-122">Para obtener más información, consulte [uso de los encabezados de Windows](/windows/win32/winprog/using-the-windows-headers).</span><span class="sxs-lookup"><span data-stu-id="898dc-122">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="898dc-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="898dc-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="898dc-124">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="898dc-124">Minimum supported client</span></span> | <span data-ttu-id="898dc-125">Solo aplicaciones de escritorio de Windows XP \[\]</span><span class="sxs-lookup"><span data-stu-id="898dc-125">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="898dc-126">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="898dc-126">Minimum supported server</span></span> | <span data-ttu-id="898dc-127">Solo aplicaciones de escritorio de Windows Server 2003 \[\]</span><span class="sxs-lookup"><span data-stu-id="898dc-127">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="898dc-128">Encabezado</span><span class="sxs-lookup"><span data-stu-id="898dc-128">Header</span></span> | <span data-ttu-id="898dc-129">ConsoleApi3. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="898dc-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="898dc-130">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="898dc-130">Library</span></span> | <span data-ttu-id="898dc-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="898dc-131">Kernel32.lib</span></span> |
| <span data-ttu-id="898dc-132">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="898dc-132">DLL</span></span> | <span data-ttu-id="898dc-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="898dc-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="898dc-134">Vea también</span><span class="sxs-lookup"><span data-stu-id="898dc-134">See also</span></span>

[<span data-ttu-id="898dc-135">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="898dc-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="898dc-136">Búferes de pantalla de la consola</span><span class="sxs-lookup"><span data-stu-id="898dc-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="898dc-137">**COORDS**</span><span class="sxs-lookup"><span data-stu-id="898dc-137">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="898dc-138">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="898dc-138">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)