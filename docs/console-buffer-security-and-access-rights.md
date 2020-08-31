---
title: Seguridad y derechos de acceso de búfer de la consola
description: El modelo de seguridad de Windows permite controlar el acceso a los búferes de entrada y de pantalla de la consola. Para obtener más información sobre la seguridad, vea modelo de control de acceso.
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_console\_buffer\_security\_and\_access\_rights'
- base.console\_buffer\_security\_and\_access\_rights
- consoles.console\_buffer\_security\_and\_access\_rights
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f9a50063-8fc8-4cd1-8f24-9ae3946d3119
ms.openlocfilehash: 63cfdb91f4ab9696ade81c7a15bc62e1c93ab6e3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2020
ms.locfileid: "89060885"
---
# <a name="console-buffer-security-and-access-rights"></a>Seguridad y derechos de acceso de búfer de la consola


El modelo de seguridad de Windows permite controlar el acceso a los búferes de entrada y de pantalla de la consola. Para obtener más información sobre la seguridad, vea [modelo de control de acceso](https://msdn.microsoft.com/library/windows/desktop/aa374876).

Puede especificar un [descriptor de seguridad](https://msdn.microsoft.com/library/windows/desktop/aa379563) para los búferes de entrada y de pantalla de la consola cuando se llama a la función [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) o [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) . Si especifica **null**, el objeto obtiene un descriptor de seguridad predeterminado. Las ACL del descriptor de seguridad predeterminado de un búfer de la consola proceden del token principal o de suplantación del creador.

Los identificadores devueltos por [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)y [**GetStdHandle**](getstdhandle.md) tienen derechos de acceso **genéricos de \_ lectura** y ** \_ escritura** .

Entre los derechos de acceso válidos se incluyen los [derechos de acceso](https://msdn.microsoft.com/library/windows/desktop/aa446632)genéricos de ** \_ lectura** y ** \_ escritura** genéricos.


| Valor                            | Significado                                                                                               |
|----------------------------------|-------------------------------------------------------------------------------------------------------|
| **Genérico \_ LECTURA** (0x80000000L)  | Solicita acceso de lectura al búfer de pantalla de la consola, lo que permite al proceso leer datos del búfer. |
| **Genérico \_ ESCRITURA** (0x40000000L) | Solicita acceso de escritura al búfer de pantalla de la consola, lo que permite que el proceso escriba datos en el búfer. |










