---
title: Položky seznamu a seznamy obrázků
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: d378c6e07280349f9995981ad794039ebc015b25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353055"
---
# <a name="list-items-and-image-lists"></a>Položky seznamu a seznamy obrázků

"Položka" v ovládacím prvku seznamu ([CListCtrl](../mfc/reference/clistctrl-class.md)) se skládá z ikony, popisku a případně dalších informací (v "podpoložkách").

Ikony položek ovládacího prvku seznamu jsou obsaženy v seznamech obrázků. Jeden seznam obrázků obsahuje ikony plné velikosti používané v zobrazení ikon. Druhý, volitelný seznam obrázků obsahuje menší verze stejných ikon pro použití v jiných zobrazeních ovládacího prvku. Třetí volitelný seznam obsahuje "stavové" obrázky, například zaškrtávací políčka, pro zobrazení před malými ikonami v určitých zobrazeních. Čtvrtý volitelný seznam obsahuje obrázky, které jsou zobrazeny v jednotlivých položkách záhlaví ovládacího prvku seznamu.

> [!NOTE]
> Pokud je ovládací prvek zobrazení seznamu vytvořen s LVS_SHAREIMAGELISTS stylem, jste zodpovědní za zničení seznamů obrázků, když se již nepoužívají. Tento styl určete, pokud přiřadíte stejné seznamy obrázků k více ovládacím prvkům zobrazení seznamu; v opačném případě se může pokusit zničit stejný seznam obrázků více ovládacích prvku.

Další informace o položkách seznamu naleznete v [tématu Seznam zobrazení obrázků](/windows/win32/Controls/using-list-view-controls) a [položek a podpoložek](/windows/win32/Controls/using-list-view-controls) v sadě Windows SDK. Viz také třída [CImageList](../mfc/reference/cimagelist-class.md) v *knihovně MFC reference* a [pomocí CImageList](../mfc/using-cimagelist.md) v této rodině článků.

Chcete-li vytvořit ovládací prvek seznamu, je třeba zadat seznamy obrázků, které mají být použity při vkládání nových položek do seznamu. Následující příklad ukazuje tento postup, kde *m_pImagelist* `CImageList` je ukazatel `CListCtrl` typu a *m_listctrl* je datový člen.

[!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]

Pokud však neplánujete zobrazit ikony v ovládacím prvku zobrazení seznamu nebo seznamu, nepotřebujete seznamy obrázků.

## <a name="see-also"></a>Viz také

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
