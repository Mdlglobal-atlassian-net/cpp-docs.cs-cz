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
ms.openlocfilehash: 34d7b62985748b9b9d741c083ec9b34fce06b309
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370876"
---
# <a name="adding-columns-to-the-control-report-view"></a>Přidávání sloupců do ovládacího prvku (zobrazení sestavy)

> [!NOTE]
> Následující postup platí pro objekt [CListView](../mfc/reference/clistview-class.md) nebo [CListCtrl.](../mfc/reference/clistctrl-class.md)

Pokud je ovládací prvek seznamu v zobrazení sestavy, zobrazí se sloupce, které poskytují způsob uspořádání různých podpoložek každé položky ovládacího prvku seznamu. Tato organizace je implementována s korespondencí 1:1 mezi sloupcem v ovládacím prvku seznamu a přidruženou podpoložkou položky ovládacího prvku seznamu. Další informace o podpoložkách naleznete v tématu [Přidání položek do ovládacího prvku](../mfc/adding-items-to-the-control.md). Příklad ovládacího prvku seznamu v zobrazení sestavy poskytuje zobrazení Podrobnosti v systémech Windows 95 a Průzkumník windows 98 Explorer. V prvním sloupci jsou uvedeny složky, ikony souborů a popisky. Velikost souboru seznamu dalších sloupců, typ souboru, datum poslední změny a tak dále.

I když sloupce lze přidat do ovládacího prvku seznamu kdykoli, sloupce `LVS_REPORT` jsou viditelné pouze v případě, že ovládací prvek má styl bit zapnutý.

Každý sloupec má přidružený objekt záhlaví (viz [CHeaderCtrl),](../mfc/reference/cheaderctrl-class.md)objekt, který označuje sloupec popisky a umožňuje uživatelům změnit velikost sloupce.

Pokud ovládací prvek seznamu podporuje zobrazení sestavy, je třeba přidat sloupec pro každou možnou podpoložku v položce ovládacího prvku seznamu. Přidejte sloupec tak, že připravíte strukturu [LVCOLUMN](/windows/win32/api/commctrl/ns-commctrl-lvcolumnw) a pak zavoláte [insertcolumn](../mfc/reference/clistctrl-class.md#insertcolumn). Po přidání potřebných sloupců (někdy označovaných jako položky záhlaví) můžete změnit jejich pořadí pomocí členských funkcí a stylů, které patří k vloženému ovládacímu prvku záhlaví. Další informace naleznete [v tématu Objednání položek v ovládacím prvku záhlaví](../mfc/ordering-items-in-the-header-control.md).

> [!NOTE]
> Pokud je ovládací prvek seznamu vytvořen pomocí **LVS_NOCOLUMNHEADER** stylu, bude jakýkoli pokus o vložení sloupců ignorován.

## <a name="see-also"></a>Viz také

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
