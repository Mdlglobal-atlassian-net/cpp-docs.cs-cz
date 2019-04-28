---
title: Ovládací prvky typu virtuální seznam
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: 7372aca9e24a554e01f7a61f43d6170e99fe34c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358241"
---
# <a name="virtual-list-controls"></a>Ovládací prvky typu virtuální seznam

Ovládací prvek seznam virtuálních je ovládací prvek zobrazení seznamu, který má LVS_OWNERDATA styl. Tento styl umožňuje kontrolu pro podporu až počet položek **DWORD** (počet položek výchozí rozšiřuje pouze na **int**). Největší výhodou poskytovaných tímto stylem ale možnost používat pouze podmnožinu datových položek v paměti v daný okamžik. To umožňuje ovládací prvek zobrazení virtuálního seznamu do řešení pro použití s velkými databázemi informací, kde specifických metod přístupu k datům, jsou už zavedené.

> [!NOTE]
>  Kromě toho, že seznam virtuálních funkcí v `CListCtrl`, MFC také funguje stejně v [CListView](../mfc/reference/clistview-class.md) třídy.

Existují některé problémy s kompatibilitou, které byste měli znát při vývoji ovládací prvky typu virtuální seznam. Další informace najdete v části problémy s kompatibilitou tématu ovládací prvky zobrazení seznamu v sadě Windows SDK.

## <a name="handling-the-lvngetdispinfo-notification"></a>Zpracování oznámení LVN_GETDISPINFO

Ovládací prvky typu virtuální seznam Udržovat velmi málo informací položky. S výjimkou výběr položek a detailní informace informace o všech položkách spravuje vlastník ovládacího prvku. Rozhraním, přes LVN_GETDISPINFO zprávu s oznámením je požadované informace. K poskytování požadované informace, musí vlastník ovládací prvek typu virtuální seznam (nebo samotný ovládací prvek) zpracovat toto oznámení. Snadno to provést pomocí okna vlastnosti (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)). Výsledný kód by měl vypadat přibližně jako v následujícím příkladu (kde `CMyDialog` vlastní objekt ovládacího prvku seznam virtuálních a dialogového okna je zpracování oznámení):

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

V obslužné rutině LVN_GETDISPINFO zprávy oznámení musíte zkontrolovat, pokud chcete zobrazit, jaké typy informací jsou požadovány. Možné hodnoty jsou:

- `LVIF_TEXT` *PszText* člena musí být vyplněna.

- `LVIF_IMAGE` *IImage* člena musí být vyplněna.

- `LVIF_INDENT` *IIndent* člena musí být vyplněna.

- `LVIF_PARAM` *LParam* člena musí být vyplněna. (Není k dispozici pro podřízené položky.)

- `LVIF_STATE` *Stavu* člena musí být vyplněna.

Pak by mělo nabízet, požadované libovolné informace zpět do rozhraní.

Následující příklad (přijatá z těla obslužné rutina oznámení pro objekt ovládacího prvku seznamu) ukazuje možných metod zadáním informací pro vyrovnávací paměti textu a obrázku položky:

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>Ukládání do mezipaměti a virtuální ovládacích prvcích seznam

Protože tento typ ovládacího prvku seznam je určený pro velké datové sady, doporučuje se, že je požadovaná položka ukládat data do mezipaměti ke zlepšení výkonu načítání. Rozhraní framework poskytuje mechanismus komentování mezipaměti pomáhat při optimalizaci mezipaměti zasláním oznámení LVN_ODCACHEHINT.

Následující příklad aktualizuje mezipaměť s rozsahem předaný funkci obslužné rutiny.

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

Další informace o přípravě a zachování v mezipaměti naleznete v části Správa mezipaměti tématu ovládací prvky zobrazení seznamu v sadě Windows SDK.

## <a name="finding-specific-items"></a>Vyhledání konkrétních položek

Zprávy oznámení LVN_ODFINDITEM posílá ovládací prvek typu virtuální seznam při dané položky ovládacího prvku musí být nalezen. Zpráva oznámení se pošle, když ovládací prvek zobrazení seznamu obdrží rychlý přístup ke klíčům, nebo když přijme zprávu LVM_FINDITEM. Hledat informace jsou odeslány ve formě **LVFINDINFO** strukturou, který je členem z **NMLVFINDITEM** struktury. Tuto zprávu zpracovat tak, že přepíšete `OnChildNotify` funkce vašeho seznamu řízení objektu a uvnitř těla obslužné rutiny, zkontrolujte LVN_ODFINDITEM zprávy. Pokud se nenašel, proveďte příslušnou akci.

Byste měli být připraveni vyhledejte položku, která odpovídá informace poskytují ovládací prvek zobrazení seznamu. Index položky v případě úspěchu nebo -1 by měla vrátit, pokud není nalezen žádný odpovídající položka.

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
