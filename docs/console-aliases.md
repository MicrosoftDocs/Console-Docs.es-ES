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
ms.openlocfilehash: b31ae10faf2c8500b0100d1a4cbc126014bf8790
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037283"
---
# <a name="console-aliases"></a>Alias de la consola

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

Los alias de consola se usan para asignar cadenas de origen a cadenas de destino. Por ejemplo, puede definir un alias de consola que asigne "Test" a "CD \\ an \_ Very \_ Long \_ path \\ Test". Cuando escribe "Test" en la línea de comandos, el subsistema de consola expande el alias y ejecuta el comando de CD especificado.

Para definir un alias de la consola, use [**Doskey.exe**](https://docs.microsoft.com/windows-server/administration/windows-commands/doskey) para crear una macro o use la función [**AddConsoleAlias**](addconsolealias.md) . En el ejemplo siguiente se usa `Doskey.exe`:

**doskey test = CD \\** una **\\ prueba** <em>de \_ \_ ruta de \_ acceso muy larga</em>

La siguiente llamada a [**AddConsoleAlias**](addconsolealias.md) crea el mismo alias de consola:

``` C
AddConsoleAlias( TEXT("test"),
                 TEXT("cd \\<a_very_long_path>\\test"),
                 TEXT("cmd.exe"));
```

Para agregar parámetros a una macro de alias de consola mediante `Doskey.exe` , utilice los parámetros de lote `$1` a través de `$9` . Para obtener más información sobre los códigos especiales que se pueden usar en las definiciones de macro de Doskey, vea la ayuda de la línea de comandos de `Doskey.exe` o [doskey](https://go.microsoft.com/fwlink/p/?linkid=196265) en TechNet.

Todas las instancias de un archivo ejecutable que se ejecuta en la misma ventana de la consola comparten los alias de consola definidos. Varias instancias del mismo archivo ejecutable que se ejecutan en ventanas de consola diferentes no comparten los alias de la consola. Los distintos archivos ejecutables que se ejecutan en la misma ventana de la consola no comparten los alias de la consola.

Para recuperar la cadena de destino de una cadena de origen y un archivo ejecutable especificados, use la función [**GetConsoleAlias**](getconsolealias.md) . Para recuperar todos los alias de un archivo ejecutable especificado, utilice la función [**GetConsoleAliases**](getconsolealiases.md) . Para recuperar los nombres de todos los alias para los que se han definido alias de la consola, use la función [**GetConsoleAliasExes**](getconsolealiasexes.md) .
