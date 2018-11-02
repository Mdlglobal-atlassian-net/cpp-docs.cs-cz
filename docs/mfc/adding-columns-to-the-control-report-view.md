---
title: Přidávání sloupců do ovládacího prvku (zobrazení sestavy)
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding columns
- report view in CListCtrl class [MFC]
- views [MFC], report
- columns [MFC], adding to CListCtrl
- CListCtrl class [MFC], report view
ms.assetid: 7392c0d7-f8a5-4e7b-9ae7-b53dc9dd80ae
ms.openlocfilehash: e40a923c755f8b32ca3a6ed1884eb7f7a1d6abfb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529334"
---
# <a name="adding-columns-to-the-control-report-view"></a>Přidávání sloupců do ovládacího prvku (zobrazení sestavy)

> [!NOTE]
>  Následující postup platí pro buď [CListView](../mfc/reference/clistview-class.md) nebo [CListCtrl](../mfc/reference/clistctrl-class.md) objektu.

Když ovládací prvek seznamu je v zobrazení sestav, zobrazí se sloupce, poskytuje způsob uspořádání různé podpoložek každou položku seznamu ovládacího prvku. Tato organizace implementuje pomocí shoda mezi sloupci v ovládacím prvku seznamu a přidružené subitem položku ovládacího prvku seznamu. Další informace o podřízené položky, naleznete v tématu [přidávání položek do ovládacího prvku](../mfc/adding-items-to-the-control.md). Příklad seznamu ovládacího prvku v zobrazení sestavy je k dispozici v zobrazení Podrobnosti ve Windows 95 a Windows 98 Explorer. První sloupec uvádí složka, soubor ikony a popisky. Ostatní sloupce seznamu velikost souboru, typ souboru, datum poslední změny a tak dále.

I když sloupce lze přidat do ovládacího prvku seznam v okamžiku, sloupce, které jsou viditelné pouze v případě, že je ovládací prvek `LVS_REPORT` styl bit zapnutý.

Položka přidružená záhlaví má každý sloupec (naleznete v tématu [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) objekt, který označuje sloupec a umožňuje uživatelům změnit velikost sloupce.

Pokud váš ovládací prvek seznamu podporuje zobrazení sestav, budete muset přidat sloupec pro každou možné podřízenou položku v položce seznamu ovládacího prvku. Přidání sloupce při přípravě [LV_COLUMN](/windows/desktop/api/commctrl/ns-commctrl-taglvcolumna) strukturu a pak provedením volání do [InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn). Po přidání potřebných sloupců (někdy označované jako položky záhlaví), můžete změnit jejich pomocí členské funkce a stylů, které patří do ovládacího prvku vloženého záhlaví. Další informace najdete v tématu [objednávání položek v ovládacím prvku záhlaví](../mfc/ordering-items-in-the-header-control.md).

> [!NOTE]
>  Pokud ovládací prvek seznamu se vytvoří s **LVS_NOCOLUMNHEADER** styl, jakýkoliv pokus o vložení sloupců se bude ignorovat.

## <a name="see-also"></a>Viz také

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

