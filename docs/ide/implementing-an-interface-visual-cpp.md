---
title: Implementace rozhraní (Visual C++) | Microsoft Docs
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
ms.openlocfilehash: 309ae9dc576f93574836ab4916e87c5232b37a6c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33332764"
---
# <a name="implementing-an-interface-visual-c"></a>Implementace rozhraní (Visual C++)
Pokud chcete implementovat rozhraní, musí jste vytvořili projekt jako aplikace ATL COM nebo jako aplikace knihovny MFC, který obsahuje podpory knihovny ATL. Můžete použít [ATL – Průvodce projektem](../atl/reference/atl-project-wizard.md) k vytvoření aplikace knihovny ATL nebo [přidat objekt knihovny ATL do aplikace knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) implementovat ATL – podpora pro aplikace MFC.  
  
 Po vytvoření projektu, k implementaci rozhraní, je nejprve nutno přidat objekt knihovny ATL. V tématu [přidávání objektů a ovládacích prvků do projektu knihovny ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) seznam průvodců, které přidat objekty do projektu knihovny ATL.  
  
> [!NOTE]
>  Průvodce nepodporuje dialogy knihovny ATL, webové služby XML pomocí knihovny ATL, objekty výkonu a čítače výkonu.  
  
 Pokud jste [přidání ovládacího prvku ATL](../atl/reference/adding-an-atl-control.md), můžete určit, zda implementovat výchozí rozhraní, uvedená v [rozhraní](../atl/reference/interfaces-atl-control-wizard.md) to průvodce a definované v atlcom.  
  
 Po přidání objektu nebo ovládacího prvku, můžete implementovat další rozhraní, které jsou umístěné v libovolné knihovně k dispozici typ pomocí Průvodce implementovat rozhraní.  
  
 Pokud přidáváte nové rozhraní, je třeba přidat ji ručně do souboru projektu. V tématu [přidání nového rozhraní v projektu knihovny ATL](../atl/reference/adding-a-new-interface-in-an-atl-project.md) Další informace.  
  
### <a name="to-implement-an-interface"></a>Implementace rozhraní  
  
1.  V zobrazení tříd klikněte pravým tlačítkem na název třídy pro ATL objektu.  
  
2.  Klikněte na tlačítko **přidat** z místní nabídky a pak klikněte na tlačítko **implementovat rozhraní** zobrazíte [Průvodce implementací rozhraní](../ide/implement-interface-wizard.md).  
  
3.  Vyberte rozhraní k implementaci z příslušného typu knihovny a klikněte na tlačítko **Dokončit**.  
  
4.  V zobrazení tříd, rozbalte položku objektu základní a uzel rozhraní zobrazíte rozhraní byla implementována a pak rozbalte uzel rozhraní zobrazíte jeho dostupné vlastnosti, metod a události.  
  
    > [!NOTE]
    >  Můžete také [Prohlížeč objektů](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470) prozkoumat členy rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření rozhraní modelu COM](../ide/creating-a-com-interface-visual-cpp.md)   
 [Úpravy rozhraní modelu COM](../ide/editing-a-com-interface.md)