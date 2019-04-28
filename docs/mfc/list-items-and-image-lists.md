---
title: Položky seznamu a seznamy obrázků
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: 1679b5c59c6dd55ca47c70ea7c880493304ebf4e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365270"
---
# <a name="list-items-and-image-lists"></a>Položky seznamu a seznamy obrázků

"Položka" v ovládacím prvku seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)) se skládá z ikonu, popisek a případně jiné informace (v "podřízené položky").

U ikon pro ovládací prvek položky seznamu jsou obsaženy v seznamech obrázků. Jeden seznam image obsahuje plnou velikostí ikony používané v zobrazení ikon. Seznam druhý, optional, image obsahuje menší verze stejné ikony pro použití v jiných zobrazení ovládacího prvku. Třetí volitelný seznam obsahuje "stavu" image, jako jsou zaškrtávací políčka pro zobrazení před malé ikony v některých zobrazeních. Čtvrtý volitelný seznam obsahuje bitové kopie, které se zobrazí v záhlaví jednotlivých položek ovládacího prvku seznamu.

> [!NOTE]
>  Pokud ovládací prvek zobrazení seznamu se vytvoří s LVS_SHAREIMAGELISTS styl, budete muset pro zničení seznamů obrázků, když se už používají. Zadejte seznamy tento styl, pokud přiřadíte stejnou bitovou kopii do více ovládací prvky zobrazení seznamu; v opačném případě více než jeden ovládací prvek může pokusit o zničit stejného seznamu obrázků.

Další informace o položkách seznamu najdete v tématu [seznamy obrázků zobrazení seznamu](/windows/desktop/Controls/using-list-view-controls) a [položek a podpoložek](/windows/desktop/Controls/using-list-view-controls) v sadě Windows SDK. Viz také třída [cimagelist –](../mfc/reference/cimagelist-class.md) v *odkaz knihovny MFC* a [používání atributu CImageList](../mfc/using-cimagelist.md) v této řadě článků.

Chcete-li vytvořit ovládací prvek seznamu, budete muset zadat seznamy obrázků, která se použije při vložení nových položek do seznamu. Následující příklad ukazuje tento postup, kde *m_pImagelist* je ukazatel typu `CImageList` a *m_listctrl* je `CListCtrl` datový člen.

[!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]

Ale pokud nemáte v úmyslu zobrazení ikon v zobrazení seznamu nebo ovládací prvek seznamu, není nutné seznamy obrázků.

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
