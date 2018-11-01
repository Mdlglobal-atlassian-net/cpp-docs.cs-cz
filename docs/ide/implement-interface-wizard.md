---
title: Průvodce implementací rozhraní
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.impl.interface.overview
helpviewer_keywords:
- Implement Interface Wizard [C++]
ms.assetid: 947c329e-0815-4ca7-835e-c41dfeb75f9e
ms.openlocfilehash: 0a307792d83404eb89b861e927a0003c5971a9bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470834"
---
# <a name="implement-interface-wizard"></a>Průvodce implementací rozhraní

Tento průvodce implementuje rozhraní pro objekt modelu COM. Implementace mnoho rozhraní jsou součástí knihovny modelu COM, který je k dispozici v sadě Visual Studio a Windows. Když je vytvořena instance objektu, a poskytuje služby, které nabízí objekt je přidružený objekt implementaci rozhraní.

Informace o rozhraní a implementaci, najdete v článku [rozhraní a implementace rozhraní](/windows/desktop/com/interfaces-and-interface-implementations) v sadě Windows SDK.

- **Implementovat rozhraní z**

   Určuje umístění knihovny typů, ze kterého se vytvoří rozhraní.

   |Možnost|Popis|
   |------------|-----------------|
   |**Projekt**|Knihovna typů je součástí projektu.|
   |**Registru**|Knihovna typů je registrován v systému. Zaregistrované knihovny typů jsou uvedeny v **dostupné knihovny typů**.|
   |**Soubor**|Knihovna typů není nutně registrován v systému, ale je obsažena v souboru. Je nutné zadat umístění souborů v **umístění**.|

- **Dostupné knihovny typů**

   Zobrazí dostupné knihovny typů obsahující definice rozhraní, které můžete implementovat. Vyberete-li **souboru** pod **implementovat rozhraní z**, toto pole je k dispozici pro změnu.

- **Poloha**

   Zobrazí umístění aktuálně vybrané v knihovně typů **dostupné knihovny typů** seznamu. Pokud jste vybrali **souboru** pod **implementovat rozhraní z**, klikněte na tlačítko se třemi tečkami vyhledejte soubor, který obsahuje knihovnu typů použitou.

- **Rozhraní**

   Zobrazí rozhraní, jejichž definice jsou obsaženy v aktuálně vybrané v knihovně typů **dostupné knihovny typů** pole.

   > [!NOTE]
   > Rozhraní, které mají stejný název jako již implementováno prostřednictvím vybraného objektu, nejsou zobrazeny v **rozhraní** pole.

   |Tlačítka převodu|Popis|
   |---------------------|-----------------|
   |**>**|Přidá **implementovat rozhraní** rozhraní název aktuálně vybraného v seznamu **rozhraní** seznamu.|
   |**>>**|Přidá **implementovat rozhraní** názvy všech rozhraní k dispozici v seznamu **rozhraní** seznamu.|
   |**\<**|Odebere aktuálně vybrané v název rozhraní **implementovat rozhraní** seznamu.|
   |**\<\<**|Odebere všechny názvy teď uvedená v rozhraní **implementovat rozhraní** seznamu.|

- **Implementovat rozhraní**

   Zobrazuje názvy rozhraní, které jste vybrali k implementaci na objekt.

   > [!NOTE]
   > Pokud zahrnete více než jedno rozhraní, která je odvozena od `IDispatch`, nebo pokud pokusíte implementovat rozhraní, který je odvozen z jiného rozhraní už ve vaší třídě, pak musí jednoznačně vyjádřit COM_MAP položky. Zobrazit [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2) Další informace.

## <a name="see-also"></a>Viz také

[Implementace rozhraní](../ide/implementing-an-interface-visual-cpp.md)