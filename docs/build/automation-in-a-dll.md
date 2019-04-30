---
title: Automatizace v knihovně DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: 4ac60c44348ea21f490cb312285ae88ac682cf7d
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341669"
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

[Knihovny DLL v jazyce Visual C++](dlls-in-visual-cpp.md)
