---
title: "Určení optimalizace kompilátoru pro projekt knihovny ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
dev_langs:
- C++
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6e60f22b7b91567948dfc2efc90935fce266d7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>Určení optimalizace kompilátoru pro projekt knihovny ATL
Ve výchozím nastavení [Průvodce ovládacím prvkem ATL](../../atl/reference/atl-control-wizard.md) generuje nové třídy s makro ATL_NO_VTABLE takto:  
  
```  
class ATL_NO_VTABLE CProjName  
{  
 ...  
};  
```  
  
 ATL potom definuje _ATL_NO_VTABLE takto:  
  
```  
#ifdef _ATL_DISABLE_NO_VTABLE  
 #define ATL_NO_VTABLE  
#else  
 #define ATL_NO_VTABLE __declspec(novtable)  
#endif  
```  
  
 Pokud nedefinujete _ATL_DISABLE_NO_VTABLE, makro ATL_NO_VTABLE se rozšíří do `declspec(novtable)`. Pomocí `declspec(novtable)`v třídě deklarace zabrání ukazatel vtable inicializaci v konstruktoru třídy a destruktor. Při sestavování projektu linkeru eliminuje vtable a všechny funkce, na které odkazuje vtable.  
  
 Použijte ATL_NO_VTABLE a proto `declspec(novtable)`, pouze pro základní třídy, které nejsou přímo vytvořitelné. Nesmí používat `declspec(novtable)` s většinou odvozených tříd v projektu, protože tato třída (obvykle [CComObject](../../atl/reference/ccomobject-class.md), [CComAggObject](../../atl/reference/ccomaggobject-class.md), nebo [CComPolyObject](../../atl/reference/ccompolyobject-class.md)) Inicializuje ukazatel vtable pro váš projekt.  
  
 Nelze volat virtuální funkce z konstruktoru objektu, který používá `declspec(novtable)`. Měli byste přejít těchto volání [FinalConstruct](ccomobjectrootex-class.md#finalconstruct) metoda.  

  
 Pokud si nejste jistí, jestli byste měli používat `declspec(novtable)` modifikátor, makro ATL_NO_VTABLE můžete odebrat z jakékoli definice třídy, nebo ji můžete globálně zakázat zadáním  
  
```  
#define _ATL_DISABLE_NO_VTABLE  
```  
  
 v souboru stdafx před všechny ostatní ATL hlavičkových souborů jsou zahrnuty.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce projektem knihovny ATL](../../atl/reference/atl-project-wizard.md)   
 [Typy projektů Visual C++](../../ide/visual-cpp-project-types.md)   
 [Tvorba běžných projektů pomocí průvodců aplikací](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Programování s použitím knihovny ATL a běhového kódu jazyka C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Základy ATL COM – objekty](../../atl/fundamentals-of-atl-com-objects.md)   
 [novtable](../../cpp/novtable.md)   
 [Výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md)

