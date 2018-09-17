---
title: Automatizace v knihovně DLL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cde5d0e400f1bdd3f5a851d47da581380273b04a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717772"
---
# <a name="automation-in-a-dll"></a>Automatizace v knihovně DLL

Pokud zvolíte možnost automatizace v průvodci knihovny MFC DLL, Průvodce poskytuje následující:

- Jazyk pro popis objektu starter (. Soubor ODL)

- Direktivě include v souboru STDAFX.h Afxole.h

- Implementace `DllGetClassObject` funkce, která volá **AfxDllGetClassObject** – funkce

- Implementace `DllCanUnloadNow` funkce, která volá **AfxDllCanUnloadNow** – funkce

- Implementace `DllRegisterServer` funkce, která volá [COleObjectFactory::UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall) – funkce

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Automatizační servery](../mfc/automation-servers.md)

## <a name="see-also"></a>Viz také

[Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)