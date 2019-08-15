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
ms.openlocfilehash: 9321a582f223269ee998dccd01721f47d90eb7fe
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509345"
---
# <a name="adding-columns-to-the-control-report-view"></a>Přidávání sloupců do ovládacího prvku (zobrazení sestavy)

> [!NOTE]
>  Následující postup se vztahuje buď na objekt [CListView –](../mfc/reference/clistview-class.md) nebo [CListCtrl](../mfc/reference/clistctrl-class.md) .

Když je ovládací prvek seznamu v zobrazení sestavy, jsou zobrazeny sloupce a poskytuje způsob uspořádání různých dílčích položek každé položky ovládacího prvku seznamu. Tato organizace je implementovaná pomocí spojení 1:1 mezi sloupcem v ovládacím prvku seznam a přidruženou dílčí položkou položky ovládacího prvku seznamu. Další informace o podpoložkách naleznete v tématu [Přidání položek do ovládacího prvku](../mfc/adding-items-to-the-control.md). Příkladem ovládacího prvku seznam v zobrazení sestava je zobrazení podrobností v oknech Windows 95 a Windows 98 Explorer. První sloupec obsahuje seznam složek, ikon souborů a popisků. Ostatní sloupce seznam velikostí souborů, typ souboru, datum poslední změny atd.

I když lze sloupce do ovládacího prvku seznamu kdykoli přidat, jsou sloupce viditelné pouze v případě, že ovládací prvek má `LVS_REPORT` zapnutý bit stylu.

Každý sloupec má přidruženou položku záhlaví (viz [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)), která má sloupec popisek a umožňuje uživatelům změnit velikost sloupce.

Pokud ovládací prvek seznam podporuje zobrazení sestav, je nutné přidat sloupec pro každou možnou podpoložku v položce ovládacího prvku seznamu. Přidejte sloupec přípravou struktury [LVCOLUMN](/windows/win32/api/commctrl/ns-commctrl-lvcolumnw) a pak zavolejte na [InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn). Po přidání nezbytných sloupců (někdy označovaných jako položky záhlaví) můžete změnit jejich pořadí pomocí členských funkcí a stylů náležejících k ovládacímu prvku vložené záhlaví. Další informace naleznete v tématu [objednávání položek v záhlaví ovládacího prvku](../mfc/ordering-items-in-the-header-control.md).

> [!NOTE]
>  Pokud se ovládací prvek seznam vytvoří se stylem **LVS_NOCOLUMNHEADER** , budou se všechny pokusy o vložení sloupců ignorovat.

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
