---
title: Implementace rozhraní (Visual C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interfaces, implementing
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f7d7bed9725e4ec1cc8ad0fc66673ce5c6212e1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211209"
---
# <a name="implementing-an-interface-visual-c"></a>Implementace rozhraní (Visual C++)
Implementovat rozhraní, musí vytvoříte projekt knihovny ATL modelu COM aplikace nebo jako aplikace knihovny MFC, která obsahuje podporu ATL. Můžete použít [Průvodce projektem ATL](../atl/reference/atl-project-wizard.md) k vytvoření aplikace knihovny ATL nebo [přidat objekt ATL do aplikace knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) k implementaci podpory knihovny ATL pro aplikaci knihovny MFC.  
  
 Po vytvoření projektu, chcete-li implementovat rozhraní, musíte nejprve přidat objekt ATL. V tématu [přidání objektů a ovládacích prvků do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) seznam průvodcích, které přidat objekty do projektu ATL s Knihovnami.  
  
> [!NOTE]
>  Průvodce nepodporuje dialogová okna ATL, webové služby XML pomocí knihovny ATL, objekty výkonu a čítače výkonu.  
  
 Pokud jste [přidání ovládacího prvku ATL](../atl/reference/adding-an-atl-control.md), můžete určit, jestli se má implementovat výchozí rozhraní, na [rozhraní](../atl/reference/interfaces-atl-control-wizard.md) stránky, který průvodce a definovaných v atlcom.  
  
 Po přidání objektu nebo ovládací prvek, můžete implementovat další rozhraní, které jsou umístěné v libovolné dostupné knihovny typů, pomocí Průvodce implementovat rozhraní.  
  
 Pokud přidáváte nové rozhraní, musíte přidat ji ručně do projektu soubor .idl. Zobrazit [přidání nového rozhraní projektu ATL](../atl/reference/adding-a-new-interface-in-an-atl-project.md) Další informace.  
  
### <a name="to-implement-an-interface"></a>Pro implementaci rozhraní  
  
1.  V zobrazení tříd klikněte pravým tlačítkem myši na název třídy pro váš objekt knihovny ATL.  
  
2.  Klikněte na tlačítko **přidat** z místní nabídky a pak klikněte na tlačítko **implementovat rozhraní** zobrazíte [Průvodce implementací rozhraní](../ide/implement-interface-wizard.md).  
  
3.  Vyberte rozhraní k implementaci z příslušného typu knihovny a klikněte na tlačítko **Dokončit**.  
  
4.  V zobrazení tříd, rozbalte objektu základních tříd a rozhraní uzel zobrazíte rozhraní jste implementovali a potom rozbalte uzel rozhraní zobrazíte jeho dostupné vlastnosti, metody a události.  
  
    > [!NOTE]
    >  Můžete také použít [prohlížeče objektů](https://msdn.microsoft.com/f89acfc5-1152-413d-9f56-3dc16e3f0470) prozkoumat členy rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření rozhraní modelu COM](../ide/creating-a-com-interface-visual-cpp.md)   
 [Úpravy rozhraní modelu COM](../ide/editing-a-com-interface.md)