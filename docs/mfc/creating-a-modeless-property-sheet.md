---
title: Vytvoření nemodálního seznamu vlastností
ms.date: 11/04/2016
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
ms.openlocfilehash: 90f6dcd5659d308a4b39d6a7d5a42003fc1f2111
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685684"
---
# <a name="creating-a-modeless-property-sheet"></a>Vytvoření nemodálního seznamu vlastností

V normálním případě se seznamy vlastností, které vytvoříte, budou modální. Při použití modálního seznamu vlastností musí uživatel před použitím jakékoli jiné části aplikace zavřít seznam vlastností. Tento článek popisuje metody, které můžete použít k vytvoření nemodálního seznamu vlastností, který umožňuje uživateli ponechat seznam vlastností otevřený při použití jiných částí aplikace.

Chcete-li zobrazit seznam vlastností jako nemodální dialogové okno namísto jako modální dialogové okno, zavolejte [CPropertySheet –:: Create](../mfc/reference/cpropertysheet-class.md#create) namísto [DoModal](../mfc/reference/cpropertysheet-class.md#domodal). Také je nutné implementovat některé dodatečné úlohy pro podporu nemodálního seznamu vlastností.

Jedna z dalších úloh vyměňuje data mezi seznamem vlastností a externím objektem, který upravuje, když je otevřen seznam vlastností. Většinou se jedná o stejný úkol jako u standardních nemodálních dialogových oken. Součástí této úlohy je implementace kanálu komunikace mezi nemodálním seznamem vlastností a externím objektem, na který se aplikuje nastavení vlastností. Tato implementace je mnohem jednodušší, pokud odvozujete třídu od [CPropertySheet –](../mfc/reference/cpropertysheet-class.md) pro váš nemodální seznam vlastností. V tomto článku se předpokládá, že jste to udělali.

Jedna metoda pro komunikaci mezi nemodálním seznamem vlastností a externím objektem (například aktuální výběr v zobrazení) je definovat ukazatel z seznamu vlastností na externí objekt. Definujte funkci (s názvem něco jako `SetMyExternalObject`) v třídě odvozené `CPropertySheet`, abyste změnili ukazatel při každé změně fokusu z jednoho externího objektu na jiný. Funkce `SetMyExternalObject` musí resetovat nastavení jednotlivých stránek vlastností tak, aby odrážela nově vybraný externí objekt. Aby to bylo možné, musí být funkce `SetMyExternalObject` schopna získat přístup k objektům [CPropertyPage –](../mfc/reference/cpropertypage-class.md) patřícím do `CPropertySheet` třídy.

Nejpohodlnější způsob poskytnutí přístupu k stránkám vlastností v rámci seznamu vlastností je vložení objektů `CPropertyPage` do objektu odvozeného od `CPropertySheet`. Vložení `CPropertyPage` objektů v objektu odvozeném `CPropertySheet`se liší od typického návrhu modálních dialogových oken, kde vlastník seznamu vlastností vytvoří objekty `CPropertyPage` a předá je do seznamu vlastností prostřednictvím [CPropertySheet –:: addPage](../mfc/reference/cpropertysheet-class.md#addpage).

Existuje mnoho alternativ uživatelského rozhraní pro určení, kdy má být nastavení nemodálního seznamu vlastností použito pro externí objekt. Jednou z možností je použít nastavení aktuální stránky vlastností vždy, když uživatel změní libovolnou hodnotu. Další možností je poskytnout tlačítko použít, které uživateli umožňuje shromáždit změny na stránkách vlastností před jejich potvrzením externímu objektu. Informace o způsobech zpracování tlačítka použít naleznete v článku [manipulace s tlačítkem použít](../mfc/handling-the-apply-button.md).

## <a name="see-also"></a>Viz také:

[Seznamy vlastností](../mfc/property-sheets-mfc.md)<br/>
[Výměna dat](../mfc/exchanging-data.md)<br/>
[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)
