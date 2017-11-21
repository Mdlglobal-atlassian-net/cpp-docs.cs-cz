---
title: "Automatizace v knihovně DLL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 69b5d723da2ac67de3c381b6a5bc09645c1f4341
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)