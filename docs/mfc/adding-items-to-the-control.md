---
title: Přidávání položek do ovládacího prvku
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
ms.openlocfilehash: 6c03be6f04746ec2e3146916d72cad637a204187
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509327"
---
# <a name="adding-items-to-the-control"></a>Přidávání položek do ovládacího prvku

Chcete-li přidat položky do ovládacího prvku seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)), zavolejte jednu z několika verzí členské funkce [InsertItem](../mfc/reference/clistctrl-class.md#insertitem) , v závislosti na tom, jaké informace máte. Jedna verze používá [LVITEM](/windows/win32/api/commctrl/ns-commctrl-lvitemw) strukturu, kterou připravíte. Vzhledem k tomu, že Strukturaobsahujemnohočlenů,mátevětšíkontrolunadatributypoložkyovládacíhoprvkuseznamu.`LVITEM`

Členy `LVITEM` `iItem` a jsoudvadůležitéčleny(vsouvislostiszobrazenímsestavy)struktury.`iSubItem` Člen je index založený na nule položky, na kterou odkazuje struktura, `iSubItem` a člen je index založený na jednom z dílčích položek, nebo nula, pokud struktura obsahuje informace o položce. `iItem` Pomocí těchto dvou členů, které určíte, podle položky, typu a hodnoty informací o dílčích položkách, které se zobrazí, když je ovládací prvek seznam v zobrazení sestava. Další informace najdete v tématu [CListCtrl:: SetItem](../mfc/reference/clistctrl-class.md#setitem).

Další členové určují text, ikonu, stav a položku položky, data a položky. "Data položky" je hodnota definovaná aplikací přidružená k položce zobrazení seznamu. Další informace o `LVITEM` struktuře naleznete v tématu [CListCtrl:: GetItem](../mfc/reference/clistctrl-class.md#getitem).

Jiné verze `InsertItem` nástroje přebírají jednu nebo více samostatných hodnot, které odpovídají členům `LVITEM` ve struktuře, a umožňují tak inicializovat pouze ty členy, které chcete podporovat. Obecně platí, že ovládací prvek seznam spravuje úložiště pro položky seznamu, ale místo toho můžete uložit některé informace v aplikaci, a to pomocí "Item callback". Další informace naleznete v tématech [položky zpětného volání a maska zpětného volání](../mfc/callback-items-and-the-callback-mask.md) v tomto tématu a [Zpětná maska zpětného volání](/windows/win32/Controls/using-list-view-controls) v Windows SDK.

Další informace najdete v tématu [Přidání položek seznamu a dílčích](/windows/win32/Controls/using-list-view-controls)položek.

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
