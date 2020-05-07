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

Když v Průvodci knihovnou MFC DLL zvolíte možnost automatizace, průvodce vám poskytne následující:

- Objekt pro popis počátečního objektu (. ODL) – soubor

- Direktiva include v souboru STDAFX. h pro AFXOLE. h

- Implementace `DllGetClassObject` funkce, která volá funkci **AfxDllGetClassObject**

- Implementace `DllCanUnloadNow` funkce, která volá funkci **AfxDllCanUnloadNow**

- Implementace `DllRegisterServer` funkce, která volá funkci [COleObjectFactory:: UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall)

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Automatizační servery](../mfc/automation-servers.md)

## <a name="see-also"></a>Viz také

[Vytváření knihoven DLL jazyka C/C++ v aplikaci Visual Studio](dlls-in-visual-cpp.md)
