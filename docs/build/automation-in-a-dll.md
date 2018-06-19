---
title: Automatizace v knihovně DLL | Microsoft Docs
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
ms.openlocfilehash: 41c5f31a72cf734296ecb281e0785d415c8043a7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360651"
---
# <a name="automation-in-a-dll"></a>Automatizace v knihovně DLL
Pokud zvolíte možnost automatizace v Průvodce MFC DLL, Průvodce vám poskytne následující:  
  
-   Jazyk popis objektu starter (. Soubor ODL)  
  
-   Direktivu v souboru STDAFX.h pro Afxole.h  
  
-   Implementace `DllGetClassObject` funkce, která volá **AfxDllGetClassObject** – funkce  
  
-   Implementace `DllCanUnloadNow` funkce, která volá **AfxDllCanUnloadNow** – funkce  
  
-   Implementace `DllRegisterServer` funkce, která volá [COleObjectFactory::UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall) – funkce  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Automatizační servery](../mfc/automation-servers.md)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)