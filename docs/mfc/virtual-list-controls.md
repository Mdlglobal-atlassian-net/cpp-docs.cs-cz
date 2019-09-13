---
title: Ovládací prvky typu virtuální seznam
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: a6e76a812a6196c487f72516e2b88198a544fdc7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907335"
---
# <a name="virtual-list-controls"></a>Ovládací prvky typu virtuální seznam

Seznam virtuálních seznamů je ovládací prvek zobrazení seznamu, který má styl LVS_OWNERDATA. Tento styl umožňuje ovládacímu prvku podporovat počet položek až do **hodnoty DWORD** (výchozí počet položek se rozšiřuje pouze na celé **číslo**). Největší výhoda poskytovaná tímto stylem však umožňuje pouze podmnožinu datových položek v paměti. To umožňuje, aby se ovládací prvek zobrazení seznamu virtuálních seznamů zapůjčuje k použití s velkými databázemi informací, kde jsou již používány konkrétní metody přístupu k datům.

> [!NOTE]
>  Kromě poskytování funkce virtuálních seznamů v `CListCtrl`prostředí MFC také poskytuje stejnou funkci ve třídě [CListView –](../mfc/reference/clistview-class.md) .

Existují některé problémy s kompatibilitou, které byste měli znát při vývoji ovládacích prvků virtuálních seznamů. Další informace naleznete v části problémy s kompatibilitou v tématu ovládací prvky seznam-zobrazení v Windows SDK.

## <a name="handling-the-lvn_getdispinfo-notification"></a>Zpracování oznámení LVN_GETDISPINFO

Ovládací prvky virtuálního seznamu udržují velmi málo informací o položkách. S výjimkou výběru položek a informací o výběru jsou všechny informace o položkách spravovány vlastníkem ovládacího prvku. Rozhraní požaduje informace prostřednictvím oznamovací zprávy LVN_GETDISPINFO. Aby bylo možné poskytnout požadované informace, musí toto oznámení zpracovat vlastník ovládacího prvku Virtual list (nebo samotného ovládacího prvku). To se dá snadno udělat pomocí [Průvodce třídami](reference/mfc-class-wizard.md) (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)). Výsledný kód by měl vypadat podobně jako v následujícím příkladu (kde `CMyDialog` vlastní objekt ovládacího prvku seznam virtuálních seznamů a dialogové okno zpracovává oznámení):

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

V obslužné rutině zprávy s oznámením LVN_GETDISPINFO je nutné ověřit, zda jsou požadovány informace o typu. Možné hodnoty jsou:

- `LVIF_TEXT`Člen *pszText* musí být vyplněn.

- `LVIF_IMAGE`Člen *iImage* musí být vyplněn.

- `LVIF_INDENT`Člen *iIndent* musí být vyplněn.

- `LVIF_PARAM`Člen *lParam* musí být vyplněn. (Pro dílčí položky nejsou k dispozici.)

- `LVIF_STATE`Člen *stavu* musí být vyplněn.

Pak byste měli dodat jakékoli informace, které jsou požadovány zpět do rozhraní.

Následující příklad (pořízený z těla obslužné rutiny oznámení pro objekt ovládacího prvku seznamu) ukazuje jednu z možných metod poskytnutím informací pro textové vyrovnávací paměti a obrázek položky:

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>Ovládací prvky pro ukládání do mezipaměti a virtuální seznam

Vzhledem k tomu, že tento typ ovládacího prvku seznam je určený pro velké datové sady, doporučujeme ukládat do mezipaměti požadovaná data položek, aby se zlepšil výkon při načítání. Rozhraní poskytuje mechanismus pro dodávání mezipaměti, který pomáhá optimalizovat mezipaměť odesláním zprávy s oznámením LVN_ODCACHEHINT.

Následující příklad aktualizuje mezipaměť s rozsahem předaným funkci obslužné rutiny.

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

Další informace o přípravě a údržbě mezipaměti naleznete v části Správa mezipaměti v tématu ovládací prvky seznam-zobrazení v Windows SDK.

## <a name="finding-specific-items"></a>Hledání konkrétních položek

Zpráva oznámení LVN_ODFINDITEM je odeslána ovládacím prvkem Virtual list, když je třeba najít konkrétní položku ovládacího prvku seznamu. Zpráva oznámení se odešle, když ovládací prvek zobrazení seznamu přijme rychlý přístup k klíči nebo když obdrží zprávu LVM_FINDITEM. Informace o hledání jsou odesílány ve formě struktury **LVFINDINFO** , která je členem struktury **NMLVFINDITEM** . Zpracování této zprávy přepsáním `OnChildNotify` funkce objektu ovládacího prvku seznamu a uvnitř těla obslužné rutiny vyhledejte zprávu LVN_ODFINDITEM. Pokud se najde, proveďte příslušnou akci.

Měli byste být připraveni vyhledat položku, která odpovídá informacím uvedeným v ovládacím prvku zobrazení seznamu. Index položky byste měli vracet, pokud je to úspěšné, nebo-1, pokud se nenajde žádná vyhovující položka.

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
