---
title: Přidávání položek do ovládacího prvku
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
ms.openlocfilehash: 88e008f06fb669db1c13872b1a58555eeb357d86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394777"
---
# <a name="adding-items-to-the-control"></a>Přidávání položek do ovládacího prvku

Přidání položek do ovládacího prvku seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)), volání jednoho z několika verzí [metody InsertItem](../mfc/reference/clistctrl-class.md#insertitem) členskou funkci, v závislosti na tom, jaké informací, které jsou potřeba. Přijímá jednu verzi [LV_ITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) struktura, která je připravit. Vzhledem k tomu, `LV_ITEM` struktura obsahuje mnoho členů, budete mít větší kontrolu nad atributy položku ovládacího prvku seznamu.

Dva důležité členy (ve vztahu zobrazení sestavy) `LV_ITEM` struktury jsou `iItem` a `iSubItem` členy. `iItem` Člen je z nuly vycházející index položky odkazuje na strukturu a `iSubItem` člen je založen na jedničce index podpoložku nebo nula, pokud struktura obsahuje informace o položce. Se tyto dva členy můžete určit, za položky, typu a hodnoty podřízenou položku informace, které se zobrazí, když je ovládací prvek seznam v zobrazení sestavy. Další informace najdete v tématu [CListCtrl::SetItem](../mfc/reference/clistctrl-class.md#setitem).

Další členy zadejte text položky, ikona, stav a data položky. "Položky dat" je hodnota definovaného aplikací přidružených k položce zobrazení seznamu. Další informace o `LV_ITEM` struktury, přečtěte si téma [CListCtrl::GetItem](../mfc/reference/clistctrl-class.md#getitem).

Další verze `InsertItem` provést jeden nebo více samostatných hodnoty odpovídající členy v `LV_ITEM` struktury, což umožňuje inicializovat pouze ty členy, které chcete podporovat. Obecně platí ovládací prvek seznamu spravuje úložiště pro položky seznamu, ale můžete uložit některé z informací ve vaší aplikaci místo toho pomocí "položky zpětného volání." Další informace najdete v tématu [položky zpětného volání a maska zpětného volání](../mfc/callback-items-and-the-callback-mask.md) v tomto tématu a [položky zpětného volání a maska zpětného volání](/windows/desktop/Controls/using-list-view-controls) v sadě Windows SDK.

Další informace najdete v tématu [přidávání zobrazení seznamu položek a podpoložek](/windows/desktop/Controls/using-list-view-controls).

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
