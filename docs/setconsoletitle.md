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
ms.openlocfilehash: 5955bba0c7b317dbcdbc9593b60bfb3092376dc1
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358545"
---
# <a name="setconsoletitle-function"></a><span data-ttu-id="d34dc-104">SetConsoleTitle función)</span><span class="sxs-lookup"><span data-stu-id="d34dc-104">SetConsoleTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="d34dc-105">Establece el título de la ventana de la consola actual.</span><span class="sxs-lookup"><span data-stu-id="d34dc-105">Sets the title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="d34dc-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d34dc-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleTitle(
  _In_ LPCTSTR lpConsoleTitle
);
```

## <a name="parameters"></a><span data-ttu-id="d34dc-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="d34dc-107">Parameters</span></span>

<span data-ttu-id="d34dc-108">*lpConsoleTitle* \[ de\]</span><span class="sxs-lookup"><span data-stu-id="d34dc-108">*lpConsoleTitle* \[in\]</span></span>  
<span data-ttu-id="d34dc-109">Cadena que se va a mostrar en la barra de título de la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="d34dc-109">The string to be displayed in the title bar of the console window.</span></span> <span data-ttu-id="d34dc-110">El tamaño total debe ser inferior a 64 k.</span><span class="sxs-lookup"><span data-stu-id="d34dc-110">The total size must be less than 64K.</span></span>

## <a name="return-value"></a><span data-ttu-id="d34dc-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="d34dc-111">Return value</span></span>

<span data-ttu-id="d34dc-112">Si la función se realiza correctamente, el valor devuelto es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="d34dc-112">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d34dc-113">Si la función no se realiza correctamente, el valor devuelto es cero.</span><span class="sxs-lookup"><span data-stu-id="d34dc-113">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d34dc-114">Para obtener información de error extendida, llame a [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span><span class="sxs-lookup"><span data-stu-id="d34dc-114">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="d34dc-115">Comentarios</span><span class="sxs-lookup"><span data-stu-id="d34dc-115">Remarks</span></span>

<span data-ttu-id="d34dc-116">Cuando finaliza el proceso, el sistema restaura el título original de la consola.</span><span class="sxs-lookup"><span data-stu-id="d34dc-116">When the process terminates, the system restores the original console title.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="d34dc-117">Esta API tiene un **[terminal virtual](console-virtual-terminal-sequences.md)** equivalente en las secuencias de **[título de ventana](console-virtual-terminal-sequences.md#window-title)** .</span><span class="sxs-lookup"><span data-stu-id="d34dc-117">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[window title](console-virtual-terminal-sequences.md#window-title)** sequences.</span></span> <span data-ttu-id="d34dc-118">Se recomiendan las _secuencias de terminal virtuales_ para todo el desarrollo nuevo y en curso.</span><span class="sxs-lookup"><span data-stu-id="d34dc-118">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="d34dc-119">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="d34dc-119">Examples</span></span>

<span data-ttu-id="d34dc-120">En el ejemplo siguiente se muestra cómo recuperar y modificar el título de la consola.</span><span class="sxs-lookup"><span data-stu-id="d34dc-120">The following example shows how to retrieve and modify the console title.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="d34dc-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d34dc-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="d34dc-122">Cliente mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="d34dc-122">Minimum supported client</span></span> | <span data-ttu-id="d34dc-123">\[Solo aplicaciones de escritorio\] de Windows 2000 Professional</span><span class="sxs-lookup"><span data-stu-id="d34dc-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="d34dc-124">Servidor mínimo compatible</span><span class="sxs-lookup"><span data-stu-id="d34dc-124">Minimum supported server</span></span> | <span data-ttu-id="d34dc-125">\[Solo aplicaciones de escritorio\] de Windows 2000 Server</span><span class="sxs-lookup"><span data-stu-id="d34dc-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="d34dc-126">Encabezado</span><span class="sxs-lookup"><span data-stu-id="d34dc-126">Header</span></span> | <span data-ttu-id="d34dc-127">ConsoleApi2. h (a través de WinCon. h, include Windows. h)</span><span class="sxs-lookup"><span data-stu-id="d34dc-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="d34dc-128">Biblioteca</span><span class="sxs-lookup"><span data-stu-id="d34dc-128">Library</span></span> | <span data-ttu-id="d34dc-129">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="d34dc-129">Kernel32.lib</span></span> |
| <span data-ttu-id="d34dc-130">Archivo DLL</span><span class="sxs-lookup"><span data-stu-id="d34dc-130">DLL</span></span> | <span data-ttu-id="d34dc-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d34dc-131">Kernel32.dll</span></span> |
| <span data-ttu-id="d34dc-132">Nombres Unicode y ANSI</span><span class="sxs-lookup"><span data-stu-id="d34dc-132">Unicode and ANSI names</span></span> | <span data-ttu-id="d34dc-133">**SetConsoleTitleW** (Unicode) y **SetConsoleTitleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="d34dc-133">**SetConsoleTitleW** (Unicode) and **SetConsoleTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="d34dc-134">Vea también</span><span class="sxs-lookup"><span data-stu-id="d34dc-134">See also</span></span>

[<span data-ttu-id="d34dc-135">Funciones de la consola</span><span class="sxs-lookup"><span data-stu-id="d34dc-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d34dc-136">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="d34dc-136">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="d34dc-137">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="d34dc-137">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="d34dc-138">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="d34dc-138">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="d34dc-139">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="d34dc-139">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)