---
title: Seguridad y derechos de acceso del búfer de la consola
description: El modelo de seguridad de Windows permite controlar el acceso a los búferes de entrada y de pantalla de la consola. Para obtener más información sobre la seguridad, vea modelo de Access-Control.
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_buffer\_security\_and\_access\_rights'
- base.console\_buffer\_security\_and\_access\_rights
- consoles.console\_buffer\_security\_and\_access\_rights
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f9a50063-8fc8-4cd1-8f24-9ae3946d3119
ms.openlocfilehash: 94ceeef240f418052c64efc3de594debccb2c8d4
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358265"
---
# <a name="console-buffer-security-and-access-rights"></a>Seguridad y derechos de acceso del búfer de la consola

El modelo de seguridad de Windows permite controlar el acceso a los búferes de entrada y de pantalla de la consola. Para obtener más información sobre la seguridad, vea [modelo de control de acceso](/windows/win32/secauthz/access-control-model).

## <a name="console-object-security-descriptors"></a>Descriptores de seguridad de objetos de consola

Puede especificar un [descriptor de seguridad](/windows/win32/secauthz/security-descriptors) para los búferes de entrada y de pantalla de la consola cuando se llama a la función [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) o [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) . Si especifica **null**, el objeto obtiene un descriptor de seguridad predeterminado. Las ACL del descriptor de seguridad predeterminado de un búfer de la consola proceden del token principal o de suplantación del creador.

Los identificadores devueltos por [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)y [**GetStdHandle**](getstdhandle.md) tienen derechos de acceso **genéricos de \_ lectura** y **\_ escritura** .

Entre los derechos de acceso válidos se incluyen los [derechos de acceso](/windows/win32/secauthz/generic-access-rights)genéricos de **\_ lectura** y **\_ escritura** genéricos.

| Valor | Significado |
|-|-|
| **Genérico \_ LECTURA** (0x80000000L)  | Solicita acceso de lectura al búfer de pantalla de la consola, lo que permite al proceso leer datos del búfer. |
| **Genérico \_ ESCRITURA** (0x40000000L) | Solicita acceso de escritura al búfer de pantalla de la consola, lo que permite que el proceso escriba datos en el búfer. |

> [!NOTE]
> Las **[aplicaciones de consola de plataforma universal de Windows](/windows/uwp/launch-resume/console-uwp)** y las que tienen un nivel de **[integridad](/windows/win32/secauthz/mandatory-integrity-control)** inferior al de la consola conectada no podrán leer el búfer de salida y escribir en el búfer de entrada, incluso si los descriptores de seguridad anteriores lo permiten normalmente. Para obtener más información, consulte la explicación de **[verbos equivocada de forma incorrecta](#wrong-way-verbs)** .

## <a name="wrong-way-verbs"></a>Verbos con dirección incorrecta

Algunas operaciones en los objetos de consola se denegarán aunque el objeto tenga un descriptor de seguridad que se indique específicamente para permitir la lectura o escritura. Esto se refiere específicamente a las aplicaciones de línea de comandos que se ejecutan en un contexto con privilegios reducidos que comparten una sesión de consola creada por una aplicación de línea de comandos en un contexto más permisivo.

El término "verbos equivocado" se ha diseñado para aplicarse a la operación que es la opuesta del flujo normal de uno de los objetos de consola. En concreto, el flujo normal para el búfer de salida está escribiendo y el flujo normal para el búfer de entrada está leyendo. La "manera equivocada" sería la lectura del búfer de salida o la escritura del búfer de entrada. Estas son funciones que se describen en la documentación de **[las funciones de e/s de la consola de bajo nivel](low-level-console-i-o.md)** .

Los dos escenarios en los que se puede encontrar se encuentran:

1. **[Plataforma universal de Windows aplicaciones de consola](/windows/uwp/launch-resume/console-uwp)**. Puesto que son primos de otras aplicaciones Plataforma universal de Windows, tienen una promesa de que están aisladas de otras aplicaciones y proporcionan garantías a los usuarios sobre los efectos de su funcionamiento.
1. Cualquier aplicación de consola iniciada intencionadamente con un **[nivel de integridad](/windows/win32/secauthz/mandatory-integrity-control)** inferior al de la sesión existente, que se puede lograr con el **[etiquetado o la manipulación de tokens durante CreateProcess](/previous-versions/dotnet/articles/bb625960(v=msdn.10))**.

Si se detecta alguno de estos escenarios, la consola aplicará la marca "verbos-Way" a la conexión de la aplicación de línea de comandos y rechazará las llamadas a las siguientes API para reducir la superficie de comunicación entre los niveles:

:::row:::
    :::column:::
        [ReadConsoleOutput](readconsoleoutput.md)  
        [ReadConsoleOutputCharacter](readconsoleoutputcharacter.md)  
        [ReadConsoleOutputAttribute](readconsoleoutputattribute.md)  
    :::column-end:::
    :::column:::
        [WriteConsoleInput](writeconsoleinput.md)  
    :::column-end:::
:::row-end:::

Las llamadas rechazadas recibirán un código de error de **acceso denegado** , lo mismo que si los descriptores de seguridad del objeto denegaran el permiso de lectura o escritura.