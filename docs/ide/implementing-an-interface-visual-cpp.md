---
title: Implementace rozhraní
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.impl.interface.overview
helpviewer_keywords:
- interfaces, implementing
- implement interface wizard [C++]
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
ms.openlocfilehash: 8e166f806d247cd93ff0f471360d749fa95e430b
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692898"
---
# <a name="implement-an-interface"></a>Implementace rozhraní

Implementovat rozhraní, musí vytvoříte projekt knihovny ATL modelu COM aplikace nebo jako aplikace knihovny MFC, která obsahuje podporu ATL. Můžete použít [Průvodce projektem ATL](../atl/reference/atl-project-wizard.md) k vytvoření aplikace knihovny ATL nebo [přidat objekt ATL do aplikace knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) k implementaci podpory knihovny ATL pro aplikaci knihovny MFC.

Po vytvoření projektu, chcete-li implementovat rozhraní, musíte nejprve přidat objekt ATL. V tématu [přidání objektů a ovládacích prvků do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) seznam průvodcích, které přidat objekty do projektu ATL s Knihovnami.

> [!NOTE]
> Průvodce nepodporuje dialogová okna ATL, webové služby XML pomocí knihovny ATL, objekty výkonu a čítače výkonu.

Pokud jste [přidání ovládacího prvku ATL](../atl/reference/adding-an-atl-control.md), můžete určit, jestli se má implementovat výchozí rozhraní. Výchozí rozhraní jsou uvedeny na [rozhraní](../atl/reference/interfaces-atl-control-wizard.md) stránky, který průvodce a definovaných v atlcom.

Po přidání objektu nebo ovládací prvek, můžete implementovat další rozhraní, které jsou umístěné v libovolné dostupné knihovny typů, pomocí Průvodce implementovat rozhraní.

Pokud přidáváte nové rozhraní, můžete musí jej ručně přidat do projektu soubor .idl. Další informace najdete v tématu [přidání nového rozhraní projektu ATL](../atl/reference/adding-a-new-interface-in-an-atl-project.md).

**Pro implementaci rozhraní:**

1. V zobrazení tříd klikněte pravým tlačítkem myši na název třídy pro váš objekt knihovny ATL.

1. Zvolte **přidat** z místní nabídky a klikněte na tlačítko **implementovat rozhraní** zobrazíte [Průvodce implementací rozhraní](#implement-interface-wizard).

1. Vyberte rozhraní a implementaci z příslušného typu knihovny vyberte **Dokončit**.

1. V zobrazení tříd, rozbalte objektu základních tříd a rozhraní uzel zobrazíte rozhraní jsme implementovali. Potom rozbalte uzel rozhraní zobrazíte jeho dostupné vlastnosti, metody a události.

   > [!NOTE]
   > Můžete také použít [prohlížeče objektů](/visualstudio/ide/viewing-the-structure-of-code) prozkoumat členy rozhraní.

## <a name="in-this-section"></a>V tomto oddílu

- [Průvodce implementací rozhraní](#implement-interface-wizard)

## <a name="implement-interface-wizard"></a>Průvodce implementací rozhraní

Tento průvodce implementuje rozhraní pro objekt modelu COM. Implementace mnoho rozhraní jsou součástí knihovny modelu COM, který je k dispozici v sadě Visual Studio a Windows. Implementace rozhraní je přidružena k objektu při vytváření instance daného objektu. Poskytuje také služby, které nabízí objektu.

Informace o rozhraní a implementaci, najdete v článku [rozhraní a implementace rozhraní](/windows/desktop/com/interfaces-and-interface-implementations) v sadě Windows SDK.

- **Implementovat rozhraní z**

  Určuje umístění knihovny typů, ze kterého se vytvoří rozhraní.

  |Možnost|Popis|
  |------------|-----------------|
  |**Projekt**|Knihovna typů je součástí projektu.|
  |**Registru**|Knihovna typů je registrován v systému. Zaregistrované knihovny typů jsou uvedeny v **dostupné knihovny typů**.|
  |**Soubor**|Knihovna typů není nutně registrován v systému, ale se nachází v souboru. Zadejte umístění souboru v **umístění**.|

- **Dostupné knihovny typů**

  Zobrazí dostupné knihovny typů obsahující definice rozhraní, které můžete implementovat. Pokud se rozhodnete **souboru** pod **implementovat rozhraní z**, toto pole je k dispozici pro změnu.

- **Poloha**

  Zobrazí umístění aktuálně vybrané v knihovně typů **dostupné knihovny typů** seznamu. Pokud jste vybrali **souboru** pod **implementovat rozhraní z**, vyberte tlačítko se třemi tečkami a vyhledejte soubor obsahující knihovnu typů použitou.

- **Rozhraní**

  Zobrazí rozhraní, jejichž definice jsou uložené v aktuálně vybrané v knihovně typů **dostupné knihovny typů** pole.

  > [!NOTE]
  > Rozhraní, které mají stejný název jako již implementováno prostřednictvím vybraného objektu, nejsou zobrazeny v **rozhraní** pole.

  |Tlačítka převodu|Popis|
  |---------------------|-----------------|
  |**>**|Přidá **implementovat rozhraní** rozhraní název aktuálně vybraného v seznamu **rozhraní** seznamu.|
  |**>>**|Přidá **implementovat rozhraní** názvy všech rozhraní k dispozici v seznamu **rozhraní** seznamu.|
  |**\<**|Odebere aktuálně vybrané v název rozhraní **implementovat rozhraní** seznamu.|
  |**\<\<**|Odebere všechny názvy teď uvedená v rozhraní **implementovat rozhraní** seznamu.|

- **Implementovat rozhraní**

  Zobrazuje názvy rozhraní, která jste vybrali k implementaci na objekt.

  > [!NOTE]
  > Pokud zahrnete více než jedno rozhraní, která je odvozena od `IDispatch`, nebo pokud pokusíte implementovat rozhraní, který je odvozen z jiného rozhraní už ve vaší třídě, pak musí jednoznačně vyjádřit COM_MAP položky. Další informace najdete v tématu [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2).
