---
title: Ovládací prvky typu virtuální seznam
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: 1ade5f404e134cf6de20756dcc5af169fefdec76
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375518"
---
# <a name="virtual-list-controls"></a>Ovládací prvky typu virtuální seznam

Ovládací prvek virtuálníseznam je ovládací prvek zobrazení seznamu, který má LVS_OWNERDATA styl. Tento styl umožňuje ovládacímu prvku podporovat počet položek až do **DWORD** (výchozí počet položek se vztahuje pouze **na int**). Největší výhodou tohoto stylu je však možnost mít pouze podmnožinu datových položek v paměti v jednom okamžiku. To umožňuje ovládacímu prvku zobrazení virtuálního seznamu, který se může použít pro velké databáze informací, kde jsou již zavedeny specifické metody přístupu k datům.

> [!NOTE]
> Kromě poskytování funkce virtuální seznam `CListCtrl`v knihovně MFC také poskytuje stejné funkce v [CListView](../mfc/reference/clistview-class.md) třídy.

Existují některé problémy s kompatibilitou, které byste měli znát při vývoji ovládacích prvků virtuálního seznamu. Další informace naleznete v části Problémy s kompatibilitou v tématu Ovládací prvky zobrazení seznamu v sadě Windows SDK.

## <a name="handling-the-lvn_getdispinfo-notification"></a>Zpracování oznámení LVN_GETDISPINFO

Ovládací prvky virtuálního seznamu udržují velmi málo informací o položkách. S výjimkou informací o výběru položky a zaměření jsou všechny informace o položce spravovány vlastníkem ovládacího prvku. Informace jsou požadovány rámcem prostřednictvím LVN_GETDISPINFO oznamovací zprávy. Chcete-li poskytnout požadované informace, vlastník ovládacího prvku virtuální seznam (nebo ovládací prvek sám) musí zpracovat toto oznámení. To lze snadno provést pomocí [Průvodce třídou](reference/mfc-class-wizard.md) (viz [Mapování zpráv na funkce).](../mfc/reference/mapping-messages-to-functions.md) Výsledný kód by měl vypadat podobně jako `CMyDialog` v následujícím příkladu (kde vlastní objekt ovládacího prvku virtuální seznam a dialogové okno zpracovává oznámení):

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

V obslužné rutině pro LVN_GETDISPINFO oznámení, je nutné zkontrolovat, jaký typ informací je požadováno. Možné hodnoty jsou:

- `LVIF_TEXT`Člen *pszText* musí být vyplněn.

- `LVIF_IMAGE`Člen *iImage* musí být vyplněn.

- `LVIF_INDENT`Člen *iIndent* musí být vyplněn.

- `LVIF_PARAM`Člen *lParam* musí být vyplněn. (Není k dispozici pro dílčí položky.)

- `LVIF_STATE`Člen *státu* musí být vyplněn.

Poté byste měli zadat všechny informace, které jsou požadovány zpět do rámce.

Následující příklad (převzatý z těla obslužné rutiny oznámení pro řídicí objekt seznamu) ukazuje jednu možnou metodu poskytnutím informací pro textové vyrovnávací paměti a obrázek položky:

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>Ovládací prvky ukládání do mezipaměti a virtuálníseznam

Vzhledem k tomu, že tento typ ovládacího prvku seznamu je určen pro velké sady dat, doporučujeme ukládat požadovaná data položek do mezipaměti za účelem zlepšení výkonu načítání. Rozhraní framework poskytuje mechanismus rady při ukládání do mezipaměti mechanismus pomoci při optimalizaci mezipaměti odesláním LVN_ODCACHEHINT oznámení.

Následující příklad aktualizuje mezipaměť s rozsahem předaným funkci obslužné rutiny.

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

Další informace o přípravě a údržbě mezipaměti naleznete v části Správa mezipaměti v tématu Ovládací prvky zobrazení seznamu v sadě Windows SDK.

## <a name="finding-specific-items"></a>Hledání konkrétních položek

Zpráva LVN_ODFINDITEM oznámení je odeslána ovládacím prvkem virtuálního seznamu, když je třeba najít určitou položku ovládacího prvku seznamu. Zpráva s oznámením je odeslána, když ovládací prvek zobrazení seznamu obdrží rychlý přístup klíčem nebo když obdrží zprávu LVM_FINDITEM. Vyhledávací informace jsou odesílány ve formě struktury **LVFINDINFO,** která je členem struktury **NMLVFINDITEM.** Zpracovat tuto zprávu `OnChildNotify` přepsáním funkce objektu ovládacího prvku seznamu a uvnitř těla obslužné rutiny zkontrolujte zprávu LVN_ODFINDITEM. Pokud je nalezen, proveďte příslušnou akci.

Měli byste být připraveni vyhledat položku, která odpovídá informacím daným ovládacím prvkem zobrazení seznamu. Pokud je úspěšná, měli byste vrátit index položky nebo -1, pokud není nalezena žádná odpovídající položka.

## <a name="see-also"></a>Viz také

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
