---
title: Automatizace v knihovně DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: 3cc5ca456842707a2c3de7b2fd74abc73d9a5307
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422283"
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

[Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)
