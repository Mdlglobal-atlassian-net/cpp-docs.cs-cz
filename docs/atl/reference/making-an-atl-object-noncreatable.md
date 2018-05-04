---
title: Provedení noncreatable – ATL objekt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.objects
dev_langs:
- C++
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05707c6771d641d383825a07d0b26a90fdf46cb1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="making-an-atl-object-noncreatable"></a>Provedení noncreatable – objekt knihovny ATL
Atributy založené na knihovně ATL COM objektu můžete změnit tak, aby klient nemůže přímo vytvářet objekt. V takovém případě objekt by být vráceny prostřednictvím volání metody na jiném objektu a nikoli přímo vytvořeny.  
  
### <a name="to-make-an-object-noncreatable"></a>K zamezení vytvoření objektu  
  
1.  Odeberte [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) pro objekt. Pokud chcete, aby objekt, který má být noncreatable – ale ovládacího prvku k registraci, nahraďte OBJECT_ENTRY_AUTO s [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto).  
  
2.  Přidat [noncreatable –](../../windows/noncreatable.md) atribut třída typu coclass v souboru. Příklad:  
  
 ```  
 [  
    uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851), 
    helpstring("MyObject"), 
    noncreatable]  
    coclass MyObject  
 {  
 [default] interface IMyInterface;  
 }  
 ```  
  
## <a name="see-also"></a>Viz také  
 [Průvodce projektem knihovny ATL](../../atl/reference/atl-project-wizard.md)   
 [Typy projektů Visual C++](../../ide/visual-cpp-project-types.md)   
 [Tvorba běžných projektů pomocí průvodců aplikací](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Programování s použitím knihovny ATL a běhového kódu jazyka C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Základy ATL COM – objekty](../../atl/fundamentals-of-atl-com-objects.md)   
 [Výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md)

