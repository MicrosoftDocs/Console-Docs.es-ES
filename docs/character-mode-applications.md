---
title: Aplicaciones en modo de carácter
description: Las consolas de administran la entrada y salida (e/s) para aplicaciones en modo de caracteres (aplicaciones que no proporcionan su propia interfaz gráfica de usuario).
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: consola, aplicaciones de modo de carácter, aplicaciones de línea de comandos, aplicaciones de terminal, API de consola
MS-HAID:
- '\_win32\_character\_mode\_applications'
- base.character\_mode\_applications
- consoles.character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ea3ea214-892c-4953-bc22-7905efbc173f
ms.openlocfilehash: 5e1b0b2b5162360122580f3ea7a100750b96272e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037353"
---
# <a name="character-mode-applications"></a>Aplicaciones en modo de carácter

Las consolas de administran la entrada y salida (e/s) para aplicaciones en modo de caracteres (aplicaciones que no proporcionan su propia interfaz gráfica de usuario).

Las funciones de la consola de permiten distintos niveles de acceso a una consola de. Las funciones de e/s de la consola de alto nivel permiten a una aplicación leer la entrada estándar para recuperar la entrada del teclado almacenada en el búfer de entrada de la consola. Las funciones también permiten que una aplicación escriba en una salida estándar o un error estándar para mostrar texto en el búfer de pantalla de la consola. Las funciones de alto nivel también admiten la redirección de los identificadores estándar y el control de los modos de la consola para la funcionalidad de e/s diferente. Las funciones de e/s de la consola de bajo nivel permiten que las aplicaciones reciban información detallada sobre los eventos del teclado y del mouse, así como los eventos que afectan a las interacciones del usuario con la ventana de la consola. Las funciones de bajo nivel también permiten un mayor control de la salida en la pantalla.

En esta información general se describe la compatibilidad con aplicaciones de modo de carácter.

- [Acerca de las consolas](about-character-mode-applications.md)
- [Uso de la consola](using-the-console.md)
- [Referencia de la consola](console-reference.md)
