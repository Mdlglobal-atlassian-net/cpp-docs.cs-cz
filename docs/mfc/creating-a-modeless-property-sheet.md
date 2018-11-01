---
title: Vytvoření nemodálního seznamu vlastností
ms.date: 11/04/2016
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
ms.openlocfilehash: 9012700ef145079cf01ee1eac1cee58449ab5b79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524897"
---
# <a name="creating-a-modeless-property-sheet"></a>Vytvoření nemodálního seznamu vlastností

Seznamy vlastností, které vytvoříte za normálních okolností bude modální okno. Při použití modální seznam vlastností, musí uživatel před použitím jakékoliv jiné části aplikace zavřete okno vlastností. Tento článek popisuje, jakou metodu použijete k vytvoření nemodálního seznamu vlastností, které mu umožní ponechat otevřené okno vlastností při použití jiných částí aplikace.

Chcete-li zobrazit seznam vlastností jako nemodálního dialogového místo jako modální dialogové okno, zavolejte [CPropertySheet::Create](../mfc/reference/cpropertysheet-class.md#create) místo [DoModal](../mfc/reference/cpropertysheet-class.md#domodal). Je nutné implementovat také některé další úkoly pro podporu nemodálního seznamu vlastností.

Jednu z dalších úloh se výměna dat mezi vlastností a externí objekt, který upravuje při otevření seznamu vlastností. Toto je obvykle stejné úlohy jako u standardní nemodální dialogová okna. Součástí této úlohy je implementace kanálu komunikace mezi nemodálního seznamu vlastností a externí objekt, na kterou se vztahují nastavení vlastností. Tato implementace je mnohem jednodušší, pokud odvodíte třídu od [cpropertysheet –](../mfc/reference/cpropertysheet-class.md) pro vaše nemodálního seznamu vlastností. Tento článek předpokládá, že jste tak učinili.

Jednu metodu pro komunikaci mezi nemodálního seznamu vlastností a externí objekt (aktuální výběr v zobrazení, například) je definování ukazatel externí objekt ze seznamu vlastností. Definovat funkci (podobným názvem `SetMyExternalObject`) v `CPropertySheet`-odvozené třídy změnit při každé změně výběru z jednoho externího objektu na jiný ukazatel. `SetMyExternalObject` Funkce potřebuje k obnovení nastavení pro každou stránku vlastností tak, aby odrážely nově vybraného externího objektu. K tomu, `SetMyExternalObject` funkce musí mít přístup k [CPropertyPage](../mfc/reference/cpropertypage-class.md) objekty, které patří k `CPropertySheet` třídy.

Nejpohodlnější způsob, jak pro poskytnutí přístupu k stránky vlastností v rámci seznamu vlastností, je vložit `CPropertyPage` objekty v `CPropertySheet`-odvozenému objektu. Vkládání `CPropertyPage` objekty v `CPropertySheet`-odvozeného objektu se liší od návrh typický pro modální dialogová okna, kde vlastník vlastností vytvoří `CPropertyPage` objektů a předává je do seznamu vlastností prostřednictvím [ CPropertySheet::AddPage](../mfc/reference/cpropertysheet-class.md#addpage).

Existuje mnoho alternativy uživatelského rozhraní pro určení, kdy bude použito nastavení nemodálního seznamu vlastností do externího objektu. Jeden alternativou je k aplikování nastavení na aktuální stránce vlastností pokaždé, když uživatel změní jakákoli hodnota. Další možností je použít tlačítko, což mu umožní accumulate změny na stránkách vlastností před jejich potvrzením do externího objektu. Další informace o způsobech ke zpracování na tlačítko použít, najdete v článku [ošetření tlačítka použít](../mfc/handling-the-apply-button.md).

## <a name="see-also"></a>Viz také

[Seznamy vlastností](../mfc/property-sheets-mfc.md)<br/>
[Výměna dat](../mfc/exchanging-data.md)<br/>
[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

