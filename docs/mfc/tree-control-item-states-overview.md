---
title: Přehled stavů položek ovládacího prvku strom
ms.date: 11/04/2016
helpviewer_keywords:
- states, CTreeCtrl items
- tree controls [MFC], item states overview
- CTreeCtrl class [MFC], item states
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
ms.openlocfilehash: bbeabf69f174fcf172808ff71f07ed05f1dc9675
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511036"
---
# <a name="tree-control-item-states-overview"></a>Přehled stavů položek ovládacího prvku strom

Každá položka v ovládacím prvku stromu ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) má aktuální stav. Položka může být například vybraná, zakázaná, rozbalená a tak dále. Ve většině případů ovládací prvek stromové struktury automaticky nastaví stav položky tak, aby odrážela akce uživatelů, jako je například výběr položky. Můžete však také nastavit stav položky pomocí členské funkce [SetItemState](../mfc/reference/ctreectrl-class.md#setitemstate) a načíst aktuální stav položky pomocí členské funkce [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate) . Úplný seznam stavů položek naleznete v tématu [konstanty ovládacího prvku strom-zobrazení](/windows/win32/Controls/tree-view-control-item-states) v Windows SDK.

Aktuální stav položky je určen parametrem *nInformace* . Ovládací prvek strom může změnit stav položky tak, aby odrážel akci uživatele, jako je například výběr položky nebo nastavení fokusu na položku. Kromě toho může aplikace změnit stav položky na zakázat nebo skrýt položku nebo určit překrývající obrázek nebo stavový obrázek.

Když zadáte nebo změníte stav položky, parametr *nStateMask* určuje, které stavové bity se mají nastavit a parametr *nInformace* obsahuje nové hodnoty pro tyto bity. Například následující příklad mění aktuální stav nadřazené položky (určené parametrem *hParentItem*) v `CTreeCtrl` objektu (`m_treeCtrl`) na `TVIS_EXPANDPARTIAL`:

[!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/cpp/tree-control-item-states-overview_1.cpp)]

Dalším příkladem změny stavu je nastavit překryvný obrázek položky. Aby to bylo možné, *nStateMask* musí zahrnovat `TVIS_OVERLAYMASK` hodnotu a *nInformace* musí zahrnovat index překrytí, který se posune vlevo o osm bitů pomocí makra [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) . Index může být 0, aby se neurčila žádná překryvná image. Překrytí obrázku musí být přidáno do seznamu překrývajících se obrázků v ovládacím prvku stromu, a to předchozím voláním funkce [atributu CImageList:: SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) . Funkce určuje index obrázku, který má být přidán, v jednom z nich. Toto je index, který se používá pro makro INDEXTOOVERLAYMASK. Stromový ovládací prvek může mít až čtyři překryté obrázky.

Chcete-li nastavit obrázek stavu položky, *nStateMask* musí zahrnovat `TVIS_STATEIMAGEMASK` hodnotu a *nInformace* musí zahrnovat index obrázku stavu posunutý doleva o 12 bitů pomocí makra [INDEXTOSTATEIMAGEMASK](/windows/win32/api/commctrl/nf-commctrl-indextostateimagemask) . Index může být 0, aby se neurčil žádný stavový obrázek. Další informace o překryvných obrázcích a obrazech stavu naleznete v tématu [seznam imagí ovládacího prvku strom](../mfc/tree-control-image-lists.md).

## <a name="see-also"></a>Viz také:

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
