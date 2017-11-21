---
title: "Vytváření rozhraní modelu COM (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.com.creating.interfaces
dev_langs: C++
helpviewer_keywords: COM interfaces, creating
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 260d56fa4a6944c7cf3a9971e3627d8b24936786
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-com-interface-visual-c"></a>Vytváření rozhraní modelu COM (Visual C++)
Visual C++ poskytuje průvodci a šablony k vytváření projektů, které používají rozhraní a odesílající rozhraní COM – objekty a třídy automatizace.  
  
 Tito průvodci můžete provádět následující tři běžné úkoly:  
  
-   [Přidání podpory knihovny ATL do projektu MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md)  
  
     Přidání podpory knihovny ATL do aplikace MFC po vytvoření projektu knihovny MFC pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md) a pak spustit **přidat podporu knihovny ATL a MFC** kód průvodce. Tato podpora se vztahuje pouze na jednoduché objekty modelu COM, přidat do spustitelného souboru knihovny MFC nebo projektu knihovny DLL. Tyto objekty knihovny ATL může mít více rozhraní.  
  
-   [Vytvoření ovládacího prvku ActiveX knihovny MFC](../mfc/reference/creating-an-mfc-activex-control.md)  
  
     Otevřete [Průvodce ovládacím prvkem ActiveX knihovny MFC](../mfc/reference/mfc-activex-control-wizard.md) vytvoření ovládacího prvku ActiveX s odesílajícím rozhraním a mapou události definované v souboru IDL a třída ovládacích prvků v uvedeném pořadí.  
  
-   [Přidání ovládacího prvku knihovny ATL](../atl/reference/adding-an-atl-control.md)  
  
     Použít kombinaci [ATL – Průvodce projektem](../atl/reference/atl-project-wizard.md) a [Průvodce ovládacím prvkem ATL](../atl/reference/atl-control-wizard.md) k vytvoření ovládacího prvku ActiveX knihovny ATL.  
  
     Můžete také přidat ovládacího prvku knihovny ATL do projektu knihovny MFC, do které jste přidali podpory knihovny ATL, jak bylo popsáno výše. Kromě toho pokud vyberete **ovládací prvek ATL** v **přidat třídu** dialogové okno a ještě nepřidali podpory knihovny ATL do projektu MFC, Visual Studio zobrazí dialogové okno potvrzení přidání podpory knihovny ATL do vaší MFC projektu.  
  
     Tento průvodce generuje IDL zdroje a mapa COM v třídách projektu.  
  
 Jakmile máte projektu knihovny ATL otevřít, [přidat třídu](../ide/add-class-dialog-box.md) dialogové okno poskytuje volba Další průvodci a šablony do projektu přidejte COM – rozhraní. Následující průvodci umožňují vytvořit jeden nebo více rozhraní pro objekt:  
  
-   [ATL COM + 1.0 součást Průvodce](../atl/reference/atl-com-plus-1-0-component-wizard.md)  
  
-   [Průvodce jednoduchého objektu knihovny ATL](../atl/reference/atl-simple-object-wizard.md)  
  
-   [Průvodce komponentou stránky ASP knihovny ATL](../atl/reference/atl-active-server-page-component-wizard.md)  
  
-   [Průvodce ovládacím prvkem knihovny ATL](../atl/reference/atl-control-wizard.md)  
  
 Kromě toho můžete implementovat nové rozhraní ovládacího prvku COM pravým tlačítkem myši na ovládací prvek třídy objektu v zobrazení tříd a kliknutím na [implementovat rozhraní](../ide/implement-interface-wizard.md).  
  
> [!NOTE]
>  Visual Studio neposkytuje průvodce přidat rozhraní do projektu. Můžete přidat do projektu knihovny ATL nebo na rozhraní [přidání podpory knihovny ATL do projektu knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) přidáním jednoduchého objektu pomocí [ATL Simple Object Wizard](../atl/reference/atl-simple-object-wizard.md). Můžete také otevřít souboru projektu a vytvořit rozhraní zadáním:  
  
```  
interface IMyInterface {  
};  
  
```  
  
 V tématu [implementace rozhraní](../ide/implementing-an-interface-visual-cpp.md) a [přidávání objektů a ovládacích prvků do projektu knihovny ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) Další informace.  
  
 Visual C++ poskytuje několik způsobů zobrazení a [úpravy rozhraní modelu COM](../ide/editing-a-com-interface.md) definovaných v projektech. [Třídy zobrazení](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925) zobrazí ikony pro všechny rozhraní a odesílající rozhraní definované v souboru IDL v projektu jazyka C++.  
  
 Zobrazení tříd pro třídy objektů na základě ATL COM, přečte COM mapy ve třídě ATL zobrazíte vztah mezi třídou ATL a všechny rozhraní, které implementuje.  
  
 V zobrazení tříd a jeho místní nabídky můžete pracovat s rozhraními takto:  
  
-   Přidáte objekty knihovny ATL do aplikace založené na MFC.  
  
-   Přidejte metody, vlastnosti a události.  
  
-   Dvojitým kliknutím na položku přejít přímo na kódu rozhraní položky.  
  
## <a name="see-also"></a>Viz také  
 [Tvorba běžných projektů pomocí průvodců aplikací](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)