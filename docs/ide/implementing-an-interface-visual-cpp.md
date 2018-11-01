---
title: Implementace rozhraní (Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- interfaces, implementing
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
ms.openlocfilehash: 5146a8ced1b8347ea724940a7419d8d2507b5b58
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449644"
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

1. V zobrazení tříd klikněte pravým tlačítkem myši na název třídy pro váš objekt knihovny ATL.

1. Klikněte na tlačítko **přidat** z místní nabídky a pak klikněte na tlačítko **implementovat rozhraní** zobrazíte [Průvodce implementací rozhraní](../ide/implement-interface-wizard.md).

1. Vyberte rozhraní k implementaci z příslušného typu knihovny a klikněte na tlačítko **Dokončit**.

1. V zobrazení tříd, rozbalte objektu základních tříd a rozhraní uzel zobrazíte rozhraní jste implementovali a potom rozbalte uzel rozhraní zobrazíte jeho dostupné vlastnosti, metody a události.

   > [!NOTE]
   > Můžete také použít [prohlížeče objektů](/visualstudio/ide/viewing-the-structure-of-code) prozkoumat členy rozhraní.

## <a name="see-also"></a>Viz také

[Vytváření rozhraní modelu COM](../ide/creating-a-com-interface-visual-cpp.md)<br>
[Úpravy rozhraní modelu COM](../ide/editing-a-com-interface.md)