---
title: Automatizace v knihovně DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: b9d4f7a71ceb384069fcbef6bf791f0c5fd1b933
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536536"
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