---
title: SetConsoleTitle función)
description: Vea la información de referencia sobre la función SetConsoleTitle, que establece el título de la ventana de la consola actual.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
f1_keywords:
- consoleapi2/SetConsoleTitle
- wincon/SetConsoleTitle
- SetConsoleTitle
- consoleapi2/SetConsoleTitleA
- wincon/SetConsoleTitleA
- SetConsoleTitleA
- consoleapi2/SetConsoleTitleW
- wincon/SetConsoleTitleW
- SetConsoleTitleW
MS-HAID:
- '\_win32\_setconsoletitle'
- base.setconsoletitle
- consoles.setconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f1db449b-0dd0-4d61-bb79-b7da9a5168f4
topic_type:
- apiref
api_name:
- SetConsoleTitle
- SetConsoleTitleA
- SetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: e1789243fd5c184221dd53038d8ec87c9b010749
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89061055"
---
# <a name="setconsoletitle-function"></a><span data-ttu-id="e52bf-104">SetConsoleTitle función)</span><span class="sxs-lookup"><span data-stu-id="e52bf-104">SetConsoleTitle function</span></span>


<span data-ttu-id="e52bf-105">Establece el título de la ventana de la consola actual.</span><span class="sxs-lookup"><span data-stu-id="e52bf-105">Sets the title for the current console window.</span></span>

<a name="syntax"></a><span data-ttu-id="e52bf-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e52bf-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleTitle(
  _In_ LPCTSTR lpConsoleTitle
);
```

<a name="parameters"></a><span data-ttu-id="e52bf-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e52bf-107">Parameters</span></span>
----------

<span data-ttu-id="e52bf-108">*lpConsoleTitle* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="e52bf-108">*lpConsoleTitle* \[in\]</span></span>  
<span data-ttu-id="e52bf-109">Cadena que se va a mostrar en la barra de título de la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="e52bf-109">The string to be displayed in the title bar of the console window.</span></span> <span data-ttu-id="e52bf-110">El tamaño total debe ser inferior a 64 k.</span><span class="sxs-lookup"><span data-stu-id="e52bf-110">The total size must be less than 64K.</span></span>

<a name="return-value"></a><span data-ttu-id="e52bf-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="e52bf-111">Return value</span></span>
------------

<span data-ttu-id="e52bf-112">Si la función se ejecuta correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="e52bf-112">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e52bf-113">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="e52bf-113">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e52bf-114">Para obtener información de error extendida, llame a [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span><span class="sxs-lookup"><span data-stu-id="e52bf-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="e52bf-115">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e52bf-115">Remarks</span></span>
-------

<span data-ttu-id="e52bf-116">Cuando finaliza el proceso, el sistema restaura el título original de la consola.</span><span class="sxs-lookup"><span data-stu-id="e52bf-116">When the process terminates, the system restores the original console title.</span></span>

<span data-ttu-id="e52bf-117">Esta función usa caracteres Unicode o caracteres de 8 bits de la página de códigos actual de la consola.</span><span class="sxs-lookup"><span data-stu-id="e52bf-117">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="e52bf-118">La página de códigos de la consola tiene como valor predeterminado la página de códigos OEM del sistema.</span><span class="sxs-lookup"><span data-stu-id="e52bf-118">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="e52bf-119">Para cambiar la página de códigos de la consola, use las funciones [**SetConsoleCP**](setconsolecp.md) o [**SetConsoleOutputCP**](setconsoleoutputcp.md) , o bien use los comandos **chcp** o **mode con CP Select =** .</span><span class="sxs-lookup"><span data-stu-id="e52bf-119">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="e52bf-120">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="e52bf-120">Examples</span></span>
--------

<span data-ttu-id="e52bf-121">En el ejemplo siguiente se muestra cómo recuperar y modificar el título de la consola.</span><span class="sxs-lookup"><span data-stu-id="e52bf-121">The following example shows how to retrieve and modify the console title.</span></span>

```C
#include <windows.h>
#include <tchar.h>
#include <conio.h>
#include <strsafe.h>

int main( void )
{
   TCHAR szOldTitle[MAX_PATH];
   TCHAR szNewTitle[MAX_PATH];

   // Save current console title.

   if( GetConsoleTitle(szOldTitle, MAX_PATH) )
   {
      // Build new console title string.

      StringCchPrintf(szNewTitle, MAX_PATH, TEXT("TEST: %s"), szOldTitle);

      // Set console title to new title
      if( !SetConsoleTitle(szNewTitle) )
      {
         _tprintf(TEXT("SetConsoleTitle failed (%d)\n"), GetLastError());
         return 1;
      }
      else
      {
         _tprintf(TEXT("SetConsoleTitle succeeded.\n"));
      }
   }
   return 0;
}
```

<a name="requirements"></a><span data-ttu-id="e52bf-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e52bf-122">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e52bf-123">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="e52bf-123">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="e52bf-124">Windows 2000 Professional [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="e52bf-124">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e52bf-125">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="e52bf-125">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="e52bf-126">Windows 2000 Server [solo aplicaciones de escritorio]</span><span class="sxs-lookup"><span data-stu-id="e52bf-126">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e52bf-127">Encabezado</span><span class="sxs-lookup"><span data-stu-id="e52bf-127">Header</span></span></p></td>
<td><span data-ttu-id="e52bf-128">ConsoleApi2. h (a través de winCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="e52bf-128">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e52bf-129">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="e52bf-129">Library</span></span></p></td>
<td><span data-ttu-id="e52bf-130">Kernel32. lib</span><span class="sxs-lookup"><span data-stu-id="e52bf-130">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e52bf-131">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="e52bf-131">DLL</span></span></p></td>
<td><span data-ttu-id="e52bf-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e52bf-132">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e52bf-133">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="e52bf-133">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="e52bf-134"><strong>SetConsoleTitleW</strong> (Unicode) y <strong>SetConsoleTitleA</strong> (ANSI)</span><span class="sxs-lookup"><span data-stu-id="e52bf-134"><strong>SetConsoleTitleW</strong> (Unicode) and <strong>SetConsoleTitleA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="e52bf-135"><span id="see_also"></span>Vea también</span><span class="sxs-lookup"><span data-stu-id="e52bf-135"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="e52bf-136">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="e52bf-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e52bf-137">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="e52bf-137">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="e52bf-138">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="e52bf-138">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="e52bf-139">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="e52bf-139">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="e52bf-140">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="e52bf-140">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

 

 




