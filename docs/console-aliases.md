---
title: Alias de la consola
description: Describe los alias de la consola y cómo se usan para asignar cadenas de origen a cadenas de destino.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- base.console\_aliases
- consoles.console\_aliases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8169708b-83da-47ef-94be-eca3ca7d0a5b
ms.openlocfilehash: 10ee932ba8c09b8e28092d4289b7da64da749b76
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357835"
---
# <a name="console-aliases"></a><span data-ttu-id="bc442-104">Alias de la consola</span><span class="sxs-lookup"><span data-stu-id="bc442-104">Console Aliases</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="bc442-105">Los alias de consola se usan para asignar cadenas de origen a cadenas de destino.</span><span class="sxs-lookup"><span data-stu-id="bc442-105">Console aliases are used to map source strings to target strings.</span></span> <span data-ttu-id="bc442-106">Por ejemplo, puede definir un alias de consola que asigne "Test" a "CD \\ an \_ Very \_ Long \_ path \\ Test".</span><span class="sxs-lookup"><span data-stu-id="bc442-106">For example, you can define a console alias that maps "test" to "cd \\a\_very\_long\_path\\test".</span></span> <span data-ttu-id="bc442-107">Cuando escribe "Test" en la línea de comandos, el subsistema de consola expande el alias y ejecuta el comando de CD especificado.</span><span class="sxs-lookup"><span data-stu-id="bc442-107">When you type "test" at the command line, the console subsystem expands the alias and executes the specified cd command.</span></span>

<span data-ttu-id="bc442-108">Para definir un alias de la consola, use [**Doskey.exe**](/windows-server/administration/windows-commands/doskey) para crear una macro o use la función [**AddConsoleAlias**](addconsolealias.md) .</span><span class="sxs-lookup"><span data-stu-id="bc442-108">To define a console alias, use [**Doskey.exe**](/windows-server/administration/windows-commands/doskey) to create a macro, or use the [**AddConsoleAlias**](addconsolealias.md) function.</span></span> <span data-ttu-id="bc442-109">En el ejemplo siguiente se usa `Doskey.exe`:</span><span class="sxs-lookup"><span data-stu-id="bc442-109">The following example uses `Doskey.exe`:</span></span>

<span data-ttu-id="bc442-110">**doskey test = CD \\** una **\\ prueba** <em>de \_ \_ ruta de \_ acceso muy larga</em></span><span class="sxs-lookup"><span data-stu-id="bc442-110">**doskey test=cd \\**<em>a\_very\_long\_path</em>**\\test**</span></span>

<span data-ttu-id="bc442-111">La siguiente llamada a [**AddConsoleAlias**](addconsolealias.md) crea el mismo alias de consola:</span><span class="sxs-lookup"><span data-stu-id="bc442-111">The following call to [**AddConsoleAlias**](addconsolealias.md) creates the same console alias:</span></span>

``` C
AddConsoleAlias( TEXT("test"),
                 TEXT("cd \\<a_very_long_path>\\test"),
                 TEXT("cmd.exe"));
```

<span data-ttu-id="bc442-112">Para agregar parámetros a una macro de alias de consola mediante `Doskey.exe` , utilice los parámetros de lote `$1` a través de `$9` .</span><span class="sxs-lookup"><span data-stu-id="bc442-112">To add parameters to a console alias macro using `Doskey.exe`, use the batch parameters `$1` through `$9`.</span></span> <span data-ttu-id="bc442-113">Para obtener más información sobre los códigos especiales que se pueden usar en las definiciones de macro de Doskey, vea la ayuda de la línea de comandos de `Doskey.exe` o [doskey](/previous-versions/windows/it-pro/windows-xp/bb490894(v=technet.10)) en TechNet.</span><span class="sxs-lookup"><span data-stu-id="bc442-113">For more information on the special codes that can be used in Doskey macro definitions, see the command-line help for `Doskey.exe` or [Doskey](/previous-versions/windows/it-pro/windows-xp/bb490894(v=technet.10)) on TechNet.</span></span>

<span data-ttu-id="bc442-114">Todas las instancias de un archivo ejecutable que se ejecuta en la misma ventana de la consola comparten los alias de consola definidos.</span><span class="sxs-lookup"><span data-stu-id="bc442-114">All instances of an executable file running in the same console window share any defined console aliases.</span></span> <span data-ttu-id="bc442-115">Varias instancias del mismo archivo ejecutable que se ejecutan en ventanas de consola diferentes no comparten los alias de la consola.</span><span class="sxs-lookup"><span data-stu-id="bc442-115">Multiple instances of the same executable file running in different console windows do not share console aliases.</span></span> <span data-ttu-id="bc442-116">Los distintos archivos ejecutables que se ejecutan en la misma ventana de la consola no comparten los alias de la consola.</span><span class="sxs-lookup"><span data-stu-id="bc442-116">Different executable files running in the same console window do not share console aliases.</span></span>

<span data-ttu-id="bc442-117">Para recuperar la cadena de destino de una cadena de origen y un archivo ejecutable especificados, use la función [**GetConsoleAlias**](getconsolealias.md) .</span><span class="sxs-lookup"><span data-stu-id="bc442-117">To retrieve the target string for a specified source string and executable file, use the [**GetConsoleAlias**](getconsolealias.md) function.</span></span> <span data-ttu-id="bc442-118">Para recuperar todos los alias de un archivo ejecutable especificado, utilice la función [**GetConsoleAliases**](getconsolealiases.md) .</span><span class="sxs-lookup"><span data-stu-id="bc442-118">To retrieve all aliases for a specified executable file, use the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span> <span data-ttu-id="bc442-119">Para recuperar los nombres de todos los alias para los que se han definido alias de la consola, use la función [**GetConsoleAliasExes**](getconsolealiasexes.md) .</span><span class="sxs-lookup"><span data-stu-id="bc442-119">To retrieve the names of all aliases for which console aliases have been defined, use the [**GetConsoleAliasExes**](getconsolealiasexes.md) function.</span></span>