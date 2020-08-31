---
title: GetConsoleTitle función)
description: Recupera el título y el tamaño del título de la ventana de la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/GetConsoleTitle
- wincon/GetConsoleTitle
- GetConsoleTitle
- consoleapi2/GetConsoleTitleA
- wincon/GetConsoleTitleA
- GetConsoleTitleA
- consoleapi2/GetConsoleTitleW
- wincon/GetConsoleTitleW
- GetConsoleTitleW
MS-HAID:
- '\_win32\_getconsoletitle'
- base.getconsoletitle
- consoles.getconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c58bba36-9813-4bdc-83bf-30d55f8d7d79
topic_type:
- apiref
api_name:
- GetConsoleTitle
- GetConsoleTitleA
- GetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-Ms-Win-Core-Console-Ansi-L2-1-0.dll
- Kernel32Legacy.dll
api_type:
- DllExport
ms.openlocfilehash: 5b8e78e65e52c3f10be14afa6a122fa12609a2eb
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060656"
---
# <a name="getconsoletitle-function"></a><span data-ttu-id="3f2e7-104">GetConsoleTitle función)</span><span class="sxs-lookup"><span data-stu-id="3f2e7-104">GetConsoleTitle function</span></span>


<span data-ttu-id="3f2e7-105">Recupera el título de la ventana de la consola actual.</span><span class="sxs-lookup"><span data-stu-id="3f2e7-105">Retrieves the title for the current console window.</span></span>

<a name="syntax"></a><span data-ttu-id="3f2e7-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3f2e7-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a><span data-ttu-id="3f2e7-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3f2e7-107">Parameters</span></span>
----------

<span data-ttu-id="3f2e7-108">*lpConsoleTitle* \[ enuncia\]</span><span class="sxs-lookup"><span data-stu-id="3f2e7-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="3f2e7-109">Un puntero a un búfer que recibe una cadena terminada en null que contiene el título.</span><span class="sxs-lookup"><span data-stu-id="3f2e7-109">A pointer to a buffer that receives a null-terminated string containing the title.</span></span> <span data-ttu-id="3f2e7-110">Si el búfer es demasiado pequeño para almacenar el título, la función almacena tantos caracteres del título como quepan en el búfer, terminando con un terminador null.</span><span class="sxs-lookup"><span data-stu-id="3f2e7-110">If the buffer is too small to store the title, the function stores as many characters of the title as will fit in the buffer, ending with a null terminator.</span></span>

<span data-ttu-id="3f2e7-111">*nSize* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="3f2e7-111">*nSize* \[in\]</span></span>  
<span data-ttu-id="3f2e7-112">Tamaño del búfer al que apunta el parámetro *lpConsoleTitle* , en caracteres.</span><span class="sxs-lookup"><span data-stu-id="3f2e7-112">The size of the buffer pointed to by the *lpConsoleTitle* parameter, in characters.</span></span>

<a name="return-value"></a><span data-ttu-id="3f2e7-113">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="3f2e7-113">Return value</span></span>
------------

<span data-ttu-id="3f2e7-114">Si la función se ejecuta correctamente, el valor devuelto es la longitud del título de la ventana de la consola, en caracteres.</span><span class="sxs-lookup"><span data-stu-id="3f2e7-114">If the function succeeds, the return value is the length of the console window's title, in characters.</span></span>

<span data-ttu-id="3f2e7-115">Si se produce un error en la función, el valor devuelto es cero y [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) devuelve el código de error.</span><span class="sxs-lookup"><span data-stu-id="3f2e7-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

<a name="remarks"></a><span data-ttu-id="3f2e7-116">Observaciones</span><span class="sxs-lookup"><span data-stu-id="3f2e7-116">Remarks</span></span>
-------

<span data-ttu-id="3f2e7-117">Para establecer el título de una ventana de la consola, use la función [**SetConsoleTitle**](setconsoletitle.md) .</span><span class="sxs-lookup"><span data-stu-id="3f2e7-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="3f2e7-118">Para recuperar la cadena de título original, utilice la función [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) .</span><span class="sxs-lookup"><span data-stu-id="3f2e7-118">To retrieve the original title string, use the [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) function.</span></span>

<span data-ttu-id="3f2e7-119">Esta función usa caracteres Unicode o caracteres de 8 bits de la página de códigos actual de la consola.</span><span class="sxs-lookup"><span data-stu-id="3f2e7-119">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="3f2e7-120">La página de códigos de la consola tiene como valor predeterminado la página de códigos OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="3f2e7-120">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="3f2e7-121">Para cambiar la página de códigos de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) , o bien use los comandos **chcp** o **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="3f2e7-121">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="3f2e7-122">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="3f2e7-122">Examples</span></span>
--------

<span data-ttu-id="3f2e7-123">Para obtener un ejemplo, vea [**SetConsoleTitle**](setconsoletitle.md).</span><span class="sxs-lookup"><span data-stu-id="3f2e7-123">For an example, see [**SetConsoleTitle**](setconsoletitle.md).</span></span>

<a name="requirements"></a><span data-ttu-id="3f2e7-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3f2e7-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="3f2e7-125">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="3f2e7-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="3f2e7-126">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="3f2e7-126">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3f2e7-127">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="3f2e7-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="3f2e7-128">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="3f2e7-128">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3f2e7-129">Encabezado</span><span class="sxs-lookup"><span data-stu-id="3f2e7-129">Header</span></span></p></td>
<td><span data-ttu-id="3f2e7-130">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="3f2e7-130">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3f2e7-131">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="3f2e7-131">Library</span></span></p></td>
<td><span data-ttu-id="3f2e7-132">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="3f2e7-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3f2e7-133">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="3f2e7-133">DLL</span></span></p></td>
<td><span data-ttu-id="3f2e7-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3f2e7-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3f2e7-135">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="3f2e7-135">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="3f2e7-136"><strong>GetConsoleTitleW</strong> (Unicode) y <strong>GetConsoleTitleA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="3f2e7-136"><strong>GetConsoleTitleW</strong> (Unicode) and <strong>GetConsoleTitleA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="3f2e7-137"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="3f2e7-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="3f2e7-138">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="3f2e7-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3f2e7-139">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="3f2e7-139">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="3f2e7-140">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="3f2e7-140">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="3f2e7-141">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="3f2e7-141">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="3f2e7-142">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="3f2e7-142">**SetConsoleTitle**</span></span>](setconsoletitle.md)

 

 




