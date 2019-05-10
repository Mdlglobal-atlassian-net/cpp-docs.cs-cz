---
title: Automatizace v knihovně DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: dedc832d6726dccf8c0c2e88f9f4d5c67590c1c2
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220928"
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

## <a name="see-also"></a>Viz také:

[Vytvoření knihovny DLL jazyka C/C++ v sadě Visual Studio](dlls-in-visual-cpp.md)
