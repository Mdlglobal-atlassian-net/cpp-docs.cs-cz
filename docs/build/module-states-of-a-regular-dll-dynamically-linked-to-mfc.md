---
title: Stavy modulů běžné knihovny MFC DLL dynamicky propojené s MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d15f533473ebe90d6d105ddeb57dcdcddd90e87b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369367"
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>Stavy modulů běžné knihovny MFC DLL dynamicky propojené s MFC
Umožňuje dynamicky propojit běžný MFC DLL ke knihovně MFC DLL umožňuje některé konfigurace, které jsou velmi složité. Například běžné knihovny MFC DLL a spustitelný soubor, který použije dynamické propojení ke knihovně MFC DLL a všechny MFC – rozšiřující knihovny DLL.  
  
 Tato konfigurace představuje problém s ohledem na MFC globální data, jako je například má ukazatel na aktuální `CWinApp` objektu a zpracovávání map.  
  
 Před MFC verze 4.0 tato globální data nacházejí v knihovně MFC DLL a byl sdílen všechny moduly v procesu. Protože každý proces, pomocí knihovny DLL Win32 získá svůj vlastní kopii dat knihovnu DLL, toto schéma poskytuje snadný způsob, jak sledovat data na proces. Navíc vzhledem k tomu, že model AFXDLL – předpokládá, že bude pouze jeden `CWinApp` objekt a jen jednu sadu zpracování mapování v procesu, tyto položky mohou být sledovány v knihovně MFC DLL.  
  
 Ale možnost běžné knihovny MFC DLL dynamicky propojené ke knihovně MFC DLL, je možné, že dvě nebo více `CWinApp` objekty v procesu – a také dva nebo více sad mapování. Jak MFC udržování přehledu o ty, které by měla být použita?  
  
 Řešení je poskytnout vlastní kopii tyto informace globální stav každého modulu (aplikaci nebo běžné knihovny MFC DLL). Proto volání **AfxGetApp** v běžné knihovny MFC DLL vrátí ukazatel `CWinApp` objekt v knihovně DLL, není ten ve spustitelném souboru. Tato kopie modulu MFC globální data se označuje jako stav modulu a je popsána v [MFC Technická poznámka 58](../mfc/tn058-mfc-module-state-implementation.md).  
  
 MFC společné okno procedury se automaticky přepne do stavu správný modul, proto není nutné se obávat v jakékoli obslužné rutiny zpráv implementované v pravidelných knihovně MFC DLL. Ale když váš spustitelný soubor volá do běžné knihovny MFC DLL, je nutné explicitně nastavit aktuální stav modulu na jeden z knihovny DLL. Chcete-li to provést, použijte **AFX_MANAGE_STATE** makro v každé funkci exportovat z knihovny DLL. To se provádí přidáním následující kód do začátku funkce exportované z knihovny DLL:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Správa dat stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md)  
  
-   [Regulární knihovny MFC DLL dynamicky propojené s MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [MFC – rozšiřující knihovny DLL](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)