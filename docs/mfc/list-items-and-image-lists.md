---
title: Položky seznamu a seznamy obrázků
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: 77dd2f6a056ca74ff3334878a9cf1ef51c773335
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508364"
---
# <a name="list-items-and-image-lists"></a>Položky seznamu a seznamy obrázků

"Item" v ovládacím prvku seznamu ([CListCtrl](../mfc/reference/clistctrl-class.md)) se skládá z ikony, popisku a případně dalších informací (v "podpoložkách").

Ikony pro položky ovládacího prvku seznam jsou obsaženy v seznamech obrázků. Jeden seznam obrázků obsahuje ikony plné velikosti použité v zobrazení ikon. Druhý, volitelný seznam obrázků obsahuje menší verze stejných ikon pro použití v jiných zobrazeních ovládacího prvku. Třetí volitelný seznam obsahuje "State" image, jako jsou zaškrtávací políčka, aby se zobrazovaly před malými ikonami v některých zobrazeních. Čtvrtý volitelný seznam obsahuje obrázky, které se zobrazují v jednotlivých položkách záhlaví ovládacího prvku seznam.

> [!NOTE]
>  Pokud se ovládací prvek zobrazení seznamu vytvoří se stylem LVS_SHAREIMAGELISTS, zodpovídáte za zničení seznamů obrázků, když už se nepoužívají. Tento styl zadejte, pokud přiřazujete stejné seznamy obrázků k více ovládacím prvkům zobrazení seznamu. v opačném případě se více než jeden ovládací prvek může pokusit zničit stejný seznam obrázků.

Další informace o položkách seznamu naleznete v tématu [zobrazení seznamů obrázků](/windows/win32/Controls/using-list-view-controls) a [položky a podpoložky](/windows/win32/Controls/using-list-view-controls) v Windows SDK. Viz také třída [atributu CImageList](../mfc/reference/cimagelist-class.md) v *Referenci knihovny MFC* a [použití atributu CImageList](../mfc/using-cimagelist.md) v této rodině článků.

Chcete-li vytvořit ovládací prvek seznamu, je nutné zadat seznamy obrázků, které budou použity při vložení nových položek do seznamu. Následující příklad ukazuje tento postup, kde *m_pImagelist* je ukazatel typu `CImageList` `CListCtrl` a *m_listctrl* je datový člen.

[!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]

Pokud ale neplánujete zobrazit ikony v zobrazení seznamu nebo v ovládacím prvku seznamu, nepotřebujete seznamy obrázků.

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
